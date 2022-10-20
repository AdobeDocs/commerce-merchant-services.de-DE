---
title: Installieren und Konfigurieren von Adobe Experience Platform Connector von Adobe Commerce
description: Erfahren Sie, wie Sie den Adobe Experience Platform Connector von Adobe Commerce installieren, konfigurieren, aktualisieren und deinstallieren.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: bd1cf8a3b4740594cf6b8678d899d771a886cb2e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Installieren und Konfigurieren des Experience Platform Connectors

Vor der Installation der Erweiterung [Voraussetzungen überprüfen](overview.md#prereqs).

## Installieren der Erweiterung

Die Experience Platform Connector-Erweiterung wird über die Befehlszeile des Servers installiert und stellt eine Verbindung zu Ihrer Adobe Commerce-Installation als [service](../landing/saas.md). Wenn der Prozess abgeschlossen ist, **Experience Platform Connector** wird auf der **System** Menü unter **Dienste** im Handel _Admin_.

Der Experience Platform Connector wird als Erweiterung von [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html).

1. So laden Sie die `experience-platform-connector` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   * `module-platform-connector-admin` - Aktualisiert die Admin-Benutzeroberfläche, sodass Sie die Datastraam-ID für eine bestimmte Adobe Commerce-Instanz auswählen können.
   * `module-platform-connector` - Legt die `Organization ID` und `datastreamId` im Storefront Events SDK
   * `data-services` - Stellt Attributkontext für Storefront-Ereignisse bereit. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.
   * `services-id` - Verbinden Sie Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) Verwenden von Sandbox- und Produktions-API-Schlüsseln und zum Adobe Experience Platform zum Abrufen der IMS-Organisations-ID

1. (Optional) Einbeziehen [!DNL Live Search] -Daten, die Suchereignisse enthalten, installieren Sie die [[!DNL Live Search]](../live-search/install.md) -Erweiterung.

## Experience Platform Connector aktualisieren {#update}

Um den Experience Platform-Connector zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Um auf eine Hauptversion wie 1.0.0 auf 2.0.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

1. Öffnen Sie den Stamm. `composer.json` Datei und suchen Sie nach `magento/platform-connector`.

1. Im `require` aktualisieren Sie die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

## Experience Platform Connector deinstallieren {#uninstall}

Informationen zum Deinstallieren des Experience Platform Connectors finden Sie unter [Deinstallationsmodule](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
