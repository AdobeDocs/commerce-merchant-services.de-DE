---
title: Storefront Popover
description: Das Popup-Storefront-Popup für die Live-Suche gibt dynamisch vorgeschlagene Produkte und Miniaturansichten zurück.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Storefront Popover

Wann [!DNL Live Search] is [installiert](install.md), wird ein Popup in der Storefront angezeigt, wenn der Käufer im Feld [Suche](https://docs.magento.com/user-guide/catalog/search-quick.html) ankreuzen. Wenn jedes Zeichen eingegeben wird, wird das Popover mit den vorgeschlagenen Produkten und Miniaturbildern der Top-Suchergebnisse aktualisiert.

[!DNL Live Search] gibt Ergebnisse für eine Abfrage von zwei Zeichen oder mehr zurück. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ &quot;Suche beim Eingeben&quot; ist nicht konfigurierbar.

>[!NOTE]
>
>Die [!DNL Live Search] Storefront-Popover ist nur für Stores verfügbar, die *Luma* Design oder ein benutzerdefiniertes Design, das auf *Luma*. Die *Luma* -Design ist im [!DNL Commerce] Beispieldaten. Das Popover unterstützt nicht die *Leer* Design. Siehe [Formatieren von Popover-Elementen](storefront-popover-styling.md) , um mehr zu erfahren.

## Durchsuchbare Attribute

Um zielgerichtete Ergebnisse zu erzielen, lesen Sie den Abschnitt [durchsuchbar](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) Produktattribute. Um die Relevanz sicherzustellen, sollten Attribute nur durchsuchbar sein, wenn sie Inhalte mit einer klaren und präzisen Bedeutung enthalten. Vermeiden Sie die Verwendung von Attributen, die weniger präzisen, langwierigen Text enthalten, z. B. `description`, die zwar standardmäßig für die Suche aktiviert ist, aber die Genauigkeit der Suchergebnisse verringern kann. Wenn beispielsweise eine Person nach &quot;Shorts&quot;sucht und es Hemden mit einer Beschreibung gibt, die den Begriff &quot;Kurzärmel&quot;enthält, werden die Hemden in die Suchergebnisse aufgenommen.

Die folgenden Attribute sind immer durchsuchbar:

* `sku`
* `name`
* `categories`

![Popup für Live-Suche](assets/storefront-search-as-you-type.png)

## Popover-Seitengröße

Die Seitengröße des Popover bestimmt, wie viele Zeilen von automatisch ausgefüllten Produkten zurückgegeben werden können. Zuvor war die Seitengröße hartcodiert als sechs Zeilen. Die Variable `page_size` -Wert ist jetzt eine Einstellung, die über die *Admin*. Während der Live Search-Installation wird die Variable `page_size` -Wert ändert sich in den aktuellen Wert der [Katalogsuche](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` -Einstellung.

Standardmäßig ist der Wert Katalogsuche - Automatische Vervollständigungsgrenze auf acht Zeilen (oder Zeilen) festgelegt. Gehen Sie wie folgt vor, um die Seitengröße des Popover zu ändern:

1. Im *Admin* Seitenleiste, navigieren Sie zu **Stores** > Einstellungen > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Katalog** und wählen Sie **Katalog** aus der Liste der Einstellungen.
1. Erweitern Sie die *Katalogsuche* Abschnitt.
1. Legen Sie die **Automatische Vervollständigungsgrenze** auf die Anzahl der Zeilen, die Sie im Popover zulassen möchten.
1. Wenn Sie fertig sind, klicken Sie auf **Konfiguration speichern**.
