---
title: Seiten-Widget "Produktliste"
description: "Aktivieren und Gestalten der [!DNL Live Search Product Listing Page Widget]"
source-git-commit: c4bca0c7238be653dd13b051634c662e5891767d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Seiten-Widget &quot;Produktliste&quot;

Die [!DNL Live Search Product Listing Page Widget] (PLP) verwendet die Commerce Services-Plattform, um eine leistungsfähige, durchsuchbare und facettenfähige Produktanlistungsseite bereitzustellen. Hier wird beschrieben, wie Sie das PLP-Widget aktivieren und gestalten.

## Aktivieren des PLP-Widgets

Wenn die [!DNL Live Search] -Dienst installiert ist, wird die Standardsuchfunktion in [!DNL Live Search] automatisch.
Das PLP-Widget muss in der Admin-Konsole aktiviert sein.

1. Navigieren Sie zu **Stores** > Einstellungen > **Konfiguration** > **[!DNL Live Search]** > **Storefront-Funktionen** und **Enable Product Listing Widgets** auf &quot;Ja&quot;.
1. Auswählen **Konfiguration speichern** , um die Einstellung zu speichern.

## Stilbeispiel

Sie können das Erscheinungsbild des PLP-Widgets so anpassen, dass es zu Ihrer Site passt, indem Sie [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Elemente mit benutzerdefinierten Klassen innerhalb eines Adobe Commerce-Designs werden nicht vererbt. Diese Elemente müssen durch ihre spezifische Klasse als Ziel ausgewählt werden, um die benutzerdefinierten Klassen abzugleichen. Primäre Aktionsklassen funktionieren nicht auf einer Widget-Schaltfläche.
>Generische Targeting-Elemente innerhalb des CSS werden vererbt. `button` wird auf Widget-Schaltflächen angewendet.

Die hervorgehobenen Divs enthalten die Zielklasse `ds-sdk-product-item__product-name`.

![Paginierung](assets/plp-css-example.png)

Passen Sie den Produktnamen an, indem Sie eine Regel hinzufügen, um sie in Großbuchstaben zu versetzen.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![Paginierung](assets/plp-css-example-after.png)

## CSS-Klassen

### Produktliste

* `.ds-sdk-product-list`: Außenbereich
* `.ds-sdk-product-list__grid`: Inner div

![Paginierung](assets/plp-css-product-list.png)

#### Paginierung von Produktlisten

* `.ds-plp-pagination`

![Paginierung](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![Paginierungselement](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![Aktuelles Element &quot;Paginierung&quot;](assets/plp-css-pagination-item-current.png)

### Widgets

* `.ds-widgets`: Außenbereich
* `.ds-widgets__actions`: Linkes seitliches inneres Div
* `.ds-widgets__results`: Rechtes inneres Div

![Widget-Ergebnisse](assets/plp-css-widgets.png)

### Sortieren-Dropdown

* `.ds-sdk-sort-dropdown`

![Sortieren-Dropdown](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![Dropdown-Schaltfläche](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![Dropdown-Elemente](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![Dropdown-Element](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![Ausgewähltes Element Dropdown](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![Dropdown-aktive Auswahl](assets/plp-css-dropdown-active.png)

### Facets

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![Facet-Kopfzeilentitel](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![Facettentabletten](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![Facette-Bezeichnung](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![Facettenliste](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-input__options`
* `.ds-sdk-input_fieldset_show-more`

![Eingabe](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![Beschriftte Eingabe](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![Eingabebezeichnung](assets/plp-css-labelled-input-label.png)

### Produktelement

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![Produkt](assets/plp-css-product.png)

### Laden

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![Ladeanzeige](assets/plp-css-loading.png)
