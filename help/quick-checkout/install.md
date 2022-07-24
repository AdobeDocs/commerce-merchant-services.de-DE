---
title: '"Installieren Sie die [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"'
description: '"Führen Sie die folgenden Schritte aus, um die [!DNL Quick Checkout] in Ihrem Adobe Commerce-Projekt."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: d6cb5ae5437f78cacb0208269598896f5d8523d0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Installieren Sie die [!DNL Quick Checkout]

Die [!DNL Quick Checkout] Erweiterung für Adobe Commerce und Magento Open Source kann mit [!DNL Composer keys], die mit dem [Magento-ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;}, die im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der Erstinstallation von Adobe Commerce oder in Situationen, in denen die [!DNL Composer keys] wurden zuvor nicht in der Variablen `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} Thema für weitere Informationen zum Abrufen [!DNL Composer keys].

Es gibt zwei Möglichkeiten, diese Erweiterung zu installieren - für [Adobe Commerce auf Cloud-Infrastruktur](#magento-commerce-cloud) oder [vor Ort](#on-premises) Installationen. Für diese Methoden müssen Sie die Befehlszeilenschnittstelle (CLI) verwenden.

## Mindeststabilitätseinstellung aktualisieren

Stellen Sie vor der Installation der Erweiterung sicher, dass die Variable `minimum-stability` in Ihrem `composer.json` -Datei auf `"stable"`:

`"minimum-stability": "stable"`

## Installieren der Erweiterung

Sie können die [!DNL Quick Checkout] Erweiterung für Adobe Commerce in Cloud-Infrastruktur und lokalen Instanzen.

### Adobe Commerce auf Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Quick Checkout] -Erweiterung für eine Commerce Cloud-Instanz.

1. Wechseln Sie auf Ihrer lokalen Workstation zum Stammordner des Cloud-Projekts.

1. Aktualisieren Sie Ihre `composer.json` Datei:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/quick-checkout`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

### Vor Ort

Diese Methode wird zum Installieren der [!DNL Quick Checkout] Erweiterung für eine Instanz vor Ort.

1. Fügen Sie das Modul &quot;Quick Checkout&quot;zum `require` Abschnitt `composer.json` Datei:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/quick-checkout`.

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

1. Zusagen von Änderungen.
1. Aktualisieren Sie Ihre lokale Instanz, um sicherzustellen, dass der bereitgestellte Code bereitgestellt wird.

## Aktualisierung der Erweiterung

Wenn wir eine neue Version der [!DNL Quick Checkout]können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/quick-checkout`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

## Fehlerbehebung

Beim Versuch, die [!DNL Quick Checkout] -Erweiterung.

Wenn während der [!DNL Quick Checkout] Installationsprozess, siehe [Fehlerbehebung bei Problemen mit der Schnellüberprüfung](https://support.magento.com/hc/en-us/articles/6909450342541) im Adobe Commerce Help Center.

## Voraussetzungen

Siehe [Voraussetzungen](../quick-checkout/prerequisites.md) für weitere Informationen.
