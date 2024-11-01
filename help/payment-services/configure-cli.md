---
title: Befehlszeilenkonfiguration
description: Nach der Installation können Sie  [!DNL Payment Services] über die Befehlszeilenschnittstelle (CLI) konfigurieren.
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Befehlszeilenkonfiguration

Nachdem Sie [!DNL Payment Services] installiert haben, können Sie es einfach über [im Home](payments-home.md) oder über die Befehlszeilenschnittstelle (CLI) konfigurieren.

## Datenexport konfigurieren

[!DNL Payment Services] kombiniert Bestelldaten aus [!DNL Magento Open Source] und [!DNL Adobe Commerce] mit aggregierten Zahlungsdaten von Zahlungsdienstleistern, um nützliche Berichte zu erstellen. Die Erweiterung [!DNL Payment Services] verwendet Indexer, um alle erforderlichen Daten für die Berichte effizient zu erfassen.

Weitere Informationen zu den in [!DNL Payment Services] -Berichten verwendeten Daten finden Sie unter [Bestellzahlstatus-Bericht](order-payment-status.md#data-used-in-the-report).

### Cron für [!DNL Magento Open Source] konfigurieren

Wenn Sie einen `BY SCHEDULE` -Indexmodus für [!DNL Magento Open Source] verwenden möchten, müssen Sie Cron konfigurieren. Siehe [cron konfigurieren und ausführen](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs).

### Indexer festlegen

Die Bestelldaten werden mithilfe eines der beiden Indexmodi exportiert und im Zahlungsdienst beibehalten: `ON SAVE` (Standard) oder `BY SCHEDULE` (empfohlen).

Die folgenden Indizes gelten für [!DNL Payment Services]:

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

Weitere Informationen zum manuellen Ändern des Modus eines Indexers finden Sie unter [Indexer konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers){target="_blank"} in der Entwicklerdokumentation. Informationen dazu, wie Sie ihn in Admin ändern können, finden Sie unter [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode){target="_blank"} im Benutzerhandbuch zu Kerninhalten.

### Daten manuell neu indizieren

Sie können Daten manuell neu indizieren, anstatt darauf zu warten, dass sie automatisch vorgenommen werden. Weitere Informationen finden Sie unter [Neuindizieren](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#reindex){target="_blank"} in [Verwalten der Indexer](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers){target="_blank"} .

Wenn der `BY SCHEDULE` -Modus festgelegt ist, verfolgt das System geänderte Entitäten und der Cron-Auftrag aktualisiert den Index für sie basierend auf einem festgelegten Zeitplan. Informationen zum manuellen Trigger der Indexierung mithilfe von Cron-Aufträgen finden Sie unter [Ausführen von cron über die Befehlszeile ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs#config-cli-cron-group-run) in [Konfigurieren und Ausführen von cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)).

### Senden von reinen Daten an den Zahlungsdienst

Nachdem die Daten indiziert wurden, werden sie automatisch an [!DNL Payment Services] gesendet. Mit diesem Befehl können Sie auch den Prozess zum Senden indizierter Daten manuell Trigger haben:

```bash
bin/magento saas:resync --feed [feedName]
```

Verwenden Sie die folgenden Befehlsoptionen:

| Befehl | Beschreibung |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Führt eine Neuindizierung des angegebenen Feeds durch und sendet ihn an den entsprechenden Dienst |
| `bin/magento saas:resync --no-reindex` | Überspringt die Indexierung und sendet nicht synchronisierte Daten aus den Indizes |

Mit dem Parameter `--feed` können Sie angeben, welcher Feed gesendet werden soll:

| Feed | Beschreibung |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Bestellungen-Feed im Produktionsmodus |
| `paymentServicesOrdersSandbox` | Bestellungen-Feed im Sandbox-Modus |
| `paymentServicesOrderStatusesProduction` | Bestellstatus im Produktionsmodus |
| `paymentServicesOrderStatusesSandbox` | Bestellstatus im Sandbox-Modus |
| `paymentServicesStoresProduction` | Stores im Produktionsmodus |
| `paymentServicesStoresSandbox` | Stores im Sandbox-Modus |

Alle für die Berichte erforderlichen Daten werden automatisch an [!DNL Payment Services] gesendet, wenn Cron konfiguriert und installiert ist. Sie können den Prozess des Versands von Cron-Daten an [!DNL Payment Services] auch manuell Trigger haben.

```bash
bin/magento cron:run --group payment_services_data_export
```

Weitere Informationen zur Neuindizierung und zu Indizes finden Sie im Thema [Verwalten der Indexer](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) in der Entwicklerdokumentation.

## L2/L3-Verarbeitung konfigurieren

[!DNL Payment Services] kann Daten der Stufe 2 und der Stufe 3 aus Kartenzahlungen verarbeiten, um zusätzliche Informationen für Händler bereitzustellen.

>[!WARNING]
>
> Die Integration mit der Verarbeitung auf Level 2 und Level 3 mit PayPal ist nur für US-Händler verfügbar. Weitere Informationen finden Sie unter [Zahlungsverarbeitung](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} in der PayPal-Entwicklerdokumentation.

Wenn Sie die L2/L3-Verarbeitungsdaten für [!DNL Payment Services] verwenden möchten oder Fragen haben, wenden Sie sich an Ihren [!DNL Payment Services]-Kundenbetreuer.

Informationen zur Verarbeitung von L2 und L3, die in [!DNL Payment Services] verwendet werden, finden Sie unter [Verarbeitung auf Ebene 2 und Stufe 3](levels-card-payment-transactions.md).
