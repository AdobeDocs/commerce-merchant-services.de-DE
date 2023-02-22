---
title: Befehlszeilenkonfiguration
description: Nach der Installation können Sie [!DNL Payment Services] über die Befehlszeilenschnittstelle (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Befehlszeilenkonfiguration

Nach der Installation [!DNL Payment Services]können Sie sie einfach über [innerhalb der Startseite](payments-home.md) oder über die Befehlszeilenschnittstelle (CLI).

## Datenexport konfigurieren

[!DNL Payment Services] kombiniert Bestelldaten aus [!DNL Magento Open Source] und [!DNL Adobe Commerce] mit aggregierten Zahlungsdaten von Zahlungsdienstleistern, um nützliche Berichte zu erstellen. Die [!DNL Payment Services] -Erweiterung verwendet Indexer, um effizient alle erforderlichen Daten für die Berichte zu erfassen.

Informationen zu den in verwendeten Daten [!DNL Payment Services] Reporting, siehe [Bestellstatusbericht](order-payment-status.md#data-used-in-the-report).

### CRON konfigurieren [!DNL Magento Open Source]

Wenn Sie eine `BY SCHEDULE` Indexmodus auf [!DNL Magento Open Source], müssen Sie Cron konfigurieren. Siehe [Cron konfigurieren und ausführen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Indexer festlegen

Die Bestelldaten werden mithilfe eines von zwei Indexmodi im Zahlungsdienst exportiert und beibehalten.—`ON SAVE` (Standard) oder `BY SCHEDULE` (empfohlen).

Die folgenden Indizes sind für [!DNL Payment Services]:

| Code | Name | Beschreibung |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Sales Order Feed | Erstellt den Index der Bestelldaten |
| `sales_order_status_data_exporter` | Feed zum Status von Verkaufsaufträgen | Builds Index of Sales Order Statuses data |
| `store_data_exporter` | Stores Feed | Erstellt einen Index von Store-Daten |

Um den Indexmodus für alle drei Indexer zu ändern, führen Sie Folgendes aus:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Wenn Sie in Ihrem Befehl keine Indexer angeben, werden alle Indexer auf denselben Wert aktualisiert. Wenn Sie einen bestimmten Indexer ändern möchten, müssen Sie ihn in Ihrem -Befehl auflisten.

Weitere Informationen zum manuellen Ändern des Indexermodus finden Sie unter [Indexer konfigurieren](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} im Benutzerhandbuch zu zentralen Themen.

### Daten manuell neu indizieren

Sie können Daten manuell neu indizieren, anstatt darauf zu warten, dass sie automatisch vorgenommen werden. Siehe [Neuindizierung](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} für weitere Informationen.

Wann `BY SCHEDULE` -Modus festgelegt ist, verfolgt das System geänderte Entitäten und der Cron-Auftrag aktualisiert den Index für sie anhand eines festgelegten Zeitplans. Siehe [Ausführen von cron über die Befehlszeile](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Cron konfigurieren und ausführen](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)), um zu erfahren, wie Sie die Indexierung manuell mit Cron-Aufträgen durchführen.

### Senden von reinen Daten an den Zahlungsdienst

Nachdem die Daten indiziert wurden, werden sie automatisch an [!DNL Payment Services]. Mit diesem Befehl können Sie auch den Prozess zum Senden indizierter Daten manuell Trigger haben:

```bash
bin/magento saas:resync --feed [feedName]
```

Verwenden Sie die folgenden Befehlsoptionen:

| Befehl | Beschreibung |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Führt eine Neuindizierung des angegebenen Feeds durch und sendet ihn an den entsprechenden Dienst |
| `bin/magento saas:resync --no-reindex` | Überspringt die Indexierung und sendet nicht synchronisierte Daten aus den Indizes |

Die `--feed` -Parameter können Sie angeben, welchen Feed Sie senden möchten:

| Feed | Beschreibung |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Bestellungen-Feed im Produktionsmodus |
| `paymentServicesOrdersSandbox` | Bestellungen-Feed im Sandbox-Modus |
| `paymentServicesOrderStatusesProduction` | Bestellstatus im Produktionsmodus |
| `paymentServicesOrderStatusesSandbox` | Bestellstatus im Sandbox-Modus |
| `paymentServicesStoresProduction` | Stores im Produktionsmodus |
| `paymentServicesStoresSandbox` | Stores im Sandbox-Modus |

Alle für die Berichte erforderlichen Daten werden an [!DNL Payment Services] automatisch, wenn Cron konfiguriert und installiert ist. Sie können den Prozess des Versands von Cron-Daten auch manuell an Trigger [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Weitere Informationen zur Neuindizierung und zu Indizes finden Sie unter [Indexer verwalten](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) Thema in der Entwicklerdokumentation.
