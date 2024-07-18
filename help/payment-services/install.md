---
title: Installieren [!DNL Payment Services]
description: Installieren Sie die Erweiterung "Payments Services".
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 692a7e55d72b1e2f1a161d508be5e179c4d26bde
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Installieren Sie [!DNL Payment Services]

Um mit der Verwendung von Zahlungsdiensten für [!DNL Adobe Commerce] und [!DNL Magento Open Source] beginnen zu können, müssen Sie einige Onboarding-Schritte ausführen.

>[!INFO]
>
> Weitere Informationen finden Sie im Video [Konfigurieren von  [!DNL Payment Services] für Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) .

Das Herunterladen und Installieren der [!DNL Payment Services] -Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist eine Voraussetzung für die Verwendung von [!DNL Payment Services].

![[!DNL Payment Services] Erweiterung Admin view](assets/admin-view.png){width="300" zoomable="yes"}

## Erweiterung herunterladen

Sie müssen die Erweiterung zunächst von [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) herunterladen, bevor Sie sie installieren.

1. Navigieren Sie zur Erweiterung [Zahlungsdienste auf der Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Um die Bearbeitung und Version auszuwählen, schalten Sie **[!UICONTROL Edition]** und **[!UICONTROL Your store version]** auf Ihre bevorzugte Auswahl um.
1. Klicken Sie auf **[!UICONTROL Add to Cart]**.
1. Beenden Sie den Checkout und klicken Sie auf **[!UICONTROL Place Order]**.
1. Überprüfen Sie die mit Ihrem Marketplace-Download verknüpfte E-Mail, um eine Bestellbestätigung und Details zu erhalten.

## Installieren der Erweiterung

Sie können die Erweiterung [!DNL Payment Services] sowohl für [!DNL Adobe Commerce] in der Cloud-Infrastruktur als auch in lokalen Instanzen installieren, die mit Ihrem Commerce-Konto [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) verknüpft sind, das im Anmeldeprozess bereitgestellt wird.
[!DNL Magento Open Source] -Kunden verwenden die lokalen Anweisungen.

Der Composer verwendet diese Schlüssel während der ersten Installation von [!DNL Adobe Commerce] oder in Situationen, in denen die Composer-Schlüssel zuvor nicht in der Datei `auth.json` gespeichert wurden.

Weitere Informationen zum Abrufen von Composer-Schlüsseln finden Sie unter [Abrufen Ihrer Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) .

Weitere Informationen dazu, was Sie beachten sollten, bevor Sie eine Erweiterung herunterladen und installieren, finden Sie unter [Installieren einer Erweiterung](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) .

### [!DNL Adobe Commerce] in der Cloud-Infrastruktur

Diese Methode wird zum Installieren der [!DNL Payment Services] -Erweiterung für eine Commerce Cloud-Instanz verwendet.

1. Aktualisieren Sie Ihre `composer.json` -Datei:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Root-Abhängigkeiten zu aktualisieren.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

### Vor Ort und sonstige Konfigurationen

Diese Methode wird zum Installieren der Erweiterung [!DNL Payment Services] für eine lokale Instanz und für [!DNL Magento Open Source] -Kunden verwendet.

1. Führen Sie die folgenden Befehle aus, um die Erweiterung abzurufen:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Root-Abhängigkeiten zu aktualisieren.

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

Wenn eine neue Version von [!DNL Payment Services] veröffentlicht wird, können Sie Ihre Erweiterung einfach aktualisieren.

1. So rufen Sie die neueste Version des Pakets ab:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Verwenden Sie den Befehl `composer update` , um alle Root-Abhängigkeiten zu aktualisieren.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

## Fehlerbehebung

Beim Versuch, die [!DNL Payment Services] -Erweiterung zu installieren, treten möglicherweise Fehler auf. Verwenden Sie die folgenden Methoden zur Fehlerbehebung, um die Fehler zu beheben.

### Falsche Composer-Schlüssel

Wenn die folgende Fehlermeldung angibt, dass Sie über falsche Composer-Schlüssel verfügen:

```
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Überprüfen Sie, ob Ihre Composer-Schlüssel gültig sind und Sie Zugriff auf andere Magento-Pakete haben.

So sehen Sie, welche Composer-Schlüssel konfiguriert sind:

1. Suchen Sie den Speicherort der Datei &quot;`auth.json`&quot;:

   ```bash
   composer config --global home
   ```

1. Anzeigen der Datei &quot;`auth.json`&quot;:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [Welche Schlüssel mit Ihrem Commerce-Konto verknüpft sind `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Nicht genügend Speicher für PHP

Wenn Sie den folgenden Fehler sehen, der angibt, dass Sie nicht genügend Speicher für PHP haben:

```
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Erhöhen Sie die Speicherbegrenzung](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) für PHP in Ihrer Umgebung in `php.ini`.

Alternativ können Sie die Speicherbegrenzung mit diesem Befehl angeben: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Beispiel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
