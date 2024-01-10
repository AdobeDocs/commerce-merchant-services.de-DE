---
title: "Facets"
description: "[!DNL Live Search] Facetten verwenden mehrere Dimensionen von Attributwerten als Suchkriterien."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 460065ecf6478e4313bd31ea848e04c7e8e192a3
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Facets

Faceting ist eine Methode der Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten als Suchkriterien verwendet werden. Die facettierte Suche ist ähnlich, aber deutlich &quot;schlauer&quot;als die Standardsuche [mehrstufige Navigation](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). Die Liste der verfügbaren Filter wird durch die Variable [filterbare Attribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) der in den Suchergebnissen zurückgegebenen Produkte.

[!DNL Live Search] verwendet die `productSearch` Abfrage, die Facetten und andere spezifische Daten für [!DNL Live Search]. Siehe Abschnitt [`productSearch` Abfrage](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) in der Entwicklerdokumentation für Codebeispiele.

![Gefilterte Suchergebnisse](assets/storefront-search-results-run.png)

Jede definierte Facette kann als URL-Parameter verwendet werden. Die Ergebnisse werden anhand der Parameterwerte gefiltert: `http://yourstore.com?brand=acme&color=red`.

## Factoryanforderungen

Die Anforderungen an Kategorie- und Produktattribute für die Facettierung ähneln den für die Navigation mit Ebenen verwendeten filterbaren Attributen. Für jede Storefront-Eigenschaft eines Attributs muss der Wert &quot;Use in Search Results Layered Navigation&quot;auf &quot;Yes&quot;gesetzt sein.

[!DNL Live Search] unterstützt bis zu:

* 100 Attribute, die als Facetten konfiguriert wurden
* 50 sortierbare Attribute
* 200 filterbare Attribute
* 200 durchsuchbare Attribute

>[!NOTE]
>
> Wenn mehr als 200 filterbare Attribute definiert sind, ist es nicht deterministisch, welcher 200 tatsächlich indiziert wird.

Wenn Sie eine große Anzahl von Attributen haben, mit denen Sie konfrontiert werden können, sollten Sie Attribute zu einem einzelnen &quot;Meta-Attribut&quot;kombinieren. Schuhe haben beispielsweise im Allgemeinen numerische Größen, während Hemden häufig die Größe &quot;S/M/L/XL&quot;aufweisen. Diese beiden Größentypen können zu einem einzigen durchsuchbaren Attribut zusammengefasst werden.

| Einstellung | Beschreibung |
|--- |--- |
| [Anzeigeparameter der Kategorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Anker - `Yes` |
| [Attributeigenschaften](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Katalogeingabetyp](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (nur Widget), `Text swatch` (nur Widget) |
| Eigenschaften von Attributspeicher | Verwendung in der Navigation mit Suchergebnisebenen - `Yes` |

## Facettenaggregation

Die Facettenaggregation wird wie folgt durchgeführt: Wenn die Storefront drei Facetten (Kategorien, Farbe und Preis) hat und die Käuferfilter für alle drei Facetten (Farbe = blau, der Preis liegt zwischen 10,00 und 50,00 USD, Kategorien = `promotions`).

* `categories` aggregation - Aggregate `categories`, wendet dann die `color` und `price` Filter, aber nicht die `categories` Filter.
* `color` aggregation - Aggregate `color`, wendet dann die`price` und `categories` Filter, aber nicht die `color` Filter.
* `price` aggregation - Aggregate `price`, wendet dann die `color` und `categories` Filter, aber nicht die `price` Filter.

## Standardmäßige Attributwerte

Die folgenden Produktattribute haben [Storefront-Eigenschaften](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) , die von [!DNL Live Search] und standardmäßig aktiviert.

| Eigenschaft | Storefront-Eigenschaft | Attribut |
|---|---|---|
| Sortierbar | Wird zur Sortierung in der Produktliste verwendet | `price` |
| Durchsuchbar | Verwendung in der Suche | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Verwendung in Ebenen Navigation - Filtern möglich (mit Ergebnissen) | `price`<br />`visibility`<br />`category_name` |

## Standardmäßige Eigenschaften von Nicht-Systemattributen

Die folgende Tabelle zeigt die standardmäßigen, suchbaren und filterbaren Eigenschaften von Nicht-System-Attributen, einschließlich der Attribute, die für die Luma-Beispieldaten spezifisch sind. Festlegen der *Verwendung in der Suche* Attributeigenschaft auf `Yes` ermöglicht die Suche nach dem Attribut in [!DNL Live Search] und natives Adobe Commerce.

| Attributcode | Durchsuchbar | Verwendung in mehrschichtiger Navigation |
|--- |--- |--- |
| activity | Ja | Filtern möglich (mit Ergebnissen) |
| attributes_brand | Ja | Nein |
| Marke | Ja | Nein |
| Klima | Ja | Filtern möglich (mit Ergebnissen) |
| Kragen | Ja | Filtern möglich (mit Ergebnissen) |
| color | Ja | Filtern möglich (mit Ergebnissen) |
| Kosten | Ja | Nein |
| eco_collection | Ja | Filtern möglich (mit Ergebnissen) |
| gender | Ja | Filtern möglich (mit Ergebnissen) |
| Hersteller | Ja | Filtern möglich (mit Ergebnissen) |
| Material | Ja | Filtern möglich (mit Ergebnissen) |
| Zweck | Ja | Filtern möglich (mit Ergebnissen) |
| strap_bags | Ja | Filtern möglich (mit Ergebnissen) |
| style_general | Ja | Filtern möglich (mit Ergebnissen) |

## Standardmäßige Systemattributeigenschaften

Die folgende Tabelle zeigt die standardmäßigen, suchbaren und filterbaren Eigenschaften von Systemattributen.

| Attributcode | Durchsuchbar | Verwendung in mehrschichtiger Navigation |
|--- |--- |--- |
| allow_open_amount | Ja | Filtern möglich (mit Ergebnissen) |
| description | Ja | Nein |
| name | Ja | Nein |
| price | Ja | Filtern möglich (mit Ergebnissen) |
| short_description | Ja | Nein |
| sku | Ja | Nein |
| status | Ja | Nein |
| tax_class_id | Ja | Nein |
| url_key | Ja | Nein |
| Gewichtung | Ja | Nein |
