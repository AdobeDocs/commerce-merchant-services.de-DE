---
title: Allgemeine Konfiguration
description: Konfigurieren allgemeiner Einstellungen zum Aktivieren von [!DNL Store Fulfillment] für Ihren Laden. Konfigurieren Sie globale Erweiterungseinstellungen, Systemeinstellungen für die Protokollierung, Datensynchronisation und Sicherheit. Stellen Sie wichtige Daten bereit, um die Integration zwischen Adobe Commerce und Store Fulfillment-Diensten zu ermöglichen.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 0cf5a99891fb6ec0b6e446aac05e64bc97d70e7c
workflow-type: tm+mt
source-wordcount: '2543'
ht-degree: 0%

---

# Konfiguration von Store-Service und -Vertrieb

Konfigurieren [!DNL Store Fulfillment] von [!DNL Commerce] Admin , um die Erweiterung zu aktivieren, Erweiterungseinstellungen anzugeben, die Sicherheitseinstellungen für Benutzer der Store Assist-App zu konfigurieren und Optionen für Bereitstellungsmethoden festzulegen.

>[!IMPORTANT]
>
>Die Konfiguration des Store Fulfillment-Dienstes gilt erst, nachdem Sie Ihre Adobe Commerce-Instanz mit der [!DNL Store Fulfillment] App. Siehe [Store-Erfüllung verbinden](connect-set-up-service.md).

## Einstellungen für Store Fulfillment-Dienste verwalten

Verwalten Sie Einstellungen für Store Fulfillment-Dienste über [!DNL Commerce Admin Store Configuration] Menü.

- Aktivieren Sie die Erweiterung, konfigurieren Sie globale Einstellungen und legen Sie Sicherheitsoptionen für Benutzerverbindungen und Konten der Store Assist-App fest, indem Sie **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

   ![Konfiguration der Admin Store-Dienste für Store-Erfüllung](assets/store-services-admin-sf-config.png)

- Versandmethoden konfigurieren, indem Sie **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

   ![Admin Store-Verkaufskonfiguration für Store-Erfüllung](assets/store-sales-admin-sf-deliver-config.png)

## Grundlegende Einstellungen

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>Der Preis, den Sie dem Kunden für die In-store-Abholung berechnen. Der Standardwert ist null.</td>
<td>Webseite</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>Der Radius (in Kilometern), der verwendet werden soll, wenn ein Käufer nach einer Speicherabholposition im Storefront-Checkout sucht. Die Suchergebnisse geben nur Stores zurück, die sich im angegebenen Suchradius befinden.</td>
<td>Webseite</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Meldung, die angezeigt wird, wenn ein Kunde die In-Store-Abholung für ein Element auswählt, das nicht für die In-Store-Abholung verfügbar ist. Sie können bei Bedarf den Standardtext anpassen.
</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>Die [!UICONTROL Search Radius] verwendet, wenn Sie die [Speicherort und Einrichtung der Zuordnung](store-location-map-provider-setup.md) für Adobe Commerce.

## Aktivieren Sie die Store Fulfillment-Lösung.

Aktivieren Sie die [!DNL Store Fulfillment] -Lösung, um die In-Store- und Cursor-Pickup-Funktionen zu den Einkaufs- und Checkout-Erlebnissen in Ihrer Adobe Commerce-Storefront hinzuzufügen.

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Lösung. Wenn diese Option aktiviert ist, konfigurieren und verwenden Sie Store Fulfillment-Funktionen und stellen Sie die Verbindung zwischen Ihrem Adobe Commerce-Store und her. [!DNL Store Fulfillment] Dienste. Wenn diese Option deaktiviert ist, sind alle Funktionen zur Store-Erfüllung deaktiviert und es gibt keine Kommunikation zwischen Adobe Commerce und Store Fulfillment-Diensten. Bestellinformationen können nicht verarbeitet oder empfangen werden.</td>
<td>Global</td>
<td>Ja</td>
</tr>
</tbody>
</table>

## Kontoanmeldeinformationen hinzufügen

<table>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Wählen Sie entweder <i>[!UICONTROL Sandbox]</i> oder <i>[!UICONTROL Production]</i><br></br>Auswählen [!UICONTROL Sandbox] ermöglicht die Kommunikation mit Fulfillment-Diensten in einer Testumgebung.<br></br>Auswählen [!UICONTROL Production] ermöglicht die Kommunikation mit Fulfillment-Diensten in einer Live-Umgebung.<br></br>Sie erhalten eine Reihe von Anmeldeinformationen für jede Umgebung und können beide Sätze in derselben Installation verwalten. <br></br>Speichern Sie die Anmeldeinformationen, bevor Sie die Verbindung überprüfen.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Die URL zum Endpunkt der Walmart Store Fulfillment-API. Hierbei muss es sich um die vollständig qualifizierte URL handeln, die während des Onboarding-Prozesses bereitgestellt wird. Kunden von Store Fulfillment erhalten sowohl eine Sandbox als auch eine Produktions-URL. Stellen Sie beim Hinzufügen der Werte sicher, dass Sie die vollständige URL kopieren und einfügen, einschließlich des nachfolgenden Schrägstrichs "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Die URL zum Endpunkt "Walmart Store Fulfillment Authentication". Der Wert muss die vollständig qualifizierte URL sein, die während des Onboarding-Prozesses bereitgestellt wird. Sie erhalten sowohl eine Sandbox als auch eine Produktions-URL. Stellen Sie beim Hinzufügen der Werte sicher, dass Sie die vollständige URL kopieren und einfügen, einschließlich des nachfolgenden Schrägstrichs "/".</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Ihre eindeutige Händler-(Mandanten-)ID, die während des Onboarding-Prozesses bereitgestellt wird. Diese ID wird verwendet, um Bestellungen weiterzuleiten, um sicherzustellen, dass Ihre Händler sie erhalten.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Die eindeutige Integrations-ID, die während des Onboarding-Prozesses bereitgestellt wird. Diese ID wird verwendet, um die gesamte Kommunikation zwischen Adobe Commerce und Store-Fulfillment-Services zu authentifizieren.</td>
<td>Global</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>Der eindeutige Integrationsschlüssel, der beim Onboarding bereitgestellt wird. Dieser Schlüssel wird verwendet, um die gesamte Kommunikation zwischen Adobe Commerce und dem Store-Fulfillment-Dienst zu authentifizieren.</td>
<td>Global</td>
<td>Ja</td>
</tr>
</table>

Nachdem Sie die [!UICONTROL Account Credentials]auswählen <strong>[!UICONTROL Validate Credentials]</strong> , um erstmals eine Verbindung zum Store-Fulfillment-Dienst zu überprüfen und herzustellen.

## Konfigurieren der Protokollierung

Protokolle für Store-Fulfillment-Dienste sind in der Protokolldatei verfügbar `var/log/walmart-bopis.log`.

Bitten Sie den Systemadministrator, Ihre Umgebungen so zu konfigurieren, dass die Ausnahmebehandlung zugelassen wird, damit API-bezogene Ausnahmen über die Firewall oder den Cache erfasst werden können.

Da die Protokolldatei der Anwendung schnell wachsen kann, aktivieren Sie bei Bedarf die Protokollierung für die Anwendung nur für kurze Zeit, z. B. bei der Fehlerbehebung von Problemen bei der Store-Erfüllung für eine [!DNL Commerce] bestellen. Diese Konfiguration verhindert Reaktionszeitprobleme in Produktionsumgebungen, die durch große Protokolldateien verursacht werden.

>[!TIP]
>
>Bitten Sie bei lokalen Installationen von Adobe Commerce Ihren Systemadministrator, eine Protokollrotation für die `var/log/walmart-bopis.log` -Datei, um die Größe zu minimieren. Informationen zu Vor-Ort-Installationen von Adobe Commerce finden Sie unter [Protokollrotation](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=en#server-settings) im _Adobe Commerce-Installationsanleitung_. Informationen zu Adobe Commerce zu Cloud-Infrastrukturprojekten finden Sie unter [Protokolle anzeigen und verwalten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Der Debug-Modus wird verwendet, um die protokollierte Aktivität innerhalb der Integration zu erhöhen. Wenn diese Option deaktiviert ist, werden keine Debugging-Informationen protokolliert. Wenn diese Option aktiviert ist, werden alle Debugging-Informationen protokolliert <br></br>Alle protokollierten Daten finden Sie in der Datei: <pre>var/log/walmart-bopis.log</pre>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Verwalten der Auftragssynchronisierung

Konfigurieren Sie die Einstellungen für die Verwaltung der Fehlerbehandlung bei der Bestellsynchronisierung, Katalogattribute, die beim Auswählen von Bestellungen für das Scannen von Barcodes verwendet werden sollen, und konfigurieren Sie die Stapelgrößen für die Warteschlange zur Erfüllung von Lageraufträgen.

Details zu Vorgängen zur Bestellsynchronisierung finden Sie im Dashboard Warteschlangenverwaltung für die Store-Ausführung im Admin (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Umgang mit Synchronisierungsfehlern

<table>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Gibt die Wiederholungsversuche für einen Synchronisierungsvorgang für Datensätze an, nachdem ein kritischer Fehler aufgetreten ist.<br></br>Kritische Fehler treten immer dann auf, wenn die Integration keine positive Antwort vom Fulfillment-Dienst erhält. Dies kann vorkommen, wenn der Dienst ausfällt oder die gesendeten Bestelldaten einen Fehler aufweisen.<br></br>Wenn die Wiederholungsschwelle erreicht ist, bleibt das Element in der Warteschlange, wird aber nicht erneut verarbeitet. Alle Elemente anzeigen, deren Fehler auftreten <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Verwaltung in der Admin-Konsole. Wenden Sie sich an Ihren Kundenbetreuer, um eine Fehlerbehebung bei konsistent fehlerhaften Elementen durchzuführen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Aktivieren Sie Fehlerbenachrichtigungen, um eine E-Mail zu erhalten, wenn die [!UICONTROL Retry Critical Error Threshold] wird für eine Bestellung erreicht. Die Benachrichtigung enthält alle verfügbaren Details zum Fehler.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Eine kommagetrennte Liste von Empfänger-E-Mail-Adressen für Fehlerbenachrichtigungen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Gibt die E-Mail-Vorlage an, mit der Empfänger über Fehler bei der Bestellsynchronisierung benachrichtigt werden. Eine Standardvorlage wird bereitgestellt. Die Anpassung wird nicht unterstützt.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</table>

### Auftragssynchronisierung

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>Das Katalogattribut, das den scannbaren Code für die entsprechenden Elemente an Ihren Händlern speichert.<br></br>Wenn Sie nur über einen vorhandenen Händler-Standort verfügen, verwenden Sie wahrscheinlich UPC-Codes, während Ihr E-Commerce-Kanal Produkte nach SKU identifiziert. Wenn dies Ihr Szenario ist, wählen Sie das Katalogattribut aus, das den UPC-Code enthält.<br></br>Diese Einstellung stellt sicher, dass an Ihre Stores gesendete Bestellungen Listenelemente mit der richtigen Kennung enthalten, sodass Storeverknüpfungen Elemente während des Pickings genau überprüfen können.<br></br>Wenn Sie sich nicht sicher sind, fragen Sie bei Ihren Fulfillment-Mitarbeitern in der Shipping and Picking-Abteilung nach, welches Attribut gesendet werden soll. Möglicherweise müssen Sie dem Adobe Commerce-Produktattributsatz das entsprechende Attribut hinzufügen, wenn das Attribut derzeit nicht in der Datenbank enthalten ist.</td>
<td>Webseite</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>Das Katalogattribut, das die Barcode-Quelle für die entsprechenden Elemente an Ihren Händlern speichert.<br></br>Diese Einstellung stellt sicher, dass an Ihre Stores gesendete Bestellungen Listenelemente mit der richtigen Kennung enthalten, sodass Storeverknüpfer Elemente während des Pickings genau überprüfen können. Zu den Optionen gehören SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.<br></br>Wenn Sie sich nicht sicher sind, wählen Sie die Option aus, die den in Ihrer [!UICONTROL Barcode Source] -Attribut. Speicherverknüpfungen können Elemente weiterhin manuell über ihre Auswahlliste zuordnen.</td>
<td>Webseite</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Die maximale Anzahl von Elementen, die gleichzeitig aus der Warteschlange für die Store-Erfüllung gesendet werden.<br></br>BOPIS-Bestellungen werden in regelmäßigen Abständen in Stapeln an den Erfüllungsdienst gesendet. Mit dieser Einstellung können Sie die Größe des Batches steuern.<br></br>Der Standardwert ist 100 Elemente. Abhängig von Ihrer Bestellmenge und -kapazität müssen Sie diesen Wert möglicherweise nach oben oder unten anpassen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Versandoptionen für Store-Erfüllung aktivieren

Konfigurieren Sie die Versandoptionen Store-Erfüllung , die die Verfügbarkeit der Optionen für die In-Store-Abholung und den Home-Versand für Ihre Adobe Commerce-Stores bestimmen.

### Zu Lager Schiff

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>Die Einstellung von Schiff zu Speicher basiert auf Ihren vorhandenen "Schiff zu Speicher"-Funktionen. Wenn Sie Inventory management verwenden oder Bestellungen an Händlern ohne Inventar über Bestandsübertragungen zwischen Lagern akzeptieren und erfüllen können, setzen Sie diese Option auf "Ja".<br></br>Wenn Sie die Option "Schiff zu Laden"nicht unterstützen oder nicht anbieten möchten, setzen Sie sie auf "Nein". Wenn diese Option deaktiviert ist, sind Elemente in Ihrem Katalog mit einem Nullbestand für einen Händlerspeicher oder Elemente, die unter dem Wert [!DNL Out of Stock Threshold], werden nicht mit Optionen zur In-Store-Abholung angeboten.<br></br>Dies ist eine globale Einstellung, die pro Händler-Standort angepasst werden kann.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

### Aus dem Geschäft verschicken

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Aktiviert oder deaktiviert die Option Home Delivery in Ihren Händlern. Wenn diese Option aktiviert ist, werden Ihre Händlerstätten zusammen mit anderen zugewiesenen Quellen im Lager betrachtet, das mit Ihrer Website verknüpft ist.<br></br>In standardmäßigen Inventory management-Diensten wird die [!DNL Ship from Store] ist eine Option, die inhärent ist und nicht deaktiviert werden kann. Mit der Lösung Store Fulfillment können Sie sie aktivieren oder deaktivieren.<br></br>Dies ist eine globale Einstellung. Sie können diese Einstellung auch für jeden Händler anpassen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>


## Verwalten von Store Fulfillment App-Benutzerkonten und -Berechtigungen

Konfigurieren Sie die Einstellungen für das Benutzerkonto der Store Fulfillment App und die Kennwortsicherheit sowie die Zwei-Faktor-Authentifizierung.

### App-Sicherheit

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Der Zeitraum in Sekunden, in dem eine Store-assoziierte Benutzersitzung vor der automatischen Abmeldung aktiv bleibt. Gültige Werte liegen zwischen 60 und 31536000.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Gibt die Anzahl fehlgeschlagener Anmeldeversuche an, die zulässig sind, bevor ein Storeverknüpfer aus seinem Konto ausgeschlossen wird.<br></br>Um die Kontosperrung zu deaktivieren, setzen Sie den Wert auf 0.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Anzahl der Minuten, in denen ein Konto nach einem Anmeldefehler gesperrt werden soll.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Der Benutzer muss nach der Kontoeinrichtung sein Kennwort ändern.<br></br><em>[!UICONTROL No]</em>: empfiehlt dem Benutzer, das Kennwort nach der Kontoeinrichtung zu ändern.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Die Anzahl der Tage, in denen ein Kennwort vor einer erforderlichen Kennwortänderung gültig bleibt. Lassen Sie es leer, um diese Option zu deaktivieren.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

### Zweifaktorauthentifizierung

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL APP User 2FA]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Zwei-Faktor-Authentifizierung für Store-Zuordnung. Wenn diese Option aktiviert ist, wird der Storeverknüpfer aufgefordert, ein einmaliges Kennwort anzugeben, das von einem Authentifizierungsanbieter generiert wurde.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL APP 2FA Policy]</strong></td>
<td>Legt die Durchsetzungsrichtlinie für die Authentifizierung mit zwei Faktoren fest.<br></br><strong>[!UICONTROL Optional]</strong>: Der Storeverknüpfer kann die Authentifizierung mit zwei Faktoren umgehen, wenn kein Provider festgelegt ist.<br></br><strong>[!UICONTROL Mandatory]</strong>: Das Store-Paar ist erforderlich, um die Authentifizierung mit zwei Faktoren abzuschließen.</td>
<td>Global</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL 2FA Providers]</strong></td>
<td>Wählen Sie einen oder mehrere Authentifizierungsanbieter-Dienste aus, um Storeverknüpfungen anzubieten. Um die Authentifizierung mit zwei Faktoren einzurichten, müssen Store-Associates die Authentifizierungs-App von einem der verfügbaren Anbieter installieren, die auf ihren Mobilgeräten installiert sind.</td>
<td>Global</td>
<td>Nein</td>
</tr>
</tbody>
</table>

## Versandmethoden

Store Fulfillment funktioniert durch Erweiterung des nativen Adobe Commerce [!DNL In-Store Delivery] Funktionen. Nachdem Sie die Erweiterung installiert haben, können Sie die Bereitstellungsmethoden im Store mithilfe der folgenden erweiterten Einstellungen konfigurieren, die zum Admin hinzugefügt werden.

- **Abholung im Geschäft**—Angebotsoptionen für den In-Store-Versand während des Checkout-Prozesses Dies ist das häufigste Bereitstellungsszenario für BOPIS-Bestellungen.

- **[!UICONTROL Curbside pick up]**-Angebotsoptionen für Kunden, die an einem Store-Speicherort parken und ihre Bestellung von einem Store-Mitarbeiter an sie senden lassen.

Konfigurieren Sie diese Einstellungen über den Administrator, indem Sie <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von In-Store-Bereitstellungsoptionen finden Sie unter [In-Store-Bereitstellung](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) im _Adobe Commerce-Benutzerhandbuch_.


### Konfiguration der Bereitstellungsmethoden

Mit der Bereitstellungsmethode im Geschäft kann der Kunde eine Quelle auswählen, die beim Checkout als Abholort verwendet werden soll.

<table>
<thead>
<tr>
<td><strong>Feld</strong></td>
<td><strong>Beschreibung</strong></td>
<td><strong>Anwendungsbereich</strong></td>
<td><strong>Erforderlich</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Option "In-Store-Abholung", die beim Checkout für Kunden verfügbar ist, die die Abholung im Geschäft auswählen. Wenn die In-Store-Abholung deaktiviert ist, wird die Option nicht angezeigt.<br></br>Diese globale Einstellung gilt für alle Einzelhandelsspeicherorte. Wenn diese Option aktiviert ist, können Sie sie selektiv am Speicherort des Einzelhandels deaktivieren.</td>
<td>Webseite</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Aktivieren oder deaktivieren Sie die Option "Cursor-Seitenabruf"während des Checkout-Prozesses für Kunden, die die Store-Abholung auswählen.<br></br>Diese globale Einstellung gilt für alle Einzelhandelsspeicherorte. Wenn diese Option aktiviert ist, können Sie sie selektiv am Speicherort des Einzelhandels deaktivieren.</td>
<td>Webseite</td>
<td>Nein</td>
</tr>
</tbody>
</table>

### Konfiguration des Titels der Bereitstellungsmethode

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
<td>Gibt den Titel an, der für die Option "Home Delivery"im Produkt-, Warenkorb- und Checkout-Bereich angezeigt werden soll. Der Home-Versand bezieht sich auf die standardmäßigen Versandfunktionen von Adobe Commerce - von einem Warehouse über einen Frachtführer oder direkt auf die vom Kunden bereitgestellte Lieferadresse. </br></br>Dieses Etikett wirkt sich nicht auf die Versandmethodenbeschriftungen für den ausgewählten Versandunternehmen aus.</td>
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
<td>Wenn einem Kunden Versandoptionen angezeigt werden und eine In-Store-Abholung verfügbar ist, wird dieser Titel angezeigt. </br></br>Sie können diese Bezeichnung anpassen, die in den Bereichen Produkt, Warenkorb und Checkout angezeigt wird.</td>
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
<td>Wenn eine Bestellung in Ihren Einzelhandelsgeschäften abgeholt werden kann, wird der Kunde per E-Mail benachrichtigt. Wenn der Kunde ausgewählt hat [!DNL In-Store Pickup] während des Auscheckens können Sie hier die Pickup-Anweisungen anpassen. </br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsspeicherorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Anweisungen zur automatischen Erfassung</strong></td>
<td>Gibt benutzerdefinierte Anweisungen zur Bestellabnahme an, die in E-Mail-Benachrichtigungen von Kunden für curbside Pickup-Bestellungen enthalten sind. </br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Anweisungen auch auf der Ebene des Einzelhandelsspeicherorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Geschätzte Abruf-Vorlaufzeit</strong></td>
<td>Die Anzahl der Minuten, die erforderlich sind, bevor eine Bestellung empfangen, erfüllt und abgeholt werden kann. Diese Informationen werden dem Kunden angezeigt, wenn er einen Einzelhandelsstandort für die Option "Store Pickup-Versand"auswählt. Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsstandorts anpassen.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Geschätzte Zeitbeschriftung für die Abholung</strong></td>
<td>Zeigt die geschätzte Zeit an, bis eine Bestellung für die Kundenabholung verfügbar ist. Diese Informationen werden Kunden angezeigt, wenn sie einen Einzelhandelsspeicherort für die [!DNL In-Store Pickup] Versandoption. </br></br>Bei der Anpassung dieser Beschriftung können Sie den Code verwenden <code>%1</code> um <strong>Geschätzte Abruf-Vorlaufzeit</strong>. Beispiel:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Dies ist eine globale Einstellung, die für alle Einzelhandelsstandorte gilt. Sie können die Vorlaufzeit auch auf der Ebene des Einzelhandelsstandorts anpassen.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
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

### Konfiguration der Lagerverfügbarkeitstitel

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
<td>Wenn ein Kunde den Locator für Einzelhandelsgeschäfte verwendet, wird für jeden Standort die Lagerverfügbarkeit für die aktuellen Elemente angezeigt. </br></br>Sie können die <em>[!UICONTROL in-stock]</em> Statusbezeichnung hier.</br></br></td>
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
<td>Wenn ein Kunde den Locator für Einzelhandelsgeschäfte verwendet, wird die Lagerverfügbarkeit für alle aktuellen Elemente für jeden Standort angezeigt. </br></br>Sie können die <em>[!UICONTROL partially in-stock]</em> Statusbezeichnung hier.</br></br></td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>
