---
title: Ältere Konfiguration der Zahlungsdienste
description: Nach der Installation können Sie  [!DNL Payment Services] in der Store-Konfiguration im Admin konfigurieren.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---

# Legacy [!DNL Payment Services]-Konfiguration

Sie können [!DNL Payment Services] mit hilfreichen Konfigurationsoptionen im Admin an Ihre Anforderungen anpassen.

Wenn Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] im Admin konfigurieren, gelten diese Konfigurationen nur für die Umgebung, die im Feld _[!UICONTROL Method]_von_[!UICONTROL General Configuration]_ festgelegt ist. Alle Änderungen, die Sie in den Konfigurationsfeldern vornehmen, sind unabhängig vom Wechsel der _[!UICONTROL Method]_-Auswahl. Wenn Sie die Methode wechseln, werden Ihre Auswahlen nicht zurückgesetzt.

## Allgemeine Konfiguration

Sie können [!DNL Payment Services] für Ihren Store und Ihre _[!UICONTROL Merchant Location]_aktivieren und entweder Sandbox-Tests oder Live-Zahlungen im Abschnitt_[!UICONTROL General Configuration]_ aktivieren.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.

   ![Ansicht &quot;Methoden&quot;](assets/methods-view.png){width="400" zoomable="yes"}

1. Legen Sie das Feld _[!UICONTROL Merchant Country]_im Feld_[!UICONTROL Merchant Location]_ fest.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_, um auf den Abschnitt_[!UICONTROL [!DNL Payment Services]]_ zuzugreifen.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_den Abschnitt_[!UICONTROL General Configuration]_ .
1. Setzen Sie für **Enable** den Wert auf `Yes` , um [!DNL Payment Services] für Ihren Store zu aktivieren.
1. Setzen Sie für **Methode** den Wert auf `Sandbox` , wenn Sie weiterhin [!DNL Payment Services] für Ihren Speicher testen, oder `Production`, wenn Sie bereit sind, Live-Zahlungen zu aktivieren.

   >[!WARNING]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in ihren entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abgeschlossen haben. Entfernen oder ändern Sie diese IDs nicht.

1. Fügen Sie für **Soft Descriptor** (benutzerdefinierte Werte, die in Bankübersichten für Kundentransaktionen angezeigt werden, um zwischen Geschäften/Marken/Katalogen zu unterscheiden) im Textfeld Ihren benutzerdefinierten Text (mit bis zu 22 Zeichen) hinzu und ersetzen Sie dabei `Custom descriptor` oder den vorhandenen Wert.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

![Vorgestellte Adobe-Lösungsansicht](assets/featured-adobe-solution-view.png){width="700" zoomable="yes"}

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder deaktivieren Sie [!DNL Payment Services] für Ihre Website. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |
| [!UICONTROL Production Merchant ID] | Store-Ansicht | Ihre Produktions-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. Ändern oder ändern Sie diese ID nicht. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites einen weichen Deskriptor hinzu und speichern Sie diese, um Informationen zu Kundentransaktionen hinzuzufügen, die Marken, Stores oder Produktlinien voneinander trennen. |

## [!UICONTROL Credit Card Fields]

Die [!UICONTROL Credit Card Fields] Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) .

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Credit Card Fields]_ .
1. Geben Sie für **[!UICONTROL Title]** Text ein (falls erforderlich), um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern.
1. Um [ die Zahlungsaktion festzulegen, wählen Sie **[!UICONTROL Authorize]** oder **Autorisieren und Erfassen** aus.](production.md#set-payment-services-as-payment-method)
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie im Feld **[!UICONTROL Sort order]** einen `Numeric Only` -Wert an.
1. Wählen Sie für **[!UICONTROL Show on checkout page]** `Yes` aus, um Kreditkartenfelder auf der Checkout-Seite zu aktivieren.
1. Wählen Sie für **[!UICONTROL Vault Enabled]** `Yes` aus, um die Kreditkartenausgabe für den Checkout zu aktivieren.
1. Wählen Sie für **[!UICONTROL Vault Enabled in Admin]** `Yes` aus, damit der Händler Bestellungen für Kunden erstellt, die seine ausgefüllte Kreditkarte verwenden.
1. Um **[!UICONTROL 3DS Secure authentication]** (`Off` standardmäßig) zu aktivieren, wählen Sie `Always` oder `When required`.
1. Wählen Sie für **[!UICONTROL Debug Mode]** `Yes` , um den Debug-Modus zu aktivieren, oder `No`, um ihn zu deaktivieren.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` Wert |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie Kreditkartenfelder auf der Checkout-Seite. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die [Kreditkartenausgabe](vaulting.md). Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | Store-Ansicht | Aktivierung oder Deaktivierung der Fähigkeit von [Händlern, Bestellungen für Kunden in Admin](vaulting.md) mit einer gültigen Zahlungsmethode abzuschließen. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | website | Aktivieren oder deaktivieren Sie die sichere [3DS-Authentifizierung](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

Mit der Zahlungsoption [!UICONTROL Apple Pay] kann der Händler seinen Kunden Apple Pay anbieten, die über die Touch-ID auf ihren Geräten Käufe über den Safari-Browser tätigen können. Händler können bis zu 99 Domänen pro Händlerkonto hinzufügen.

Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#apple-pay-button) .

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Apple Pay]_ .
1. Geben Sie für **[!UICONTROL Title]** Text ein (falls erforderlich), um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern.
1. Um [ die Zahlungsaktion festzulegen, wählen Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]** aus.](production.md#set-payment-services-as-payment-method)
1. Geben Sie an, wo die Option [!DNL Apple Pay] in Adobe Commerce aktiviert ist, indem Sie nach Bedarf in den folgenden Optionen die Option `Yes` auswählen:
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für den **[!UICONTROL Debug Mode]** (`No` deaktiviert ihn).
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode angezeigt werden soll. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Checkout-Seite. `Numeric Only` Wert |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Apple Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

Mit der Zahlungsoption [!UICONTROL Google Pay] kann der Händler seinen Käufern Google Pay anbieten, die die Google-Geldbörse auf ihren Geräten verwenden können, um Käufe zu tätigen.

Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#google-pay-button) .

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL Google Pay]_ .
1. (Optional) Ändern Sie den Namen der beim Checkout angezeigten Zahlungsmethode, indem Sie den neuen Namen in das Feld **[!UICONTROL Title]** eingeben.
1. [Legen Sie die Zahlungsaktion fest](production.md#set-payment-services-as-payment-method), indem Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]** auswählen.
1. Geben Sie an, wo die Option [!DNL Google Pay] in Adobe Commerce aktiviert ist, indem Sie nach Bedarf in den folgenden Optionen die Option `Yes` auswählen:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für den **[!UICONTROL Debug Mode]** (`No` deaktiviert ihn).
1. Konfigurieren Sie das Erscheinungsbild der Schaltfläche _[!UICONTROL Google Pay]_, indem Sie die Schaltflächen **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**und **[!UICONTROL Button Style]**nach Bedarf auswählen.
1. Zum Festlegen der Höhe verwendet den Standardwert für die in **[!UICONTROL Button Style]** definierte Höhe.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Gibt die Textbeschriftung an, die während des Checkouts in der Ansicht &quot;Zahlungsmethode&quot;für diese Zahlungsoption angezeigt wird. Optionen: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) für die angegebene Zahlungsmethode. Optionen: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie [!DNL Google Pay] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Checkout-Seite. `Numeric Only` Wert |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Google Pay] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Google Pay] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL Google Pay] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Store-Ansicht | Definieren Sie die Farbe der Schaltfläche [!DNL Google Pay] . Optionen: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Store-Ansicht | Definieren Sie den Typ der Schaltfläche [!DNL Google Pay] . Optionen: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Weitere Informationen finden Sie in der Dokumentation zu den Optionen für Google Pay API-Anforderungsobjekte](https://developers.google.com/pay/api/web/reference/request-objects) .[

## [!DNL PayPal Payment Buttons]

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden.

Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) .

Konfigurieren von [!DNL PayPal payment buttons]

Sie können die Zahlungsoptionen der PayPal-Zahlungsschaltflächen innerhalb des Administrators aktivieren und konfigurieren:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL Payment Services]_den Abschnitt_[!UICONTROL PayPal payment buttons]_ .
1. Um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern, bearbeiten Sie das Feld _[!UICONTROL Title]_.
1. Um [ die Zahlungsaktion festzulegen, wählen Sie **[!UICONTROL Authorize]** oder **[!UICONTROL Authorize and Capture]** aus.](production.md#set-payment-services-as-payment-method)
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie im Feld **[!UICONTROL Sort order]** einen `Numeric Only` -Wert an.
1. Um die [Später Nachrichten bezahlen](payments-options.md#pay-later-button) zu aktivieren/deaktivieren, wählen Sie `Yes`/`No` für **[!UICONTROL Display Pay Later Message]** aus.
1. Geben Sie an, wo die PayPal-Zahlungsschaltflächen in Adobe Commerce aktiviert sind, indem Sie in den folgenden Optionen nach Bedarf `Yes` auswählen:
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Um Venmo als Zahlungsoption zu aktivieren, wählen Sie `Yes` für **[!UICONTROL Venmo Enabled]** aus.
1. Um Kredit- und Debitkarten als Zahlungsoption zu aktivieren (PayPal Smart-Schaltfläche), wählen Sie `Yes` für **[!UICONTROL Credit and Debit Card Enabled]** aus.
1. Um die Zahlungsoption [PayPal Pay Later Pay Pay Later](payments-options.md#pay-later-button) zu aktivieren/deaktivieren, wählen Sie `Yes`/`No` für **[!UICONTROL PayPal Pay Later Enabled]** aus.
1. Um den Debug-Modus zu aktivieren, wählen Sie `Yes` für den **[!UICONTROL Debug Mode]** (`No` deaktiviert ihn).
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Checkout-Seite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Warenkorbseite. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Optionen der Kredit- und Debitkarte, in denen Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die PayPal PayPal Pay Later Payment-Option, wenn Zahlungsschaltflächen angezeigt werden. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_-Optionen der Zahlungsschaltflächen konfigurieren:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich den Wert **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Payment Methods]** aus.
1. Erweitern Sie den Abschnitt _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. Erweitern Sie im Abschnitt _[!UICONTROL [!DNL Payment Services]]_den Abschnitt_[!UICONTROL PayPal Smart Button Styling]_ .
1. Um das Layout festzulegen, wählen Sie `Vertical` oder `Horizontal` für **[!UICONTROL Layout]** aus
1. Um die Farbe festzulegen, wählen Sie aus den verfügbaren Farben in **[!UICONTROL Color]** aus.
1. Um die Form festzulegen, wählen Sie `Rectangular` oder `Pill` für **[!UICONTROL Shape]** aus.
1. Um die Standardhöhe zu verwenden, wählen Sie `Yes` oder `No` für **[!UICONTROL Use Default Height]** aus.
1. Um die benutzerdefinierte Höhe festzulegen, fügen Sie die gewünschte Pixelhöhe für **[!UICONTROL Height]** hinzu.
1. Um die Tagline festzulegen, wählen Sie `Yes` oder `No` für **[!UICONTROL Tagline]** aus.
1. Klicken Sie auf **[!UICONTROL Save Config]** , um Ihre Änderungen zu speichern.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie dann auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können auch den Stil der Zahlungsschaltfläche [in Einstellungen](settings.md#button-style) von der Zahlungsdienst-Startseite aus konfigurieren.

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

Wenn Sie die Konfiguration ändern, leeren Sie den Cache ](/help/payment-services/settings.md#flush-the-cache) manuell, sodass Ihr Speicher die neuesten Konfigurationseinstellungen anzeigt.[
