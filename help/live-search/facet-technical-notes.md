---
title: Facettentechnische Hinweise
description: Technische Hinweise zur Verwendung von Live-Suchfacetten.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
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

## Standardmäßige Attributwerte

Die folgenden Produktattribute haben einige [Storefront-Eigenschaften](https://docs.magento.com/user-guide/stores/attributes-product.html) die standardmäßig aktiviert sind.

| Eigenschaft | Storefront-Eigenschaft | Attribut |
|---|---|---|
| Sortierbar | Wird zur Sortierung in der Produktliste verwendet | `price` |
| Durchsuchbar | Verwendung in der Suche | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Verwendung in Ebenen Navigation - Filtern möglich (mit Ergebnissen) | `price`<br />`visibility`<br />`category_name` |
