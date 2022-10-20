---
title: Installieren [!DNL Payment Services]
description: Installieren Sie die Erweiterung "Payments Services".
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Installieren [!DNL Payment Services]

Herunterladen und Installieren der [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist ein erforderlicher Schritt zur Verwendung von [!DNL Payment Services].

![[!DNL Payment Services] Admin-Ansicht der Erweiterung](assets/admin-view.png)

## Erweiterung herunterladen

Sie müssen zuerst die Erweiterung von [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) vor der Installation.

1. Navigieren Sie zum [Zahlungsdiensterweiterung im Commerce Marketplace](https://marketplace.magento.com/magento-payment-services.html).
1. Um die Bearbeitung und Version auszuwählen, schalten Sie **[!UICONTROL Edition]** und **[!UICONTROL Your store version]** zu Ihrer gewünschten Auswahl hinzufügen.
1. Klicken **[!UICONTROL Add to Cart]**.
1. Checkout abschließen und klicken **[!UICONTROL Place Order]**.
1. Überprüfen Sie die mit Ihrem Marketplace-Download verknüpfte E-Mail, um eine Bestellbestätigung und Details zu erhalten.

## Installieren der Erweiterung

Sie können die [!DNL Payment Services] -Erweiterung für beide [!DNL Adobe Commerce] in der Cloud-Infrastruktur und in lokalen Instanzen, die mit Ihrem Commerce-Konto verknüpft sind [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) im Anmeldeprozess bereitgestellt werden. [!DNL Magento Open Source] Kunden verwenden die Anweisungen vor Ort.

Der Verfasser verwendet diese Schlüssel bei der ersten Installation von [!DNL Adobe Commerce]oder in Situationen, in denen die Composer-Schlüssel zuvor nicht im `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

Siehe [Installieren einer Erweiterung](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) Weitere Informationen dazu, was Sie beachten sollten, bevor Sie eine Erweiterung herunterladen und installieren.

### [!DNL Adobe Commerce] zur Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Payment Services] -Erweiterung für eine Commerce Cloud-Instanz.

1. Aktualisieren Sie Ihre `composer.json` Datei:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie die `composer update` -Befehl, um alle Stammabhängigkeiten zu aktualisieren.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

### Vor Ort und sonstige Konfigurationen

Diese Methode wird zum Installieren der [!DNL Payment Services] Erweiterung für eine örtliche Instanz und [!DNL Magento Open Source] -Kunden.

1. Führen Sie die folgenden Befehle aus, um die Erweiterung abzurufen:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie die `composer update` -Befehl, um alle Stammabhängigkeiten zu aktualisieren.

1. Aktualisieren Sie Ihre Instanz:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

1. Zusagen von Änderungen.
1. Um sicherzustellen, dass der bereitgestellte Code bereitgestellt wird, aktualisieren Sie Ihre Instanz .

## Aktualisierung der Erweiterung

Wenn eine neue Version von [!DNL Payment Services] veröffentlicht wurde, können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie die `composer update` -Befehl, um alle Stammabhängigkeiten zu aktualisieren.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

## Fehlerbehebung

Beim Versuch, die [!DNL Payment Services] -Erweiterung. Verwenden Sie die folgenden Methoden zur Fehlerbehebung, um die Fehler zu beheben.

### Falsche Composer-Schlüssel

Wenn die folgende Fehlermeldung angibt, dass Sie über falsche Composer-Schlüssel verfügen:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Überprüfen Sie, ob Ihre Composer-Schlüssel gültig sind und Sie Zugriff auf andere Magento-Packages haben.

So sehen Sie, welche Composer-Schlüssel konfiguriert sind:

1. Suchen Sie den Speicherort der `auth.json` Datei:

   ```bash
   composer config --global home
   ```

1. Anzeigen der `auth.json` Datei:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [welche Schlüssel mit Ihrem Commerce-Konto verknüpft sind `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Nicht genügend Speicher für PHP

Wenn Sie den folgenden Fehler sehen, der angibt, dass Sie nicht genügend Speicher für PHP haben:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Erhöhen Sie die Speicherbegrenzung.](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) für PHP in Ihrer Umgebung in `php.ini`.

Alternativ können Sie die Speicherbegrenzung mit diesem Befehl angeben: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Beispiel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
