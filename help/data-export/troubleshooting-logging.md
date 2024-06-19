---
title: Protokolle überprüfen und Fehlerbehebung
description: "Informationen zur Fehlerbehebung [!DNL data export] Fehler in den Logs zum Datenexport und SAAS-Export."
feature: Services
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Überprüfen von Protokollen und Fehlerbehebung

Die [!DNL data export] -Erweiterung stellt Protokolle zur Verfolgung von Datenerfassungs- und Synchronisierungsprozessen bereit.

## Protokolle

Protokolle sind im Abschnitt `var/log` Ordner auf dem Commerce-Anwendungsserver.

| Protokollname | filename | description |
|-----------------| ----------| -------------|
| SaaS-Datenexport-Protokoll | `commerce-data-export.log` | Bietet Informationen zu Datenexportaktivitäten wie Entitätsereignissen und vollständigen Triggern zur erneuten Synchronisierung.  Jeder Protokolldatensatz hat eine bestimmte Struktur und enthält Informationen zu Feed, Vorgang, Status, verstrichener Zeit, Prozess-ID und Aufrufer. |
| Fehlerprotokoll beim SAAS-Datenexport | `data-export-errors.log` | Stellt Fehlermeldungen und Stacktraces für Fehler bereit, die während des Datensynchronisierungsprozesses auftreten. |
| SaaS-Exportprotokoll | `saas-export.log` | Bietet Informationen zu den Daten, die an Commerce SaaS-Dienste gesendet werden. |
| Systemexport-Fehlerprotokoll | `saas-export-errors.log` | Enthält Informationen zu Fehlern, die beim Senden von Daten an Commerce SaaS-Dienste auftreten. |

Wenn die erwarteten Daten für einen Adobe Commerce-Dienst nicht angezeigt werden, verwenden Sie die Fehlerprotokolle für die Datenexport-Erweiterung, um zu ermitteln, wo das Problem aufgetreten ist.

Sie können Protokolle mit zusätzlichen Daten für die Verfolgung und Fehlerbehebung erweitern. Siehe [Erweiterte Protokollierung](#extended-logging).

### Protokollformat

Jeder Protokolldatensatz hat die folgende Struktur.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>Die JSON-basierte Zeichenfolge ist für eine bessere Lesbarkeit verschönert.

In der folgenden Tabelle werden die in den Protokollen aufgezeichneten Vorgangsarten beschrieben.

| Vorgang | Beschreibung | Caller-Beispiel |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Vollständige Synchronisierung | Vollständige Synchronisierung erfasst und sendet alle Daten für einen bestimmten Feed an das SaaS. | `bin/magento saas:resync --feed=products` |
| partieller Reindex | Teilsynchronisierung erfasst und sendet Daten nur für aktualisierte Entitäten in einem bestimmten Feed an SaaS. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=index` |
| Wiederholen fehlgeschlagener Elemente | Sendet Elemente für einen bestimmten Feed an SaaS, wenn der vorherige Synchronisierungsvorgang aufgrund eines Commerce-Anwendungs- oder Serverfehlers fehlgeschlagen ist. Dieses Protokoll ist nur vorhanden, wenn fehlgeschlagene Elemente vorhanden sind. | `bin/magento cron:run --group=saas_data_exporter`  (beliebige Cron-Gruppe &quot;*_data_exporting&quot;) |
| Vollständige Synchronisierung (alt) | Vollständige Synchronisierung für einen bestimmten Feed im alten Exportmodus. | `bin/magento saas:resync --feed=categories` |
| partielle Neuindizierung (alt) | Sendet aktualisierte Entitäten an SaaS für einen bestimmten Feed im alten Exportmodus. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=index` |
| Partielle Synchronisierung (alt) | Sendet aktualisierte Entitäten an SaaS für einen bestimmten Feed im alten Exportmodus. Dieses Protokoll ist nur vorhanden, wenn aktualisierte Entitäten vorhanden sind. | `bin/magento cron:run --group=saas_data_exporter` (beliebige Cron-Gruppe &quot;*_data_exporting&quot;) |


### Beispiele für die Protokollierung

Während einer vollständigen Neusynchronisierung wird der Fortschritt standardmäßig alle 30 Sekunden verfolgt und protokolliert. Im Folgenden finden Sie einen Beispielprotokolleintrag.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

In diesem Beispiel wird die `status` -Werte liefern Informationen zum Synchronisierungsvorgang:

- **`"Progress 2/5"`** gibt an, dass 2 von 5 Iterationen abgeschlossen sind. Die Anzahl der Iterationen hängt von der Anzahl der exportierten Entitäten ab.
- **`"processed: 200"`** gibt an, dass 200 Elemente verarbeitet wurden.
- **`"synced: 100"`** gibt an, dass 100 Elemente an SaaS gesendet wurden. Es wird erwartet, dass `"synced"` ist nicht gleich `"processed"`. Im Folgenden finden Sie ein Beispiel:
   - **`"synced" < "processed"`** bedeutet, dass die Feed-Tabelle im Vergleich zur zuvor synchronisierten Version keine Änderungen am Element erkannt hat. Solche Elemente werden während des Synchronisierungsvorgangs ignoriert.
   - **`"synced" > "processed"`** dieselbe Entitäts-ID (z. B. `Product ID`) kann mehrere Werte in verschiedenen Bereichen aufweisen. Beispielsweise kann ein Produkt fünf Websites zugewiesen werden. In diesem Fall verfügen Sie möglicherweise über &quot;1 verarbeitetes&quot;Element und &quot;5 synchronisierte&quot;Elemente.

+++ Beispiel: Vollständiges Resync-Protokoll für den Preisfeed

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## Anzeigen von und Fehlerbehebung bei Protokollen mit New Relic

Wenn Sie Adobe Commerce-Logs in der New Relic speichern, können Sie Parsing-Regeln hinzufügen, um die Lesbarkeit und das Abfrageerlebnis zu verbessern.

1. Melden Sie sich bei New Relic an.

1. Navigieren Sie zu `Logs => Parsing`.

1. Klicks `Create parsing rule`.

1. Konfigurieren Sie die Parsing-Regel, indem Sie die folgenden Werte hinzufügen.

   - **Filtern von Protokollen basierend auf NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Parsing-Regel**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

In diesem Beispiel wird eine Regel hinzugefügt, mit der Sie New Relic-Protokolle nach Feed-Typ, Vorgang usw. abfragen können.

**Beispielabfragezeichenfolge**—`feed.feed:"products" and feed.status:"Complete"`

## Erweiterte Protokollierung

Sie können Umgebungsvariablen verwenden, um Protokolle mit zusätzlichen Daten für Tracking und Fehlerbehebung zu erweitern.

### Überprüfen der Feed-Payload

Fügen Sie die Feed-Payload in das SaaS-Exportprotokoll ein, indem Sie die `EXPORTER_EXTENDED_LOG=1` Umgebungsvariable beim erneuten Synchronisieren des Feeds.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

Nach Abschluss des Vorgangs ist die Feed-Payload im SaaS-Exportprotokoll (`var/.log/saas-export.log`).

### Payload in Feed-Indextabelle beibehalten

Für die Commerce SaaS-Datenexport-Erweiterung (`magento/module-data-exporter`) 103.3.0 und höher halten sofortige Export-Feeds nur die erforderlichen Mindestdaten in der Indextabelle. Die Feeds enthalten alle Katalog- und Bestandsstatus-Feeds.

Die Beibehaltung von Payload-Daten in der Indextabelle wird in Produktionsumgebungen nicht empfohlen, kann aber in einer Entwicklungsumgebung nützlich sein. Fügen Sie die Feed-Payload in den Index ein, indem Sie die `PERSIST_EXPORTED_FEED=1` Umgebungsvariable beim erneuten Synchronisieren des Feeds.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Führen Sie einen Profiler aus, um eine Fehlerbehebung bei langsamer Leistung durchzuführen

Wenn der Neuindizierungsprozess eines bestimmten Feeds unangemessen lange dauert, führen Sie den Profiler aus, um zusätzliche Daten zu erfassen, die für das Supportteam nützlich sein könnten.

Führen Sie den Profiler aus, indem Sie die `EXPORTER_PROFILER=1` Umgebungsvariable beim Ausführen des Befehls &quot;reindex&quot;.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profildaten werden im Datenexport-Protokoll gespeichert (`var/log/commerce-data-export.log`) im folgenden Format:

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```




