---
title: Seiten-Widget "Produktliste"
description: Aktivieren und Gestalten der [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: faf217486d57588d8535c1d605e963c91ec3ee68
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Seiten-Widget &quot;Produktliste&quot;

Die [!DNL Live Search Product Listing Page Widget] (PLP) verwendet die Commerce Services-Plattform, um eine leistungsfähige, durchsuchbare und facettenfähige Produktseite bereitzustellen. Hier wird beschrieben, wie Sie das PLP-Widget aktivieren und gestalten.

## Aktivieren des PLP-Widgets

Wenn die Variable [!DNL Live Search] installiert ist, wird die Standardsuchfunktion in [!DNL Live Search] automatisch.

Die [!DNL Live Search] PLP-Widget ist für neue Installationen standardmäßig aktiviert. Wenn Sie ein Upgrade [!DNL Live Search] und das PLP-Widget bereits deaktiviert wurde, bleibt es so.

>[!IMPORTANT]
>
>Wenn die Variable [!DNL Live Search Product Listing Page Widget] aktiviert ist, kann die Sortierreihenfolge auf einer Produktlistenseite nicht geändert werden.

## Widget-Funktionen

Das PLP-Widget bietet die folgenden nativen Funktionen:

- Zum Warenkorb hinzufügen - Nur für einfache Produkte verfügbar.
- Mehrere Bilder pro Produkt - Das Bild kann sich ändern, wenn für ein konfigurierbares Produkt eine andere Farbe ausgewählt wird.
- Unterstützung für Farbmuster - Beachten Sie, dass das Farbattribut geschrieben werden muss `color` , damit der Code ordnungsgemäß validiert wird.

### Anpassen des Widgets

Zusätzlich zu den vordefinierten Funktionen des PLP-Widgets können Sie das Widget weiter anpassen, um die folgenden Funktionen einzuschließen:

- Filtern nach Attributen
- Unterstützung mehrerer Sprachen
- Preisregler

Informationen zum Anpassen des PLP-Widgets für die oben genannten Funktionen finden Sie in der `storefront-product-listing-page` Lesen Sie die folgenden Informationen: [repo](https://github.com/adobe/storefront-product-listing-page/).

>[!WARNING]
>
>Wenn Sie das PLP-Widget mithilfe des im Repository verfügbaren Codes anpassen, sind Sie für die Wartung und erforderliche Updates verantwortlich. Alle neuen PLP-Widget-Funktionen, die von Adobe veröffentlicht werden, sind möglicherweise nicht mit Ihrer benutzerdefinierten Implementierung kompatibel.

## Stilbeispiel

Sie können das Erscheinungsbild des PLP-Widgets so anpassen, dass es zu Ihrer Site passt, indem Sie [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Elemente mit benutzerdefinierten Klassen innerhalb eines Adobe Commerce-Designs werden nicht vererbt. Diese Elemente müssen von ihrer jeweiligen Klasse angesprochen werden, um mit den benutzerdefinierten Klassen übereinstimmen. Primäre Aktionsklassen funktionieren nicht mit Widget-Schaltflächen. Generische Targeting-Elemente innerhalb des CSS werden vererbt. `button` gilt für Widget-Schaltflächen.

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

- `.ds-sdk-product-list`: Externes div
- `.ds-sdk-product-list__grid`: Inner div

![Paginierung](assets/plp-css-product-list.png)

#### Paginierung von Produktlisten

- `.ds-plp-pagination`

![Paginierung](assets/plp-css-pagination.png)

- `.ds-plp-pagination_item`

![Paginierungselement](assets/plp-css-pagination-item.png)

- `.ds-plp-pagination_item--current`

![Aktuelles Element &quot;Paginierung&quot;](assets/plp-css-pagination-item-current.png)

### Widgets

- `.ds-widgets`: Externes div
- `.ds-widgets__actions`: Linkes seitliches inneres Div
- `.ds-widgets__results`: Rechtsseitiges inneres Div

![Widget-Ergebnisse](assets/plp-css-widgets.png)

### Sortieren-Dropdown

- `.ds-sdk-sort-dropdown`

![Sortieren-Dropdown](assets/plp-css-dropdown.png)

- `.ds-sdk-sort-dropdown__button`

![Dropdown-Schaltfläche](assets/plp-css-dropdown-button.png)

- `.ds-sdk-sort-dropdown__items`

![Dropdown-Elemente](assets/plp-css-dropdown-items.png)

- `.ds-sdk-sort-dropdown__items--item`

![Dropdown-Element](assets/plp-css-dropdown-item.png)

- `.ds-sdk-sort-dropdown__items--item-selected`

![Ausgewähltes Element Dropdown](assets/plp-css-dropdown-selected.png)

- `.ds-sdk-sort-dropdown__items--item-active`

![Dropdown-aktive Auswahl](assets/plp-css-dropdown-active.png)

### Facets

- `.ds-plp-facets`
- `.ds-plp-facets__header`
- `.ds-plp-facets__header_title`
- `.ds-plp-facets__header__clear-all`

![Facet-Kopfzeilentitel](assets/plp-css-facets-title-clear.png){width="350"}

- `.ds-plp-facets__pills`
- `.ds-sdk-pill`

![Facettentabletten](assets/plp-css-facets-pill.png){width="350"}

- `.ds-sdk-pill__label`
- `.ds-sdk-pill__cta`

![Facette-Bezeichnung](assets/plp-css-pill-label-cta.png){width="350"}

- `.ds-plp-facets__list`

![Facettenliste](assets/plp-css-facets-list.png){width="350"}

- `.ds-sdk-input`
- `.ds-sdk-input__label`
- `.ds-sdk-product-item__product-swatch-group`
- `ds-sdk-product-item__product-swatch-item`
- `.ds-sdk-input_fieldset_show-more`

![Eingabe](assets/plp-css-sdk-input.png)

- `.ds-sdk-labelled-input`

![Beschriftte Eingabe](assets/plp-css-labelled-input.png)

- `.ds-sdk-labelled-input__input`
- `.ds-sdk-labelled-input__label`

![Eingabebezeichnung](assets/plp-css-labelled-input-label.png)

### Produktelement

- `.ds-sdk-product-item`
- `.ds-sdk-product-item__image`
- `.ds-sdk-product-item__product-name`
- `.ds-sdk-product-item__product-options`
- `.ds-sdk-product-price`
   - `.ds-sdk-product-price--no-discount`
   - `.ds-sdk-product-price--grouped`
   - `.ds-sdk-product-price--bundle`
   - `.ds-sdk-product-price--discount`

![Produkt](assets/plp-css-product.png)

### Laden

- `.ds-sdk-loading`
- `.ds-sdk-loading__spinner`
- `.ds-sdk-loading__spinner-label`

![Ladeanzeige](assets/plp-css-loading.png)

## Deaktivieren des PLP-Widgets

So deaktivieren Sie das PLP-Widget:

1. Navigieren Sie zu **Stores** > Einstellungen > **Konfiguration** > **[!DNL Live Search]** > **Storefront-Funktionen** und **Enable Product Listing Widgets** auf &quot;Nein&quot;.
1. Auswählen **Konfiguration speichern** , um die Einstellung zu speichern.
