---
title: "Installieren [!DNL Live Search]"
description: "Erfahren Sie, wie Sie installieren, aktualisieren und deinstallieren [!DNL Live Search] von Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---

# Installieren [!DNL Live Search]

Live Search wird als Erweiterung von Adobe Marketplace installiert. Nach dem [!DNL Live Search] -Modul (mit Katalogmodulen als Abhängigkeiten) installiert und konfiguriert ist, [!DNL Commerce] beginnt mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle *Admin* -Benutzer können Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

Dieses Thema enthält Anweisungen zu folgenden Aktionen:

* Installieren [!DNL Live Search] (Methoden 1 und 2)
* [Aktualisieren [!DNL Live Search]](#update)
* [Deinstallieren [!DNL Live Search]](#uninstall)

## Bevor Sie beginnen {#before-you-begin}

Gehen Sie wie folgt vor:

1. Vergewissern Sie sich, dass [Cron-Aufträge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) und [Indexer](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) laufen.

1. Wählen Sie die Integrationsmethode aus, die Ihren Anforderungen entspricht, und befolgen Sie die Anweisungen.

   * [Methode 1](#method-1): Installieren ohne [!DNL Elasticsearch]
   * [Methode 2](#method-2): Installieren mit [!DNL Elasticsearch] (Keine Ausfallzeiten)

## Methode 1: Installation ohne Elasticsearch {#method-1}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] zu a:

* Neu [!DNL Commerce] Installation
* Staging-Umgebung

In diesem Szenario werden Storefront-Vorgänge während der [!DNL Live Search] -Dienst indiziert alle Produkte im Katalog. Während der Installation [!DNL Live Search] -Module aktiviert sind und [!DNL Elasticsearch] -Module deaktiviert sind.

>[!TIP]
>
>Um Tippfehler zu vermeiden, bewegen Sie den Mauszeiger über die rechte Ecke des Codefelds und klicken Sie auf die Schaltfläche [!UICONTROL **Kopieren**] und fügen Sie ihn in die Befehlszeile ein.

1. Installieren Sie Adobe Commerce 2.4.x ohne [!DNL Live Search].

1. So laden Sie die `live-search` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

   Weitere Informationen finden Sie in der Liste der [!DNL Live Search] [dependencies](#dependencies) die von [!DNL Composer].

1. Führen Sie die folgenden Befehle aus, um zu deaktivieren [!DNL Elasticsearch] und zugehörige Module und installieren [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriedurchsuchvorgänge nicht in der Storefront verfügbar. Je nach der Größe Ihres Katalogs kann der Vorgang mindestens eine Stunde dauern `cron` läuft, um Ihre Daten zu synchronisieren [!DNL Live Search] Dienste.

1. Stellen Sie sicher, dass Folgendes [Indexer](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) auf `Update by Schedule`:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) und überprüfen Sie, ob Ihre Katalogdaten [synchronisiert](#synchronize-catalog-data) mit [!DNL Live Search] Dienste.

1. Um Facetten als Filter in der Storefront verfügbar zu machen, fügen Sie die [facets](facets-add.md) Sie benötigen die [Facettenanforderungen](facets.md).

   Sie sollten in der Lage sein, nach `cron` führt die Attributmetadaten für Feeds und Exporte aus.

1. Warten Sie mindestens eine Stunde nach `cron` wird ausgeführt, um Daten zu synchronisieren. Dann [verify](#verify-export) dass die Daten exportiert wurden.

1. [Test](#test-the-connection) die Verbindung von der Storefront.

## Methode 2: Installieren mit Elasticsearch {#method-2}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] an:

* eine bestehende Produktion [!DNL Commerce] Installation

In diesem Szenario [!DNL Elasticsearch] verwaltet vorübergehend Suchanfragen aus der Storefront, während die [!DNL Live Search] -Dienst indiziert alle Produkte im Hintergrund, ohne dass der normale Storefront-Betrieb unterbrochen wird. [!DNL Elasticsearch] ist deaktiviert und [!DNL Live Search] aktiviert, nachdem alle Katalogdaten indiziert und synchronisiert wurden.

>[!TIP]
>
>Um Tippfehler zu vermeiden, bewegen Sie den Mauszeiger über die rechte Ecke des Codefelds und klicken Sie auf die Schaltfläche [!UICONTROL **Kopieren**] und fügen Sie ihn in die Befehlszeile ein.

1. So laden Sie die `live-search` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

   Weitere Informationen finden Sie in der Liste der [!DNL Live Search] [dependencies](#live-search-dependencies) die von [!DNL Composer].

1. Führen Sie den folgenden Befehl aus, um die [!DNL Live Search] -Module, die Storefront-Suchergebnisse bereitstellen.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] verwaltet weiterhin Suchanforderungen aus dem Store, während die [!DNL Live Search] -Dienst synchronisiert Katalogdaten und indiziert Produkte im Hintergrund.

1. Stellen Sie sicher, dass Folgendes [Indexer](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) auf `Update by Schedule`:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) und überprüfen Sie, ob Ihre Katalogdaten [synchronisiert](#synchronize-catalog-data) mit [!DNL Live Search] Dienste.

1. Um Facetten als Filter in der Storefront verfügbar zu machen, fügen Sie die [facets](facets-add.md) Sie benötigen die [Facettenanforderungen](facets.md).

   Sie sollten in der Lage sein, nach `cron` führt die Produkt- und Attributfeeds aus und exportiert Attributmetadaten zu [!DNL Live Search] Dienste.

1. Warten Sie mindestens eine Stunde, bis die Daten indiziert und synchronisiert werden. Verwenden Sie dann die [GraphQL-Playground](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) mit der Standardabfrage, um Folgendes zu überprüfen:

   * Die zurückgegebene Produktanzahl entspricht in etwa dem, was Sie für die Store-Ansicht erwarten.
   * Facets werden zurückgegeben.

1. Führen Sie die folgenden Befehle aus, um [!DNL Live Search] Module, deaktivieren [!DNL Elasticsearch]und ausführen `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
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

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind erforderlich, um eine Verbindung herzustellen [!DNL Live Search] auf eine Installation von Adobe Commerce. Der API-Schlüssel wird im Konto der [!DNL Commerce] Lizenzinhaber, der sie für den Entwickler oder SI freigeben kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten.  Wenn Sie bereits über eine Reihe von API-Schlüsseln verfügen, müssen Sie diese nicht neu generieren.

### Adobe Commerce-Lizenzinhaber

Informationen zum Generieren eines API-Schlüssels und eines privaten Schlüssels finden Sie unter [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce-Entwickler oder SI

Der Entwickler oder SI konfiguriert den SaaS-Datenraum wie im Abschnitt *Commerce-Services* -Abschnitt der Konfiguration. Im *Admin*, werden die Commerce-Services im *Konfiguration* Seitenleiste, wenn ein SaaS-Modul installiert ist.

## Katalogdaten synchronisieren {#synchronize-catalog-data}

[!DNL Live Search] erfordert synchronisierte Produktdaten für Suchvorgänge und synchronisierte Attributdaten zum Konfigurieren von Facetten. Die erste Synchronisierung zwischen dem Produktkatalog und dem Katalogdienst beginnt mit dem Datum [!DNL Live Search] ist zuerst verbunden. Je nach Installationsmethode und Größe des Katalogs kann es bis zu acht Stunden dauern, bis die Daten exportiert und indiziert werden durch [!DNL Live Search]. Die Liste der mit dem Katalogdienst synchronisierten und freigegebenen Daten finden Sie im Schema, das in folgendem Verzeichnis definiert ist:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Export überprüfen {#verify-export}

So überprüfen Sie, ob die Katalogdaten aus Ihrer Adobe Commerce-Instanz exportiert wurden und für [!DNL Live Search], suchen Sie in den folgenden Tabellen nach Einträgen:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Weitere Hilfe finden Sie unter [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync.html) in der Support-Wissensdatenbank.

### Künftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu 15 Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar sind. Weitere Informationen finden Sie unter [Indizierung - Streaming von Produktaktualisierungen](indexing.md).

## Verbindung testen {#test-connection}

Überprüfen Sie Folgendes in der Storefront:

* Die [!UICONTROL Search] box gibt Ergebnisse korrekt zurück
* Kategoriesuche gibt Ergebnisse korrekt zurück
* Facets sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles korrekt funktioniert, gratulieren Sie! [!DNL Live Search] installiert, verbunden und einsatzbereit ist.

Wenn Probleme in der Storefront auftreten, überprüfen Sie die `var/log/system.log` -Datei für API-Kommunikationsfehler oder -fehler auf der Dienstseite.

## Überprüfen der installierten Version

Führen Sie vor der Aktualisierung der Live-Suche Folgendes über die Befehlszeile aus, um die derzeit installierte Live Search-Version zu überprüfen:

```bash
composer show magento/module-live-search | grep version
```

## Aktualisieren [!DNL Live Search] {#update}

Zu aktualisieren [!DNL Live Search], führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/live-search --with-dependencies
```

Um auf eine Hauptversion wie 1.0.0 auf 2.0.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

1. Wenn derzeit installiert `magento/live-search` Version ist `1.3.1` oder darunter, und Sie aktualisieren auf Version `2.0.0` oder höher führen Sie vor dem Upgrade den folgenden Befehl aus:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Informationen zu den derzeit installierten `magento/live-search` -Version, führen Sie den folgenden Befehl aus:

   ```bash
   composer show magento/live-search
   ```

1. Öffnen Sie den Stamm. `composer.json` Datei und suchen Sie nach `magento/live-search`.

1. Im `require` aktualisieren Sie die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## Deinstallation [!DNL Live Search] {#uninstall}

Deinstallation [!DNL Live Search], siehe [Module deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] packages {#packages}

| Paket | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern, ihre Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. zu konfigurieren, und bietet Zugriff auf einen schreibgeschützten GraphQL-Spielplatz, auf dem Abfragen aus dem *Admin*. |
| `module-live-search-adapter` | Routet Suchanforderungen von der Storefront zum [!DNL Live Search] und rendert die Ergebnisse in der Storefront. <br />- Kategoriesuche - Routen von Anforderungen aus der Storefront [obere Navigation](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) zum Suchdienst hinzu.<br />- Globale Suche - Routen von Anfragen von der [Schnellsuche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) in der oberen rechten Ecke des Storefront zur [!DNL Live Search] Dienst. |
| `module-live-search-storefront-popover` | Ein Popup &quot;Suche beim Eingeben&quot;ersetzt die standardmäßige Schnellsuche und gibt Daten und Miniaturansichten der Top-Suchergebnisse zurück. |

## [!DNL Live Search] dependencies {#dependencies}

Folgendes [!DNL Live Search] Abhängigkeiten werden von [!DNL Composer]:

| Abhängigkeit | Beschreibung |
|--- |--- |
| Exportmodule | Die folgenden Module erfassen und synchronisieren Katalogdaten:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Erforderlich, um Ihre Verbindung zu Commerce Services zu konfigurieren. |
| `module-services-id` | Erforderlich, um Ihre Verbindung zu Commerce Services zu konfigurieren. |
