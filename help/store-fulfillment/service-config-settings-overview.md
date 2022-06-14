---
title: Konfigurationsübersicht für Store Fulfillment
description: Erfahren Sie mehr über die Kategorien für die Admin-Konfigurationseinstellungen, die für die Store Fulfillment-Lösung verfügbar sind, und wie sie konfiguriert sind.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Konfigurationsübersicht für die Store-Erfüllung

In Adobe Commerce Admin werden die Konfigurationseinstellungen für Store Fulfillment Services von Walmart Commerce Technologies nach Typ kategorisiert.

**Konfigurationseinstellungen für die Store-Ausführung nach Typ**

| **Typ** | **Beschreibung** | **API konfigurierbar** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Allgemeine Konfiguration](enable-general.md) | Allgemeine Integration für die Store Fulfillment-Lösung, ihre aktiven Funktionen und Anmeldeinformationen, um eine Verbindung mit den Fulfillment-Diensten herzustellen. | Nein |
| [E-Mail-Konfiguration für Vertrieb](sales-emails.md) | Richten Sie zusätzliche E-Mail-Vorlagen für Kundenbenachrichtigungen ein, die während des Eincheckvorgangs gesendet werden. | Nein |
| [Merchant Store-Konfiguration](merchant-store-configuration.md) | Richten Sie erweiterte Inventory management-Quellen als Händler ein. | Ja |
| [ProduktStock-Management](product-stock.md) | Konfigurieren Sie die für Kunden verfügbaren Merchant Stock Messaging und Funktionen. | Ja |
| [Inventory management Source Transfer](inventory-stock-transfer.md) | Richten Sie ein neues Lager ein, übertragen Sie das Inventar aus dem Standardbestand. | Ja |
| [Konfiguration mehrerer Websites/Bereiche](multi-site-and-scope-config.md) | Konfigurieren Sie Lager und Bereitstellungsmethoden für mehrere Websites/Storebereiche. | Nein |
| [Systemkonfiguration für Hintergrundprozesse](background-processes.md) | Konfigurieren Sie die Zeitpläne für Hintergrundprozesse, die zum Synchronisieren von Daten mit den Fulfillment-Diensten verwendet werden. | Nein |
| [Speicherort und Einrichtung der Zuordnung](store-location-map-provider-setup.md) | Konfigurieren Sie die Möglichkeit, mithilfe eines Entfernungsanbieters nach Einzelhandelsgeschäften zu suchen und diese Informationen auf der SLS-Karte anzuzeigen | Ja |
| [Einrichtung des Check-in-Erlebnisses](store-location-map-provider-setup.md) | Konfigurieren Sie die Auto-Farbe und die Automake-Optionen, die während des Eincheckvorgangs verfügbar sein werden. | Ja |
| [Benutzereinstellungen](user-setup.md) | Verwalten Sie Benutzerkonten, Rollen und Berechtigungen für Storeverknüpfungen, die die Store-Hilfe-App verwenden. Bereiche. | Ja |
| [App-Einrichtung](app-setup.md) | Überprüfen Sie die verfügbaren Konfigurationen für die Store Assist App, die zum Abschließen des Onboarding-Prozesses erforderlich sind. Diese Einstellungen können nicht über den Adobe Commerce-Administrator konfiguriert werden. | Ja |


## Verwenden Sie die Konfigurationsreferenz

Zeigen Sie die Konfigurationsreferenz für jeden Einstellungstyp an, indem Sie den Typnamen im _Konfigurationseinstellungen für die Store-Ausführung nach Typ_ Tabelle.

In der Konfigurationsreferenz für jeden Typ werden die Konfigurationsdetails in einer Tabelle mit den folgenden Spaltenüberschriften angezeigt:

- **Feld** bezieht sich auf den Namen des zu konfigurierenden Felds

- **Beschreibung** liefert wichtige Details zum Zweck und Verhalten des Felds

- **Anwendungsbereich** gibt den Adobe Commerce-Konfigurationsbereich für die Einstellung an (global, website, store)

- **Erforderlich** Wert gibt an, ob ein Wert für das Feld festgelegt werden muss

Als technische Referenz können Sie auch den internen Konfigurationspfad für jedes Feld finden.
