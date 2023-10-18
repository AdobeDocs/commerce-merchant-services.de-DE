---
title: "[!DNL Storefront Popover]"
description: "Die [!DNL Live Search storefront popover] gibt dynamisch vorgeschlagene Produkte und Miniaturansichten zurück."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 5d76d5537c8625296663239195abd26d4ee24db4
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Wann [!DNL Live Search] is [installiert](install.md), a [!DNL popover] erscheint in der Storefront, wenn der Käufer im Feld [Suche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ankreuzen. Mit jedem eingegebenen Zeichen muss die [!DNL popover] wird mit vorgeschlagenen Produkten und Miniaturbildern der wichtigsten Suchergebnisse aktualisiert.

[!DNL Live Search] gibt Ergebnisse für eine Abfrage von zwei Zeichen oder mehr zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ &quot;Suche beim Eingeben&quot; ist nicht konfigurierbar.

Standardmäßig ist [!DNL Live Search] unterstützt [Suchbegriffumleitungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## Durchsuchbare Attribute

Um zielgerichtete Ergebnisse zu erzielen, lesen Sie den Abschnitt [durchsuchbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) Produktattribute. Um die Relevanz sicherzustellen, sollten Attribute nur durchsuchbar sein, wenn sie Inhalte mit einer klaren und präzisen Bedeutung enthalten. Vermeiden Sie die Verwendung von Attributen, die weniger präzisen, langwierigen Text enthalten, z. B. `description`, die zwar standardmäßig für die Suche aktiviert ist, aber die Genauigkeit der Suchergebnisse verringern kann.
Wenn beispielsweise eine Person nach &quot;Shorts&quot;sucht und es Hemden mit einer Beschreibung gibt, die den Begriff &quot;Kurzärmel&quot;enthält, werden die Hemden in die Suchergebnisse aufgenommen.

[!DNL Live Search] berücksichtigt auch [Gewichtung](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) eines Produktattributs, wie in Adobe Commerce festgelegt. Attribute mit einer höheren Gewichtung werden in den Suchergebnissen höher angezeigt.

Die folgenden Attribute sind immer durchsuchbar:

* `sku`
* `name`
* `categories`

## [!DNL Popover] Seitengröße

Die Seitengröße der [!DNL popover] bestimmt, wie viele Zeilen von automatisch ausgefüllten Produkten zurückgegeben werden können. Zuvor war die Seitengröße hartcodiert als sechs Zeilen. Die Variable `page_size` -Wert ist jetzt eine Einstellung, die über die *Admin*. Während der Live Search-Installation wird die Variable `page_size` -Wert ändert sich in den aktuellen Wert der [Katalogsuche](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` -Einstellung.

Standardmäßig ist der Wert Katalogsuche - Automatische Vervollständigungsgrenze auf acht Zeilen (oder Zeilen) festgelegt. So ändern Sie die Seitengröße der [!DNL popover]führen Sie folgende Schritte aus:

1. Im *Admin* Seitenleiste, navigieren Sie zu **Stores** > Einstellungen > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Katalog** und wählen **Katalog** aus der Liste der Einstellungen.
1. Erweitern Sie die *Katalogsuche* Abschnitt.
1. Legen Sie die **Automatische Vervollständigungsgrenze** auf die Anzahl der Zeilen, die Sie in der Variablen [!DNL popover].
1. Wenn Sie fertig sind, klicken Sie auf **Konfiguration speichern**.

## Catalog Service

Die [Catalog Service für Adobe Commerce](../catalog-service/overview.md) -Erweiterung bietet umfassende Ansicht-Modell-Katalogdaten, um produktbezogene Storefront-Erlebnisse schnell und vollständig zu rendern. Catalog Service kann in Verbindung mit Live Search verwendet werden, um Funktionen bereitzustellen, die derzeit von der nativen Erweiterung nicht unterstützt werden:

* Farbmuster
* Erweiterte Attribute
* Andere Produktinformationen können

Merchants können Widgets oder Storefront-Elemente mithilfe des Katalogdienstes anpassen und erweitern. Dies ist jedoch für das Adobe-Supportteam nicht möglich.

## Headless-Implementierungen

Bei Implementierungen ohne Headless ist es möglich, das Live Search-Popup mit einer [npm package](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## Einschränkungen

* Die [!DNL Live Search] [!DNL storefront popover] ist nur für Stores verfügbar, die *Luma* Design oder ein benutzerdefiniertes Design, das auf *Luma*. Breadcrumbs auf der Suchergebnisseite haben keine *Luma* Stile.
* Die [!DNL popover] unterstützt nicht die *Leer* Design. Siehe [Formatierung [!DNL Popover] Elemente](storefront-popover-styling.md) , um mehr zu erfahren.
* Die [!DNL popover] wird im Schnellbestellformular nicht unterstützt.
* Wunschlisten und Produktvergleiche werden nicht unterstützt.
