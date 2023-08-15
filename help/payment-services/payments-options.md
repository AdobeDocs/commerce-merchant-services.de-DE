---
title: Zahlungsoptionen
description: Legen Sie die Zahlungsoptionen fest, um die für Ihre Store-Kunden verfügbaren Methoden anzupassen.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 9a52976be16afa707b494f4da3b99192dd73b8f2
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Zahlungsoptionen

Mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] [!DNL Payment Services], haben Sie mehrere Zahlungsoptionen für Sie. Sie können diese Zahlungsoptionen wie folgt konfigurieren:

* [Home settings](payments-home.md)
* [Store-Konfiguration](configure-admin.md) (empfohlen für ältere Zahlungsoptionen oder ein Multistore-Setup)

Je nachdem, wo Sie sich im Checkout-Prozess befinden, gibt es für jede Zahlungsmethode unterschiedliche Verhaltensweisen:

* Produktseite - Die Produktseite für ein Element
* Mini-Warenkorb: Verfügbar beim Klicken auf das Warenkorbsymbol, wenn ein Produkt zum Warenkorb hinzugefügt wurde
* Warenkorb - Verfügbar bei Klick auf _Warenkorb anzeigen und bearbeiten_ aus dem Mini-Warenkorb
* Checkout-Ansicht - bei Klick auf _Zur Kasse gehen_ aus dem Mini-Warenkorb oder Warenkorb

>[!IMPORTANT]
>
>Zahlungsdienste müssen vor der Abwicklung der Zahlungen abgeschlossen sein.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkartenzahlmethoden. Wenn ein Kunde mit Kreditkartenfeldern zur Kasse geht, gibt er seinen Namen, seine Rechnungsadresse sowie seine Kredit- oder Debitkarteninformationen ein, um seine Bestellung aufzugeben. Ihre Kundeninformationen werden während der Kaufsitzung sicher verwendet, um sie nahtlos durch den Checkout-Fluss zu führen.

Aktivieren [Kreditkartenausfall](#vaulting) für Ihre Geschäfte, damit die Käufer ihre Kreditkarteninformationen für einen schnellen Checkout zu einem späteren Zeitpunkt überprüfen können.

Sie können [!UICONTROL Credit Card Fields] in der Store-Konfiguration oder der Zahlungsdienst-Startseite. Siehe [Einstellungen](settings.md#credit-card-fields) für weitere Informationen.

Sie können auch das Layout, die Breite, die Höhe und den äußeren Stil der Kreditkartenfelder ändern. Siehe [PayPal-Dokumentation](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) für weitere Informationen.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], die PayPal verwenden, um einen Kauf abzuschließen, speichert die Lieferadresse Ihres Käufers, die Rechnungsadresse und Zahlungsdetails zur späteren Verwendung. Käufer können jede Zahlungsmethode verwenden, die zuvor von PayPal gespeichert oder angeboten wurde.

![[!DNL PayPal Smart Buttons] options](assets/payment-buttons.png){width="500"}

Sie können [!UICONTROL PayPal Smart Buttons] in der Store-Konfiguration oder der Zahlungsdienst-Startseite.  Siehe [Einstellungen](settings.md#payment-buttons) für weitere Informationen.

Siehe PayPal&#39;s [Dokumentation zu Zahlungsmethoden](https://developer.paypal.com/docs/checkout/payment-methods/) , um zu erfahren, in welchen Ländern die einzelnen Zahlungsmethoden derzeit verfügbar sind.

### [!DNL PayPal] button

Kunden können mit der Schaltfläche PayPal problemlos und sicher auschecken.

Die [!DNL PayPal] -Schaltfläche ist von der Produktseite aus sichtbar, in der Mini-Warenkorb-, Warenkorb- und Checkout-Ansicht.

### [!DNL Venmo] button

Kunden können mit dem [Venmo](https://venmo.com/) Schaltfläche.

Die [!DNL Venmo] -Schaltfläche ist von der Produktseite aus sichtbar, in der Mini-Warenkorb-, Warenkorb- und Checkout-Ansicht.

### [!DNL Apple Pay] button

Kunden können die Touch-ID auf ihren Geräten verwenden, um [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), die auf ihrem iOS- oder macOS-Gerät gespeicherte Zahlungsberechtigungen für Kredit- und Debitkarten verwendet.

Die [!DNL Apple Pay] -Schaltfläche ist von der Produktseite aus sichtbar, in der Mini-Warenkorb-, Warenkorb- und Checkout-Ansicht.

>[!NOTE]
>
> Verwendung [!DNL Apple Pay] für Ihre Filialen [Selbstregistrierung mit [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Live-Domäne registrieren_ nur -Abschnitt) und [Konfigurieren Sie es für Ihre Stores in [!DNL Payment Services]](settings.md#payment-buttons).

### Schaltfläche &quot;PayPal Debit&quot;oder &quot;Kreditkarte&quot;

Kunden können mit der Schaltfläche PayPal Debit oder Kreditkarte auschecken.

Die Schaltfläche PayPal Debit oder Kreditkarte ist auf der Checkout-Seite sichtbar.

Diese Option kann verwendet werden, um Ihren Kunden eine Lastschrift oder Kreditkartenzahlungsoption mit einer PayPal-gehosteten Schaltfläche als Alternative zu einer Kreditkartenintegration vorzuzeigen.

### [!DNL Pay Later] button

Bieten Sie Ihren Kunden kurzfristige, zinsfreie Zahlungen und andere Finanzierungsoptionen an, damit sie jetzt kaufen und später mit dem [!DNL Pay Later] Schaltfläche.

Die [!DNL Pay Later] -Schaltfläche ist von der Produktseite aus sichtbar, in der Mini-Warenkorb-, Warenkorb- und Checkout-Ansicht.

Weitere Informationen zu den Pay-Later-Angeboten finden Sie unter [PayPal&#39;s Pay Later bietet Dokumentation](https://developer.paypal.com/docs/checkout/pay-later/us/). Verwenden Sie die **Land oder Region** Dropdown-Liste, um eine Zielregion auszuwählen.

Siehe [Einstellungen](settings.md#payment-buttons) , um zu erfahren, wie Sie die [!DNL Pay Later] Messaging.

### [!DNL Pay Now] button

Die [!DNL Pay Now] -Schaltfläche im PayPal-Popup-Fenster angezeigt, wenn ein Kunde auf eine Zahlungsschaltfläche auf dem Zahlungsbildschirm klickt.

Wenn der endgültige Bestellbetrag noch nicht bekannt ist (z. B. wenn Sie noch keine Versandadressen-Informationen haben) und der Kunde gerade von der Produktseite, dem Mini-Warenkorb oder dem Warenkorb auscheckt, wird ein _Weiter_ -Schaltfläche verfügbar ist. Klickt ein Kunde _Weiter_, nachdem sie ihre Zahlungsmethode bestätigt haben, werden sie auf eine Bestellüberprüfungsseite geleitet, um die erforderlichen Details zu erfassen, bevor sie den Kassengang abschließen.

## Verwenden Sie nur PayPal-Zahlungsschaltflächen

Um Ihren Store schnell in den Produktionsmodus zu bringen, können Sie Folgendes konfigurieren: _only_ PayPal-Zahlungsschaltflächen (Venmo, PayPal usw.)—anstatt auch die Zahlungsoption PayPal Kreditkarte zu verwenden.

Dies ermöglicht Ihnen Folgendes:

* Stellen Sie eine Vielzahl von Zahlungsoptionen für Ihre Kunden bereit, einschließlich Venmo- und PayPal-Zahlungsschaltflächen, mit der Möglichkeit, gehostete PayPal-Kartenfelder zu deaktivieren und einen vorhandenen Kreditkartenanbieter zu verwenden.
* Nutzen Sie Ihren bestehenden Kreditkartenanbieter für Kreditkartenzahlungen und nutzen Sie gleichzeitig die anderen Zahlungsoptionen von PayPal.
* Verwenden Sie die Zahlungsschaltflächen von PayPal in einer Region, in der PayPal keine Kreditkarten als Zahlungsoption unterstützt.

nach **Erfassen von Zahlungen mit _only_ PayPal-Zahlungsschaltflächen (_not_ die Zahlungsoption PayPal für Kreditkarten)**:

1. Stellen Sie sicher, dass Ihr Store [im Produktionsmodus](settings.md#enable-payment-services).
1. [Konfigurieren der gewünschten PayPal-Zahlungsschaltflächen](settings.md#payment-buttons) in den Einstellungen.
1. drehen _Aus_ die **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** in der _[!UICONTROL Payment buttons]_Abschnitt.

nach **Zahlungen mit Ihrem bestehenden Kreditkartenanbieter erfassen _und_ PayPal-Zahlungsschaltflächen**:

1. Stellen Sie sicher, dass Ihr Store [im Produktionsmodus](settings.md#enable-payment-services).
1. [Konfigurieren der gewünschten PayPal-Zahlungsschaltflächen](settings.md#payment-buttons).
1. drehen _Aus_ die **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** in der _[!UICONTROL Payment buttons]_Abschnitt.
1. drehen _Aus_ die **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** in der _[!UICONTROL Credit card fields]_und verwenden Sie Ihre [bestehendes Kreditkartenkonto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Auftragsumberechnung

Wenn ein Kunde von der Mini-Warenkorb-, Warenkorb- oder Produktseite aus in den Kassengang wechselt, wird er auf eine Seite zur Überprüfung der Bestellung weitergeleitet, auf der er die ausgewählte Lieferadresse in einem PayPal-Popup-Fenster sehen kann. Nachdem der Kunde die Versandmethode ausgewählt hat, wird der Auftragsbetrag entsprechend neu berechnet und der Kunde kann Versandkosten und Steuern sehen.

Wenn ein Kunde von der Checkout-Seite aus in den Checkout-Fluss eintritt, ist dem System die Lieferadresse und der endgültige berechnete Betrag bereits bekannt und die Summen werden entsprechend dargestellt.

Steuerferien, Versandkosten und Umsatzsteuern können von Ort zu Ort sehr variieren. Nachher [!DNL Payment Services] die Lieferadresse und den Preis erhalten, berechnet sie schnell alle anwendbaren Kosten neu und zeigt sie in den letzten Phasen des Auscheckens entsprechend an.

## Kreditkartenausnahme

Käufer können ihre Kreditkarteninformationen für zukünftige Käufe auf der Website (alle Geschäfte innerhalb desselben Händlers-Kontos) verwerten oder &quot;speichern&quot;.

Siehe [Kreditkartenausnahme](vaulting.md) für weitere Informationen.

## Sicherheit

Siehe [PCI-Compliance](security.md#pci-compliance) für weitere Informationen.
