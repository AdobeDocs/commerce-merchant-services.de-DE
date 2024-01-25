---
title: Onboarding und Installation
description: "Erfahren Sie, wie Sie installieren [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: d02ffe4028bdf5765fb0f23fd210f398729bee62
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Onboarding und Installation

Die folgenden Videos führen Sie durch die [!DNL Catalog Service] -Prozess.

**Teil 1**: Onboarding und Installieren

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Teil 2**: Verwenden Sie die [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## Voraussetzungen

Onboarding-Prozess für [!DNL Catalog Service] erfordert Zugriff auf die Befehlszeile des Servers. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

**Softwareanforderungen**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Verfasser: 2.x

**Unterstützte Plattformen**

- Adobe Commerce für Cloud-Infrastruktur: 2.4.4+
- Adobe Commerce vor Ort: 2.4.4+

>[!ENDSHADEBOX]

## Endpunkte

[!DNL Catalog Service] verfügt über zwei Endpunkte, die für das Onboarding verfügbar sind:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`) - wird vor der Live-Schaltung zum Testen und Validieren verwendet
- Produktion (`https://catalog-service.adobe.io/graphql`) - wird für Live-Traffic für Commerce-Händler und Websites verwendet

Alle Testinstanzen von Commerce sollten den Sandbox-Endpunkt verwenden.

Ladetests sollten nur am Sandbox-Endpunkt durchgeführt werden. Es wird empfohlen, dass ein [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) beim Laden geöffnet werden, damit das Services-Team den zusätzlichen Server-Traffic vorhersehen kann.

## Installation und Konfiguration

Erste Schritte mit [!DNL Catalog Service] Für Adobe Commerce sind die folgenden Schritte erforderlich:

- Installieren der Datenexport-Erweiterungen
- Dienst und Datenexport konfigurieren
- Zugriff auf den Dienst

### Installieren der Datenexport-Erweiterungen

Onboarding-Prozess für [!DNL Catalog Service] erfordert Zugriff auf die Befehlszeile des Servers.

Die [!DNL Catalog Service] -Erweiterung kann sowohl auf der Adobe Commerce-Cloud-Infrastruktur als auch auf lokalen Instanzen installiert werden.

Die [!DNL Catalog Service] wird mit Composer-Schlüsseln installiert, die mit dem Commerce-Konto verknüpft sind. [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) während des Anmeldeprozesses bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der Erstinstallation von Adobe Commerce oder in Situationen, in denen die Composer-Schlüssel zuvor nicht in einem externen Ordner gespeichert wurden `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

#### Adobe Commerce auf Cloud-Infrastruktur

Verwenden Sie diese Methode, um die [!DNL Catalog Service] -Erweiterung für eine Commerce Cloud-Instanz.

1. Wechseln Sie auf Ihrer lokalen Workstation zum Projektverzeichnis.
1. Fügen Sie das Modul Catalog Service hinzu.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Aktualisieren Sie Package-Abhängigkeiten.

   ```bash
   composer update
   ```

1. Änderungen am Zustimmungs- und Push-Code für die `composer.json` und `composer.lock` -Dateien.

#### Vor Ort

Verwenden Sie diese Methode, um die [!DNL Catalog Service] Erweiterung für eine lokale Instanz.

1. Verwenden Sie Composer, um Ihrem Projekt das Catalog Service-Modul hinzuzufügen:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

### Dienst und Datenexport konfigurieren

Nach der Installation [!DNL Catalog Service], müssen Sie die [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) durch Angabe der API-Schlüssel und Auswahl eines SaaS-Datenspeichers.

Nachdem die SaaS-Konfiguration abgeschlossen ist, führen Sie eine erste Datensynchronisation durch, indem Sie der [Katalogsynchronisierung](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) Handbuch.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- Bestätigen Sie, dass Cron-Aufträge ausgeführt werden.
- Überprüfen Sie, ob die Indexer ausgeführt werden.
- Stellen Sie sicher, dass `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, und `Product Variant Feed` Indexer sind auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt.

Die anfängliche Synchronisation kann abhängig von der Kataloggröße einige Minuten bis Stunden dauern. Nach der ersten Synchronisierung exportiert der Katalog laufend Produktdaten vom Commerce-Server in Commerce-Dienste, um die Dienste auf dem neuesten Stand zu halten.

### Zugriff auf den Dienst

Die [!DNL Catalog Service] Auf die API kann über POST-Befehle über HTTPS zugegriffen werden.

Um den API-Schlüssel zu erhalten, wechseln Sie im Admin zum Bereich Commerce Service Connector und kopieren Sie den öffentlichen API-Schlüssel.

Lesen Sie die [GraphQL-Dokumentation](https://developer.adobe.com/commerce/services/graphql/) , um zu verstehen, wie Sie die Header abfragen und senden, die zum Generieren von API-Anfragen erforderlich sind.

In [!DNL Catalog Service] durch eine Firewall hinzufügen `commerce.adobe.io` in die Zulassungsliste.

## Catalog Service und API-Mesh

Die [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe IO private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

Siehe [[!DNL Catalog Service] und API-Mesh](mesh.md) Thema für die Installation und Konfiguration.
