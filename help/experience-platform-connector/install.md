---
title: Installieren von Adobe Experience Platform Connector
description: Erfahren Sie, wie Sie den Adobe Experience Platform Connector von Adobe Commerce installieren, aktualisieren und deinstallieren.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 24494546d6d21cf46e3cb9f0fdd503ec8007daf8
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Installieren des Adobe Experience Platform Connectors

Vor der Installation der Erweiterung [Voraussetzungen überprüfen](overview.md#prereqs).

## Installieren der Erweiterung

Die Experience Platform-Connector-Erweiterung ist über das [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Wenn Sie diese Erweiterung über die Befehlszeile des Servers installieren, stellt sie eine Verbindung zu Ihrer Adobe Commerce-Installation als [service](../landing/saas.md). Wenn der Prozess abgeschlossen ist, **Experience Platform-Connector** und **Commerce Services Connector** auf der **System** Menü unter **Dienste** im Handel _Admin_.

>[!NOTE]
>
>![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler gibt es eine separate Erweiterung, die Sie installieren müssen. Diese Erweiterung unterstützt jetzt auch B2B-spezifische Ereignisse. [Weitere Infos](#install-the-b2b-extension).

1. So laden Sie die `experience-platform-connector` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   * `module-experience-connector-admin` - Aktualisiert die Admin-Benutzeroberfläche, sodass Sie die Datastream-ID für eine bestimmte Adobe Commerce-Instanz auswählen können.
   * `module-experience-connector` - Legt die `Organization ID` und `datastreamId` im Storefront Events SDK.
   * `data-services` - Stellt Attributkontext für Storefront-Ereignisse bereit. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.
   * `services-id` - Verbinden Sie Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) Verwendung von Sandbox- und Produktions-API-Schlüsseln sowie zum Abrufen der IMS-Organisations-ID in Adobe Experience Platform.
   * `orders-connector` - Verbindet den Auftragsstatus-Dienst mit Ihrer Adobe Commerce-Instanz.

1. (Optional) Einbeziehen [!DNL Live Search] Daten, die [Suchereignisse](events.md#search-events), installieren Sie die [[!DNL Live Search]](../live-search/install.md) -Erweiterung.

### Konfigurieren des Auftrags-Connectors

Nach der Installation `experience-platform-connector`, müssen Sie die Installation der `orders-connector` -Modul basierend auf dem Bereitstellungstyp: lokal oder Adobe Commerce auf Cloud-Infrastruktur.

#### Vor Ort

In lokalen Umgebungen müssen Sie die Codegenerierung und Adobe Commerce-Ereignisse manuell aktivieren:

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### Über die Cloud-Infrastruktur

Aktivieren Sie in der Cloud-Infrastruktur von Adobe Commerce die `ENABLE_EVENTING` globale Variable in `.magento.env.yaml`. [Weitere Infos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Übernehmen und pushen Sie aktualisierte Dateien in die Cloud-Umgebung. Wenn die Bereitstellung abgeschlossen ist, aktivieren Sie das Senden von Ereignissen mit dem folgenden Befehl:

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Installieren der B2B-Erweiterung

Installieren Sie für B2B-Händler die folgende Erweiterung, um [Anforderungsliste](events.md#b2b-events) Ereignisdaten.

Laden Sie die `magento/experience-platform-connector-b2b` -Erweiterung durch Ausführen der folgenden Aktionen über die Befehlszeile:

```bash
composer require magento/experience-platform-connector-b2b
```

## Experience Platform-Connector aktualisieren {#update}

Um den Experience Platform-Connector zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

B2B-Händler:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Um auf eine Hauptversion wie 2.0.0 auf 3.0.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

1. Öffnen Sie den Stamm `composer.json` Datei und suchen Sie nach `magento/experience-platform-connector`.

1. Im `require` aktualisieren Sie die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   B2B-Händler:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Deinstallieren des Experience Platform-Connectors {#uninstall}

Informationen zum Deinstallieren des Experience Platform-Connectors finden Sie unter [Deinstallationsmodule](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
