---
title: Verwenden von Adobe Journey Optimizer zum Senden einer E-Mail zum abgebrochenen Warenkorb
description: Erfahren Sie, wie Sie mit Adobe Journey Optimizer eine E-Mail versenden, die den Warenkorb abgebrochen hat.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: 6500aaa373d8e9abf88d1ca45dc2742c83bfeca3
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---

# Verwenden von Adobe Journey Optimizer zum Senden einer E-Mail zum abgebrochenen Warenkorb

Erfahren Sie, wie Sie eine personalisierte E-Mail zur erneuten Interaktion oder Benachrichtigung senden, wenn eine Warenkorb- oder Browsersitzung abgebrochen wurde. In diesem Artikel verwenden Sie Daten von Kunden, die eine Reihe von Produkten und Kategorien angesehen, mit einem Produkt interagiert oder auf einer Seite verbracht haben.

## Welche Daten sollten verwendet werden?

Erstellen Sie einen abgebrochenen Warenkorb, durchsuchen Sie E-Mails oder Benachrichtigungen mithilfe von Daten aus Storefront- und Back-Office-Ereignissen.

| Datentypen | Storefront-Daten (Verhaltensereignisse) | Back Office Data (Server-Side Events) |
|---|---|---|
| **Definition** | Klicks oder Aktionen, die Kunden auf Ihrer Site ausführen. | Informationen zum Lebenszyklus und Details der einzelnen Bestellungen (Vergangenheit und aktuell). |
| **Von Adobe Commerce erfasste Ereignisse** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlaced](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[Auftragsverlauf](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### Was haben andere Kunden erreicht?

Adobe [!DNL Commerce] -Kunden haben durch die Implementierung personalisierter Abbruchkampagnen mit Adobe [!DNL Commerce], Adobe [!DNL Journey Optimizer] und Adobe [!DNL Real-Time CDP] erhebliche geschäftliche Auswirkungen erzielt.

Ein weltweiter Bekleidungshändler mit mehreren Marken erzielte folgende Ergebnisse:

- 1.9x Konversion bei Klick aus neuen Kampagnen
- 57 % Anstieg des Umsatzes, der aus den Abbruch-Journey innerhalb von Kanälen stammt
- 41% Steigerung der Konversionsrate von Rückgewinnungskampagnen
- Mehr als 1000 neue Käufer pro Woche

Ein weltweites Getränkeunternehmen erzielte:

- 36 % E-Mail-Öffnungsraten zur erneuten Interaktion
- 21 % Steigerung der Clickthrough-Raten
- 8,5 % Steigerung der Konversionsrate
- 89 % der rückbeschäftigten Verlassenen konvertieren

## Fangen wir an

Dieser besondere Anwendungsfall konzentriert sich auf das Erstellen einer E-Mail im abgebrochenen Warenkorb mit Daten aus Ihrer [!DNL Commerce] -Instanz und den Versand an Adobe [!DNL Journey Optimizer].

### Was ist Adobe Journey Optimizer?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) hilft Ihnen, das Commerce-Erlebnis für Ihre Kunden zu personalisieren. Sie können beispielsweise Journey Optimizer verwenden, um geplante Marketingkampagnen zu erstellen und bereitzustellen, z. B. wöchentliche Promotions für einen Einzelhandelsgeschäft, oder eine E-Mail zu einem abgebrochenen Warenkorb zu generieren, wenn ein Kunde ein Produkt zu einem Warenkorb hinzugefügt, aber dann den Checkout-Prozess nicht abgeschlossen hat.

In diesem Thema erfahren Sie, wie Sie eine E-Mail mit stehendem Warenkorb erstellen, indem Sie ein `checkout` -Ereignis überwachen, das von Ihrer [!DNL Commerce] -Instanz generiert wurde und auf dieses Ereignis in Journey Optimizer reagiert.

>[!IMPORTANT]
>
>Verwenden Sie zur Veranschaulichung Ihre Sandbox-Umgebung [!DNL Commerce] , damit Sie Ihre Produktionsereignisdaten nicht mit den Ereignisdaten für Storefront und Backoffice verdünnen, die Sie an Experience Platform senden.

### Voraussetzungen

Bevor Sie mit diesen Schritten beginnen, stellen Sie Folgendes sicher:

- Sie können Adobe [!DNL Journey Optimizer] verwenden. Wenn Sie sich nicht sicher sind, wenden Sie sich an Ihren Systemintegrator oder das Entwicklungsteam, das Projekte und Umgebungen verwaltet.
- Sie [haben ](install.md) und [konfiguriert](connect-data.md) die Erweiterung [!DNL Data Connection] in [!DNL Commerce] installiert.
- Sie haben [bestätigt](connect-data.md#confirm-that-event-data-is-collected), dass Ihre [!DNL Commerce] -Ereignisdaten am Experience Platform-Edge eintreffen.

## Schritt 1: Erstellen eines Benutzers in Ihrer Sandbox-Umgebung mit [!DNL Commerce]

Erstellen Sie einen Benutzer in Ihrer Sandbox-Umgebung und bestätigen Sie, dass diese Benutzerkontoinformationen auf dem Experience Platform angezeigt werden. Stellen Sie sicher, dass die angegebene E-Mail gültig ist, da sie später in diesem Abschnitt zum Senden der E-Mail zum abgebrochenen Warenkorb verwendet wird.

1. Melden Sie sich an oder erstellen Sie ein Konto in Ihrer Sandbox-Umgebung.[!DNL Commerce]

   ![Anmelden bei Ihrem Testkonto](assets/sign-in-account.png){width="700" zoomable="yes"}

   Wenn die [!DNL Data Connection] -Erweiterung installiert und konfiguriert ist, werden diese Kontoinformationen als Profil an die Experience Platform gesendet.

1. Vergewissern Sie sich, dass Ihre Benutzerkontoinformationen im Abschnitt **[!UICONTROL Profile]** von Experience Platform angezeigt werden.

   Wechseln Sie in der Adobe Experience Platform zu &quot;**[!UICONTROL Profiles]**&quot;. Klicken Sie im Profil auf **[!UICONTROL Detail]** , um das von Ihnen erstellte Profil anzuzeigen.

   ![Profil bestätigen](assets/check-event-profile.png){width="700" zoomable="yes"}

## Schritt 2: Anzeigen von Ereignissen in Journey Optimizer

In Ihrer [!DNL Commerce] -Sandbox-Umgebung werden Trigger-Ereignisse auf Ihrer Storefront angezeigt, indem Produktseiten angezeigt, Artikel zu einem Warenkorb hinzugefügt und verschiedene andere Aktivitäten ausgeführt werden, die ein Käufer durchführen würde. Bestätigen Sie dann, dass diese Ereignisse an Journey Optimizer weitergeleitet werden.

1. Starten Sie [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Wählen Sie **[!UICONTROL Profiles]** aus.
1. Setzen Sie **[!UICONTROL Identity namespace]** auf `Email`.
1. Stellen Sie den **[!UICONTROL Identity value]** auf Ihre E-Mail-Adresse ein.
1. Wählen Sie Ihr Profil und dann den Tab **[!UICONTROL Events]** aus.

   ![Überprüfen der Ereignisdetails](assets/check-event-details.png){width="700" zoomable="yes"}

   Suchen Sie nach dem `commerce.checkouts` -Ereignis und untersuchen Sie die Ereignis-Payload:

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   Wie Sie sehen können, enthält die vollständige Ereignis-Payload Rich-Event-Daten. Im nächsten Abschnitt konfigurieren Sie Ereignisse in Journey Optimizer, um auf das `commerce.checkouts` -Ereignis zu warten und darauf zu reagieren, das aus Ihrer [!DNL Commerce] -Storefront generiert wurde.

## Schritt 3: Konfigurieren von Ereignissen in Journey Optimizer

Konfigurieren Sie zwei Ereignisse in Journey Optimizer: Ein Ereignis überwacht das `commerce.checkouts` -Ereignis aus Commerce und das andere ein einfaches Timeout-Ereignis, das auf einen bestimmten Zeitraum wartet, bevor eine E-Mail zum Warenkorb ausgelöst wird.

### Listenereignis erstellen

1. Starten Sie [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Klicken Sie im linken Bereich unter dem Abschnitt **[!UICONTROL Administration]** auf **[!UICONTROL Configurations]** .

1. Klicken Sie in der Kachel **[!UICONTROL Events]** auf **[!UICONTROL Manage]**.

   ![Journey Optimizer-Ereigniskonfiguration](assets/ajo-config.png){width="700" zoomable="yes"}

1. Klicken Sie auf der Seite **[!UICONTROL Events]** auf **[!UICONTROL Create Event]**.

1. Richten Sie das Ereignis in der rechten Navigation wie folgt ein:

   1. Setzen Sie den **[!UICONTROL Name]** auf: `firstname_lastname_checkout`.
   1. Setzen Sie **[!UICONTROL Type]** auf **[!UICONTROL Unitary]**.
   1. Setzen Sie **[!UICONTROL Event id typ]e** auf **[!UICONTROL Rule based]**.
   1. Setzen Sie **[!UICONTROL Schema]** auf Ihr [!DNL Commerce] [Schema](update-xdm.md).
   1. Wählen Sie **[!UICONTROL Fields]** aus, um die Seite **[!UICONTROL Fields]** zu öffnen. Wählen Sie dann die für dieses Ereignis nützlichen Felder aus. Wählen Sie beispielsweise alle Felder unter den Feldern **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]** und **[!UICONTROL Web]** aus.
   1. Klicken Sie auf **[!UICONTROL OK]** , um die ausgewählten Felder zu speichern.
   1. Klicken Sie in das Feld **[!UICONTROL Event id condition]** . Erstellen Sie dann eine Bedingung: `eventType` ist gleich `commerce.checkouts` UND `personalEmail.address` ist gleich der E-Mail-Adresse, die Sie beim Erstellen des Profils im vorherigen Abschnitt verwendet haben.

      ![Journey Optimizer-Set-Bedingung](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Klicken Sie auf **[!UICONTROL OK]**.
   1. Klicken Sie auf **[!UICONTROL Save]** , um Ihr Ereignis zu speichern.

### Timeout-Ereignis erstellen

1. Erstellen Sie in Journey Optimizer ein Ereignis wie zuvor.

1. Richten Sie das Ereignis in der rechten Navigation wie folgt ein:

   1. Setzen Sie den **[!UICONTROL Name]** auf: `firstname_lastname_timeout`.
   1. Setzen Sie **[!UICONTROL Type]** auf **[!UICONTROL Unitary]**.
   1. Setzen Sie **[!UICONTROL Event id type]** auf **[!UICONTROL Rule based]**.
   1. Setzen Sie **[!UICONTROL Schema]** auf Ihr [!DNL Commerce] [Schema](update-xdm.md).
   1. Setzen Sie die **[!UICONTROL Schema]**, **[!UICONTROL Fields]** und **[!UICONTROL Event id condition]** auf denselben Wert wie oben.
   1. Klicken Sie auf **[!UICONTROL Save]** , um Ihr Ereignis zu speichern.

Erstellen Sie mit den beiden konfigurierten Ereignissen eine Journey, die eine E-Mail mit dem abgebrochenen Warenkorb sendet.

## Schritt 4: Erstellen einer Checkout-Journey

Erstellen Sie eine Journey, die auf das `commerce.checkouts` -Ereignis wartet und dann nach Ablauf einer bestimmten Zeitdauer eine E-Mail an den abgebrochenen Warenkorb sendet.

1. Wählen Sie in Journey Optimizer unter &quot;**J[!UICONTROL OURNEY MANAGEMENT]**&quot;die Option &quot;**[!UICONTROL Journeys]**&quot;aus.
1. Klicken Sie auf **[!UICONTROL Create Journey]**.
1. Geben Sie den Namen Ihrer Journey an.
1. Klicken Sie auf **[!UICONTROL OK]** , um die Journey zu speichern.
1. Suchen Sie im linken Navigationsbereich unter dem Abschnitt **[!UICONTROL EVENTS]** nach dem zuvor erstellten Checkout-Ereignis: `firstname_lastname_checkout` und ziehen Sie es auf die Arbeitsfläche.

   >[!TIP]
   >
   >Wenn Sie auf das Ereignis doppelklicken, wird es automatisch zur Arbeitsfläche hinzugefügt.

1. Suchen Sie nach dem Timeout-Ereignis und fügen Sie es der Arbeitsfläche hinzu.
1. Doppelklicken Sie auf das Timeout-Ereignis.

   1. Aktivieren Sie im Abschnitt **[!UICONTROL Timeout]** das Kontrollkästchen **[!UICONTROL Define the event time]** .
   1. Geben Sie im Feld **[!UICONTROL Wait for]** den Wert `1` und den Wert `Minute` ein.
   1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Set a timeout path]** .

   Bei dieser Timeout-Konfiguration führt ein Käufer, der innerhalb von 1 Triggern nach diesem Timeout-Zweig einen Checkout durchführt, die Bestellung jedoch nicht abschließt. In einer tatsächlichen Produktionsumgebung würden Sie dies für einen längeren Zeitraum festlegen, z. B. 24 Stunden.

1. Fügen Sie im linken Navigationsbereich unter **[!UICONTROL ACTIONS]** die Aktion **[!UICONTROL Email]** zum Timeout-Zweig hinzu. Ihre Journey sollte wie folgt aussehen:

   ![Journey Optimizer-Arbeitsfläche](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Erstellen einer E-Mail mit stehendem Warenkorb

Erstellen Sie eine E-Mail zum Verlassen des Warenkorbs, die gesendet wird, wenn ein verlassener Warenkorb erkannt wird.

1. Doppelklicken Sie in der oben erstellten Journey auf das Symbol **[!UICONTROL Email]** auf der Arbeitsfläche.

1. Führen Sie die [Schritte](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) im Journey Optimizer-Handbuch aus, um die E-Mail zum abgebrochenen Warenkorb zu erstellen.

Sie verfügen jetzt über eine Journey in Journey Optimizer, die das `commerce.checkouts` -Ereignis aus Ihrem [!DNL Commerce]-Speicher überwacht, und über eine E-Mail, die den Warenkorb verlassen hat und nach Ablauf eines bestimmten Zeitraums gesendet wird. Im nächsten Abschnitt erfahren Sie, wie Sie die Journey testen.

## Schritt 5: Trigger des Checkout-Ereignisses in Echtzeit

In diesem Abschnitt testen Sie das Ereignis in Echtzeit.

1. Aktivieren Sie in Journey Optimizer den Testmodus .

   ![Testmodus aktivieren](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Um diese Journey in Echtzeit zu testen, öffnen Sie eine weitere Browser-Registerkarte und rufen Sie die Website [!DNL Commerce] in Ihrer Sandbox-Umgebung auf.

   1. Fügen Sie Ihrem Warenkorb ein Produkt hinzu.
   1. Gehen Sie zur Checkout-Seite.
   1. Verlassen Sie den Warenkorb von der Checkout-Seite aus, indem Sie zur Hauptseite zurückkehren oder Ihren Tab schließen.

      Die Journey wird jetzt ausgelöst. Öffnen Sie zur Bestätigung die Registerkarte mit Ihrer Journey in Journey Optimizer. Es sollte ein grüner Pfeil angezeigt werden, der den Pfad anzeigt, den Ihr Benutzer durchlaufen hat.

1. Überprüfen Sie Ihren Posteingang auf die E-Mail.
