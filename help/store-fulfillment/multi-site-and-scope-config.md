---
title: Konfiguration mehrerer Websites und Perimeter
description: Konfigurieren Sie Lager und Bereitstellungsmethoden für mehrere Websites und Storebereiche.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Konfiguration mehrerer Websites und Perimeter

Sie können den [Umfang](https://docs.magento.com/user-guide/configuration/scope.html) für einige Elemente festlegen, um mehrere Websites, Stores und Store-Ansichten aufzunehmen:

- [ Stock verwalten](https://docs.magento.com/user-guide/catalog/inventory-stock.html) pro Umfang

- Verwalten von [!DNL Delivery Methods] pro Umfang

Sie können einem Website- oder Store-Bereich ein Lager zuweisen. Aktualisieren Sie dann die Store-Quellen, um verfügbare Bereitstellungsmethoden festzulegen (Startseite, Store-Abruf).

Nach erfolgreicher Aktualisierung der Konfiguration können die Speicherbereinigungsoptionen auf der Produktdetailseite (PDP) in der Adobe Commerce-Storefront nur für Produkte ausgewählt werden, die von einer Lagerquelle verfügbar sind, die die Speicherbereinigung ermöglicht.

## Einstellungen zur In-Store-Abholung verwalten

Aktivieren oder deaktivieren Sie die [!UICONTROL In-Store Pickup] -Optionen für jede Website oder jeden Speicherbereich in den [Konfigurationen für Bereitstellungsmethoden](enable-general.md#delivery-methods) im Admin.

1. Navigieren Sie zu **[!UICONTROL Stores > Configuration]**.

1. Wählen Sie den zu konfigurierenden Perimeter (Website zu Store) aus.

1. Navigieren Sie bei ausgewähltem Bereich zu &quot;**[!UICONTROL Sales > Delivery Methods]**&quot;.

1. Deaktivieren oder aktivieren Sie die Versandmethode **[!UICONTROL In-Store Pickup]** .

In diesem Abschnitt können Sie auch verwalten, ob die Cursor- oder In-Store-Abholung global verfügbar ist.

Verwalten Sie die Einstellungen [!UICONTROL In-Store Pickup] und [!UICONTROL Delivery Method] pro Lagerbestand. Es gibt zahlreiche weitere Konfigurationen, um die volle Flexibilität Ihrer Implementierung zu gewährleisten.
