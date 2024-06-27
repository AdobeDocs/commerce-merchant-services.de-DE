---
title: "Einrichten der Live-Suche"
description: Die [!DNL Live Search] Workspace wird zum Konfigurieren, Verwalten und Überwachen der Suchleistung verwendet.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 5e79bb43449b95b4c6aa0e234a0dbc999c312e59
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Einrichten der Live-Suche

Im Arbeitsbereich können Sie die Leistung von [!DNL Live Search]. Das Menü oben bietet Zugriff auf die Tools in den einzelnen Funktionsbereichen. Die verfügbaren Funktionen spiegeln die aktuelle Menüauswahl wider.

![Workspace](assets/workspace.png)

## Datenerfassung

Um sicherzustellen, dass jeder Funktionsbereich des Arbeitsbereichs die richtigen Daten enthält, müssen Sie die Datenerfassung auf der Grundlage der ausgewählten Storefront-Implementierung konfigurieren:

1. Luma - Die Datenerfassung ist standardmäßig verfügbar.
1. Headless - Die Datenerfassung muss je nach Storefront-Implementierung manuell konfiguriert werden.

Wenn Sie eine Headless-Storefront verwenden, finden Sie in der folgenden Dokumentation weitere Informationen zu den erforderlichen Ereignissen, die Sie hinzufügen müssen:

- [Erforderliche Ereignisse](events.md) für das Dashboard &quot;Live-Suche&quot;.
- [Storefront-Ereignis-Wächter](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) muss als Voraussetzung hinzugefügt werden.
- [Beispiele](https://github.com/adobe/commerce-events/tree/main/examples) der Ereignisstruktur.

## Festlegen des Umfangs

Zunächst wird die [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) von allen [!DNL Live Search] -Einstellungen auf `Default Store View`. Wenn [!DNL Commerce] Installation umfasst mehrere Store-Ansichten, Satz **Anwendungsbereich** der [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) wo Ihre Facetteneinstellungen angewendet werden.

## Menüoptionen

| Option | Beschreibung |
|--- |--- |
| [Leistung](performance.md) | Dashboard bietet Einblicke in die Leistung bei der Produktsuche. |
| [Facebook](facets.md) | Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten verwendet werden, um Suchkriterien zu verfeinern. |
| [Synonyme](synonyms.md) | Erweitern Sie die Reichweite der Suche, um Wörter einzuschließen, mit denen Käufer Produkte finden können, die sich von denen in Ihrem Katalog unterscheiden. |
| [Merchandising durchsuchen](rules.md) | Gestalten Sie das Sucherlebnis mit logischen Regeln, die geplante Aktionen Trigger haben. Sie können Produkte steigern, begraben, anheften oder ausblenden, um Suchergebnisse zur Unterstützung Ihrer Geschäftsziele zu kalibrieren. |
| [Kategorie-Merchandising](category-merch.md) | Anwenden von Regeln und intelligentem Merchandising auf Kategorieebene. |
| [GraphQL](graphql.md) | Entwickler, die beim Administrator Ihres Stores angemeldet sind, können Abfragen mit tatsächlichen Katalogdaten erstellen und testen. Weitere Informationen finden Sie unter [Übersicht über GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) im [!DNL Live Search] Entwicklerdokumentation. |
| [Einstellungen](settings.md) | Bestimmen Sie, wie Preisfacettenwerte in der Storefront nach Preisbereichen gruppiert werden, und legen Sie die Indexsprache fest. |

## Festlegen von Attributen als durchsuchbar

Um zielgerichtete Ergebnisse zu erzielen, lesen Sie den Abschnitt [durchsuchbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) Produktattribute. Um die Relevanz sicherzustellen, sollten Attribute nur durchsuchbar sein, wenn sie Inhalte mit einer klaren und präzisen Bedeutung enthalten. Vermeiden Sie die Verwendung von Attributen, die weniger präzisen, langwierigen Text enthalten, z. B. `description`, die zwar standardmäßig für die Suche aktiviert ist, aber die Genauigkeit der Suchergebnisse verringern kann. Wenn beispielsweise eine Person nach &quot;Shorts&quot;sucht und es Hemden mit einer Beschreibung gibt, die den Begriff &quot;Kurzärmel&quot;enthält, werden die Hemden in die Suchergebnisse aufgenommen.

Führen Sie die folgenden Schritte aus, um die Suche nach Attributen zu ermöglichen:

1. Navigieren Sie im Admin zu **Stores** > *Attribut* > **Produkt**.
1. Wählen Sie das Attribut aus, nach dem Sie suchen möchten, z. B. `color`.
1. Auswählen **Store-Eigenschaften** und **Verwendung in der Suche** nach `yes`.

   ![Workspace](assets/attribute-searchable.png)

[!DNL Live Search] berücksichtigt auch [Gewichtung](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) eines Produktattributs, wie in Adobe Commerce festgelegt. Attribute mit einer höheren Gewichtung werden in den Suchergebnissen höher angezeigt.

Die folgenden Attribute sind immer durchsuchbar:

- `sku`
- `name`
- `categories`

[Facets](facets.md) sind Produktattribute, die in [!DNL Live Search] gefilterbar sein. Sie können jedes filterbare Attribut als Facette in [!DNL Live Search], aber es gibt [limits](boundaries-limits.md) an, nach wie vielen Facetten Sie gleichzeitig suchen können.

[Synonyme](synonyms.md) sind Begriffe, die Sie definieren können, um Benutzer zum richtigen Produkt zu führen. Benutzer, die nach Hosen suchen, können &quot;Hosen&quot;oder &quot;Schläge&quot;eingeben. Sie können Synonyme festlegen, sodass diese Suchbegriffe Benutzer zu den Ergebnissen der &quot;Hosen&quot;führen.

## Commerce-Konfigurationseinstellungen

Im folgenden Abschnitt werden die unterstützten und nicht unterstützten Commerce-Konfigurationseinstellungen für [!DNL Live Search].

### Unterstützte Konfigurationswerte

| Commerce-Konfigurationseinstellungen | Beschreibung | Unterstützt von Popover | Vom Adapter unterstützt |
|---|---|---|---|
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Alle Produkte pro Seite zulassen | Wenn auf `Yes`, enthält die `ALL` im Steuerelement &quot;Pro Seite anzeigen&quot;. | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Minimale Abfragelänge | Die Mindestanzahl von Zeichen, die bei einer Katalogsuche zulässig ist. | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite - Zulässige Werte im Raster | Bestimmt die Anzahl der Produkte, die in der Rasteransicht angezeigt werden. | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite auf Raster Standardwert | Bestimmt die Anzahl der Produkte, die standardmäßig in der Rasteransicht pro Seite angezeigt werden. | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Bestand > Nicht vorrätige Produkte anzeigen | Zeigt nicht vorrätige Produkte an. | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Stores > Konfiguration > Währung > Standardanzeigewährung | Die Primärwährung, die zur Anzeige der Preise verwendet wird. | Ja w/3.1.0+ | Ja w/3.1.0+ |
| Stores > Konfiguration > Allgemein > Währungseinstellungen > Währungsoptionen > Basiswährung | Die Primärwährung, die für alle Online-Zahlungsvorgänge verwendet wird. | Ja | Ja |

Die Preise auf der Produktlistungsseite des Widgets und in Popover werden mithilfe der konfigurierten Währungsraten in die Standardanzeigewährung konvertiert.

### Nicht unterstützte Konfigurationswerte

| Commerce-Konfigurationseinstellungen | Beschreibung | Hinweise |
|---|---|---|
| Stores > Konfiguration > Katalog > Storefront > Listenmodus | Bestimmt das Format der Suchergebnisliste. | Wird korrekt gerendert, aber für einige Seiteninteraktionen werden keine Ereignisse gesendet |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Maximale Abfragelänge | Die maximal zulässige Anzahl von Zeichen bei einer Katalogsuche. | Nicht implementiert. Search Services akzeptiert bis zu 255 Zeichen |
| Konfiguration > Vertrieb > Steuern > Preisanzeigeeinstellungen > Produktpreise im Katalog anzeigen | Bestimmt, ob die im Katalog veröffentlichten Produktpreise Steuern enthalten oder ausschließen oder zwei Versionen des Preises anzeigen, eine mit und die andere ohne Steuern |  |
| Stores > Konfiguration > Katalog > Storefront > Produktlisten Sortieren nach | Bestimmt die Sortierreihenfolge der Suchergebnisliste. | Gilt nicht für die [!DNL Live Search] [Seiten-Widget &quot;Produktliste&quot;](plp-styling.md) |

### Suchbegriffe

[!DNL Live Search] unterstützt [Suchbegriffumleitungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) bei Implementierungen, bei denen Adobe Commerce das Routing durchführt, z. B. bei Luma und anderen php-basierten Designs.
