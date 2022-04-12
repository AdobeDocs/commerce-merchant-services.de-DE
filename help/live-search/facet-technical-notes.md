---
title: Facettentechnische Hinweise
description: Technische Hinweise zur Verwendung von Live-Suchfacetten.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Facettentechnische Hinweise

Faceting ist eine leistungsstarke Filtermethode, die mehrere Dimensionen durchsuchbarer statischer und dynamischer Attributwerte als Suchkriterien verwendet.

[!DNL Live Search] verwendet die `productSearch` Abfrage, die Facetten und andere Daten zurückgibt, die spezifisch für [!DNL Live Search]. Siehe [`productSearch` Abfrage](https://devdocs.magento.com/live-search/product-search.html) für Codebeispiele.

## Facettenaggregation

Die Facettenaggregation wird wie folgt durchgeführt, wenn die Storefront drei Facetten hat (Kategorien, Farbe und Preis) und die Käuferfilter für alle drei Facetten (Farbe = blau, Preis ist von 10,00-50,00 USD, Kategorien = `promotions`).

* `categories` aggregation - Aggregate `categories`, gilt `color` und `price` Filter, aber nicht die `categories` Filter.
* `color` aggregation - Aggregate `color`, gilt `price` und `categories` Filter, aber nicht die `color` Filter.
* `price` aggregation - Aggregate `price`, gilt `color` und `categories` Filter, aber nicht die `price` Filter.
