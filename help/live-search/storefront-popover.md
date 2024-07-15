---
title: "[!DNL Storefront Popover]"
description: "Der [!DNL Live Search storefront popover] gibt dynamisch vorgeschlagene Produkte und Miniaturansichten zurück."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Wenn [!DNL Live Search] den Wert [installed](install.md) aufweist, wird in der Storefront ein Wert [!DNL popover] angezeigt, wenn der Käufer den Wert in das Feld [Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) eingibt. Bei jedem eingegebenen Zeichen wird der [!DNL popover] mit den vorgeschlagenen Produkten und Miniaturbildern der Top-Suchergebnisse aktualisiert.

[!DNL Live Search] gibt Ergebnisse für eine Abfrage von zwei Zeichen oder mehr zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ &quot;Suche beim Eingeben&quot; ist nicht konfigurierbar.

Standardmäßig unterstützt [!DNL Live Search] [Umleitungen von Suchbegriffen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Erfahren Sie, wie Sie im Artikel [Einrichten der Live-Suche](workspace.md) Produktattribute als durchsuchbar festlegen.

## [!DNL Popover] Seitengröße

Die Seitengröße von [!DNL popover] bestimmt, wie viele Zeilen von automatisch ausgefüllten Produkten zurückgegeben werden können. Während der Live-Suchinstallation ändert sich der Wert `page_size` in den aktuellen Wert der Einstellung [Katalogsuche](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` .

Standardmäßig ist der Wert Katalogsuche - Automatische Vervollständigungsgrenze auf acht Zeilen (oder Zeilen) festgelegt. Gehen Sie wie folgt vor, um die Seitengröße von [!DNL popover] zu ändern:

1. Wechseln Sie in der Seitenleiste *Admin* zu **Stores** > Einstellungen > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Katalog** und wählen Sie **Katalog** aus der Liste der Einstellungen.
1. Erweitern Sie den Abschnitt *Katalogsuche* .
1. Setzen Sie das **Autocomplete-Limit** auf die Anzahl der Zeilen, die Sie in den [!DNL popover] zulassen möchten.
1. Klicken Sie nach Abschluss des Vorgangs auf **Konfiguration speichern**.

## Beispiel für die Formatierung [!DNL Popover]

Sie können das Erscheinungsbild des Widgets [!DNL Popover] an den Stil und die Branding-Richtlinien Ihres Unternehmens anpassen.

Das [!DNL storefront popover] zeigt immer das Produkt `name` und `price` an, und die Auswahl der Felder kann nicht konfiguriert werden. [!DNL popover] -Elemente können jedoch mit [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) -Klassen formatiert werden. Beispielsweise ändern die folgenden Deklarationen die Hintergrundfarbe des Containers und der Fußzeile [!DNL popover] .

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Behälteranzeige

Die übergeordnete Komponente von `.livesearch.popover-container` ist `.search-autocomplete`.  Die Klasse `.active` gibt die Sichtbarkeit des Containers an. Die Klasse `.active` wird bedingt hinzugefügt, wenn der [!DNL popover] geöffnet ist.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Weitere Informationen zum Formatieren von Storefront-Elementen finden Sie unter [Kaskadierende Stylesheets (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) im [Frontend-Entwicklerhandbuch](https://developer.adobe.com/commerce/frontend-core/guide/).

## Klassenselektoren

Sie können die folgenden Klassenselektoren verwenden, um den Container und die Produktelemente im [!DNL popover] zu gestalten.

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

![Alle Fußzeile anzeigen](assets/livesearch-view-all-footer.png)

### Produktklassenauswahl

#### .livesearch.products-container

![Produkt-Container](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Produktergebnis](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Produktname](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Produktpreis](assets/livesearch-product-price.png)

#### .livesearch product-link

![Produktergebnis](assets/livesearch-product-link.png)

## Arbeiten mit einem geänderten Design {#working-with-modified-theme}

Sie können den [!DNL storefront popover] mit einem angepassten [Design](https://developer.adobe.com/commerce/frontend-core/guide/themes/) verwenden, das die erforderlichen Dateien von *Luma* übernimmt. Der Block `top.search` im `header-wrapper` des `Magento_Search`-Moduls darf nicht geändert werden.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Deaktivieren des [!DNL popover]

Geben Sie den folgenden Befehl ein, um die [!DNL popover] zu deaktivieren und die standardmäßige [Schnellsuche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search)-Funktion wiederherzustellen:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Headless-Implementierungen

Für Implementierungen ohne Headless können Sie die [!DNL Live Search popover] mit einem [npm-Paket](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils) installieren.
