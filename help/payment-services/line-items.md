---
title: Linienelemente für  [!DNL Payment Services]
description: Erfahren Sie mehr über die Zeileneinträge für [!DNL Payment Services] und wie Sie Zeileneinträge im Händler-Dashboard anzeigen.
feature: Payments
role: User
source-git-commit: 5481b19f95908b441e12c4700c51649921dabb08
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Linienelemente für [!DNL Payment Services]

Zeileneinträge für [!DNL Payment Services] sind die Elemente, die in einer Bestellung enthalten sind. Diese Zeileneinträge enthalten Informationen wie:

* Produktdetails
* Menge
* Preis (einschließlich Steuern, Rabatte und sonstige relevante Informationen)

Diese Informationen sind für den Kundendienst, die Auftragsverwaltung und die ordnungsgemäße Rechnungsstellung nützlich.

Diese Funktion ist standardmäßig für [!DNL Payment Services] aktiviert. So zeigen Sie Zeilenelemente an:

1. Navigieren Sie zu Ihrem [PayPal-Händler-Dashboard](https://www.paypal.com/merchant/){target=_blank}.

1. Klicken Sie auf **Aktivität** > **Alle Transaktionen**.

1. Wählen Sie die gewünschte Reihenfolge aus und zeigen Sie die zugehörigen Zeileneinträge an:

   > Beispiel für Zeileneinträge in der Dashboard-Ansicht des Käufers

   ![Ansicht der Zeileneinträge](assets/paypal-shopper-dashboard-line-items-view.png){width="500" zoomable="yes"}

## Linienelementattribute

Zeilenelemente werden generiert, wenn die Bestellung über Adobe Commerce aufgegeben wird, und Informationen werden an PayPal gesendet, mit den folgenden Attributen:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `name` | String! | Der Elementname. Wenn ein Artikel mehr als eine Zeile enthält, weil es mehrere Mengen oder eine Steuerrundung gibt, bleibt der Artikelname für alle Zeilen gleich, aber der angezeigte Preis kann aufgrund der Rundung leicht variieren. |
| `unit_amount` | Objekt! | Der Artikelpreis oder -preis pro Einheit. Umfasst die folgenden Attribute: `currency_code` und `value`. |
| `tax` | Objekt | Die Artikelsteuer für jede Einheit. Umfasst die folgenden Attribute: `currency_code` und `value`. |
| `quantity` | String! | Die Artikelmenge. wird eine ganze Zahl sein. |
| `description` | Zeichenfolge | Die detaillierte Elementbeschreibung. |
| `sku` | Zeichenfolge | Die Lagereinheit (oder SKU) für den Artikel. |
| `url` | Zeichenfolge | Die `URL` für den Artikel, der gekauft wird. Für Käufer sichtbar und in Käufererlebnissen verwendet. |
| `upc` | Objekt | Der Universal Product Code (oder UPC) des Artikels. |
| `category` | Zeichenfolge | Der Elementkategorietyp. |

### `unit_amount` Attribute

Das Objekt `unit_amount` enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `currency_code` | String! | Der [ dreistellige ISO-4217-Währungscode](https://developer.paypal.com/api/rest/reference/currency-codes/), der die Währung angibt. |
| `value` | String! | Gibt den Wert des Elements an. Der `currency_code` bestimmt die erforderliche Anzahl von Dezimalstellen, falls vorhanden. |

### `tax` Attribute

Das Objekt `tax` enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `currency_code` | String! | Der [ dreistellige ISO-4217-Währungscode](https://developer.paypal.com/api/rest/reference/currency-codes/), der die Währung angibt. |
| `value` | String! | Gibt den Wert des Elements an. Hängt von jedem `currency_code` für die erforderliche Anzahl von Dezimalstellen ab. |

### `upc` Attribute

Das Objekt `upc` enthält die folgenden Attribute:

| Attribut | Datentyp | Beschreibung |
| --- | --- | --- |
| `type` | Zeichenfolge! | Der UPC-Typ. |
| `code` | Zeichenfolge! | Der UPC-Produktcode des Artikels. |

Beispiel für +++Zeileneinträge

```json
{
    "name": "Crown Summit Backpack - 1",
    "unit_amount": {
        "currency_code": "USD",
        "value": "38.50"
    },
    "tax": {
        "currency_code": "USD"
        "value": "3.13"
    },
    "quantity": "1",
    "description": "The Crown Summit Backpack is equally at home in a gym locker, study cube or a pup tent, so be sure yours is packed with books,",
    "sku": "24-MB03",
    "url": "https://magento.test/crown-summit-backpack.html",
    "upc": {
        "type": "UPC-A",
        "code": "000003"
    },
    "category": "PHYSICAL_GOODS"
},
{
    "name": "Crown Summit Backpack - 2",
    "unit_amount": {
        "currency_code": "USD",
        "value": "38.50"
    },
    "tax": {
        "currency_code": "USD",
        "value": "3.14"
    },
    "quantity": "1",
    "description": "The Crown Summit Backpack is equally at home in a gym locker, study cube or a pup tent, so be sure yours is packed with books,",
    "sku": "24-MB03",
    "url": "https://magento.test/crown-summit-backpack.html",
    "upc": {
        "type": "UPC-A",
        "code": "000003"
    },
    "category": "PHYSICAL_GOODS"
}
```

+++

Weitere Informationen zu diesen Feldern und deren Einschränkungen finden Sie in der [PayPal-Entwicklerdokumentation zu Zeileneinträgen](https://developer.paypal.com/docs/api/orders/v2/#definition-line_item){target=_blank} .

## Zeilenelemente verwalten

Adobe Commerce [berechnet die Steuer auf Grundlage des Gesamtbetrags für jede Zeile](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/taxes/taxes#warning-messages){target=_blank}, was zu Rundungsfehlern führen kann, wenn mehrere Mengen desselben Artikels bestellt werden oder wenn im Katalog Steuereinschlusspreise angezeigt werden. In diesem Fall kann die Gesamtmenge in zwei Zeilen aufgeteilt werden, aber die Menge entspricht den bestellten Artikeln insgesamt.

> Beispiel für Zeilenelemente mit Rundungsproblemen in der Dashboard-Ansicht des Händlers

![Ansicht der Zeileneinträge](assets/line-items-example.png){width="600" zoomable="yes"}

+++Wie Adobe Commerce ein Rundungsproblem in Zeileneinträgen berechnet

Die Zeileneinträge für [!DNL Payment Services] gleichen dieses Rundungsproblem so, dass der `unit_amount` - oder `unit_tax` -Wert dem Gesamtbetrag für die Bestellung entspricht. Ein Element kann in zwei Zeilen aufgeteilt werden, um dieses Rundungsproblem zu beheben:

* Wenn das Rundungsproblem auf dem `unit_amount` auftritt, sollte der Händler einen Unterschied zum Preis in dieser zusätzlichen Zeile sehen.
* Wenn das Rundungsproblem auf dem `unit_tax` auftritt, wird kein Unterschied bei den einzelnen Zeileneinträgen angezeigt, da der `tax` nicht im Raster, sondern nur als Gesamtsumme am unteren Rand angezeigt wird.

+++
