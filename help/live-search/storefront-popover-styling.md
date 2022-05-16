---
title: '"Stile [!DNL Popover] Elemente"'
description: '"Technische Hinweise zur Anpassung der [!DNL Live Search storefront popover]"'
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Formatierung [!DNL Popover] Elemente

Die [[!DNL storefront popover]](storefront-popover.md) zeigt immer das Produkt an `name` und `price`und die Feldauswahl nicht konfigurierbar ist. Allerdings [!DNL popover] -Elemente können mit CSS-Klassen formatiert werden. Beispielsweise ändern die folgenden Deklarationen die Hintergrundfarbe der [!DNL popover] Container und Fußzeile.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Container-Sichtbarkeit

Die übergeordnete Komponente der `.livesearch.popover-container` is `.search-autocomplete`.  Die `.active` -Klasse gibt die Sichtbarkeit des Containers an. Die `.active` -Klasse wird bedingt hinzugefügt, wenn die [!DNL popover] ist offen.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Weitere Informationen zum Formatieren von Storefront-Elementen finden Sie unter [Kaskadierende Stylesheets (CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) im [Frontend-Entwicklerhandbuch](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

## Klassenselektoren

Die folgenden Klassenselektoren können verwendet werden, um den Container, die Empfehlung und die Produktelemente im [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.suggestions-container`
* `.livesearch.suggestions-header`
* `.livesearch.suggestion`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Container-Klassenauswahl

`.livesearch.popover-container`

![[!DNL Popover] container](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![Alle Fußzeilen anzeigen](assets/livesearch-view-all-footer.png)

### Empfehlungen-Klassenauswahl

`.livesearch.suggestions-container`
![Container mit Empfehlungen](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`
![Kopfzeile für Vorschläge](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`
![Empfehlung](assets/livesearch-suggestion.png)

### Produktklassenauswahl

`.livesearch.products-container`
![Produktcontainer](assets/livesearch-product-container.png)

`.livesearch.product-result`
![Produktergebnis](assets/livesearch-product-result.png)

`.livesearch.product-name`
![Produktname](assets/livesearch-product-name.png)

`.livesearch.product-price`
![Produktpreis](assets/livesearch-product-price.png)

## Arbeiten mit einem geänderten Design {#working-with-modified-theme}

Die [!DNL storefront popover] kann mit einer benutzerdefinierten [Design](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) , der die erforderlichen Dateien von *Luma*. Die `top.search` im `header-wrapper` des `Magento_Search` darf nicht geändert werden.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Deaktivieren der [!DNL popover]

So deaktivieren Sie die [!DNL popover] und stellen Sie den Standard wieder her [Schnellsuche](https://docs.magento.com/user-guide/catalog/search-quick.html) verwenden, geben Sie den folgenden Befehl ein:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
