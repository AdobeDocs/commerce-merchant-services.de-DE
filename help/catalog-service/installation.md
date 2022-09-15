---
title: Onboarding und Installation
description: Erfahren Sie, wie Sie installieren [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 595d7644374b066b7608748cf09df1c41bf0eaee
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Onboarding und Installation

Partner und Kunden können gerne mit der Verwendung der [!DNL Catalog Service] für die Adobe Commerce Beta-Version, die am 9. August 2022 veröffentlicht wurde. Um teilnehmen zu können, müssen Sie unsere [Adobe Commerce Beta-Programmbedingungen](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Sobald Sie die Vereinbarung unterzeichnet haben, wenden Sie sich an unser Team im [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) öffentlicher Slack. Wir werden alle Informationen und die nächsten Schritte bereitstellen, die für die Zusammenarbeit mit dem [!DNL Catalog Service] Beta-Version.

## Voraussetzungen

Onboarding-Prozess für [!DNL Catalog Service] erfordert Zugriff auf die Befehlszeile des Servers. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

### Softwareanforderungen

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Verfasser: 2.x, 1.x

### Unterstützte Plattformen

- Adobe Commerce über Cloud-Infrastruktur: 2.4.x
- Adobe Commerce vor Ort: 2.4.x

## Installieren der Erweiterung

Sie können die [!DNL Catalog Service] Erweiterung für Adobe Commerce in Cloud-Infrastruktur und lokalen Instanzen.

Die [!DNL Catalog Service] wird mit Composer-Schlüsseln installiert, die mit der Magento-ID ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der ersten Installation von [!DNL Adobe Commerce]oder in Situationen, in denen die Composer-Schlüssel zuvor nicht im `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

### Adobe Commerce auf Cloud-Infrastruktur

Verwenden Sie diese Methode, um die [!DNL Catalog Service] -Erweiterung für eine Commerce Cloud-Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` Datei in einem Texteditor speichern und aktualisieren `require` wie folgt:

   ```json
   "require": {
    "magento/composer-root-update-plugin": "^2.0.2",
    "magento/magento-cloud-metapackage": ">=2.4.5 <2.4.6",
    "magento/saas-export": "^101.4.0",
    "magento/commerce-data-export": "^101.3.1",
    "magento/commerce-data-export-ee": "^101.3.1",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
    }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Testen Sie die neue Konfiguration lokal und aktualisieren Sie Abhängigkeiten:

   ```bash
   composer update
   ```

   Der Befehl aktualisiert alle Abhängigkeiten.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie für `composer.json` und `composer.lock`.

### Vor Ort

Verwenden Sie diese Methode, um die [!DNL Catalog Service] Erweiterung für eine lokale Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` Datei in einem Texteditor speichern und aktualisieren `require` wie folgt:

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Der Befehl aktualisiert alle Abhängigkeiten.

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

## Konfigurieren des Katalogexports

Nach der Installation [!DNL Catalog Service], müssen Sie die [Commerce Services Connector](../landing/saas.md) durch Angabe von API-Schlüsseln und Auswahl eines SaaS-Datenspeichers.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- Vergewissern Sie sich, dass [Cron-Aufträge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) laufen.
- Überprüfen Sie die [Indexer](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) laufen.
- Stellen Sie sicher, dass `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`und `Product Variant Feed` Indexer werden auf `Update by Schedule`.
