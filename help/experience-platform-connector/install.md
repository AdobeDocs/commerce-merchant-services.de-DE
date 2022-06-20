---
title: Installieren und Konfigurieren von Adobe Experience Platform Connector von Adobe Commerce
description: Erfahren Sie, wie Sie den Adobe Experience Platform Connector von Adobe Commerce installieren, konfigurieren, aktualisieren und deinstallieren.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Experience Platform Connector installieren und konfigurieren

Vor der Installation der Erweiterung [Voraussetzungen überprüfen](overview.md#prereqs).

## Installieren der Erweiterung

1. Installieren Sie das Experience Platform Connector-Metapaket.

   ```bash
   composer require magento/platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module:

   * `module-platform-connector-admin` - Aktualisiert die Admin-Benutzeroberfläche
   * `module-platform-connector` - Legt die `ImsOrgId` und `datastreamId` im Magento Storefront Events SDK

1. Installieren Sie die Erweiterung Commerce Data Services , um Profil- und Checkout-Ereignisse einzuschließen.

   ```bash
   composer require magento/data-services
   ```

   Die Commerce Data Services-Erweiterung bietet Attributkontext für Storefront-Ereignisse. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.

1. Installieren Sie den Commerce Service Connector.

   ```bash
   composer require magento/commerce-services
   ```

   Mit dem Commerce Service Connector können Sie Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) und der Adobe Experience Platform.

1. (Optional) Einbeziehen [!DNL Live Search] -Daten, die Suchereignisse enthalten, installieren Sie die [[!DNL Live Search]](../live-search/install.md) -Erweiterung.

## Experience Platform Connector aktualisieren {#update}

Um den Experience Platform-Connector zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/platform-connector --with-dependencies
```

Um auf eine Hauptversion wie 1.0.0 auf 2.0.0 zu aktualisieren, bearbeiten Sie das Stammverzeichnis des Projekts [!DNL Composer] `.json` Datei wie folgt:

1. Öffnen Sie den Stamm. `composer.json` Datei und suchen Sie nach `magento/platform-connector`.

1. Im `require` aktualisieren Sie die Versionsnummer wie folgt:

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Speichern** `composer.json`. Führen Sie dann Folgendes über die Befehlszeile aus:

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Experience Platform Connector deinstallieren {#uninstall}

Informationen zum Deinstallieren des Experience Platform Connectors finden Sie unter [Deinstallationsmodule](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
