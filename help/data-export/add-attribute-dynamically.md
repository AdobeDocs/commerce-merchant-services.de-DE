---
title: Dynamisches Hinzufügen von Produktattributen
description: Erfahren Sie, wie Sie dem Datenexport-Feed während des Datensynchronisierungsprozesses dynamisch benutzerdefinierte Produktattribute hinzufügen.
role: Admin, Developer
exl-id: fd0e142e-eb39-4c4b-90da-6c9279b7706c
source-git-commit: 839d7ca7871acfbbfe1d1654c74e3002e1d170f7
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Dynamisches Hinzufügen von Produktattributen während der Datensynchronisation

Sie können Produktattribute erweitern, ohne sie in Adobe Commerce zu registrieren, indem Sie ein Plug-in erstellen, um die Attribute während des Datensynchronisierungsprozesses hinzuzufügen.

>[!NOTE]
>
>Die beste Möglichkeit, Produktattribute zu erweitern, besteht darin[ sie zu Adobe Commerce hinzuzufügen](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) wo Sie sie über den Commerce-Administrator konfigurieren und verwalten können. Fügen Sie sie nur dann dynamisch hinzu, wenn Sie sie ausschließlich für Commerce-Storefront-Services benötigen und nicht in Adobe Commerce registrieren möchten. Sie haben außerdem die Möglichkeit, benutzerdefinierte Attribute mithilfe von [API Mesh mit dem Katalog-Service](../catalog-service/mesh.md) zu verwalten, um das GraphQL-Schema des Katalog-Service zu erweitern.

## Produktattribute hinzufügen

Erstellen Sie ein Plug-in, das der `Magento\CatalogDataExporter\Model\Provider\Product\Attributes`-Klasse einen `customer_attribute` hinzufügt.

1. Aktualisieren Sie die [Konfigurationsdatei für die Abhängigkeitseinspeisung](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in zu definieren.

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

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Services synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```
   bin/magento saas:resync --feed=products
   ```

## Deklarieren benutzerdefinierter Produktattribut-Metadaten

Wenn Sie ein benutzerdefiniertes Produktattribut dynamisch erstellen und es für die Anzeige, Suche oder Filterung in Storefront-Services verwenden möchten, fügen Sie die Metadaten des Produktattributs hinzu, um das Verhalten der Storefront zu konfigurieren.

1. Aktualisieren Sie die [Konfigurationsdatei für Abhängigkeitseinfügungen](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`), um das Plug-in für die Metadaten des Produktattributs zu definieren.

   ```xml
   <type name="\Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
     <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
   </type>
   ```

1. Erstellen Sie das Plug-in im folgenden Provider-`\Magento\CatalogDataExporter\Model\Provider\ProductMetadata`.

   Überprüfen Sie `ProductAttributeMetadata` in `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` auf Pflichtfelder.

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

   Nachdem Sie das Plug-in hinzugefügt haben, werden die Änderungen bei der nächsten geplanten Synchronisierung mit verbundenen Storefront-Services synchronisiert. Um die Aktualisierungen sofort zu senden, verwenden Sie den folgenden CLI-Befehl, um den Synchronisierungsprozess manuell zu starten.

   ```
   bin/magento saas:resync --feed=productattributes
   ```