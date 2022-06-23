---
title: Allgemeine Konfiguration
description: Konfigurieren allgemeiner Einstellungen zum Aktivieren von [!DNL Store Fulfillment] für Ihren Laden. Konfigurieren Sie globale Erweiterungseinstellungen, Systemeinstellungen für die Protokollierung, Datensynchronisation und Sicherheit. Stellen Sie wichtige Daten bereit, um die Integration zwischen Adobe Commerce und Store Fulfillment-Diensten zu ermöglichen.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '2413'
ht-degree: 0%

---

# Allgemeine Konfiguration

Konfigurieren Sie in Adobe Commerce Admin allgemeine Konfigurationseinstellungen, um [!DNL Store Fulfillment] Dienste für Ihren Store konfigurieren, globale Erweiterungseinstellungen konfigurieren und Schlüsseldaten für die Integration bereitstellen, indem Sie die [!UICONTROL Account Credentials].

Die Integration muss mit dem Store Fulfillment-Dienst verbunden sein. Konfigurieren Sie außerdem die allgemeinen Einstellungen zur Store-Erfüllung , um Store Fulfillment-Dienste basierend auf den Fähigkeiten und operativen Anforderungen Ihres Unternehmens zu aktivieren und anzupassen.

Die allgemeine Konfiguration für [!DNL Store Fulfillment] enthält die folgenden Konfigurationseinstellungen:

- [Lösung aktivieren](#enable-the-store-fulfillment-solution)
- [Kontoanmeldeinformationen verwalten, um eine Verbindung zu Store Fulfillment-Diensten herzustellen](#account-credentials)
- [Konfigurieren der Protokollierung](#configure-logging)
- [Optionen zum Verwalten von Bestell- und Fehlersynchronisierungsvorgängen festlegen](#order-synchronization)
- [Versandoptionen für Store-Erfüllung aktivieren](#enable-store-fullment-shipping-options)
- [Konfigurieren von Sicherheits- und Authentifizierungseinstellungen für die Store Fulfillment-App](#store-fulfillment-app)
- [Verfügbarkeit und Nachrichtenkonfiguration der Versandmethode festlegen](#in-store-delivery-methods)

## Aktivieren Sie die Store Fulfillment-Lösung.

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | Aktivieren oder deaktivieren Sie die Lösung. Wenn diese Option aktiviert ist, konfigurieren und verwenden Sie Store Fulfillment-Funktionen und stellen Sie die Verbindung zwischen Ihren Adobe Commerce Store- und Store Fulfillment-Diensten her. Wenn diese Option deaktiviert ist, sind alle Funktionen zur Store-Erfüllung deaktiviert und es gibt keine Kommunikation zwischen Adobe Commerce und Store Fulfillment-Diensten. Bestellinformationen können nicht verarbeitet oder empfangen werden. | Global | Ja |

Informationen zum Abschließen dieser Einrichtung finden Sie unter **Stores > Konfiguration > Dienste > Store Fulfillment by Walmart Commerce Technologies**.

## Kontoanmeldeinformationen hinzufügen

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]** | Kann *Sandbox* oder *Produktion*:</br> Sandbox kommuniziert in einem Test mit den Erfüllungsdiensten.</br>Die Produktion kommuniziert mit einer Live-Umgebung. Verwendung **only** in der Produktion.</br>Sie erhalten eine Reihe von Anmeldeinformationen für jede Umgebung und können beide Sätze in derselben Installation verwalten. </br></br>Speichern Sie die Anmeldeinformationen, bevor Sie die Verbindung überprüfen. | Global | Ja |
| **[!UICONTROL API Server URL]** | Die URL zum Endpunkt der Walmart Store Fulfillment-API. Hierbei muss es sich um eine vollständig qualifizierte URL handeln, die Ihnen während des Onboarding-Prozesses zur Verfügung gestellt wird. Kunden von Store Fulfillment erhalten sowohl eine Sandbox als auch eine Produktions-URL. Stellen Sie sicher, dass Sie die vollständige URL kopieren/einfügen, einschließlich des Schrägstrichs &quot;/&quot;. | Global | Ja |
| **[!UICONTROL Token Auth Server URL]** | Die URL zum Endpunkt &quot;Walmart Store Fulfillment Authentication&quot;. Der Wert muss die vollständig qualifizierte URL sein, die Ihnen während des Onboarding-Prozesses zur Verfügung gestellt wird. Sie erhalten sowohl eine Sandbox als auch eine Produktions-URL. Stellen Sie sicher, dass Sie die vollständige URL kopieren/einfügen, einschließlich Schrägstrich `/`&quot;. | Global | Ja |
| **[!UICONTROL Merchant Id]** | Ihre eindeutige Händlerkennung (Mandantenkennung), die Ihnen während des Onboarding-Prozesses zur Verfügung gestellt wird. Ihre ID wird verwendet, um Ihre Bestellungen zu leiten und sicherzustellen, dass Ihre Händler sie erhalten. | Global | Ja |
| **[!UICONTROL Consumer Id]** | Ihre eindeutige Integrations-ID. Dies wird Ihnen während des Onboarding-Prozesses zur Verfügung gestellt. Es ändert sich nicht. Sie wird verwendet, um die gesamte Kommunikation mit den Fulfillment-Diensten zu authentifizieren. | Global | Ja |
| **[!UICONTROL Consumer Secret]** | Ihr eindeutiger Integrationsschlüssel. Dies wird Ihnen während des Onboarding-Prozesses zur Verfügung gestellt. Sie wird verwendet, um die gesamte Kommunikation mit den Fulfillment-Diensten zu authentifizieren. | Global | Ja |

Nachdem Sie die Kontoanmeldeinformationen konfiguriert haben, wählen Sie **[!UICONTROL Validate Credentials]** zum ersten Mal eine Verbindung zum Fulfillment-Webdienst zu überprüfen und herzustellen.

## Konfigurieren der Protokollierung

Wenn die Protokollierung aktiviert ist, kann Ihre Protokolldatei schnell erweitert werden. Achten Sie darauf, die Protokollierung zu aktivieren, damit Sie bei Bedarf nur für kurze Zeit aktivieren können, um Antwortzeitprobleme in Produktionsumgebungen zu vermeiden.

Bitten Sie den Systemadministrator, Ihre Umgebungen so zu konfigurieren, dass die Ausnahmebehandlung zugelassen wird, damit API-bezogene Ausnahmen über die Firewall oder den Cache erfasst werden können. Sie können Ihren Systemadministrator auch bitten, eine Protokollrotation für diese Datei einzurichten, um die Größe zu minimieren.

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Debug-Modus** | Der Debug-Modus wird verwendet, um die protokollierte Aktivität innerhalb der Integration zu erhöhen. Wenn diese Option deaktiviert ist, werden keine Debugging-Informationen protokolliert. Wenn diese Option aktiviert ist, werden alle Debugging-Informationen protokolliert.</br> Alle protokollierten Daten befinden sich in der Datei: `var/log/walmart-bopis.log` | Global | Nein |

## Verwalten der Auftragssynchronisierung

Konfigurieren Sie die Einstellungen für die Verwaltung der Fehlerbehandlung bei der Bestellsynchronisierung, Katalogattribute, die beim Auswählen von Bestellungen für das Scannen von Barcodes verwendet werden sollen, und konfigurieren Sie die Stapelgrößen für die Warteschlange zur Erfüllung von Lageraufträgen.

Details zu Vorgängen zur Bestellsynchronisierung finden Sie im Dashboard Warteschlangenverwaltung für die Store-Ausführung im Admin (
**[!UICONTROL System > Tools > Store Fulfillment Queue]**).

### Umgang mit Synchronisierungsfehlern

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Kritischen Fehler erneut versuchen** | Gibt die Wiederholungsversuche für einen Synchronisierungsvorgang für Datensätze an, nachdem ein kritischer Fehler aufgetreten ist.</br></br>Kritische Fehler treten immer dann auf, wenn die Integration keine positive Antwort vom Fulfillment-Dienst erhält. Dies kann vorkommen, wenn der Dienst ausfällt oder die gesendeten Bestelldaten einen Fehler aufweisen.</br></br>Wenn die Wiederholungsschwelle erreicht ist, bleibt das Element in der Warteschlange, wird aber nicht erneut verarbeitet. Alle Elemente anzeigen, deren Fehler auftreten **[!UICONTROL System > Tools > Store Fulfillment Queue]** Verwaltung in der Admin-Konsole. Wenden Sie sich an Ihren Kundenbetreuer, um eine Fehlerbehebung bei konsistent fehlerhaften Elementen durchzuführen. | Global | Nein |
| **E-Mail zur Fehlerbenachrichtigung aktivieren** | Aktivieren Sie Fehlerbenachrichtigungen, um eine E-Mail zu erhalten, wenn die [!UICONTROL Retry Critical Error Threshold] wird für eine Bestellung erreicht. Die Benachrichtigung enthält alle verfügbaren Details zum Fehler. | Global | Nein |
| **E-Mail zur Fehlerbenachrichtigung an senden** | Eine kommagetrennte Liste von Empfänger-E-Mail-Adressen für Fehlerbenachrichtigungen. | Global | Nein |
| **E-Mail-Vorlage für die Bestellsynchronisierung** | Gibt die E-Mail-Vorlage an, mit der Empfänger über Fehler bei der Bestellsynchronisierung benachrichtigt werden. Eine Standardvorlage wird bereitgestellt. Die Anpassung wird nicht unterstützt. | Store-Ansicht | Nein |

### Auftragssynchronisierung

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]** | Das Katalogattribut, das den scannbaren Code für die entsprechenden Elemente an Ihren Händlern speichert.</br></br>Wenn Sie nur über einen vorhandenen Händler-Standort verfügen, verwenden Sie wahrscheinlich UPC-Codes, während Ihr E-Commerce-Kanal Produkte nach SKU identifiziert. Wenn dies Ihr Szenario ist, wählen Sie das Katalogattribut aus, das den UPC-Code enthält.</br></br>Diese Einstellung stellt sicher, dass an Ihren Händler gesendete Bestellungen Listenelemente mit der richtigen Kennung speichern, damit Storeverknüpfer Elemente während des Pickings genau überprüfen können.</br></br>Wenn Sie sich nicht sicher sind, fragen Sie bei Ihren Fulfillment-Mitarbeitern in der Shipping and Picking-Abteilung nach, welches Attribut gesendet werden soll. Möglicherweise müssen Sie dem Adobe Commerce-Produktattributsatz das entsprechende Attribut hinzufügen, wenn das Attribut derzeit nicht in der Datenbank enthalten ist. | Webseite | Ja |
| **[!UICONTROL Barcode Type]** | Das Katalogattribut, das die Barcode-Quelle für die entsprechenden Elemente an Ihren Händlern speichert.</br></br>Diese Einstellung stellt sicher, dass an Ihren Händler gesendete Bestellungen Listenelemente mit der richtigen Kennung speichern, damit Storeverknüpfer Elemente während des Pickings genau überprüfen können. Zu den Optionen gehören SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.</br></br>Wenn Sie sich nicht sicher sind, wählen Sie die Option aus, die den in Ihrer [!UICONTROL Barcode Source] -Attribut. Speicherverknüpfungen können Elemente weiterhin manuell über ihre Auswahlliste zuordnen. | Webseite | Ja |
| **[!UICONTROL Max Number of Items]** | Die maximale Anzahl von Elementen, die gleichzeitig aus der Warteschlange für die Store-Erfüllung gesendet werden.</br></br>BOPIS-Bestellungen werden in regelmäßigen Abständen in Stapeln an den Erfüllungsdienst gesendet. Mit dieser Einstellung können Sie die Größe des Batches steuern.</br></br>Der Standardwert ist 100 Elemente. Abhängig von Ihrer Bestellmenge und -kapazität müssen Sie diesen Wert möglicherweise nach oben oder unten anpassen. | Global | Nein |


## Versandoptionen für Store-Erfüllung aktivieren

Konfigurieren Sie die Versandoptionen Store-Erfüllung , die die Verfügbarkeit der Optionen für die In-Store-Abholung und den Home-Versand für Ihre Adobe Commerce-Stores bestimmen.

### Zu Lager Schiff

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | Die Einstellung von Schiff zu Geschäft nutzt Ihre vorhandenen Funktionen von Schiff zu Speicher. Wenn Sie Inventory management verwenden oder Bestellungen an Händlern ohne Inventar über Bestandsübertragungen zwischen Lagern akzeptieren und erfüllen können, setzen Sie diese Option auf `Yes`.</br></br>Wenn Sie die Option &quot;Schiff zu Laden&quot;nicht unterstützen oder nicht anbieten möchten, setzen Sie `No`. Wenn diese Option deaktiviert ist, sind Elemente in Ihrem Katalog mit einem Nullbestand für einen Händlerspeicher oder Elemente, die unter dem Wert [!DNL Out of Stock Threshold], werden nicht mit Optionen zur In-Store-Abholung angeboten.</br></br>Dies ist eine globale Einstellung, die pro Händler-Standort angepasst werden kann. | Global | Nein |

### Aus dem Geschäft verschicken

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | Aktiviert oder deaktiviert die Option Home Delivery in Ihren Händlern. Wenn diese Option aktiviert ist, werden Ihre Händlerstätten zusammen mit anderen zugewiesenen Quellen im Lager betrachtet, das mit Ihrer Website verknüpft ist.</br></br>In standardmäßigen Inventory management-Diensten wird die [!DNL Ship from Store] ist eine Option, die inhärent ist und nicht deaktiviert werden kann. Mit der Lösung Store Fulfillment haben Sie die Möglichkeit, sie zu aktivieren oder zu deaktivieren.</br></br>Dies ist eine globale Einstellung. Sie können diese Einstellung auch für jeden Händler anpassen. | Global | Nein |


## Verwalten von Store Fulfillment App-Benutzerkonten und -Berechtigungen

Konfigurieren Sie die Einstellungen für das Benutzerkonto der Store Fulfillment App und die Kennwortsicherheit sowie die Zwei-Faktor-Authentifizierung.

### App-Sicherheit

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]** | Der Zeitraum in Sekunden, in dem eine Store-assoziierte Benutzersitzung vor der automatischen Abmeldung aktiv bleibt. Gültige Werte liegen zwischen 60 und 31536000. | Global | Nein |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | Gibt die Anzahl fehlgeschlagener Anmeldeversuche an, die zulässig sind, bevor ein Storeverknüpfer aus seinem Konto ausgeschlossen wird.</br></br>Um die Kontosperrung zu deaktivieren, setzen Sie den Wert auf 0. | Global | Nein |
| **[!UICONTROL Lockout Time (minutes)]** | Anzahl der Minuten, in denen ein Konto nach einem Anmeldefehler gesperrt werden soll. | Global | Nein |
| **[!UICONTROL Force Password Change]** | Bestimmt, ob eine Änderung des Benutzerkennworts erforderlich ist.</br></br>`Yes`: Der Benutzer muss nach der Kontoeinrichtung sein Kennwort ändern.</br>`No`: empfiehlt dem Benutzer, das Kennwort nach der Kontoeinrichtung zu ändern. | Global | Nein |
| **Kennwortlebensdauer** | Die Anzahl der Tage, in denen ein Kennwort vor einer erforderlichen Kennwortänderung gültig bleibt. Lassen Sie es leer, um diese Option zu deaktivieren. | Global | Nein |

### Zweifaktorauthentifizierung

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **APP User 2FA** | Aktivieren oder deaktivieren Sie die Zwei-Faktor-Authentifizierung für Store-Zuordnung. Wenn diese Option aktiviert ist, wird der Storeverknüpfer aufgefordert, ein einmaliges Kennwort anzugeben, das von einem Authentifizierungsanbieter generiert wurde. | Global | Nein |
| **APP 2FA-Richtlinie** | Legt die Durchsetzungsrichtlinie für die Authentifizierung mit zwei Faktoren fest.</br></br>**[!UICONTROL Optional]**: Der Storeverknüpfer kann die Authentifizierung mit zwei Faktoren umgehen, wenn kein Provider festgelegt ist.</br></br>**[!UICONTROL Mandatory]**: Das Store-Paar ist erforderlich, um die Authentifizierung mit zwei Faktoren abzuschließen. | Global | Nein |
| **2FA-Anbieter** | Wählen Sie einen oder mehrere Authentifizierungsanbieter-Dienste aus, um Storeverknüpfungen anzubieten. Um die Authentifizierung mit zwei Faktoren einzurichten, müssen Store-Associates die Authentifizierungs-App von einem der verfügbaren Anbieter installieren, die auf ihren Mobilgeräten installiert sind. | Global | Nein |

### Versandmethoden

Store Fulfillment funktioniert durch Erweiterung des nativen Adobe Commerce [!DNL In-Store Delivery] Funktionen.
Nach der Installation der Erweiterung sind zusätzliche Admin-Konfigurationsoptionen für Bereitstellungsmethoden im Store verfügbar. Konfigurieren Sie diese zusätzlichen Optionen über den Administrator, indem Sie **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

In den Einstellungen für die Store-Erfüllung können Sie die folgenden Versandmethoden für In-Store-Abholaufträge konfigurieren.

- **Abholung im Geschäft**—Angebotsoptionen für den In-Store-Versand während des Checkout-Prozesses Dies ist das häufigste Bereitstellungsszenario für BOPIS-Bestellungen.

- **Kehrseite abholen**-Angebotsoptionen für Kunden, die an einem Store-Speicherort parken und ihre Bestellung von einem Store-Mitarbeiter an sie senden lassen.

#### Konfiguration der Bereitstellungsmethoden

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | Aktivieren oder deaktivieren Sie die Option &quot;In-Store-Abholung&quot;, die beim Checkout für Kunden verfügbar ist, die die Abholung im Geschäft auswählen. Wenn die In-Store-Abholung deaktiviert ist, wird die Option nicht angezeigt.</br></br>Diese globale Einstellung gilt für alle Einzelhandelsspeicherorte. Wenn diese Option aktiviert ist, können Sie sie selektiv am Speicherort des Einzelhandels deaktivieren. | Webseite | Nein |
| **Aktivieren der aktuellen Erfassung** | Aktivieren oder deaktivieren Sie die Option &quot;Cursor-Seitenabruf&quot;während des Checkout-Prozesses für Kunden, die die Store-Abholung auswählen.</br></br>Diese globale Einstellung gilt für alle Einzelhandelsspeicherorte. Wenn diese Option aktiviert ist, können Sie sie selektiv am Speicherort des Einzelhandels deaktivieren. | Webseite | Nein |

Weitere Informationen zum Anpassen der Versandmethoden an ausgewählten Einzelhandelsstandorten finden Sie unter **Konfiguration des Einzelhandelsspeichers**.

#### Konfiguration des Titels der Bereitstellungsmethode

<table>
<thead>
<tr>
<th><strong>Feld</strong></th>
<th><strong>Beschreibung</strong></th>
<th><strong>Anwendungsbereich</strong></th>
<th><strong>Erforderlich</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Startseite - Versandtitel</strong></td>
<td>Gibt den Titel an, der für die Option "Home Delivery"im Produkt-, Warenkorb- und Checkout-Bereich angezeigt werden soll. Der Home-Versand bezieht sich auf die standardmäßigen Versandfunktionen von Adobe Commerce, von einem Warehouse über einen Frachtführer direkt zur vom Kunden angegebenen Lieferadresse.</br></br>Dieses Etikett hat keine Auswirkungen auf den ausgewählten Versandunternehmen oder dessen verfügbare Versandmethodenbeschriftungen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Startseite - Versandbeschreibung</strong></td>
<td>Eine optionale Beschreibung, die angezeigt wird, sobald der Titel des Home-Versands für Kunden angezeigt wird. Meistens handelt es sich bei der Beschreibung um eine statische Nachricht, mit der Sie Ihre Versandversprechen kommunizieren können. Beispiele:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Store Pickup Title</strong></td>
<td>Wenn einem Kunden Versandoptionen angezeigt werden und eine In-Store-Abholung verfügbar ist, wird dieser Titel angezeigt.</br></br>Sie können diese Bezeichnung anpassen, die in den Bereichen Produkt, Warenkorb und Checkout angezeigt wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Store Pickup-Beschreibung</strong></td>
<td>Wo auch immer der Store-Abholtitel angezeigt wird, können Sie optional eine Beschreibung einfügen. Diese statische Nachricht hilft bei der Verbesserung der Kundenkommunikation im Zusammenhang mit dem Store-Abruf. Beispiele:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>In-Store-Abruf-Titel</strong></td>
<td>Wenn die In-Store-Abholung aktiviert ist, wird diesen Titel Kunden als Bereitstellungsoption "Datenabruf speichern"angezeigt. Sie können den Titel anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<tr>
<td><strong>Cursor-Abruf-Titel</strong></td>
<td>Wenn die Option "Cumulative Pickup"aktiviert ist, wird die Option den Kunden als eine Art Store-Abruf-Bereitstellungsoption angezeigt. Hier können Sie den Titel anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Anweisungen zur In-Store-Abholung</strong></td>
<td>Wenn eine Bestellung in Ihren Einzelhandelsgeschäften abgeholt werden kann, wird der Kunde per E-Mail benachrichtigt. Wenn der Kunde ausgewählt hat [!DNL In-Store Pickup] während des Auscheckens können Sie hier die Pickup-Anweisungen anpassen.</br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsspeicherorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Anweisungen zur automatischen Erfassung</strong></td>
<td>Gibt benutzerdefinierte Anweisungen zum Bestellabruf an, die in E-Mail-Benachrichtigungen von Kunden für aktuelle Abrufbestellungen enthalten sind.</br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsspeicherorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Geschätzte Abruf-Vorlaufzeit</strong></td>
<td>Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, erfüllt und abgeholt werden kann. Diese Informationen werden dem Kunden angezeigt, wenn er einen Einzelhandelsstandort für die Option "Store Pickup-Versand"auswählt.</br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsstandorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Geschätzte Zeitbeschriftung für die Abholung</strong></td>
<td>Zeigt die geschätzte Zeit an, bis eine Bestellung für die Kundenabholung verfügbar ist. Diese Informationen werden Kunden angezeigt, wenn sie einen Einzelhandelsspeicherort für die Option "Store Pickup-Versand"auswählen.</br></br>Bei der Anpassung dieser Beschriftung können Sie den Code verwenden <code>%1</code> um <strong>Geschätzte Abruf-Vorlaufzeit</strong>.Beispiel:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsstandorts anpassen.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Store-Ansicht</td>
<td>Nein</td>
<tr>
<td><strong>Haftungsausschluss zur Abholzeit</strong></td>
<td>Der Inhalt, der auf der Produktseite in der QuickInfo angezeigt wird, in der Store-Stunden, Feiertage, unerwartete Schließungen usw. aufgelistet sind</td>
<td>Store-Ansicht
</td>
<td>Nein
</td>
</tr>
</tbody></table>

#### Konfiguration der Lagerverfügbarkeitstitel

<table>
<thead>
<tr>
<th><strong>Feld</strong></th>
<th><strong>Beschreibung</strong></th>
<th><strong>Anwendungsbereich</strong></th>
<th><strong>Erforderlich</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Auf Lager</strong></td>
<td>Wenn ein Kunde den Locator für Einzelhandelsgeschäfte verwendet, wird für jeden Standort die Lagerverfügbarkeit für die aktuellen Artikel angezeigt.</br></br>Hier können Sie die Statusbezeichnung "auf Lager"anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Nicht auf Lager</strong></td>
<td>Wenn ein Kunde den Locator für Einzelhandelsgeschäfte verwendet, wird für jeden Standort die Lagerverfügbarkeit für alle aktuellen Elemente angezeigt.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise auf Lager</strong></td>
<td>Wenn ein Kunde den Locator für Einzelhandelsgeschäfte verwendet, wird die Lagerverfügbarkeit für alle aktuellen Elemente für jeden Standort angezeigt.</br></br>Hier können Sie die Statusbezeichnung "teilweise auf Lager"anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>
