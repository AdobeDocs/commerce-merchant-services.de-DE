---
title: Befehlszeilenschnittstelle für den SAAS-Datenexport
description: Erfahren Sie, wie Sie die Befehlszeilenschnittstelle verwenden, um Feeds und Prozesse für die [!DNL data export extension] für Adobe Commerce SaaS-Dienste zu verwalten.
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Befehlszeilenschnittstelle für den SAAS-Datenexport

Entwickler und Systemadministratoren können Synchronisierungsvorgänge für den SAAS-Datenexport mithilfe des Befehlszeilen-Tools [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) verwalten. Der Befehl `saas:resync` ist im Paket `magento/saas-export` enthalten.

Adobe rät von der regelmäßigen Verwendung des Befehls `saas:resync` ab. Typische Szenarien für die Verwendung des Befehls sind:

- Die erste Synchronisierung
- Die [SaaS-Datenraum-ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) wurde geändert, und Sie müssen Daten mit dem neuen Datenraum synchronisieren.
- Fehlerbehebung

## Erstsynchronisierung

>[!NOTE]
>Wenn Sie Live Search oder Product Recommendations verwenden, müssen Sie die erste Synchronisierung nicht ausführen. Der Prozess wird automatisch ausgelöst, nachdem Sie den Dienst mit Ihrer Commerce-Instanz verbunden haben.

Wenn Sie je nach Kataloggröße einen `saas:resync` aus der Befehlszeile Trigger haben, kann es einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

Für die anfängliche Synchronisierung empfiehlt Adobe, die Befehle in der folgenden Reihenfolge auszuführen:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Befehlsbeispiele

Bevor Sie `saas:resync` -Befehle verwenden, lesen Sie die Beschreibung der [Optionen](#command-options) durch.

- Führen Sie eine vollständige Neusynchronisierung für einen Entitäts-Feed durch.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Feeds, die bereits erfolgreich exportiert wurden, werden nicht erneut synchronisiert.

- Vollständige Neusynchronisierung der angegebenen Feed- und Bereinigungsdaten

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Verwenden Sie dies nur nach dem Ausführen eines [!DNL Data Space ID Cleanup] -Vorgangs.

- Senden Sie bei sofortigem Export von Feeds alle Daten erneut an verbundene Commerce-Dienste, ohne die Indexdaten in der Feed-Tabelle abzuschneiden.

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Auflisten der verfügbaren Befehle und Optionen mit Beschreibungen.

  ```
  bin/magento saas:resync --help
  ```

## Befehlsoptionen

Die folgenden Optionen sind für die Verwaltung von `saas:resync` -Vorgängen verfügbar.

>[!NOTE]
>
>Der Befehl `saas:resync` unterstützt auch erweiterte Optionen zur Verbesserung der Datenexportbefehle durch Vergrößerung der Stapelgröße und Hinzufügen der Verarbeitung mit mehreren Threads. Siehe [Anpassen der Exportverarbeitung](customize-export-processing.md).

### `feed`

Diese erforderliche Option gibt an, welche Feed-Entität neu synchronisiert werden soll, z. B. `products`.

Der Optionswert `feed` kann einen der verfügbaren Entitäts-Feeds enthalten:

- `products`: Produktdaten-Feed
- `productAttributes`: Datenfeed für Produktattribute
- `categories`: Datenfeed für Kategorien
- `variants`: Daten-Feed zu konfigurierbaren Produktvarianten
- `prices`: Datenfeed zu Produktpreisen
- `categoryPermissions`: Datenfeed für Kategorieberechtigungen
- `productOverrides`: Datenfeed für Produktberechtigungen
- `inventoryStockStatus`: Bestandsstatusdaten-Feed
- `scopesWebsite`: Websites mit Stores und Store-Datenfeed für Ansichten
- `scopesCustomerGroup`: Datenfeed für Kundengruppen
- `orders`: Daten-Feed zu Verkaufsbestellungen

Je nachdem, welche [Commerce Services](../landing/saas.md) installiert sind, stehen Ihnen möglicherweise andere Feeds für den Befehl `saas:resync` zur Verfügung.

### `no-reindex`

Mit dieser Option werden die vorhandenen Katalogdaten ohne Neuindizierung an [!DNL Commerce Services] zurückgesendet. Wenn diese Option nicht angegeben ist, führt der Befehl vor der Synchronisierung der Daten eine vollständige Neuindizierung durch.

Das Verhalten dieser Option hängt davon ab, ob der Feed im [alten oder sofortigen Exportmodus exportiert wird ](data-synchronization.md#synchronization-modes)

- Bei Legacy-Export-Feeds schneidet der Synchronisierungsprozess die indizierten Daten in der Feeds-Tabelle nicht ab. Stattdessen werden alle Daten an den Adobe Commerce-Dienst weitergeleitet.
- Bei sofortigen Export-Feeds wird diese Option ignoriert, wenn sie angegeben wird. Bei diesen Feeds schneidet der Synchronisierungsprozess den Index nicht ab und synchronisiert nur Aktualisierungen oder Elemente, die zuvor fehlgeschlagen waren, neu.

### `cleanup`

Diese Option bereinigt die Feed-Indexer-Tabelle vor einer Synchronisierung. Wenn angegeben, führt der SaaS-Datenexport eine vollständige Neusynchronisierung für den angegebenen Feed aus und bereinigt alle vorhandenen Daten in der Feed-Tabelle.

Adobe empfiehlt, diesen Befehl erst nach Ausführung des Vorgangs [!DNL Data Space ID Cleanup] zu verwenden.

>[!WARNING]
>
>**Verwenden Sie diese Option nicht regelmäßig**. Dies kann zu Problemen bei der Datensynchronisierung in Adobe Commerce Services führen. Beispielsweise wird die `delete product event` nicht an den Adobe Commerce-Dienst weitergegeben, wenn die `cleanup` -Option verwendet wird.

## Fehlerbehebung

Wenn die erwarteten Daten in den verbundenen Commerce Services nicht angezeigt werden, beheben Sie Probleme, indem Sie die Fehlerprotokolle für den Datenexport überprüfen und den Befehl `saas:resync` mit Umgebungsvariablen verwenden, um Payloads und Profilerdaten zu überprüfen. Siehe [Überprüfen von Protokollen und Fehlerbehebung](troubleshooting-logging.md).
