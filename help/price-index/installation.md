---
title: Installation der SaaS-Preisindizierung
description: Installieren der SaaS-Preisindizierung
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Installation der SaaS-Preisindizierung

Für die Einrichtung der SaaS-Preisindizierung müssen neue Module installiert und CLI-Befehle ausgeführt werden. Administratoren benötigen Befehlszeilenzugriff, um diese Installation abzuschließen.

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
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
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

Führen Sie die oben genannten Indexer nach Bedarf manuell aus. Andernfalls werden die Daten im standardmäßigen Synchronisierungsprozess aktualisiert. Mehr über [Katalogsynchronisierung](../landing/catalog-sync.md) Dienst.

Benutzer von Luma und Adobe Commerce Core GraphQL können die `catalog-adapter` -Modul, das Luma- und Core-GraphQl-Kompatibilität bietet und den PHP Core-Preisindex deaktiviert.
So verwenden Sie die `catalog-adapter` Modul, [!DNL Live Search] und [!DNL Catalog Service] muss zuerst installiert und konfiguriert werden. Befolgen Sie die [Installieren [!DNL Live Search]](../live-search/install.md) und [Installation des Katalogdienstes](../catalog-service/installation.md) Anweisungen vor dem Fortfahren.

Gehen Sie wie folgt vor, um die Live-Suche und den Katalog-Adapter zu konfigurieren [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) Anweisungen.

```bash
composer require adobe-commerce/catalog-adapter
```

Bei Bedarf kann der PHP Core-Preisindex mit dem folgenden Befehl reaktiviert werden:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
