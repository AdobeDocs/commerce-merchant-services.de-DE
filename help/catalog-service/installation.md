---
title: Onboarding und Installation
description: "Erfahren Sie, wie Sie [!DNL Catalog Service] installieren."
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 0b0bc88c13d8c90a6209d9156f6fd6a7ce040f72
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Onboarding und Installation

Installieren Sie den Catalog Service , um mithilfe der [Catalog Service GraphQL API](https://developer.adobe.com/commerce/services/graphql/catalog-service/) Produktdaten von einer Commerce-Instanz anzufordern und zu empfangen. Der Catalog Service wird als Composer-Metapaket vom repo.magento.com Repository bereitgestellt.

>[!NOTE]
>
>Wenn Ihre Commerce-Instanz die Live Search- oder Produkt-Recommendations verwendet, wird der Katalogdienst automatisch installiert oder aktualisiert, wenn Sie diese Dienste integrieren oder aktualisieren. Weitere Informationen finden Sie in den Installationsanweisungen für [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) und [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## Systemanforderungen

**Softwareanforderungen**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3
- Verfasser: 2.x

**Unterstützte Plattformen**

- Adobe Commerce für Cloud-Infrastruktur: 2.4.4+
- Adobe Commerce vor Ort: 2.4.4+

## Endpunkte

[!DNL Catalog Service] verfügt über zwei Endpunkte, die für das Onboarding verfügbar sind:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`), die vor der Live-Schaltung zum Testen und Validieren verwendet wird
- Produktion (`https://catalog-service.adobe.io/graphql`) - für Live-Traffic für Commerce-Händler und -Websites verwendet

Alle Commerce-Testinstanzen verwenden den Sandbox-Endpunkt.

Führen Sie alle Belastungstests für den Sandbox-Endpunkt durch. Bevor Sie mit dem Laden beginnen, senden Sie ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), damit das Services-Team den zusätzlichen Server-Traffic vorhersehen kann.

## Installation und Konfiguration

Um mit [!DNL Catalog Service] für Adobe Commerce zu beginnen, sind die folgenden Schritte erforderlich:

- Installieren Sie die Catalog Service-Erweiterung (`magento/catalog-service`)
- Dienst und Datenexport konfigurieren
- Zugriff auf den Dienst

### Installieren der Catalog Service-Erweiterung

>[!BEGINSHADEBOX]

**Voraussetzung**

- Rufen Sie [repo.magento.com](https://repo.magento.com) auf, um die Erweiterung zu installieren. Informationen zur Schlüsselgenerierung und zum Abrufen der erforderlichen Berechtigungen finden Sie unter [Abrufen Ihrer Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Informationen zu Cloud-Installationen finden Sie im [Commerce on Cloud Infrastructure Guide](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Zugriff auf die Befehlszeile des Adobe Commerce-Anwendungsservers.

>[!ENDSHADEBOX]

Installieren Sie die neueste Version der Catalog Services-Erweiterung (`magento/catalog-service`) auf einer Adobe Commerce-Instanz, auf der Adobe Commerce-Version 2.4.4 oder höher ausgeführt wird. Der Catalog Service wird als Composer-Metapaket vom Repository [repo.magento.com](https://repo.magento.com) bereitgestellt.

>[!BEGINTABS]

>[!TAB Cloud-Infrastruktur]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine Commerce Cloud-Instanz zu installieren.

1. Wechseln Sie auf Ihrer lokalen Workstation zum Projektverzeichnis für Ihr Adobe Commerce-Projekt in der Cloud-Infrastruktur-Projekt.

   >[!NOTE]
   >
   >Informationen zum lokalen Verwalten von Commerce-Projektumgebungen finden Sie unter [Verwalten von Verzweigungen mit der CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) im _Benutzerhandbuch zu Adobe Commerce on Cloud Infrastructure_.

1. Sehen Sie sich die Umgebungsverzweigung an, die mit der Adobe Commerce Cloud-CLI aktualisiert werden soll.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Fügen Sie das Modul Catalog Service hinzu.

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Aktualisieren Sie Package-Abhängigkeiten.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Übernehmen und pushen Sie Code-Änderungen für die Dateien `composer.json` und `composer.lock`.

1. Fügen Sie die Codeänderungen für die Dateien `composer.json` und `composer.lock` hinzu, übertragen Sie sie und übertragen Sie sie in die Cloud-Umgebung.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Durch das Übermitteln der Aktualisierungen an die Cloud-Umgebung wird der [Commerce-Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) initiiert, um die Änderungen anzuwenden. Überprüfen Sie den Bereitstellungsstatus im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-premise]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine lokale Instanz zu installieren.

1. Verwenden Sie Composer, um Ihrem Projekt das Catalog Service-Modul hinzuzufügen:

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In einigen Fällen, insbesondere bei der Bereitstellung in der Produktionsumgebung, sollten Sie das Löschen von kompiliertem Code vermeiden, da dies einige Zeit in Anspruch nehmen kann. Stellen Sie sicher, dass Sie Ihr System sichern, bevor Sie Änderungen vornehmen.

>[!ENDTABS]

### Dienst und Datenexport konfigurieren

Führen Sie nach der Installation von [!DNL Catalog Service] die folgenden Schritte aus, um den Catalog-Dienst in Ihre Adobe Commerce-Instanz zu integrieren. Diese Integration ermöglicht die Datensynchronisation und Kommunikation zwischen der Commerce-Instanz, dem Catalog Service und anderen unterstützenden Diensten. Die Datensynchronisation wird von der [SAAS-Datenexport-Erweiterung](../data-export/overview.md) durchgeführt.

1. Richten Sie den [Commerce Services Connector](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) ein, indem Sie die API-Schlüssel angeben und einen SaaS-Datenraum auswählen.

   Die Einrichtung des Commerce Services Connector ist ein einmaliger Prozess, der für die Verwendung von Adobe Commerce-Diensten wie dem Katalogdienst, der Live-Suche und der Produkt-Recommendations erforderlich ist. Wenn Sie den Connector bereits für einen anderen Dienst konfiguriert haben, überspringen Sie diesen Schritt.

1. Führen Sie eine erste Datensynchronisation über das [Daten-Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) durch.

   Die anfängliche Synchronisation kann abhängig von der Kataloggröße einige Minuten bis Stunden dauern. Sie können den Synchronisierungsstatus im Data Management-Dashboard überwachen. Nach der ersten Synchronisierung exportiert der Katalog laufend Produktdaten, um die Dienste auf dem neuesten Stand zu halten.

   >[!NOTE]
   >
   >Sie können die Erstsynchronisierung auch über die Befehlszeile mit der Commerce-CLI starten. Siehe [Erstsynchronisierung](../data-export/data-export-cli-commands.md#initial-sync) im _SAAS-Datenexportleitfaden_.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- [Vergewissern Sie sich, dass Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Stellen Sie sicher, dass die Indexer über den Befehl [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) oder den Commerce-CLI-Befehl `bin/magento indexer:info` ausgeführt werden.
- Stellen Sie sicher, dass die Indexer `Catalog Attributes Feed, Product Feed, Product Overrides Feed` und `Product Variant Feed` auf `Update by Schedule` eingestellt sind.

### Überwachung und Fehlerbehebung bei der Datensynchronisation

Über den Commerce-Administrator können Sie den Synchronisierungsprozess mithilfe des [Daten-Management-Dashboards](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) überwachen. Verwenden Sie die [Commerce-CLI](../data-export/data-export-cli-commands.md#troubleshooting) und Protokolle, um den Prozess zu verwalten und Fehler zu beheben.

### Zugriff auf den Dienst

Der Zugriff auf die GraphQL-API [!DNL Catalog Service] erfolgt über die POST-Befehle über HTTPS vom ` https://catalog-service.adobe.io/graphql` -Endpunkt aus.

In Ihren GraphQL-Abfragen müssen Sie mehrere HTTP-Header angeben, einschließlich des öffentlichen API-Schlüssels, den Sie in der Admin-Konfiguration von Adobe Commerce Services Connector hinzugefügt haben. Weitere Informationen finden Sie in der Dokumentation zu [Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) .

### Firewall-Konfiguration

Um [!DNL Catalog Service] über eine Firewall zuzulassen, fügen Sie `commerce.adobe.io` zur Zulassungsliste hinzu.

## Catalog Service und API-Mesh

Das [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht Entwicklern die Integration von privaten oder Drittanbieter-APIs und anderen Schnittstellen mit Adobe-Produkten mithilfe von Adobe IO.

Informationen zur Installation und Konfiguration finden Sie im Thema [[!DNL Catalog Service] und zum API-Mesh](mesh.md) .

## Data Management Dashboard

Weitere Informationen zur [!DNL Catalog Service] Datensynchronisation finden Sie im [Dashboard &quot;Datenverwaltung&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
