---
title: "Grenzen und Grenzen"
description: Erfahren Sie mehr über die Grenzen und Beschränkungen für [!DNL Live Search] s, um sicherzustellen, dass sie den Anforderungen Ihres Unternehmens entsprechen.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Grenzen und Beschränkungen

Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie die folgenden Grenzen und Beschränkungen, um sicherzustellen, dass [!DNL Live Search] und [!DNL Catalog Service] die Anforderungen Ihres Unternehmens erfüllen. Wenn Sie erweiterte Suchfunktionen wie Inhaltssuche, BYY-eigenen Algorithmus (BYOA) oder attributbasiertes Merchandising benötigen, sollten Sie eine Drittanbieter-Suchlösung in Erwägung ziehen.

## Allgemein

- Das Modul [Erweiterte Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) ist deaktiviert, wenn [!DNL Live Search] installiert ist, und der Link Erweiterte Suche in der Fußzeile der Storefront wird entfernt.
- [Tier-Preise](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) und [Sonderpreise](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) werden im Feld [!DNL Live Search] und im Widget &quot;Seite der Produktliste&quot;nicht unterstützt.
- Die Produktpreise enthalten keine Mehrwertsteuer (MwSt.).
- Die Inhaltssuche wird nicht unterstützt.
- Es gibt eine Grenze von 10.000 Produkten, die paginiert werden können.
- Pro Attribut gibt es eine feste Grenze von 1 MB, einschließlich Beschreibungen und benutzerdefinierten Attributen.
- Der Suchadapter unterstützt keine Produktattribute, die mit einem benutzerdefinierten Quellmodell erstellt und als Facetten verwendet werden. Um diese Funktion zu unterstützen, müssen Sie das Widget [Produktanlistungsseite](plp-styling.md) verwenden.

## Indizierung

- [!DNL Live Search] [ indiziert ](indexing.md) bis zu insgesamt 450 Produktattribute pro Store-Ansicht. Diese werden wie folgt verteilt:
   - 50 sortierbare Attribute
   - 200 filterbare Attribute
   - 200 durchsuchbare Attribute
- [!DNL Live Search] indiziert nur Produkte aus der Adobe Commerce-Datenbank.
- CMS-Seiten werden nicht indiziert.
- SKU-, Name- und Kategorieattribute sind standardmäßig durchsuchbar und können nicht aus der Suche ausgeschlossen werden. Achten Sie darauf, die Zuweisung der Produkte aus den Kategorien aufzuheben, wenn sie nicht in diesen Kategorien enthalten sein sollen.

## Facets

- Maximal 100 Attribute können als Facetten aus den 200 filterbaren Attributen konfiguriert werden, die indiziert werden können.
- Innerhalb einer Facette können maximal 30 Buckets zurückgegeben werden. Wenn mehr als 30 Behälter zurückgegeben werden müssen, erstellen Sie ein Support-Ticket ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) , damit Adobe die Leistungsbeeinträchtigung analysieren und feststellen kann, ob es möglich ist, diese Grenze für Ihre Umgebung zu erhöhen.[
- Dynamische Facetten können Leistungsprobleme in großen Indizes und Indizes mit hoher Ordnungsmäßigkeit verursachen. Wenn Sie dynamische Facetten erstellt haben und eine Leistungsbeeinträchtigung feststellen oder eine Seite nicht mit Zeitüberschreitungsfehlern geladen wird, versuchen Sie, Ihre Facetten so zu ändern, dass sie angeheftet werden, um festzustellen, ob dadurch Ihr Leistungsproblem behoben wird.
- Der Lagerstatus (`quantity_and_stock_status`) wird nicht als Facette unterstützt. Sie können `inStock: 'true'` verwenden, um aus Lagerprodukten zu filtern. Dies wird im Modul `LiveSearchAdapter` standardmäßig unterstützt, wenn &quot;Nicht vorrätige Produkte anzeigen&quot;in der Admin-Aktivität von [!DNL Commerce] auf &quot;True&quot;gesetzt ist.
- Attribute vom Typ Datum werden nicht als Facette unterstützt.

## Abfrage

- [!DNL Live Search] verwendet einen eindeutigen [GraphQL-Endpunkt](https://developer.adobe.com/commerce/services/graphql/live-search/) für Abfragen, um Funktionen wie dynamische Facetten und Suchen nach Ihrem Typ zu unterstützen. Obwohl dies der [GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/) ähnelt, gibt es einige Unterschiede und einige Felder sind möglicherweise nicht vollständig kompatibel.
- Die maximale Anzahl an Ergebnissen, die in einer Suchanfrage zurückgegeben werden können, beträgt 10.000.
- Es ist nicht möglich, Ergebnisse mit einem Attribut vom Typ Datum zu filtern.

## Regeln

- Die maximale Anzahl von SuchMerchandising [rules](rules.md) pro Store-Ansicht beträgt 50.
- Kategorievermarktung kann eine Regel pro Kategorie enthalten.
- Die maximale Anzahl von Bedingungen pro Regel beträgt 10.
- Die maximale Anzahl von Ereignissen pro Regel beträgt 25.
- Um unvorhersehbare Ergebnisse bei paginierten Antworten zu vermeiden, sollte die Anzahl der fixierten Produkte die angeforderte Seitengröße nicht überschreiten.

## Synonyme

- [!DNL Live Search] kann bis zu 200 [Synonyme](synonyms.md) pro Store-Ansicht verwalten.
- Multiword-Synonyme funktionieren möglicherweise nicht immer erwartungsgemäß. Testen Sie diese Synonyme unbedingt in der Staging-Umgebung, bevor Sie sie in der Produktion verwenden, da sie sich möglicherweise nachteilig auf die Relevanz auswirken können.

## Kategorievermarktung

- Für jede Store-Ansicht kann eine Regel pro Kategorie erstellt werden. Jede Regel kann Folgendes enthalten:
   - Bis zu zehn Bedingungen
   - Bis zu 25 Ereignisse

## B2B- und Kategorieberechtigungen

- Produkte werden nicht angezeigt, wenn sie nicht zu einem standardmäßigen freigegebenen Katalog hinzugefügt wurden.
- So beschränken Sie Kundengruppen mithilfe von [Kategorieberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions):
   - Produkte müssen der Stammkategorie zugeordnet werden.
   - Die Kundengruppe &quot;Nicht angemeldet&quot;muss über Browserberechtigungen vom Typ &quot;Zulassen&quot;verfügen.
   - Um Produkte auf die Kundengruppe &quot;Nicht angemeldet&quot;zu beschränken, gehen Sie zu jeder Kategorie und legen Sie die Berechtigung für jede [Kundengruppe](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) fest.
- Die native Unterstützung für B2B mit dem PLP-Widget auf PWA Studio wird derzeit nicht unterstützt. Sie können diese Funktion jedoch [mit der API](install.md#pwa-support) implementieren.
- Kategoriefacetten in [!DNL Live Search] zeigen möglicherweise Kategorien an, die für eine bestimmte [Kundengruppe](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) nicht angezeigt werden können.
- [!DNL Live Search] kann bis zu 1.000 Kundengruppen unterstützen.

## [!DNL Storefront popover]

- Der [[!DNL popover]](storefront-popover.md) ist nur für Stores verfügbar, die das Design *Luma* oder ein benutzerdefiniertes Design verwenden, das auf *Luma* basiert. Breadcrumbs auf der Suchergebnisseite verfügen nicht über den Stil *Luma* .
- Das Design *Leer* wird vom [!DNL popover] nicht unterstützt.
- Die [!DNL popover] wird im Schnellbestellformular nicht unterstützt.
- Wunschlisten und Produktvergleiche werden nicht unterstützt.
