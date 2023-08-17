---
title: "Facettentechnische Hinweise"
description: "Technische Hinweise zur Verwendung von [!DNL Live Search] Facetten."
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Facettentechnische Hinweise

Faceting ist eine leistungsstarke Filtermethode, die mehrere Dimensionen durchsuchbarer statischer und dynamischer Attributwerte als Suchkriterien verwendet.

[!DNL Live Search] verwendet die `productSearch` Abfrage, die Facetten und andere spezifische Daten zurückgibt [!DNL Live Search]. Siehe Abschnitt [`productSearch` Abfrage](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) für Codebeispiele.

## Facettenaggregation

Die Facettenaggregation wird wie folgt durchgeführt: Wenn die Storefront drei Facetten (Kategorien, Farbe und Preis) hat und die Käuferfilter für alle drei Facetten (Farbe = blau, der Preis liegt zwischen 10,00 und 50,00 USD, Kategorien = `promotions`).

* `categories` aggregation - Aggregate `categories`, wendet dann die `color` und `price` Filter, aber nicht die `categories` Filter.
* `color` aggregation - Aggregate `color`, wendet dann die`price` und `categories` Filter, aber nicht die `color` Filter.
* `price` aggregation - Aggregate `price`, wendet dann die `color` und `categories` Filter, aber nicht die `price` Filter.
