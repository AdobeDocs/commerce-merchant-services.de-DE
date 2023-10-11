---
title: "Onboarding-Übersicht"
description: "[!DNL Live Search] Onboarding-Fluss, Systemanforderungen, Grenzen und Einschränkungen"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: a6d8c259f232ab27d7ed64558d5d193d59d23cad
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Onboarding-Übersicht

Erste Schritte mit [!DNL Live Search] Führen Sie für Adobe Commerce den Onboarding-Prozess aus, um die Erweiterung zu installieren, Ihre API-Schlüssel zu konfigurieren und Ihren Katalog zu synchronisieren.

## Voraussetzungen {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Unterstützte Plattformen

* Adobe Commerce On-Premise (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpunkt

[!DNL Live Search] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

## Grenzen und Schwellenwerte

Derzeit wird die [!DNL Live Search] Die Such-/Kategorie-API weist die folgenden unterstützten Einschränkungen und statischen Begrenzungen auf:

### Indizierung

* Indexiert bis zu 300 Produktattribute pro Store-Ansicht.
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

* Maximale Regelanzahl pro Store-Ansicht ist 50.
* Maximale Anzahl an Bedingungen pro Regel ist 10.
* Maximale Anzahl an Ereignissen pro Regel ist 25.

### Synonyme

* [!DNL Live Search] kann bis zu 200 Synonyme pro Store-Ansicht verwalten.

## Kategorie-Merchandising

KategorieMerchandising ermöglicht Ihnen die Konfiguration von [!DNL Live Search] , um auf der Produktkategorienebene zu arbeiten.

Dieses Video ist eine Einführung in Kategorie-Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Inventory management

[!DNL Live Search] unterstützt [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) Funktionen in Commerce (früher bekannt als Multi-Source-Bestand oder MSI). Um den vollständigen Support zu ermöglichen, müssen Sie [update](install.md#update) das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+.

[!DNL Live Search] gibt einen booleschen Hinweis zurück, ob ein Produkt in Inventory management verfügbar ist, enthält jedoch keine Informationen darüber, welche Quelle über das Lager verfügt.

## Preisindex

Live Search-Kunden können die neue [SaaS-Preisindexer](../price-index/index.md), was schnellere Preisänderungen und Synchronisierungszeiten ermöglicht.

## PWA-Unterstützung

[!DNL Live Search] funktioniert mit PWA Studio, aber die Benutzer sehen möglicherweise geringfügige Unterschiede im Vergleich zu anderen Commerce-Implementierungen. Grundlegende Funktionen wie Suche und Produktlistenseite funktionieren in Venia, aber einige Permutationen von Graphql funktionieren möglicherweise nicht ordnungsgemäß. Es kann auch Leistungsunterschiede geben.

* Die aktuelle PWA-Implementierung von [!DNL Live Search] benötigt mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben als [!DNL Live Search] mit der nativen Commerce-Storefront.
* [!DNL Live Search] in PWA wird nicht unterstützt [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Daher funktioniert intelligentes Merchandising nicht.
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
* [Basispreis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) wird im Live Search Popover- und Product Listing-Seiten-Widget nicht unterstützt.

## Cookies

[!DNL Live Search] erfasst Benutzerinteraktionsdaten im Rahmen der grundlegenden Funktionalität und Cookies werden zum Speichern dieser Daten verwendet. Beim Erfassen von Benutzerinformationen muss der Benutzer dem Speichern von Cookies zustimmen. [!DNL Live Search] und [!DNL Product Recommendations] den Datenstrom und damit denselben Cookie-Mechanismus teilen. Weitere Informationen dazu finden Sie unter [Umgang mit Cookie-Einschränkungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
