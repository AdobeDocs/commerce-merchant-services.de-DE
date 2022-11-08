---
title: Anpassen
description: Erfahren Sie, wie Sie Ihre Produktempfehlungen anpassen können.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: a34c3c8a5caca1bbf611b2df650c562aeeab297b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Anpassen

Wenn Sie das Produkt-Recommendations-Modul installieren, erstellt Adobe Commerce die `ProductRecommendationsLayout` Verzeichnis. Dieser Ordner enthält Vorlagendateien, die Sie anpassen können, um die Darstellung der Empfehlungen in Ihrer Storefront zu ändern. Insbesondere können Sie die folgende Vorlage ändern oder überschreiben:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Weitere Informationen zum Ändern von Vorlagendateien finden Sie unter [Vorlagenanpassung](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) im Frontend-Entwicklerhandbuch.

Wenn Sie die `recommendations.html` müssen Sie die folgenden Tags in der Datei beibehalten, um sicherzustellen, dass Adobe Commerce Empfehlungsmetriken aus Ihrem Storefront erfassen kann:

| Tag | Verwendung |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Erfasst Ansichtsereignisse. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Erfasst Klickereignisse. <br/>**Hinweis:** Wenn Sie Anker-Tags hinzufügen, müssen Sie diese Attribute einbeziehen. |

Zusätzlich zu den `recommendations.html` -Datei, die `ProductRecommendationsLayout` enthält die folgenden Unterverzeichnisse:

| Verzeichnis | Zweck |
|---|---|
| `layout` | Enthält `*.xml` Dateien für jeden Seitentyp |
| `templates` | Enthält Dateien, die die Skripte zum Abrufen und Rendern aufrufen |
| `web/js` | Enthält die JavaScript-Dateien, die Empfehlungen für Ihren Store abrufen und rendern |
| `web/template` | Enthält die Vorlage für die `magento/product-recommendations` Modul |

## Positionierung von Empfehlungseinheiten

Wenn Sie [erstellen](create.md) eine Empfehlung, legen Sie die [location](placement.md) wo sie auf der Seite angezeigt wird. Eine Empfehlungseinheit kann entweder oben oder unten im Hauptinhaltsbehälter platziert werden. Sie können diese Platzierung jedoch anpassen. Wenn Sie einen Inhaltstyp für Seitenaufbau-Empfehlungen erstellen, verwenden Sie die Seitenaufbau-Tools, um die Empfehlungseinheit auf der Seite zu positionieren. Für alle anderen Seitentypen bearbeiten Sie die `*.xml` -Dateien, die beim Erstellen der Empfehlung generiert werden.

1. Änderung an `layout` directory:

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
   >Die Dateinamen im `layout` kann sich unterscheiden, wenn Ihr Store Drittanbietererweiterungen verwendet.

1. Ändern wir die `catalog_product_view.xml` -Datei, damit die Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt wird. Bevor Sie diese XML-Datei anpassen, schauen wir uns die Datei an und lernen die Abschnitte kennen, die Sie ändern müssen:

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

   Im obigen Snippet wird die `main.content` Der Referenzblock gibt an, dass die Empfehlungseinheit an einer Stelle relativ zu diesem Element platziert wird. Seine `block` -Element enthält `after="-"` -Attribut, das angibt, dass die Empfehlungseinheit auf der Seite nach dem Hauptinhaltsbaustein angezeigt wird.

1. Ändern wir diese Datei, indem wir einen anderen Inhaltsbaustein angeben.

   Sie ändern den Referenzblock `name` von `main.content` nach `product.info.media`.

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

   Diese Änderung führt dazu, dass Ihre Empfehlungseinheit nach dem Produktbild auf der Produktdetailseite angezeigt wird. Wenn Sie möchten, dass die Empfehlungseinheit vor der `product.info.media`, ändern Sie die `after="-"` Attribut `before="-"`. Die `pagePlacement` -Argument ist ein internes Argument, das nicht geändert werden sollte.

Siehe [Layout-Übersicht](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) für weitere Informationen zu den Bausteintypen auf der Seite.

## Benutzerdefinierte Produktattribute

Entwickler benötigen oft Zugriff auf benutzerdefinierte Produktattributwerte in Empfehlungseinheiten auf Storefronts, damit sie visuelle Behandlungen zu Produkten hinzufügen können, die auf diesen Attributen basieren.

Wenn Ihr Geschäft beispielsweise Bio-Produkte verkauft, können Sie ein benutzerdefiniertes Attribut für die Produkte haben, die sie als `Organic = Yes`. Möglicherweise benötigen Sie Zugriff auf diesen Attributwert in der Storefront, damit Sie diese Produkte besonders visuell behandeln können, wenn sie in Recommendations angezeigt werden. Auf ähnliche Weise können Sie durch den Zugriff auf diese benutzerdefinierten Produktattributwerte Produkte kennzeichnen oder benutzerdefinierte Logik in der Präsentationsebene Ihrer Site fördern.

![Badge hinzufügen](assets/unit-custom.png)

Um sicherzustellen, dass beim Rendern der Empfehlungseinheit auf der Seite ein benutzerdefiniertes Produktattribut verfügbar ist, legen Sie die `Used in Product Listing` Eigenschaft auf `Yes` im [Produktattribute](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) in der Admin-Seite.

Wenn diese Eigenschaft festgelegt ist, enthält die JSON-Payload eine `attributes` -Objekt, das ein Array von Attributcodes und -werten enthält. Anschließend können Sie auf der Grundlage dieser Attributwerte benutzerdefinierte Storefront-Stile anwenden, z. B. das Hinzufügen von speziellen visuellen Behandlungen oder Badges wie oben erwähnt.

>[!NOTE]
>
>Änderungen von Produktattributen können bis zu einer Stunde dauern, bis sie in der JSON-Payload angezeigt werden.
