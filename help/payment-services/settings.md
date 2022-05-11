---
title: Zahlungsdiensteinstellungen
description: Nach der Installation können Sie [!DNL Payment Services] in der Startseite.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: b30c15ab808be4526424a4a3be19e3d0aedcc662
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# Einstellungen

Sie können [!DNL Payment Services] entsprechend Ihren Anforderungen mithilfe hilfreicher Einstellungen im [!DNL Payment Services] Home.

So konfigurieren Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Diese Konfigurationsoptionen gelten nur für die Umgebung, die im _[!UICONTROL Payment mode]_in den allgemeinen Einstellungen.

Siehe [[!UICONTROL General] Einstellungsabschnitt](#general-settings) für weitere Informationen.

>[!IMPORTANT]
>
> Informationen zur Konfiguration mehrerer Stores oder Legacy finden Sie im Abschnitt [In Admin konfigurieren](configure-admin.md) Thema.

## Zahlungsdienste aktivieren

Sie können [!DNL Payment Services] für Ihre Website und aktivieren Sie entweder Sandbox-Tests oder Live-Zahlungen im [!UICONTROL General] Abschnitt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Startansicht](assets/payment-services-menu-small.png)

1. Klicken **[!UICONTROL Settings]**. Siehe [Einführung in [!DNL Payment Services] Startseite](payments-home.md) für weitere Informationen.

   Die _[!UICONTROL General]_enthält Einstellungen, die zum Aktivieren von [!DNL Payment Services] als Zahlungsmethode.

1. Aktivieren [!DNL Payment Services] als Zahlungsmethode für Ihren Store verwenden, schalten Sie (**[!UICONTROL Enable Payment Services as payment method]**) zu `Yes`.

1. Wenn Sie noch testen [!DNL Payment Services] für Ihren Store festlegen **Zahlungsmodus** nach `Sandbox`. Wenn Sie bereit sind, Live-Zahlungen zu aktivieren, setzen Sie sie auf `Production`.

   >[!WARNING]
   >
   >Ihre _[!UICONTROL Sandbox Merchant ID]_und_[!UICONTROL Production Merchant ID]_ werden automatisch generiert und in den entsprechenden Feldern angezeigt, wenn Sie das Onboarding für die Sandbox und/oder die Produktion abschließen. Entfernen oder ändern Sie diese IDs nicht.

1. Um die Standardeinstellungen für Zahlungsfunktionen und die Anzeige der Storefront zu ändern, legen Sie die zusätzlichen Optionen nach Bedarf fest:

   - [Kreditkartenfelder](#credit-card-fields)
   - [PayPal-Schaltflächen](#paypal-smart-buttons)
   - [Schaltflächenstil](#button-style)

1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### Kreditkartenfelder

Die _[!UICONTROL Credit Card Fields]_Einstellungen bieten eine einfache und sichere Checkout-Option für Kreditkarten- oder Debitkartenzahlmethoden.

Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

1. Um den Namen der Zahlungsmethode zu ändern, die beim Checkout angezeigt wird, bearbeiten Sie den Wert im **[!UICONTROL Checkout title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Um den Debug-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

### PayPal-Schaltflächen

Die [!DNL PayPal Smart Buttons] Zahlungsoptionen bieten einen einfachen, schnellen und sicheren Checkout-Prozess für Ihren Kunden. Siehe [Zahlungsoptionen](payments-options.md#paypal-smart-buttons) für weitere Informationen.

Sie können die Zahlungsoptionen für PayPal-Smart-Schaltflächen aktivieren und konfigurieren:

1. Um den Namen der Zahlungsmethode zu ändern, wie er beim Checkout angezeigt wird, bearbeiten Sie den Wert im **[!UICONTROL Checkout Title]** -Feld.
1. nach [die Zahlungsaktion festlegen](production.md#set-payment-services-as-payment-method), Umschalten **[!UICONTROL Payment action]** nach `Authorize` oder `Authorize and Capture`.
1. Umschalter-Selektoren zum Aktivieren oder Deaktivieren verwenden [!DNL PayPal smart button] Anzeigefunktionen:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. So ändern Sie die [Spätere Nachrichten bezahlen](payments-options.md#pay-later-button), um die **[!UICONTROL Display Pay Later message]** -Option.
1. Um den Debug-Modus zu aktivieren, schalten Sie die **[!UICONTROL Debug Mode]** auswählen.
1. Klicken **[!UICONTROL Save]**.

   Wenn Sie versuchen, von dieser Ansicht weg zu navigieren, ohne Ihre Änderungen zu speichern, wird ein Modal angezeigt, in dem Sie aufgefordert werden, Änderungen zu verwerfen, die Bearbeitung fortzusetzen oder Änderungen zu speichern.

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

#### Schaltflächenstil

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

Sie können [!DNL PayPal Smart Buttons] Stile in der Admin-Konsole oder [!DNL Payment Services Home]. Siehe [Handbuch zum Schaltflächenstil von PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) für weitere Informationen.