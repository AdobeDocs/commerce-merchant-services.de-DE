---
title: Grenzen und Beschränkungen
description: Erfahren Sie mehr über die Grenzen und Einschränkungen von  [!DNL Live Search] , um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 7539c0fe9ebe4b82f42f3a7ff30b03c951980eed
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 0%

---

# Grenzen und Beschränkungen

Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie die folgenden Grenzen und Beschränkungen, um sicherzustellen, dass [!DNL Live Search] und [!DNL Catalog Service] den Anforderungen Ihres Unternehmens entsprechen. Wenn Sie erweiterte Suchfunktionen wie Inhaltssuche, BYOA (bring-your-own-algorithm) oder attributbasiertes Merchandising benötigen, sollten Sie eine Suchlösung eines Drittanbieters in Betracht ziehen.

## Allgemein

- Das [Erweiterte Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search)-Modul ist deaktiviert, wenn [!DNL Live Search] installiert ist, und der Link für die erweiterte Suche in der Storefront-Fußzeile wird entfernt.
- [Preisstufe](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) wird im [!DNL Live Search] Feld und im Widget „Produktlistenseite“ nicht unterstützt.
- Die Produktpreise beinhalten keine Mehrwertsteuer (MwSt.).
- Die Inhaltssuche (CMS-Seiten und -Blöcke) wird nicht unterstützt.
- Es gibt eine Grenze von 10.000 Produkten, die paginiert werden können. Dieser Grenzwert kann zwar erhöht werden, aber er kann sich auf die Leistung auswirken. Stellen Sie sicher, dass Sie aussagekräftige Möglichkeiten zum Filtern von Produkten bereitstellen, falls eine Kategorie oder ein Suchergebnis über eine große Anzahl von Produkten verfügt, sodass Käufer keine tiefe Paginierung verwenden müssen.
- Es gibt eine feste Grenze von 1 MB pro Attribut, einschließlich Beschreibung und benutzerdefinierten Attributen.
- Der Suchadapter unterstützt keine Produktattribute, die mit einem benutzerdefinierten Quellmodell erstellt und als Facetten verwendet werden. Um diese Funktion zu unterstützen, müssen Sie das Widget [Produktlistenseite“ ](plp-styling.md).
- Benutzerdefinierte Produkttypen werden nicht unterstützt.
- Benutzerdefinierte Attribute, die programmgesteuert mit `"is_user_defined": false` erstellt wurden, werden nicht unterstützt.
- Sie können Ergebnisse mithilfe der Bedingungen „Beginnt mit“ oder „Enthält“ mit einigen Einschränkungen filtern, wie [hier](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#limitations) beschrieben.
- Sie können Leistungsmetriken nur innerhalb des letzten Jahres verfolgen.

## Indizierung

- [!DNL Live Search] [indizes](indexing.md) bis zu insgesamt 450 Produktattribute pro Shop-Ansicht. Diese sind wie folgt verteilt:
   - 50 sortierbare Attribute
   - 200 filterbare Attribute
   - 200 durchsuchbare Attribute
- [!DNL Live Search] indiziert nur Produkte aus der Adobe Commerce-Datenbank.
- CMS-Seiten sind nicht indiziert.
- Attribute für SKU, Name und Kategorie sind standardmäßig durchsuchbar und können nicht von der Suche ausgeschlossen werden. Heben Sie die Zuweisung der Produkte zu den Kategorien auf, wenn sie nicht zu diesen Kategorien gehören sollen.

## Facetten

- Es können maximal 100 Attribute aus den 200 filterbaren Attributen, die indiziert werden können, als Facetten konfiguriert werden.
- Innerhalb einer Facette können maximal 100 Buckets zurückgegeben werden. Wenn Sie mehr als 100 Behälter zurückgeben müssen, erstellen [ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) damit Adobe die Leistungsauswirkungen analysieren und ermitteln kann, ob es möglich ist, diese Grenze für Ihre Umgebung zu erhöhen.
- Dynamische Facetten können Leistungsprobleme bei großen Indizes und Indizes mit hoher Ordinalität verursachen. Wenn Sie dynamische Facetten erstellt haben und eine Leistungsbeeinträchtigung oder das Laden einer Seite mit Zeitüberschreitungsfehlern bemerken, versuchen Sie, Ihre Facetten zu ändern und anzuheften, um festzustellen, ob dies Ihr Leistungsproblem behebt.
- Lagerstatus (`quantity_and_stock_status`) wird nicht als Facette unterstützt. Sie können `inStock: 'true'` verwenden, um nicht vorrätige Produkte zu filtern. Dies wird im `LiveSearchAdapter`-Modul standardmäßig unterstützt, wenn „Nicht vorrätige Produkte anzeigen“ im [!DNL Commerce] Admin auf „True“ eingestellt ist.
- Datentypattribute werden nicht als Facette unterstützt.
- Änderungen, die an den Attributmetadaten vorgenommen werden, nachdem dieses Attribut als Facette hinzugefügt wurde, werden in der Facette nicht widergespiegelt.

## Abfrage

- [!DNL Live Search] verwendet einen eindeutigen [GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/)Endpunkt für Abfragen zur Unterstützung von Funktionen wie dynamisches Facettieren und Suche nach eigener Eingabe. Obwohl es der [GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/) ähnelt, gibt es einige Unterschiede, und einige Felder sind möglicherweise nicht vollständig kompatibel.
- Die maximale Anzahl von Ergebnissen, die in einer Suchanfrage zurückgegeben werden können, beträgt 10.000.
- Die maximale Anzahl von Ergebnissen pro Seite beträgt 500.
- Es ist nicht möglich, Ergebnisse mithilfe eines Attributs vom Typ Datum zu filtern.

## Regeln

- Die maximale Anzahl von Merchandising-[ (Regeln](rules.md) pro Store-Ansicht ist 50.
- Kategorie-Merchandising kann eine Regel pro Kategorie aufweisen.
- Die maximale Anzahl von Bedingungen pro Regel ist 10.
- Die maximale Anzahl von Ereignissen pro Regel ist 25.
- Um unvorhersehbare Ergebnisse in paginierten Antworten zu vermeiden, sollte die Anzahl der angehefteten Produkte die angeforderte Seitengröße nicht überschreiten.

## Synonyme

- [!DNL Live Search] können bis zu 200 [Synonyme](synonyms.md) pro Shop-Ansicht verwalten.
- Mehrwortsynonyme funktionieren möglicherweise nicht immer wie erwartet. Achten Sie darauf, diese Synonyme in der Staging-Umgebung zu testen, bevor Sie sie in der Produktion verwenden, da sie möglicherweise negative Auswirkungen auf die Relevanz haben können.

## Kategorie-Merchandising

- Für jede Shop-Ansicht kann eine Regel pro Kategorie erstellt werden. Jede Regel kann Folgendes enthalten:
   - Bis zu zehn Bedingungen
   - Bis zu 25 Ereignisse

## B2B- und Kategorieberechtigungen

- Produkte werden nicht angezeigt, wenn sie nicht zu einem freigegebenen Standardkatalog hinzugefügt werden.
- So beschränken Sie Kundengruppen mithilfe von [Kategorieberechtigungen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions):
   - Produkte müssen der Stammkategorie zugewiesen werden.
   - Die Kundengruppe „Nicht angemeldet“ muss über „Erlauben“-Browserberechtigungen verfügen.
   - Um Produkte auf die Kundengruppe „Nicht angemeldet“ zu beschränken, gehen Sie zu jeder Kategorie und legen Sie die Berechtigungen für jede [Kundengruppe“ ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- Vorkonfigurierte Unterstützung für B2B mit dem PLP-Widget in PWA Studio wird derzeit nicht unterstützt. Sie können jedoch [die API verwenden](install.md#pwa-support) um diese Funktion zu implementieren.
- Kategoriefacetten in [!DNL Live Search] zeigen möglicherweise Kategorien an, die für eine bestimmte [ (Kundengruppe) nicht ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) werden können.
- [!DNL Live Search] können bis zu 1.000 Kundengruppen unterstützen.

## [!DNL Storefront popover]

- Die [[!DNL popover]](storefront-popover.md) ist nur für Stores verfügbar, die das Design *Luma* verwenden, oder für ein benutzerdefiniertes Design, das auf &quot;*&quot;*. Breadcrumbs auf der Suchergebnisseite haben keinen *Luma*-Stil.
- Das [!DNL popover] unterstützt das Design &quot;*&quot;*.
- Die [!DNL popover] wird im Schnellbestellungsformular nicht unterstützt.
- Wunschlisten und Produktvergleiche werden nicht unterstützt.
- Das Währungssymbol für den Peruanischen Sol (PEN) wird nicht unterstützt.

## Fehlerbehebung

Hilfe bei der Fehlerbehebung bei einigen häufigen Problemen in [!DNL Live Search] finden Sie in den folgenden Knowledgebase-Artikeln:

- [[!DNL Live Search] Katalog nicht synchronisiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync)
- [[!DNL Live Search] Das Dashboard und die Suchergebnis-Rangfolge sind falsch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-dashboard-ranking-incorrect)
- [[!DNL Live Search] zeigt nicht vorrätige Produkte unabhängig von den Lagerstatuseinstellungen in Admin an](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-displays-out-of-stock-products)
- [[!DNL Live Search] Facetten sind nicht alphabetisch sortiert](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-facets-not-sorted)

Wenn Sie zusätzliche Hilfe benötigen, wenden Sie sich an [Support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
