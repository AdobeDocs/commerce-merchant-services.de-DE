---
title: Speicherstandort und Systemkonfiguration für die Zuordnung
description: Konfigurieren Sie einen Entfernungsanbieter, um die Zuordnung von Speicherorten in der Storefront-Benutzeroberfläche zu unterstützen. Für die Lösungen zur Store-Erfüllung ist ein Fernanbieter erforderlich, der die Einzelhandelssuche sowie andere Zuordnungs- und Planungsfunktionen für den End-to-End-Workflow zur Erfüllung von Anforderungen ermöglicht.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Speicherort und Einrichtung der Zuordnung

Aktivieren Sie die Speicherstandort- und Zuordnungsfunktionen für die Store-Ausführung, indem Sie eine [Fernabsatzanbieter](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) , um nach Einzelhandelsspeicherorten zu suchen.

**Voraussetzungen**

Während des Konfigurationsprozesses stellen Sie einen Google-API-Schlüssel für die Google Maps-Plattform bereit. Wenn Sie keine haben, [eine aus der Google Maps-Plattform generieren](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

So konfigurieren Sie den Entfernungsanbieter:

1. Aus dem **[!UICONTROL Stores > General]** -Konfiguration in Admin die Google Maps-Integration für den Inhaltstyp &quot;Map&quot;hinzufügen.

   - Navigieren Sie zu **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Hinzufügen Ihres Google-API-Schlüssels zu **[!UICONTROL Google Maps API Key]** -Feld.

1. Aus dem **[!UICONTROL Stores > Inventory]** -Konfiguration in der Admin-Konfiguration wählen Sie den Entfernungsanbieter für Store-Erfüllung aus.

   - Navigieren Sie zu **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Erweitern Sie die **[!UICONTROL Distance Provider for Distance Based SSA]** Abschnitt.

   - Legen Sie die **Anbieter** nach **Google Map**.

1. Konfigurieren Sie die Einstellungen für **[!UICONTROL Google Distance Provider]**.

   - Fügen Sie Ihre **Google-API-Schlüssel**.

   - Satz **[!UICONTROL Computation Mode]** nach `Driving` und **[!UICONTROL Value]** nach `Distance`
