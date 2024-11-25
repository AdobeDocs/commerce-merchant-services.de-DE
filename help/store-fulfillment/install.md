---
title: Installation
description: "Installieren Sie die [!DNL Store Fulfillment solution] für eine Adobe Commerce-Storefront mit Composer für PHP."
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: b2425eb7204400899dfe6eaa9978e49c3ff00ec7
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Installation

Schließen Sie die Erstinstallation der Erweiterung [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] in einer Nicht-Produktionsumgebung ab, wobei der Warteschlangenmanager ausgeführt und die Zwischenspeicherung so konfiguriert ist, dass die Ausnahmebehandlung möglich ist. Stellen Sie sicher, dass Ihre Entwicklungsumgebung Entwicklungstools enthält, um Best Practices für den Betrieb und die Wartung Ihrer Adobe Commerce-Instanz sicherzustellen.

>[!TIP]
>
>Aktualisieren Sie die Store Fulfillment-Erweiterung für Adobe Commerce lokal, indem Sie die [Upgrade-Anweisungen](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html) im _Adobe Commerce Upgrade-Handbuch_ befolgen. Informationen zu Adobe Commerce in der Cloud-Infrastruktur finden Sie unter [Aktualisieren einer Erweiterung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html#upgrade-an-extension) im *Commerce on Cloud Infrastructure Guide*.

## Voraussetzungen

Überprüfen Sie die [Anforderungen](solution-requirements.md) für die Store Fulfillment-Lösung und sammeln Sie die erforderlichen Informationen, bevor Sie die [!DNL Store Fulfillment] -Erweiterung für Adobe Commerce installieren oder aktualisieren.

Wenn Sie eine Vorabversion oder Betaversion der Erweiterung Store Fulfillment for Adobe Commerce installiert haben, verwenden Sie den folgenden Befehl, um sie zu entfernen, bevor Sie die aktuelle Version installieren.

```bash
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installationsanforderungen

- **Zugriff auf das Softwarearchiv für die Store-Ausführung von Walmart Commerce Technologies (.zip-Datei)** - Wenden Sie sich während des Onboarding- und Aktivierungsprozesses an Ihren Kundenbetreuer, um Zugriff auf die Installationsdatei für die Store Fulfillment-Erweiterung zu erhalten.

- **Adobe Commerce-Kontoinformationen** - Für die Installation der [!DNL Store Fulfillment] -Lösung ist ein [[!DNL Commerce] Konto](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create){target="_blank"} erforderlich. Sie benötigen eine Konto-ID und Anmeldeinformationen mit dem Inhaber- oder Administratorzugriff auf das [!DNL Adobe Commerce] -Projekt.

- Für [!DNL Adobe Commerce] bei Cloud-Infrastrukturprojekten müssen Softwareinstallateure Administratorzugriff auf das Cloud-Projekt haben. Siehe [Verwalten des Benutzerzugriffs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/user-access).

- **Erlebnis mit Composer und dem[!DNL Commerce CLI]** - Informationen zur Verwendung dieser Tools zum Installieren und Verwalten von Erweiterungen auf der [!DNL Adobe Commerce]-Plattform finden Sie unter [Allgemeine CLI-Installation](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions){target="_blank"} .

- **Erlebnis der Installation von Drittanbietererweiterungen auf Adobe Commerce** - Weitere Informationen finden Sie in der Adobe Commerce-Dokumentation.

   - [Installieren Sie eine Erweiterung für eine Adobe Commerce in der Cloud-Infrastrukturinstanz](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension).

   - [Installieren Sie eine Erweiterung für eine lokale Adobe Commerce-Instanz](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions).

### Schritt 1: Herunterladen des Erweiterungs-Bundles

Befolgen Sie die Anweisungen Ihrer Kundenbetreuer, um die Archivdatei herunterzuladen, die die Composer-Pakete für die Installation der Store Fulfillment Services-Erweiterung enthält.

### Schritt 2: Erweiterungsartefakte in Ihre Anwendung extrahieren

Extrahieren Sie die Archivdatei, die das Integrations-Bundle enthält, um die Erweiterung Store Fulfillment Services zu installieren.

1. Erstellen Sie ein Zielverzeichnis für die extrahierten Dateien.

   - Wechseln Sie in der Befehlszeile zum Basisverzeichnis des Webservers.

   - Erstellen Sie ein Verzeichnis &quot;`artifacts`&quot;.

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

1. Fügen Sie die Erweiterung Store Fulfillment Services zu `composer.json` hinzu.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Für eine bessere Leistung bei lokalen Instanzen von Adobe Commerce können Sie [die automatische Ladekonfiguration aktualisieren](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Schritt 4: Datenbankschema und Daten aktualisieren

Schließen Sie die Installation mit dem Wert &quot;`bin/magento setup:upgrade`&quot;ab, um das Datenbankschema und die Daten mit den Änderungen zu aktualisieren, die die Store Fulfillment-Lösung unterstützen.

>[!NOTE]
>
>Für Adobe Commerce in Cloud-Infrastrukturprojekten müssen Sie die Erweiterung nicht registrieren. Übernehmen Sie stattdessen die Codeänderungen aus dem vorherigen Schritt und übertragen Sie sie in Ihre Umgebungsverzweigung. Die Befehle zum Aktualisieren des Datenbankschemas und der Daten werden während des Build- und Bereitstellungsprozesses der Cloud automatisch ausgeführt.

### Schritt 5: Installation abschließen

1. Registrieren Sie die Erweiterung mithilfe des Befehls `setup:upgrade` Magento CLI bei Adobe Commerce.

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie bei entsprechender Aufforderung Ihr [!DNL Commerce] -Projekt erneut.

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

   Bei Installationen in Adobe Commerce auf Cloud-Infrastruktur verwenden Sie [SSH, um sich bei der Remote-Umgebung anzumelden](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).

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

Verwenden Sie bei Bedarf den CLI-Befehl [setup:static-content:deploy](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises){target="_blank"} , um statische Ansichtsdateien für Ihre Produktionsumgebung bereitzustellen.

```bash
php bin/magento setup:static-content:deploy -f
```

Die Option `-f` ist erforderlich, wenn Sie ein leeres Design verwenden.

>[!NOTE]
>
>Weitere Informationen finden Sie im Artikel [Best Practices für die Bereitstellung statischer Inhalte in Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) im Adobe Commerce Help Center.


