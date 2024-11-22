---
title: Produktattribute dynamisch hinzufügen
description: Erfahren Sie, wie Sie während der Datensynchronisierung dynamische benutzerdefinierte Produktattribute zum Datenexport-Feed hinzufügen.
role: Admin, Developer
source-git-commit: e75092e918d06d4d1291784b0498d274ea8396e8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Produktattribute dynamisch während der Datensynchronisation hinzufügen

Sie können Produktattribute erweitern, ohne sie in Adobe Commerce zu registrieren, indem Sie ein Plug-in erstellen, um die Attribute während des Datensynchronisierungsprozesses hinzuzufügen.

>[!NOTE]
>
>Die beste Möglichkeit, Produktattribute zu erweitern, besteht darin, sie [zu Adobe Commerce](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) hinzuzufügen, wo Sie sie über den Commerce-Administrator konfigurieren und verwalten können. Fügen Sie sie nur dynamisch hinzu, wenn Sie sie ausschließlich für Commerce Storefront-Dienste benötigen und sie nicht in Adobe Commerce registrieren möchten. Sie können auch benutzerdefinierte Attribute mithilfe von [API-Mesh mit dem Catalog Service](../catalog-service/mesh.md) verwalten, um das GraphQL-Schema für den Catalog Service zu erweitern.

## Produktattribute hinzufügen

Erstellen Sie ein Plug-in, das der `Magento\CatalogDataExporter\Model\Provider\Product\Attributes` -Klasse eine `customer_attribute` hinzufügt.

1. Aktualisieren Sie die Konfigurationsdatei für die [Abhängigkeitseinspritzung](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in zu definieren.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\Product\Attributes">
     <plugin name="product_customer_attributes" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttribute"/>
   </type>
   ```

1. Erstellen Sie das Plug-in.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\Product\Attributes;
   
    class AddAttribute {
   
         /**
          * @param Attributes $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(Attributes $subject, array $result, $arguments): array
         {
              $productIds = \array_column($arguments, 'productId');
   
              foreach ($productIds as $productId) {
                    $result[] = [
                         'productId' => $productId,
                         // "storeViewCode" must be specified for products where the customer attribute value should be set
                         'storeViewCode' => 'default',
                         'attributes' => [
                              // specify the customer attribute code
                              'attributeCode' => 'customer_attribute',
                              // provide single or multiple values for the attribute
                              'value' => [
                                    rand(41,43)
                              ]
                         ]
                    ];
              }
   
              return $result;
         }
    }
   ```

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Diensten synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```
   bin/magento saas:resync --feed=products
   ```

## Deklarieren benutzerdefinierter Produktattribut-Metadaten

Wenn Sie ein benutzerdefiniertes Produktattribut dynamisch erstellen und es für die Anzeige, Suche oder Filterung in Storefront-Diensten verwenden möchten, fügen Sie die Produktattribut-Metadaten hinzu, um das Storefront-Verhalten zu konfigurieren.

1. Aktualisieren Sie die Konfigurationsdatei für die [Abhängigkeitsinjektion](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in für die Produktattribut-Metadaten zu definieren.

   ```xml
   <type name="\Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
     <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
   </type>
   ```

1. Erstellen Sie das Plug-in für den folgenden Provider `\Magento\CatalogDataExporter\Model\Provider\ProductMetadata`.

   Überprüfen Sie `ProductAttributeMetadata` in `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` auf erforderliche Felder.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\ProductMetadata;
   
    class AddAttributeMetadata {
   
         /**
          * @param ProductMetadata $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(ProductMetadata $subject, array $result, $arguments): array
         {
              $result[] = [
                'id' => '123',
                'storeCode' => 'default',
                'websiteCode' => 'base',
                'storeViewCode' => 'default',
                // specify the customer attribute code - should be the same as used in the products attributes plugin
                'attributeCode' => 'customer_attribute',
                // only product attributes are supported
                'attributeType' => 'catalog_product',
                // specify the data type
                'dataType' => 'int',
                'multi' => false,
                'label' => 'Customer Attribute',
                'frontendInput' => 'select',
                'required' => false,
                'unique' => false,
                'global' => true,
                'visible' => true,
                'searchable' => true,
                'filterable' => true,
                // This value must be set to true to export it to the storefront services
                'visibleInCompareList' => true,
                'visibleInListing' => true,
                'sortable' => true,
                'visibleInSearch' => true,
                'filterableInSearch' => true,
                'searchWeight' => 1.0,
                'usedForRules' => true,
                'boolean' => false,
                'systemAttribute' => false,
                'numeric' => false,
                // specify the list of attribute options
                'attributeOptions' => [
                    'option1',
                    'option2',
                    'option3'
                ]
             ];
   
              return $result;
         }
      }
   ```

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Diensten synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```
   bin/magento saas:resync --feed=productattributes
   ```




