---
title: Was ist [!DNL Live Search]?
description: '[!DNL Live Search] von Adobe Commerce bietet ein schnelles, relevantes und intuitives Sucherlebnis.'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 7f536c93ab1c87bf88bc892b2a485067fa8f8110
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# Was ist [!DNL Live Search]?

[!DNL Live Search] ist eine Funktion, die die standardmäßigen Suchfunktionen in Adobe Commerce ersetzt. Die Funktion &quot;[!DNL Live Search]&quot; wird mit Composer installiert und verbindet Ihren [!DNL Commerce]-Speicher mit dem [Commerce Services Connector](../landing/saas.md). Wenn es konfiguriert ist, wird das Standardsuchtextfeld durch das Textfeld [!DNL Live Search] ersetzt. [!DNL Live Search] installiert auch das Widget &quot;Product Listing Page&quot;(PLP), das beim Durchsuchen von Suchergebnissen robuste Filterfunktionen bietet.

Mit [!DNL Live Search] können Sie:

- Erstellen Sie aussagekräftige Sucherlebnisse, um Käufern und Käufern zu helfen, mit möglichst wenig Aufwand das zu finden, was sie wollen.
- Nutzen Sie die KI-gestützte dynamische facettierte Suche und das erneute Ranking von Suchergebnissen als Reaktion auf sitzungsinterne Käuferverhaltensweisen.
- Nutzen Sie einen leichten SaaS-Service, der einfache Updates bietet und in Ihrer Lizenz enthalten ist, was die Gesamtbetriebskosten reduziert.
- Technische Unterstützung erhalten Sie durch die Aktivierung der GraphQL-API, Headless-Flexibilität, API-Sandbox-Umgebungen und besonders schnelles SaaS.

>[!IMPORTANT]
>
>Wenn es um die Site-Suche geht, bietet Ihnen Adobe Commerce Optionen. Überprüfen Sie vor der Implementierung die Informationen zu [Grenzen und Beschränkungen](boundaries-limits.md) , um sicherzustellen, dass [!DNL Live Search] Ihren Geschäftsanforderungen entspricht.

## Architektur

Die Adobe Commerce-Seite der Architektur umfasst das Hosten der Suche *Admin*, das Synchronisieren von Katalogdaten und das Ausführen des Abfragedienstes. Nachdem [!DNL Live Search] installiert und konfiguriert wurde, beginnt Adobe Commerce mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Admin-Benutzer die Suche [facets](facets.md), [synonyme](synonyms.md) und [Merchandising-Regeln](category-merch.md) einrichten, anpassen und verwalten.

![Live-Suchdatenfluss](assets/ls-cs-data-flow.png)

## Quick Tour

Mit dem Fokus auf Geschwindigkeit, Relevanz und Benutzerfreundlichkeit ist [!DNL Live Search] ein Wendepunkt für Käufer und Händler gleichermaßen. Sehen Sie sich das folgende Video an und nehmen Sie dann eine kurze Tour durch [!DNL Live Search] von der Storefront.

>[!VIDEO](https://video.tv.adobe.com/v/3418797?learn=on)

Ein ausführlicheres Video zur Verwendung und Konfiguration der Live-Suche finden Sie im Thema [Vollständige Demonstration zu [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) .

### Suchen nach der Eingabe

[!DNL Live Search] antwortet mit empfohlenen Produkten und einem Miniaturbild der Top-Suchergebnisse in einem [Popup](storefront-popover.md), wenn der Käufer Abfragen in das Feld [Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) eingibt. Die Seite mit den [Produktdetails](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) wird angezeigt, wenn Käufer auf ein vorgeschlagenes oder vorgestelltes Produkt klicken. Ein _Alle_ -Link in der Fußzeile des Popups anzeigen zeigt die Seite mit den Suchergebnissen an.

[!DNL Live Search] gibt Ergebnisse für eine Abfrage von zwei oder mehr Zeichen &quot;Suche beim Eingeben&quot;zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in der Abfrage kann nicht konfiguriert werden. Das Popover enthält die Felder `name`, `sku` und `category_ids`.

![Beispiel-Storefront - Suche beim Eingeben von ](assets/storefront-search-as-you-type.png)

### Alle Suchergebnisse anzeigen

Um alle von der Abfrage &quot;Suche beim Eingeben&quot;zurückgegebenen Produkte aufzulisten, klicken Sie in der Fußzeile des Popover auf _Alle anzeigen_ .

![Beispiel-Storefront - Preisfacetten](assets/storefront-view-all-search-results.png)

### Gefilterte Suche mit Facetten

Gefilterte Suche verwendet mehrere Dimensionen von Attributwerten oder [Facetten](facets.md) als Suchkriterien. Die Auswahl der Filter wird vom Händler definiert und ändert sich entsprechend den zurückgegebenen Produkten, wobei die am häufigsten verwendeten Facetten oben in der Liste platziert werden.

Verwenden Sie Facetten als URL-Parameter:`http://yourwebsite.com?color=red`, und die Live-Suche filtert Ergebnisse basierend auf diesen Attributwerten.

### Synonyme

[Synonyme](synonyms.md) erweitern die Reichweite und schärfen den Fokus von Abfragen, indem Wörter einbezogen werden, die von denen im Katalog abweichen. Sie können das Synonym-Wörterbuch anpassen, um die Interaktion der Käufer und den Weg zum Kauf zu gewährleisten.

### Merchandising-Regeln

Merchandising [rules](rules.md) prägt das Einkaufserlebnis mit if-then-Anweisungen, die Logik und Ereignisse zur Suche hinzufügen. Sie können Produkte für eine Promotion, eine Saison oder einen anderen Zeitraum einfach steigern oder begraben.

### Suchbegriffe - Unterstützung

[!DNL Live Search] unterstützt Commerce [Umleitungen von Suchbegriffen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms). Beispielsweise können Benutzer nach einem Begriff wie &quot;Versandtarife&quot;suchen und direkt zur Versandtarifseite gelangen.

## Live Search-Komponenten

- [!DNL Live Search] [Popover-Widget](storefront-popover.md) ist das Feld, das unter dem Suchfeld geöffnet wird, das die Suchergebnisse enthält.
- Das Widget [Seite mit Produktauflistungen](plp-styling.md) (PLP) bietet eine durchsuchbare Seite mit Produktauflistungen mit Facetten und Synonym-Unterstützung. Das Widget wird in Live Search 4.0.0 oder höher installiert und aktiviert.
- (**Veraltet**) Der Suchadapter war der Vorläufer des PLP-Widgets und wurde mit Live Search &lt; 4.0.0 installiert. Wenn Sie eine Live Search-Version verwenden, die älter als Version 4.0.0 ist, empfiehlt Commerce ein Upgrade, um die Vorteile der PLP-Widget-Funktionen und künftigen Verbesserungen zu erhalten.

## [!DNL Live Search] Arbeitsbereich

Der [!DNL Live Search] [Arbeitsbereich](workspace.md) ist der Bereich im Admin, in dem Sie [!DNL Live Search]-Funktionen wie Synonyme, Facetten und Kategorie-Merchandising konfigurieren.

## Veranstaltungen

[!DNL Live Search] verwendet [events](events.md) zur Berechnung der [intelligenten Merchandising](category-merch.md)- und [performance](performance.md)-Dashboards. Eventing wird mit Standardimplementierungen bereitgestellt. Eventing für Headless-Storefronts sollte manuell aktiviert werden.
