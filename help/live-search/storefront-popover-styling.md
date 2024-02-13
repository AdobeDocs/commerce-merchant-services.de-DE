---
title: "Stile [!DNL Popover] Elemente"
description: "Technische Hinweise zum Anpassen der [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 67da9016d4bca9750fa9e440cce08ad1ae7100e2
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Formatierung [!DNL Popover] Elemente

Die [[!DNL storefront popover]](storefront-popover.md) zeigt immer das Produkt an `name` und `price`und die Feldauswahl nicht konfigurierbar ist. Allerdings [!DNL popover] -Elemente können mithilfe von CSS-Klassen formatiert werden. Beispielsweise ändern die folgenden Deklarationen die Hintergrundfarbe der [!DNL popover] Container und Fußzeile.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Behälteranzeige

Die übergeordnete Komponente der `.livesearch.popover-container` is `.search-autocomplete`.  Die `.active` -Klasse gibt die Sichtbarkeit des Containers an. Die `.active` -Klasse wird bedingt hinzugefügt, wenn die [!DNL popover] ist offen.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Weitere Informationen zum Formatieren von Storefront-Elementen finden Sie unter [Kaskadierende Stylesheets (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) im [Frontend-Entwicklerhandbuch](https://developer.adobe.com/commerce/frontend-core/guide/).

## Klassenselektoren

Die folgenden Klassenselektoren können verwendet werden, um den Container und die Produktelemente im [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Container-Klassen-Selektoren

#### .livesearch.popover-container

![[!DNL Popover] container](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![Alle Fußzeilen anzeigen](assets/livesearch-view-all-footer.png)

### Produktklassenauswahl

#### .livesearch.products-container

![Produktcontainer](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Produktergebnis](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Produktname](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Produktpreis](assets/livesearch-product-price.png)

#### .livesearch product-link

![Produktergebnis](assets/livesearch-product-link.png)

## Arbeiten mit einem geänderten Design {#working-with-modified-theme}

Die [!DNL storefront popover] kann mit einer benutzerdefinierten [Design](https://developer.adobe.com/commerce/frontend-core/guide/themes/) , der die erforderlichen Dateien von *Luma*. Die `top.search` -Block im `header-wrapper` des `Magento_Search` darf nicht geändert werden.

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

So deaktivieren Sie die [!DNL popover] und den Standard wiederherstellen [Schnellsuche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) verwenden, geben Sie den folgenden Befehl ein:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
