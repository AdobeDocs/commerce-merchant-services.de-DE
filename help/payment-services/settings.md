---
title: Zahlungsdiensteinstellungen
description: Nach der Installation können Sie  [!DNL Payment Services] auf der Startseite konfigurieren.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# Einstellungen

Sie können [!DNL Payment Services] mit hilfreichen Einstellungen auf der [!DNL Payment Services]-Startseite an Ihre Anforderungen anpassen.

Um [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zu konfigurieren, klicken Sie auf **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im Feld _[!UICONTROL Payment mode]_der Konfigurationsoptionen[_ Allgemein _im Feld ](#configure-general-settings) festgelegt ist.

Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie unter [Konfigurieren in der Admin-Konsole](configure-admin.md).

## Allgemeine Einstellungen konfigurieren

Die [!UICONTROL General] -Einstellungen bieten die Möglichkeit, Zahlungsdienste als Zahlungsmethode zu aktivieren oder zu deaktivieren und Kundentransaktionen Informationen hinzuzufügen, um eine Website- oder Store-Ansicht mit benutzerdefinierten Informationen zu kennzeichnen oder ihnen vorzustellen.

### Zahlungsdienste aktivieren

Sie können [!DNL Payment Services] für Ihre Website aktivieren und entweder Sandbox-Tests oder Live-Zahlungen aktivieren.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden Sie unter [Einführung in  [!DNL Payment Services] Startseite](payments-home.md) .

   ![Ansicht &quot;React settings&quot;](assets/react-settings-view.png){width="500" zoomable="yes"}

   Der Abschnitt _[!UICONTROL General]_enthält Einstellungen, mit denen [!DNL Payment Services] als Zahlungsmethode aktiviert wird.

1. Um [!DNL Payment Services] als Zahlungsmethode für Ihren Speicher zu aktivieren, schalten Sie im Abschnitt _[!UICONTROL General]_**[!UICONTROL Enable Payment Services as payment method]**auf `Yes` um.

1. Wenn Sie weiterhin [!DNL Payment Services] für Ihren Store testen, setzen Sie **Zahlungsmodus** auf `Sandbox`. Wenn Sie bereit sind, Live-Zahlungen zu aktivieren, setzen Sie sie auf `Production`.

1. Ihre Werte **[!UICONTROL Payment Services Sandbox ID]** und **[!UICONTROL Payment Services Production ID]** werden automatisch ausgefüllt, sobald Sie den [Commerce Services Connector](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} eingerichtet und das Dashboard [!DNL Payment Services] zum ersten Mal aufgerufen haben. Führen Sie diese Schritte aus, um das Onboarding für Ihre Sandbox- und/oder Produktionsumgebungen abzuschließen. Diese Werte verknüpfen Ihre SaaS-ID mit [!DNL Payment Services].

   >[!WARNING]
   >
   > Wenn Sie Ihre [!DNL Payment Services] -IDs zurücksetzen, müssen Sie erneut eingebunden werden.

1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können jetzt mit der Änderung der Standardeinstellungen für [Zahlungsoptionen](#configure-payment-options)-Funktionen und die Anzeige der Storefront fortfahren.

### Hinzufügen eines Softdeskriptors

Sie können Ihrer Website(n) oder einzelnen Speicheransichtskonfigurationen einen [!UICONTROL Soft Descriptor] hinzufügen. Softbounce-Deskriptoren werden in Kontoauszügen von Kunden angezeigt. Wenn Sie beispielsweise über mehrere Stores/Marken/Kataloge verfügen, können Sie diese einfach trennen, indem Sie benutzerdefinierten Text zum Feld [!UICONTROL Soft Descriptor] hinzufügen.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden Sie unter [Einführung in  [!DNL Payment Services] Startseite](payments-home.md) .
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen weichen Deskriptor erstellen möchten. Lassen Sie bei der Ersteinrichtung diesen Wert auf **[!UICONTROL Default]**, um den Standardwert festzulegen.
1. Fügen Sie Ihren benutzerdefinierten Text (bis zu 22 Zeichen) in das Textfeld ein und ersetzen Sie dadurch `Soft descriptor`.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. So erstellen Sie einen anderen Soft-Deskriptor als den konfigurierten Standard für eine Website- oder Store-Ansicht:
   1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen weichen Deskriptor erstellen möchten.
   1. Schalten Sie _aus_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]**, je nachdem, welchen Bereich Sie ausgewählt haben) um.
   1. Fügen Sie Ihren benutzerdefinierten Text in das Textfeld ein.
   1. Klicken Sie auf **[!UICONTROL Save]**.
1. Um für eine Website- oder Store-Ansicht zu aktivieren, verwenden Sie den standardmäßigen Softdeskriptor _oder_ des für die übergeordnete Website verwendeten Softdeskriptors:
   1. Wählen Sie im Dropdown-Menü **[!UICONTROL Scope]** die Website- oder Store-Ansicht aus, für die Sie einen vorhandenen Softbounce aktivieren möchten.
   1. Schalten Sie _für_ **[!UICONTROL Use website]** (oder **[!UICONTROL Use default]** ein, je nach ausgewähltem Umfang).
   1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder deaktivieren Sie [!DNL Payment Services] für Ihre Website. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Payment Services Production ID] | Store-Ansicht | Ihre Produktions-Merchant-ID, die beim (Live-)Onboarding der Produktion automatisch generiert wird. |
| [!UICONTROL Soft Descriptor] | Website- oder Store-Ansicht | Fügen Sie Ihren Websites einen weichen Deskriptor hinzu und speichern Sie diese, um Informationen zu Kundentransaktionen hinzuzufügen, die Marken, Stores oder Produktlinien voneinander trennen. Mit dem Umschalter [!UICONTROL Use website] wird jeder weiche Deskriptor angewendet, der auf Website-Ebene hinzugefügt wird. Mit dem Umschalter [!UICONTROL Use default] wird jeder weiche Deskriptor angewendet, der als Standard hinzugefügt wurde. |

## Zahlungsoptionen konfigurieren

Nachdem Sie jetzt [!UICONTROL Payment Services] für Ihre Website aktiviert haben, können Sie die Standardeinstellungen für Zahlungsfunktionen und Storefront-Anzeige ändern.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Settings]**. Weitere Informationen finden Sie unter [Einführung in  [!DNL Payment Services] Startseite](payments-home.md) .
1. Konfigurieren Sie die Zahlungsoptionen für [Kreditkarten](#credit-card-fields), [Zahlungsschaltflächen](#payment-buttons) und [Schaltflächenstil](#button-style) gemäß den folgenden Abschnitten.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_-Einstellungen bieten eine einfache und sichere Checkout-Option für Kreditkarten- oder Debitkartenzahlmethoden.

Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#credit-card-fields) .

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie die Store-Ansicht im Dropdown-Menü **[!UICONTROL Scope]** aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Bearbeiten Sie im Abschnitt **[!UICONTROL Credit card fields]** den Wert im Feld **[!UICONTROL Checkout title]** , um den Namen der beim Checkout angezeigten Zahlungsmethode zu ändern.
1. Um [ die Zahlungsaktion](production.md#set-payment-services-as-payment-method) festzulegen, schalten Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture` um.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie im Feld **[!UICONTROL Sort order]** einen `Numeric Only` -Wert an.
1. Um die sichere [3DS-Authentifizierung](security.md#3ds) (`Off` standardmäßig) zu aktivieren, schalten Sie den **[!UICONTROL 3DS Secure authentication]** -Selektor auf `Always` oder `When required` um.
1. Um Kreditkartenfelder auf der Checkout-Seite zu aktivieren bzw. zu deaktivieren, aktivieren Sie die Auswahl **[!UICONTROL Show on checkout page]** .
1. Um die [Kartenwertaufzeichnung](#card-vaulting) zu aktivieren oder zu deaktivieren, schalten Sie den **[!UICONTROL Vault enabled]** -Selektor um.
1. Um [wertvolle Zahlungsmethoden in Admin](#card-vaulting) zu aktivieren oder zu deaktivieren (damit Händler Bestellungen von Kunden in Admin mit ihrer bewährten Zahlungsmethode abschließen können), aktivieren Sie den Selektor **[!UICONTROL Show vaulted methods in Admin]** .
1. Um den Debug-Modus zu aktivieren oder zu deaktivieren, schalten Sie den &quot;**[!UICONTROL Debug Mode]**&quot;-Selektor um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` Wert |
| [!UICONTROL 3DS Secure authentication] | website | Aktivieren oder deaktivieren Sie die sichere [3DS-Authentifizierung](security.md#3ds). Optionen: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie Kreditkartenfelder, die auf der Checkout-Seite angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | Store-Ansicht | Aktivieren oder deaktivieren Sie die [Kreditkartenausgabe](vaulting.md). Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | Store-Ansicht | Aktivierung oder Deaktivierung der Möglichkeit für Händler, Bestellungen für Kunden in der Admin-Konsole [mit einer gültigen Zahlungsmethode](vaulting.md) abzuschließen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

Mit der Zahlungsoption für die Schaltfläche [!UICONTROL Apple Pay] können Sie eine Zahlungsschaltfläche für [!UICONTROL Apple Pay] beim Checkout Ihres Geschäfts aus dem Safari-Browser bereitstellen (für bis zu 99 Domänen pro Händlerkonto).

Sie können Apple Pay nur verwenden, wenn Sie die [Apple Pay-Selbstregistrierung über Paypal](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) abgeschlossen haben und dann für Ihre Geschäfte [Apple Pay](settings.md/#payment-buttons) konfigurieren. Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#apple-pay-button) .

Sie können die Zahlungsoption für die Schaltfläche [!UICONTROL Apple Pay] aktivieren und konfigurieren:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Wählen Sie die Store-Ansicht im Dropdown-Menü **[!UICONTROL Scope]** aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Bearbeiten Sie im Abschnitt **[!UICONTROL Apple Pay]** den Wert im Feld _[!UICONTROL Checkout title]_, um den Namen der beim Checkout angezeigten Zahlungsmethode zu ändern.
1. Um [ die Zahlungsaktion](production.md#set-payment-services-as-payment-method) festzulegen, schalten Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture` um.
1. Um die Apple-Bezahlung auf der Checkout-Seite zu aktivieren oder zu deaktivieren, aktivieren Sie den &quot;**[!UICONTROL Show Apple Pay on checkout page]**&quot;-Selektor.
1. Um Apple Pay auf der Produktdetailseite zu aktivieren oder zu deaktivieren, aktivieren Sie die Auswahl &quot;**[!UICONTROL Show Apple Pay on product detail page]**&quot;.
1. Um Apple Pay in der Vorschau des kleinen Warenkorbs zu aktivieren bzw. zu deaktivieren, aktivieren Sie die Auswahl &quot;**[!UICONTROL Show Apple Pay on the mini cart preview]**&quot;.
1. Um die Apple-Bezahlung auf der Warenkorbseite zu aktivieren bzw. zu deaktivieren, aktivieren Sie die Auswahl &quot;**[!UICONTROL Show Apple Pay on cart page]**&quot;.
1. Um den Debug-Modus zu aktivieren oder zu deaktivieren, schalten Sie den &quot;**[!UICONTROL Debug Mode]**&quot;-Selektor um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Checkout title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions) für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Checkout-Seite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Produktdetailseite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | website | Aktivieren oder deaktivieren Sie die Apple-Schaltfläche &quot;Bezahlen&quot;, um sie in der Vorschau des kleinen Warenkorbs anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | website | Aktivieren oder deaktivieren Sie die Apple-Zahlungsschaltfläche , um sie auf der Warenkorbseite anzuzeigen. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Zahlungsschaltflächen

Die [!DNL PayPal payment buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Weitere Informationen finden Sie unter [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) .

Sie können die Zahlungsoptionen der PayPal-Zahlungsschaltflächen aktivieren und konfigurieren:

1. Wählen Sie die Store-Ansicht im Dropdown-Menü **[!UICONTROL Scope]** aus, für die Sie eine Zahlungsmethode aktivieren möchten.
1. Um den Namen der Zahlungsmethode wie beim Checkout angezeigt zu ändern, bearbeiten Sie den Wert im Feld **[!UICONTROL Checkout Title]** .
1. Um [ die Zahlungsaktion](production.md#set-payment-services-as-payment-method) festzulegen, schalten Sie **[!UICONTROL Payment action]** auf `Authorize` oder `Authorize and Capture` um.
1. Um eine Zahlungsmethode auf der Checkout-Seite zu priorisieren, geben Sie im Feld **[!UICONTROL Sort order]** einen `Numeric Only` -Wert an.
1. Verwenden Sie die Umschalter-Selektoren, um die [!DNL PayPal smart button]-Anzeigefunktionen zu aktivieren oder zu deaktivieren:

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
     > Um Apple Pay verwenden zu können, müssen Sie über ein Apple-Sandbox-Tester-Konto](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) verfügen (einschließlich gefälschter Kreditkarten- und Rechnungsinformationen), um es zu testen. [ Wenn Sie bereit sind, Apple Pay im Sandbox- _oder_ Produktionsmodus zu verwenden, schließen Sie nach Abschluss von [ Tests und Validierung](test-validate.md#test-in-sandbox-environment) die [Selbstregistrierung mit  [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Nur die Live-Domäne registrieren_ ) ab und konfigurieren Sie sie für Ihre Geschäfte in  [!DNL Payment Services]](settings.md#payment-buttons).[

     Wenn Sie die Sichtbarkeit auf die Zahlungsschaltflächen oder die PayPal PayPay-später-Nachricht aktivieren/deaktivieren, wird unten auf der Seite &quot;Einstellungen&quot;eine visuelle Vorschau dieser Konfiguration angezeigt.

1. Um den Debug-Modus zu aktivieren, schalten Sie den &quot;**[!UICONTROL Debug Mode]**&quot;-Selektor um.
1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | Store-Ansicht | Die Sortierreihenfolge für die angegebene Zahlungsmethode auf der Kassenseite. `Numeric Only` Wert |
| [!UICONTROL Show PayPal buttons on checkout page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Checkout-Seite. Optionen: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Produktdetailseite. Optionen: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] in der Vorschau des Mini-Warenkorbs. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | Store-Ansicht | Aktivieren oder deaktivieren Sie [!DNL PayPal payment buttons] auf der Warenkorbseite. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | Store-Ansicht | Aktivieren oder deaktivieren Sie das Erscheinungsbild der Zahlungsoption Spätere Zahlung , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Apple-Zahlungsoption, bei der Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Option Kreditkartenzahlung und Debitkarte, wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Off] / [!UICONTROL On] |

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_-Optionen der Zahlungsschaltflächen konfigurieren:

1. Um den **[!UICONTROL Layout]** zu ändern, wählen Sie `Vertical` oder `Horizontal` aus.

   >[!NOTE]
   >
   > Wenn der Schaltflächenstil als `Horizontal` konfiguriert ist und Ihr Store so konfiguriert ist, dass mehrere Zahlungsschaltflächen angezeigt werden, werden möglicherweise nur zwei Schaltflächen auf der Produktseite, auf der Checkout-Seite und im Mini-Warenkorb sowie eine Schaltfläche im Warenkorb angezeigt.

1. Um die Tag-Zeile in einem horizontalen Layout zu aktivieren, schalten Sie die &quot;**[!UICONTROL Show tagline]**&quot;-Auswahl um.
1. Um den **[!UICONTROL Color]** zu ändern, wählen Sie die gewünschte Farboption aus.
1. Um den **[!UICONTROL Shape]** zu ändern, wählen Sie `Pill` oder `Rectangle` aus.
1. Um die Auswahl der Schaltflächenhöhe zu aktivieren, schalten Sie den Selektor **[!UICONTROL Responsive button height]** ein.
1. Um den **[!UICONTROL Label]** zu ändern, wählen Sie die gewünschte Beschriftungsoption aus.

   Wenn Sie die Konfigurationsoptionen für Layout, Farbe, Form, Höhe und Beschriftung ändern, wird unten auf der Seite &quot;Einstellungen&quot;eine visuelle Vorschau dieser Konfiguration angezeigt. In der Abbildung unten ist **[!UICONTROL Shape]** auf _Rechteck_ und **[!UICONTROL Label]** auf _PayPal (empfohlen)_ gesetzt.

   ![[!DNL PayPal payment buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

1. Klicken Sie auf **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. [Leeren Sie den Cache](#flush-the-cache).

Sie können den Stil der Zahlungsschaltfläche [in der alten Konfiguration in Admin](configure-admin.md#configure-paypal-smart-buttons) oder hier in [!DNL Payment Services Home] konfigurieren. Weitere Informationen zum Formatieren von PayPal-Zahlungsschaltflächen finden Sie im [Handbuch zum Schaltflächenstil von PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) .

#### Konfigurationsoptionen

| Feld | Umfang | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Store-Ansicht | Definieren Sie den Stil des Layouts für Zahlungsschaltflächen. Optionen: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Store-Ansicht | Aktivieren/deaktivieren Sie die Tagline. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | Store-Ansicht | Definieren Sie die Farbe der Zahlungsschaltflächen. Optionen: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Store-Ansicht | Definieren Sie die Form der Zahlungsschaltflächen. Optionen: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Store-Ansicht | Definiert, ob Zahlungsschaltflächen eine Standardhöhe verwenden. Optionen: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | Store-Ansicht | Definieren Sie die Höhe der Zahlungsschaltflächen. Standardwert: keiner |
| [!UICONTROL Label] | Store-Ansicht | Definieren Sie den Titel, der in den Zahlungsschaltflächen angezeigt wird. Optionen: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Rollen konfigurieren

Um sicherzustellen, dass Admin-Benutzer Bestellungen in Commerce Admin erstellen und verwalten können, aktivieren Sie für Benutzerrollen [!DNL Payment Services] spezifische Ressourcen.

Informationen zum Verwalten von Rollen finden Sie unter [Benutzerrollen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) .

Beim Zuweisen von Ressourcen zur Rolle müssen Sie Folgendes auswählen:

- **Mit[!DNL Payment Services]** bezahlen - Diese Ressource stellt sicher, dass bei der Erstellung einer Bestellung in der Admin-Konsole [!DNL Payment Services] Kreditkarten als Zahlungsmethode verfügbar sind. Wenn Sie die übergeordnete Ressource **Aktionen** auswählen, wird auch diese Ressource ausgewählt.
- **[!DNL Payment Services]** - Diese Ressource enthält die Ressourcen **Dashboard** und **SaaS-Dienst-Proxy** , die ebenfalls ausgewählt werden müssen. Sie stellen sicher, dass [!DNL Payment Services] im Menü _Verkauf_ angezeigt wird.

  ![Zahlungsdienstressourcen](assets/roles-payments.png){width="400" zoomable="yes"}

## Cache leeren

Wenn Sie die Konfiguration in _Einstellungen_ ändern (z. B. durch Umschalten der Schaltflächen &quot;Apple Pay&quot;, &quot;Venmo&quot;oder &quot;PayPal PayLater&quot;), leeren Sie den Cache manuell, damit Ihr Store die neuesten Konfigurationen anzeigt.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Wenn ein beliebiger Cache-Typ in der Tabelle &quot;Cache Management&quot;den Status &quot;`INVALIDATED`&quot;aufweist, zeigt Ihr Store möglicherweise nicht die neueste Konfiguration für dieses Element an. Leeren Sie den Cache, um Ihren Store zu aktualisieren und die neueste Konfiguration anzuzeigen.

Um sicherzustellen, dass Ihr Store die richtige Konfiguration anzeigt, leeren Sie den Cache regelmäßig [.](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management)

## Kartengewölbe

Sie können Funktionen aktivieren, mit denen Ihre Kunden ihre Kreditkarteninformationen in ihrem Mein Konto für zukünftige Käufe verwenden oder speichern können.

Sie können auch die Kartenauswertung in Admin verwenden, um nachfolgende Bestellungen für bestehende Kunden abzuschließen.

Aktivieren oder deaktivieren Sie die Kartenüberprüfung in den Einstellungen für das Feld [Kreditkartenfeld](#credit-card-fields).

Weitere Informationen finden Sie unter [Kreditkartenausnahme](vaulting.md) .

## 3DS

3DS schützt Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften und ermöglicht die Einhaltung der EU-Standards.

Aktivieren oder deaktivieren Sie 3DS in den Einstellungen für [Kreditkartenfelder](#credit-card-fields).

Weitere Informationen finden Sie unter [3DS in Sicherheit](security.md#3ds) .

## Verwenden mehrerer PayPal-Konten

In [!UICONTROL Payment Services] können Sie mehrere PayPal-Konten innerhalb von **ein** Handelskonto auf der Website-Ebene verwenden. Wenn Sie beispielsweise Ihre Geschäfte in mehreren Ländern betreiben (die unterschiedliche [Währungen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency) verwenden) oder Adobe Commerce für einige Teile Ihres Unternehmens, aber nicht für _alle_ verwenden möchten, können Sie Ihr Händlerkonto so einrichten, dass mehrere PayPal-Konten verwendet werden.

Weitere Informationen zur Hierarchie von Websites, Stores und Store-Ansichten finden Sie unter [Site-, Store- und View-Umfang](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) .

Ihr Vertriebsmitarbeiter kann einen neuen [Perimeter](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) für Ihr Händlerkonto erstellen und die zusätzliche Site mit PayPal einbinden, sodass eine der PayPal-Schaltflächen, die Sie konfigurieren, auf Ihrer Site angezeigt wird. Wenden Sie sich an Ihren Vertriebsmitarbeiter, um Unterstützung bei der Verwendung mehrerer PayPal-Konten für Ihre Websites zu erhalten.
