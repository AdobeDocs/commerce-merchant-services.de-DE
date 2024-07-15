---
title: Installieren [!DNL Data Connection]
description: Erfahren Sie, wie Sie die [!DNL Data Connection] Erweiterung von Adobe Commerce installieren, aktualisieren und deinstallieren.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Installieren Sie [!DNL Data Connection]

Überprüfen Sie vor der Installation der Erweiterung [die Voraussetzungen](overview.md#prereqs).

## Installieren der Erweiterung

Die Erweiterung [!DNL Data Connection] ist im [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html) verfügbar. Wenn Sie diese Erweiterung über die Befehlszeile des Servers installieren, stellt sie eine Verbindung zu Ihrer Adobe Commerce-Installation als [Dienst](../landing/saas.md) her. Wenn der Vorgang abgeschlossen ist, werden im Menü **System** unter **Dienste** in der Commerce _Admin_ die Optionen **[!DNL Data Connection]** und **Commerce Services Connector** angezeigt.

![[!DNL Data Connection] Erweiterung Admin view](assets/epc-adminui.png)

>[!IMPORTANT]
>
>Der Name der Erweiterung wurde zwar von Experience Platform-Connector zu [!DNL Data Connection] geändert, der Paketname bleibt jedoch `experience-platform-connector`, um die Abwärtskompatibilität zu unterstützen.

1. Um das Paket `experience-platform-connector` herunterzuladen, führen Sie Folgendes über die Befehlszeile aus:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Dieses Metapaket enthält die folgenden Module und Erweiterungen:

   * `module-experience-connector-admin` - Aktualisiert die Admin-Benutzeroberfläche, sodass Sie die Datastraam-ID für eine bestimmte Adobe Commerce-Instanz auswählen können.
   * `module-experience-connector` - Legt die `Organization ID` und `datastreamId` im Storefront Events SDK fest.
   * `data-services` - Stellt Attributkontext für Storefront-Ereignisse bereit. Wenn beispielsweise ein Checkout-Ereignis eintritt, werden Informationen darüber eingeschlossen, wie viele Elemente sich im Warenkorb befanden und wie viele Produktattributdaten für diese Elemente vorhanden sind.
   * `services-id` - Verbindet Ihre Adobe Commerce-Instanz mit [Adobe Commerce SaaS](../landing/saas.md) mithilfe von Sandbox- und Produktions-API-Schlüsseln und mit der Adobe Experience Platform, um die IMS-Organisations-ID abzurufen.
   * `orders-connector` - Verbindet den Auftragsstatus-Dienst mit Ihrer Adobe Commerce-Instanz.

1. (Optional) Um [!DNL Live Search] -Daten einzuschließen, die [Suchereignisse](events.md#search-events) enthalten, installieren Sie die Erweiterung [[!DNL Live Search]](../live-search/install.md) .

1. (Optional) Um B2B-Daten einzubeziehen, die [Anforderungsereignisse](events.md#b2b-events) enthalten, installieren Sie die [B2B-Erweiterung](#install-the-b2b-extension).

### Installieren der Adobe I/O-Ereignisse

Nachdem Sie die Erweiterung `experience-platform-connector` installiert haben, müssen Sie die Adobe I/O Events für Adobe Commerce installieren.

Die folgenden Schritte gelten für Adobe Commerce sowohl für Cloud-Infrastrukturen als auch für lokale Installationen.

1. Wenn Sie Commerce 2.4.4 oder 2.4.5 ausführen, verwenden Sie den folgenden Befehl, um die Ereignismodule zu laden:

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 und höher lädt diese Module automatisch.

1. Aktualisieren Sie die Projektabhängigkeiten.

   ```bash
   composer update
   ```

1. Aktivieren Sie die neuen Module:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Fertigstellen Sie die Installation basierend auf dem Bereitstellungstyp: lokal oder Adobe Commerce in der Cloud-Infrastruktur.

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

Aktivieren Sie in der Adobe Commerce on Cloud-Infrastruktur die globale Variable `ENABLE_EVENTING` in `.magento.env.yaml`. [Weitere Infos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

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

Installieren Sie für B2B-Händler die folgende Erweiterung, um die Ereignisdaten für [Anforderungsliste](events.md#b2b-events) einzuschließen.

Laden Sie die Erweiterung `magento/experience-platform-connector-b2b` herunter, indem Sie Folgendes über die Befehlszeile ausführen:

```bash
composer require magento/experience-platform-connector-b2b
```

## Aktualisieren der [!DNL Data Connection] -Erweiterung {#update}

Um die Erweiterung [!DNL Data Connection] zu aktualisieren, führen Sie Folgendes über die Befehlszeile aus:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Oder für B2B-Händler:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Um auf eine Hauptversion wie 2.0.0 auf 3.0.0 zu aktualisieren, bearbeiten Sie die Stammdatei des Projekts [!DNL Composer] `.json` wie folgt:

1. Öffnen Sie die Stammdatei `composer.json` und suchen Sie nach `magento/experience-platform-connector`.

1. Aktualisieren Sie im Abschnitt `require` die Versionsnummer wie folgt:

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

   Oder für B2B-Händler:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Deinstallieren der [!DNL Data Connection] -Erweiterung {#uninstall}

Informationen zum Deinstallieren der Erweiterung [!DNL Data Connection] finden Sie unter [Module deinstallieren](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
