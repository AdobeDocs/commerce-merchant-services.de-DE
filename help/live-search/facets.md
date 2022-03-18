---
title: Facets
description: Live-Suchfacetten verwenden mehrere Dimensionen von Attributwerten als Suchkriterien.
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Facets

Faceting ist eine Methode der Hochleistungsfilterung, bei der mehrere Dimensionen von Attributwerten als Suchkriterien verwendet werden. Die facettierte Suche ist ähnlich, aber deutlich &quot;schlauer&quot;als die Standardsuche [mehrstufige Navigation](https://docs.magento.com/user-guide/catalog/navigation-layered.html). Die Liste der verfügbaren Filter wird durch die Variable [filterbare Attribute](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) der in den Suchergebnissen zurückgegebenen Produkte. Es können bis zu 100 Facetten konfiguriert werden mit [!DNL Live Search].

![Gefilterte Suchergebnisse](assets/storefront-search-results-run.png)

## Factoryanforderungen

Die Anforderungen an Kategorie- und Produktattribute für die Facettierung ähneln den für die Navigation mit Ebenen verwendeten filterbaren Attributen. Die Storefront-Eigenschaften jedes Attributs müssen auf `filterable (with results)`.

| Einstellung | Beschreibung |
|--- |--- |
| [Anzeigeparameter der Kategorie](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | Anker - `Yes` |
| [Attributeigenschaften](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [Katalogeingabetyp](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Eigenschaften von Attributspeicher | Verwendung in mehrschichtiger Navigation - `Filterable (with results)` |

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
