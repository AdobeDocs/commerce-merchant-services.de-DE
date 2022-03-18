---
title: Live Search installieren
description: Erfahren Sie, wie Sie Live Search über Adobe Commerce installieren, aktualisieren und deinstallieren.
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 0%

---

# Installieren [!DNL Live Search]

[!DNL Live Search] ist ein Satz eigenständiger [packages](#live-search-packages) ersetzt die standardmäßigen Magento Open Source- und Adobe Commerce-Suchfunktionen. Die [!DNL Live Search] -Modul wird über die Befehlszeile des Servers installiert und stellt eine Verbindung zu Ihrer Adobe Commerce-Installation als [service](https://docs.magento.com/user-guide/system/saas.html). Wenn der Prozess abgeschlossen ist, [!DNL Live Search] wird auf der *Marketing* Menü unter *SEO und Suche* im [!DNL Commerce] Admin.

Auf der Adobe Commerce-Seite finden Sie das Hosten des Suchadministrators, das Synchronisieren von Katalogdaten und das Ausführen des Abfragedienstes.

![Architekturdiagramm der Live-Suche](assets/architecture-diagram.svg)

Nach dem [!DNL Live Search] -Modul (mit Katalogmodulen als Abhängigkeiten) installiert und konfiguriert ist, [!DNL Commerce] beginnt mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Admin-Benutzer Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

Dieses Thema enthält Anweisungen zu folgenden Aktionen:

* [Installieren [!DNL Live Search]](#before-you-begin) (Methoden 1 und 2)
* [Aktualisieren [!DNL Live Search]](#update)
* [Deinstallieren [!DNL Live Search]](#uninstall)

## Voraussetzungen {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Unterstützte Plattformen

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Grenzen und Schwellenwerte

Derzeit hat die Live Search-Kategoriesuche/-Kategorie-API die folgenden unterstützten Einschränkungen und statischen Begrenzungen:

### Indizierung

* Indexiert bis zu 300 Produktattribute pro Store-Ansicht
* Indexiert nur Produkte aus der Adobe Commerce-Datenbank
* Indexiert keine CMS-Seiten

### Funktionalität

* Storefront [Erweiterte Suche (Formular)](https://docs.magento.com/user-guide/catalog/search-advanced.html) Modul
* [Kundengruppen](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Benutzerspezifische Preisgruppen](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Mehrere Lagerorte, die von [MCOM](https://docs.magento.com/user-guide/mcom.html) oder anderen OMS-Erweiterungen
* [Integrierte B2B-Funktionen](https://business.adobe.com/products/magento/b2b-ecommerce.html)

### Abfragen

* Die Live-Suche hat keinen Zugriff auf die vollständige Taxonomie des Kategoriebaums, wodurch einige Navigationsszenarien mit Ebenen über ihre Reichweite hinausgehen.
* Die Live-Suche verwendet einen eindeutigen GraphQL-Endpunkt für Abfragen, um Funktionen wie intelligente Facettierung und Suche nach dem eigenen Typ zu unterstützen. Obwohl ähnlich der [Magento GraphQL-API](https://devdocs.magento.com/guides/v2.4/graphql), gibt es einige Unterschiede und einige Felder sind derzeit möglicherweise nicht vollständig kompatibel.

### Progressive Web Application (PWA)

* Live Search unterstützt nicht [PWA](https://developer.adobe.com/commerce/pwa-studio/) zu diesem Zeitpunkt.

## Bevor Sie beginnen {#before-you-begin}

Gehen Sie wie folgt vor:

1. Vergewissern Sie sich, dass [Cron-Aufträge](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) und [Indexer](https://docs.magento.com/user-guide/system/index-management.html) laufen.

1. Wählen Sie die Integrationsmethode aus, die Ihren Anforderungen entspricht, und befolgen Sie die Anweisungen.

   * [Methode 1](#method-1): Installieren ohne [!DNL Elasticsearch]
   * [Methode 2](#method-2): Installieren mit [!DNL Elasticsearch] (Keine Ausfallzeiten)

   >[!TIP]
   >
   >Um Anweisungen in die Befehlszeile einzugeben, bewegen Sie den Mauszeiger über die rechte Ecke des Codefelds und klicken Sie auf [!UICONTROL **Kopieren**] Link. Fügen Sie es dann in die Befehlszeile ein. Wenn Sie keine Erfahrung mit der Arbeit über die Befehlszeile haben, bitten Sie Ihren Systemintegrator oder Entwickler um Hilfe.

## Methode 1: Installation ohne Elasticsearch {#method-1}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] zu a:

* Neu [!DNL Commerce] Installation
* Staging-Umgebung

In diesem Szenario werden Storefront-Vorgänge während der [!DNL Live Search] -Dienst indiziert alle Produkte im Katalog. Während der Installation [!DNL Live Search] -Module aktiviert sind und [!DNL Elasticsearch] -Module deaktiviert sind.

1. Installieren Sie Adobe Commerce 2.4.x ohne [!DNL Live Search].

1. So laden Sie die `live-search` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/DNL live-search
   ```

   Weitere Informationen finden Sie in der Liste der [!DNL Live Search] [dependencies](#dependencies) die von [!DNL Composer].

1. Führen Sie die folgenden Befehle aus, um zu deaktivieren [!DNL Elasticsearch] und zugehörige Module und installieren [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch  Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriedurchsuchvorgänge nicht in der Storefront verfügbar. Je nach der Größe Ihres Katalogs kann der Vorgang mindestens eine Stunde dauern `cron` läuft, um Ihre Daten zu synchronisieren [!DNL Live Search] Dienste.

1. Stellen Sie sicher, dass Folgendes [Indexer](https://docs.magento.com/user-guide/system/index-management.html) auf `Update by Schedule`:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) nach [synchronisieren](#synchronize-catalog-data) Ihre Katalogdaten an [!DNL Live Search] Dienste.

1. Um Facetten als Filter in der Storefront verfügbar zu machen, fügen Sie die [facets](https://docs.magento.com/user-guide/live-search/facets-add.html) Sie benötigen die [Facettenanforderungen](https://docs.magento.com/user-guide/live-search/facets.html).

   Sie sollten in der Lage sein, nach `cron` führt die Attributmetadaten für Feeds und Exporte aus.

1. Warten Sie mindestens eine Stunde nach `cron` wird ausgeführt, um Daten zu synchronisieren. Dann [verify](#verify-export) dass die Daten exportiert wurden.

1. [Test](#test-the-connection) die Verbindung von der Storefront.

## Methode 2: Installieren mit Elasticsearch {#method-2}

Diese Onboarding-Methode wird bei der Installation von [!DNL Live Search] an:

* eine bestehende Produktion [!DNL Commerce] Installation

In diesem Szenario [!DNL Elasticsearch] verwaltet vorübergehend Suchanfragen aus der Storefront, während die [!DNL Live Search] -Dienst indiziert alle Produkte im Hintergrund, ohne dass der normale Storefront-Betrieb unterbrochen wird. [!DNL Elasticsearch] ist deaktiviert und [!DNL Live Search] aktiviert, nachdem alle Katalogdaten indiziert und synchronisiert wurden.

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

1. Stellen Sie sicher, dass Folgendes [Indexer](https://docs.magento.com/user-guide/system/index-management.html) auf `Update by Schedule`:

   * Produkt-Feed
   * Produktvarianten-Feed
   * Katalogattribut-Feed

1. Konfigurieren Sie Ihre [API-Schlüssel](#configure-api-keys) nach [synchronisieren](#synchronize-catalog-data) Ihre Katalogdaten an [!DNL Live Search] Dienste.

1. Um Facetten als Filter in der Storefront verfügbar zu machen, fügen Sie die [facets](https://docs.magento.com/user-guide/live-search/facets-add.html) Sie benötigen die [Facettenanforderungen](https://docs.magento.com/user-guide/live-search/facets.html).

   Sie sollten in der Lage sein, nach `cron` führt die Produkt- und Attributfeeds aus und exportiert Attributmetadaten zu [!DNL Live Search] Dienste.

1. Warten Sie mindestens eine Stunde, bis die Daten indiziert und synchronisiert werden. Verwenden Sie dann die [GraphQL-Playground](https://devdocs.magento.com/live-search/graphql-support.html) mit der Standardabfrage, um Folgendes zu überprüfen:

   * Die zurückgegebene Produktanzahl entspricht in etwa dem Wert, den Sie für die Store-Ansicht erwarten
   * Facets werden zurückgegeben

1. Führen Sie die folgenden Befehle aus, um zu deaktivieren [!DNL Elasticsearch] Module, aktivieren [!DNL Live Search] Module und ausführen `setup`:

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Test](#test-the-connection) die Verbindung von der Storefront.

## API-Schlüssel konfigurieren {#configure-api-keys}

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind erforderlich, um eine Verbindung herzustellen [!DNL Live Search] auf eine Installation von Adobe Commerce. Der API-Schlüssel wird im Konto der [!DNL Commerce] Lizenzinhaber, der sie für den Entwickler oder SI freigeben kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten.

### Adobe Commerce-Lizenzinhaber

Informationen zum Generieren eines API-Schlüssels und eines privaten Schlüssels finden Sie unter [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html).

### Adobe Commerce-Entwickler oder SI

Der Entwickler oder SI konfiguriert den SaaS-Datenraum, wie im Abschnitt Commerce Services der Konfiguration beschrieben. Commerce Services wird in der Seitenleiste &quot;Admin-Konfiguration&quot;verfügbar, wenn ein SaaS-Modul installiert ist.

## Katalogdaten synchronisieren {#synchronize-catalog-data}

[!DNL Live Search] erfordert synchronisierte Produktdaten für Suchvorgänge und synchronisierte Attributdaten zum Konfigurieren von Facetten. Die erste Synchronisierung zwischen dem Produktkatalog und dem Katalogdienst beginnt mit dem Datum [!DNL Live Search] ist zuerst verbunden. Je nach Installationsmethode und Größe des Katalogs kann es bis zu acht Stunden dauern, bis die Daten exportiert und indiziert werden durch [!DNL Live Search]. Die Liste der mit dem Katalogdienst synchronisierten und freigegebenen Daten finden Sie im Schema, das in folgendem Verzeichnis definiert ist:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Export überprüfen {#verify-export}

So überprüfen Sie, ob die Katalogdaten aus Ihrer Adobe Commerce-Instanz exportiert wurden und für [!DNL Live Search], suchen Sie in den folgenden Tabellen nach Einträgen:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Weitere Hilfe finden Sie unter [[!DNL Live Search] Katalog nicht synchronisiert](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) in der Support-Wissensdatenbank.

### Künftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu fünfzehn Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar sind. Weitere Informationen finden Sie unter [Streaming-Produktaktualisierungen](https://devdocs.magento.com/live-search/indexing.html).

## Verbindung testen {#test-connection}

Überprüfen Sie Folgendes in der Storefront:

* Die [!UICONTROL Search] box gibt Ergebnisse korrekt zurück
* Kategoriesuche gibt Ergebnisse korrekt zurück
* Facets sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles korrekt funktioniert, gratulieren Sie! [!DNL Live Search] installiert, verbunden und einsatzbereit ist.

Wenn Probleme in der Storefront auftreten, überprüfen Sie die `var/log/system.log` -Datei für API-Kommunikationsfehler oder -fehler auf der Dienstseite.

## Aktualisieren [!DNL Live Search] {#update}

Zu aktualisieren [!DNL Live Search], führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/live-search --with-dependencies
```

Um auf eine Hauptversion wie 1.0 auf 2.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

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

Deinstallation [!DNL Live Search], siehe [Module deinstallieren](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] packages {#packages}

| Paket | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern, ihre Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. zu konfigurieren, und bietet Zugriff auf einen schreibgeschützten GraphQL-Player zum Testen von Abfragen vom Administrator. |
| `module-live-search-adapter` | Routet Suchanforderungen von der Storefront zum [!DNL Live Search] und rendert die Ergebnisse in der Storefront. <br />- Kategoriesuche - Routen von Anforderungen aus der Storefront [obere Navigation](https://docs.magento.com/user-guide/catalog/navigation-top.html) zum Suchdienst hinzu.<br />- Globale Suche - Routen von Anfragen von der [Schnellsuche](https://docs.magento.com/user-guide/catalog/search-quick.html) in der oberen rechten Ecke des Storefront zur [!DNL Live Search] Dienst. |
| `module-live-search-storefront-popover` | Ein Popup &quot;Suche beim Eingeben&quot;ersetzt die standardmäßige Schnellsuche und gibt dynamische Produktvorschläge und Miniaturansichten der Top-Suchergebnisse zurück. |

## [!DNL Live Search] dependencies {#dependencies}

Folgendes [!DNL Live Search] Abhängigkeiten werden von [!DNL Composer]:

| Abhängigkeit | Beschreibung |
|--- |--- |
| Exportmodule | Die folgenden Module erfassen und synchronisieren Katalogdaten:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Erforderlich, um Ihre Verbindung zu Commerce Services zu konfigurieren. |
| `module-services-id` | Erforderlich, um Ihre Verbindung zu Commerce Services zu konfigurieren. |
