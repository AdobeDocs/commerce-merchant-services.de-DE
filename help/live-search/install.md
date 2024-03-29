---
title: "Installieren [!DNL Live Search]"
description: "Erfahren Sie, wie Sie installieren, aktualisieren und deinstallieren [!DNL Live Search] von Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# Installieren [!DNL Live Search]

[!DNL Live Search] wird als Erweiterung von Adobe Marketplace installiert. Nach dem [!DNL Live Search] -Modul (mit Katalogmodulen als Abhängigkeiten) installiert und konfiguriert ist, [!DNL Commerce] beginnt mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle *Admin* -Benutzer können Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

Dieses Thema enthält Anweisungen zu folgenden Aktionen:

* Installieren [!DNL Live Search] (Methoden 1 und 2)
* [Aktualisieren [!DNL Live Search]](#update)
* [Deinstallieren [!DNL Live Search]](#uninstall)

## Bevor Sie beginnen {#before-you-begin}

Gehen Sie wie folgt vor:

1. Bestätigen Sie, dass [Cron-Aufträge](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) und [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) laufen.

1. Wählen Sie die Integrationsmethode aus, die Ihren Anforderungen entspricht, und befolgen Sie die Anweisungen.

   * [Methode 1](#method-1): Installieren ohne [!DNL OpenSearch]
   * [Methode 2](#method-2): Installieren mit [!DNL OpenSearch] (Keine Ausfallzeiten)

>[!IMPORTANT]
>
>Aufgrund der Ankündigung zum Ende der Unterstützung für Elasticsearch 7 vom August 2023 wird empfohlen, dass alle Adobe Commerce-Kunden zur OpenSearch 2.x-Suchmaschine migrieren. Informationen zur Migration Ihrer Suchmaschine während der Produktaktualisierung finden Sie unter [Migration zu OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) im _Upgrade-Handbuch_.

## Methode 1: Installieren ohne OpenSearch {#method-1}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] zu a:

* Neu [!DNL Commerce] Installation
* Staging-Umgebung

In diesem Szenario werden Storefront-Vorgänge während der [!DNL Live Search] -Dienst indiziert alle Produkte im Katalog. Während der Installation [!DNL Live Search] -Module aktiviert sind und [!DNL OpenSearch] -Module deaktiviert sind.

1. Installieren Sie Adobe Commerce 2.4.4+ ohne [!DNL Live Search].

1. So laden Sie die `live-search` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

1. Führen Sie die folgenden Befehle aus, um zu deaktivieren [!DNL OpenSearch] und zugehörige Module und installieren [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriedurchsuchvorgänge nicht in der Storefront verfügbar. Je nach der Größe Ihres Katalogs kann der Vorgang mindestens eine Stunde dauern. `cron` läuft, um Ihre Daten zu synchronisieren [!DNL Live Search] Dienste.

1. Stellen Sie sicher, dass Folgendes [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt sind:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed
   * Produktpreis-Feed
   * Bereich Website-Daten-Feed
   * Umfang des Daten-Feeds für Kundengruppen
   * Kategorien-Feed
   * Kategorieberechtigungs-Feed

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) und überprüfen Sie, ob Ihre Katalogdaten [synchronisiert](#synchronize-catalog-data) mit [!DNL Live Search] Dienste.

1. Um Facetten als Filter im Storefront verfügbar zu machen, fügen Sie die [facets](facets-add.md) Sie benötigen je nach [Facettenanforderungen](facets.md).

   Sie sollten in der Lage sein, nach `cron` führt die Attributmetadaten für Feeds und Exporte aus.

1. Führen Sie den folgenden Befehl in dieser Reihenfolge aus:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [Überprüfen](#verify-export) dass die Daten exportiert wurden.

1. [Test](#test-the-connection) die Verbindung von der Storefront.

## Methode 2: Installieren mit OpenSearch {#method-2}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] an:

* eine bestehende Produktion [!DNL Commerce] Installation

In diesem Szenario [!DNL OpenSearch] verwaltet vorübergehend Suchanfragen aus der Storefront, während die [!DNL Live Search] -Dienst indiziert alle Produkte im Hintergrund, ohne dass der normale Storefront-Betrieb unterbrochen wird. [!DNL OpenSearch] ist deaktiviert und [!DNL Live Search] aktiviert, nachdem alle Katalogdaten indiziert und synchronisiert wurden.

1. So laden Sie die `live-search` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

1. Führen Sie den folgenden Befehl aus, um die [!DNL Live Search] -Module, die Storefront-Suchergebnisse bereitstellen.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] verwaltet weiterhin Suchanforderungen aus dem Store, während die [!DNL Live Search] -Dienst synchronisiert Katalogdaten und indiziert Produkte im Hintergrund.

1. Stellen Sie sicher, dass Folgendes [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt sind:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed
   * Produktpreis-Feed
   * Umfang des Website-Daten-Feeds
   * Umfang des Daten-Feeds von Kundengruppen

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) und überprüfen Sie, ob Ihre Katalogdaten [synchronisiert](#synchronize-catalog-data) mit [!DNL Live Search] Dienste.

1. Um Facetten als Filter im Storefront verfügbar zu machen, fügen Sie die [facets](facets-add.md) Sie benötigen je nach [Facettenanforderungen](facets.md).

   Sie sollten in der Lage sein, nach `cron` führt die Produkt- und Attributfeeds aus und exportiert Attributmetadaten zu [!DNL Live Search] Dienste.

1. Führen Sie den folgenden Befehl in dieser Reihenfolge aus:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. Nachdem die Synchronisierung abgeschlossen ist, verwenden Sie die [GraphQL-Playground](https://developer.adobe.com/commerce/services/graphql/live-search/) mit der Standardabfrage, um Folgendes zu überprüfen:

   * Die zurückgegebene Produktanzahl entspricht in etwa dem, was Sie für die Store-Ansicht erwarten.
   * Facets werden zurückgegeben.

1. Führen Sie die folgenden Befehle aus, um [!DNL Live Search] Module, deaktivieren [!DNL OpenSearch]und ausführen `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Test](#test-the-connection) die Verbindung von der Storefront.

## API-Schlüssel konfigurieren {#configure-api-keys}

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind für die Verbindung erforderlich. [!DNL Live Search] auf eine Installation von Adobe Commerce. Der API-Schlüssel wird im Konto der [!DNL Commerce] Lizenzinhaber, der sie für den Entwickler oder SI freigeben kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten.  Wenn Sie bereits über eine Reihe von API-Schlüsseln verfügen, müssen Sie diese nicht neu generieren.

### Adobe Commerce-Lizenzinhaber

Informationen zum Generieren eines API-Schlüssels und eines privaten Schlüssels finden Sie unter [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce-Entwickler oder SI

Der Entwickler oder SI konfiguriert den SaaS-Datenraum wie im Abschnitt *Commerce-Services* -Abschnitt der Konfiguration. Im *Admin*, werden die Commerce-Services im *Konfiguration* Seitenleiste, wenn ein SaaS-Modul installiert ist.

## Katalogdaten synchronisieren {#synchronize-catalog-data}

[!DNL Live Search] erfordert synchronisierte Produktdaten für Suchvorgänge und synchronisierte Attributdaten zum Konfigurieren von Facetten. Die erste Synchronisierung zwischen dem Produktkatalog und dem Katalogdienst beginnt mit dem Datum [!DNL Live Search] ist zuerst verbunden. Je nach Installationsmethode und Größe des Katalogs kann es bis zu 30 Minuten dauern, bis die Daten exportiert und indiziert werden durch [!DNL Live Search]. Die Liste der mit dem Katalogdienst synchronisierten und freigegebenen Daten finden Sie im Schema, das in folgendem Verzeichnis definiert ist:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Export überprüfen {#verify-export}

So überprüfen Sie, ob die Katalogdaten aus Ihrer Adobe Commerce-Instanz exportiert wurden und synchronisiert werden für [!DNL Live Search], suchen Sie in den folgenden Tabellen nach Einträgen:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Weitere Hilfe finden Sie unter [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in der Support-Wissensdatenbank.

### Zukünftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu 15 Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar sind. Weitere Informationen finden Sie unter [Indizierung - Streaming von Produktaktualisierungen](indexing.md).

## Verbindung testen {#test-connection}

Überprüfen Sie Folgendes in der Storefront:

* Die [!UICONTROL Search] box gibt Ergebnisse korrekt zurück
* Kategoriesuche gibt Ergebnisse korrekt zurück
* Facets sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles korrekt funktioniert, gratulieren Sie! [!DNL Live Search] installiert, verbunden und einsatzbereit ist.

Wenn Probleme in der Storefront auftreten, überprüfen Sie die `var/log/system.log` -Datei für API-Kommunikationsfehler oder -fehler auf der Dienstseite.

Um die Live-Suche über eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste.

## Überprüfen der installierten Version

Führen Sie vor der Aktualisierung der Live Search-Suche Folgendes über die Befehlszeile aus, um die installierte Live Search-Version zu überprüfen:

```bash
composer show magento/module-live-search | grep version
```

## Aktualisieren [!DNL Live Search] {#update}

Zu aktualisieren [!DNL Live Search], führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/live-search --with-dependencies
```

Um auf eine Hauptversion wie 3.1.1 auf 4.0.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

1. Wenn derzeit installiert `magento/live-search` Version ist `3.1.1` und Sie aktualisieren auf Version `4.0.0` oder höher führen Sie vor dem Upgrade den folgenden Befehl aus:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Informationen zu den derzeit installierten `magento/live-search` -Version, führen Sie den folgenden Befehl aus:

   ```bash
   composer show magento/live-search
   ```

1. Öffnen Sie den Stamm `composer.json` Datei und suchen Sie nach `magento/live-search`.

1. Im `require` aktualisieren Sie die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Deinstallation [!DNL Live Search] {#uninstall}

Deinstallation [!DNL Live Search], siehe [Module deinstallieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

| Paket | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern, ihre Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. zu konfigurieren, und bietet Zugriff auf einen schreibgeschützten GraphQL-Spielplatz, auf dem Abfragen aus dem *Admin*. |
| `module-live-search-adapter` | Routet Suchanforderungen von der Storefront zum [!DNL Live Search] und rendert die Ergebnisse in der Storefront. <br />- Kategoriesuche - Routen von Anforderungen aus der Storefront [oberste Navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) zum Suchdienst hinzu.<br />- Globale Suche - Routen von Anfragen von der [Schnellsuche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) in der oberen rechten Ecke des Storefront zur [!DNL Live Search] -Dienst. |
| `module-live-search-storefront-popover` | Ein Popup &quot;Suche beim Eingeben&quot;ersetzt die standardmäßige Schnellsuche und gibt Daten und Miniaturansichten der Top-Suchergebnisse zurück. |

## [!DNL Live Search] dependencies {#dependencies}

Die folgenden [!DNL Live Search] Abhängigkeiten werden von [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
