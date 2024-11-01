---
title: Speicherstandort und Systemkonfiguration für die Zuordnung
description: Konfigurieren Sie einen Entfernungsanbieter, um die Zuordnung von Speicherorten in der Storefront-Benutzeroberfläche zu unterstützen. Für die Lösungen zur Store-Erfüllung ist ein Fernanbieter erforderlich, der die Einzelhandelssuche sowie andere Zuordnungs- und Planungsfunktionen für den End-to-End-Workflow zur Erfüllung von Anforderungen ermöglicht.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Speicherort und Einrichtung der Zuordnung

Aktivieren Sie die Speicherstandort- und Zuordnungsfunktionen für die Store-Erfüllung, indem Sie einen [Entfernungsanbieter](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm) konfigurieren, um nach Einzelhandelsspeicherorten zu suchen.

**Anforderungen**

Während des Konfigurationsprozesses stellen Sie einen Google-API-Schlüssel für die Google Maps-Plattform bereit. Wenn Sie noch keine haben, generieren Sie [eine von der Google Maps-Plattform](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/distance-priority-algorithm#configure-google-maps).

So konfigurieren Sie den Entfernungsanbieter:

1. Fügen Sie aus der Konfiguration **[!UICONTROL Stores > General]** in Admin die Google Maps-Integration für den Inhaltstyp Zuordnung hinzu.

   - Wechseln Sie zu &quot;**[!UICONTROL Stores > Configuration  > General > Content Management]**&quot;.

   - Fügen Sie Ihren Google-API-Schlüssel zum Feld **[!UICONTROL Google Maps API Key]** hinzu.

1. Wählen Sie in der Konfiguration **[!UICONTROL Stores > Inventory]** in Admin den Entfernungsanbieter für Store Fulfillment aus.

   - Wechseln Sie zu &quot;**[!UICONTROL Stores > Configuration > Catalog > Inventory]**&quot;.

   - Erweitern Sie den Abschnitt **[!UICONTROL Distance Provider for Distance Based SSA]** .

   - Stellen Sie den **Provider** auf **Google Map** ein.

1. Konfigurieren Sie die Einstellungen für **[!UICONTROL Google Distance Provider]**.

   - Fügen Sie Ihren **Google-API-Schlüssel** hinzu.

   - Setzen Sie **[!UICONTROL Computation Mode]** auf `Driving` und **[!UICONTROL Value]** auf `Distance`
