---
title: Installieren [!DNL Payment Services]
description: Installieren Sie die Erweiterung "Payments Services".
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Installieren [!DNL Payment Services]

Installieren der [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist ein erforderlicher Schritt zur Verwendung von [!DNL Payment Services].

![[!DNL Payment Services] Admin-Ansicht der Erweiterung](assets/admin-view.png)

Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann mit Composer-Schlüsseln installiert werden, die mit der Magento-ID ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der ersten Installation von [!DNL Adobe Commerce]oder in Situationen, in denen die Composer-Schlüssel zuvor nicht im `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

Es gibt zwei Möglichkeiten, diese Erweiterung zu installieren - für [[!DNL Adobe Commerce] zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [Vor Ort](install.md#on-premises) Installationen. Für diese Methoden müssen Sie die Befehlszeilenschnittstelle (CLI) verwenden.

## Mindeststabilitätseinstellung aktualisieren

Vor der Installation der Erweiterung müssen Sie die `minimum-stability` Anforderung an `RC` (Freigabekandidat) in Ihrem `composer.json` -Datei. Sie können eine IDE oder Ihren bevorzugten Texteditor (wie Visual Studio Code oder Sublime Text) verwenden.

In `composer.json` Datei, ändern `"minimum-stability": "stable"` nach `"minimum-stability": "RC"`.

## Installieren der Erweiterung

Sie können die [!DNL Payment Services] -Erweiterung für beide [!DNL Adobe Commerce] auf Cloud-Infrastruktur und lokalen Instanzen.

### [!DNL Adobe Commerce] zur Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Payment Services] -Erweiterung für eine Commerce Cloud-Instanz.

1. Aktualisieren Sie Ihre `composer.json` Datei:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer require magento/payment-services`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

### Vor Ort

Diese Methode wird zum Installieren der [!DNL Payment Services] Erweiterung für eine Instanz vor Ort.

1. Führen Sie die folgenden Befehle aus, um die Erweiterung abzurufen:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer require magento/payment-services`.

1. Upgrade [!DNL Adobe Commerce]:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

1. Zusagen von Änderungen.
1. Um sicherzustellen, dass der zugewiesene Code bereitgestellt wird, aktualisieren Sie Ihre lokale Instanz .

## Aktualisierung der Erweiterung

Wenn eine neue Version von [!DNL Payment Services] veröffentlicht wurde, können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update
   ```

   Die `composer update` -Befehl aktualisiert alle Abhängigkeiten. Wenn Sie nicht alle Abhängigkeiten gleichzeitig aktualisieren möchten, verwenden Sie stattdessen diesen Befehl: `composer update magento/payment-services`.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

## Fehlerbehebung

Beim Versuch, die [!DNL Payment Services] -Erweiterung. Verwenden Sie die folgenden Methoden zur Fehlerbehebung, um die Fehler zu beheben.

### Falsche Composer-Schlüssel

Wenn die folgende Fehlermeldung angibt, dass Sie über falsche Composer-Schlüssel verfügen:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Überprüfen Sie, ob Ihre Composer-Schlüssel mit der Magento-ID verknüpft sind, die während der [!DNL Payment Services] registrieren.

So sehen Sie, welche Composer-Schlüssel konfiguriert sind:

1. Suchen Sie den Speicherort der `auth.json` Datei:

   ```bash
   composer config --global home
   ```

1. Anzeigen der `auth.json` Datei:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [welche Schlüssel Ihrer Magento-ID zugeordnet sind](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

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
