---
title: Zahlungsdiensteinstellungen
description: Nach der Installation können Sie [!DNL Payment Services] in der Startseite.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration
source-git-commit: 85f8e158509231fb3b30c778309a9ac0fb468131
workflow-type: tm+mt
source-wordcount: '2410'
ht-degree: 0%

---

# Einstellungen

Sie können [!DNL Payment Services] entsprechend Ihren Anforderungen mithilfe hilfreicher Einstellungen im [!DNL Payment Services] Home.

So konfigurieren Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im _[!UICONTROL Payment mode]_des[_ Allgemein _Konfigurationsoptionen](#configure-general-settings).

Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie unter [In Admin konfigurieren](configure-admin.md).

## Allgemeine Einstellungen konfigurieren

Die [!UICONTROL General] -Einstellungen bieten die Möglichkeit, Zahlungsdienste als Zahlungsmethode zu aktivieren oder zu deaktivieren und Kundentransaktionen Informationen hinzuzufügen, um eine Website oder Store-Ansicht mit benutzerspezifischen Informationen zu markieren oder zu präfixieren.

### Zahlungsdienste aktivieren

Sie können [!DNL Payment Services] für Ihre Website hinzufügen und entweder Sandbox-Tests oder Live-Zahlungen aktivieren.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Startansicht](assets/payment-services-menu-small.png){width="400" zoomable="yes"}

1. Klicken **[!UICONTROL Settings]**. Siehe [Einführung in [!DNL Payment Services] Startseite](payments-home.md) für weitere Informationen.

   Die _[!UICONTROL General]_enthält Einstellungen, die zum Aktivieren von [!DNL Payment Services] als Zahlungsmethode.

1. Aktivieren [!DNL Payment Services] als Zahlungsmethode für Ihren Speicher in der _[!UICONTROL General]_Abschnitt, umschalten **[!UICONTROL Enable Payment Services as payment method]**nach `Yes`.

1. Wenn Sie noch testen [!DNL Payment Services] für Ihren Store festlegen **Zahlungsmodus** nach `Sandbox`. Wenn Sie bereit sind, Live-Zahlungen zu aktivieren, setzen Sie sie auf `Production`.

   >[!NOTE]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abschließen.

1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können jetzt die Standardeinstellungen für [Zahlungsoptionen](#configure-payment-options) Funktionen und Anzeige der Storefront.

### Hinzufügen eines Softdeskriptors

Sie können eine [!UICONTROL Soft Descriptor] zu Ihrer Website(s) oder Konfiguration einzelner Store-Ansichten hinzufügen. Softbounce-Deskriptoren werden in Kontoauszügen von Kunden angezeigt. Wenn Sie beispielsweise über mehrere Stores/Marken/Kataloge verfügen, können Sie diese einfach trennen, indem Sie benutzerdefinierten Text zum [!UICONTROL Soft Descriptor] -Feld.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Settings]**. Siehe [Einführung in [!DNL Payment Services] Startseite](payments-home.md) für weitere Informationen.
1. Wählen Sie die Website- oder Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie einen weichen Deskriptor erstellen möchten. Behalten Sie für die Ersteinrichtung Folgendes bei: **[!UICONTROL Default]** , um den Standardwert festzulegen.
1. Fügen Sie Ihren benutzerdefinierten Text (bis zu 22 Zeichen) in das Textfeld ein und ersetzen Sie `Custom descriptor`.
1. Klicken **[!UICONTROL Save]**.
1. So erstellen Sie einen anderen Soft-Deskriptor als den konfigurierten Standard für eine Website- oder Store-Ansicht:
   1. Wählen Sie die Website- oder Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie einen weichen Deskriptor erstellen möchten.
   1. Umschalten _off_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]**, abhängig vom ausgewählten Bereich).
   1. Fügen Sie Ihren benutzerdefinierten Text in das Textfeld ein.
   1. Klicken **[!UICONTROL Save]**.
1. So aktivieren Sie für eine Website oder eine Store-Ansicht den standardmäßigen Softdeskriptor _oder_ der für die übergeordnete Website verwendete Softdeskriptor:
   1. Wählen Sie die Website- oder Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie einen vorhandenen Soft-Deskriptor aktivieren möchten.
   1. Umschalten _on_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]** je nach ausgewähltem Bereich).
   1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Payment Services] für Ihre Website. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Production Merchant ID] | Store-Ansicht | Ihre Produktions-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites einen weichen Deskriptor hinzu und speichern Sie diese, um Informationen zu Kundentransaktionen hinzuzufügen, die Marken, Stores oder Produktlinien voneinander trennen. Die [!UICONTROL Use website] toggle wendet einen beliebigen Soft-Deskriptor an, der auf Website-Ebene hinzugefügt wird. Die [!UICONTROL Use default] toggle wendet einen beliebigen Softdescriptor an, der als Standard hinzugefügt wurde. |

## Zahlungsoptionen konfigurieren

Nachdem Sie die [!UICONTROL Payment Services] für Ihre Website können Sie die Standardeinstellungen für Zahlungsfunktionen und Storefront-Anzeige ändern.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Settings]**. Siehe [Einführung in [!DNL Payment Services] Startseite](payments-home.md) für weitere Informationen.
1. Zahlungsoptionen konfigurieren für [Kreditkarten](#credit-card-fields), [Zahlungsschaltflächen](#payment-buttons), und [Schaltflächenstil](#button-style), entsprechend den folgenden Abschnitten.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_Einstellungen bieten eine einfache und sichere Checkout-Option für Kreditkarten- oder Debitkartenzahlmethoden.

Siehe [Zahlungsoptionen](payments-options.md#credit-card-fields) für weitere Informationen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie die Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie eine Zahlungsmethode aktivieren möchten.
1. Im **[!UICONTROL Credit card fields]** Bearbeiten Sie den Wert im Abschnitt **[!UICONTROL Checkout title]** -Feld, um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie eine `Numeric Only` Wert in **[!UICONTROL Sort order]** -Feld.
1. Aktivieren [Sichere 3DS-Authentifizierung](security.md#3ds) (`Off` standardmäßig) können Sie die **[!UICONTROL 3DS Secure authentication]** Auswahl zu `Always` oder `When required`.
1. Um Kreditkartenfelder auf der Checkout-Seite zu aktivieren oder zu deaktivieren, aktivieren Sie die **[!UICONTROL Show on checkout page]** auswählen.
1. Aktivieren oder Deaktivieren [Kartengewölbe](#card-vaulting), um die **[!UICONTROL Vault enabled]** auswählen.
1. Aktivieren oder Deaktivieren [Gültige Zahlungsmethoden im Admin](#card-vaulting) (Damit Händler ihre Bestellungen für Kunden in der Admin-Konsole mit ihrer gültigen Zahlungsmethode abschließen können), schalten Sie die **[!UICONTROL Show vaulted methods in Admin]** auswählen.
1. Um den Debug-Modus zu aktivieren bzw. zu deaktivieren, müssen Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Cache leeren](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` value |
| [!UICONTROL 3DS Secure authentication] | website | Aktivieren oder Deaktivieren [Sichere 3DS-Authentifizierung](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie Kreditkartenfelder, die auf der Checkout-Seite angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | Store-Ansicht | Aktivieren oder Deaktivieren [Kreditkartenausfall](vaulting.md). Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | Store-Ansicht | Aktivierung oder Deaktivierung der Möglichkeit für Händler, Bestellungen für Kunden in Admin abzuschließen [Verwendung einer gültigen Zahlungsmethode](vaulting.md). Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

Die [!UICONTROL Apple Pay] Die Zahlungsoption für Schaltflächen ermöglicht die Bereitstellung einer [!UICONTROL Apple Pay] Zahlungsschaltfläche im Checkout Ihres Geschäfts.

Sie können Apple Pay nur verwenden, wenn Sie [Apple Pay-Selbstregistrierung über Paypal](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) und dann [Apple Pay konfigurieren](settings.md/#payment-buttons) für Ihre Geschäfte. Siehe [Zahlungsoptionen](payments-options.md#apple-pay-button) für weitere Informationen.

Sie können die [!UICONTROL Apple Pay] Schaltflächenzahloption:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie die Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie eine Zahlungsmethode aktivieren möchten.
1. Im **[!UICONTROL Apple Pay]** Bearbeiten Sie den Wert im Abschnitt _[!UICONTROL Checkout title]_-Feld, um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Um Apple Pay auf der Checkout-Seite zu aktivieren bzw. zu deaktivieren, müssen Sie die **[!UICONTROL Show Apple Pay on checkout page]** auswählen.
1. Um Apple Pay auf der Produktdetailseite zu aktivieren oder zu deaktivieren, aktivieren Sie die **[!UICONTROL Show Apple Pay on product detail page]** auswählen.
1. Um Apple Pay in der Vorschau des kleinen Warenkorbs zu aktivieren bzw. zu deaktivieren, aktivieren Sie die Option **[!UICONTROL Show Apple Pay on the mini cart preview]** auswählen.
1. Um Apple Pay auf der Warenkorbseite zu aktivieren bzw. zu deaktivieren, aktivieren Sie die **[!UICONTROL Show Apple Pay on cart page]** auswählen.
1. Um den Debug-Modus zu aktivieren bzw. zu deaktivieren, müssen Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Cache leeren](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Checkout title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Checkout-Seite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Produktdetailseite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | website | Aktivieren oder deaktivieren Sie die Apple-Schaltfläche &quot;Bezahlen&quot;, um sie in der Vorschau des kleinen Warenkorbs anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Warenkorbseite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Zahlungsschaltflächen

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Sie können die Zahlungsoptionen für PayPal-Smart-Schaltflächen aktivieren und konfigurieren:

1. Wählen Sie die Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie eine Zahlungsmethode aktivieren möchten.
1. Um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern, bearbeiten Sie den Wert im **[!UICONTROL Checkout Title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie eine `Numeric Only` Wert in **[!UICONTROL Sort order]** -Feld.
1. Umschalter-Selektoren zum Aktivieren oder Deaktivieren [!DNL PayPal smart button] Anzeigefunktionen:

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Verwenden von Apple Pay You [muss über ein Apple-Sandbox-Tester-Konto verfügen](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (mit gefälschten Kreditkarten- und Rechnungsinformationen), um sie zu testen. Wenn Sie bereit sind, Apple Pay in Sandbox zu verwenden _oder_ Produktionsmodus, nach Abschluss [Tests und Validierung](test-validate.md#test-in-sandbox-environment), complete [Selbstregistrierung mit [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Live-Domäne registrieren_ nur -Abschnitt) und [Konfigurieren Sie es für Ihre Stores in [!DNL Payment Services]](settings.md#payment-buttons).

     Wenn Sie die Sichtbarkeit auf die Zahlungsschaltflächen oder die PayPal PayPay-später-Nachricht aktivieren/deaktivieren, wird unten auf der Seite &quot;Einstellungen&quot;eine visuelle Vorschau dieser Konfiguration angezeigt.

1. Um den Debug-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Cache leeren](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` value |
| [!UICONTROL Show PayPal buttons on checkout page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Checkout-Seite. Optionen: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Produktdetailseite. Optionen: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] in der Vorschau des Mini-Warenkorbs. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Warenkorbseite. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | Store-Ansicht | Aktivieren oder deaktivieren Sie das Erscheinungsbild der Zahlungsoption Spätere Zahlung , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Apple-Zahlungsoption, bei der Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Option Kreditkartenzahlung und Debitkarte, wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der Zahlungsschaltflächen:

1. So ändern Sie die **[!UICONTROL Layout]** auswählen `Vertical` oder `Horizontal`.

   >[!NOTE]
   >
   > Wenn der Schaltflächenstil als `Horizontal` und Ihr Store so konfiguriert ist, dass mehrere Zahlungsschaltflächen angezeigt werden, werden möglicherweise nur zwei Schaltflächen auf der Produktseite, auf der Checkout-Seite und im Mini-Warenkorb sowie eine Schaltfläche im Warenkorb angezeigt.

1. Um die Tagline in einem horizontalen Layout zu aktivieren, können Sie die **[!UICONTROL Show tagline]** auswählen.
1. So ändern Sie die **[!UICONTROL Color]** wählen Sie die gewünschte Farboption aus.
1. So ändern Sie die **[!UICONTROL Shape]** auswählen `Pill` oder `Rectangle`.
1. Um die Auswahl der Schaltflächenhöhe zu aktivieren, schalten Sie die **[!UICONTROL Responsive button height]** auswählen.
1. So ändern Sie die **[!UICONTROL Label]** wählen Sie die gewünschte Beschriftungsoption aus.

   Wenn Sie die Konfigurationsoptionen für Layout, Farbe, Form, Höhe und Beschriftung ändern, wird unten auf der Seite &quot;Einstellungen&quot;eine visuelle Vorschau dieser Konfiguration angezeigt.

   ![[!DNL PayPal Smart Buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Cache leeren](#flush-the-cache).

Sie können die Formatierung von Zahlungsschaltflächen konfigurieren [in der Legacy-Konfiguration in der Admin-Konsole](configure-admin.md#configure-paypal-smart-buttons) oder hier [!DNL Payment Services Home]. Siehe [Handbuch zum Schaltflächenstil von PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) für weitere Informationen zum Formatieren von PayPal-Zahlungsschaltflächen.

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Store-Ansicht | Definieren Sie den Stil des Layouts für Zahlungsschaltflächen. Optionen: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Store-Ansicht | Aktivieren/deaktivieren Sie die Tagline. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | Store-Ansicht | Definieren Sie die Farbe der Zahlungsschaltflächen. Optionen: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Store-Ansicht | Definieren Sie die Form der Zahlungsschaltflächen. Optionen: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Store-Ansicht | Definiert, ob Zahlungsschaltflächen eine Standardhöhe verwenden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | Store-Ansicht | Definieren Sie die Höhe der Zahlungsschaltflächen. Standardwert: keiner |
| [!UICONTROL Label] | Store-Ansicht | Definieren Sie den Titel, der in den Zahlungsschaltflächen angezeigt wird. Optionen: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Rollen konfigurieren

Um sicherzustellen, dass Admin-Benutzer Bestellungen in Commerce Admin erstellen und verwalten können, aktivieren Sie [!DNL Payment Services]-spezifische Ressourcen für Benutzerrollen.

Siehe [Benutzerrollen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) , um zu erfahren, wie Rollen verwaltet werden.

Beim Zuweisen von Ressourcen zur Rolle müssen Sie Folgendes auswählen:

- **Bezahlen mit[!DNL Payment Services]**—Diese Ressource stellt sicher, dass beim Erstellen einer Bestellung in der Admin-Konsole [!DNL Payment Services] Kreditkarten sind als Zahlungsmethode verfügbar. Wenn Sie die **Aktionen** übergeordnete Ressource, wird diese Ressource ebenfalls ausgewählt.
- **[!DNL Payment Services]**—Diese Ressource enthält die **Dashboard** und **SaaS-Dienste-Proxy** Ressourcen, die ebenfalls ausgewählt werden müssen. Sie stellen sicher, dass [!DNL Payment Services] im _Vertrieb_ Menü.

  ![Zahlungsdienste-Ressourcen](assets/roles-payments.png){width="400" zoomable="yes"}

## Cache leeren

Wenn Sie die Konfiguration in _Einstellungen_ Wenn Sie beispielsweise die Schaltflächen Apple Pay, Venmo oder PayPal PayLater umschalten, leeren Sie den Cache manuell, sodass Ihr Store die neuesten Konfigurationen anzeigt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicks **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Wenn ein beliebiger Cache-Typ in der Tabelle &quot;Cache Management&quot;über eine `INVALIDATED` -Status, zeigt Ihr Store möglicherweise nicht die neueste Konfiguration für dieses Element an. Leeren Sie den Cache, um Ihren Store zu aktualisieren und die neueste Konfiguration anzuzeigen.

Um sicherzustellen, dass Ihr Store die richtige Konfiguration anzeigt, werden regelmäßig [Cache leeren](https://docs.magento.com/user-guide/system/cache-management.html).

## Kartengewölbe

Sie können Funktionen aktivieren, mit denen Ihre Kunden ihre Kreditkarteninformationen in ihrem Mein Konto für zukünftige Käufe verwenden oder speichern können.

Sie können auch die Kartenauswertung in Admin verwenden, um nachfolgende Bestellungen für bestehende Kunden abzuschließen.

Aktivieren oder deaktivieren Sie die Kartenüberprüfung im [Einstellungen für Kreditkartenfelder](#credit-card-fields).

Siehe [Kreditkartenausnahme](vaulting.md) für weitere Informationen.

## 3DS

3DS schützt Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften und ermöglicht die Einhaltung der EU-Standards.

Aktivieren oder deaktivieren Sie 3DS im [Einstellungen für Kreditkartenfelder](#credit-card-fields).

Siehe [3DS in Sicherheit](security.md#3ds) für weitere Informationen.

## Verwenden mehrerer PayPal-Konten

In [!UICONTROL Payment Services], können Sie mehrere PayPal-Konten in **one** Handelskonto auf der Website-Ebene. Wenn Sie beispielsweise Ihre Geschäfte in mehreren Ländern betreiben (die unterschiedliche [Währungen](https://docs.magento.com/user-guide/stores/currency.html)) oder möchten Adobe Commerce für einige Teile Ihres Unternehmens verwenden, jedoch nicht _all_ können Sie Ihr Händlerkonto so einrichten, dass mehrere PayPal-Konten verwendet werden.

Siehe [Site-, Store- und Ansichtsbereich](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) für weitere Informationen zur Hierarchie von Websites, Stores und Store-Ansichten.

Ihr Vertriebsmitarbeiter kann eine neue [Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) für Ihr Händlerkonto und die zusätzliche Site mit PayPal einbinden, sodass alle PayPal-Schaltflächen, die Sie konfigurieren, auf Ihrer Site angezeigt werden. Wenden Sie sich an Ihren Vertriebsmitarbeiter, um Unterstützung bei der Verwendung mehrerer PayPal-Konten für Ihre Websites zu erhalten.
