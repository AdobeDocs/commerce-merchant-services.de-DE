---
title: Verbessern der SAAs-Datenexportleistung
description: Erfahren Sie, wie Sie die Leistung des SAAS-Datenexports für Commerce Services verbessern können, indem Sie den Datenexport-Modus mit mehreren Threads verwenden.
role: Admin, Developer
recommendations: noCatalog
exl-id: 20c81ef4-5a97-45cd-9401-e82910a2ccc3
source-git-commit: 42a9ea0f62f35db451cd3e780adf530d0699a638
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Verbessern der SAAs-Datenexportleistung

**Datenexportmodus mit mehreren Threads** beschleunigt den Exportvorgang, indem Feed-Daten in Batches aufgeteilt und parallel verarbeitet werden.

Entwickler oder Systemintegratoren können die Leistung verbessern, indem sie den Datenexport-Modus mit mehreren Threads anstelle des standardmäßigen Einzelthread-Modus verwenden. Im Single-Thread-Modus gibt es keine Parallelisierung des Feed-Sendeprozesses. Aufgrund der festgelegten Standardbeschränkungen sind außerdem alle Clients darauf beschränkt, nur einen Thread zu verwenden. In den meisten Fällen ist eine Anpassung der Konfiguration nicht erforderlich.

## Überlegungen zur Verwendung des Multi-Thread-Modus

Beim Arbeiten mit Datenexportdiensten möchten Sie die Leistung optimieren und gleichzeitig eine genaue Synchronisierung sicherstellen.
Adobe empfiehlt die Verwendung der Standardkonfiguration für die Datenerfassung, die normalerweise den Synchronisierungsanforderungen für Commerce-Händler entspricht. Es gibt jedoch Szenarien, in denen die Anpassung die Verarbeitungszeit verkürzen kann.

Beachten Sie bei der Entscheidung, ob die Konfiguration des Datenexports angepasst werden soll, die folgenden Schlüsselfaktoren:

- **Erstsynchronisierung** - Evaluieren Sie die Anzahl der Produkte und [schätzen Sie das Datenvolumen und die Übertragungszeit](estimate-data-volume-sync-time.md) anhand der Standardkonfiguration. Fragen Sie sich selbst: Können Sie nach dem Einstieg in einen Commerce-Dienst auf diese erste Datensynchronisation warten?

- **Hinzufügen neuer Store-Ansichten oder Websites** - Wenn Sie Store-Ansichten oder Websites mit derselben Produktanzahl nach der Live-Schaltung hinzufügen möchten, schätzen Sie das Datenvolumen und die Übertragungszeit. Bestimmen Sie, ob die Synchronisierungszeit mit der Standardkonfiguration akzeptabel ist oder ob eine Verarbeitung mit mehreren Threads erforderlich ist.

- **Reguläre Importe** - Vorwegige regelmäßige Importe, wie Preisaktualisierungen oder Änderungen des Lagerstatus. Überprüfen Sie, ob diese Aktualisierungen innerhalb eines akzeptablen Zeitrahmens angewendet werden können oder ob eine schnellere Verarbeitung erforderlich ist.

- **Produktgewicht** - Überlegen Sie, ob Ihre Produkte leicht oder schwer sind. Passen Sie die Stapelgröße entsprechend an, wenn Produktbeschreibungen oder Attribute die Produktgröße erhöhen.

Beachten Sie, dass eine sorgfältige Planung, einschließlich der Schätzung des Datenvolumens und der Synchronisierungszeit, häufig die Notwendigkeit einer Anpassung eliminieren kann. Planen Sie auf Grundlage dieser Schätzungen Vorgängen zur Feed-Erfassung, um optimale Ergebnisse zu erzielen.

>[!NOTE]
>
>Adobe empfiehlt, bei der Verarbeitung mehrerer Threads Vorsicht walten zu lassen. Diese Funktion ist eine Funktion für frühzeitigen Zugriff, die noch verbessert wird. Wenn Sie mehrere Threads konfigurieren, um die Leistung zu beschleunigen, können Sie die in Adobe Commerce Services enthaltenen Limits nutzen, um Systemmissbrauch bei der Datenerfassung zu verhindern. Diese Limits hindern Benutzer auch daran, Synchronisierungsänderungen auszulösen, die das System überlasten können. Wenn die Limits ausgelöst werden, werden die Anfragen blockiert und das System gibt 429 Fehler zurück. Wenn diese Fehler auftreten, passen Sie Ihre Konfiguration an und senden Sie ein Support-Ticket für Unterstützung.

## Multithreading konfigurieren

Der Multi-Thread-Modus wird für alle [Synchronisierungsmethoden](data-synchronization.md#synchronization-process) unterstützt - vollständige Synchronisierung, teilweise Synchronisierung und Synchronisation fehlgeschlagener Elemente. Um die Multithreading-Funktion zu konfigurieren, geben Sie die Anzahl der Threads und die Stapelgröße an, die bei der Synchronisierung verwendet werden sollen.

- `threadCount` ist die Anzahl der Threads, die für Prozessentitäten aktiviert sind. Der Standardwert `threadCount` ist `1`.
- `batchSize` ist die Anzahl der Entitäten, die in einer Iteration verarbeitet werden. Der Standardwert `batchSize` ist `100` -Datensätze für alle Feeds außer dem Preis-Feed. Für den Preis-Feed ist der Standardwert `500` Datensätze.

Sie können Multi-Threading als temporäre Option konfigurieren, wenn Sie einen Resync-Befehl ausführen, oder indem Sie die Multi-Thread-Konfiguration zur Adobe Commerce-Anwendungskonfiguration hinzufügen.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie die Leistung des SAAS-Datenexports mit der für einen Kunden auf der Verbraucherseite definierten Ratenbegrenzung abstimmen.

### Multithreading zur Laufzeit konfigurieren

Wenn Sie einen vollständigen Synchronisierungsbefehl über die Befehlszeile ausführen, geben Sie die Verarbeitung mit mehreren Threads an, indem Sie die Optionen `threadCount` und `batchSize` zum CLI-Befehl hinzufügen.

```
bin/magento saas:resync --feed=products --threadCount=2 --batchSize=200
```

Die in der Befehlszeile angegebenen Optionen überschreiben die in der Datei mit der Adobe Commerce-Anwendung `config.php` angegebene Datenexportkonfiguration.

### Hinzufügen von Multithreading zur Commerce-Konfiguration

Um alle Datenexportvorgänge mit Multithreading zu verarbeiten, können Systemintegratoren oder Entwickler die Anzahl der Threads und die Batch-Größe für jeden Feed in der Commerce-Anwendungskonfiguration ändern.

Diese Änderungen können angewendet werden, indem benutzerdefinierte Werte zum [Systemabschnitt](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) der Konfigurationsdatei `app/etc/config.php` hinzugefügt werden.

**Beispiel: Multithreading für Produkte und Preise konfigurieren**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
