---
title: Manuelle Installation der SaaS-Preisindizierung
description: Installieren der SaaS-Preisindizierung für ältere Versionen
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: b2ebf26c9a34e5e2e08b7adbabcc780f24363e3c
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Manuelle Installation der SaaS-Preisindizierung

Die SaaS-Preisindizierung ist für unterstützte [neueste Version](index.md#Requirements) von Commerce Services.
Wenn Sie nicht über die neueste Version verfügen und die SaaS-Preisindizierung für Ihre Adobe Commerce-Instanz aktivieren möchten, verwenden Sie dieses Handbuch.

## Voraussetzungen

* Adobe Commerce 2.4.4+
* Mindestens einer der folgenden SaaS-Dienste installiert:

   * [Catalog Service](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Produkt-Recommendations](../product-recommendations/guide-overview.md)

## Installieren erforderlicher Module

Abhängig von Ihrer Einrichtung unterscheidet sich der Installationsprozess möglicherweise geringfügig.
Es gibt Erweiterungen, die die neuen Feeds und den unterstützenden Code hinzufügen, und es gibt eine Erweiterung, die den Feed der Standardpreise entfernt.

1. Fügen Sie die folgenden Module zu Ihrem `composer.json` Datei:

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. Führen Sie den Aktualisierungsbefehl aus:

   ```bash
   bin/magento setup:upgrade
   ```

Nach dem Upgrade sind drei neue Feeds verfügbar:

* `prices` - die für die Bereitstellung der Preisdaten an den Dienst verantwortlich ist
* `scopesCustomerGroup` - verantwortlich für die Zustellung von Kundengruppen an den Dienst
* `scopesWebsite` - verantwortlich für die Bereitstellung von Websites, Store-Gruppen und Store-Ansichten an den Dienst

1. Konfigurieren Sie die neuen Feeds, die auf den Modus &quot;Auf Zeitplan aktualisieren&quot;eingestellt werden sollen:

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Neuindizieren der neuen Feeds:

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Führen Sie die oben genannten Indexer nach Bedarf manuell aus. Andernfalls werden die Daten im standardmäßigen Synchronisierungsprozess aktualisiert. Mehr über [Katalogsynchronisierung](../landing/catalog-sync.md) -Dienst.

Benutzer von Luma und Adobe Commerce Core GraphQL können die [`Catalog Adapter`](catalog-adapter.md) -Erweiterung, die Luma- und Core-GraphQl-Kompatibilität bietet und den Adobe Commerce Product Price-Indexer deaktiviert.

## Einschränkungen

Vorher `103.0.0` -Version, SaaS-Preisindizierung unterstützt einfache, gruppierte, virtuelle, konfigurierbare und gebündelte dynamische Produktarten.
Die Unterstützung für herunterladbare, vergünstigte und gebündelte feste Produkttypen ist ab `magento/module-saas-price:103.0.0` und für unterstützte Commerce Services standardmäßig verfügbar sind.

Neue Feeds sollten manuell mit der `resync` [CLI, Befehl](../landing/catalog-sync.md#resynccmdline). Andernfalls werden die Daten im standardmäßigen Synchronisierungsprozess aktualisiert. Weitere Informationen zu [Katalogsynchronisierung](../landing/catalog-sync.md) -Prozess.
