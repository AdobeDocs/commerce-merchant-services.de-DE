---
title: Konfiguration von Merchant Stores
description: Richten Sie erweiterte Inventory management-Quellen als Händler ein.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# Konfiguration von Merchant Stores (Source)

Diese Lösung verbessert die nativen Inventory management-Funktionen, indem sie Lagerquellen mit betriebsorientierten Funktionen für Händler erweitert.

- Geografische Koordinaten für den Speicherort hinzufügen
- Geben Sie die Quelle als &quot;[!DNL Store Pickup Location]&quot; an und geben Sie die verfügbaren Versandfunktionen an (Versand an Store, Versand aus Store).
- Geben Sie die verfügbaren Pickup-Optionen (im Store oder direkt am Bildschirm), benutzerdefinierte Pickup-Anweisungen und andere Informationen an, um den Kunden Pickup-Details und -Anweisungen mitzuteilen.

Die Begriffe _source_ und _merchant store location_ werden synonym verwendet. Alle Datensätze sind Inventarquellen, aber je nach Konfigurationseinstellungen können auch Verkaufs- oder Verkaufsspeicherorte verwendet werden.

Verwalten Sie die Konfiguration &quot;Merchant Stores&quot;über den Administrator: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>Während des Einrichtungsprozesses kann es erforderlich sein, den Cache zu leeren, nachdem Sie Quellen erstellt oder vorhandene Quellen aktualisiert haben.

## **Allgemein**

<table>
<tbody>
<tr>
<th>Feld</th>
<th>Beschreibung</th>
<th>Anwendungsbereich</th>
<th>Erforderlich</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Breitengrad der Koordinate des Standorts des Händlers. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Längenkoordinate des Händlerstandorts. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Geben Sie die Quelle als verfügbaren Speicherort für die Speicherabnahme an. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Konfigurieren Sie die Funktionen von Schiff zu Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Breitengrad der Koordinate des Standorts des Händlers. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Längenkoordinate des Händlerstandorts. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Geben Sie die Quelle als verfügbaren Speicherort für die Speicherabnahme an. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Konfigurieren Sie die Funktionen von Schiff zu Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Konfigurieren Sie die Funktionen für den Versand aus dem Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
<td>Konfigurieren Sie die Funktionen für den Versand aus dem Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>



| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Breitengrad der Koordinate des Standorts des Händlers. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen. | Global | Ja |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Längenkoordinate des Händlerstandorts. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen. | Global | Ja |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Geben Sie die Quelle als verfügbaren Speicherort für die Speicherabnahme an. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird. | Global | Nein |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Konfigurieren Sie die Funktionen von Schiff zu Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), **[!UICONTROL Enable Ship To Store]**. | Global | Nein |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Konfigurieren Sie die Funktionen für den Versand aus dem Speicher auf der Quellebene. Weitere Informationen finden Sie unter der Option [Allgemeine Konfiguration](enable-general.md), [!UICONTROL Enable Ship From Store] . | Global | Nein |

{style="table-layout:auto"}

## Konfiguration des Pickup-Standorts

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Eine von zwei Pickup-Optionen. [!DNL In-Store Pickup] bezieht sich auf die Fähigkeit, einem Kunden zu erlauben, den Händlerstammspeicherort einzugeben, um seine Bestellung abzurufen. </br></br>Wenn diese Option aktiviert ist, wird diese Option dem Kunden beim Checkout angezeigt. </br></br>Diese Option überschreibt auch die globale Konfiguration in [!UICONTROL Enable In-store Pickup], die auf dem [!UICONTROL Delivery Method] für [!UICONTROL In-store Pickup] konfiguriert wurde. | Global | Nein |
| **Anweisungen zur In-Store-Abholung**</br>`Extension Attribute: store_pickup_instructions` | Eine anpassbare Nachricht, die an den Kunden in der E-Mail-Benachrichtigung **Bestellbereit für die Abholung im Store** gesendet wird. | Global | Nein |
| **Lassen Sie die aktuelle Seite**</br>`Extension Attribute: curbside_enabled` | Eine von zwei Pickup-Optionen. Die aktuelle Auslieferung ermöglicht es einem Kunden, sein Fahrzeug an einem bestimmten Ort im Kaufhaus zu parken. In diesem Szenario wird die Bestellung dem Kunden von einem Store-Mitarbeiter zugestellt. </br></br>Wenn diese Option aktiviert ist, wird diese Option dem Kunden beim Checkout angezeigt. Außerdem kann der Kunde während des Check-In-Verfahrens aufgefordert werden, seinen Fahrzeug- und Parkplatz zu beschreiben. </br></br>Diese Option überschreibt auch die globale Konfiguration in **Aktivieren der aktuellen Erfassung**, die für die **Bereitstellungsmethode** für die **In-store-Erfassung** konfiguriert wurde. | Global | Nein |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Eine anpassbare Nachricht, die dem Kunden in der [!UICONTROL Order Ready For Pickup in Store] -E-Mail-Benachrichtigung zugestellt wird. | Global | Nein |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, aufgenommen und zur Aufnahme bereit ist. </br></br>Diese Informationen werden verwendet, um geschätzte Zeiten für die Bestellabnahme an Kunden auf der Website anzuzeigen.</br></br> Durch Festlegen dieser Option wird die globale Konfiguration für die **geschätzte Abruf-Lead-Zeit** überschrieben, die für die **Bereitstellungsmethode** in der Konfiguration **In-store-Abruf** konfiguriert ist. | Global | Nein |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Beschriftung, die die Anzahl der Minuten anzeigt, bis eine Bestellung abgeholt werden kann.</br></br> Wenn Sie diese Beschriftung anpassen, können Sie den Code %1 verwenden, um Ihre **geschätzte Abruf-Vorlaufzeit** einzufügen.</br></br> Wenn Sie diese Option festlegen, wird die globale Konfiguration für [!UICONTROL Estimated Pickup Time Label] überschrieben, die für die [!UICONTROL Delivery Method] in der [!UICONTROL In-store Pickup] konfiguriert ist. | Global | Nein |

### **Öffnungszeiten**

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | Die Zeitzone des Händlerspeicherorts. Legen Sie für jeden Tag die Öffnungs- und Abschlusszeiten fest.</br></br>Diese Einstellungen werden verwendet, um die geschätzten Abrufzeiten und die Berichte zum Vollfüllungsdienst zu optimieren. | Global | Ja |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | Die Betriebszeiten für den Händlerstandort. </br></br>Diese Informationen können verwendet werden, um die geschätzten Abrufzeiten und die Berichte zum Ausführungsdienst zu optimieren. | Global | Ja |

### Optionen der Einchecken-Benutzeroberfläche konfigurieren



| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Geben Sie an, ob der Händler-Store-Standort über Ausweisungs-Parkplätze für die Cursor-Sickup verfügt. </br></br>Wenn diese Option aktiviert ist, können Sie verfügbare Parkplätze konfigurieren. | Global | Nein |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Geben Sie an, ob die Identifizierung des Parkplatzes für Kunden während des Einkaufs erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei der Ankunft seinen Parkplatz anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Die verfügbaren Parkplätze stehen in diesem Kaufhaus zur Verfügung. Verwenden Sie die bereitgestellte Oberfläche, um jeden Spot zu benennen.</br></br> Sie müssen nicht jeden Parkplatz benennen, sondern nur die Plätze, die für die Kehrseite vorgesehen sind. Sie können beispielsweise die Zeilen A-G des Parkplatzes zur Verfügung haben, aber nur die ersten 8 Punkte von Zeile A sind für die Schnellabnahme vorgesehen. In diesem Szenario können Sie 8 Spots definieren, z. B. A1, A2, A3 usw. | Global | Nein |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Wenn diese Einstellung aktiviert ist, kann der Kunde seinen Parkplatz während des Check-ins beschreiben. | Global | Nein |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Geben Sie an, ob die Erfassung der Fahrzeugfarbe vom Kunden während des Check-ins unterstützt werden soll. </br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Color] werden in den Admin [Systemeinstellungen für das Eincheckerlebnis](check-in-experience-setup.md) konfiguriert. | Global | Nein |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Geben Sie an, ob für Kunden während des Check-ins eine Identifizierung der Fahrzeugfarbe erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, die Farbe seines Fahrzeugs anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Geben Sie an, ob die Erfassung von Fahrzeugen vom Kunden während des Check-ins unterstützt werden soll.</br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Make] werden in den Admin [Systemeinstellungen für das Eincheckerlebnis](check-in-experience-setup.md) konfiguriert. | Global | Nein |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Geben Sie an, ob die Identifizierung des Fahrzeugs für Kunden während des Check-ins erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei der Ankunft die Marke seines Fahrzeugs anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Geben Sie an, ob die Erfassung zusätzlicher Informationen vom Kunden während des Check-ins unterstützt werden soll. | Global | Nein |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Geben Sie an, ob zusätzliche Informationen für Kunden während des Check-ins erforderlich sind. </br></br>Wenn diese Option aktiviert ist, wird der Kunde bei der Ankunft aufgefordert, zusätzliche Informationen einzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
