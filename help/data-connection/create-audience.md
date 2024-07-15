---
title: Erstellen einer Zielgruppe in Real-Time CDP mithilfe von  [!DNL Commerce] Ereignisdaten
description: Erfahren Sie, wie Sie mit [!DNL Commerce] Ereignisdaten eine Zielgruppe in Real-Time CDP erstellen können.
role: Admin, Developer
feature: Personalization, Integration
exl-id: b637f40b-0d35-4c41-a4eb-563085966dc0
source-git-commit: fc6d33dcd069b5351b3e953daa14ca0014ee093d
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Erstellen von Zielgruppen in Real-Time CDP mit [!DNL Commerce] Ereignisdaten

Verwenden Sie Ereignisdaten, die aus Ihrem [!DNL Commerce] -Store erfasst werden, um Zielgruppen in Real-Time CDP zu erstellen. Die erfassten Daten basieren auf dem Browsing-Verhalten, früheren Käufen, Profilattributen, Konvertierungs- oder Abwanderungsneigungen, dem Treuestatus, dem hohen und niedrigen Kundenwert und mehr.

## Welche Daten sollten verwendet werden?

Erstellen Sie Zielgruppen in Real-Time CDP mithilfe von Daten aus Storefront-, Back-Office- und Profilereignissen.

| Datentypen | Storefront-Daten (Verhaltensereignisse) | Back Office Data (Server-Side Events) | Kundenprofil und Segmentdaten |
|---|---|---|---|
| **Definition** | Klicks oder Aktionen, die Kunden auf Ihrer Site ausführen. | Informationen zum Lebenszyklus und Details der einzelnen Bestellungen (Vergangenheit und aktuell). | Wer Ihre Käufer sind und für welche Segmente sie sich qualifizieren. |
| **Von Adobe Commerce erfasste Ereignisse** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[orderPlace](events-backoffice.md#orderplaced)<br>[orderLineItemRefunding](events-backoffice.md#orderlineitemrefunded)<br>[order Cancelled](events-backoffice.md#ordercancelled)<br>[order history](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[Profildatensatz](events-profilerecord.md) |

## Was haben andere Kunden erreicht?

Adobe [!DNL Commerce] -Kunden haben durch die Aktivierung von in Real-Time CDP erstellten Zielgruppen und deren Bereitstellung in ihrer [!DNL Commerce]-Instanz erhebliche geschäftliche Auswirkungen erzielt.

Ein weltweiter Bekleidungshändler mit mehreren Marken erzielte folgende Ergebnisse:

- Eine Quelle der Wahrheit mit 10 Millionen von einheitlichen Kundenprofilen
- Es wurden mehr als 40 einzigartige Zielgruppen von &quot;Kunden mit hohem Intent&quot;erstellt, um kanalübergreifend Interaktionen zu ermöglichen

Ein globales Getränkekonzern:

- 98 Millionen Kundenprofile aus über 100 Ländern

## Fangen wir an

In diesem Artikel lernen Sie Folgendes:

- Erstellen einer Zielgruppe in Real-Time CDP basierend auf den [!DNL Commerce] Daten, die von den Ereignissen erfasst werden
- Aktivieren Sie diese Zielgruppe für Ihren [!DNL Commerce]-Store
- Verwenden Sie die Zielgruppe in [!DNL Commerce], um eine Preisregel für den Warenkorb zu informieren.

>[!IMPORTANT]
>
>Führen Sie die in diesem Artikel beschriebenen Aufgaben mit Ihrer Sandbox-Umgebung [!DNL Commerce] aus. Dadurch wird sichergestellt, dass die an Experience Platform gesendeten Storefront- und Back-Office-Ereignisdaten Ihre Produktionsereignisdaten nicht verwässern.

### Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

- Sie sind für die Verwendung von Real-Time CDP freigeschaltet. Wenn Sie sich nicht sicher sind, wenden Sie sich an Ihren Systemintegrator oder das Entwicklungsteam, das Projekte und Umgebungen verwaltet.
- Sie [haben ](install.md) und [konfiguriert](connect-data.md) die Erweiterung [!DNL Data Connection] in [!DNL Commerce] installiert.
- Sie haben [bestätigt](connect-data.md#confirm-that-event-data-is-collected), dass Ihre [!DNL Commerce] -Ereignisdaten am Experience Platform-Edge eintreffen.

### 1. Erstellen einer Audience

Eine Zielgruppe ist eine Gruppe von Kunden, die ähnliche Verhaltensweisen oder Merkmale aufweisen. In dieser Übung erstellen Sie eine Zielgruppe, die Personen qualifiziert, die an einem bestimmten Produkt aus Ihrem Geschäft interessiert sind.

Um diese Übung zu vereinfachen, verwenden Sie Ereignisdaten aus dem [productPageView](events.md#productpageview) -Ereignis. Dieses Ereignis erfasst Details zum angezeigten Produkt, z. B. Produktname, SKU, Preis usw.

Verwenden Sie diese Ereignisdaten, um anzugeben, dass die Zielgruppe Kontakte enthält, die mindestens ein Ereignis &quot;Produktansichten&quot;haben, bei dem die SKU (Produkt-ID) mit einem bestimmten Produkt auf Ihrer Site übereinstimmt und das Ereignis innerhalb des letzten Tages eintritt. &#x200B;

1. Öffnen Sie Experience Platform und wählen Sie im linken Navigationsmenü die Option **[!UICONTROL Audiences]** aus.

   ![Zielgruppen-Dashboard](assets/audience-left-rail.png)

1. Klicken Sie auf **[!UICONTROL Create Audience]**.

   ![Zielgruppe erstellen](assets/browse-create-audience.png)

   Der Arbeitsbereich **Segmentaufbau** wird angezeigt.

1. Wählen Sie im Arbeitsbereich **Segmentaufbau** die Erstellungsmethode **Regel erstellen** aus.

   ![Build-Regel](assets/build-rule.png)

   Im Arbeitsbereich **Segment Builder** definieren Sie die Regeln und Bedingungen für Ihre Zielgruppe. &#x200B; Diese Regeln und Bedingungen basieren auf Ereignis- und Profildaten aus Ihrem Commerce-Store und definieren die Kriterien, anhand derer bestimmt wird, ob sich ein Benutzer für die Zielgruppe qualifiziert. Sie können beispielsweise eine Regel erstellen, die Benutzer umfasst, die ein bestimmtes Produkt angesehen haben, oder Benutzer, die innerhalb eines bestimmten Zeitraums einen Kauf getätigt haben. Erfahren Sie mehr über [Segmentaufbau](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) und Regeln und Bedingungen.

1. Wählen Sie die Registerkarte [Ereignisse](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) aus.

   ![Registerkarte &quot;Ereignisse&quot;](assets/audience-events-tab.png)

1. Suchen Sie nach dem Ereignistyp &quot;Produktansichten&quot;. Ziehen Sie es dann in den Arbeitsbereich **Segment Builder** .

1. Kehren Sie zur Registerkarte **Ereignisse** zurück und suchen Sie nach &quot;SKU&quot;, dem Datenfeld unter dem Feld `productListItems` . Ziehen Sie es in den Arbeitsbereich **Segment Builder** , um ihn über dem Ereignis **Produktansicht** zu platzieren.

   Im Abschnitt **Ereignisregeln** wird angezeigt, wo Sie das spezifische Produkt angeben können, aus dem Sie Ihre Zielgruppe erstellen möchten.

   ![SKU auswählen](assets/audience-addsku.png)

1. Legen Sie das Zeitintervall auf einen Tag fest, indem Sie auf **Beliebige Zeit** klicken und *Im letzten* mit dem Wert *1* auswählen.

   Beim Erstellen einer Zielgruppe können Sie ein Zeitintervall festlegen, in dem die aktuelle Aktivität erfasst werden soll. Durch das Festlegen eines Zeitintervalls können Sie Benutzer auf der Basis ihrer aktuellen Interaktionen oder Verhaltensweisen innerhalb eines bestimmten Zeitraums ansprechen.

1. Legen Sie im Abschnitt **Zielgruppeneigenschaften** auf der rechten Seite des Arbeitsbereichs die Zielgruppeneigenschaften fest, indem Sie einen Namen, eine Beschreibung und eine Auswertungsmethode für die Zielgruppe angeben.

1. Klicken Sie zum Speichern der Zielgruppe auf **[!UICONTROL Save and Close]**.

   Die Details Ihrer Zielgruppe werden im Dashboard **Zielgruppe** angezeigt.

### 2. Aktivieren Sie die Zielgruppe für das [!DNL Commerce]-Ziel.

Sie stellen eine Zielgruppe in [!DNL Commerce] zur Verfügung, indem Sie sie für das [!DNL Commerce]-Ziel aktivieren.

>[!IMPORTANT]
>
>Wenn Sie [!DNL Commerce] noch nicht als verfügbares Ziel für den Empfang von Daten festgelegt haben, lesen Sie das Thema [Adobe [!DNL Commerce] Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) .

1. Klicken Sie auf der Registerkarte **Details** Ihrer Zielgruppe auf **Für Ziel aktivieren**.

1. Wählen Sie Ihr [!DNL Commerce] Ziel aus. Klicken Sie dann auf **Weiter**.

1. Schließen Sie den Aktivierungsprozess ab, indem Sie auf **[!UICONTROL Finish]** klicken.

## 3. Anzeigen der Audience im Audiences-Dashboard

In [!DNL Commerce] können Sie alle [aktiven](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) Zielgruppen anzeigen, die für Ihre [!DNL Commerce] -Instanz personalisiert werden können, indem Sie das Dashboard **Real-Time CDP-Zielgruppen** verwenden.

Um auf das Dashboard **Real-Time CDP-Zielgruppen** zuzugreifen, wechseln Sie zur Seitenleiste _Admin_ und dann zu **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

Suchen Sie im Dashboard nach der von Ihnen erstellten Audience. Beachten Sie, dass sie nicht in einer Warenkorbpreisregel oder in einem dynamischen Block verwendet wird. Im nächsten Abschnitt verknüpfen Sie die Zielgruppe mit einer Warenkorbpreisregel.

![Real-Time CDP-Zielgruppen-Dashboard](assets/real-time-cdp-dashboard.png)

### 4. Erstellen Sie eine auf der Zielgruppe basierende Warenkorbpreisregel.

In diesem Abschnitt erfahren Sie, wie Sie basierend auf Ihrer neuen Zielgruppe eine Preisregel für den Warenkorb erstellen.

1. Vergewissern Sie sich, dass Ihre neue Zielgruppe im Dashboard **Real-Time CDP-Zielgruppen** angezeigt wird.
1. [Erstellen Sie eine Warenkorbpreisregel](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Legen Sie die Bedingung](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) der Preisregel für den Warenkorb mit Ihrer neuen Zielgruppe fest.
1. [Legen Sie die Aktion ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) fest, die ausgeführt werden soll, wenn das Produkt zum Warenkorb hinzugefügt wird.
1. Konfigurieren Sie weiterhin die Regel für den Warenkorbpreis.
1. Rufen Sie die Kundenansicht Ihrer Sandbox-Instanz auf.
1. Fügen Sie das Produkt, auf dem die Zielgruppe von basiert, zum Warenkorb hinzu. Beachten Sie, dass die Regel zum Warenkorbpreis aktiviert ist.

## Aufschließen

In dieser Übung haben Sie eine Zielgruppe in Real-Time CDP erstellt und für das [!DNL Commerce]-Ziel aktiviert. Anschließend haben Sie in der Admin-Datei [!DNL Commerce] eine auf dieser Zielgruppe basierende Warenkorbpreisregel erstellt und die Regel in Ihrer Sandbox-Umgebung aktiviert.
