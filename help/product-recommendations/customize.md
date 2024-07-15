---
title: Anpassen
description: Erfahren Sie, wie Sie Ihre Produktempfehlungen anpassen können.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Anpassen

Wenn Sie das Produkt-Recommendations-Modul installieren, erstellt Adobe Commerce den Ordner &quot;`ProductRecommendationsLayout`&quot;. Dieser Ordner enthält Vorlagendateien, die Sie anpassen können, um die Darstellung der Empfehlungen in Ihrer Storefront zu ändern. Insbesondere können Sie die folgende Vorlage ändern oder überschreiben:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Weitere Informationen zum Ändern von Vorlagendateien finden Sie unter [Vorlagenanpassung](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) im Frontend-Entwicklerhandbuch.

Wenn Sie die `recommendations.html` -Datei ändern, müssen Sie die folgenden Tags in der Datei beibehalten, um sicherzustellen, dass Adobe Commerce Empfehlungsmetriken aus Ihrem Storefront erfassen kann:

| Tag | Verwendung |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Erfasst Ansichtsereignisse. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Erfasst Klickereignisse. <br/>**Hinweis:** Wenn Sie Anker-Tags hinzufügen, müssen Sie diese Attribute einschließen. |

Zusätzlich zur Datei &quot;`recommendations.html`&quot; enthält das Verzeichnis &quot;`ProductRecommendationsLayout`&quot; die folgenden Unterverzeichnisse:

| Verzeichnis | Zweck |
|---|---|
| `layout` | Enthält `*.xml` -Dateien für jeden Seitentyp |
| `templates` | Enthält Dateien, die die Skripte zum Abrufen und Rendern aufrufen |
| `web/js` | Enthält die JavaScript-Dateien, die Empfehlungen für Ihren Store abrufen und rendern |
| `web/template` | Enthält die Vorlage für das Modul `magento/product-recommendations` |

## Positionierung von Empfehlungseinheiten

Wenn Sie [eine Empfehlung erstellen](create.md), geben Sie die [Position](placement.md) an, an der sie auf der Seite angezeigt wird. Eine Empfehlungseinheit kann entweder oben oder unten im Hauptinhaltsbehälter platziert werden. Sie können diese Platzierung jedoch anpassen. Wenn Sie einen Inhaltstyp für Seitenaufbau-Empfehlungen erstellen, verwenden Sie die Seitenaufbau-Tools, um die Empfehlungseinheit auf der Seite zu positionieren. Bearbeiten Sie für alle anderen Seitentypen die `*.xml` -Dateien, die beim Erstellen der Empfehlung generiert werden.

1. Wechseln Sie zum Ordner &quot;`layout`&quot;:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   In der folgenden Tabelle sind die in diesem Verzeichnis vorhandenen XML-Dateien aufgeführt:

   | Dateiname | Seite |
   |---|---|
   | `catalog_category_view.xml` | Kategorie |
   | `catalog_product_view.xml` | Produktdetails |
   | `checkout_cart_index.xml` | Warenkorb |
   | `checkout_onepage_success.xml` | Checkout |
   | `cms_index_index.xml` | Startseite |

   >[!NOTE]
   >
   >Die Dateinamen im Ordner &quot;`layout`&quot;können sich unterscheiden, wenn Ihr Store Drittanbietererweiterungen verwendet.

1. Ändern Sie die Datei &quot;`catalog_product_view.xml`&quot;, sodass die Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt wird. Bevor Sie diese XML-Datei anpassen, sollten Sie sich die Datei ansehen und die Abschnitte verstehen, die Sie ändern müssen:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Im obigen Ausschnitt zeigt der Referenzblock `main.content` an, dass die Empfehlungseinheit an einer relativ zu diesem Element angelegten Stelle platziert wird. Das Element `block` enthält das Attribut `after="-"` , das angibt, dass die Empfehlungseinheit auf der Seite nach dem Hauptinhaltsblock angezeigt wird.

1. Ändern wir diese Datei, indem wir einen anderen Inhaltsbaustein angeben.

   Ändern Sie den Referenzblock `name` von `main.content` in `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Diese Änderung führt dazu, dass Ihre Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt wird. Wenn die Empfehlungseinheit vor dem `product.info.media` angezeigt werden soll, ändern Sie das Attribut `after="-"` in `before="-"`. Das `pagePlacement` -Argument ist ein internes Argument, das nicht geändert werden sollte.

Weitere Informationen zu den Bausteintypen auf der Seite finden Sie in der [Layout-Übersicht](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) .

## Benutzerdefinierte Produktattribute

Entwickler benötigen oft Zugriff auf benutzerdefinierte Produktattributwerte in Empfehlungseinheiten auf Storefronts, damit sie visuelle Behandlungen zu Produkten hinzufügen können, die auf diesen Attributen basieren.

Wenn Ihr Store beispielsweise Bio-Produkte verkauft, haben Sie möglicherweise ein benutzerdefiniertes Attribut für die Produkte, die sie als `Organic = Yes` kennzeichnen. Möglicherweise benötigen Sie Zugriff auf diesen Attributwert in der Storefront, damit Sie diese Produkte besonders visuell behandeln können, wenn sie in Recommendations angezeigt werden. Auf ähnliche Weise können Sie durch den Zugriff auf diese benutzerdefinierten Produktattributwerte Produkte kennzeichnen oder benutzerdefinierte Logik in der Präsentationsebene Ihrer Site fördern.

![Badge hinzufügen](assets/unit-custom.png)

Um sicherzustellen, dass beim Rendern der Empfehlungseinheit auf der Seite ein benutzerdefiniertes Produktattribut verfügbar ist, setzen Sie die Eigenschaft `Used in Product Listing` auf `Yes` auf der Seite [Produktattribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) im Admin.

Wenn diese Eigenschaft festgelegt ist, enthält die JSON-Payload ein `attributes` -Objekt, das ein Array von Attributcodes und -werten enthält. Anschließend können Sie auf der Grundlage dieser Attributwerte benutzerdefinierte Storefront-Stile anwenden, z. B. das Hinzufügen von speziellen visuellen Behandlungen oder Badges wie oben erwähnt.

>[!NOTE]
>
>Änderungen von Produktattributen können bis zu einer Stunde dauern, bis sie in der JSON-Payload angezeigt werden.
