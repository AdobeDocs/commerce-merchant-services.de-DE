---
title: Zahlungsdiensteinstellungen
description: Nach der Installation können Sie [!DNL Payment Services] in der Startseite.
role: Admin, User
level: Intermediate
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Konfigurieren in der Startansicht

Sie können [!DNL Payment Services] auf Ihre Bedürfnisse mit hilfreichen Einstellungen in der Startansicht.

So konfigurieren Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im _[!UICONTROL Payment mode]_in den allgemeinen Einstellungen.

Siehe [[!UICONTROL General] Einstellungsabschnitt](#general-settings) für weitere Informationen.

>[!IMPORTANT]
>
> Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie im Abschnitt [In Admin konfigurieren](configure-admin.md) Thema.

## Zahlungsdienste konfigurieren

Sie können [!DNL Payment Services] für Ihre Website und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen im [!UICONTROL General] Einstellungsbereich.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Startansicht](assets/payment-services-menu-small.png)

1. Klicken Sie in der Startansicht auf **[!UICONTROL Settings]**. Siehe [Startseite](payments-home.md) für weitere Informationen.

   Die _[!UICONTROL General]_enthält die Konfigurationsoptionen, die zum Festlegen von [!DNL Payment Services] als Zahlungsmethode.

1. Für die Umschaltoption oben (**[!UICONTROL Enable Payment Services as payment method]**), setzen Sie sie auf `Yes` aktivieren [!DNL Payment Services] für Ihre Website.

1. Für **Zahlungsmodus**, setzen Sie sie auf `Sandbox` wenn Sie noch testen [!DNL Payment Services] für Ihr Geschäft oder `Production` wenn Sie bereit sind, Live-Zahlungen zu aktivieren.

   >[!WARNING]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abgeschlossen haben. Entfernen oder ändern Sie diese IDs nicht.

1. Um die Standardeinstellungen für Zahlungsfunktionen und die Anzeige der Storefront zu ändern, legen Sie die zusätzlichen Optionen nach Bedarf fest:

   - [Kreditkartenfelder](#credit-card-fields)
   - [PayPal-Schaltflächen](#paypal-smart-buttons)
   - [Schaltflächenstil](#button-style)

1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

1. Für **[!UICONTROL Checkout title]**, geben Sie bei Bedarf Text ein, um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), set **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Für **[!UICONTROL Debug Mode]**, um den Selektor zu aktivieren, um den Debug-Modus zu aktivieren.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### PayPal-Schaltflächen

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Sie können die Zahlungsoptionen der PayPal-Smart-Schaltflächen auf der Startseite aktivieren:

1. Um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird, bearbeiten Sie den Wert im **[!UICONTROL Checkout Title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), set **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Umschalter-Selektoren zum Aktivieren oder Deaktivieren verwenden [!DNL PayPal smart button] Anzeigefunktionen:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** , um die Option zum Anzeigen der Schaltfläche beim Checkout zu aktivieren.

1. So ändern Sie die [Spätere Nachrichten bezahlen](payments-options.md#pay-later-button) (falls gewünscht) können Sie die **[!UICONTROL Display Pay Later message]** -Option.
1. Um den Debug-Modus zu aktivieren, klicken Sie auf **[!UICONTROL Debug Mode]**,
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der PayPal-Smart-Schaltflächen auf der Startseite:

1. So ändern Sie die **[!UICONTROL Layout]** auswählen `Vertical` oder `Horizontal`.
1. Um Tags in einem horizontalen Layout zu aktivieren, klicken Sie auf **[!UICONTROL Show tagline]**.
1. So ändern Sie die **[!UICONTROL Color]** wählen Sie die gewünschte Farboption aus.
1. So ändern Sie die **[!UICONTROL Shape]** auswählen `Pill` oder `Rect`.
1. Um die Auswahl der Schaltflächenhöhe zu aktivieren, klicken Sie auf **[!UICONTROL Responsive button height]**.
1. So ändern Sie die **[!UICONTROL Label]** wählen Sie die gewünschte Beschriftungsoption aus.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können [!DNL PayPal Smart Buttons] Formatierung in der Admin- oder Startseite. Siehe [Handbuch zum Schaltflächenstil von PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) für weitere Informationen.
