---
title: Ältere Konfiguration der Zahlungsdienste
description: Nach der Installation können Sie [!DNL Payment Services] in der Store-Konfiguration in der Admin -Konfiguration.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---

# Ältere Konfiguration der Zahlungsdienste

Sie können [!DNL Payment Services] Sie können Ihre Anforderungen mit hilfreichen Konfigurationsoptionen in der Admin-Konsole erfüllen.

Bei der Konfiguration [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] im Admin gelten diese Konfigurationen nur für die Umgebung, die im _[!UICONTROL Method]_-Feld_[!UICONTROL General Configuration]_. Alle Änderungen, die Sie in den Konfigurationsfeldern vornehmen, sind unabhängig vom Wechsel der _[!UICONTROL Method]_selection - wenn Sie die Methode wechseln, werden Ihre Auswahlen nicht zurückgesetzt.

## Allgemeine Konfiguration

Sie können [!DNL Payment Services] für Ihren Store und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen im _[!UICONTROL General Configuration]_Abschnitt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.

   ![Ansicht &quot;Methoden&quot;](assets/methods-view.png)

1. Erweitern Sie die _[!UICONTROL Recommended Solutions]_Abschnitt.
1. Im _[!UICONTROL [!DNL Payment Services]]_-Abschnitt, erweitern Sie die_[!UICONTROL General Configuration]_ Abschnitt.
1. Für **Aktivieren**, setzen Sie sie auf `Yes` aktivieren [!DNL Payment Services] für Ihren Laden.
1. Für **Methode**, setzen Sie sie auf `Sandbox` wenn Sie noch testen [!DNL Payment Services] für Ihr Geschäft oder `Production` wenn Sie bereit sind, Live-Zahlungen zu aktivieren.

   >[!WARNING]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abgeschlossen haben. Entfernen oder ändern Sie diese IDs nicht.

1. Klicken **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Payment Services] für Ihre Website. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |
| [!UICONTROL Production Merchant ID] | Store-Ansicht | Ihre Produktions-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |

## [!UICONTROL Credit Card Fields]

Die [!UICONTROL Credit Card Fields] Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

### Kreditkartenfelder konfigurieren

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL Recommended Solutions]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL Credit Card Fields]_ Abschnitt.
1. Für **[!UICONTROL Title]**, geben Sie bei Bedarf Text ein, um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method)auswählen **[!UICONTROL Authorize]** oder **Autorisieren und Erfassen**.
1. Für **[!UICONTROL Show on checkout page]** auswählen `Yes` um Kreditkartenfelder auf der Checkout-Seite zu aktivieren oder zu deaktivieren.
1. Für **[!UICONTROL Vault Enabled]** auswählen `Yes` , um die Kreditkartenausgabe für den Checkout zu aktivieren.
1. Für **Debug-Modus** auswählen `Yes` , um den Debug-Modus zu aktivieren (oder `No` , um sie zu deaktivieren).
1. Klicken **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

### Konfigurieren [!DNL PayPal Smart Buttons]

Sie können die Zahlungsoptionen für PayPal Smart-Schaltflächen innerhalb des Administrators aktivieren und konfigurieren:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL Recommended Solutions]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL PayPal Smart Buttons]_ Abschnitt.
1. Um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird, bearbeiten Sie die _[!UICONTROL Title]_-Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method)auswählen **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. So deaktivieren Sie die [Spätere Nachrichten bezahlen](payments-options.md#pay-later-button) (falls gewünscht), wählen Sie `No` für **[!UICONTROL Display Pay Later Message]**.
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für **[!UICONTROL Debug Mode]** (`No` deaktiviert es).
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Apple-Zahlungsoption, bei der Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie das Erscheinungsbild der Zahlungsoption Spätere Zahlung , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Produktdetailseite. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] in der Vorschau des Mini-Warenkorbs. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Warenkorbseite. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] Stiloptionen

| Feld | Anwendungsbereich | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Store-Ansicht | Definieren Sie den Stil des Layouts für Paypal Smart Buttons. Optionen: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | Store-Ansicht | Definieren Sie die Farbe der Smart-Schaltflächen &quot;Paypal&quot;. Optionen: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Store-Ansicht | Definieren Sie die Form der Paypal-Smart-Schaltflächen. Optionen: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | Store-Ansicht | Definiert, ob PayPal Smart-Schaltflächen eine Standardhöhe verwenden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Store-Ansicht | Definieren Sie die Höhe der PayPal-Smart-Schaltflächen. Standardwert: Keine |
| [!UICONTROL Label] | Store-Ansicht | Definieren Sie eine Beschriftung, die in den PayPal-Smart-Schaltflächen angezeigt wird. Optionen: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | Store-Ansicht | Aktiviert Tagline. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |

## Cache leeren

Wenn Sie die Konfiguration ändern, [Cache manuell leeren](/help/payment-services/settings.md#flush-the-cache) sodass Ihr Store die neuesten Konfigurationseinstellungen anzeigt.
