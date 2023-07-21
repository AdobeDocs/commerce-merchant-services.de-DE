---
title: Installation
description: "Installieren Sie die [!DNL Store Fulfillment solution] für eine Adobe Commerce-Storefront mit Composer für PHP."
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# Installation

Führen Sie die Erstinstallation des [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] -Erweiterung in einer Nicht-Produktionsumgebung mit ausgeführtem Warteschlangenmanager und konfigurierter Zwischenspeicherung, um die Ausnahmebehandlung zu ermöglichen. Stellen Sie sicher, dass Ihre Entwicklungsumgebung Entwicklungstools enthält, um Best Practices für den Betrieb und die Wartung Ihrer Adobe Commerce-Instanz sicherzustellen.

## Voraussetzungen

Überprüfen Sie die [Anforderungen](solution-requirements.md) für die Store Fulfillment-Lösung und sammeln Sie die erforderlichen Informationen, bevor Sie die [!DNL Store Fulfillment] Erweiterung für Adobe Commerce.

Wenn Sie eine Vorabversion oder Betaversion der Erweiterung Store Fulfillment for Adobe Commerce installiert haben, verwenden Sie den folgenden Befehl, um sie zu entfernen, bevor Sie die aktuelle Version installieren.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installationsanforderungen

- **Zugriff auf das Softwarearchiv der Walmart Commerce Technologies-Software zur Store-Erfüllung (.zip-Datei)**—Wenden Sie sich während des Onboarding- und Aktivierungsprozesses an Ihren Kundenbetreuer, um Zugriff auf die Installationsdatei für die Store Fulfillment-Erweiterung zu erhalten.

- **Adobe Commerce-Kontoinformationen**- Installieren der [!DNL Store Fulfillment] -Lösung erfordert [[!DNL Commerce] account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. Sie benötigen eine Konto-ID und Anmeldedaten mit dem Inhaber- oder Administratorzugriff auf die [!DNL Adobe Commerce] Projekt.

- Für [!DNL Adobe Commerce] Bei Cloud-Infrastrukturprojekten müssen Softwareinstallateure Administratorzugriff auf das Cloud-Projekt haben. Siehe [Benutzerzugriff verwalten](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Erlebnis mit Composer und dem[!DNL Commerce CLI]**—Siehe [Allgemeine CLI-Installation](https://devdocs.magento.com/extensions/install/){target="_blank"} Informationen zur Verwendung dieser Tools zum Installieren und Verwalten von Erweiterungen auf der [!DNL Adobe Commerce] Plattform.

- **Erlebnis der Installation von Drittanbietererweiterungen auf Adobe Commerce**—Weitere Informationen finden Sie in der Adobe Commerce-Dokumentation.

   - [Installieren einer Erweiterung für eine Adobe Commerce in einer Cloud-Infrastrukturinstanz](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Installieren einer Erweiterung für eine lokale Adobe Commerce-Instanz](https://devdocs.magento.com/extensions/install/).

### Schritt 1: Herunterladen des Erweiterungspakets

Befolgen Sie die Anweisungen Ihrer Kundenbetreuer, um die Archivdatei herunterzuladen, die die Composer-Pakete für die Installation der Store Fulfillment Services-Erweiterung enthält.

### Schritt 2: Erweiterungsartefakte in Ihre Anwendung extrahieren

Extrahieren Sie die Archivdatei, die das Integrations-Bundle enthält, um die Erweiterung Store Fulfillment Services zu installieren.

1. Erstellen Sie ein Zielverzeichnis für die extrahierten Dateien.

   - Wechseln Sie in der Befehlszeile zum Basisverzeichnis des Webservers.

   - Erstellen Sie eine `artifacts` Verzeichnis.

1. Extrahieren Sie die Archivdatei in das neue Verzeichnis.

1. Überprüfen Sie, ob die Dateien erfolgreich extrahiert wurden, indem Sie die Dateiauflistung überprüfen.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Schritt 3: App mit Composer konfigurieren

Verwenden Sie Composer, um den Quellordner für die Installation zu konfigurieren und die Erweiterung &quot;Store Fulfillment Services&quot;zu installieren.

1. Konfigurieren Sie das Quell-Repository für die Composer-Installation.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Fügen Sie die Erweiterung Store Fulfillment Services zu `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Für eine bessere Leistung bei Adobe Commerce-Instanzen vor Ort können Sie [die automatische Ladekonfiguration aktualisieren](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Schritt 4: Datenbankschema und Daten aktualisieren

Schließen Sie die Installation mit der `bin/magento setup:upgrade` , um das Datenbankschema und die Daten mit den Änderungen zu aktualisieren, um die Lösung zur Store-Erfüllung zu unterstützen.

>[!NOTE]
>
>Für Adobe Commerce in Cloud-Infrastrukturprojekten müssen Sie die Erweiterung nicht registrieren. Übernehmen Sie stattdessen die Codeänderungen aus dem vorherigen Schritt und übertragen Sie sie in Ihre Umgebungsverzweigung. Die Befehle zum Aktualisieren des Datenbankschemas und der Daten werden während des Build- und Bereitstellungsprozesses der Cloud automatisch ausgeführt.

### Schritt 5: Schließen Sie die Installation ab

1. Registrieren Sie die Erweiterung bei Adobe Commerce mithilfe der `setup:upgrade` Magento-CLI-Befehl.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie bei entsprechender Aufforderung Ihre [!DNL Commerce] Projekt.

   ```bash
   bin/magento setup:di:compile
   ```

1. Bereinigen Sie den Cache.

   ```bash
   bin/magento cache:clean
   ```

1. Wartungsmodus deaktivieren.

   ```bash
   bin/magento maintenance:disable
   ```

### Schritt 6: Installation überprüfen

Überprüfen Sie vom Adobe Commerce-Server, ob die Module für die Erweiterung &quot;Store Fulfillment Services&quot;installiert und aktiviert sind.

1. Melden Sie sich beim Server an.

   Für Installationen in Adobe Commerce auf Cloud-Infrastruktur: [Verwenden Sie SSH, um sich bei der Remote-Umgebung anzumelden.](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. Stellen Sie sicher, dass die Module für Store Fulfillment Services aktiviert sind.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   Die Ausgabe sollte die folgenden Module enthalten:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Zusätzliche Schritte

Verwenden Sie bei Bedarf die [Setup:static-content:deploy](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} CLI-Befehl zum Bereitstellen von statischen Ansichtsdateien in Ihrer Produktionsumgebung.

```terminal
php bin/magento setup:static-content:deploy -f
```

Die `-f` ist erforderlich, wenn Sie ein leeres Design verwenden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Best Practices für die Bereitstellung statischer Inhalte in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) Artikel im Adobe Commerce Help Center.

