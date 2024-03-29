---
title: Ältere Konfiguration der Zahlungsdienste
description: Nach der Installation können Sie [!DNL Payment Services] in der Store-Konfiguration in der Admin -Konfiguration.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---

# Veraltet [!DNL Payment Services] Konfiguration

Sie können [!DNL Payment Services] Sie können Ihre Anforderungen mit hilfreichen Konfigurationsoptionen in der Admin-Konsole erfüllen.

Bei der Konfiguration [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] im Admin gelten diese Konfigurationen nur für die Umgebung, die in der _[!UICONTROL Method]_-Feld_[!UICONTROL General Configuration]_. Alle Änderungen, die Sie in den Konfigurationsfeldern vornehmen, sind unabhängig vom Wechsel der _[!UICONTROL Method]_selection - wenn Sie die Methode wechseln, werden Ihre Auswahlen nicht zurückgesetzt.

## Allgemeine Konfiguration

Sie können [!DNL Payment Services] für Ihr Geschäft und Ihre  _[!UICONTROL Merchant Location]_und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen in der_[!UICONTROL General Configuration]_ Abschnitt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.

   ![Ansicht &quot;Methoden&quot;](assets/methods-view.png){width="400" zoomable="yes"}

1. Legen Sie die _[!UICONTROL Merchant Country]_im Feld_[!UICONTROL Merchant Location]_.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_-Abschnitt, um auf die_[!UICONTROL [!DNL Payment Services]]_ Abschnitt.
1. Im _[!UICONTROL [!DNL Payment Services]]_-Abschnitt, erweitern Sie die_[!UICONTROL General Configuration]_ Abschnitt.
1. Für **Aktivieren**, setzen Sie sie auf `Yes` aktivieren [!DNL Payment Services] für Ihren Laden.
1. Für **Methode**, setzen Sie sie auf `Sandbox` wenn Sie noch testen [!DNL Payment Services] für Ihr Geschäft oder `Production` wenn Sie bereit sind, Live-Zahlungen zu aktivieren.

   >[!WARNING]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abgeschlossen haben. Entfernen oder ändern Sie diese IDs nicht.

1. Für **Soft Deskriptor** (benutzerdefinierte Werte, die in Bankübersichten für Kundenkunden angezeigt werden, um zwischen Geschäften/Marken/Katalogen zu unterscheiden), fügen Sie Ihren benutzerdefinierten Text (bis zu 22 Zeichen) in das Textfeld ein und ersetzen Sie `Custom descriptor` oder den vorhandenen Wert.
1. Klicks **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

![Ansicht der vorgestellten Adobe-Lösung](assets/featured-adobe-solution-view.png){width="700" zoomable="yes"}

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Payment Services] für Ihre Website. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |
| [!UICONTROL Production Merchant ID] | Store-Ansicht | Ihre Produktions-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites einen weichen Deskriptor hinzu und speichern Sie diese, um Informationen zu Kundentransaktionen hinzuzufügen, die Marken, Stores oder Produktlinien voneinander trennen. |

## [!UICONTROL Credit Card Fields]

Die [!UICONTROL Credit Card Fields] Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL Credit Card Fields]_ Abschnitt.
1. Für **[!UICONTROL Title]**, geben Sie bei Bedarf Text ein, um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method)auswählen **[!UICONTROL Authorize]** oder **Autorisieren und Erfassen**.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie eine `Numeric Only` Wert in **[!UICONTROL Sort order]** -Feld.
1. Für **[!UICONTROL Show on checkout page]** auswählen `Yes` , um Kreditkartenfelder auf der Checkout-Seite zu aktivieren.
1. Für **[!UICONTROL Vault Enabled]** auswählen `Yes` , um die Kreditkartenausgabe für den Checkout zu aktivieren.
1. Für **[!UICONTROL Vault Enabled in Admin]** auswählen `Yes` , damit der Händler Bestellungen für Kunden mit seiner Kreditkarte erstellen kann.
1. Aktivieren **[!UICONTROL 3DS Secure authentication]** (`Off` Standardmäßig) `Always` oder `When required`.
1. Für **[!UICONTROL Debug Mode]** auswählen `Yes` , um den Debugmodus zu aktivieren, oder `No` , um sie zu deaktivieren.
1. Klicks **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie Kreditkartenfelder auf der Checkout-Seite. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | Store-Ansicht | Aktivieren oder Deaktivieren [Kreditkartenausfall](vaulting.md). Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | Store-Ansicht | Aktivieren oder Deaktivieren der Funktion für [Händler, um Kundenaufträge im Admin abzuschließen](vaulting.md) mit einer gültigen Zahlungsmethode. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | website | Aktivieren oder Deaktivieren [Sichere 3DS-Authentifizierung](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

Die [!UICONTROL Apple Pay] Mit der Zahlungsoption kann der Händler seinen Kunden Apple Pay anbieten, die über die Touch-ID auf ihren Geräten Käufe über den Safari-Browser tätigen können. Händler können bis zu 99 Domänen pro Händlerkonto hinzufügen.

Siehe [Zahlungsoptionen](payments-options.md#apple-pay-button) für weitere Informationen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL Apple Pay]_ Abschnitt.
1. Für **[!UICONTROL Title]**, geben Sie bei Bedarf Text ein, um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method)auswählen **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Geben Sie an, wo die [!DNL Apple Pay] in Adobe Commerce aktiviert ist, indem Sie `Yes` in den folgenden Optionen nach Bedarf:
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** (`No` deaktiviert es).
1. Klicken Sie zum Speichern der Änderungen auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder Deaktivieren [!DNL Apple Pay] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Checkout-Seite. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Apple Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Apple Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Apple Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

Die [!UICONTROL Google Pay] Die Zahlungsoption ermöglicht es dem Händler, seinen Kunden Google Pay anzubieten, die die Google-Geldbörse auf ihren Geräten verwenden können, um Käufe zu tätigen.

Siehe [Zahlungsoptionen](payments-options.md#google-pay-button) für weitere Informationen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL Google Pay]_ Abschnitt.
1. (Optional) Ändern Sie den Namen der Zahlungsmethode, die beim Checkout angezeigt wird, indem Sie den neuen Namen in die **[!UICONTROL Title]** -Feld.
1. [Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method) durch Auswahl **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Geben Sie an, wo die [!DNL Google Pay] in Adobe Commerce aktiviert ist, indem Sie `Yes` in den folgenden Optionen nach Bedarf:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** (`No` deaktiviert es).
1. Konfigurieren des Erscheinungsbilds der _[!UICONTROL Google Pay]_durch Auswahl der **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**, und **[!UICONTROL Button Style]**nach Bedarf.
1. Zum Festlegen der Höhe verwendet den Standardwert für die Höhe, der in **[!UICONTROL Button Style]**.
1. Klicken Sie zum Speichern der Änderungen auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Gibt die Textbeschriftung an, die während des Checkouts in der Ansicht &quot;Zahlungsmethode&quot;für diese Zahlungsoption angezeigt wird. Optionen: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder Deaktivieren [!DNL Google Pay] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Checkout-Seite. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Google Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Google Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL Google Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Store-Ansicht | Definieren Sie die Farbe der [!DNL Google Pay] Schaltfläche. Optionen: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Store-Ansicht | Definieren Sie den Typ der [!DNL Google Pay] Schaltfläche. Optionen: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Siehe [Google Pay API-Anforderungsobjektoptionen](https://developers.google.com/pay/api/web/reference/request-objects) Dokumentation finden Sie weitere Informationen.

## [!DNL PayPal Payment Buttons]

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Konfigurieren [!DNL PayPal payment buttons]

Sie können die Zahlungsoptionen der PayPal-Zahlungsschaltflächen innerhalb des Administrators aktivieren und konfigurieren:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_Abschnitt.
1. Im _[!UICONTROL Payment Services]_-Abschnitt, erweitern Sie die_[!UICONTROL PayPal payment buttons]_ Abschnitt.
1. Um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern, bearbeiten Sie die _[!UICONTROL Title]_-Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method)auswählen **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]**.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie eine `Numeric Only` Wert in **[!UICONTROL Sort order]** -Feld.
1. So aktivieren/deaktivieren Sie die [Spätere Nachrichten bezahlen](payments-options.md#pay-later-button)auswählen `Yes`/`No` für **[!UICONTROL Display Pay Later Message]**.
1. Geben Sie an, wo die PayPal-Zahlungsschaltflächen in Adobe Commerce aktiviert sind, indem Sie `Yes` in den folgenden Optionen nach Bedarf:
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Um Venmo als Zahlungsoption zu aktivieren, wählen Sie `Yes` für **[!UICONTROL Venmo Enabled]**.
1. Um Kredit- und Debitkarten als Zahlungsoption zu aktivieren (Schaltfläche &quot;PayPal Smart&quot;), wählen Sie `Yes` für **[!UICONTROL Credit and Debit Card Enabled]**.
1. So aktivieren/deaktivieren Sie die [PayPal Pay Später](payments-options.md#pay-later-button) Zahlungsoption, wählen Sie `Yes`/`No` für **[!UICONTROL PayPal Pay Later Enabled]**.
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für die **[!UICONTROL Debug Mode]** (`No` deaktiviert es).
1. Klicken Sie zum Speichern der Änderungen auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal payment buttons] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal payment buttons] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Optionen der Kredit- und Debitkarte, in denen Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die PayPal PayPal Pay Later Payment-Option, wenn Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der Zahlungsschaltflächen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Sales]** und wählen **[!UICONTROL Payment Methods]**.
1. Erweitern Sie die _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_Abschnitt.
1. Im _[!UICONTROL [!DNL Payment Services]]_-Abschnitt, erweitern Sie die_[!UICONTROL PayPal Smart Button Styling]_ Abschnitt.
1. Um das Layout festzulegen, wählen Sie `Vertical` oder `Horizontal` für **[!UICONTROL Layout]**
1. Um die Farbe festzulegen, wählen Sie aus den verfügbaren Farben unter **[!UICONTROL Color]**.
1. Um die Form festzulegen, wählen Sie `Rectangular` oder `Pill` für **[!UICONTROL Shape]**.
1. Um die Standardhöhe zu verwenden, wählen Sie `Yes` oder `No` für **[!UICONTROL Use Default Height]**.
1. Um die benutzerdefinierte Höhe festzulegen, fügen Sie die gewünschte Pixelhöhe für **[!UICONTROL Height]**.
1. Um die Tagline festzulegen, wählen Sie `Yes` oder `No` für **[!UICONTROL Tagline]**.
1. Klicken Sie zum Speichern der Änderungen auf **[!UICONTROL Save Config]** .
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie anschließend auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können auch die Formatierung von Zahlungsschaltflächen konfigurieren [in Einstellungen](settings.md#button-style) von der Zahlungsdienst-Startseite aus.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Store-Ansicht | Definieren Sie den Stil des Layouts für die PayPal-Zahlungsschaltflächen. Optionen: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Store-Ansicht | Definieren Sie die Farbe der PayPal-Zahlungsschaltflächen. Optionen: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Store-Ansicht | Definieren Sie die Form der PayPal-Zahlungsschaltflächen. Optionen: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Store-Ansicht | Definiert, ob PayPal-Zahlungsschaltflächen eine Standardhöhe verwenden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Store-Ansicht | Definieren Sie die Höhe der PayPal-Zahlungsschaltflächen. Standardwert: keiner |
| [!UICONTROL Label] | Store-Ansicht | Definieren Sie den Titel, der auf den PayPal-Zahlungsschaltflächen angezeigt wird. Optionen: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Store-Ansicht | Aktiviert Tagline. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Cache leeren

Wenn Sie die Konfiguration ändern [Cache manuell leeren](/help/payment-services/settings.md#flush-the-cache) sodass Ihr Store die neuesten Konfigurationseinstellungen anzeigt.
