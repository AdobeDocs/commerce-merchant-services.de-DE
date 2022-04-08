---
title: Konfigurieren im Dashboard
description: Nach der Installation können Sie [!DNL Payment Services] im Dashboard.
role: Admin, User
level: Intermediate
exl-id: 015c5c8c-8184-45c1-932a-f4365ddf5a30
source-git-commit: 695666596ed11026983215c745c7b33ee4b0bfdc
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# Konfigurieren im Dashboard

Sie können [!DNL Payment Services] nach Ihren Bedürfnissen mit hilfreichen Konfigurationsoptionen im Dashboard.

Wenn Sie auf [!UICONTROL Settings] im Dashboard können Sie schnell [!DNL Payment Services] für Adobe Commerce und Magento Open Source. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im [!UICONTROL Payment mode] in den allgemeinen Einstellungen.

Siehe [[!UICONTROL General] Einstellungsabschnitt](#general-settings) für weitere Informationen.

>[!IMPORTANT]
>
> Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie im Abschnitt [In Admin konfigurieren](configure-admin.md) Thema.

## Zahlungsdienste konfigurieren

Sie können [!DNL Payment Services] für Ihre Website und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen im [!UICONTROL General] Einstellungsbereich.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Dashboard-Ansicht](assets/payment-services-menu-small.png)

1. Klicken Sie im Dashboard auf **[!UICONTROL Settings]** oben rechts auf der Seite.

   Die _[!UICONTROL General]_enthält die Konfigurationsoptionen, die zum Festlegen von [!DNL Payment Services] als Zahlungsmethode.

1. Für die Umschaltoption oben (**[!UICONTROL Enable Payment Services as payment method]**), setzen Sie sie auf `Yes` aktivieren [!DNL Payment Services] für Ihre Website.

1. Für **Zahlungsmodus**, setzen Sie sie auf `Sandbox` wenn Sie noch testen [!DNL Payment Services] für Ihr Geschäft oder `Production` wenn Sie bereit sind, Live-Zahlungen zu aktivieren.

   >[!WARNING]
   >
   >Ihre [!UICONTROL Sandbox Merchant ID] und [!UICONTROL Production Merchant ID] werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abgeschlossen haben. Entfernen oder ändern Sie diese IDs nicht.

1. Um die Standardeinstellungen für Zahlungsfunktionen und die Anzeige der Storefront zu ändern, legen Sie die zusätzlichen Optionen nach Bedarf fest:

   - [Kreditkartenfelder](#credit-card-fields)
   - [PayPal-Schaltflächen](#paypal-smart-buttons)
   - [Schaltflächenstil](#button-style)

1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Kreditkartenfelder

Die [!UICONTROL Credit Card Fields] Zahlungsoptionen bieten einen einfachen und sicheren Checkout für Kreditkarten- oder Debitkarten-Zahlungsmethoden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

1. Für **[!UICONTROL Checkout title]**, geben Sie bei Bedarf Text ein, um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), set **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Für **[!UICONTROL Debug Mode]**, um den Selektor zu aktivieren, um den Debug-Modus zu aktivieren.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### PayPal-Schaltflächen

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Sie können die Zahlungsoptionen für PayPal-Smart-Schaltflächen im Dashboard aktivieren:

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
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Schaltflächenstil

Sie können auch die _[!UICONTROL Button style]_Optionen der PayPal-Smart-Schaltflächen im Dashboard:

1. So ändern Sie die **[!UICONTROL Layout]** auswählen `Vertical` oder `Horizontal`.
1. Um Tags in einem horizontalen Layout zu aktivieren, klicken Sie auf **[!UICONTROL Show tagline]**.
1. So ändern Sie die **[!UICONTROL Color]** wählen Sie die gewünschte Farboption aus.
1. So ändern Sie die **[!UICONTROL Shape]** auswählen `Pill` oder `Rect`.
1. Um die Auswahl der Schaltflächenhöhe zu aktivieren, klicken Sie auf **[!UICONTROL Responsive button height]**.
1. So ändern Sie die **[!UICONTROL Label]** wählen Sie die gewünschte Beschriftungsoption aus.
1. Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Save]** oben rechts auf der Seite.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

Sie können [!DNL PayPal Smart Buttons] Formatierung im Admin oder Dashboard. Siehe [Konfiguration [!DNL PayPal Smart Buttons style]](configure-admin.md#configure-paypal-smart-button-styling) für weitere Informationen.
