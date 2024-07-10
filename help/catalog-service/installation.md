---
title: Onboarding und Installation
description: "Erfahren Sie, wie Sie installieren [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 6ca91feefbfc2fbc4d5851040b9f1ca3de6a6560
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Onboarding und Installation

Installieren Sie den Katalogdienst , um Produktdaten von einer Commerce-Instanz mit der [Catalog Service GraphQL-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/). Der Catalog Service wird als Composer-Metapaket vom repo.magento.com Repository bereitgestellt.

>[!NOTE]
>
>Wenn Ihre Commerce-Instanz die Live Search- oder Produkt-Recommendations verwendet, wird der Katalogdienst automatisch installiert oder aktualisiert, wenn Sie diese Dienste integrieren oder aktualisieren. Weitere Informationen finden Sie in den Installationsanweisungen für [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) und [Produkt-Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



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

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`) - wird vor der Live-Schaltung zum Testen und Validieren verwendet
- Produktion (`https://catalog-service.adobe.io/graphql`) - wird für Live-Traffic für Commerce-Händler und -Websites verwendet

Alle Commerce-Testinstanzen verwenden den Sandbox-Endpunkt.

Führen Sie alle Belastungstests für den Sandbox-Endpunkt durch. Bevor Sie mit dem Laden beginnen, senden Sie eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) damit das Services-Team den zusätzlichen Server-Traffic vorhersehen kann.

## Installation und Konfiguration

Erste Schritte mit [!DNL Catalog Service] Für Adobe Commerce sind die folgenden Schritte erforderlich:

- Installieren Sie die Catalog Service-Erweiterung (`magento/catalog-service`)
- Dienst und Datenexport konfigurieren
- Zugriff auf den Dienst

### Installieren der Catalog Service-Erweiterung

>[!BEGINSHADEBOX]

**Voraussetzung**

- Zugriff [repo.magento.com](https://repo.magento.com) , um die Erweiterung zu installieren. Informationen zur Schlüsselgenerierung und zum Erhalt der erforderlichen Berechtigungen finden Sie unter [Abrufen der Authentifizierungsschlüssel](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Informationen zu Cloud-Installationen finden Sie unter [Handbuch zu Commerce on Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Zugriff auf die Befehlszeile des Adobe Commerce-Anwendungsservers.

>[!ENDSHADEBOX]

Installieren Sie die neueste Version der Catalog Services-Erweiterung (`magento/catalog-service`) auf einer Adobe Commerce-Instanz, auf der Adobe Commerce-Version 2.4.4 oder höher ausgeführt wird. Der Katalogdienst wird als Composer-Metapaket aus dem [repo.magento.com](https://repo.magento.com) Repository.

>[!BEGINTABS]

>[!TAB Cloud-Infrastruktur]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine Commerce Cloud-Instanz.

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

1. Änderungen am Zustimmungs- und Push-Code für die `composer.json` und `composer.lock` -Dateien.

1. Fügen Sie die Codeänderungen für die `composer.json` und `composer.lock` -Dateien in die Cloud-Umgebung.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Wenn Sie die Aktualisierungen in die Cloud-Umgebung pushen, wird die [Commerce Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) , um die Änderungen anzuwenden. Überprüfen Sie den Bereitstellungsstatus im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Vor Ort]

Verwenden Sie diese Methode, um die [!DNL Catalog Service] für eine örtliche Instanz.

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

Nach der Installation [!DNL Catalog Service]Führen Sie die folgenden Aufgaben aus, um den Catalog Service in Ihre Adobe Commerce-Instanz zu integrieren. Diese Integration ermöglicht die Datensynchronisation und Kommunikation zwischen der Commerce-Instanz, dem Catalog Service und anderen unterstützenden Diensten.

1. Richten Sie die [Commerce Services Connector](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) durch Angabe der API-Schlüssel und Auswahl eines SaaS-Datenspeichers.

   Die Einrichtung des Commerce Services Connector ist ein einmaliger Prozess, der für die Verwendung von Adobe Commerce-Diensten wie dem Katalogdienst, der Live-Suche und der Produkt-Recommendations erforderlich ist. Wenn Sie den Connector bereits für einen anderen Dienst konfiguriert haben, überspringen Sie diesen Schritt.

1. Führen Sie eine erste Datensynchronisierung über die [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   Die anfängliche Synchronisation kann abhängig von der Kataloggröße einige Minuten bis Stunden dauern. Sie können den Synchronisierungsstatus im Data Management-Dashboard überwachen. Nach der ersten Synchronisierung exportiert der Katalog laufend Produktdaten, um die Dienste auf dem neuesten Stand zu halten.

   >[!NOTE]
   >
   >Sie können die Erstsynchronisierung auch über die Befehlszeile mit der Commerce-CLI starten. Siehe [Erstsynchronisierung](../data-export/data-export-cli-commands.md#initial-sync) im _SaaS-Datenexportanleitung_.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- [Überprüfen, ob Cron-Aufträge ausgeführt werden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Stellen Sie sicher, dass die Indexer von der [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) oder mithilfe des Commerce-CLI-Befehls `bin/magento indexer:info`.
- Stellen Sie sicher, dass `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, und `Product Variant Feed` Indexer werden auf `Update by Schedule`.

### Zugriff auf den Dienst

Die [!DNL Catalog Service] Auf die GraphQL-API kann über die ` https://catalog-service.adobe.io/graphql` -Endpunkt mit POST-Befehlen über HTTPS.

In Ihren GraphQL-Abfragen müssen Sie mehrere HTTP-Header angeben, einschließlich des öffentlichen API-Schlüssels, den Sie in der Admin-Konfiguration von Adobe Commerce Services Connector hinzugefügt haben. Weitere Informationen finden Sie unter [Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) Dokumentation.

### Firewall-Konfiguration

In [!DNL Catalog Service] durch eine Firewall hinzufügen `commerce.adobe.io` in die Zulassungsliste.

## Catalog Service und API-Mesh

Die [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe IO private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

Siehe [[!DNL Catalog Service] und API-Mesh](mesh.md) Thema für die Installation und Konfiguration.

## Data Management Dashboard

Weitere Informationen finden Sie unter [!DNL Catalog Service] Datensynchronisation, siehe [Data Management Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
