---
title: Benutzereinstellungen
description: Richten Sie erweiterte Inventory management-Quellen als Händler-Stores ein, um die Store Fulfillment-Lösung für Adobe Commerce zu unterstützen.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, User Account, Tools and External Services
exl-id: eb735bef-c339-4d0b-b3e7-10328915725b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Benutzereinstellungen

Store-Hilfe-App-Benutzer werden in Adobe Commerce verwaltet. Diese Benutzer interagieren jedoch nicht direkt mit Adobe Commerce. Die Benutzerverwaltung ist in Adobe Commerce konfiguriert, um sichere Verbindungen zwischen Adobe Commerce und der App zu ermöglichen.

Das Benutzermodell &quot;Store Fulfillment App User&quot;ist von anderen Adobe Commerce-Benutzermodellen getrennt. Die App verwaltet ihr eigenes Berechtigungsmodell über Benutzerrollen und Benutzer, die allen oder bestimmten Orten zugewiesen werden können. Die folgenden Berechtigungen werden unterstützt: Abwählreihenfolge, Abgabereihenfolge und Reduzierung der Elementmenge (und Abbruch).

>[!TIP]
>
>Für optimale Ergebnisse: [Verbindung konfigurieren](connect-set-up-service.md) bevor Sie Benutzer und Berechtigungen für Store Associates hinzufügen, die die Store-Hilfe-App verwenden.

## Store Assist App - Benutzerrollen

Erstellen Sie bei der ersten Einrichtung der Store-Hilfe-App durch den Benutzer Benutzerrollen, um die Benutzerberechtigungen für die Store-Hilfe-App anzupassen. Sie können beispielsweise verschiedene Rollen für Store-Manager erstellen und Verknüpfungen speichern und verschiedene Rollenressourcen zuweisen, um Berechtigungen für jeden Benutzertyp zu verwalten.

Konfigurieren von Benutzerrollen aus **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Rolleninformationen

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Benutzer aktivieren oder deaktivieren. | Global | Ja |

### Rollenressourcen

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Liste der verfügbaren Berechtigungsgruppen, die einer Benutzerrolle zugewiesen werden können. Derzeit sind für die Lösung zur Store-Erfüllung keine unterschiedlichen Berechtigungsstufen für Ressourcenrollen definiert. Alle Benutzerrollen haben denselben Ressourcenzugriff. | Global | Ja |

## Store Assist - Benutzerinformationen

Verwalten Sie Benutzerprofile der Store-Hilfe-App über die Admin System-Einstellungen:  **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Benutzer aktivieren oder deaktivieren. | Global | Ja |
| **[!UICONTROL User Name]** | Benutzername, der dem Benutzer zugeordnet ist | Global | Ja |
| **[!UICONTROL First Name]** | Vorname, der dem Benutzer zugeordnet ist | Global | Nein |
| **[!UICONTROL Last Name]** | Nachname, der dem Benutzer zugeordnet ist | Global | Nein |
| **[!UICONTROL Role]** | Mit dem Benutzer verknüpfte Rolle | Global | Nein |
| **[!UICONTROL Access to all locations]** | Weisen Sie Benutzern Zugriff auf alle Stores zu oder wählen Sie einzelne Stores aus. | Global | Nein |
| **Gebietsschema der Benutzeroberfläche** | Wenn Ihr Store mehrere Sprachen hat, setzen Sie &quot;Interface Locale&quot;auf die Sprache, die für die Admin-Oberfläche verwendet werden soll. | Global | Nein |
| **Aktiv ab** | Um ein Startdatum festzulegen, wählen Sie das Kalendersymbol aus. | Global | Nein |
| **Aktiv bis** | Legen Sie das Ablaufdatum fest, indem Sie auf das Kalendersymbol klicken. Das Festlegen eines Ablaufdatums ist nützlich, um temporäre Benutzer- oder Rollenzuweisungen einzurichten. Nach dem Ablaufdatum ändert sich der Benutzerkontenstatus in `Inactive`, aber das Konto kann bei Bedarf dennoch aktualisiert werden. | Global | Nein |
