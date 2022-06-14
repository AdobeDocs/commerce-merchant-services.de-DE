---
title: Hintergrundprozesse
description: '"Konfigurieren Sie die Zeitpläne für [!DNL Store Fulfillment] Hintergrundprozesse, die zur Synchronisierung von Daten mit den Erfüllungsdiensten verwendet werden"                   '
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Konfiguration des Hintergrundprozesses

Die Integration von Store Fulfillment verwendet Hintergrundprozesse und Nachrichtenwarteschlangen für optimale Leistung und Skalierung. Erstellen Sie Umgebungen für Ihre Adobe Commerce-Stores mit [Bereitstellungsvariablen](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) automatisch starten [Nachrichtenwarteschlangenläufer](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Hintergrundprozesse werden mithilfe des standardmäßigen Adobe Commerce verwaltet [Geplante Aufgaben](https://docs.magento.com/user-guide/system/cron.html) Funktionalität. Diese Prozesse sind für die Synchronisierung von Bestell- und Merchant Store-Konfigurationsdaten mit Store-Erfüllungs-Webdiensten verantwortlich.

## Geplante Aufgaben für die Store-Erfüllung verwalten

Navigieren Sie vom Administrator zu **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks)> Cron configuration options for group:store_fulfillment]**.


Überprüfen Sie die Standardkonfiguration für Store Fulfillment-Dienste. Abhängig von Ihrem Auftragsverarbeitungsvolumen und Ihrer Ressourcenverfügbarkeit müssen Sie diese Einstellungen möglicherweise anpassen.


