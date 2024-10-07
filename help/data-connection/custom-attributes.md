---
title: Benutzerdefinierte Bestellattribute hinzufügen
description: Erfahren Sie, wie Sie Ihren Backoffice-Daten benutzerdefinierte Bestellattribute hinzufügen und diese Attribute an die Experience Platform senden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Benutzerdefinierte Bestellattribute hinzufügen

In diesem Artikel erfahren Sie, wie Sie benutzerdefinierte Attribute zu Backoffice-Ereignissen hinzufügen. Mit benutzerdefinierten Attributen können Sie umfangreiche Dateneinblicke erfassen, um die Analyse zu verbessern und personalisierte Erlebnisse für Ihre Kunden zu erstellen.

Benutzerdefinierte Attribute werden auf zwei Ebenen unterstützt:

- Bestellebene
- Bestellelementebene

>[!NOTE]
>
>Adobe [!DNL Commerce] unterstützt benutzerdefinierte Attribute mit einem Datentyp aus Zeichenfolge, Booleschem Wert oder Datum.

Zum Hinzufügen benutzerdefinierter Attribute zu Backoffice-Ereignissen müssen Sie Folgendes tun:

1. Erstellen Sie ein Projekt in Ihrer [!DNL Commerce] -Installation.
1. Aktualisieren Sie Ihr Schema, sodass die neuen benutzerdefinierten Attribute ordnungsgemäß in Experience Platform aufgenommen werden können.
1. Bestätigen Sie im Admin, dass die benutzerdefinierten Attribute erfasst und an Experience Platform gesendet werden.

>[!IMPORTANT]
>
>Die folgende Ordnerstruktur und Codebeispiele veranschaulichen, wie Sie benutzerdefinierte Attribute implementieren können. Die tatsächliche Ordnerstruktur und der erforderliche Code hängen von Ihrer Speicherkonfiguration und -umgebung ab.

## Schritt 1: Verzeichnisstruktur erstellen

1. Navigieren Sie zum Ordner &quot;`app/code`&quot;in Ihrer [!DNL Commerce] -Installation und erstellen Sie einen Modulordner. Beispiel: `Magento/AepCustomAttributes`. Dieser Ordner enthält die Dateien, die für Ihre benutzerdefinierten Attribute erforderlich sind.
1. Erstellen Sie im Modulverzeichnis ein Unterverzeichnis mit dem Namen `etc`. Das Verzeichnis `etc` enthält die Dateien `module.xml`, `query.xml`, `di.xml` und `et_schema.xml`.

## Schritt 2: Abhängigkeiten und Setup-Version definieren

Erstellen Sie eine `module.xml` -Datei, die die Abhängigkeiten und die Setup-Version definiert. Beispiel:

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

## Schritt 3: Abrufen von Daten zu Verkaufsbestellungen

Erstellen Sie eine `query.xml` -Datei, die Daten zu Verkaufsbestellungen abruft. Beispiel:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Schritt 4: Einrichten der Abhängigkeitsinjektion

Erstellen Sie eine `di.xml` -Datei, die die Abhängigkeitseinspritzung einrichtet. Beispiel:

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

## Schritt 5: Definieren Sie die Dienste, die für die Abhängigkeitsinjektion verwendet werden

Erstellen Sie eine `et_schema.xml` -Datei, die die Dienste definiert, die für die Abhängigkeitsinjektion verwendet werden. Beispiel:

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

## Schritt 6: Erstellen eines Verzeichnisses für die PHP-Dateien

Erstellen Sie auf derselben Ebene wie das Verzeichnis `etc` einen Ordner mit dem Namen `Module/Provider`. Dieses Verzeichnis enthält die PHP-Dateien `OrderCustomAttributes` und `OrderItemCustomAttributes`.

## Schritt 7: Definieren der OrderCustomAttributes

Erstellen Sie eine `OrderCustomAttributes.php` -Datei, die die benutzerdefinierten Attribute zur Reihenfolge definiert. Beispiel:

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

## Schritt 8: Definieren der OrderItemCustomAttributes

Erstellen Sie eine `OrderItemCustomAttributes.php` -Datei, die die benutzerdefinierten Attribute des Bestellelements definiert. Beispiel:

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

## Schritt 9: Erstellen eines Ordners für die productContext-Datei

Erstellen Sie auf derselben Ebene wie das Verzeichnis `etc` einen Ordner mit dem Namen `Plugin/Module`. Dieses Verzeichnis enthält die Datei &quot;`ProductContext.php`&quot;.

## Schritt 10: Definieren der ProductContext-Klasse

Erstellen Sie eine Datei mit dem Namen `ProductContext.php` , die die Klasse `ProductContext` definiert. Beispiel:

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

Erstellen Sie auf derselben Ebene wie das Verzeichnis &quot;`etc`&quot; eine &quot;`registration.php`&quot;-Datei, die das Modul registriert. Beispiel:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Schritt 12: Erweitern des vorhandenen XDM-Schemas

Um sicherzustellen, dass die neuen benutzerdefinierten Bestellattribute von Ihrem [!DNL Commerce] -Schema in Experience Platform erfasst werden können, müssen Sie das Schema erweitern, um diese benutzerdefinierten Felder einzuschließen.

Informationen zum Erweitern eines vorhandenen XDM-Schemas um diese benutzerdefinierten Felder finden Sie im Artikel [Erstellen und Bearbeiten von Schemas in der Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) in der Experience Platform-Dokumentation. Das Feld Mandantenkennung wird dynamisch generiert. Die Feldstruktur sollte jedoch dem in der Experience Platform-Dokumentation angegebenen Beispiel ähneln.

>[!IMPORTANT]
>
>Benutzerdefinierte XDM-Attribute müssen mit den von [!DNL Commerce] gesendeten Attributen übereinstimmen.

Fügen Sie `commerce.order` ein Feld für die Bestellebene hinzu:

![Bestellstufe](assets/order-level.png)

Fügen Sie zu `productListItems` Felder für die Bestellelementebene hinzu:

![Bestellelementebene](assets/order-item-level.png)

## Schritt 12: Überprüfen, ob Daten erfasst werden

Überprüfen Sie im Admin die Registerkarte [Datenanpassung](connect-data.md#data-customization) , ob benutzerdefinierte Attributdaten erfasst und an die Experience Platform gesendet werden.

### Fehlerbehebung

Wenn die Meldung `No custom order attributes found.` auf der Registerkarte **[!UICONTROL Data Customization]** angezeigt wird, bestätigen Sie Folgendes:

1. Sie haben die Voraussetzungen für die Aktivierung der [Data Connector-Erweiterung](overview.md#prerequisites) erfüllt.
1. Sie haben [benutzerdefinierte Bestellattribute](#add-custom-order-attributes) konfiguriert.
1. Es wurde mindestens ein Bestellereignis generiert.
