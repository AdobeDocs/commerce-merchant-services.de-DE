---
title: "Quick Tour"
description: "Machen Sie einen kurzen Überblick über [!DNL Live Search] aus der Storefront."
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 9cf48f6f900385a5cb772adee8834ec9cfe5ee13
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Quick Tour

mit dem Schwerpunkt auf Geschwindigkeit, Relevanz und Benutzerfreundlichkeit, [!DNL Live Search] ist ein Spielveränderer für Käufer und Händler gleichermaßen. Folgen Sie dem Abschnitt für eine kurze Übersicht [!DNL Live Search] von der Schaufensterfront aus.

## Suchen nach der Eingabe

[!DNL Live Search] antwortet mit vorgeschlagenen Produkten und einem Miniaturbild der Top-Suchergebnisse in einer [Popover](storefront-popover.md) als Käufer Abfragen in die [Suche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ankreuzen. Die [Produktdetails](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) wird angezeigt, wenn Kunden auf ein vorgeschlagenes oder vorgestelltes Produkt klicken. A _Alle anzeigen_ -Link in der Fußzeile des Popups zeigt die Suchergebnisseite an.

[!DNL Live Search] gibt Ergebnisse vom Typ &quot;Suche beim Eingeben&quot;für eine Abfrage von zwei oder mehr Zeichen zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in der Abfrage kann nicht konfiguriert werden. Die folgenden Felder sind im Popover enthalten: `name`, `sku`, und `category_ids`.

![Beispiel-Storefront - Suche während der Eingabe](assets/storefront-search-as-you-type.png)

## Alle Suchergebnisse anzeigen

Um alle von der Abfrage &quot;Suche beim Eingeben&quot;zurückgegebenen Produkte aufzulisten, klicken Sie auf _Alle anzeigen_ in der Fußzeile des Popups.

![Beispiel-Storefront - Preisfacetten](assets/storefront-view-all-search-results.png)

## Gefilterte Suche mit Facetten

Gefilterte Suche verwendet mehrere Dimensionen von Attributwerten oder [facets](facets.md)als Suchkriterien. Die Auswahl der Filter wird vom Händler definiert und ändert sich entsprechend den zurückgegebenen Produkten, wobei die am häufigsten verwendeten Facetten oben in der Liste platziert werden.

Verwenden Sie Facetten als URL-Parameter:`http://yourwebsite.com?color=red`und die Live-Suche filtert Ergebnisse basierend auf diesen Attributwerten.

## Synonyme

[Synonyme](synonyms.md) Erweitern Sie die Reichweite und schärfen Sie den Fokus von Abfragen, indem Sie Wörter einschließen, die von denen im Katalog abweichen könnten. Sie können das Synonym-Wörterbuch anpassen, um die Interaktion der Käufer und den Weg zum Kauf zu gewährleisten.

## Merchandising-Regeln

Merchandising [Regeln](rules.md) gestalten Sie das Einkaufserlebnis mit if-then-Anweisungen, die Logik und Ereignisse zur Suche hinzufügen. Sie können Produkte für eine Promotion, eine Saison oder einen anderen Zeitraum einfach steigern oder begraben.
