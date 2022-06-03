---
title: Onboarding-Übersicht
description: '"Verbinden Sie Ihre [!DNL Commerce] -Instanz auf [!DNL Store Fulfillment Manager] Service durch Ausführung einiger Onboarding-Schritte."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# Onboarding-Übersicht

Integrierte Store-Erfüllung durch Installation der Erweiterung in Ihrer Commerce-Instanz und Konfiguration der API-Verbindungen. Diese Verbindungen ermöglichen die Kommunikation und Datensynchronisation zwischen Ihrer Commerce-Instanz, Drittanbietersystemen für die Lagerbestandsverwaltung und der Store-Hilfe-App.

Nachdem Sie das Onboarding abgeschlossen haben, konfigurieren und verwalten Sie die Lösung über den Commerce Admin

![[!DNL Store Fulfillment Service] Konfiguration in der Admin-Ansicht](assets/store-fulfillment-admin-home.png)

## Onboarding-Übersicht

1. Installieren Sie die Erweiterung Store Fulfillment by Walmart Technologies für Adobe Commerce.

1. Aktivieren Sie über den Administrator die Lösung und füllen Sie die allgemeine Konfiguration für die Integration und die aktiven Funktionen aus. Füllen Sie das Formular für die Onboarding-Aufnahme aus, um eine Verbindung zu den Fulfillment-Diensten herzustellen.

1. Konfigurieren Sie die Versandmethoden.

1. Richten Sie Quellen als Ihre physischen Stores ein und konfigurieren Sie Produkte in Ihrem Katalog.

1. Wählen Sie die E-Mail-Vorlagen aus und konfigurieren Sie sie, um die Kundenkommunikation für Online-Käufe, Käufe im Geschäft (BOPIS) zu verwalten.

1. Erstellen Sie Benutzer und Rollen für die Store Assist-App.

1. Konfigurieren Sie die Zeitpläne für Hintergrundprozesse zum Synchronisieren von Daten mit dem Fulfillment-Dienst.

## Voraussetzungen

Sie müssen die folgenden Anforderungen erfüllen, um die Lösung zu installieren, bereitzustellen und zu verwenden.

* **Commerce-Kontoinformationen**- Installieren [!DNL Channel Manager] erfordert [Commerce-Konto](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Sie benötigen eine Konto-ID und Anmeldedaten mit dem Inhaber- oder Administratorzugriff auf die [!DNL Adobe Commerce] -Instanz.

* Für [!DNL Adobe Commerce] Bei Cloud-Infrastrukturprojekten müssen Softwareinstallateure Administratorzugriff auf das Cloud-Projekt haben. Siehe [Benutzerzugriff verwalten](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Zugriff auf das Software-Archiv &quot;Store Fulfillment by Walmart Technologies&quot;(ZIP-Datei) zur Installation der Store Fulfillment-Lösung**-Während des Onboarding- und Aktivierungsprozesses bietet Ihr Kundenbetreuer Download-Zugriff auf die Installationsdatei.

* **Erlebnis mit Composer und dem[!DNL Commerce CLI]**—Siehe [Allgemeine CLI-Installation](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} für Informationen zur Verwendung dieser Tools zum Installieren und Verwalten von Erweiterungen in [!DNL Adobe Commerce] und [!DNL Magento Open Source] Plattformen.

* [!DNL Inventory Management] Erweiterung für Adobe Commerce und Magento Open Source

   Sie müssen die Inventory management-Erweiterung auf Ihrer Adobe Commerce- und Magento Open Source-Instanz installiert und aktiviert haben. In der Regel wird diese Erweiterung unter Adobe Commerce 2.3.x und höher standardmäßig installiert und aktiviert. Weitere Informationen finden Sie unter [Installieren von Inventory management](https://devdocs.magento.com/extensions/inventory-management/) in der Adobe Commerce Developer-Dokumentation.

## Anforderungen an die Plattform und Version

Die [!DNL Store Fulfillment] -Lösung ist für Adobe Commerce-Kunden auf den folgenden Plattformen verfügbar.

* Adobe Commerce über Cloud-Infrastruktur (ECE)
* Adobe Commerce vor Ort (EE)

Die Store Fulfillment-Lösung ist mit den folgenden Softwareversionen kompatibel.

**Softwarekompatibilität**

| **Software** | **Mindestversion** | **Maximale Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2,4,0 | 2,4,4 |
| Verfasser | 1.x | 2.x |
| MariaDB | Artikel 10 Absatz 2 | Artikel 10 Absatz 4 |
| MySQL | 5,7 | 8,0 |
| PHP | 7,4 | 8,1 |

Detaillierte Anforderungen finden Sie unter Adobe Commerce . [Systemanforderungen](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) in der Entwicklerdokumentation.

### Geschäftsanforderungen

Ihr Unternehmen muss die folgenden Mindestkriterien erfüllen, um die Store Fulfillment-Lösung zu implementieren.

* Nur in den USA ansässige Unternehmen

* B2C-Einzelhändler, CPG-Hersteller, die D2C verkaufen, oder Distributoren, die D2C oder kleine Unternehmen verkaufen

* Mindestens ein physisches Lager oder Lager

* Verwalten des Produktbestands mit Inventory management für Adobe Commerce (d. h. MSI)

* Möglichkeit zur Konsortimentierung des Händlerinventars

* Store-Wi-Fi-Verfügbarkeit an allen Standorten, die die Store Fulfillment-Lösung unterstützen

* Store- und Warehouse-Mitarbeiter haben während ihres Verlags Zugriff auf Mobilgeräte mit iOS oder Android, die entweder persönlich oder vom Händler bereitgestellt werden

* Produkte, die mit der Store Fulfillment-Lösung verwaltet werden, müssen über Produktattribute verfügen, die entweder einen SKU- oder einen UPC-Produktcode enthalten
