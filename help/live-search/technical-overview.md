---
title: "Technischer Überblick"
description: "[!DNL Live Search] Onboarding-Fluss, Systemanforderungen, Grenzen und Einschränkungen"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# Technischer Überblick

In diesem Thema werden die technischen Anforderungen und Tipps für die Installation und Optimierung beschrieben. [!DNL Live Search] für Adobe Commerce.

## Voraussetzungen {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Unterstützte Plattformen

* Adobe Commerce On-Premise (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpunkt

[!DNL Live Search] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] keinen Zugriff auf die vollständige Produktdatenbank hat, [!DNL Live Search] GraphQL und Commerce Core GraphQL werden nicht vollständig parity sein.

Es wird empfohlen, die SaaS-APIs direkt aufzurufen - insbesondere den Catalog Service-Endpunkt.

* Steigern Sie die Leistung und reduzieren Sie die Prozessorlast, indem Sie die Commerce-Datenbank/den Graphql-Prozess umgehen.
* Nutzen Sie die Vorteile der [!DNL Catalog Service] Föderation anrufen [!DNL Live Search], [!DNL Catalog Service], und [!DNL Product Recommendations] von einem einzelnen Endpunkt aus.

Für einige Anwendungsfälle ist es möglicherweise besser, [!DNL Catalog Service] für Produktdetails und ähnliche Fälle. Siehe [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) für weitere Informationen.

Wenn Sie über eine benutzerdefinierte Headless-Implementierung verfügen, überprüfen Sie die [!DNL Live Search] Referenzimplementierungen:

* [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
* [Live-Suchfeld](https://github.com/adobe/storefront-search-as-you-type)

Wenn Sie nicht die Standardkomponenten wie Suchadapter oder Widgets auf Luma oder AEM CIF Widgets verwenden, beachten Sie, dass Eventing (Clickstream-Daten, die Adobe Sensei für intelligente Merchandising- und Leistungsmetriken speisen) nicht vorkonfiguriert funktioniert und benutzerdefinierte Entwicklung erfordert, um Headless-Eventing zu implementieren.
Die neueste Version von [!DNL Live Search] bereits verwendet [!DNL Catalog Service] und die Installationen [!DNL Catalog Service] Module.

## Grenzen und Schwellenwerte

Derzeit wird die [!DNL Live Search] Die Such-/Kategorie-API weist die folgenden unterstützten Einschränkungen und statischen Begrenzungen auf:

### Indizierung

* [Indizes](indexing.md) bis zu 300 Produktattribute pro Store-Ansicht.
* Indiziert nur Produkte aus der Adobe Commerce-Datenbank.
* CMS-Seiten werden nicht indiziert.

### Abfrage

* [!DNL Live Search] hat keinen Zugriff auf die vollständige Taxonomie des Kategoriebaums, wodurch einige Navigationsszenarien mit Ebenen über die Reichweite hinausgehen.
* [!DNL Live Search] verwendet einen eindeutigen GraphQL-Endpunkt für Abfragen, um Funktionen wie dynamische Facetten und Suchen nach Ihrem Typ zu unterstützen. Obwohl ähnlich der [GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/), gibt es einige Unterschiede und einige Felder sind möglicherweise nicht vollständig kompatibel.

So beschränken Sie Kundengruppen mithilfe von Katalogberechtigungen:

* Produkte müssen der Kategorie Stammordner zugewiesen sein.
* Die Kundengruppe &quot;Nicht angemeldet&quot;muss über Browserberechtigungen vom Typ &quot;Zulassen&quot;verfügen.
* Um Produkte auf die Kundengruppe Nicht angemeldet zu beschränken, gehen Sie zu jeder Kategorie und legen Sie die Berechtigungen für jede Kundengruppe fest.

### Regeln

* Maximale Anzahl von Suchmaschinen-Merchandising [Regeln](rules.md) pro Store-Ansicht 50.
* Kategorievermarktung kann eine Regel pro Kategorie enthalten.
* Maximale Anzahl an Bedingungen pro Regel ist 10.
* Maximale Anzahl an Ereignissen pro Regel ist 25.

### Synonyme

* [!DNL Live Search] kann bis zu 200 [Synonyme](synonyms.md) pro Store-Ansicht.

## Sprachunterstützung

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
| portugiesisch | Brasilien | pt_BR | pt_BR |
| portugiesisch | Portugal | pt_PT | pt_PT |
| rumänisch | Rumänien | ro_RO | ro_RO |
| Russisch | Russland | ru_RU | ru_RU |
| schwedisch | Schweden | sv_SE | sv_SE |
| Thailändisch | Thailand | th_TH | th_TH |
| türkisch | Türkei | tr_TR | tr_TR |
| Chinesisch | China | zh_CN | zh_Hans_CN |
| Chinesisch | Taiwan | zh_TW | zh_Hant_TW |

Wenn das Widget erkennt, dass die Spracheinstellung &quot;Commerce Admin&quot;(_Stores_ > Einstellungen > _Konfiguration_ > _Allgemein_ > Länderoptionen) mit einer unterstützten Sprache übereinstimmen, wird standardmäßig diese Sprache verwendet. Andernfalls wird für die Widgets standardmäßig Englisch angezeigt.

Administratoren können auch die Sprache der [Suchindex](settings.md#language), um bessere Suchergebnisse sicherzustellen.

## Kategorie-Merchandising

[Kategorie-Merchandising](category-merch.md) ermöglicht Ihnen die Konfiguration [!DNL Live Search] , um auf der Produktkategorienebene zu arbeiten.

Dieses Video ist eine Einführung in Kategorie-Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Widget-Code-Repository

Das Widget &quot;Seite der Produktauflistungen&quot;und das Widget &quot;Feld der Live-Suche&quot;können über ihr GitHub-Repository heruntergeladen werden.

Dadurch können Entwickler die Funktionalität und den Stil vollständig anpassen. Diese Benutzer hosten den Code selbst, während sie weiterhin die [!DNL Live Search] -Dienst.

* [PLP-Widget](https://github.com/adobe/storefront-product-listing-page)
* [Suchleiste](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] unterstützt [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) Funktionen in Commerce (früher bekannt als Multi-Source-Bestand oder MSI). Um den vollständigen Support zu ermöglichen, müssen Sie [update](install.md#update) das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+.

[!DNL Live Search] gibt einen booleschen Hinweis zurück, ob ein Produkt in Inventory management verfügbar ist, enthält jedoch keine Informationen darüber, welche Quelle über das Lager verfügt.

## Preisindex

Live Search-Kunden können die neue [SaaS-Preisindexer](../price-index/price-indexing.md), was schnellere Preisänderungen und Synchronisierungszeiten ermöglicht.

## Preisstützung

Live Search-Widgets unterstützen die meisten, aber nicht alle von Adobe Commerce unterstützten Preistypen.

Derzeit werden Basispreise unterstützt. Folgende erweiterte Preise werden nicht unterstützt:

* Kosten
* Mindestpreis für Werbung

Sehen Sie sich an [API-Mesh](../catalog-service/mesh.md) für komplexere Preisberechnungen.

Das Preisformat unterstützt die Gebietsschema-Konfigurationseinstellung innerhalb der Commerce-Instanz: *Stores* > Einstellungen > *Konfiguration* > Allgemein > *Allgemein* > Lokale Optionen > Gebietsschema.

## PWA-Unterstützung

[!DNL Live Search] funktioniert mit PWA Studio, aber die Benutzer sehen möglicherweise geringfügige Unterschiede im Vergleich zu anderen Commerce-Implementierungen. Grundlegende Funktionen wie Suche und Produktlistenseite funktionieren in Venia, aber einige Permutationen von Graphql funktionieren möglicherweise nicht ordnungsgemäß. Es kann auch Leistungsunterschiede geben.

* Die aktuelle PWA-Implementierung von [!DNL Live Search] benötigt mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben als [!DNL Live Search] mit der nativen Commerce-Storefront.
* [!DNL Live Search] in PWA wird nicht unterstützt [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Daher funktionieren Suchberichte und intelligentes Merchandising.
* Direktes Filtern auf `description`, `name`, `short_description` wird von GraphQL nicht unterstützt, wenn [PWA](https://developer.adobe.com/commerce/pwa-studio/), werden jedoch mit einem allgemeineren Filter zurückgegeben.

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

## Derzeit nicht unterstützt

* Die [Erweiterte Suche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) -Modul deaktiviert ist, wenn [!DNL Live Search] installiert ist und der Link Erweiterte Suche in der Fußzeile der Storefront entfernt wird.
* [Tier-Preise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) und [Sonderpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) werden im [!DNL Live Search] -Feld und das Widget zur Produktauflistungsseite.

## Cookies

[!DNL Live Search] erfasst Benutzerinteraktionsdaten im Rahmen der grundlegenden Funktionalität und Cookies werden zum Speichern dieser Daten verwendet. Beim Erfassen von Benutzerinformationen muss der Benutzer dem Speichern von Cookies zustimmen. [!DNL Live Search] und [!DNL Product Recommendations] den Datenstrom und damit denselben Cookie-Mechanismus teilen. Weitere Informationen dazu finden Sie unter [Umgang mit Cookie-Einschränkungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
