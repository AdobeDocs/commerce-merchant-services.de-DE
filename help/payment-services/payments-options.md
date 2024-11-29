---
title: Zahlungsoptionen
description: Legen Sie die Zahlungsoptionen fest, um die für Ihre Store-Kunden verfügbaren Methoden anzupassen.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 17c8d16a2593f7bb6015f5b2968fc4c67be8ed5b
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Zahlungsoptionen

Bei [!DNL Adobe Commerce] und [!DNL Magento Open Source] [!DNL Payment Services] stehen Ihnen mehrere Zahlungsoptionen zur Verfügung.

Sie können diese Zahlungsoptionen in den [Home settings](payments-home.md) oder in der [Store-Konfiguration](configure-admin.md) konfigurieren (empfohlen für ältere Zahlungsoptionen oder ein Multi-Store-Setup).

Je nachdem, wo Sie sich im Checkout-Prozess befinden, gibt es für jede Zahlungsmethode unterschiedliche Verhaltensweisen:

* Produktseite - Die Produktseite für ein Element
* Mini-Warenkorb: Verfügbar beim Klicken auf das Warenkorbsymbol, wenn ein Produkt zum Warenkorb hinzugefügt wurde
* Warenkorb: Verfügbar bei Klick auf _Warenkorb anzeigen und bearbeiten_ aus dem Mini-Warenkorb
* Checkout-Ansicht - Verfügbar beim Klicken auf _Fahren Sie mit dem Checkout_ aus dem Mini-Warenkorb oder Warenkorb fort.

>[!IMPORTANT]
>
>[!DNL Payment Services] Das Onboarding muss abgeschlossen sein, bevor Zahlungen verarbeitet werden können.

## Erlebnis für Standardzahlungen im Vergleich zu erweiterten Zahlungen

[!DNL Payment Services] bietet je nach Land, in dem Sie tätig sind, **Erweiterte Optionen** (vollständig unterstützt) und **Standard** (Express-Checkout) sowie Onboarding-Zahlungsoptionen.

* **Erweitert** - Alle verfügbaren [Zahlungsoptionen](../payment-services/payments-options.md) sind für die aktuellen [vollständig unterstützten Länder](../payment-services/overview.md#availability) verfügbar. Wählen Sie beim Onboarding die Option [Erweitertes Onboarding](../payment-services/production.md#advanced-onboarding), um Live-Zahlungen zu aktivieren.
* **Standard** - Eine Untergruppe von Zahlungsoptionen (Express Checkout) - PayPal-Kredit- und Debitkarten - ist für andere verfügbare unterstützte Länder verfügbar. [Kreditkartenfelder](#credit-card-fields) und [Apple Pay](#apple-pay-button) sind für diese Onboarding-Option nicht verfügbar. Wählen Sie beim Onboarding die Option [Standardeinstieg](../payment-services/production.md#standard-onboarding) aus, um Live-Zahlungen zu aktivieren.

Informationen zum Abschluss des erweiterten und standardmäßigen Onboarding finden Sie unter [Aktivieren [!DNL Payment Services] für die Produktion](../payment-services/production.md#complete-merchant-onboarding) .

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] bietet einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkartenzahlmethoden. Wenn ein Kunde mit Kreditkartenfeldern zur Kasse geht, gibt er seinen Namen, seine Rechnungsadresse sowie seine Kredit- oder Debitkarteninformationen ein, um seine Bestellung aufzugeben. Ihre Kundeninformationen werden während der Kaufsitzung sicher verwendet, um sie nahtlos durch den Checkout-Fluss zu führen.

![Kreditkartenfelder im Checkout](assets/credit-card-fields.png){width="500" zoomable="yes"}

Aktivieren Sie [Kreditkartengewinn](#vaulting) für Ihre Geschäfte, damit Käufer ihre Kreditkarteninformationen für einen schnellen Checkout später überprüfen (speichern) können.

Sie können [!UICONTROL Credit Card Fields] in der Store-Konfiguration oder der [!DNL Payment Services]-Startseite konfigurieren. Weitere Informationen finden Sie unter [Einstellungen](settings.md#credit-card-fields) .

Sie können auch das Layout, die Breite, die Höhe und den äußeren Stil der Kreditkartenfelder ändern. Weitere Informationen finden Sie in der [PayPal-Dokumentation](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) .

## Schaltfläche [!DNL Apple Pay]

Kunden können [[!DNL Apple Pay]](https://www.apple.com/apple-pay/) verwenden, das die auf einem iOS- oder macOS-Gerät gespeicherten Zahlungsberechtigungen für Kredit- und Debitkarten verwendet, um Käufe zu tätigen.

[!DNL Apple Pay] ist nur im Safari-Browser verfügbar. Händler können bis zu 99 Domänen pro Händlerkonto hinzufügen.

![Apple-Schaltfläche &quot;Bezahlen&quot;im Minicart](assets/applepay-button.png){width="500" zoomable="yes"}

Die Schaltfläche &quot;[!DNL Apple Pay]&quot; ist von der Produktseite aus sichtbar, in den Miniaturausschnitten, im Warenkorb und in den Checkout-Ansichten.

Um [!DNL Apple Pay] für Ihre Stores zu verwenden, führen Sie die [ Selbstregistrierung mit  [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) durch (_Nur die Live-Domäne registrieren_ ) und konfigurieren Sie sie für Ihre Stores in  [!DNL Payment Services]](settings.md#payment-buttons).[

>[!NOTE]
>
> Weitere Informationen dazu, wie Sie Käufern die Zahlung mit Apple PayPal auf Ihrer Site ermöglichen, finden Sie unter [Erweiterter Checkout](https://www.paypal.com/us/cshelp/article/what-is-paypal-advanced-checkout-and-how-do-i-get-started-help953){target=_blank} in der PayPal-Entwicklerdokumentation.

Sie können [!UICONTROL Apple Pay] in der Store-Konfiguration oder auf der Zahlungsdienst-Startseite konfigurieren. Weitere Informationen finden Sie unter [Einstellungen](settings.md#apple-pay) .

## Schaltfläche [!DNL Google Pay]

Kunden können [[!DNL Google Pay]](https://pay.google.com/about/) verwenden, indem sie Zahlungsdetails zu ihrem Google-Konto hinzufügen, wo sie sicher für ein nahtloses Checkout-Erlebnis gespeichert sind.

[!DNL Google Pay] ist nur in bestimmten Ländern oder Regionen und auf bestimmten Geräten verfügbar. Weitere Informationen finden Sie in der [[!DNL Google Pay] Dokumentation](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration) .

![Google-Schaltfläche &quot;Bezahlen&quot;im Checkout](assets/google-pay-button.png){width="500" zoomable="yes"}

Die Schaltfläche &quot;[!DNL Google Pay]&quot; ist von der Produktseite aus sichtbar, in den Miniaturausschnitten, im Warenkorb und in den Checkout-Ansichten.

Sie können [!UICONTROL Google Pay] in der Store-Konfiguration oder auf der Zahlungsdienst-Startseite konfigurieren. Weitere Informationen finden Sie unter [Einstellungen](configure-admin.md) .

>[!NOTE]
>
> Die [!DNL Google Pay] -API kann nur auf Websites in einem sicheren Kontext verwendet werden. Weitere Informationen finden Sie in der Dokumentation zur Fehlerbehebung ](https://developers.google.com/pay/api/web/support/troubleshooting) .[

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], das PayPal zum Abschluss eines Kaufs verwendet, speichert die Lieferadresse, Rechnungsadressen und Zahlungsdetails Ihres Käufers zur späteren Verwendung. Käufer können jede Zahlungsmethode verwenden, die zuvor von PayPal gespeichert oder angeboten wurde.

![Schaltfläche &quot;PayPal&quot;](assets/paypal-button.png){width="350" zoomable="yes"}

Sie können [!UICONTROL PayPal payment buttons] in der Store-Konfiguration oder der [!DNL Payment Services]-Startseite konfigurieren. Weitere Informationen finden Sie unter [Einstellungen](settings.md#payment-buttons) .

Erfahren Sie mehr über die Verfügbarkeit der Zahlungsmethoden nach Ländern in der Dokumentation zu PayPal [Zahlungsmethoden](https://developer.paypal.com/docs/checkout/payment-methods/).

### Schaltfläche [!DNL PayPal]

Kunden können mit der Schaltfläche PayPal problemlos und sicher auschecken.

Die Schaltfläche &quot;[!DNL PayPal]&quot; ist von der Produktseite aus sichtbar, in den Miniaturausschnitten, im Warenkorb und in den Checkout-Ansichten.

### Schaltfläche [!DNL Venmo]

Kunden können mit der Schaltfläche [Venmo](https://venmo.com/) auschecken.

Die Schaltfläche &quot;[!DNL Venmo]&quot; ist von der Produktseite aus sichtbar, in den Miniaturausschnitten, im Warenkorb und in den Checkout-Ansichten.

### Schaltfläche &quot;PayPal Debit&quot;oder &quot;Kreditkarte&quot;

Kunden können mit der Schaltfläche PayPal Debit oder Kreditkarte auschecken.

Die Schaltfläche PayPal Debit oder Kreditkarte ist auf der Checkout-Seite sichtbar.

Diese Option kann verwendet werden, um Ihren Kunden eine Lastschrift oder Kreditkartenzahlungsoption mit einer PayPal-gehosteten Schaltfläche als Alternative zu einer Kreditkartenintegration vorzuzeigen.

### Schaltfläche [!DNL Pay Later]

Bieten Sie Ihren Kunden kurzfristige, zinsfreie Zahlungen und andere Finanzierungsoptionen an, damit sie jetzt kaufen und später mit der Schaltfläche [!DNL Pay Later] bezahlen können.

Die Schaltfläche &quot;[!DNL Pay Later]&quot; ist von der Produktseite aus sichtbar, in den Miniaturausschnitten, im Warenkorb und in den Checkout-Ansichten.

Weitere Informationen zu den Angeboten von Pay-Later finden Sie in der Dokumentation zu PayPal&#39;s PayPal&#39;s Pay-Later-Angeboten](https://developer.paypal.com/docs/checkout/pay-later/us/). [ Verwenden Sie das Dropdown-Menü **Land oder Region** , um eine Region auszuwählen.

Erfahren Sie, wie Sie die [!DNL Pay Later]-Nachricht deaktivieren oder aktivieren, indem Sie die Konfiguration [Einstellungen](settings.md#payment-buttons) aktualisieren.

## Verwenden Sie nur PayPal-Zahlungsschaltflächen

Um Ihren Store schnell in den Produktionsmodus zu versetzen, können Sie die Zahlungsschaltflächen _nur_ PayPal (Venmo, PayPal usw.) konfigurieren.—anstatt auch die Zahlungsoption PayPal Kreditkarte zu verwenden.

Dies ermöglicht Ihnen Folgendes:

* Stellen Sie verschiedene Zahlungsoptionen für Ihre Kunden bereit, einschließlich der Zahlungsschaltflächen Venmo und PayPal, mit der Option, gehostete PayPal-Kartenfelder zu deaktivieren und einen vorhandenen Kreditkartenanbieter zu verwenden.
* Verwenden Sie Ihren bestehenden Kreditkartenanbieter für Kreditkartenzahlungen und gleichzeitig die anderen Zahlungsoptionen von PayPal.
* Verwenden Sie die Zahlungsschaltflächen von PayPal in Regionen, in denen PayPal keine Kreditkarten als Zahlungsoption unterstützt.

So erfassen Sie Zahlungen mit _nur_ PayPal-Zahlungsschaltflächen (_nicht_ die Zahlungsoption PayPal-Kreditkarte)**:**

1. Stellen Sie sicher, dass Ihr Store im Produktionsmodus ](settings.md#enable-payment-services) [ist.
1. [Konfigurieren Sie die gewünschten PayPal-Zahlungsschaltflächen](settings.md#payment-buttons) in den Einstellungen.
1. Deaktivieren Sie _Aus_ die Option **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** im Abschnitt _[!UICONTROL Payment buttons]_.

So erfassen Sie **Zahlungen mit Ihrem vorhandenen Kreditkartenanbieter _und_ PayPal-Zahlungsschaltflächen**:

1. Stellen Sie sicher, dass Ihr Store im Produktionsmodus ](settings.md#enable-payment-services) [ist.
1. [Konfigurieren Sie die gewünschten PayPal-Zahlungsschaltflächen](settings.md#payment-buttons).
1. Deaktivieren Sie _Aus_ die Option **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** im Abschnitt _[!UICONTROL Payment buttons]_.
1. Deaktivieren Sie _Aus_ die Option **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** im Abschnitt _[!UICONTROL Credit card fields]_und verwenden Sie Ihr [bestehendes Kreditkartenanbieterkonto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Auftragsumberechnung

Wenn ein Kunde von der Mini-Warenkorb-, Warenkorb- oder Produktseite aus in den Kassengang wechselt, wird er auf eine Seite zur Überprüfung der Bestellung weitergeleitet, auf der er die ausgewählte Lieferadresse in einem PayPal-Popup-Fenster sehen kann. Nachdem der Kunde die Versandmethode ausgewählt hat, wird der Auftragsbetrag entsprechend neu berechnet und der Kunde kann Versandkosten und Steuern sehen.

Wenn ein Kunde von der Checkout-Seite aus in den Checkout-Fluss eintritt, ist dem System die Lieferadresse und der endgültige berechnete Betrag bereits bekannt und die Summen werden entsprechend dargestellt.

Steuerferien, Versandkosten und Umsatzsteuern können von Ort zu Ort sehr variieren. Nachdem [!DNL Payment Services] die Lieferadresse und den Versandpreis erhalten hat, berechnet es schnell alle anwendbaren Kosten neu und zeigt sie in den letzten Phasen des Checkout korrekt an.

## Kreditkartenausnahme

Käufer können ihre Kreditkarteninformationen für zukünftige Käufe auf der Website (alle Geschäfte innerhalb desselben Händlers-Kontos) verwerten oder &quot;speichern&quot;.

Weitere Informationen finden Sie unter [Kreditkartenausnahme](vaulting.md) .

## Sicherheit

Weitere Informationen finden Sie unter [PCI compliance](security.md#pci-compliance) .
