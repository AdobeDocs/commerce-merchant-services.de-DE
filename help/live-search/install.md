---
title: "Erste Schritte mit [!DNL Live Search]"
description: "Erfahren Sie mehr über die Systemanforderungen und Installationsschritte für [!DNL Live Search] von Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: eb9835c7681041abbcc6d1ece91e74bafe343d82
workflow-type: tm+mt
source-wordcount: '2396'
ht-degree: 0%

---

# Für einen erfolgreichen Einsatz mit [!DNL Live Search]

Adobe Commerce [!DNL Live Search] und [[!DNL Catalog Service]](../catalog-service/guide-overview.md) arbeiten Sie zusammen, um eine leistungsfähige, relevante und intuitive Suchlösung bereitzustellen, mit der Ihre Kunden schnell genau das finden können, was sie benötigen. Insbesondere gilt: [!DNL Catalog Service] oberflächert Ihre Katalogdaten für SaaS-Dienste, z. B. [!DNL Live Search] verwendet werden.

Dieser Artikel enthält schrittweise Anweisungen zur Implementierung von [!DNL Live Search] mit [!DNL Catalog Service].

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Lesen Sie unbedingt [Grenzen und Grenzen](boundaries-limits.md) vor der Umsetzung [!DNL Live Search] ist für Ihre Geschäftsanforderungen geeignet.

## Zielgruppe

Dieser Artikel richtet sich an Entwickler oder Systemintegratoren in Ihrem Team, die für die Installation und Konfiguration Ihrer Adobe Commerce-Instanz zuständig sind.

## Voraussetzungen

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## Unterstützte Plattformen

- Adobe Commerce on Cloud (ECE) : 2.4.4+
- Adobe Commerce On-Premise (EE) : 2.4.4+

## Workflow-Übersicht

Onboarding auf hoher Ebene [!DNL Live Search] erfordert, dass Sie:

- Installieren der Erweiterung
- API-Schlüssel konfigurieren
- Katalogdaten synchronisieren
- Überprüfen, ob die Daten exportiert wurden
- Daten konfigurieren
- Verbindung testen
- Benutzerspezifisch für Ihre Storefront

![Live Search-Workflow](assets/livesearch-workflow.png)

## 1. Installieren Sie die [!DNL Live Search] Erweiterung

[!DNL Live Search] wird als Erweiterung von installiert. [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) bis [Verfasser](https://getcomposer.org/). Nach der Installation und Konfiguration [!DNL Live Search], ADOBE [!DNL Commerce] beginnt mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle *Admin* -Benutzer können Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

>[!NOTE]
>
>Als [!DNL Live Search] 3.0.2, die [!DNL Catalog Service] -Erweiterung wird mit der [!DNL Live Search] Installation.

1. Bestätigen Sie, dass [Cron-Aufträge](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) und [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) laufen.

   >[!IMPORTANT]
   >
   >Aufgrund der Ankündigung zum Ende der Unterstützung für Elasticsearch 7 vom August 2023 wird empfohlen, dass alle Adobe Commerce-Kunden zur OpenSearch 2.x-Suchmaschine migrieren. Informationen zur Migration Ihrer Suchmaschine während eines Produkt-Upgrades finden Sie unter [Migration zu OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) im _Upgrade-Handbuch_.

1. Laden Sie die `live-search` -Paket aus [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

   Wenn Sie die Variable [!DNL Live Search] Erweiterung auf **new** Führen Sie zur Deaktivierung der Adobe Commerce-Installation Folgendes aus [!DNL OpenSearch] und zugehörige Module und installieren [!DNL Live Search]. Fahren Sie dann mit Schritt 4 fort.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Wenn Sie die Variable [!DNL Live Search] Erweiterung auf eine **vorhandene** Führen Sie die folgenden Schritte aus, um die Adobe Commerce-Installation vorübergehend zu deaktivieren [!DNL Live Search] -Module, die Storefront-Suchergebnisse bereitstellen. Fahren Sie dann mit Schritt 4 fort:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] verwaltet weiterhin Suchanforderungen aus dem Store, während die [!DNL Live Search] -Dienst synchronisiert Katalogdaten und indiziert Produkte im Hintergrund.

1. Führen Sie Folgendes aus:

   ```bash
   bin/magento setup:upgrade
   ```

1. Stellen Sie sicher, dass Folgendes [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt sind:

   - Produkt-Feed
   - Produktvarianten-Feed
   - Katalogattribut-Feed
   - Produktpreis-Feed
   - Umfang des Website-Daten-Feeds
   - Umfang des Daten-Feeds für Kundengruppen
   - Kategorien-Feed
   - Kategorieberechtigungs-Feed

1. Wenn Sie die [!DNL Live Search] In einer neuen Commerce-Instanz sind Sie fertig und können zum [2. API-Schlüssel konfigurieren](#2-configure-api-keys) Abschnitt. Wenn Sie die Live-Suche in einer vorhandenen Commerce-Instanz installieren, fahren Sie mit dem nächsten Schritt fort.

1. Führen Sie die folgenden Befehle aus, um die [!DNL Live Search] Erweiterung, deaktivieren [!DNL OpenSearch]und ausführen `setup`.

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

## 2. API-Schlüssel konfigurieren

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind für die Verbindung erforderlich. [!DNL Live Search] auf eine Installation von Adobe Commerce. Der API-Schlüssel wird im Konto der [!DNL Commerce] Lizenzinhaber, der sie für Entwickler oder Systemintegratoren freigeben kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten. Wenn Sie bereits über eine Reihe von API-Schlüsseln verfügen, müssen Sie diese nicht neu generieren.

Erfahren Sie, wie Sie Ihre API-Schlüssel im Abschnitt [Commerce Services Connector](../landing/saas.md) Artikel.

## 3. Ihre Katalogdaten synchronisieren {#synchronize-catalog-data}

[!DNL Live Search] verschiebt Katalogdaten in die Adobe SaaS-Infrastruktur. Die Daten werden indiziert und die Suchergebnisse werden von diesem Index direkt an die Storefront übermittelt. Je nach Größe und Komplexität kann die Indizierung zwischen 30 Minuten und einigen Stunden dauern.

Um die erste Synchronisierung Ihrer Katalogdaten mit SaaS-Diensten zu starten, führen Sie die folgenden Befehle in dieser Reihenfolge aus:

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

Wenn Sie diese Befehle ausführen, beginnt die erste Synchronisierung Ihrer Katalogdaten mit SaaS-Diensten.

>[!WARNING]
>
> Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriedurchsuchvorgänge nicht in der Storefront verfügbar. Je nach der Größe Ihres Katalogs kann der Vorgang mindestens eine Stunde dauern. `cron` wird ausgeführt, um Ihre Daten mit SaaS-Diensten zu synchronisieren.

### Fortschritt der Synchronisierung überwachen

Sie können die synchronisierten und freigegebenen Daten mit dem [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Dieses Dashboard bietet wertvolle Einblicke in die Verfügbarkeit von Produktdaten für Ihre Storefront, sodass sie Ihren Käufern umgehend angezeigt werden können.

![Data Management Dashboard](assets/data-management-dashboard.png)

#### Zukünftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu 15 Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar sind. Weitere Informationen finden Sie unter [Indizierung - Streaming von Produktaktualisierungen](indexing.md).

## 4. Überprüfen, ob die Daten exportiert wurden {#verify-export}

So überprüfen Sie, ob die Katalogdaten aus Ihrer Adobe Commerce-Instanz exportiert wurden und synchronisiert werden für [!DNL Live Search], haben Sie einige Optionen:

- Suchen Sie in den folgenden Tabellen nach Einträgen:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Verwenden Sie die [GraphQL-Playground](https://developer.adobe.com/commerce/services/graphql/live-search/) mit der Standardabfrage, um Folgendes zu überprüfen:

   - Die zurückgegebene Produktanzahl entspricht in etwa dem, was Sie für die Store-Ansicht erwarten.
   - Facets werden zurückgegeben.

Weitere Hilfe finden Sie unter [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in der Support-Wissensdatenbank.

## 5. Konfigurieren der Daten

Durch die korrekte Konfiguration Ihrer Produktdaten werden gute Suchergebnisse für Ihre Kunden sichergestellt. In diesem Abschnitt aktivieren Sie die Widgets zur Produktliste und weisen Kategorien und Attribute zu.

### Enable Product Listing Widgets

Bei der Installation [!DNL Live Search] 4.0.0+ sind Product Listing Widgets standardmäßig aktiviert. Wenn Widgets aktiviert sind, wird eine andere UI-Komponente für die Suchergebnisseite und die Kategorieseite zum Durchsuchen von Produktlisten-Seiten verwendet. Diese UI-Komponente führt direkte Aufrufe an die [Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), was zu schnelleren Antwortzeiten führt.

Wenn Sie [!DNL Live Search] -Version, die älter als 4.0.0 ist, müssen Sie das Widget &quot;Produktliste&quot;manuell aktivieren.

1. Aus dem *Admin*, gehen Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. under **[!UICONTROL Live Search]** auswählen **[!UICONTROL Storefront Features]**.
1. Satz **[!UICONTROL Enable Product Listing Widgets]** nach `Yes`.

   ![Enable Product Listing Widgets](assets/ls-admin-enable-widget.png)

Wenn Sie diese Konfiguration ändern, wird die Meldung `Page cache is invalidated` angezeigt. Sie müssen den Magento-Cache leeren, um Ihre Änderung zu speichern.

1. Zugriff auf [Cacheverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) Seite durch einen der folgenden Schritte:

   - Klicken Sie auf **[!UICONTROL Cache Management]** in der Meldung über dem Arbeitsbereich.
   - Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Wählen Sie die **Konfiguration** [!UICONTROL Cache Type] und klicken **[!UICONTROL Flush Magento Cache]**.

   Änderungen an der Storefront werden unmittelbar nach dem Leeren des Caches vorgenommen.

### Zuweisen von Kategorien

Zurückgegebene Produkte [!DNL Live Search] muss einer [category](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). In Luma beispielsweise werden Produkte in Kategorien wie &quot;Männer&quot;, &quot;Frauen&quot;und &quot;Zahnrad&quot;unterteilt. Unterkategorien sind auch &quot;Tops&quot;, &quot;Bottom&quot; und &quot;Watches&quot;. Dies ermöglicht eine bessere Granularität beim Filtern.

### Durchsuchbare und filterbare Felder

Produkte werden zugewiesen [attributes](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) die für die Suche und Filterung verwendet werden können. Attribute sind Dinge wie &quot;Farbe&quot;, &quot;Größe&quot;, &quot;Materialtyp&quot;. Mit diesen Attributen können Benutzer nach &quot;grünen Spitzen&quot;suchen. Jedes Produkt kann über viele Attribute verfügen, die im [!DNL Commerce] Admin.

Jedes dieser Attribute kann als [&quot;searchable&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) im Admin. Wenn diese Attribute als &quot;durchsuchbar&quot;festgelegt sind, können sie von [!DNL Live Search].

[Facets](facets.md) sind Produktattribute, die in [!DNL Live Search] gefilterbar sein. Jedes filterbare Attribut kann als Facette in [!DNL Live Search] Es gibt jedoch Einschränkungen dafür, wie viele Facetten gleichzeitig durchsucht werden können.

[Synonyme](synonyms.md) sind Begriffe, die Sie definieren können, um Benutzer zum richtigen Produkt zu führen. Benutzer, die nach Hosen suchen, können &quot;Hosen&quot;oder &quot;Schläge&quot;eingeben. Sie können Synonyme festlegen, sodass diese Suchbegriffe Benutzer zu den Ergebnissen der &quot;Hosen&quot;führen.

## 6. Verbindung testen {#test-connection}

Testen Sie mit Ihren Katalogdaten jetzt in SaaS, um sicherzustellen, dass in den folgenden Szenarien Produktdaten zurückgegeben werden:

- Die [!UICONTROL Search] box gibt Ergebnisse korrekt zurück
- Kategoriesuche gibt Ergebnisse korrekt zurück
- Facets sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles ordnungsgemäß funktioniert, [!DNL Live Search] installiert, verbunden und einsatzbereit ist.

Wenn Probleme in der Storefront auftreten, überprüfen Sie die `var/log/system.log` -Datei für API-Kommunikationsfehler oder -fehler auf der Dienstseite.

In [!DNL Live Search] durch eine Firewall hinzufügen `commerce.adobe.io` in die Zulassungsliste.

## 7. Benutzerspezifisch für Ihre Storefront

Sie haben die Variable [!DNL Live Search] Erweiterung, Synchronisierung, Validierung und Konfiguration Ihrer Daten. Jetzt möchten Sie sicherstellen, dass die Variable [!DNL Live Search] Widgets entsprechen dem Erscheinungsbild Ihres Stores.

Sie können die Popover- und PLP-Widgets gestalten, indem Sie nach Bedarf benutzerdefinierte CSS-Regeln definieren. Siehe [Formatieren von Popover-Elementen](storefront-popover-styling.md) und [Seiten-Widget &quot;Produktliste&quot;](plp-styling.md).

Wenn Sie die Funktionalität der Widgets erweitern möchten, ist der Quellcode für jedes in einem öffentlichen Repository verfügbar.
In diesem Szenario können Sie das JavaScript für Ihre eigenen Anforderungen anpassen und dann Ihren benutzerdefinierten Code auf Ihrem CDN hosten. Dieses benutzerdefinierte Skript kommuniziert mit dem [!DNL Live Search] und gibt die Ergebnisse wie normal zurück, sodass Sie die Funktionalität des Widgets steuern können.

- [PLP-Widget-Repo](https://github.com/adobe/storefront-product-listing-page)
- [Suchleistensymbol](https://github.com/adobe/storefront-search-as-you-type)

## Aktualisieren [!DNL Live Search] {#update}

Führen Sie vor der Aktualisierung der Live Search-Suche Folgendes über die Befehlszeile aus, um die installierte Live Search-Version zu überprüfen:

```bash
composer show magento/module-live-search | grep version
```

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

1. Speichern `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Deinstallation [!DNL Live Search] {#uninstall}

Deinstallation [!DNL Live Search], siehe [Module deinstallieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] packages {#packages}

Die [!DNL Live Search] -Erweiterung umfasst die folgenden Pakete:

| Paket | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern, ihre Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. zu konfigurieren, und bietet Zugriff auf einen schreibgeschützten GraphQL-Spielplatz, auf dem Abfragen aus dem *Admin*. |
| `module-live-search-adapter` | Routet Suchanforderungen von der Storefront zum [!DNL Live Search] und rendert die Ergebnisse in der Storefront. <br />- Kategoriesuche - Routen von Anforderungen aus der Storefront [oberste Navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) zum Suchdienst hinzu.<br />- Globale Suche - Routen von Anfragen von der [Schnellsuche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) in der oberen rechten Ecke des Storefront zur [!DNL Live Search] -Dienst. |
| `module-live-search-storefront-popover` | Ein Popup &quot;Suche beim Eingeben&quot;ersetzt die standardmäßige Schnellsuche und gibt Daten und Miniaturansichten der Top-Suchergebnisse zurück. |

## [!DNL Live Search] dependencies {#dependencies}

Die folgenden [!DNL Live Search] Abhängigkeiten werden von [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Erweiterte Konzepte

In den folgenden Abschnitten werden erweiterte Themen zur Verwendung von [!DNL Live Search] und [!DNL Catalog Service].

### Endpunkt

[!DNL Live Search] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] keinen Zugriff auf die vollständige Produktdatenbank hat, [!DNL Live Search] GraphQL und Commerce Core GraphQL verfügen nicht über vollständige Parität.

Es wird empfohlen, die SaaS-APIs direkt aufzurufen - insbesondere den Catalog Service-Endpunkt.

- Steigern Sie die Leistung und reduzieren Sie die Prozessorlast durch Umgehen der Commerce-Datenbank/des Graphql-Prozesses.
- Nutzen Sie die Vorteile der [!DNL Catalog Service] Föderation anrufen [!DNL Live Search], [!DNL Catalog Service], und [!DNL Product Recommendations] von einem einzelnen Endpunkt aus.

Für einige Anwendungsfälle ist es möglicherweise besser, [!DNL Catalog Service] für Produktdetails und ähnliche Fälle. Siehe [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) für weitere Informationen.

Wenn Sie über eine benutzerdefinierte Headless-Implementierung verfügen, überprüfen Sie die [!DNL Live Search] Referenzimplementierungen:

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Live-Suchfeld](https://github.com/adobe/storefront-search-as-you-type)

Wenn Sie nicht die Standardkomponenten wie Suchadapter oder Widgets auf Luma oder AEM CIF Widgets verwenden, funktioniert Eventing (Clickstream-Daten, die Adobe Sensei für intelligente Merchandising- und Leistungsmetriken speisen) nicht standardmäßig und erfordert eine benutzerdefinierte Entwicklung, um Headless-Eventing zu implementieren.

Die neueste Version von [!DNL Live Search] bereits verwendet [!DNL Catalog Service].

### Sprachunterstützung

[!DNL Live Search] -Widgets unterstützen die folgenden Sprachen:

|  |  |  |  |
|--- |--- |--- |--- |
| Sprache | Region | Sprachcode | Magento Locale |
| bulgarisch | Bulgarien | bg_BG | bg_BG |
| Katalan | Spanien | ca_ES | ca_ES |
| tschechisch | Tschechische Republik | cs_CZ | cs_CZ |
| dänisch | Dänemark | da_DK | da_DK |
| deutsch | Deutschland | de_DE | de_DE |
| griechisch | Griechenland | el_GR | el_GR |
| englisch | Vereinigtes | en_GB | en_GB |
| englisch | Vereinigte Staaten | en_US | en_US |
| spanisch | Spanien | es_ES | es_ES |
| estnisch | Estland | et_EE | et_EE |
| Baskisch | Spanien | eu_ES | eu_ES |
| Persisch | Iran | fa_IR | fa_IR |
| finnisch | Finnland | fi_FI | fi_FI |
| französisch | Frankreich | fr_FR | fr_FR |
| Galizisch | Spanien | gl_ES | gl_ES |
| Hindi | Indien | hi_IN | hi_IN |
| ungarisch | Ungarn | hu_HU | hu_HU |
| Indonesisch | Indonesien | id_ID | id_ID |
| italienisch | Italien | it_IT | it_IT |
| Koreanisch | Südkorea | ko_KR | ko_KR |
| litauisch | Litauen | lt_LT | lt_LT |
| lettisch | Lettland | lv_LV | lv_LV |
| norwegisch | Norwegen Bokmal | nb_NO | nb_NO |
| holländisch | Niederlande | nl_NL | nl_NL |
| polnisch | Polen | pl_PL | pl_PL |
| portugiesisch | Brasilien | pt_BR | pt_BR |
| portugiesisch | Portugal | pt_PT | pt_PT |
| rumänisch | Rumänien | ro_RO | ro_RO |
| Russisch | Russland | ru_RU | ru_RU |
| schwedisch | Schweden | sv_SE | sv_SE |
| Thailändisch | Thailand | th_TH | th_TH |
| türkisch | Türkei | tr_TR | tr_TR |
| Chinesisch | China | zh_CN | zh_Hans_CN |
| Chinesisch | Taiwan | zh_TW | zh_Hant_TW |

Wenn das Widget erkennt, dass die Commerce-Admin-Spracheinstellung (_Stores_ > Einstellungen > _Konfiguration_ > _Allgemein_ > Länderoptionen) mit einer unterstützten Sprache übereinstimmen, wird standardmäßig diese Sprache verwendet. Andernfalls wird für die Widgets standardmäßig Englisch angezeigt.

Administratoren können auch die Sprache der [Suchindex](settings.md#language), um bessere Suchergebnisse sicherzustellen.

### Widget-Code-Repository

Das Widget &quot;Seite der Produktauflistungen&quot;und das Widget &quot;Feld der Live-Suche&quot;können über ihr GitHub-Repository heruntergeladen werden.

Dadurch können Entwickler die Funktionalität und den Stil vollständig anpassen. Diese Benutzer hosten den Code selbst, während sie weiterhin die [!DNL Live Search] -Dienst.

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Suchleiste](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] unterstützt [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Funktionen in Commerce (ehemals &quot;Multi-Source Inventory&quot;oder &quot;MSI&quot;). Um den vollständigen Support zu ermöglichen, müssen Sie [update](install.md#update) das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+.

[!DNL Live Search] gibt einen booleschen Hinweis zurück, ob ein Produkt in Inventory management verfügbar ist, enthält jedoch keine Informationen darüber, welche Quelle über das Lager verfügt.

### Preisindex

Live Search-Kunden können die neue [SaaS-Preisindexer](../price-index/price-indexing.md), was schnellere Preisänderungen und Synchronisierungszeiten ermöglicht.

### Preisstützung

Live Search-Widgets unterstützen die meisten, aber nicht alle von Adobe Commerce unterstützten Preistypen.

Derzeit werden Basispreise unterstützt. Folgende erweiterte Preise werden nicht unterstützt:

- Kosten
- Mindestpreis für Werbung

Sehen Sie sich an [API-Mesh](../catalog-service/mesh.md) für komplexere Preisberechnungen.

Das Preisformat unterstützt die Gebietsschema-Konfigurationseinstellung innerhalb der Commerce-Instanz: *Stores* > Einstellungen > *Konfiguration* > Allgemein > *Allgemein* > Lokale Optionen > Gebietsschema.

### PWA-Unterstützung

[!DNL Live Search] funktioniert mit PWA Studio, aber die Benutzer sehen möglicherweise leichte Unterschiede im Vergleich zu anderen Commerce-Implementierungen. Grundlegende Funktionen wie Suche und Produktlistenseite funktionieren in Venia, aber einige Permutationen von Graphql funktionieren möglicherweise nicht ordnungsgemäß. Es kann auch Leistungsunterschiede geben.

- Die aktuelle PWA-Implementierung von [!DNL Live Search] benötigt mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben als [!DNL Live Search] mit der nativen Commerce-Storefront.
- [!DNL Live Search] in PWA wird nicht unterstützt [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Daher funktionieren Suchberichte und intelligentes Merchandising.
- Direktes Filtern auf `description`, `name`, `short_description` wird von GraphQL nicht unterstützt, wenn [PWA](https://developer.adobe.com/commerce/pwa-studio/), werden jedoch mit einem allgemeineren Filter zurückgegeben.

Verwendung [!DNL Live Search] Mit PWA Studio müssen Integratoren auch:

1. Installieren [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Legen Sie die `environmentId` im `storeDetails` -Objekt.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] erfasst Benutzerinteraktionsdaten im Rahmen der grundlegenden Funktionalität und Cookies werden zum Speichern dieser Daten verwendet. Beim Erfassen von Benutzerinformationen muss der Benutzer dem Speichern von Cookies zustimmen. [!DNL Live Search] und [!DNL Product Recommendations] den Datenstrom und damit denselben Cookie-Mechanismus teilen. Weitere Informationen dazu finden Sie unter [Umgang mit Cookie-Einschränkungen](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
