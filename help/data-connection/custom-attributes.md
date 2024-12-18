---
title: Hinzufügen benutzerdefinierter Bestellattribute
description: Erfahren Sie, wie Sie Ihren Back-Office-Daten benutzerdefinierte Bestellattribute hinzufügen und diese Attribute an die Experience Platform senden.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 69b99cd7-33ee-4c22-8819-64e9d4410fb1
source-git-commit: 8cf67ed76e191b03ddfbfb68ed4ba07e456a3c35
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Hinzufügen benutzerdefinierter Bestellattribute

In diesem Artikel erfahren Sie, wie Sie Backoffice-Ereignissen benutzerdefinierte Attribute hinzufügen. Mit benutzerdefinierten Attributen können Sie umfangreiche Dateneinblicke erfassen, um die Analyse zu verbessern und weitere personalisierte Erlebnisse für Ihre Kunden zu erstellen.

Benutzerdefinierte Attribute werden auf zwei Ebenen unterstützt:

- Auftragsebene
- Bestellartikelebene

>[!NOTE]
>
>Adobe [!DNL Commerce] unterstützt benutzerdefinierte Attribute mit dem Datentyp „String“, „Boolean“ oder „Date“.

Das Hinzufügen benutzerdefinierter Attribute zu Back-Office-Ereignissen erfordert Folgendes:

1. Erstellen Sie ein Projekt in Ihrer [!DNL Commerce].
1. Aktualisieren Sie Ihr Schema, damit die neuen benutzerdefinierten Attribute ordnungsgemäß in Experience Platform erfasst werden können.
1. Bestätigen Sie in der Admin-Liste, dass die benutzerdefinierten Attribute erfasst und an Experience Platform gesendet werden.

>[!IMPORTANT]
>
>Die folgende Verzeichnisstruktur und die folgenden Codebeispiele veranschaulichen, wie Sie benutzerdefinierte Attribute implementieren können. Die tatsächliche Verzeichnisstruktur und der erforderliche Code hängen von Ihrer Store-Konfiguration und -Umgebung ab.

## Schritt 1: Ordnerstruktur erstellen

1. Navigieren Sie zum `app/code`-Verzeichnis in Ihrer [!DNL Commerce] und erstellen Sie ein Modulverzeichnis. Beispiel: `Magento/AepCustomAttributes`. Dieses Verzeichnis enthält die Dateien, die für Ihre benutzerdefinierten Attribute erforderlich sind.
1. Erstellen Sie im Modulverzeichnis ein Unterverzeichnis mit dem Namen `etc`. Das `etc` enthält die `module.xml`-, `query.xml`-, `di.xml`- und `et_schema.xml`.

## Schritt 2: Definieren der Abhängigkeiten und der Setup-Version

Erstellen Sie eine `module.xml`, die die Abhängigkeiten und die Setup-Version definiert. Beispiel:

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## Schritt 3: Kundenauftragsdaten abrufen

Erstellen Sie eine `query.xml`, die Kundenauftragsdaten abruft. Beispiel:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Schritt 4: Einrichten der Injektion von Abhängigkeiten

Erstellen Sie eine `di.xml` Datei , die die Injektion von Abhängigkeiten einrichtet. Beispiel:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## Schritt 5: Definieren der für die Injektion von Abhängigkeiten verwendeten Services

Erstellen Sie eine `et_schema.xml` Datei, die die Services definiert, die für die Injektion von Abhängigkeiten verwendet werden. Beispiel:

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## Schritt 6: Erstellen Sie ein Verzeichnis für die PHP-Dateien

Erstellen Sie auf derselben Ebene wie das `etc` Verzeichnis ein Verzeichnis mit dem Namen `Module/Provider`. Dieses Verzeichnis enthält die `OrderCustomAttributes` und `OrderItemCustomAttributes` PHP-Dateien.

## Schritt 7: OrderCustomAttributes definieren

Erstellen Sie eine `OrderCustomAttributes.php`, die die Reihenfolge der benutzerdefinierten Attribute definiert. Beispiel:

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## Schritt 8: OrderItemCustomAttributes definieren

Erstellen Sie eine `OrderItemCustomAttributes.php`, die die benutzerdefinierten Attribute des Bestellartikels definiert. Beispiel:

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## Schritt 9: Erstellen eines Verzeichnisses für die productContext-Datei

Erstellen Sie auf derselben Ebene wie das `etc` Verzeichnis ein Verzeichnis mit dem Namen `Plugin/Module`. Dieses Verzeichnis enthält die `ProductContext.php`.

## Schritt 10: Definieren Sie die ProductContext-Klasse

Erstellen Sie eine Datei mit dem Namen `ProductContext.php`, die die `ProductContext` definiert. Beispiel:

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## Schritt 11: Modul registrieren

Erstellen Sie auf derselben Ebene wie das `etc`-Verzeichnis eine `registration.php`-Datei, die das Modul registriert. Beispiel:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Schritt 12: Erweitern des vorhandenen XDM-Schemas

Um sicherzustellen, dass die neuen benutzerdefinierten Sortierattribute von Ihrem [!DNL Commerce] in Experience Platform aufgenommen werden können, müssen Sie das Schema erweitern, um diese benutzerdefinierten Felder einzuschließen.

Informationen zum Erweitern eines vorhandenen XDM-Schemas um diese benutzerdefinierten Felder finden Sie im Artikel [Erstellen und Bearbeiten von Schemas in der Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) in der Experience Platform-Dokumentation. Das Feld Mandanten-ID wird dynamisch generiert. Die Feldstruktur sollte jedoch dem Beispiel in der Experience Platform-Dokumentation ähneln.

>[!IMPORTANT]
>
>Benutzerdefinierte XDM-Attribute müssen mit den von [!DNL Commerce] gesendeten Attributen übereinstimmen.

Fügen Sie `commerce.order` ein Feld für die Auftragsebene hinzu:

![Bestellebene](assets/order-level.png)

Fügen Sie `productListItems` Felder für die Bestellartikelebene hinzu:

![Bestellartikelebene](assets/order-item-level.png)

## Schritt 12: Bestätigen Sie, dass Daten erfasst werden

Gehen Sie in der Admin [ Registerkarte ](connect-data.md#data-customization)Datenanpassung“, um zu bestätigen, dass benutzerdefinierte Attributdaten erfasst und an die Experience Platform gesendet werden.

### Fehlerbehebung

Wenn die Meldung `No custom order attributes found.` auf der Registerkarte **[!UICONTROL Data Customization]** angezeigt wird, bestätigen Sie Folgendes:

1. Sie haben die Voraussetzungen zum Aktivieren der [Data Connector-Erweiterung](overview.md#prerequisites) erfüllt.
1. Sie haben [benutzerdefinierte Bestellattribute“ ](#add-custom-order-attributes).
1. Mindestens ein Auftragsereignis wurde generiert.
