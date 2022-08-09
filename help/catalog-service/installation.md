---
title: '"Onboarding und Installation"'
description: '"Erfahren Sie, wie Sie installieren [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '381'
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
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Der Befehl aktualisiert alle Abhängigkeiten.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie.

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

Um sicherzustellen, dass der Katalogexport ordnungsgemäß ausgeführt wird, überprüfen Sie, ob die Variable [Cron-Aufträge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) und [Indexer](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) ausgeführt werden und der Produkt-Feed-Indexer auf &quot;Nach Zeitplan aktualisieren&quot;eingestellt ist.
