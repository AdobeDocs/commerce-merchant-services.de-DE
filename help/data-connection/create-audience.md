---
title: Erstellen einer Zielgruppe in Real-Time CDP mithilfe von [!DNL Commerce] Ereignisdaten
description: Verwendung von [!DNL Commerce] Ereignisdaten zum Erstellen einer Zielgruppe in Real-Time CDP
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: fc2a7ba6891cf8affdec13b0400d75350284faa2
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Erstellen von Zielgruppen in Real-Time CDP mithilfe von [!DNL Commerce] Ereignisdaten

Verwenden Sie Ereignisdaten, die aus Ihrem [!DNL Commerce] speichern, um Zielgruppen in Real-Time CDP zu erstellen. Die erfassten Daten basieren auf dem Browsing-Verhalten, früheren Käufen, Profilattributen, Konvertierungs- oder Abwanderungsneigungen, dem Treuestatus, dem hohen und niedrigen Kundenwert und mehr.

## Welche Daten sollten verwendet werden?

Erstellen Sie Zielgruppen in Real-Time CDP mithilfe von Daten aus Storefront-, Back-Office- und Profilereignissen.

| Datentypen | Storefront-Daten (Verhaltensereignisse) | Back Office Data (Server-Side Events) | Kundenprofil und Segmentdaten |
|---|---|---|---|
| **Definition** | Klicks oder Aktionen, die Kunden auf Ihrer Site ausführen. | Informationen zum Lebenszyklus und Details der einzelnen Bestellungen (Vergangenheit und aktuell). | Wer Ihre Käufer sind und für welche Segmente sie sich qualifizieren. |
| **Von Adobe Commerce erfasste Ereignisse** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[orderplace](events-backoffice.md#orderplaced)<br>[orderLineItemRefund](events-backoffice.md#orderlineitemrefunded)<br>[Bestellung abgebrochen](events-backoffice.md#ordercancelled)<br>[Bestellverlauf](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[Profildatensatz](events-profilerecord.md) |

## Was haben andere Kunden erreicht?

Adobe [!DNL Commerce] Kunden haben durch die Aktivierung von in Real-Time CDP erstellten Zielgruppen und deren Bereitstellung für ihre [!DNL Commerce] -Instanz.

Ein weltweiter Bekleidungshändler mit mehreren Marken erzielte folgende Ergebnisse:

- Eine Quelle der Wahrheit mit 10 Millionen von einheitlichen Kundenprofilen
- Es wurden mehr als 40 einzigartige Zielgruppen von &quot;Kunden mit hohem Intent&quot;erstellt, um kanalübergreifend Interaktionen zu ermöglichen

Ein globales Getränkekonzern:

- 98 Millionen Kundenprofile aus über 100 Ländern

## Fangen wir an

In diesem Artikel lernen Sie Folgendes:

- Erstellen einer Zielgruppe in Real-Time CDP basierend auf der [!DNL Commerce] Daten, die von den Ereignissen erfasst werden
- Aktivieren Sie diese Zielgruppe für Ihre [!DNL Commerce] store
- Verwenden Sie die Zielgruppe in [!DNL Commerce] zur Information über eine Preisregel im Warenkorb

>[!IMPORTANT]
>
>Führen Sie die in diesem Artikel beschriebenen Aufgaben mithilfe Ihrer [!DNL Commerce] Sandbox-Umgebung. Dadurch wird sichergestellt, dass die an Experience Platform gesendeten Storefront- und Back-Office-Ereignisdaten Ihre Produktionsereignisdaten nicht verwässern.

### Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

- Sie sind für die Verwendung von Real-Time CDP freigeschaltet. Wenn Sie sich nicht sicher sind, wenden Sie sich an Ihren Systemintegrator oder das Entwicklungsteam, das Projekte und Umgebungen verwaltet.
- You [installiert](install.md) und [konfiguriert](connect-data.md) die [!DNL Data Connection] Erweiterung in [!DNL Commerce].
- You [bestätigt](connect-data.md#confirm-that-event-data-is-collected) dass [!DNL Commerce] Ereignisdaten gelangen am Experience Platform-Edge.

### 1. Erstellen einer Audience

Eine Zielgruppe ist eine Gruppe von Kunden, die ähnliche Verhaltensweisen oder Merkmale aufweisen. In dieser Übung erstellen Sie eine Zielgruppe, die Personen qualifiziert, die an einem bestimmten Produkt aus Ihrem Geschäft interessiert sind.

Um diese Übung zu vereinfachen, verwenden Sie Ereignisdaten aus dem [productPageView](events.md#productpageview) -Ereignis. Dieses Ereignis erfasst Details zum angezeigten Produkt, z. B. Produktname, SKU, Preis usw.

Verwenden Sie diese Ereignisdaten, um anzugeben, dass die Zielgruppe Kontakte enthält, die mindestens ein Ereignis &quot;Produktansichten&quot;haben, bei dem die SKU (Produkt-ID) mit einem bestimmten Produkt auf Ihrer Site übereinstimmt und das Ereignis innerhalb des letzten Tages eintritt. &#x200B;

1. Öffnen Sie Experience Platform und wählen Sie **[!UICONTROL Audiences]** aus dem linken Navigationsmenü.

   ![Zielgruppen-Dashboard](assets/audience-left-rail.png)

1. Klicks **[!UICONTROL Create Audience]**.

   ![Zielgruppe erstellen](assets/browse-create-audience.png)

   Die **Segment Builder** Arbeitsbereich angezeigt.

1. Im **Segment Builder** Arbeitsbereich, wählen Sie die **Regel erstellen** Erstellungsmethode.

   ![Build-Regel](assets/build-rule.png)

   Die **Segment Builder** In Workspace definieren Sie die Regeln und Bedingungen für Ihre Audience. &#x200B; Diese Regeln und Bedingungen basieren auf Ereignis- und Profildaten aus Ihrem Commerce-Store und definieren die Kriterien, anhand derer bestimmt wird, ob sich ein Benutzer für die Zielgruppe qualifiziert. Sie können beispielsweise eine Regel erstellen, die Benutzer umfasst, die ein bestimmtes Produkt angesehen haben, oder Benutzer, die innerhalb eines bestimmten Zeitraums einen Kauf getätigt haben. Weitere Informationen [Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) und Regeln und Bedingungen.

1. Wählen Sie die [Veranstaltungen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) Registerkarte.

   ![Registerkarte &quot;Ereignisse&quot;](assets/audience-events-tab.png)

1. Suchen Sie nach dem Ereignistyp &quot;Produktansichten&quot;. Ziehen Sie es dann per Drag-and-Drop in den **Segment Builder** Arbeitsbereich.

1. Kehren Sie zu **Veranstaltungen** und suchen Sie nach &quot;SKU&quot;, dem Datenfeld unter dem `productListItems` -Feld. Ziehen Sie es per Drag-and-Drop in den **Segment Builder** Arbeitsbereich über dem **Produktansicht** -Ereignis.

   Die **Ereignisregeln** zeigt an, wo Sie das spezifische Produkt angeben können, aus dem Sie Ihre Zielgruppe erstellen möchten.

   ![SKU auswählen](assets/audience-addsku.png)

1. Legen Sie das Zeitintervall auf einen Tag fest, indem Sie auf **Beliebige Zeit** und auswählen *Letzten* mit dem Wert *1*.

   Beim Erstellen einer Zielgruppe können Sie ein Zeitintervall festlegen, in dem die aktuelle Aktivität erfasst werden soll. Durch das Festlegen eines Zeitintervalls können Sie Benutzer auf der Basis ihrer aktuellen Interaktionen oder Verhaltensweisen innerhalb eines bestimmten Zeitraums ansprechen.

1. Im **Zielgruppeneigenschaften** Legen Sie auf der rechten Seite des Arbeitsbereichs die Zielgruppeneigenschaften fest, indem Sie einen Namen, eine Beschreibung und eine Auswertungsmethode für die Zielgruppe angeben.

1. Klicken Sie zum Speichern der Audience auf **[!UICONTROL Save and Close]**.

   Die Details Ihrer Audience werden auf der Seite **Zielgruppe** Dashboard.

### 2. Aktivieren Sie die Audience für die [!DNL Commerce] Ziel

Sie stellen eine Zielgruppe in [!DNL Commerce] durch Aktivierung für [!DNL Commerce] Ziel.

>[!IMPORTANT]
>
>Wenn Sie nicht bereits [!DNL Commerce] als verfügbares Ziel für den Empfang von Daten, siehe [Adobe [!DNL Commerce] Verbindung](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) Thema.

1. Im **Details** Registerkarte Ihrer Audience klicken Sie auf **Auf Ziel aktivieren**.

1. Wählen Sie [!DNL Commerce] Ziel. Klicken Sie anschließend auf **Nächste**.

1. Schließen Sie den Aktivierungsprozess durch Klicken auf **[!UICONTROL Finish]**.

## 3. Anzeigen der Audience im Audiences-Dashboard

In [!DNL Commerce], können Sie alle [active](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) Zielgruppen, die für Ihre [!DNL Commerce] -Instanz mit der **Real-Time CDP-Zielgruppen** Dashboard.

So greifen Sie auf die **Real-Time CDP-Zielgruppen** Dashboard, navigieren Sie zum _Admin_ Seitenleiste, dann zu **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

Suchen Sie im Dashboard nach der von Ihnen erstellten Audience. Beachten Sie, dass sie nicht in einer Warenkorbpreisregel oder in einem dynamischen Block verwendet wird. Im nächsten Abschnitt verknüpfen Sie die Zielgruppe mit einer Warenkorbpreisregel.

![Dashboard für Real-Time CDP-Zielgruppen](assets/real-time-cdp-dashboard.png)

### 4. Erstellen Sie eine auf der Zielgruppe basierende Warenkorbpreisregel.

In diesem Abschnitt erfahren Sie, wie Sie basierend auf Ihrer neuen Zielgruppe eine Preisregel für den Warenkorb erstellen.

1. Vergewissern Sie sich, dass Ihre neue Zielgruppe im **Real-Time CDP-Zielgruppen** Dashboard.
1. [Erstellen einer Preisregel für den Warenkorb](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Bedingung festlegen](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) der Preisregel des Warenkorbs unter Verwendung Ihrer neuen Zielgruppe.
1. [Aktion festlegen](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) die Sie beim Hinzufügen des Produkts zum Warenkorb erhalten möchten.
1. Konfigurieren Sie weiterhin die Regel für den Warenkorbpreis.
1. Rufen Sie die Kundenansicht Ihrer Sandbox-Instanz auf.
1. Fügen Sie das Produkt, auf dem die Zielgruppe von basiert, zum Warenkorb hinzu. Beachten Sie, dass die Regel zum Warenkorbpreis aktiviert ist.

## Aufschließen

In dieser Übung haben Sie eine Zielgruppe in Real-Time CDP erstellt und für die [!DNL Commerce] Ziel. Dann in der [!DNL Commerce] Admin, haben Sie eine auf dieser Zielgruppe basierende Warenkorbpreisregel erstellt und die Regel in Ihrer Sandbox-Umgebung aktiviert.
