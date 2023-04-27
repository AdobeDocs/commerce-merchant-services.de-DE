---
title: Installieren und Konfigurieren von Adobe Experience Platform Connector von Adobe Commerce
description: Erfahren Sie, wie Sie den Adobe Experience Platform Connector von Adobe Commerce installieren, konfigurieren, aktualisieren und deinstallieren.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 898d49cbeb4711862a47693a0d608b74730dc845
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Installieren und Konfigurieren des Experience Platform Connectors

Vor der Installation der Erweiterung [Voraussetzungen überprüfen](overview.md#prereqs).

## Installieren der Erweiterung

Die Experience Platform Connector-Erweiterung ist über das [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Wenn Sie diese Erweiterung über die Befehlszeile des Servers installieren, stellt sie eine Verbindung zu Ihrer Adobe Commerce-Installation als [service](../landing/saas.md). Wenn der Prozess abgeschlossen ist, **Experience Platform Connector** und **Commerce Services Connector** auf **System** Menü unter **Dienste** im Handel _Admin_.

>[!NOTE]
>
>![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler gibt es eine separate Erweiterung, die Sie installieren müssen. Diese Erweiterung unterstützt jetzt auch B2B-spezifische Ereignisse. [Weitere Infos](#install-the-b2b-extension).


1. So laden Sie die `experience-platform-connector` -Paket, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   * `module-experience-connector-admin` - Aktualisiert die Admin-Benutzeroberfläche, sodass Sie die Datastraam-ID für eine bestimmte Adobe Commerce-Instanz auswählen können.
   * `module-experience-connector` - Legt die `Organization ID` und `datastreamId` im Storefront Events SDK
   * `data-services` - Stellt Attributkontext für Storefront-Ereignisse bereit. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.
   * `services-id` - Verbinden Sie Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) Verwenden von Sandbox- und Produktions-API-Schlüsseln und zum Adobe Experience Platform zum Abrufen der IMS-Organisations-ID

1. (Optional) Einbeziehen [!DNL Live Search] -Daten, die Suchereignisse enthalten, installieren Sie die [[!DNL Live Search]](../live-search/install.md) -Erweiterung.

### Installieren der B2B-Erweiterung

Installieren Sie für B2B-Händler die folgende Erweiterung, um [Anforderungsliste](events.md#b2b-events) Ereignisdaten.

Laden Sie die `magento/experience-platform-connector-b2b` -Erweiterung durch Ausführen der folgenden Aktionen über die Befehlszeile:

```bash
composer require magento/experience-platform-connector-b2b
```

## Experience Platform Connector aktualisieren {#update}

Um den Experience Platform-Connector zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

B2B-Händler:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
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

   B2B-Händler:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Experience Platform Connector deinstallieren {#uninstall}

Informationen zum Deinstallieren des Experience Platform Connectors finden Sie unter [Deinstallationsmodule](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
