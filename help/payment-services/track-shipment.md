---
title: Verfolgen Ihrer Sendungen in [!DNL Payment Services]
description: Passen Sie die im PayPal-Merchant-Dashboard angezeigten Sendungen und Tracking-Informationen an. [!DNL Payment Services]
feature: Payments
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Versandverfolgung in [!DNL Payment Services]

[!DNL Payment Services] ermöglicht es Händlern, die Tracking-Informationen für eine Sendung im PayPal Merchant Dashboard anzuzeigen.

Weitere Informationen zum Versandraster für Adobe Commerce finden Sie unter [Sendungen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/shipments){target=_blank} .

## Funktionsweise der Versandverfolgung

Diese Funktion hängt davon ab, ob die Bestellung in Rechnung gestellt wurde, da PayPal eine `capture_id` erhalten muss, um die Tracking-Informationen zu verarbeiten. Wenn ein Händler seine Produkte vor der Erfassung aussendet, werden die Tracking-Informationen nicht an PayPal gesendet.

>[!NOTE]
>
> Es wird empfohlen, eine Sendung pro Trackingnummer zu erstellen und die richtigen Artikel mit der Sendung zu verknüpfen.

## Trackingnummer hinzufügen

Die folgenden Anweisungen führen Sie durch den Prozess zum Erstellen einer Sendung in Adobe Commerce mit [!DNL Payment Services]:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.

1. Klicken Sie in der Spalte **[!UICONTROL Action]** für die ausgewählte Reihenfolge auf **[!UICONTROL View]**.

1. Klicken Sie auf **[!UICONTROL Ship]**.

1. Scrollen Sie nach unten zum Block **[!UICONTROL Payment & Shipping Method]** und klicken Sie auf **[!UICONTROL Add Tracking Number]** in **[!UICONTROL Shipping Information]**.

1. Legen Sie den Wert **[!UICONTROL Carrier]** fest.

1. Um die Sendung zu verfolgen, geben Sie die Werte **[!UICONTROL Title]** und **[!UICONTROL Number]** ein.

1. Klicken Sie auf **[!UICONTROL Submit Shipment]**.

>[!NOTE]
>
> Alternativ können Sie ein Versandmodul verwenden, um die Trackingnummerninformationen einzugeben. Stellen Sie sicher, dass das Versandmodul die Trackingnummerninformationen im Feld `tracking_number` speichert.

### Vereinbarkeit mit Dritten

Jede Erweiterung von Drittanbietern ist mit der Funktionalität kompatibel, wenn eine Sendungsentität über die [Commerce API](https://developer.adobe.com/commerce/webapi/rest/attributes/#magentosalesapishipmentrepositoryinterface-shipmentrepositoryinterface){target=_blank} erstellt wird.
