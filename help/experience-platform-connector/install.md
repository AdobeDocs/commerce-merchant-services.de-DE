---
title: Installieren und Konfigurieren von Adobe Experience Platform Connector von Adobe Commerce
description: Erfahren Sie, wie Sie den Adobe Experience Platform Connector von Adobe Commerce installieren, konfigurieren, aktualisieren und deinstallieren.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Experience Platform Connector installieren und konfigurieren

Vor der Installation der Erweiterung [Voraussetzungen überprüfen](overview.md#prereqs).

## Installieren der Erweiterung

1. Installieren Sie das Experience Platform Connector-Metapaket.

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   * `module-platform-connector-admin` - Aktualisiert die Administrator-Benutzeroberfläche, sodass Sie die Datastream-ID konfigurieren können.
   * `module-platform-connector` - Legt die `ImsOrgId` und `datastreamId` im Adobe Commerce Storefront Event SDK
   * `data-services` - Stellt Attributkontext für Storefront-Ereignisse bereit. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.
   * `commerce-services` - Verbinden Sie Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) Verwendung von Sandbox- und Produktions-API-Schlüsseln sowie zur Adobe Experience Platform mithilfe der IMS-Organisations-ID.

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
