---
title: Was ist [!DNL Live Search]?
description: "[!DNL Live Search] von Adobe Commerce bietet eine schnelle, relevante und intuitive Sucherfahrung."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 362592eae354b43a3bf98e2839ffe90c21fd3593
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# Was ist [!DNL Live Search]?

[!DNL Live Search] ist eine Funktion, die die standardmäßigen Suchfunktionen in Adobe Commerce ersetzt. Die [!DNL Live Search] -Funktion mit Composer installiert ist und Ihre [!DNL Commerce] speichern in [Commerce Services Connector](../landing/saas.md). Wenn es konfiguriert ist, wird das standardmäßige Suchtextfeld durch das [!DNL Live Search] Textfeld. [!DNL Live Search] installiert außerdem das Widget &quot;Product Listing Page&quot;(PLP), das beim Durchsuchen von Suchergebnissen robuste Filterfunktionen bietet.

Mit [!DNL Live Search]können Sie:

- Erstellen Sie aussagekräftige Sucherlebnisse, um Käufern und Käufern zu helfen, mit möglichst wenig Aufwand das zu finden, was sie wollen.
- Nutzen Sie die KI-gestützte dynamische facettierte Suche und das erneute Ranking von Suchergebnissen als Reaktion auf sitzungsinterne Käuferverhaltensweisen.
- Nutzen Sie einen leichten SaaS-Service, der einfache Updates bietet und in Ihrer Lizenz enthalten ist, was die Gesamtbetriebskosten reduziert.
- Nutzen Sie technische Unterstützung durch die Aktivierung der graphQL-API, der Headless-Flexibilität, API-Sandbox-Umgebungen und der besonders schnellen SaaS.

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie vor der Implementierung die [Grenzen und Grenzen](boundaries-limits.md) Informationen, die sicherstellen, dass [!DNL Live Search] ist für Ihre Geschäftsanforderungen geeignet.

## Architektur

Die Adobe Commerce-Seite der Architektur umfasst das Hosten der Suche *Admin*, Synchronisieren Sie Katalogdaten und führen Sie den Abfragedienst aus. Nachher [!DNL Live Search] installiert und konfiguriert ist, beginnt Adobe Commerce mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Administratoren die Suche einrichten, anpassen und verwalten [facets](facets.md), [Synonyme](synonyms.md), und [Merchandisingregeln](category-merch.md).

![Live-Suchdatenfluss](assets/ls-cs-data-flow.png)

## Quick Tour

mit dem Schwerpunkt auf Geschwindigkeit, Relevanz und Benutzerfreundlichkeit, [!DNL Live Search] ist ein Spielveränderer für Käufer und Händler gleichermaßen. Sehen Sie sich das folgende Video an und nehmen Sie eine kurze Tour durch [!DNL Live Search] von der Schaufensterfront aus.

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Ein detaillierteres Video zur Verwendung und Konfiguration der Live-Suche finden Sie unter [Vollständige Demonstration auf [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) Thema.

### Suchen nach der Eingabe

[!DNL Live Search] antwortet mit vorgeschlagenen Produkten und einem Miniaturbild der Top-Suchergebnisse in einer [Popover](storefront-popover.md) als Käufer Abfragen in die [Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) ankreuzen. Die [Produktdetails](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) wird angezeigt, wenn Kunden auf ein vorgeschlagenes oder vorgestelltes Produkt klicken. A _Alle anzeigen_ -Link in der Fußzeile des Popups zeigt die Suchergebnisseite an.

[!DNL Live Search] gibt Ergebnisse vom Typ &quot;Suche beim Eingeben&quot;für eine Abfrage von zwei oder mehr Zeichen zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in der Abfrage kann nicht konfiguriert werden. Das Popover enthält die`name`, `sku`, und `category_ids` -Felder.

![Beispiel-Storefront - Suche während der Eingabe](assets/storefront-search-as-you-type.png)

### Alle Suchergebnisse anzeigen

Um alle von der Abfrage &quot;Suche beim Eingeben&quot;zurückgegebenen Produkte aufzulisten, klicken Sie auf _Alle anzeigen_ in der Fußzeile des Popups.

![Beispiel-Storefront - Preisfacetten](assets/storefront-view-all-search-results.png)

### Gefilterte Suche mit Facetten

Gefilterte Suche verwendet mehrere Dimensionen von Attributwerten oder [facets](facets.md)als Suchkriterien. Die Auswahl der Filter wird vom Händler definiert und ändert sich entsprechend den zurückgegebenen Produkten, wobei die am häufigsten verwendeten Facetten oben in der Liste platziert werden.

Verwenden Sie Facetten als URL-Parameter:`http://yourwebsite.com?color=red`und die Live-Suche filtert Ergebnisse basierend auf diesen Attributwerten.

### Synonyme

[Synonyme](synonyms.md) Erweitern Sie die Reichweite und schärfen Sie den Fokus von Abfragen, indem Sie Wörter einschließen, die von denen im Katalog abweichen könnten. Sie können das Synonym-Wörterbuch anpassen, um die Interaktion der Käufer und den Weg zum Kauf zu gewährleisten.

### Merchandising-Regeln

Merchandising [Regeln](rules.md) gestalten Sie das Einkaufserlebnis mit if-then-Anweisungen, die Logik und Ereignisse zur Suche hinzufügen. Sie können Produkte für eine Promotion, eine Saison oder einen anderen Zeitraum einfach steigern oder begraben.

### Suchbegriffe - Unterstützung

[!DNL Live Search] unterstützt Commerce [Suchbegriffumleitungen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms). Beispielsweise können Benutzer nach einem Begriff wie &quot;Versandtarife&quot;suchen und direkt zur Versandtarifseite gelangen.

## Live Search-Komponenten

- [!DNL Live Search] [Popover-Widget](storefront-popover.md) ist das Feld, das unter dem Suchfeld geöffnet wird, das die Suchergebnisse enthält.
- [Widget &quot;Seite für Produktauflistung&quot;](plp-styling.md) (PLP) bietet eine durchsuchbare Produktlistenseite mit Facetten- und Synonym-Unterstützung. Das Widget wird in Live Search 4.0.0 oder höher installiert und aktiviert.
- (**Veraltet**) Der Suchadapter war der Vorläufer des PLP-Widgets und wurde mit Live Search &lt; 4.0.0 installiert. Wenn Sie eine Live Search-Version verwenden, die älter als Version 4.0.0 ist, empfiehlt Commerce ein Upgrade, um die Vorteile der PLP-Widget-Funktionen und künftigen Verbesserungen zu erhalten.

## [!DNL Live Search] Arbeitsbereich

Die [!DNL Live Search] [Arbeitsbereich](workspace.md) ist der Bereich im Admin, in dem Sie [!DNL Live Search] Funktionen wie Synonyme, Facetten und Kategorie-Merchandising.

## Veranstaltungen

[!DNL Live Search] uses [events](events.md) berechnet [Intelligente Merchandising](category-merch.md) und [Leistung](performance.md) Dashboards. Eventing wird mit Standardimplementierungen bereitgestellt. Eventing für Headless-Storefronts sollte manuell aktiviert werden.
