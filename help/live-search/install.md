---
title: "Erste Schritte mit [!DNL Live Search]"
description: "Erfahren Sie mehr über die Systemanforderungen und Installationsschritte für [!DNL Live Search] von Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: aba1f41965e6c430f569adcf9d940cf399b50b73
workflow-type: tm+mt
source-wordcount: '2266'
ht-degree: 0%

---

# Für Erfolg mit [!DNL Live Search] einrichten

Adobe Commerce [!DNL Live Search] und [[!DNL Catalog Service]](../catalog-service/guide-overview.md) arbeiten zusammen, um eine leistungsfähige, relevante und intuitive Suchlösung bereitzustellen, mit der Ihre Kunden schnell genau das finden können, was sie benötigen. Genauer gesagt überdeckt [!DNL Catalog Service] Ihre Katalogdaten für SaaS-Dienste, z. B. [!DNL Live Search].

Dieser Artikel enthält schrittweise Anweisungen zur Implementierung von [!DNL Live Search] mit [!DNL Catalog Service].

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Lesen Sie vor der Implementierung unbedingt [Grenzen und Beschränkungen](boundaries-limits.md) , um sicherzustellen, dass [!DNL Live Search] Ihren Geschäftsanforderungen entspricht.

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

Auf hoher Ebene erfordert das Onboarding von [!DNL Live Search], dass Sie:

![Live Search-Workflow](assets/livesearch-workflow.png)

## 1. Installieren Sie die [!DNL Live Search] -Erweiterung

[!DNL Live Search] wird als Erweiterung von [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) bis [Composer](https://getcomposer.org/) installiert. Nach der Installation und Konfiguration von [!DNL Live Search] beginnt Adobe [!DNL Commerce] mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Benutzer von *Admin* Suchfacetten, Synonyme und Merchandising-Regeln einrichten, anpassen und verwalten.

>[!NOTE]
>
>Ab [!DNL Live Search] 3.0.2 ist die [!DNL Catalog Service] -Erweiterung im Paket mit der [!DNL Live Search] -Installation enthalten.

1. Vergewissern Sie sich, dass [cron-Aufträge](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) und [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ausgeführt werden.

   >[!IMPORTANT]
   >
   >Aufgrund der Ankündigung zum Ende der Unterstützung für Elasticsearch 7 vom August 2023 wird empfohlen, dass alle Adobe Commerce-Kunden zur OpenSearch 2.x-Suchmaschine migrieren. Weitere Informationen zur Migration Ihrer Suchmaschine während eines Produkt-Upgrades finden Sie unter [Migration zu OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) im _Upgrade-Handbuch_.

1. Laden Sie das Paket `live-search` vom [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) herunter.

1. Führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/live-search
   ```

   Wenn Sie die Erweiterung [!DNL Live Search] zu einer Adobe Commerce-Installation vom Typ **new** hinzufügen, führen Sie Folgendes aus, um [!DNL OpenSearch] und die zugehörigen Module zu deaktivieren, und installieren Sie [!DNL Live Search]. Fahren Sie dann mit Schritt 4 fort.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Wenn Sie die Erweiterung [!DNL Live Search] zu einer vorhandenen Adobe Commerce-Installation von **2} hinzufügen, führen Sie Folgendes aus, um die [!DNL Live Search] -Module, die Storefront-Suchergebnisse bereitstellen, vorübergehend zu deaktivieren.** Fahren Sie dann mit Schritt 4 fort:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] verwaltet weiterhin Suchanforderungen aus dem Store, während der [!DNL Live Search]-Dienst Katalogdaten synchronisiert und Produkte im Hintergrund indiziert.

1. Führen Sie Folgendes aus:

   ```bash
   bin/magento setup:upgrade
   ```

1. Stellen Sie sicher, dass die folgenden [Indexer](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt sind:

   - Produkt-Feed
   - Produktvarianten-Feed
   - Katalogattribut-Feed
   - Produktpreis-Feed
   - Umfang des Website-Daten-Feeds
   - Umfang des Daten-Feeds für Kundengruppen
   - Kategorien-Feed
   - Kategorieberechtigungs-Feed

1. Wenn Sie [!DNL Live Search] auf einer neuen Commerce-Instanz installieren, sind Sie fertig und können zu [2 überspringen. Konfigurieren Sie den Abschnitt &quot;API-Schlüssel](#2-configure-api-keys)&quot;. Wenn Sie die Live-Suche in einer vorhandenen Commerce-Instanz installieren, fahren Sie mit dem nächsten Schritt fort.

1. Führen Sie die folgenden Befehle aus, um die Erweiterung [!DNL Live Search] zu aktivieren, [!DNL OpenSearch] zu deaktivieren und `setup` auszuführen.

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

Der Adobe Commerce-API-Schlüssel und der zugehörige private Schlüssel sind erforderlich, um [!DNL Live Search] mit einer Installation von Adobe Commerce zu verbinden. Der API-Schlüssel wird im Konto des [!DNL Commerce] -Lizenzinhabers generiert und verwaltet, der ihn für den Entwickler oder den Systemintegrator freigeben kann. Der Entwickler kann dann die SaaS-Datenräume im Auftrag des Lizenzinhabers erstellen und verwalten. Wenn Sie bereits über eine Reihe von API-Schlüsseln verfügen, müssen Sie diese nicht neu generieren.

Erfahren Sie, wie Sie Ihre API-Schlüssel im Artikel [Commerce Services Connector](../landing/saas.md) konfigurieren.

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
> Während die Daten indiziert und synchronisiert sind, sind die Such- und Kategoriedurchsuchvorgänge nicht in der Storefront verfügbar. Je nach Größe Ihres Katalogs kann es mindestens eine Stunde dauern, bis `cron` ausgeführt wird, bis der Prozess Ihre Daten mit den SaaS-Diensten synchronisiert.

### Fortschritt der Synchronisierung überwachen

Sie können die synchronisierten und freigegebenen Daten über das [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) anzeigen. Dieses Dashboard bietet wertvolle Einblicke in die Verfügbarkeit von Produktdaten für Ihre Storefront, sodass sie Ihren Käufern umgehend angezeigt werden können.

![Dashboard &quot;Datenverwaltung&quot;](assets/data-management-dashboard.png)

#### Zukünftige Produktaktualisierungen

Nach der ersten Synchronisierung kann es bis zu 15 Minuten dauern, bis inkrementelle Produktaktualisierungen für die Storefront-Suche verfügbar sind. Weitere Informationen finden Sie unter [Indizierung - Streaming von Produktaktualisierungen](indexing.md).

## 4. Überprüfen, ob die Daten exportiert wurden {#verify-export}

Um sicherzustellen, dass die Katalogdaten aus Ihrer Adobe Commerce-Instanz exportiert und für [!DNL Live Search] synchronisiert wurden, haben Sie einige Optionen:

- Suchen Sie in den folgenden Tabellen nach Einträgen:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Verwenden Sie den [GraphQL-Playground](https://developer.adobe.com/commerce/services/graphql/live-search/) mit der Standardabfrage, um Folgendes zu überprüfen:

   - Die zurückgegebene Produktanzahl entspricht in etwa dem, was Sie für die Store-Ansicht erwarten.
   - Facets werden zurückgegeben.

Weitere Hilfe finden Sie unter [[!DNL Live Search] Nicht synchronisierter Katalog](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in der Support-Wissensdatenbank.

## 5. Konfigurieren der Daten

Durch die korrekte Konfiguration Ihrer Produktdaten werden gute Suchergebnisse für Ihre Kunden sichergestellt. In diesem Abschnitt aktivieren Sie die Widgets zur Produktliste und weisen Kategorien zu.

### Enable Product Listing Widgets

Wenn Sie [!DNL Live Search] 4.0.0+ installieren, sind die Widgets für die Produktauflistung standardmäßig aktiviert. Wenn Widgets aktiviert sind, wird eine andere UI-Komponente für die Suchergebnisseite und die Kategorieseite zum Durchsuchen von Produktlisten-Seiten verwendet. Diese UI-Komponente führt direkte Aufrufe an die [Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/) durch, was zu schnelleren Antwortzeiten führt.

Wenn Sie eine [!DNL Live Search] -Version vor 4.0.0+ haben, müssen Sie das Widget &quot;Produktliste&quot;manuell aktivieren.

1. Navigieren Sie vom *Admin* zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Wählen Sie unter &quot;**[!UICONTROL Live Search]**&quot;die Option &quot;**[!UICONTROL Storefront Features]**&quot;.
1. Setzen Sie **[!UICONTROL Enable Product Listing Widgets]** auf `Yes`.

   ![Aktiviert die Widgets zur Produktliste](assets/ls-admin-enable-widget.png)

Wenn Sie diese Konfiguration ändern, wird die Meldung `Page cache is invalidated` angezeigt. Sie müssen den Magento-Cache leeren, um Ihre Änderung zu speichern.

1. Greifen Sie auf die Seite [Cache-Verwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) zu, indem Sie einen der folgenden Schritte ausführen:

   - Klicken Sie auf den Link **[!UICONTROL Cache Management]** in der Meldung über dem Arbeitsbereich.
   - Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Wählen Sie die **Konfiguration** [!UICONTROL Cache Type] aus und klicken Sie auf **[!UICONTROL Flush Magento Cache]**.

   Änderungen an der Storefront werden unmittelbar nach dem Leeren des Caches vorgenommen.

### Zuweisen von Kategorien

Produkte, die in [!DNL Live Search] zurückgegeben werden, müssen einer [Kategorie](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories) zugewiesen werden. In Luma beispielsweise werden Produkte in Kategorien wie &quot;Männer&quot;, &quot;Frauen&quot;und &quot;Zahnrad&quot;unterteilt. Unterkategorien sind auch &quot;Tops&quot;, &quot;Bottom&quot; und &quot;Watches&quot;. Dies ermöglicht eine bessere Granularität beim Filtern.

## 6. Verbindung testen {#test-connection}

Testen Sie mit Ihren Katalogdaten jetzt in SaaS, um sicherzustellen, dass in den folgenden Szenarien Produktdaten zurückgegeben werden:

- Das Feld [!UICONTROL Search] gibt die Ergebnisse korrekt zurück
- Kategoriesuche gibt Ergebnisse korrekt zurück
- Facets sind als Filter auf Suchergebnisseiten verfügbar

Wenn alles ordnungsgemäß funktioniert, ist [!DNL Live Search] installiert, verbunden und einsatzbereit.

Wenn Sie im Storefront auf Probleme stoßen, überprüfen Sie die Datei &quot;`var/log/system.log`&quot;auf API-Kommunikationsfehler oder -fehler auf der Dienstseite.

Um [!DNL Live Search] über eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## 7. Benutzerspezifisch für Ihre Storefront

Sie haben Ihre Daten installiert, synchronisiert, validiert und konfiguriert. [!DNL Live Search] Jetzt möchten Sie sicherstellen, dass die [!DNL Live Search] -Widgets dem Look-and-Feel Ihres Stores entsprechen.

Sie können die Popover- und PLP-Widgets gestalten, indem Sie nach Bedarf benutzerdefinierte CSS-Regeln definieren. Siehe [Formatieren von Popover-Elementen ](storefront-popover.md#styling-popover-example) und [Seitenwidget für Produktauflistungen](plp-styling.md#styling-example).

Wenn Sie die Funktionalität der Widgets erweitern möchten, ist der Quellcode für jedes in einem öffentlichen Repository verfügbar.
In diesem Szenario können Sie die JavaScript an Ihre eigenen Anforderungen anpassen und dann Ihren benutzerdefinierten Code auf Ihrem CDN hosten. Dieses benutzerdefinierte Skript kommuniziert mit dem [!DNL Live Search] -Dienst und gibt die Ergebnisse wie normal zurück, sodass Sie die Funktionalität des Widgets steuern können.

- [PLP widget repo](https://github.com/adobe/storefront-product-listing-page)
- [Suchleiste repo](https://github.com/adobe/storefront-search-as-you-type)

## Aktualisieren von [!DNL Live Search] {#update}

Führen Sie vor der Aktualisierung der Live Search-Suche Folgendes über die Befehlszeile aus, um die installierte Live Search-Version zu überprüfen:

```bash
composer show magento/module-live-search | grep version
```

Um [!DNL Live Search] zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/live-search --with-dependencies
```

Um auf eine Hauptversion wie 3.1.1 auf 4.0.0 zu aktualisieren, bearbeiten Sie die Stammdatei des Projekts [!DNL Composer] `.json` wie folgt:

1. Wenn Ihre derzeit installierte `magento/live-search` -Version `3.1.1` oder niedriger ist und Sie auf Version `4.0.0` oder höher aktualisieren, führen Sie vor dem Upgrade den folgenden Befehl aus:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Führen Sie den folgenden Befehl aus, um Informationen zur derzeit installierten Version von `magento/live-search` zu erhalten:

   ```bash
   composer show magento/live-search
   ```

1. Öffnen Sie die Stammdatei `composer.json` und suchen Sie nach `magento/live-search`.

1. Aktualisieren Sie im Abschnitt `require` die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. Speichern Sie `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Deinstallieren von [!DNL Live Search] {#uninstall}

Informationen zum Deinstallieren von [!DNL Live Search] finden Sie unter [Module deinstallieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] Pakete {#packages}

Die Erweiterung [!DNL Live Search] besteht aus den folgenden Paketen:

| Paket | Beschreibung |
|--- |--- |
| `module-live-search` | Ermöglicht Händlern, ihre Sucheinstellungen für Facetten, Synonyme, Abfrageregeln usw. zu konfigurieren und bietet Zugriff auf einen schreibgeschützten GraphQL-Player, auf dem Abfragen vom *Admin* getestet werden können. |
| `module-live-search-adapter` | Sendet Suchanfragen von der Storefront an den Dienst [!DNL Live Search] und rendert die Ergebnisse in der Storefront. <br /> - Kategoriedurchsuchen - Routen von Anforderungen aus der Storefront [oberste Navigation](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) zum Suchdienst.<br /> - Globale Suche - Routet Anfragen aus dem Feld [Schnellsuche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) oben rechts im Storefront zum Dienst [!DNL Live Search]. |
| `module-live-search-storefront-popover` | Ein Popup &quot;Suche beim Eingeben&quot;ersetzt die standardmäßige Schnellsuche und gibt Daten und Miniaturansichten der Top-Suchergebnisse zurück. |

## [!DNL Live Search] dependencies {#dependencies}

Die folgenden [!DNL Live Search] -Abhängigkeiten werden von [!DNL Composer] erfasst.

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

Die folgenden Abschnitte enthalten erweiterte Themen bei Verwendung von [!DNL Live Search] und [!DNL Catalog Service].

### Endpunkt

[!DNL Live Search] kommuniziert über den Endpunkt bei `https://catalog-service.adobe.io/graphql`.

Da [!DNL Live Search] keinen Zugriff auf die gesamte Produktdatenbank hat, weisen [!DNL Live Search] GraphQL und Commerce Core GraphQL keine vollständige Parität auf.

Es wird empfohlen, die SaaS-APIs direkt aufzurufen - insbesondere den Catalog Service-Endpunkt.

- Steigern Sie die Leistung und reduzieren Sie die Prozessorlast durch Umgehen der Commerce-Datenbank/des Graphql-Prozesses.
- Nutzen Sie die [!DNL Catalog Service] -Föderation, um [!DNL Live Search], [!DNL Catalog Service] und [!DNL Product Recommendations] von einem einzelnen Endpunkt aus aufzurufen.

Für einige Anwendungsfälle ist es möglicherweise besser, [!DNL Catalog Service] für Produktdetails und ähnliche Fälle aufzurufen. Weitere Informationen finden Sie unter [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) .

Wenn Sie über eine benutzerdefinierte Headless-Implementierung verfügen, sehen Sie sich die [!DNL Live Search]-Referenzimplementierungen an:

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Live-Suchfeld](https://github.com/adobe/storefront-search-as-you-type)

Wenn Sie nicht die Standardkomponenten wie Suchadapter oder Widgets auf Luma oder AEM CIF Widgets verwenden, funktioniert Eventing (Clickstream-Daten, die Adobe Sensei für intelligente Merchandising- und Leistungsmetriken speisen) nicht standardmäßig und erfordert eine benutzerdefinierte Entwicklung, um Headless-Eventing zu implementieren.

Die neueste Version von [!DNL Live Search] verwendet bereits [!DNL Catalog Service].

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

Wenn das Widget erkennt, dass die Commerce-Admin-Spracheinstellung (_Stores_ > Einstellungen > _Konfiguration_ > _Allgemein_ > Länderoptionen) mit einer unterstützten Sprache übereinstimmt, wird standardmäßig diese Sprache verwendet. Andernfalls wird für die Widgets standardmäßig Englisch angezeigt.

Administratoren können auch die Sprache des [Suchindex](settings.md#language) festlegen, um bessere Suchergebnisse sicherzustellen.

### Widget-Code-Repository

Das Widget &quot;Seite der Produktauflistungen&quot;und das Widget &quot;Feld der Live-Suche&quot;können über ihr GitHub-Repository heruntergeladen werden.

Dadurch können Entwickler die Funktionalität und den Stil vollständig anpassen. Diese Benutzer hosten den Code selbst, während sie weiterhin den Dienst [!DNL Live Search] nutzen.

- [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
- [Suchleiste](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] unterstützt die Funktionen von [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) in Commerce (ehemals &quot;Multi-Source-Inventar&quot;oder &quot;MSI&quot;). Um die vollständige Unterstützung zu aktivieren, müssen Sie [das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+ aktualisieren.](install.md#update)

[!DNL Live Search] gibt einen booleschen Hinweis zurück, ob ein Produkt in Inventory management verfügbar ist, enthält jedoch keine Informationen darüber, welche Quelle den Bestand hat.

### Preisindex

Live Search-Kunden können den neuen [SaaS-Preisindex](../price-index/price-indexing.md) verwenden, der schnellere Preisänderungen und Synchronisierungszeiten ermöglicht.

### Preisstützung

Live Search-Widgets unterstützen die meisten, aber nicht alle von Adobe Commerce unterstützten Preistypen.

Derzeit werden Basispreise unterstützt. Folgende erweiterte Preise werden nicht unterstützt:

- Kosten
- Mindestpreis für Werbung

Komplexere Preisberechnungen finden Sie unter [API-Mesh](../catalog-service/mesh.md) .

Das Preisformat unterstützt die Gebietsschema-Konfigurationseinstellung in der Commerce-Instanz: *Stores* > Einstellungen > *Konfiguration* > Allgemein > *Allgemein* > Lokale Optionen > Gebietsschema.

### Headless-Storefront-Unterstützung

Optional müssen Sie möglicherweise das `module-data-services-graphql` -Modul installieren, das die bestehende GraphQL-Abdeckung der Anwendung erweitert und Felder enthält, die für die Erfassung von verhaltensbezogenen Storefront-Daten erforderlich sind.

```bash
composer require magento/module-data-services-graphql
```

Dieses Modul fügt GraphQL-Abfragen zusätzliche Kontexte hinzu:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### B2B-Unterstützung

[!DNL Live Search] unterstützt [B2B-Funktionalität](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) mit zusätzlichen [Einschränkungen](boundaries-limits.md#b2b-and-category-permissions).

### PWA-Unterstützung

[!DNL Live Search] funktioniert mit PWA Studio, aber die Benutzer sehen möglicherweise geringfügige Unterschiede im Vergleich zu anderen Commerce-Implementierungen. Grundlegende Funktionen wie Such- und Produktlistenseite funktionieren in Venia, aber einige Permutationen von Graphql funktionieren möglicherweise nicht ordnungsgemäß. Es kann auch Leistungsunterschiede geben.

- Die aktuelle PWA-Implementierung von [!DNL Live Search] erfordert mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben als [!DNL Live Search] mit der nativen Commerce-Storefront.
- [!DNL Live Search] in PWA unterstützt nicht die [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Daher funktionieren Suchberichte und intelligentes Merchandising.
- Das direkte Filtern nach `description`, `name` und `short_description` wird von GraphQL bei Verwendung mit [PWA](https://developer.adobe.com/commerce/pwa-studio/) nicht unterstützt, wird jedoch mit einem allgemeineren Filter zurückgegeben.

Um [!DNL Live Search] mit PWA Studio zu verwenden, müssen Integratoren auch:

1. Installieren Sie [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Legen Sie die `environmentId` im Objekt `storeDetails` fest.

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

[!DNL Live Search] erfasst Benutzerinteraktionsdaten im Rahmen seiner grundlegenden Funktionalität und Cookies werden zum Speichern dieser Daten verwendet. Beim Erfassen von Benutzerinformationen muss der Benutzer dem Speichern von Cookies zustimmen. [!DNL Live Search] und [!DNL Product Recommendations] teilen den Datenstrom und daher denselben Cookie-Mechanismus. Weitere Informationen dazu finden Sie unter [Umgang mit Cookie-Einschränkungen](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
