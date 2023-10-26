---
title: SaaS-Preisindizierung
description: Verwenden der SaaS-Preisindizierung zur Leistungsverbesserung
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 3809d27fc3689519e4a162aa52f481d254aec656
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# SaaS-Preisindizierung

Die SaaS-Preisindizierung beschleunigt die Zeit, die für Preisänderungen benötigt wird, um sie widerzuspiegeln. [Commerce-Services](../landing/saas.md) nachdem sie eingereicht wurden. So können Händler mit großen, komplexen Katalogen oder mit mehreren Websites oder Kundengruppen Preisänderungen kontinuierlich verarbeiten.
Wenn Sie eine Headless-Storefront haben oder die [catalog-adapter](./catalog-adapter.md) -Erweiterung verwenden, können Kunden den Adobe Commerce-Core-Preisindex deaktivieren.

Rechenintensive Prozesse wie Indizierung und Preisberechnung wurden vom Commerce-Kern in die Adobe Cloud-Infrastruktur verschoben. Dadurch können Händler Ressourcen schnell skalieren, um die Indexierungszeiten zu erhöhen und diese Änderungen schneller widerzuspiegeln.

Der Datenfluss der Core-Indizierung zu SaaS-Diensten sieht wie folgt aus:

![Standarddatenfluss](assets/old_way.png)

Bei SaaS-Preisindizierung lautet der Fluss:

![Datenfluss der SaaS-Preisindizierung](assets/new_way.png)

Alle Händler können von diesen Verbesserungen profitieren, aber diejenigen, die die größten Gewinne erzielen, sind Kunden mit:

* Konstante Preisänderungen: Händler, die wiederholte Preisänderungen erfordern, um strategische Ziele wie häufige Promotions, saisonale Rabatte oder Inventarmarkdowns zu erreichen.
* Mehrere Websites und/oder Kundengruppen: Händler mit freigegebenen Produktkatalogen über mehrere Websites (Domänen/Marken) und/oder Kundengruppen hinweg.
* Große Anzahl einzigartiger Preise für Websites oder Kundengruppen: Händler mit umfangreichen gemeinsam genutzten Produktkatalogen, die individuelle Preise für Websites oder Kundengruppen enthalten, wie B2B-Händler mit vorab ausgehandelten Preisen, Marken mit unterschiedlichen Preisstrategien.

Die SaaS-Preisindizierung ist für Kunden, die Adobe Commerce-Dienste verwenden, kostenlos verfügbar und unterstützt die Preisberechnung für alle integrierten Adobe Commerce-Produktarten.

In diesem Mini-Handbuch wird beschrieben, wie die SaaS-Preisindizierung funktioniert und wie sie aktiviert wird.

## Voraussetzungen

* Adobe Commerce 2.4.4+
* Mindestens einer der folgenden Commerce-Dienste mit der neuesten Version der Adobe Commerce-Erweiterung:

   * [Catalog Service](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Produkt-Recommendations](../product-recommendations/guide-overview.md)

Benutzer von Luma und Adobe Commerce Core GraphQL können die [`catalog-adapter`](catalog-adapter.md) -Erweiterung, die Luma- und Core-GraphQl-Kompatibilität bietet und den Adobe Commerce Product Price-Indexer deaktiviert.

## Nutzung

Synchronisieren Sie nach dem Upgrade Ihrer Adobe Commerce-Instanz mit SaaS-Preisindizierungsunterstützung die neuen Feeds:

```
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Preise für benutzerdefinierte Produktarten

Preisberechnungen werden für benutzerdefinierte Produktarten wie Basispreis, Sonderpreis, Gruppenpreis, Katalogregelpreis usw. unterstützt.

Wenn Sie über einen benutzerdefinierten Produkttyp verfügen, der eine bestimmte Formel zur Berechnung des Endpreises verwendet, können Sie das Verhalten des Produktpreis-Feeds erweitern.

## Nutzung

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

Neue Feeds sollten manuell mit der `resync` [CLI, Befehl](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Andernfalls werden die Daten im standardmäßigen Synchronisierungsprozess aktualisiert. Weitere Informationen zu [Katalogsynchronisierung](../landing/catalog-sync.md) -Prozess.

## Nutzungsszenarien

### Luma ohne Erweiterungsabhängigkeiten

* Ein Luma- oder Adobe Commerce Core GraphQL-Händler, der einen erforderlichen Dienst installiert hat (Live Search, Product Recommendations, Catalog Service)
* Keine Drittanbietererweiterungen, die auf den PHP Core-Preisindex angewiesen sind
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren.
1. Installieren Sie den Katalogadapter.

### Grundlegende GraphQl-Abhängigkeiten von Luma und Adobe Commerce mit PHP-Kernpreisindizes

* Ein Luma- oder Adobe Commerce Core GraphQL-Händler, der einen unterstützten Dienst installiert hat (Live Search, Product Recommendations, Catalog Service)
* Mit einer Drittanbietererweiterung, die auf den PHP-Core-Preisindex angewiesen ist
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren
1. Installieren Sie den Katalogadapter.
1. Aktivieren Sie den PHP Core-Preisindex erneut.
1. Verwenden Sie neue Feeds und den Luma-Kompatibilitätscode im `catalog-adapter` -Modul.

### Headless-Händler

* Ein Headless-Händler, der einen unterstützten Dienst installiert hat (Live Search, Product Recommendations, Catalog Service)
* Keine Abhängigkeit von PHP Core-Preisindex
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren
1. Installieren Sie den Katalog-Adapter, der den PHP Core-Preisindex deaktiviert.

## Benutzerspezifische Preise

Der SaaS-Preisindexer unterstützt in der Adobe Commerce verfügbare, benutzerdefinierte Produkttyppreisfunktionen wie Sonderpreise, Gruppenpreise und Katalogregelpreis.

Beispiel: Es gibt einen benutzerdefinierten Produkttyp  `custom_type` und ein Produkt mit der SKU &quot;Custom Type Product&quot;.

Standardmäßig sendet die Commerce Data Export-Erweiterung den folgenden Preis-Feed an den Preisindexer:

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

Wenn &quot;Benutzerdefinierter Produkttyp&quot;eine eindeutige Formel zur Berechnung des Produktpreises verwendet, können Systemintegratoren die Preis- und Rabattfelder überschreiben, indem sie die Erweiterung &quot;Commerce Data Export&quot;erweitern.

1. Erstellen Sie ein Plug-in im `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` -Klasse.

`di.xml` Datei:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. Erstellen Sie eine Methode mit der benutzerdefinierten Formel:

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
