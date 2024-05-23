---
title: "Grenzen und Grenzen"
description: Erfahren Sie mehr über die Grenzen und Beschränkungen für [!DNL Live Search] um sicherzustellen, dass sie den Anforderungen Ihres Unternehmens entspricht.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 29983ec083a49859b99c9c906710ce0a01054a50
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Grenzen und Beschränkungen

Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie die folgenden Grenzen und Beschränkungen, um sicherzustellen, dass [!DNL Live Search] und [!DNL Catalog Service] erfüllen die Anforderungen Ihres Unternehmens. Wenn Sie erweiterte Suchfunktionen wie Inhaltssuche, BYY-eigenen Algorithmus (BYOA) oder attributbasiertes Merchandising benötigen, sollten Sie eine Drittanbieter-Suchlösung in Erwägung ziehen.

## Allgemein

- Die [Erweiterte Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) -Modul deaktiviert ist, wenn [!DNL Live Search] installiert ist und der Link Erweiterte Suche in der Fußzeile der Storefront entfernt wird.
- [Tier-Preise](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) und [Sonderpreise](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) werden im [!DNL Live Search] -Feld und das Widget zur Produktauflistungsseite.
- Die Produktpreise enthalten keine Mehrwertsteuer (MwSt.).
- Die Inhaltssuche wird nicht unterstützt.
- Es gibt eine Grenze von 10.000 Produkten, die paginiert werden können.
- Der Suchadapter unterstützt keine Produktattribute, die mit einem benutzerdefinierten Quellmodell erstellt und als Facetten verwendet werden. Um diese Funktion zu unterstützen, müssen Sie die [Seiten-Widget &quot;Produktliste&quot;](plp-styling.md).

## Indizierung

- [!DNL Live Search] [Indizes](indexing.md) bis zu 450 Produktattribute pro Store-Ansicht. Diese werden wie folgt verteilt:
   - 50 sortierbare Attribute
   - 200 filterbare Attribute
   - 200 durchsuchbare Attribute
- [!DNL Live Search] indiziert nur Produkte aus der Adobe Commerce-Datenbank.
- CMS-Seiten werden nicht indiziert.
- SKU-, Name- und Kategorieattribute sind standardmäßig durchsuchbar und können nicht aus der Suche ausgeschlossen werden. Achten Sie darauf, die Zuweisung der Produkte aus den Kategorien aufzuheben, wenn sie nicht in diesen Kategorien enthalten sein sollen.

## Facets

- Maximal 100 Attribute können als Facetten aus den 200 filterbaren Attributen konfiguriert werden, die indiziert werden können.
- Innerhalb einer Facette können maximal 30 Buckets zurückgegeben werden. Wenn mehr als 30 Behälter zurückgegeben werden müssen, [Support-Ticket erstellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) so kann Adobe die Leistungsbeeinträchtigung analysieren und feststellen, ob es möglich ist, diesen Grenzwert für Ihre Umgebung zu erhöhen.
- Dynamische Facetten können Leistungsprobleme in großen Indizes und Indizes mit hoher Ordnungsmäßigkeit verursachen. Wenn Sie dynamische Facetten erstellt haben und eine Leistungsbeeinträchtigung feststellen oder eine Seite nicht mit Zeitüberschreitungsfehlern geladen wird, versuchen Sie, Ihre Facetten so zu ändern, dass sie angeheftet werden, um festzustellen, ob dadurch Ihr Leistungsproblem behoben wird.
- Lagerstatus (`quantity_and_stock_status`) wird nicht als Facette unterstützt. Sie können `inStock: 'true'` , um aus Lagerprodukten herauszufiltern. Dies wird standardmäßig im `LiveSearchAdapter` -Modul, wenn &quot;Nicht vorrätige Produkte anzeigen&quot;im [!DNL Commerce] Admin.

## Abfrage

- [!DNL Live Search] hat keinen Zugriff auf die vollständige Taxonomie des Kategoriebaums, wodurch einige Navigationsszenarien mit Ebenen über die Reichweite hinausgehen.
- [!DNL Live Search] verwendet eine eindeutige [GraphQL-Endpunkt](https://developer.adobe.com/commerce/services/graphql/live-search/) für Abfragen, um Funktionen wie dynamische Facetten und Suchen nach dem Typ zu unterstützen. Obwohl ähnlich der [GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/), gibt es einige Unterschiede und einige Felder sind möglicherweise nicht vollständig kompatibel.
- Die maximale Anzahl an Ergebnissen, die in einer Suchanfrage zurückgegeben werden können, beträgt 10.000.

## Regeln

- Die maximale Anzahl von Such-Merchandising [Regeln](rules.md) pro Store-Ansicht 50.
- Kategorievermarktung kann eine Regel pro Kategorie enthalten.
- Die maximale Anzahl von Bedingungen pro Regel beträgt 10.
- Die maximale Anzahl von Ereignissen pro Regel beträgt 25.

## Synonyme

- [!DNL Live Search] kann bis zu 200 [Synonyme](synonyms.md) pro Store-Ansicht.
- Multiword-Synonyme werden nicht unterstützt.

## Kategorievermarktung

- Für jede Store-Ansicht kann eine Regel pro Kategorie erstellt werden. Jede Regel kann Folgendes enthalten:
   - Bis zu zehn Bedingungen
   - Bis zu 25 Ereignisse

## B2B- und Kategorieberechtigungen

- Produkte werden nicht angezeigt, wenn sie nicht zu einem standardmäßigen freigegebenen Katalog hinzugefügt wurden.
- So beschränken Sie Kundengruppen mithilfe von Katalogberechtigungen:
   - Produkte müssen der Kategorie Stammordner zugewiesen sein.
   - Die Kundengruppe &quot;Nicht angemeldet&quot;muss über Browserberechtigungen vom Typ &quot;Zulassen&quot;verfügen.
   - Um Produkte auf die Kundengruppe &quot;Nicht angemeldet&quot;zu beschränken, gehen Sie zu jeder Kategorie und legen Sie die Berechtigungen für jede Kundengruppe fest.
- Die Unterstützung für B2B mit Live Search for PWA Studio wird derzeit nicht unterstützt.
