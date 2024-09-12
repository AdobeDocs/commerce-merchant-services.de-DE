---
title: Checkout in [!DNL Payment Services]
description: Passen Sie den Checkout an die Anforderungen Ihres Kunden an. [!DNL Payment Services]
feature: Payments, Checkout
exl-id: 47df165f-2145-4e0e-b272-54b8e768cf19
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Checkout in [!DNL Payment Services]

Sie können den Checkout für Adobe Commerce [!DNL Payment Services] so konfigurieren, dass er Ihren Kunden am besten passt. Funktionen wie [automatische Aufhebung der Bestellung](#order-auto-voided-if-error) und [Kreditkartenauswertung](#credit-card-vaulting) stellen sicher, dass Ihre Kunden ein reibungsloses Benutzererlebnis bieten.

## Reihenfolge bei Fehler automatisch aufgehoben

Tritt beim Auschecken ein Fehler auf, wird die Bestellung von [!DNL Payment Services] automatisch aufgehoben bzw. abgebrochen.

Auf der Checkout-Seite für den Käufer wird eine Fehlermeldung angezeigt. Die Nachricht kann variieren.

![Fehler beim Überprüfen von ](assets/user-checkout-error.png "Fehler beim Auschecken"){width="600" zoomable="yes"}

Ein Kommentar zur stornierten Bestellung wird auch im Admin für eine bestimmte [Bestellung](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en) angezeigt.

![Abgebrochener Bestellkommentar in Admin für Bestellung](assets/admin-checkout-error.png "Abgebrochener Bestellkommentar in Admin für Bestellung"){width="600" zoomable="yes"}

Wenn ein Käufer die Autorisierung für eine Bestellung erhält, die Bestellung jedoch nicht erstellt und in `Capture` konvertiert wurde, wird die Bestellung automatisch aufgehoben. Auf diese Weise wird sichergestellt, dass keine Kreditkarte auf der Kreditkarte des Kunden reserviert wird und die Gebühr des Zahlungsdienstleisters vermieden wird, die eintritt, wenn die Genehmigung am Ende des standardmäßigen Zeitraums von 29 Tagen widerrufen wird.

>[!NOTE]
>
>Die automatische Aufhebung der Bestellung tritt nur dann auf, wenn der Kunde eine Zahlungsmethode verwendet, die auf den Modus `Authorize` und nicht auf den Modus `Authorize and Capture` eingestellt ist.

## Kasse von der Produktseite

Wenn ein Kunde direkt über die Produktseite mit den Schaltflächen PayPal oder [!DNL Pay Later] zur Kasse geht, wird nur der Artikel gekauft, der auf der aktuellen Produktseite dargestellt wird. Artikel, die sich bereits im Warenkorb des Kunden befinden, werden nicht zum Kassengang hinzugefügt und werden nicht gekauft.

Mit dieser Funktion kann der Kunde den Artikel, den er gerade anzeigt, schnell kaufen und dabei Artikel beibehalten, die ihm zuvor in den Warenkorb gelegt wurden.
Wenn der Kunde die Bestellung storniert, wird der Artikel auf der aktuellen Produktseite zum Warenkorb des Kunden hinzugefügt.

Wenn ein Kunde von der Produktseite aus in den Checkout-Fluss wechselt, wird die Checkout-Seite vereinfacht. In der Ansicht werden nur die bestellbaren Daten und Optionen angezeigt.

## Kreditkartenausnahme

Käufer können ihre Kreditkarteninformationen für zukünftige Käufe auf der Website (alle Geschäfte innerhalb desselben Händlers-Kontos) verwerten oder &quot;speichern&quot;.

Weitere Informationen finden Sie unter [Kreditkartenausnahme](vaulting.md) .
