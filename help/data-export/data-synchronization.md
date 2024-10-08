---
title: Daten mit SaaS-Datenexport synchronisieren
description: Erfahren Sie, wie [!DNL SaaS Data Export] Daten zwischen Adobe Commerce-Instanzen und verbundenen SaaS-Diensten erfasst und synchronisiert.
role: Admin, Developer
exl-id: 530a6ed7-46ec-45fc-94e9-c850168e8aed
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Daten mit SaaS-Datenexport synchronisieren

Wenn Sie einen Commerce-Dienst installieren, der einen Datenexport erfordert, z. B. Catalog Service, Live Search oder Product Recommendations, wird eine Sammlung von Saas-Datenexportmodulen installiert, um den Datenerfassungs- und Synchronisierungsprozess zu verwalten.

Der SAAS-Datenexport verschiebt Produktdaten laufend von einer Adobe Commerce-Instanz auf die Commerce Services-Plattform, um die Daten auf dem neuesten Stand zu halten. Beispielsweise erfordert Product Recommendations die aktuellen Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit exakt zurückzugeben. Verwenden Sie das [Dashboard &quot;Datenverwaltung&quot;](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync), um den Synchronisierungsprozess zu beobachten und zu verwalten, oder die Befehlszeilenschnittstelle, um eine Synchronisierung Trigger und Produktdaten für die Verwendung durch Commerce Services neu zu indizieren.

Das folgende Diagramm zeigt den SaaS-Datenexport-Fluss.

![Speichern des Datexport-Erfassungsablaufs und Synchronisierungsablaufs für Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

Zu den Hauptkomponenten des SAAS-Datenexportflusses gehören:

- SaaS-Datenexportmodule, die die Daten für Feeds aus Adobe Commerce erfassen, Feed-Elemente assemblieren, auf Aktualisierungen warten und den Feed-Status beibehalten.
- SaaS-Exportmodule, die Daten exportieren, Routing konfigurieren und die Feeds in verbundenen Diensten veröffentlichen.
- Der Adobe Commerce-Dienst verwaltet den Datenerfassungsprozess, um eingehende Feeds zu validieren und Aktualisierungen an verbundenen Diensten beizubehalten.

## Synchronisierungsmodi

Der SaaS-Datenexport verfügt über zwei Modi zur Verarbeitung von Entitäts-Feeds:

- **Sofortiger Exportmodus**: In diesem Modus werden Daten erfasst und in einer einzigen Iteration sofort an den Commerce-Dienst gesendet. Dieser Modus beschleunigt die Bereitstellung von Entitätsaktualisierungen für den Commerce-Dienst und verringert die Speichergröße der Feed-Tabellen.

- **Legacy export mode**: In diesem Modus werden Daten in einem einzigen Prozess erfasst. Dann sendet ein Cron-Auftrag die erfassten Daten an die verbundenen Commerce-Dienste. In Datenexport-Protokolleinträgen werden Feeds, die den alten Modus verwenden, als `(legacy)` bezeichnet.

## Synchronisierungstypen

Der SAAS-Datenexport unterstützt die Synchronisierung von drei Synchronisierungstypen: vollständige Synchronisierung, teilweise Synchronisierung und Wiederholung der Synchronisierung fehlgeschlagener Elemente.

### Vollständige Synchronisierung

Nachdem Sie eine Adobe Commerce-Instanz mit Commerce Service verbunden haben, führen Sie eine vollständige Synchronisierung durch, um Entitäts-Feed-Daten von Adobe Commerce an den verbundenen Dienst zu senden.

>[!NOTE]
>
>Vollständige Synchronisation ist hauptsächlich für die Onboarding-Phase vorgesehen. Vermeiden Sie die regelmäßige Verwendung, um eine Überlastung der Datenbank zu verhindern. Nach der ersten Synchronisierung werden laufende Änderungen automatisch mithilfe einer partiellen Synchronisierung synchronisiert.

### Teilsynchronisierung

Bei teilweiser Synchronisierung sendet der SaaS-Datenexport automatisch Aktualisierungen von der Commerce-Anwendung, wie z. B. Produktnamensänderungen oder Preisaktualisierungen, an verbundene Commerce-Dienste.

Der Datenexportprozess verwendet die folgenden Cron-Aufträge, um den Teilsynchronisierungsvorgang zu automatisieren.

- Cron-Gruppenaufträge &quot;index&quot;:
   - Der `indexer_reindex_all_invalid` -Auftrag deklariert alle ungültigen Feeds neu. Es handelt sich um einen standardmäßigen Adobe Commerce-Cron-Auftrag.
   - Der `saas_data_exporter`-Auftrag ist für veraltete Export-Feeds bestimmt.
   - Der Auftrag `sales_data_exporter` ist spezifisch für den Export-Feed für Verkaufsdaten.

Diese Aufträge werden jede Minute ausgeführt.

Damit die teilweise Synchronisierung funktioniert, muss die Commerce-Anwendung wie folgt konfiguriert werden:

- [Die Aufgabenplanung ist über Cron-Aufträge aktiviert](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Alle SaaS-Datenexport-Indexer werden im `Update by Schedule` -Modus konfiguriert.

  In der SaaS-Datenexportversion 103.1.0 und höher ist der `Update by Schedule` -Modus standardmäßig aktiviert. Sie können die Indexkonfiguration auf dem Server mithilfe des Commerce CLI-Befehls `bin/magento indexer:show-mode | grep -i feed` überprüfen.

### Synchronisation fehlgeschlagener Elemente wiederholen

Die Synchronisierung fehlgeschlagener Elemente erneut versuchen verwendet einen separaten Prozess, um Elemente erneut zu senden, die während des Synchronisierungsprozesses aufgrund von Fehlern nicht synchronisiert werden konnten, z. B. einen Anwendungsfehler, eine Netzwerkunterbrechung oder einen SaaS-Dienstfehler. Die Implementierung für diese Synchronisierung basiert auch auf Cron-Aufträgen.

- `resync_failed_feeds_data_exporter` Cron-Gruppenaufträge:
   - Der Auftrag `<feed name>_feed_resend_failed_feeds_items` sendet erneut Elemente, die nicht synchronisiert werden konnten, z. B. `products_feed_resend_failed_items`.

### Synchronisierungsprozess anzeigen und verwalten

Die meisten Synchronisierungsaktivitäten werden automatisch auf der Basis der Anwendungskonfiguration verarbeitet. Der SaaS-Datenexport bietet jedoch auch Tools zur Verwaltung des Prozesses.

- Admin-Benutzer können den Synchronisierungsfortschritt anzeigen und verfolgen und Informationen zu den Daten aus dem [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) abrufen.

- Entwickler, Systemintegratoren oder Administratoren mit Zugriff auf den Commerce-Anwendungsserver können den Synchronisierungsprozess und die Daten-Feeds mithilfe des Befehlszeilen-Tools (CLI) von Adobe Commerce verwalten. Siehe [Referenz zum Datenexport-Befehl](data-export-cli-commands.md).

### Commerce-Anwendungskonfiguration überprüfen

Die Synchronisierung fehlerhafter Elemente teilweise synchronisieren und erneut versuchen funktioniert nur, wenn die Commerce-Instanz richtig konfiguriert wurde. In der Regel wird die Konfiguration beim Einrichten des Commerce-Dienstes abgeschlossen. Wenn der Datenexport nicht ordnungsgemäß funktioniert, überprüfen Sie die folgende Konfiguration.

- [Vergewissern Sie sich, dass Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- Stellen Sie sicher, dass die Indexer über den Befehl [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) oder den Commerce-CLI-Befehl `bin/magento indexer:info` ausgeführt werden.

- Stellen Sie sicher, dass die Indexer für die folgenden Feeds auf &quot;`Update by Schedule`&quot; eingestellt sind: Katalogattribute, Produkt, Produktüberschreibungen und Produktvarianten. Sie können die Indexer über die [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) im Admin oder über die CLI (`bin/magento indexer:show-mode | grep -i feed`) überprüfen.

### Benachrichtigungen des Ereignismanagers für die Datenübertragungsprotokollierung

In Version 103.3.4 und höher sendet der SaaS-Datenexport das `data_sent_outside` -Ereignis, wenn Daten von der Commerce-Instanz an Adobe Commerce-Dienste gesendet werden.

```php
$this->eventManager->dispatch(
   "data_sent_outside",
   [
       "timestamp" => time(),
       "type" => $metadata->getFeedName(),
       "data" => $data
   ]
);
```

>[!NOTE]
>
>Weitere Informationen zu Ereignissen und deren Abonnement finden Sie unter [Ereignisse und Beobachter](https://developer.adobe.com/commerce/php/development/components/events-and-observers) in der Adobe Commerce-Entwicklerdokumentation.