---
title: Konfiguration von Merchant Stores
description: Richten Sie erweiterte Inventory management-Quellen als Händler ein.
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Konfiguration von Merchant Stores (Quelle)

Diese Lösung verbessert die nativen Inventory management-Funktionen, indem sie Lagerquellen mit betriebsorientierten Funktionen für Händler erweitert.

- Geografische Koordinaten für den Speicherort hinzufügen
- Quelle als [!DNL Store Pickup Location] und legen Sie die verfügbaren Versandfunktionen fest (Versand an Lager, Versand aus Speicher).
- Geben Sie die verfügbaren Pickup-Optionen (im Store oder direkt am Bildschirm), benutzerdefinierte Pickup-Anweisungen und andere Informationen an, um den Kunden Pickup-Details und -Anweisungen mitzuteilen.

Die Begriffe _source_ und _Kaufspeicherort_ werden synonym verwendet. Alle Datensätze sind Inventarquellen, aber je nach Konfigurationseinstellungen können auch Verkaufs- oder Verkaufsspeicherorte verwendet werden.

Verwalten Sie die Konfiguration von Merchant Stores über den Administrator: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

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
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Breitengrad der Koordinate des Standorts des Händlers. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen. | Global | Ja |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Längenkoordinate des Händlerstandorts. Diese erforderlichen Informationen werden bei der Positionierungs- und Zuordnungsplatzierung im Storefront-Erlebnis verwendet. Der Wert muss mit der exakten Adresse des Stores übereinstimmen, um die Validierung zu bestehen. | Global | Ja |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Geben Sie die Quelle als verfügbaren Speicherort für die Speicherabnahme an. Diese Einstellung bestimmt, ob die Quelle synchronisiert und Besuchern angezeigt wird. | Global | Nein |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Konfigurieren Sie die Funktionen von Schiff zu Speicher auf der Quellebene. Weitere Informationen finden Sie unter [Allgemeine Konfiguration](enable-general.md) Option, **[!UICONTROL Enable Ship To Store]**. | Global | Nein |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Konfigurieren Sie die Funktionen für den Versand aus dem Speicher auf der Quellebene. Weitere Informationen finden Sie unter [Allgemeine Konfiguration](enable-general.md) Option, [!UICONTROL Enable Ship From Store] | Global | Nein |

{style=&quot;table-layout:auto&quot;}

## Konfiguration des Pickup-Standorts

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Eine von zwei Pickup-Optionen. [!DNL In-Store Pickup] bezieht sich auf die Möglichkeit, einem Kunden die Eingabe des Händlers zum Abrufen seiner Bestellung zu ermöglichen. </br></br>Wenn diese Option aktiviert ist, wird diese Option dem Kunden beim Checkout angezeigt. </br></br>Diese Option setzt auch die globale Konfiguration außer Kraft, um [!UICONTROL Enable In-store Pickup] , die auf der [!UICONTROL Delivery Method] für [!UICONTROL In-store Pickup] | Global | Nein |
| **Anweisungen zur In-Store-Abholung**</br>`Extension Attribute: store_pickup_instructions` | Eine anpassbare Nachricht, die dem Kunden im **Bestellbereit für Abholung im Store** E-Mail-Benachrichtigung. | Global | Nein |
| **Curb zulassen**</br>`Extension Attribute: curbside_enabled` | Eine von zwei Pickup-Optionen. Die aktuelle Auslieferung ermöglicht es einem Kunden, sein Fahrzeug an einem bestimmten Ort im Kaufhaus zu parken. In diesem Szenario wird die Bestellung dem Kunden von einem Store-Mitarbeiter zugestellt. </br></br>Wenn diese Option aktiviert ist, wird diese Option dem Kunden beim Checkout angezeigt. Außerdem kann der Kunde während des Check-In-Verfahrens aufgefordert werden, seinen Fahrzeug- und Parkplatz zu beschreiben. </br></br>Diese Option setzt auch die globale Konfiguration außer Kraft, um **Aktivieren der aktuellen Erfassung** , die auf der **Versandmethode** für **In-store-Abruf** | Global | Nein |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Eine anpassbare Nachricht, die dem Kunden im [!UICONTROL Order Ready For Pickup in Store] E-Mail-Benachrichtigung. | Global | Nein |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, aufgenommen und zur Aufnahme bereit ist. </br></br>Diese Informationen werden verwendet, um geschätzte Zeiten für die Bestellabnahme an Kunden auf der Website anzuzeigen.</br></br> Durch das Festlegen dieser Option wird die globale Konfiguration für **Geschätzte Abruf-Vorlaufzeit** für die **Versandmethode** im **In-store-Abruf** Konfiguration. | Global | Nein |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Beschriftung, die die Anzahl der Minuten anzeigt, bis eine Bestellung abgeholt werden kann.</br></br> Bei der Anpassung dieser Beschriftung können Sie den Code %1 verwenden, um Ihre **Geschätzte Abruf-Vorlaufzeit**.</br></br> Durch das Festlegen dieser Option wird die globale Konfiguration für [!UICONTROL Estimated Pickup Time Label] für die [!UICONTROL Delivery Method] im [!UICONTROL In-store Pickup]. | Global | Nein |

### **Öffnungszeiten**

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | Die Zeitzone des Händlerspeicherorts. Legen Sie für jeden Tag die Öffnungs- und Abschlusszeiten fest.</br></br>Diese Einstellungen werden verwendet, um die geschätzten Abholzeiten zu optimieren und die Berichte zum Ausführungsdienst zu nutzen. | Global | Ja |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | Die Betriebszeiten für den Händlerstandort. </br></br>Diese Informationen können verwendet werden, um die geschätzten Abholzeiten und die Berichterstellung für den Vollfüllungsdienst zu optimieren. | Global | Ja |

### Optionen der Einchecken-Benutzeroberfläche konfigurieren



| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Geben Sie an, ob der Händler-Store-Standort über Ausweisungs-Parkplätze für die Cursor-Sickup verfügt. </br></br>Wenn diese Option aktiviert ist, können Sie die verfügbaren Parkplätze konfigurieren. | Global | Nein |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Geben Sie an, ob die Identifizierung des Parkplatzes für Kunden während des Einkaufs erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei der Ankunft seinen Parkplatz anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Die verfügbaren Parkplätze stehen in diesem Kaufhaus zur Verfügung. Verwenden Sie die bereitgestellte Oberfläche, um jeden Spot zu benennen.</br></br> Sie müssen nicht jeden Parkplatz benennen, sondern nur die Plätze, die für die Kulisse vorgesehen sind. Sie können beispielsweise die Zeilen A-G des Parkplatzes zur Verfügung haben, aber nur die ersten 8 Punkte von Zeile A sind für die Schnellabnahme vorgesehen. In diesem Szenario können Sie 8 Spots definieren. z. B.: A1, A2, A3 usw. | Global | Nein |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Wenn diese Einstellung aktiviert ist, kann der Kunde seinen Parkplatz während des Check-ins beschreiben. | Global | Nein |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Geben Sie an, ob die Erfassung der Fahrzeugfarbe vom Kunden während des Check-ins unterstützt werden soll. </br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Color] werden im Admin konfiguriert [Systemeinstellungen für das Check-in-Erlebnis](check-in-experience-setup.md). | Global | Nein |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Geben Sie an, ob für Kunden während des Check-ins eine Identifizierung der Fahrzeugfarbe erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei der Ankunft die Farbe seines Fahrzeugs anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Geben Sie an, ob die Erfassung von Fahrzeugen vom Kunden während des Check-ins unterstützt werden soll.</br></br> Die verfügbaren Auswahlmöglichkeiten für [!UICONTROL Car Make] werden im Admin konfiguriert [Systemeinstellungen für das Check-in-Erlebnis](check-in-experience-setup.md). | Global | Nein |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Geben Sie an, ob die Identifizierung des Fahrzeugs für Kunden während des Check-ins erforderlich ist.</br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei der Ankunft die Marke seines Fahrzeugs anzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Geben Sie an, ob die Erfassung zusätzlicher Informationen vom Kunden während des Check-ins unterstützt werden soll. | Global | Nein |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Geben Sie an, ob zusätzliche Informationen für Kunden während des Check-ins erforderlich sind. </br></br>Wenn diese Option aktiviert ist, wird der Kunde aufgefordert, bei seiner Ankunft zusätzliche Informationen einzugeben. Wenn diese Option deaktiviert ist, kann der Kunde diese Eingabe überspringen. | Global | Nein |
