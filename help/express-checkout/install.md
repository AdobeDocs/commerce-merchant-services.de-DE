---
title: Installieren Sie die [!DNL Express Checkout] für die Adobe Commerce-Erweiterung
description: Führen Sie die folgenden Schritte aus, um die [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt.
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Installieren Sie die [!DNL Express Checkout]

>[!IMPORTANT]
>
> Diese Funktion ist nur für Benutzer des Early Adopter Program (EAP) gedacht und steht noch nicht allen Kunden zur Verfügung. Derzeit auf US-Kunden beschränkt. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

Die [!DNL Express Checkout] für Adobe Commerce bietet ein nahtloses Checkout-Erlebnis, mit dem einmalige Gast-Käufer in treue Kontoinhaber umgewandelt werden können.

Die [!DNL Express Checkout] -Erweiterung für Adobe Commerce und Magento Open Source können mit Composer-Schlüsseln installiert werden, die mit dem [Magento-ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;}, die im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der ersten Installation von Adobe Commerce oder in Situationen, in denen die Composer-Schlüssel zuvor nicht im `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} für weitere Informationen zum Abrufen von Composer-Schlüsseln.

Es gibt zwei Möglichkeiten, diese Erweiterung zu installieren - für [Adobe Commerce auf Cloud-Infrastruktur](#magento-commerce-cloud) oder [vor Ort](#on-premises) Installationen. Für diese Methoden müssen Sie die Befehlszeilenschnittstelle (CLI) verwenden.

## Mindeststabilitätseinstellung aktualisieren

Vor der Installation der Erweiterung können Sie die `minimum-stability` Anforderung an `RC` (Freigabekandidat) in Ihrem `composer.json` -Datei, wenn Sie die Release-Kandidatenversion ausprobieren möchten. Sie können eine IDE oder Ihren bevorzugten Texteditor (wie Visual Studio Code oder Sublime Text) verwenden.

In `composer.json` Datei, ändern `"minimum-stability": "stable"` nach `"minimum-stability": "RC"`.

## Installieren der Erweiterung

Sie können die [!DNL Express Checkout] Erweiterung für Adobe Commerce in Cloud-Infrastruktur und lokalen Instanzen.

### Adobe Commerce auf Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Express Checkout] -Erweiterung für eine Commerce Cloud-Instanz.

1. Wechseln Sie auf Ihrer lokalen Workstation zum Stammordner des Cloud-Projekts.

1. Aktualisieren Sie Ihre `composer.json` Datei:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/express-checkout`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

### Vor Ort

Diese Methode wird zum Installieren der [!DNL Express Checkout] Erweiterung für eine Instanz vor Ort.

1. Fügen Sie das Express-Checkout-Modul zum `require` Abschnitt `composer.json` Datei:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/express-checkout`.

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

Wenn wir eine neue Version der [!DNL Express Checkout]können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/express-checkout`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

## Fehlerbehebung

Beim Versuch, die [!DNL Express Checkout] -Erweiterung.

Siehe Abschnitt [Fehlerbehebung](../express-checkout/troubleshooting.md) für weitere Informationen, wenn bei der Installation von [!DNL Express Checkout].

## Voraussetzungen

Siehe [Voraussetzungen](../express-checkout/prerequisites.md) für weitere Informationen.
