---
title: Konfiguration des Hintergrundprozesses
description: "Konfigurieren Sie die Zeitpläne für [!DNL Store Fulfillment] Hintergrundprozesse, die zum Synchronisieren von Daten mit den Fulfillment-Diensten verwendet werden."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Konfiguration des Hintergrundprozesses

Die Integration von Store Fulfillment verwendet Hintergrundprozesse und Nachrichtenwarteschlangen für optimale Leistung und Skalierung. Erstellen Sie Umgebungen für Ihre Adobe Commerce-Stores mithilfe von [Bereitstellungsvariablen](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) , die automatisch [Nachrichtenwarteschlangen-Läufern](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html) starten.

Hintergrundprozesse werden mit der standardmäßigen Adobe Commerce [Geplante Aufgaben](https://docs.magento.com/user-guide/system/cron.html) -Funktion verwaltet. Diese Prozesse sind für die Synchronisierung von Bestell- und Merchant Store-Konfigurationsdaten mit Store-Erfüllungs-Webdiensten verantwortlich.

## Geplante Aufgaben für die Store-Erfüllung verwalten

Wechseln Sie vom Administrator zu &quot;**[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**&quot;.

Überprüfen Sie die Standardkonfiguration für Store Fulfillment-Dienste. Sie können diese Einstellungen entsprechend Ihrem Auftragsverarbeitungsvolumen und Ihrer Ressourcenverfügbarkeit anpassen.
