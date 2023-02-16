---
title: Onboarding und Installation
description: Erfahren Sie, wie Sie installieren [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 242060d94700efc018a520d2d680c0f47a0cb915
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Onboarding und Installation

Sehen Sie sich eine exemplarische Vorgehensweise zum Catalog Service-Prozess an.

Teil 1:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

Teil 2:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## Voraussetzungen

Onboarding-Prozess für [!DNL Catalog Service] erfordert Zugriff auf die Befehlszeile des Servers. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

### Softwareanforderungen

- Adobe Commerce 2.4.x
- PHP 8.1
- Verfasser: 2.x

### Unterstützte Plattformen

- Adobe Commerce über Cloud-Infrastruktur: 2.4.x
- Adobe Commerce vor Ort: 2.4.x

## Umgebungen

Catalog Service verfügt über zwei Umgebungen, die für das Onboarding verfügbar sind:

- Sandbox (https://catalog-service-sandbox.adobe.io/graphql) - wird zum Testen und Validieren vor der Live-Schaltung verwendet
- Produktion (https://catalog-service.adobe.io/graphql)- für Live-Traffic für Commerce-Händler und Websites verwendet

## Installation und Konfiguration

Um mit dem Catalog Service für Adobe Commerce zu beginnen, sind die folgenden Schritte erforderlich:

- Installieren der Datenexport-Erweiterungen
- Dienst und Datenexport konfigurieren
- Zugriff auf den Dienst

### Installieren der Datenexport-Erweiterungen

Der Integrationsprozess für Catalog Service erfordert Zugriff auf die Befehlszeile des Servers.

Die Catalog Service-Erweiterung kann sowohl auf der Adobe Commerce-Cloud-Infrastruktur als auch auf lokalen Instanzen installiert werden.

Der Catalog Service wird mit Composer-Schlüsseln installiert, die mit dem Commerce-Konto verknüpft sind [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) während des Anmeldeprozesses bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der Erstinstallation von Adobe Commerce oder in Situationen, in denen die Composer-Schlüssel zuvor nicht in einem externen Ordner gespeichert wurden `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

#### Adobe Commerce auf Cloud-Infrastruktur

Verwenden Sie diese Methode zum Installieren der Catalog Service-Erweiterung für eine Commerce Cloud-Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` in einem Texteditor erstellen und den erforderlichen Abschnitt wie folgt aktualisieren:

```json
"require": {
  "magento/catalog-service": "^1.0.2"
}
```

1. Testen Sie die neue Konfiguration lokal und aktualisieren Sie Abhängigkeiten:

```bash
composer update
```

Der Befehl aktualisiert alle Abhängigkeiten.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie für `composer.json` und `composer.lock`.

#### Vor Ort

Verwenden Sie diese Methode zum Installieren der Catalog Service-Erweiterung für eine lokale Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` in einem Texteditor erstellen und den erforderlichen Abschnitt wie folgt aktualisieren:

```json
"require": {
    "magento/catalog-service": "^1.0.2"
}
```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

```bash
composer update
```

Der Befehl aktualisiert alle Abhängigkeiten.

1. Upgrade von Adobe Commerce:

```bash
bin/magento setup:upgrade
```

1. Löschen Sie den Cache:

```bash
bin/magento cache:clean
```

### Dienst und Datenexport konfigurieren

Nach der Installation von Catalog Service müssen Sie die [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) durch Angabe der API-Schlüssel und Auswahl eines SaaS-Datenspeichers.

Nachdem die SaaS-Konfiguration abgeschlossen ist, führen Sie eine erste Datensynchronisation durch, indem Sie der [Katalogsynchronisierung](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) Handbuch.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- Vergewissern Sie sich, dass Cron-Aufträge ausgeführt werden.
- Überprüfen Sie, ob die Indexer ausgeführt werden.
- Stellen Sie sicher, dass `Catalog Attributes Feed, Product Feed, Product Overrides Feed`und `Product Variant Feed` Indexer sind auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt.

Die anfängliche Synchronisation kann abhängig von der Kataloggröße einige Minuten bis Stunden dauern. Nach der ersten Synchronisierung exportiert der Katalog laufend Produktdaten vom Commerce-Server in Commerce-Dienste, um die Dienste auf dem neuesten Stand zu halten.

### Zugriff auf den Dienst

Auf die Catalog Service-API kann über POST-Befehle über HTTPS zugegriffen werden.

Um den API-Schlüssel zu erhalten, wechseln Sie im Admin zum Bereich Commerce Service Connector und kopieren Sie den öffentlichen API-Schlüssel.

Lesen Sie die [GraphQL-Dokumentation](https://developer.adobe.com/commerce/webapi/graphql/) , um zu verstehen, wie Sie die Header abfragen und senden, die zum Generieren von API-Anfragen erforderlich sind.

## Catalog Service und API-Mesh

Die [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe IO private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

Siehe  [Catalog Service und API-Mesh](mesh.md) Thema für Installations- und Konfigurationsdetails.
