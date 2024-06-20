---
title: "[!DNL Storefront Popover]"
description: "Die [!DNL Live Search storefront popover] gibt dynamisch vorgeschlagene Produkte und Miniaturansichten zurück."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Wann [!DNL Live Search] is [installiert](install.md), a [!DNL popover] erscheint in der Storefront, wenn der Käufer im Feld [Suche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ankreuzen. Mit jedem eingegebenen Zeichen muss die [!DNL popover] wird mit vorgeschlagenen Produkten und Miniaturbildern der wichtigsten Suchergebnisse aktualisiert.

[!DNL Live Search] gibt Ergebnisse für eine Abfrage von zwei Zeichen oder mehr zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ &quot;Suche beim Eingeben&quot; ist nicht konfigurierbar.

Standardmäßig ist [!DNL Live Search] unterstützt [Suchbegriffumleitungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Erfahren Sie, wie Sie Produktattribute in der [Einrichten der Live-Suche](workspace.md) Artikel.

## [!DNL Popover] Seitengröße

Die Seitengröße der [!DNL popover] bestimmt, wie viele Zeilen von automatisch ausgefüllten Produkten zurückgegeben werden können. Während der Live Search-Installation wird die Variable `page_size` -Wert ändert sich in den aktuellen Wert der [Katalogsuche](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` -Einstellung.

Standardmäßig ist der Wert Katalogsuche - Automatische Vervollständigungsgrenze auf acht Zeilen (oder Zeilen) festgelegt. So ändern Sie die Seitengröße der [!DNL popover]führen Sie folgende Schritte aus:

1. Im *Admin* Seitenleiste, navigieren Sie zu **Stores** > Einstellungen > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Katalog** und wählen **Katalog** aus der Liste der Einstellungen.
1. Erweitern Sie die *Katalogsuche* Abschnitt.
1. Legen Sie die **Automatische Vervollständigungsgrenze** auf die Anzahl der Zeilen, die Sie in der Variablen [!DNL popover].
1. Wenn Sie fertig sind, klicken Sie auf **Konfiguration speichern**.

## Formatierung [!DNL Popover] example

Sie können das Erscheinungsbild der [!DNL Popover] -Widget an den Stil und die Branding-Richtlinien Ihres Unternehmens anzupassen.

Die [!DNL storefront popover] zeigt immer das Produkt an `name` und `price`und die Feldauswahl nicht konfigurierbar ist. Allerdings [!DNL popover] -Elemente können mit [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) Klassen. Beispielsweise ändern die folgenden Deklarationen die Hintergrundfarbe der [!DNL popover] Container und Fußzeile.

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

Sie können die folgenden Klassenselektoren verwenden, um den Container und die Produktelemente im [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

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

Sie können die [!DNL storefront popover] mit einer benutzerdefinierten [Design](https://developer.adobe.com/commerce/frontend-core/guide/themes/) , der die erforderlichen Dateien von *Luma*. Die `top.search` -Block im `header-wrapper` des `Magento_Search` darf nicht geändert werden.

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

## Headless-Implementierungen

Für Implementierungen mit Headless können Sie die [!DNL Live Search popover] mithilfe einer [npm package](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
