---
title: Erweitern und Anpassen von SAAS-Datenexport-Feed-Daten
description: Erfahren Sie, wie Sie die [!DNL SaaS Data Export] Feed-Daten erweitern und anpassen.
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Erweitern und Anpassen von SAAS-Datenexport-Feed-Daten

Die Erweiterung [!DNL Commerce Data Export] bietet eine Möglichkeit, Daten aus der [!DNL Commerce] -Anwendung in Commerce-Dienste wie Live Search, Catalog Service und Product Recommendations zu exportieren. Bei Bedarf können Sie die Feed-Daten erweitern und anpassen, um zusätzliche Daten einzuschließen, oder die erfassten Daten ändern, indem Sie das Modul `Magento\CatalogDataExporter` aktualisieren.

>[!NOTE]
>
>Das Hinzufügen neuer Daten zum Feed oder die Änderung vorhandener Daten können sich auf die Feed-Erfassungsleistung auswirken und Probleme bei der Verarbeitungslogik auf der Adobe Commerce-Seite verursachen. Testen Sie den angepassten Code vor dem Zusammenführen mit einer Produktionsumgebung.

## Erweitern von Attributdaten im Produkt-Feed

Der Produkt-Feed enthält Standardattribute, die für die Produktverarbeitung erforderlich sind oder häufig von Verbrauchern verwendet werden. Sie können dem Produkt-Feed zusätzliche Systemattribute hinzufügen, indem Sie sie zum Feed hinzufügen.

Um diese Aufgabe abzuschließen, aktualisieren Sie das Modul `magento/catalog-data-exporter` , um die zusätzlichen Systemattribute zur Konfigurationsdatei für die Abhängigkeitsinjektion ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) hinzuzufügen. [ Fügen Sie die Attribute zur Produktattribut-Abfrage (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`) hinzu.

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
