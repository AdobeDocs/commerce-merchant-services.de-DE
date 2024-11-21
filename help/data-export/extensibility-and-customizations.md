---
title: Erweitern und Anpassen von SAAS-Datenexport-Feed-Daten
description: Erfahren Sie, wie Sie die [!DNL SaaS Data Export] Feed-Daten erweitern und anpassen.
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: 06ef294d2670e5d36bbb6cd18deafce2cc751772
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Erweitern und Anpassen von SAAS-Datenexport-Feed-Daten

Die Erweiterung [!DNL Commerce Data Export] bietet eine Möglichkeit, Daten aus der [!DNL Commerce] -Anwendung in Commerce-Dienste wie Live Search, Catalog Service und Product Recommendations zu exportieren. Bei Bedarf können Sie die Feed-Daten erweitern und anpassen, um zusätzliche Attributdaten hinzuzufügen oder die erfassten Daten zu ändern.

Nachdem Sie Attributdaten hinzugefügt haben, können Sie über das Feld [attribute](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type) im GraphQL-Schema für den Storefront-Dienst darauf zugreifen.

>[!NOTE]
>
>Das Hinzufügen oder Ändern von Feed-Daten kann sich auf die Leistung und Verarbeitungslogik im Commerce-Backend auswirken. Testen Sie benutzerdefinierten Code vor dem Zusammenführen zur Produktion. Verwenden Sie anstelle von Daten zum Backend API-Mesh, um das GraphQL-Schema des Catalog Service zu erweitern. Weitere Informationen zur Konfiguration finden Sie unter [Catalog Service and API Mesh](../catalog-service/mesh.md).

## Erweitern von Systemattributdaten im Produkt-Feed

Der Produkt-Feed enthält standardmäßige Systemattribute, die für die Produktverarbeitung erforderlich sind oder häufig von Verbrauchern verwendet werden. Sie können dem Produkt-Feed zusätzliche Systemattribute hinzufügen, indem Sie sie zum Feed hinzufügen.

Um diese Aufgabe abzuschließen, aktualisieren Sie das Modul `magento/catalog-data-exporter` , um die zusätzlichen Systemattribute zur Konfigurationsdatei für die Abhängigkeitsinjektion ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) hinzuzufügen.[

Fügen Sie die Attribute zur Produktattribut-Abfrage (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`) hinzu.

**Beispiel**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```

## Hinzufügen von Produktattributen zu Adobe Commerce

Entwickler können Produktattribute hinzufügen, auf die über das Feld [Produktattribute](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#output-fields) zugegriffen werden kann, indem sie eine der folgenden Methoden verwenden:

- Fügen Sie das -Attribut zu Adobe Commerce hinzu, um es in die `products` -Feed-Daten einzubeziehen, die an Commerce StoreFront-Services exportiert wurden.
- Fügen Sie das Attribut während des Feed-Synchronisierungsprozesses mithilfe eines Plug-ins dynamisch hinzu.

### Hinzufügen des Attributs zu Adobe Commerce

Sie können ein Produktattribut vom Commerce Admin hinzufügen oder programmgesteuert ein benutzerdefiniertes PHP-Modul verwenden, um das Attribut zu definieren und Adobe Commerce zu aktualisieren. Dies ist die einfachste Methode zum Hinzufügen eines Produktattributs, da Sie das -Attribut und alle erforderlichen Metadaten hinzufügen können. Das neue Attribut und seine Metadateneigenschaften werden während der nächsten geplanten Synchronisierung automatisch in die SaaS-Dienste exportiert.

#### Erstellen des Produktattributs vom Administrator

1. Erstellen Sie im Commerce Admin das -Attribut auf der Konfigurationsseite des Produktattributs ([!UICONTROL Stores] > *[!UICONTROL Attributes]* > [!UICONTROL Product]).

1. Fügen Sie das Attribut nach Bedarf einem Attributsatz hinzu.

Siehe [Erstellen von Produktattributen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create) im *Adobe Commerce Admin-Handbuch*.

#### Das Produktattribut programmgesteuert erstellen

Fügen Sie ein Produktattribut programmgesteuert hinzu, indem Sie einen Datenpatch erstellen, der die `DataPatchInterface` implementiert, und instanziieren Sie eine Kopie der `EavSetup Factory` -Klasse im Konstruktor, um die Attributoptionen zu konfigurieren.

Wenn Sie die Attributoptionen definieren, sind alle Attributparameter außer `type`, `label` und `input` optional. Definieren Sie die folgenden zusätzlichen Optionen und alle anderen Optionen, die von den Standardeinstellungen abweichen.

- Stellen Sie sicher, dass die Eigenschaft während der Datensynchronisation in Storefront-Dienste exportiert wird, indem Sie `user_defined` = `1` festlegen.
- Um sicherzustellen, dass das Attribut in der Datenbankabfrage zur Produktliste verfügbar ist, legen Sie `used_in_product_listing` = `1` fest.

Weitere Informationen zum Erstellen von Daten-Patches finden Sie unter [Daten- und Schema-Patches entwickeln](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) im *PHP Developer Guide*.

### Produktattribut dynamisch hinzufügen

Weitere Informationen zum dynamischen Erstellen von Produktattributen ohne Einführung neuer ev-Attribute finden Sie unter [Attribut dynamisch hinzufügen](add-attribute-dynamically.md).
