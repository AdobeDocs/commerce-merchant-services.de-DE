---
title: Zahlungsoptionen
description: Legen Sie die Zahlungsoptionen fest, um die für Ihre Store-Kunden verfügbaren Methoden anzupassen.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Zahlungsoptionen

Mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] [!DNL Payment Services], haben Sie mehrere Zahlungsoptionen für Sie. Sie können diese Zahlungsoptionen wie folgt konfigurieren:

* [Startseite](payments-home.md)
* [Store-Konfiguration](configure-admin.md) (empfohlen für ältere Zahlungsoptionen oder ein Multistore-Setup)

Je nachdem, wo Sie sich im Checkout-Prozess befinden, gibt es für jede Zahlungsmethode unterschiedliche Verhaltensweisen:

* Produktseite - Die Produktseite für ein Element
* Mini-Warenkorb: Verfügbar beim Klicken auf das Warenkorbsymbol, wenn ein Produkt zum Warenkorb hinzugefügt wurde
* Warenkorb - Verfügbar bei Klick auf _Warenkorb anzeigen und bearbeiten_ aus dem Mini-Warenkorb
* Checkout-Ansicht - bei Klick auf _Zum Auschecken fortfahren_ aus dem Mini-Warenkorb oder Warenkorb

>[!IMPORTANT]
>
>Zahlungsdienste müssen vor der Abwicklung der Zahlungen abgeschlossen sein.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkartenzahlmethoden. Wenn ein Kunde mit Kreditkartenfeldern zur Kasse geht, gibt er seinen Namen, seine Rechnungsadresse sowie seine Kredit- oder Debitkarteninformationen ein, um seine Bestellung aufzugeben. Ihre Kundeninformationen werden während der Kaufsitzung sicher verwendet, um sie nahtlos durch den Checkout-Fluss zu führen.

Sie können [!UICONTROL Credit Card Fields] in der Store-Konfiguration oder der Zahlungsdienst-Startseite. Siehe [Konfiguration [!DNL Payment Services]](settings.md#configure-credit-card-fields) für weitere Informationen.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], die PayPal verwenden, um einen Kauf abzuschließen, speichert die Lieferadresse Ihres Käufers, die Rechnungsadresse und Zahlungsdetails zur späteren Verwendung. Käufer können jede Zahlungsmethode verwenden, die zuvor von PayPal gespeichert oder angeboten wurde.

Sie können [!DNL PayPal Smart Buttons] in der Store-Konfiguration oder der Zahlungsdienst-Startseite.  Siehe [Konfiguration [!DNL Payment Services]](settings.md#configure-paypal-smart-buttons) für weitere Informationen.

### Schaltfläche &quot;PayPal&quot;

Kunden können mit der Schaltfläche PayPal problemlos und sicher auschecken.

Die Schaltfläche PayPal ist von der Produktseite aus sichtbar, in den Miniaturansichten, im Warenkorb und in den Checkout-Ansichten.

### Schaltfläche &quot;Venmo&quot;

Kunden können mit dem [Venmo](https://venmo.com/) Schaltfläche.

Die Venmo-Schaltfläche ist von der Produktseite aus sichtbar, von Mini-Warenkorb, Warenkorb und Checkout-Ansichten.

### [!DNL Pay Later] button

Bieten Sie Ihren Kunden kurzfristige, zinsfreie Zahlungen und andere Finanzierungsoptionen an, damit sie jetzt kaufen und später mit dem [!DNL Pay Later] Schaltfläche.

Die [!DNL Pay Later] -Schaltfläche ist von der Produktseite aus sichtbar, in der Mini-Warenkorb-, Warenkorb- und Checkout-Ansicht.

Es gibt zwei Zahlungsoptionen mit der [!DNL Pay Later] Schaltfläche:

* **Bezahlung in 4**—Kunden können ihren Bestellsaldo in vier zinsfreien Zahlungen (alle zwei Wochen) nach einer anfänglichen Anzahlung zahlen. Siehe [In 4 Dokumentation bezahlen](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) für weitere Informationen.
* **PayPal-Guthaben**- Kunden können ihren Bestellsaldo innerhalb von sechs Monaten vollständig, zinsfrei bezahlen. Siehe [PayPal-Kreditdokumentation](https://www.paypal.com/us/webapps/mpp/paypal-credit) für weitere Informationen.

### [!DNL Pay Now] button

Die [!DNL Pay Now] -Schaltfläche im PayPal-Popup-Fenster angezeigt, wenn ein Kunde auf eine Zahlungsschaltfläche auf dem Zahlungsbildschirm klickt.

Wenn der endgültige Bestellbetrag noch nicht bekannt ist (z. B. wenn Sie noch keine Versandadressen-Informationen haben) und der Kunde gerade von der Produktseite, dem Mini-Warenkorb oder dem Warenkorb auscheckt, wird ein _Weiter_ -Schaltfläche verfügbar. Klickt ein Kunde _Weiter_, nachdem sie ihre Zahlungsmethode bestätigt haben, werden sie auf eine Bestellüberprüfungsseite geleitet, um die erforderlichen Details zu erfassen, bevor sie den Kassengang abschließen.

## [!DNL Pay Later] Messaging

Um Ihren Kunden dabei zu unterstützen, diese als potenzielle Zahlungsoptionen zu identifizieren, [!DNL Pay Later] Nachrichten sind auf der Produktseite, im Mini-Warenkorb und im Warenkorb sowie beim Checkout sichtbar.

* **Wenn ein Kunde ein Produkt zwischen 30 und 600 $ auswählt**, Nachrichten unter dem PayPal und [!DNL Pay Later] -Schaltflächen geben dem Kunden weitere Informationen über die Zahlungsoption In 4. Kunden können auf **Weitere Infos** Informationen zur Option &quot;In 4 bezahlen&quot; _oder_ Klicken Sie auf den Text &quot;Oder sehen Sie 6 Monate Sonderfinanzierung&quot; im Popup, um mehr über die PayPal-Kreditoption zu erfahren und sie zu bewerben.
* **Wenn ein Kunde ein Produkt oder Produkte auswählt, die über 98,99 USD hinausgehen**, Nachrichten unter dem PayPal und [!DNL Pay Later] -Schaltflächen bieten Kunden weitere Informationen zur Zahlungsoption PayPal Credit. Kunden können auf **Weitere Infos** , um mehr über die PayPal-Kreditoption zu erfahren und sie zu bewerben _oder_ Klicken Sie im Popup auf den Text &quot;Oder siehe In 4 bezahlen&quot;, um mehr über die Option Bezahlen in 4 zu erfahren.

   >[!NOTE]
   >
   >Die oben aufgeführten Beträge können sich ändern.

Siehe [Konfigurieren [!DNL Payment Services]](configure-admin.md#configure-paypal-smart-buttons) , um zu erfahren, wie Sie die [!DNL Pay Later] Messaging.

## Auftragsumberechnung

Wenn ein Kunde von der Mini-Warenkorb-, Warenkorb- oder Produktseite aus in den Kassengang wechselt, wird er auf eine Seite zur Überprüfung der Bestellung weitergeleitet, auf der er die ausgewählte Lieferadresse in einem PayPal-Popup-Fenster sehen kann. Nachdem der Kunde die Versandmethode ausgewählt hat, wird der Auftragsbetrag entsprechend neu berechnet und der Kunde kann Versandkosten und Steuern sehen.

Wenn ein Kunde von der Checkout-Seite aus in den Checkout-Fluss eintritt, kennt das System bereits die Lieferadresse und den endgültigen berechneten Betrag und die Summen werden angemessen dargestellt.

Steuerferien, Versandkosten und Umsatzsteuern können von Ort zu Ort sehr variieren. Nachher [!DNL Payment Services] die Lieferadresse und den Preis erhalten, berechnet sie schnell alle anwendbaren Kosten neu und zeigt sie in den letzten Phasen des Auscheckens entsprechend an.

## Kasse von der Produktseite

Wenn ein Kunde direkt von der Produktseite aus mit PayPal auscheckt oder [!DNL Pay Later] -Schaltflächen, wird nur der Artikel gekauft, der auf der aktuellen Produktseite dargestellt wird. Artikel, die sich bereits im Warenkorb des Kunden befinden, werden nicht zum Kassengang hinzugefügt und werden nicht gekauft.

Wenn der Kunde die Bestellung storniert, wird der Artikel auf der aktuellen Produktseite zum Warenkorb des Kunden hinzugefügt, zusammen mit allen anderen Artikeln im Warenkorb. Mit dieser Funktion kann der Kunde den Artikel, den er gerade anzeigt, schnell kaufen und gleichzeitig alle anderen Artikel beibehalten, die er zuvor beim Durchsuchen von Produkten zum Warenkorb hinzugefügt hat.

Wenn ein Kunde von der Produktseite aus in den Checkout-Fluss wechselt, wird die Checkout-Seite vereinfacht. In der Ansicht werden nur die bestellbaren Daten und Optionen angezeigt.

## Sicherheit

Siehe [PCI-Compliance](security.md#pci-compliance) für weitere Informationen.
