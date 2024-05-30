---
title: Verwenden von Adobe Journey Optimizer zum Senden einer E-Mail zum abgebrochenen Warenkorb
description: Erfahren Sie, wie Sie mit Adobe Journey Optimizer eine E-Mail versenden, die den Warenkorb abgebrochen hat.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: ee84525a9146123d80c303e40acdc6baba098cdd
workflow-type: tm+mt
source-wordcount: '1412'
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

### Was kann ich nur mit Adobe Commerce machen?

Adobe verwenden [!DNL Commerce] zur Einrichtung regelbasierter E-Mail-Erinnerungen, die als Warenkorb dienen oder E-Mails zum Abbruch durchsuchen können. Hier erfahren Sie mehr dazu.

### Was kann ich mit Adobe machen? [!DNL Commerce] und Experience Cloud?

- **Adobe [!DNL Commerce] mit Adobe Journey Optimizer** - Verwendung von Adobe [!DNL Commerce] Mit Adobe Journey Optimizer können Sie [!DNL Commerce] -Daten als Trigger für eine kanalübergreifende Abbruch-Journey. Sie können diese Journey anhand von Kundenattributen, von ihnen abgebrochenen Artikeln, anderen Kaufverhaltensweisen und früheren Kaufverhaltensweisen personalisieren.

- **Adobe Commerce, Adobe Journey Optimizer und Adobe Real-Time CDP** - Durch das Hinzufügen von Real-Time CDP können Sie Abbruchkampagnen weiter verfeinern, die auf einheitlichen Kundenprofilen und zentral verwalteten regelbasierten oder KI-gestützten Zielgruppen basieren. Sie können beispielsweise Folgendes erstellen:

   - Zielgruppe &quot;starke Konverter&quot;, deren Abbruchrate niedrig ist
   - Eine Zielgruppe mit hoher Berücksichtigung, die bestimmte Kategorien mehrmals neu besucht hat
   - Eine Zielgruppe mit &quot;hohem Potenzial&quot;, die hohe Ausgaben und Loyalität aufweist, aber in letzter Zeit aufgegeben wurde

### Was haben andere Kunden erreicht?

Adobe [!DNL Commerce] Kunden haben durch die Implementierung personalisierter Abbruchkampagnen mit Adobe erhebliche geschäftliche Auswirkungen erzielt [!DNL Commerce], ADOBE [!DNL Journey Optimizer]und Adobe [!DNL Real-Time CDP].

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

Dieser besondere Anwendungsfall konzentriert sich auf die Erstellung einer E-Mail zum abgebrochenen Warenkorb mit Daten aus Ihrem [!DNL Commerce] -Instanz und Senden an Adobe [!DNL Journey Optimizer].

### Was ist Adobe Journey Optimizer?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) hilft Ihnen bei der Personalisierung des Commerce-Erlebnisses für Ihre Kunden. Sie können beispielsweise Journey Optimizer verwenden, um geplante Marketingkampagnen zu erstellen und bereitzustellen, z. B. wöchentliche Promotions für einen Einzelhandelsgeschäft, oder eine E-Mail zu einem abgebrochenen Warenkorb zu generieren, wenn ein Kunde ein Produkt zu einem Warenkorb hinzugefügt, aber dann den Checkout-Prozess nicht abgeschlossen hat.

In diesem Thema erfahren Sie, wie Sie eine E-Mail mit einem abgebrochenen Warenkorb erstellen, indem Sie eine `checkout` -Ereignis generiert aus Ihrem [!DNL Commerce] -Instanz und Reaktion auf dieses Ereignis in Journey Optimizer.

>[!IMPORTANT]
>
>Verwenden Sie zur Veranschaulichung Ihre [!DNL Commerce] Sandbox-Umgebung verwenden, sodass Sie Ihre Produktionsereignisdaten nicht mit den Storefront- und Back-Office-Ereignisdaten verdünnen, die Sie an Experience Platform senden.

### Voraussetzungen

Bevor Sie mit diesen Schritten beginnen, stellen Sie Folgendes sicher:

- Sie sind für die Verwendung von Adobe bereitgestellt [!DNL Journey Optimizer]. Wenn Sie sich nicht sicher sind, wenden Sie sich an Ihren Systemintegrator oder das Entwicklungsteam, das Projekte und Umgebungen verwaltet.
- You [installiert](install.md) und [konfiguriert](connect-data.md) die [!DNL Data Connection] Erweiterung in [!DNL Commerce].
- You [bestätigt](connect-data.md#confirm-that-event-data-is-collected) dass [!DNL Commerce] Ereignisdaten gelangen am Experience Platform-Edge.

## Schritt 1: Erstellen Sie einen Benutzer in Ihrer [!DNL Commerce] Sandbox-Umgebung

Erstellen Sie einen Benutzer in Ihrer Sandbox-Umgebung und bestätigen Sie, dass diese Benutzerkontoinformationen auf dem Experience Platform angezeigt werden. Stellen Sie sicher, dass die angegebene E-Mail gültig ist, da sie später in diesem Abschnitt zum Senden der E-Mail zum abgebrochenen Warenkorb verwendet wird.

1. Anmelden oder Konto in Ihrer [!DNL Commerce] Sandbox-Umgebung.

   ![Bei Ihrem Testkonto anmelden](assets/sign-in-account.png){width="700" zoomable="yes"}

   Mit dem [!DNL Data Connection] installiert und konfiguriert wurde, werden diese Kontoinformationen als Profil an die Experience Platform gesendet.

1. Vergewissern Sie sich, dass die Informationen zu Ihrem Benutzerkonto in der **[!UICONTROL Profile]** Abschnitt von Experience Platform.

   Navigieren Sie zu **[!UICONTROL Profiles]** in der Adobe Experience Platform. Klicks **[!UICONTROL Detail]** im Profil, um das von Ihnen erstellte Profil anzuzeigen.

   ![Profil bestätigen](assets/check-event-profile.png){width="700" zoomable="yes"}

## Schritt 2: Anzeigen von Ereignissen in Journey Optimizer

In der [!DNL Commerce] Sandbox-Umgebung, Trigger-Ereignisse in Ihrem Storefront durch Anzeigen von Produktseiten, Hinzufügen von Artikeln zu einem Warenkorb und Ausführen verschiedener anderer Aktivitäten, die ein Käufer ausführen würde. Bestätigen Sie dann, dass diese Ereignisse an Journey Optimizer weitergeleitet werden.

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Auswählen **[!UICONTROL Profiles]**.
1. Satz **[!UICONTROL Identity namespace]** nach `Email`.
1. Legen Sie die **[!UICONTROL Identity value]** an Ihre E-Mail-Adresse.
1. Wählen Sie Ihr Profil aus und wählen Sie dann die **[!UICONTROL Events]** Registerkarte.

   ![Überprüfen der Ereignisdetails](assets/check-event-details.png){width="700" zoomable="yes"}

   Suchen Sie nach `commerce.checkouts` -Ereignis und untersuchen Sie die Ereignis-Payload:

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

   Wie Sie sehen können, enthält die vollständige Ereignis-Payload Rich-Event-Daten. Im nächsten Abschnitt konfigurieren Sie Ereignisse in Journey Optimizer, um auf die `commerce.checkouts` -Ereignis generiert aus Ihrem [!DNL Commerce] Storefront.

## Schritt 3: Konfigurieren von Ereignissen in Journey Optimizer

Konfigurieren Sie zwei Ereignisse in Journey Optimizer: ein Ereignis überwacht die `commerce.checkouts` -Ereignis von Commerce aus und das andere ist ein grundlegendes Timeout-Ereignis, das auf einen bestimmten Zeitraum wartet, bevor eine E-Mail zum Warenkorb ausgelöst wird.

### Listenereignis erstellen

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Klicks **[!UICONTROL Configurations]** unter **[!UICONTROL Administration]** im linken Bereich.

1. Im **[!UICONTROL Events]** tile, click **[!UICONTROL Manage]**.

   ![Journey Optimizer-Ereigniskonfiguration](assets/ajo-config.png){width="700" zoomable="yes"}

1. Im **[!UICONTROL Events]** Seite, klicken **[!UICONTROL Create Event]**.

1. Richten Sie das Ereignis in der rechten Navigation wie folgt ein:

   1. Legen Sie die **[!UICONTROL Name]** an: `firstname_lastname_checkout`.
   1. Satz **[!UICONTROL Type]** nach **[!UICONTROL Unitary]**.
   1. Satz **[!UICONTROL Event id typ]e** nach **[!UICONTROL Rule based]**.
   1. Satz **[!UICONTROL Schema]** auf [!DNL Commerce] [schema](update-xdm.md).
   1. Auswählen **[!UICONTROL Fields]** , um die **[!UICONTROL Fields]** Seite. Wählen Sie dann die für dieses Ereignis nützlichen Felder aus. Wählen Sie beispielsweise alle Felder unter dem **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, und **[!UICONTROL Web]**.
   1. Klicks **[!UICONTROL OK]** , um die ausgewählten Felder zu speichern.
   1. Klicken Sie in die **[!UICONTROL Event id condition]** -Feld. Erstellen Sie dann eine Bedingung: `eventType` ist gleich `commerce.checkouts` UND `personalEmail.address` entspricht der E-Mail-Adresse, die Sie beim Erstellen des Profils im vorherigen Abschnitt verwendet haben.

      ![Journey Optimizer Set-Bedingung](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Klicks **[!UICONTROL OK]**.
   1. Klicks **[!UICONTROL Save]** , um das Ereignis zu speichern.

### Timeout-Ereignis erstellen

1. Erstellen Sie in Journey Optimizer ein Ereignis wie zuvor.

1. Richten Sie das Ereignis in der rechten Navigation wie folgt ein:

   1. Legen Sie die **[!UICONTROL Name]** an: `firstname_lastname_timeout`.
   1. Satz **[!UICONTROL Type]** nach **[!UICONTROL Unitary]**.
   1. Satz **[!UICONTROL Event id type]** nach **[!UICONTROL Rule based]**.
   1. Satz **[!UICONTROL Schema]** auf [!DNL Commerce] [schema](update-xdm.md).
   1. Legen Sie die **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, und **[!UICONTROL Event id condition]** auf das gleiche wie oben.
   1. Klicks **[!UICONTROL Save]** , um das Ereignis zu speichern.

Erstellen Sie mit den beiden konfigurierten Ereignissen eine Journey, die eine E-Mail mit dem abgebrochenen Warenkorb sendet.

## Schritt 4: Erstellen einer Checkout-Journey

Erstellen Sie eine Journey, die auf die `commerce.checkouts` -Ereignis und sendet dann eine E-Mail mit einem abgebrochenen Warenkorb, nachdem ein bestimmter Zeitraum verstrichen ist.

1. Wählen Sie in Journey Optimizer **[!UICONTROL Journeys]** under **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Klicks **[!UICONTROL Create Journey]**.
1. Geben Sie den Namen Ihrer Journey an.
1. Klicks **[!UICONTROL OK]** , um die Journey zu speichern.
1. Im linken Navigationsbereich unter **[!UICONTROL EVENTS]** nach dem zuvor erstellten Checkout-Ereignis suchen: `firstname_lastname_checkout` und ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche.

   >[!TIP]
   >
   >Wenn Sie auf das Ereignis doppelklicken, wird es automatisch zur Arbeitsfläche hinzugefügt.

1. Suchen Sie nach dem Timeout-Ereignis und fügen Sie es der Arbeitsfläche hinzu.
1. Doppelklicken Sie auf das Timeout-Ereignis.

   1. Im **[!UICONTROL Timeout]** auswählen, wählen Sie die **[!UICONTROL Define the event time]** aktivieren.
   1. Im **[!UICONTROL Wait for]** Feldeingabe `1` und `Minute`.
   1. Wählen Sie die **[!UICONTROL Set a timeout path]** aktivieren.

   Bei dieser Timeout-Konfiguration führt ein Käufer, der innerhalb von 1 Triggern nach diesem Timeout-Zweig einen Checkout durchführt, die Bestellung jedoch nicht abschließt. In einer tatsächlichen Produktionsumgebung würden Sie dies für einen längeren Zeitraum festlegen, z. B. 24 Stunden.

1. Im linken Navigationsbereich unter **[!UICONTROL ACTIONS]**, fügen Sie die **[!UICONTROL Email]** -Aktion auf die Zeitüberschreitungsverzweigung. Ihre Journey sollte wie folgt aussehen:

   ![Journey Optimizer-Arbeitsfläche](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Erstellen einer E-Mail mit stehendem Warenkorb

Erstellen Sie eine E-Mail zum Verlassen des Warenkorbs, die gesendet wird, wenn ein verlassener Warenkorb erkannt wird.

1. Doppelklicken Sie in der oben erstellten Journey auf die **[!UICONTROL Email]** auf der Arbeitsfläche.

1. Befolgen Sie die [Schritte](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) im Journey Optimizer-Handbuch, um die E-Mail zum abgebrochenen Warenkorb zu erstellen.

Sie verfügen jetzt über eine Journey in Journey Optimizer, die auf die `commerce.checkouts` -Ereignis aus [!DNL Commerce] speichern und eine E-Mail mit stehendem Warenkorb erstellen, die nach Ablauf eines bestimmten Zeitraums gesendet wird. Im nächsten Abschnitt erfahren Sie, wie Sie die Journey testen.

## Schritt 5: Trigger des Checkout-Ereignisses in Echtzeit

In diesem Abschnitt testen Sie das Ereignis in Echtzeit.

1. Aktivieren Sie in Journey Optimizer den Testmodus .

   ![Testmodus aktivieren](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Um dieses Journey in Echtzeit zu testen, öffnen Sie eine weitere Browser-Registerkarte und rufen Sie die [!DNL Commerce] Website in Ihrer Sandbox-Umgebung.

   1. Fügen Sie Ihrem Warenkorb ein Produkt hinzu.
   1. Gehen Sie zur Checkout-Seite.
   1. Verlassen Sie den Warenkorb von der Checkout-Seite aus, indem Sie zur Hauptseite zurückkehren oder Ihren Tab schließen.

      Die Journey wird jetzt ausgelöst. Öffnen Sie zur Bestätigung die Registerkarte mit Ihrer Journey in Journey Optimizer. Es sollte ein grüner Pfeil angezeigt werden, der den Pfad anzeigt, den Ihr Benutzer durchlaufen hat.

1. Überprüfen Sie Ihren Posteingang auf die E-Mail.
