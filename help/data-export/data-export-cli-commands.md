---
title: Befehlszeilenschnittstelle für den SAAS-Datenexport
description: "Erfahren Sie, wie Sie die Befehlszeilenschnittstelle verwenden, um Feeds und Prozesse für die [!DNL data export extension] für Adobe Commerce SaaS-Dienste."
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Befehlszeilenschnittstelle für den SAAS-Datenexport

Entwickler und Systemadministratoren können Synchronisierungsvorgänge für den SaaS-Datenexport mithilfe des [Adobe Commerce-Befehlszeilen-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI). Die `saas:resync` -Befehl ist im `magento/saas-export` Paket.

Adobe rät von der Verwendung der `saas:resync` regulären Befehl. Typische Szenarien für die Verwendung des Befehls sind:

- Die erste Synchronisierung
- Die [SaaS-Datenraum-ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) geändert wurde und Sie Daten mit dem neuen Datenraum synchronisieren müssen.
- Fehlerbehebung

## Erstsynchronisierung

Beim Trigger eines `saas:resync` über die Befehlszeile kann es je nach Größe Ihres Katalogs einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

>[!NOTE]
>Wenn Sie Live Search oder Product Recommendations verwenden, müssen Sie die Synchronisierung nicht initiieren. Der Prozess wird automatisch ausgelöst, nachdem Sie den Dienst mit Ihrer Commerce-Instanz verbunden haben.

## Befehlsbeispiele

Vor der Verwendung `saas:resync` -Befehle, überprüfen Sie die [Optionsbeschreibungen](#command-options).

- Führen Sie eine vollständige Neusynchronisierung für einen Entitäts-Feed durch.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Feeds, die bereits erfolgreich exportiert wurden, werden nicht erneut synchronisiert.

- Vollständige Neusynchronisierung der angegebenen Feed- und Bereinigungsdaten

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Verwenden Sie dies nur nach dem Ausführen von [!DNL Data Space ID Cleanup] Vorgang.

- Senden Sie bei sofortigem Export von Feeds alle Daten erneut an verbundene Commerce-Dienste, ohne die Indexdaten in der Feed-Tabelle abzuschneiden.

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Auflisten der verfügbaren Befehle und Optionen mit Beschreibungen.

  ```
  bin/magento saas:resync --help
  ```

## Befehlsoptionen

Die folgenden Optionen stehen zur Verwaltung von `saas:resync` Vorgänge.

>[!NOTE]
>
>Die `saas:resync` unterstützt außerdem erweiterte Optionen zur Verbesserung von Datenexportbefehlen durch Vergrößerung der Stapelgröße und Hinzufügen der Verarbeitung mehrerer Threads. Siehe [Exportverarbeitung anpassen](customize-export-processing.md).

### `feed`

Diese erforderliche Option gibt an, welche Feed-Entität neu synchronisiert werden soll, z. B. `products`.

Die `feed` Der Optionswert kann jeden der verfügbaren Entitäts-Feeds umfassen:

- `products`: Produktdaten-Feed
- `productAttributes`: Produktattribut-Daten-Feed
- `categories`: Kategoriedaten-Feed
- `variants`: konfigurierbarer Daten-Feed für Produktvarianten
- `prices`: Produktpreisdatenfeed
- `categoryPermissions`: Datenfeed für Kategorieberechtigungen
- `productOverrides`: Produktberechtigungsdaten-Feed
- `inventoryStockStatus`: Bestandsstatusdaten-Feed
- `scopesWebsite`: Websites mit Datenfeed für Stores und Store-Ansichten
- `scopesCustomerGroup`: Datenfeed für Kundengruppen
- `orders`: Daten-Feed für Verkaufsaufträge

Je nach [Commerce Services](../landing/saas.md) installiert sind, stehen Ihnen möglicherweise andere Feeds zur Verfügung für `saas:resync` Befehl.

### `no-reindex`

Diese Option sendet die vorhandenen Katalogdaten erneut an [!DNL Commerce Services] ohne Neuindizierung. Wenn diese Option nicht angegeben ist, führt der Befehl vor der Synchronisierung der Daten eine vollständige Neuindizierung durch.

Das Verhalten dieser Option hängt davon ab, ob der Feed exportiert wird in [Legacy- oder sofortiger Exportmodus](data-synchronization.md#synchronization-modes)

- Bei Legacy-Export-Feeds schneidet der Synchronisierungsprozess die indizierten Daten in der Feeds-Tabelle nicht ab. Stattdessen werden alle Daten an den Adobe Commerce-Dienst weitergeleitet.
- Bei sofortigen Export-Feeds wird diese Option ignoriert, wenn sie angegeben wird. Bei diesen Feeds schneidet der Synchronisierungsprozess den Index nicht ab und synchronisiert nur Aktualisierungen oder Elemente, die zuvor fehlgeschlagen waren, neu.

### `cleanup`

Diese Option bereinigt die Feed-Indexer-Tabelle vor einer Synchronisierung. Wenn angegeben, führt der SaaS-Datenexport eine vollständige Neusynchronisierung für den angegebenen Feed aus und bereinigt alle vorhandenen Daten in der Feed-Tabelle.

Adobe empfiehlt die Verwendung dieses Befehls erst nach Ausführung der [!DNL Data Space ID Cleanup] Vorgang.

>[!WARNING]
>
>**Verwenden Sie diese Option nicht regelmäßig**. Dies kann zu Problemen bei der Datensynchronisierung in Adobe Commerce Services führen. Beispiel: die `delete product event` wird möglicherweise nicht an den Adobe Commerce-Dienst weitergeleitet, wenn die Variable `cleanup` verwendet.

## Fehlerbehebung

Wenn die erwarteten Daten in den verbundenen Commerce Services nicht angezeigt werden, beheben Sie Probleme, indem Sie die Fehlerprotokolle für den Datenexport überprüfen und die `saas:resync` -Befehl mit Umgebungsvariablen zum Überprüfen von Payloads und Profilerdaten. Siehe [Protokolle überprüfen und Fehlerbehebung](troubleshooting-logging.md).
