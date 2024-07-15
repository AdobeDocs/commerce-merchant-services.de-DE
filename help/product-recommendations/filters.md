---
title: Produkte filtern
description: Definieren Sie Bedingungen, die Produkte entweder ein- oder ausschließen, um sie als Empfehlungen zu verwenden.
exl-id: baab28ff-b529-4cbc-adb7-4fa225e87d4a
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Produkte filtern

Adobe Commerce wendet automatisch nicht konfigurierbare Standardfilter auf Empfehlungseinheiten an. Wenn Sie mehrere Empfehlungseinheiten auf einer Seite bereitgestellt haben, filtert Adobe Commerce alle Produkte heraus, die in den Einheiten wiederholt werden. Es wird nur der erste Verweis auf ein wiederholtes Produkt verwendet, um Platz für andere Produkte zu schaffen, die empfohlen werden. Adobe Commerce filtert auch alle zuvor gekauften und im Warenkorb befindlichen Produkte heraus.

Wenn Sie [eine Empfehlungseinheit ](create.md) erstellen, können Sie Filter definieren, die steuern, welche Produkte in Empfehlungen angezeigt werden können. Diese Filter basieren auf einem Satz von Einschluss- oder Ausschlussbedingungen, die Sie definieren. In Empfehlungen werden nur Produkte angezeigt, die alle Aufnahmebedingungen erfüllen. Produkte, die eine der Ausschlussbedingungen erfüllen, werden nicht empfohlen.

Sie können mehrere Filter konfigurieren und nur die gewünschten Filter aktivieren, indem Sie auf jeder Filterseite den Umschalter aktivieren. Auf diese Weise können Sie Entwürfe von Filtern für die zukünftige Verwendung erstellen. Die Anzahl der aktivierten Filter wird auf jeder Registerkarte angezeigt.

## Bedingungen

Bedingungen können statisch oder dynamisch sein.

- Eine statische Bedingung verwendet vorhandene Produktattribute, um zu bestimmen, welche Produkte in der Einheit angezeigt werden können. Sie können beispielsweise festlegen, dass nur Lagerprodukte mit einem Preis von mehr als 25 Euro in der Einheit angezeigt werden. Statische Bedingungen sind für alle Seitentypen verfügbar.

- Eine dynamische Bedingung bestimmt den aktuellen Kontext eines Käufers, z. B. die aktuell angezeigte Kategorie oder das aktuell angezeigte Produkt. Wenn Sie beispielsweise eine Produktempfehlung erstellen, die auf Produktdetailseiten bereitgestellt werden soll, können Sie eine Bedingung erstellen, um nur Produkte zu empfehlen, die innerhalb eines relativen Preisbereichs des aktuell angezeigten Produkts liegen. Dynamische Bedingungen sind für jeden Seitentyp außer der Startseite und für Seiten mit Empfehlungen verfügbar, die in Page Builder platziert werden.

### Logische Operatoren

Die logischen Operatoren `AND` und `OR` werden verwendet, um mehrere Bedingungen miteinander zu verbinden. Bei Verwendung von Einschluss- und Ausschlussfiltern werden die Einschlüsse zuerst ausgewertet, um alle möglichen Produkte zu ermitteln, die empfohlen werden können, und dann werden Produkte, die mit Ausschlussfiltern übereinstimmen, aus der Liste entfernt.

- `AND` - Verbindet zwei Einschlussfilterbedingungen
- `OR` - Verbindet zwei Ausschlussfilterbedingungen

>[!NOTE]
>
> Einschluss- und Ausschlussfilter ersetzen die alten Kategorieausschlüsse in Version 3.2.2 und höher des Moduls `magento/product-recommendations` . Weitere Informationen zu Adobe Commerce-Versionen finden Sie in den [Versionshinweisen](release-notes.md) .

## Filtertypen {#filtertypes}

![Filter](assets/rec-conditions.png)

### Kategorie

Filter, die auf der Kategorie eines Produkts basieren, verwenden direkte Kategoriezuweisungen und deren Unterkategorien. Wenn Sie beispielsweise eine Ausschlussbedingung für die Kategorie `Gear` aktivieren, werden die `Gear` zugewiesenen Produkte sowie alle zugehörigen Unterkategorien wie `Gear/Bags` oder `Gear/Fitness Equipment` ausgeschlossen. Bei B2B-Händlern erfüllt der Kategoriefilter alle [kundenspezifischen Produktkategorien](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), die Sie konfiguriert haben.

Adobe Commerce empfiehlt die Verwendung der folgenden Kategoriefilterkonfiguration, wenn Sie Empfehlungen für Ihre Seitentypen bereitstellen:

| Seite | Filtern nach |
|---|---|
| Startseite | Produkte nicht filtern. |
| Kategorie | Filtern von Produkten in der jeweiligen Kategorie. |
| Produktdetails | Filtern Sie Produkte in denselben Kategorien. |
| Warenkorb | Filtern von Produktkategorien im Warenkorb. |
| Bestellbestätigung | Filtern Sie die Kategorien der gekauften Produkte. |

### Produkt

Produktfilter geben an, welche spezifischen Produkte in Empfehlungen angezeigt werden dürfen oder nicht. Sie können keine Produkte auswählen, die deaktiviert sind oder nicht einzeln sichtbar sind, da diese Produkte nie in Empfehlungen angezeigt werden können.

### Typ

Ein auf dem Produkttyp basierender Filter schließt alle Produkte eines bestimmten Typs ein oder aus. Zu den unterstützten Typen gehören _Einfach_, _Konfigurierbar_, _Virtual_, _herunterladbar_ oder _Geschenkkarte_. Die Produkte _Bundle_ und _Grouped_ werden noch nicht unterstützt.

### Sichtbarkeit

Filtert Produkte basierend auf der Sichtbarkeit, z. B.: _Katalog_, _Suche_ oder beides.

### Preis

Ein auf dem Produktpreis basierender Filter verwendet den Endpreis, um den Vergleich durchzuführen. Der Endpreis beinhaltet alle Rabatte oder Sonderpreise, die anonymen Käufern zur Verfügung stehen. Bei B2B-Händlern spiegelt der angezeigte Preis die von Ihnen konfigurierten [kundenspezifischen Gruppenpreise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) wider.

### Lagerstatus

Die folgenden Ausschlussfilter können verwendet werden, um Produkte nach Lagerstatus herauszufiltern:

- Nicht vorrätig - (nur Ausschluss) Schließt nicht vorrätige Produkte aus.
- Gering auf Lager - (nur Ausschluss) Schließt Produkte aus, die nicht vorrätig sind. Der Status &quot;Geringer Bestand&quot;basiert auf dem Wert _Nur X linker Schwellenwert_ in der [Lagerbestandskonfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/inventory.html) .
