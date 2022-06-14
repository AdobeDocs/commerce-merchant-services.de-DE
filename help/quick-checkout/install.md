---
title: '"Installieren Sie die [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"'
description: '"Führen Sie die folgenden Schritte aus, um die [!DNL Quick Checkout] in Ihrem Adobe Commerce-Projekt."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Installieren Sie die [!DNL Quick Checkout]

Die [!DNL Quick Checkout] für Adobe Commerce bietet ein nahtloses Checkout-Erlebnis, mit dem einmalige Gast-Käufer in treue Kontoinhaber umgewandelt werden können.

Die [!DNL Quick Checkout] Erweiterung für Adobe Commerce und [!DNL Magento Open Source] kann mit [!DNL Composer keys], die mit dem [Magento-ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;}, die im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der Erstinstallation von Adobe Commerce oder in Situationen, in denen die [!DNL Composer keys] wurden zuvor nicht in der Variablen `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} Thema für weitere Informationen zum Abrufen [!DNL Composer keys].

Es gibt zwei Möglichkeiten, diese Erweiterung zu installieren - für [Adobe Commerce auf Cloud-Infrastruktur](#magento-commerce-cloud) oder [vor Ort](#on-premises) Installationen. Für diese Methoden müssen Sie die Befehlszeilenschnittstelle (CLI) verwenden.

## Mindeststabilitätseinstellung aktualisieren

Vor der Installation der Erweiterung können Sie die `minimum-stability` Anforderung an `RC` (Freigabekandidat) in Ihrem `composer.json` -Datei, wenn Sie die Release-Kandidatenversion ausprobieren möchten. Sie können eine IDE oder Ihren bevorzugten Texteditor (wie Visual Studio Code oder Sublime Text) verwenden.

In `composer.json` Datei, ändern `"minimum-stability": "stable"` nach `"minimum-stability": "RC"`.

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

Siehe Abschnitt [Fehlerbehebung](../quick-checkout/troubleshooting.md) für weitere Informationen, wenn bei der Installation von [!DNL Quick Checkout].

## Voraussetzungen

Siehe [Voraussetzungen](../quick-checkout/prerequisites.md) für weitere Informationen.