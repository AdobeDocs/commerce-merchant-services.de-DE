---
title: Zahlungsdiensteinstellungen
description: Nach der Installation können Sie [!DNL Payment Services] in der Startseite.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 89fa175b70a2b4b37d5999dedc56a7e41ae28b7d
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Einstellungen

Sie können [!DNL Payment Services] entsprechend Ihren Anforderungen mithilfe hilfreicher Einstellungen im [!DNL Payment Services] Home.

So konfigurieren Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im _[!UICONTROL Payment mode]_-Feld in_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie im Abschnitt [In Admin konfigurieren](configure-admin.md) Thema.

## Zahlungsdienste aktivieren

Sie können [!DNL Payment Services] für Ihre Website und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen im [!UICONTROL General] Abschnitt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Startansicht](assets/payment-services-menu-small.png)

1. Klicken **[!UICONTROL Settings]**. Siehe [Einführung in [!DNL Payment Services] Startseite](payments-home.md) für weitere Informationen.

   Die _[!UICONTROL General]_enthält Einstellungen, die zum Aktivieren von [!DNL Payment Services] als Zahlungsmethode.

1. Aktivieren [!DNL Payment Services] als Zahlungsmethode für Ihren Speicher in der _[!UICONTROL General]_-Abschnitt ein-/ausblenden (**[!UICONTROL Enable Payment Services as payment method]**) zu `Yes`.

1. Wenn Sie noch testen [!DNL Payment Services] für Ihren Store festlegen **Zahlungsmodus** nach `Sandbox`. Wenn Sie bereit sind, Live-Zahlungen zu aktivieren, setzen Sie sie auf `Production`.

   >[!NOTE]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abschließen.

1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können jetzt die Standardeinstellungen für [Zahlungsoptionen](#configure-payment-options) Funktionen und Anzeige der Storefront.

### Allgemeine Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Payment Services] für Ihre Website. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | Store-Ansicht | Legen Sie die -Methode oder -Umgebung für Ihren Store fest. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | Store-Ansicht | Ihre Sandbox-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |
| [!UICONTROL Production Merchant ID] | Store-Ansicht | Ihre Produktions-Händler-ID, die beim Sandbox-Onboarding automatisch generiert wird. |

## Zahlungsoptionen konfigurieren

Nachdem Sie Zahlungsdienste für Ihre Website aktiviert haben, können Sie die Standardeinstellungen für Zahlungsfunktionen und die Anzeige der Storefront ändern.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_Einstellungen bieten eine einfache und sichere Checkout-Option für Kreditkarten- oder Debitkartenzahlmethoden.

Siehe [Zahlungsoptionen](payments-options.md#credit-card-fields) für weitere Informationen.

1. Wählen Sie die Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie eine Zahlungsmethode aktivieren möchten.
1. Um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird, bearbeiten Sie den Wert im **[!UICONTROL Checkout title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Um den Debug-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |

### Zahlungsschaltflächen

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Sie können die Zahlungsoptionen für PayPal-Smart-Schaltflächen aktivieren und konfigurieren:

1. Wählen Sie die Store-Ansicht im **[!UICONTROL Scope]** Dropdown-Menü, für das Sie eine Zahlungsmethode aktivieren möchten.
1. Um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird, bearbeiten Sie den Wert im **[!UICONTROL Checkout Title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Umschalter-Selektoren zum Aktivieren oder Deaktivieren verwenden [!DNL PayPal smart button] Anzeigefunktionen:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple Pay ist standardmäßig für den Sandbox-Modus aktiviert, Sie können aber auch [muss über ein Apple-Entwicklerkonto verfügen](test-validate.md#test-in-sandbox-environment) (mit gefälschten Kreditkarten- und Rechnungsinformationen), um sie zu testen. Wenn Sie bereit sind, Apple Pay im Produktionsmodus zu verwenden, nachdem Sie alle [Tests und Validierung](test-validate.md), kontaktieren Sie Sales , um es für Ihre Live-Stores zu aktivieren.

1. Um den Debug-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text hinzu, der beim Checkout als Titel für diese Zahlungsoption angezeigt werden soll. Optionen: Textfeld |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Produktdetailseite. Optionen: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] in der Vorschau des Mini-Warenkorbs. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | Store-Ansicht | Aktivieren oder Deaktivieren [!DNL PayPal Smart Buttons] auf der Warenkorbseite. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | Store-Ansicht | Aktivieren oder deaktivieren Sie das Erscheinungsbild der Zahlungsoption Spätere Zahlung , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | website | Aktivieren oder deaktivieren Sie die &quot;Später bezahlen&quot;-Benachrichtigung im Warenkorb, auf der Produktseite, im Mini-Warenkorb und während des Checkout-Verfahrens. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Zahlungsoption Venmo , wenn Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | Store-Ansicht | Aktivieren oder deaktivieren Sie die Apple-Zahlungsoption, bei der Zahlungsschaltflächen angezeigt werden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der PayPal-Smart-Schaltflächen:

1. So ändern Sie die **[!UICONTROL Layout]** auswählen `Vertical` oder `Horizontal`.

   >[!NOTE]
   >
   > Wenn der Schaltflächenstil als `Horizontal` und Ihr Store so konfiguriert ist, dass mehrere PayPal-Smart-Schaltflächen angezeigt werden, werden möglicherweise nur zwei Schaltflächen auf der Produktseite, auf der Checkout-Seite und im Mini-Warenkorb sowie eine Schaltfläche im Warenkorb angezeigt.

1. Um die Tagline in einem horizontalen Layout zu aktivieren, können Sie die **[!UICONTROL Show tagline]** auswählen.
1. So ändern Sie die **[!UICONTROL Color]** wählen Sie die gewünschte Farboption aus.
1. So ändern Sie die **[!UICONTROL Shape]** auswählen `Pill` oder `Rect`.
1. Um die Auswahl der Schaltflächenhöhe zu aktivieren, schalten Sie die **[!UICONTROL Responsive button height]** auswählen.
1. So ändern Sie die **[!UICONTROL Label]** wählen Sie die gewünschte Beschriftungsoption aus.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können [!DNL PayPal Smart Buttons] Stil [in der Legacy-Konfiguration in der Admin-Konsole](configure-admin.md#configure-paypal-smart-buttons) oder hier [!DNL Payment Services Home]. Siehe [Handbuch zum Schaltflächenstil von PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) für weitere Informationen zu den Optionen.

#### Konfigurationsoptionen

| Feld | Anwendungsbereich | Beschreibung |
|--- |--- |--- |
| [!UICONTROL Layout] | Store-Ansicht | Definieren Sie den Stil des Layouts für Zahlungsschaltflächen. Optionen: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Store-Ansicht | Aktivieren/deaktivieren Sie die Tagline. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Store-Ansicht | Definieren Sie die Farbe der Zahlungsschaltflächen. Optionen: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Store-Ansicht | Definieren Sie die Form der Zahlungsschaltflächen. Optionen: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Store-Ansicht | Definiert, ob Zahlungsschaltflächen eine Standardhöhe verwenden. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Store-Ansicht | Definieren Sie die Höhe der Zahlungsschaltflächen. Standardwert: Keine |
| [!UICONTROL Label] | Store-Ansicht | Definieren Sie den Titel, der in den Zahlungsschaltflächen angezeigt wird. Optionen: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
