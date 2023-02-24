---
title: Testen und Bereitstellen der Store-Erfüllung
description: Testen Sie den Plan, um die Funktion zur Store-Erfüllung zu überprüfen. Tests umfassen die API zur Lagerbestandssynchronisierung, den End-to-End-Erfüllungs-Workflow für abgebrochene Bestellungen, die Benutzerverwaltung der App zur Inhaltsbearbeitung und das Customer Check-in-Erlebnis.
role: User, Admin
level: Intermediate
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '2660'
ht-degree: 0%

---

# Testen und Bereitstellen der Store-Erfüllung für Adobe Commerce

Nachdem Sie das Onboarding in Ihrer Entwicklungsumgebung abgeschlossen haben, können Sie den Prozess starten, um die Store Fulfillment-Lösung zu testen und in Ihrer Produktionsumgebung bereitzustellen.

**Voraussetzungen**

Bevor Sie Informationen, Stores oder Bestellungen testen oder synchronisieren, überprüfen Sie, ob Sie die folgenden Aufgaben ausgeführt haben:

- Abgeschlossen wurde die [Allgemeine Konfiguration](enable-general.md) für Store Fulfillment-Dienste.

- [Hinzufügen und Überprüfen der Kontoanmeldeinformationen und Verbindungsdetails für Ihre Sandbox- und Produktionsumgebungen](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Vergewissern Sie sich, dass die [Adobe Commerce-Integration](connect-set-up-service.md#configure-store-fulfillment-account-credentials) für die Lösung zur Herstellung einer Fulfillment-Lösung ist verfügbar und zugelassen.

## Testvorbereitung

Die Verbindungskonfiguration muss abgeschlossen sein, bevor Sie Testaufträge erstellen oder Integrationstests durchführen können. Vor dem Testen müssen Sie auch überprüfen, ob Ihre Speicherdaten synchronisiert sind.

1. Synchronisieren Sie die Store-Ausführungsquellen.

   - Navigieren Sie zu **[!UICONTROL Stores > Sources]**.

   - Auswählen **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. Überprüfen Sie im Store-Raster, ob Stores als `Synced` vor der Erstellung von Testbestellungen.

## Beispieltestplan

Einzelhändler validieren die grundlegenden Funktionen der Lösung zur Store-Erfüllung während der Konfigurations- und Testphase einer Implementierung. Dieser Beispieltestplan bietet einen Ausgangspunkt für Tests. Fügen Sie zusätzliche Szenarien hinzu, die Ihren Anforderungen entsprechen.

>[!NOTE]
>
>Nach dem ersten Onboarding für die Store Fulfillment-Lösung oder Aktualisieren einer vorhandenen Installation sollten Sie die Anwendung immer in einer Nicht-Produktionsumgebung testen, bevor Sie sie für die Produktion bereitstellen.

Dieser Stichprobenprüfplan umfasst die folgenden Funktionsbereiche:

| Funktionaler Bereich | Funktion | Rolle |
|-------------------------------------|------------------------------------------|----------------------------------|
| Bestand- und Auftragssynchronisierung | Inventar-API-Synchronisierung | Adobe Commerce Admin |
| End-to-End | Workflows zur Auftragsabbruch | Kunde, Admin, Store Associate |
| Admin | App-Berechtigungen für die Store-Ausführung | Admin |
| Adobe Commerce Frontend | Produkttypen | Kunde, Admin |
| Frontend-Checkout</br>Formular für das Einchecken | Eincheckerlebnis | Kunde, Admin |
| Store Assist App | Bestellung</br>Auswahl</br>Staging</br>und Übergabe | Store Associate |

### Inventar-API-Synchronisierung

In diesem Abschnitt des Testplans wird die Bestands- und Bestellsynchronisierung behandelt, um zu überprüfen, ob Aktualisierungen an Erfassungsquellen und Lagerbeständen korrekt zwischen Adobe Commerce und der Store Fulfillment-Lösung synchronisiert werden.

**Funktionaler Bereich**: Bestand- und Auftragssynchronisierung</br>
**Rolle:** Admin</br>
**Testtyp:** Alle positiven

<table>
<thead>
<tr>
<th>Funktion</th>
<th>Testszenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Hinzufügen der Freigabequelle</strong></td>
<td>Speichern Sie eine neue Sicherungskopie-Datenquelle.</td>
<td>Die Echtzeit-Synchronisation sendet die Quelldetails innerhalb von 5 Minuten an den Walmart GIF-Dienst.</td>
</tr>
<tr>
<td><strong>Vorhandene Freigabequelle aktualisieren</strong></td>
<td>Speichern Sie Aktualisierungen in einer vorhandenen Sicherungskopie-Datenquelle.</td>
<td>Der Echtzeit-Synchronisierungsvorgang sendet die Details innerhalb von 5 Minuten an die Walmart-GIF</td>
</tr>
<tr>
<td><strong>Abholquellenquelle</br><code>Is Synced</code> status</br><code>Is Synced</code></strong></td>
<td>Speichern Sie Aktualisierungen in einer vorhandenen Sicherungskopie-Datenquelle.</td>
<td>Nach einem erfolgreichen Vorgang wird die <code>Is Synced</code> Spalte der Seite "Quelle verwalten"von <code>No</code> nach <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>Geänderter Lagerreservierungsprozess</strong></td>
<td>Erstellen und senden Sie eine neue Bestellung für ein Produkt.</td>
<td>Die Verkaufsmenge für das Produkt nimmt entsprechend ab.</td>
</tr>
<tr>
<td><strong>Neue Bestellaufgabe-Push, API-Synchronisierung - Kundenreihenfolge</strong></td>
<td>Der Kunde sendet eine Store-Abholbestellung.</td>
<td><ul><li>In der Ansicht "Admin Order"wird eine <strong>Adobe Commerce Admin-Benutzer</strong> erkennt, dass der Status "Bestellsynchronisierung"auf aktualisiert wurde. <code>Sent</code></li><li>Das Bestelldetailprotokoll enthält die Meldung <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Neue Bestellung Push, API Sync - Admin sendet die Bestellung</strong></td>
<td>Eine Adobe Commerce <strong>Admin</strong> sendet eine Abholbestellung.</td>
<td><ul><li>In der Ansicht "Admin Order"wird der Status "Auftragssynchronisierung"auf <code>Sent</code>.</li><li>Das Bestelldetailprotokoll enthält die Meldung <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Neue Auftragspush-, Ausnahmenwarteschlange<strong></td>
<td>Identifizieren Sie mehrere virtuelle und herunterladbare Produkte in Adobe Commerce Admin, die über Adobe Commerce erfüllt werden können, ohne dass eine Interaktion mit dem Fulfillment-Dienst (FAAs) erforderlich ist.</td>
<td>Diese Produkte werden im Export entsprechend entfernt oder gekennzeichnet, um einen nachgelagerten Konflikt mit der FAA zu verhindern.</td>
</tr>
</tbody>
</table>

### Workflows für die Auftragsabbruch

Dieser Abschnitt des Testplans enthält Szenarien zum Testen des End-to-End-Workflows für Bestellungen, die über Adobe Commerce abgebrochen werden.

**Funktionaler Bereich:** Adobe Commerce Admin</br>
**Rolle:** End-to-End (Admin, Store Associate, Kunde)</br>
**Testergebnistyp:** Positiv für alle Szenarien

<table style="table-layout:fixed">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Absage der vollständigen Bestellung</strong></td>
<td><ol>
<li>Bestellung aufgeben.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie die Rechnungserstellung (falls autorisiert und erfasst) des Quittierungs-E-Mails.</li>
<li>Erstellen Sie ein Credit Memo mit allen bestellten Produkten aus der Rechnungsansicht.</li>
</ol>
</td>
<td>
<ul>
<li>Auftragsverlauf aktualisiert mit <code>We refunded $X online. Transaction ID: transactionID</code> und <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>Bestellstatus: <code>Closed</code>. (Wir haben jetzt ZAHLUNGSÜBERPRÜFUNG festgelegt.)</li>
<li>In Adobe Commerce erstelltes Credit Memo. (Warten Sie, bis das Cron funktioniert.)</li>
<li>Wenn alle Elemente ausgewählt wurden, können Sie die E-Mail abrufen. <code>DISPLAY COMMENT HISTORY</code> zeigt <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.</li>
<li>Wenn alle Elemente nicht ausgewählt sind, wird die E-Mail zum Abbruch und die Anzeige des KOMMENTARVERLAUFS angezeigt <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.</li>
</ul>
</td>
</tr>
<tr><td><strong>Teilweiser Auftragsabbruch<strong></td>
<td>
<ol>
<li>Bestellung mit mindestens zwei Produkten.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Warten Sie zwei Stunden für die Abwicklung von Transaktionen.</li>
<li>Erstellen Sie ein Credit Memo mit nur einem Teil der bestellten Produkte aus der Rechnungsansicht.</li>
</td>
<td>
<ul>
<li>Aktualisierung des Auftragsverlaufs: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Aktualisierung des Auftragsverlaufs: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Erhalt der Bestellrückerstattungs-E-Mail: <code>$x amount was refunded</code></li>
<li>Bestellstatus: <code>Processing</code>.</li>
<li>In Adobe Commerce erstelltes Credit Memo (Warten Sie, bis Cron funktioniert).</li>
<li>Wenn einige Elemente nicht ausgewählt wurden, bestätigen Sie, dass die [!UICONTROL Ready for Pickup] E-Mail mit dem Abschnitt "Auswahl oder Rückerstattung von Null" angezeigt. <code>DISPLAY COMMENT HISTORY</code> zeigt <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> Markierung ist <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Bereit zum Abholen</br></br>Vollständige Stornierung</br>(alle Produkte werden mit 0 qty eingestellt)</br></strong></td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage "Bereit für Abruf"mit allen Produkten aus, die als <code>picked</code> mit <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline</code></li>
<li>Der Bestellstatus lautet <code>CLOSED</code>.
<li>Das Credit Memo wird erstellt. (Warten Sie, bis das Cron funktioniert.)</li>
<li>erhaltene Rückerstattungs-E-Mail: <code>$x amount was refunded</code></li>
<li>E-Mail zur Auftragsabbruch gesendet.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Bereit für Abruf - Teilstornierung</strong></br></br><strong>(Einige Produkte werden gepflückt und einige werden mit <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage "Bereit für Abholung"aus, wobei ein Teil der Produkte wie mit 0 qty festgelegt und der Rest ausgewählt ist.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> mit [!UICONTROL Ready for Pickup Items] und [!UICONTROL Canceled Items] -Tabellen. </li>
<li>Der Bestellstatus ist FÜR PICKUP BEREIT. </li>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline.</code>
<li>Auftragsverlauf aktualisiert: <code>Order notified as partly canceled at: Date and hour</code>
<li>erhaltene Rückerstattungs-E-Mail: <code>$x amount was refunded</code>
<li>Das Kreditmemo wird erstellt. (Warten Sie, bis das Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Bereit für Abruf - Teilkündigungen</br></br>Einige Produkte werden gepflückt und einige werden mit <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage "Bereit für Abholung"aus, wobei ein Teil der Produkte wie mit 0 qty festgelegt und der Rest ausgewählt ist.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> mit [!UICONTROL Ready for Pickup Items] und [!UICONTROL Canceled Items] -Tabellen. </li>
<li>Der Bestellstatus ist FÜR PICKUP BEREIT. </li>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline.</code>
<li>Auftragsverlauf aktualisiert: <code>Order notified as partly canceled at: Date and hour</code>
<li>erhaltene Rückerstattungs-E-Mail: <code>$x amount was refunded</code>
<li>Das Kreditmemo wird erstellt. (Warten Sie, bis das Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Verworfen (während der Entlassung) </br></br>Vollständige Stornierung (alle Produkte werden als abgelehnt festgelegt)</strong>
</td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anfrage "Bereit für Abruf"mit allen Produkten aus, die wie ausgewählt festgelegt sind.</li>
<li>Öffnen Sie Ihr Postfach und suchen Sie nach der E-Mail "Bereit für Abruf". Klicken Sie dann auf **[!UICONTROL Confirm Arrival]**.</li>
<li>Einchecken.</li>
<li>Wechseln Sie zu Postman und führen Sie die Anforderung "Bereitstellung"aus, wobei alle Produkte als abgelehnt festgelegt sind.</li>
</ol>
<td><ul>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline.</code></li>
<li>erhaltene Rückerstattungs-E-Mail: <code>$x amount was refunded</code></li>
<li>Status festgelegt auf <code>CLOSED</code>.</li>
<li>Credit Memo erstellt. (Warten Sie, bis das Cron funktioniert.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Verworfen (während der Entlassung)</br></br>Teilweiser Abbruch</br>(Einige Produkte werden vertrieben. einige werden abgelehnt.)</strong>
</br></td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wechseln Sie zu Postman und führen Sie die Anfrage "Bereit für Abruf"mit allen Produkten aus, die wie ausgewählt festgelegt sind.</li>
<li>Öffnen Sie Ihren Posteingang. Suchen Sie die E-Mail "Bereit für Abruf"und wählen Sie <code>Confirm Arrival</code>.</li>
<li>Einchecken.</li>
<li>Wechseln Sie zur Postman und führen Sie die Anforderung "Lizenziert"aus, wobei einige Produkte auf "bereitgestellt"und einige auf "abgelehnt"eingestellt sind.</li>
</ol>
</td>
<td>
<li>Auftragsverlauf aktualisiert: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>erhaltene Rückerstattungs-E-Mail: <code>$x amount was refunded</code>
<li>Bestellstatus auf <code>Ready for pickup Dispensed</code>
<li>Credit Memo erstellt. (Warten Sie, bis das Cron funktioniert.)</li>
</td>
</tr>
<tr>
<td> <strong>Neue RMA nach Rückgabe (vollständig)</strong>
</td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Wenn die Option zum Autorisieren und Erfassen konfiguriert ist, überprüfen Sie, ob die Rechnung erstellt wurde und ob der Kunde die E-Mail zur Rechnung erhalten hat.</li>
<li>Wählen Sie alle Produkte mit Postman aus.</li>
<li>Einchecken.</li>
<li>Richten Sie einen Verzicht!</li>
<li>Gehen Sie zur Bestellung und wählen Sie<strong>[!UICONTROL Create returns]=
<li>RMA erstellen.</li>
</ol>
</td>
<td>
<ul>
<li>Die RMA wurde erstellt und wird unter dem <strong>[!UICONTROL Returns]</b> in der Bestellansicht.</li>
<li>Der Kunde hat eine RMA-Bestätigungs-E-Mail erhalten.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Neue RMA nach Rückgabe — Teil</strong>
</td>
<td>
<ol>
<li>Platzieren Sie die Bestellung.</li>
<li>Warten Sie, bis die Bestellung synchronisiert wurde.</li>
<li>Überprüfen Sie, ob die Rechnung erstellt wurde (falls autorisiert und erfasst) und ob die E-Mail zur Rechnung eingegangen ist.</li>
<li>Wählen Sie alle Produkte mit Postman aus.</li>
<li>Einchecken.</li>
<li>Richten Sie einen Verzicht!</li>
<li>Gehen Sie zur Reihenfolge und wählen Sie  <strong>[!UICONTROL Create returns]</strong></li>
<li>Erstellen Sie die RMA mit einem Teil der bestellten Produkte.</li>
</ol>
<td>
<ul>
<li>RMA erstellt und unter dem <strong>[!UICONTROL Returns]</strong> in der Bestellansicht.</li>
<li>Der Kunde hat die RMA-Bestätigungs-E-Mail erhalten.</li>
<li>Rufen Sie nach der Erstellung von RMA die RMA-Autorisierung ab: Navigieren Sie vom Administrator zu <strong>[!UICONTROL Sales > Returns]</strong>. Wählen Sie die von Ihnen erstellte RMA aus und autorisieren Sie sie.</li>
<li>Stellen Sie sicher, dass der Kunde die E-Mail zur RMA-Autorisierungsbestätigung erhalten hat.</li>
<li>Überprüfen Sie, ob die Rückerstattung dem Transaktionsverlauf und dem Auftragsverlauf hinzugefügt wurde.</li>
</ul>
</td>
</tr>
</table>


### App-Berechtigungen für die Store-Ausführung

In diesem Abschnitt des Testplans wird die Kontoverwaltung für Store Fulfillment App-Benutzer behandelt.

- Vergewissern Sie sich, dass sich ein Store-Associate mit einem neuen Benutzerkonto authentifizieren kann, das vom Adobe Commerce-Administrator erstellt wurde.
- Vergewissern Sie sich, dass die Aktualisierungen der bestehenden Konten erfolgreich angewendet wurden.

**Funktionaler Bereich:** Adobe Commerce Admin</br>
**Rolle:** Admin, Store Associate</br>
**Testtyp:** Alle positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Benutzerkontoverwaltung - Konto erstellen</strong></br></br>
</td>
<td>
<ol>
<li><strong>Admin</strong> — Melden Sie sich bei Adobe Commerce Admin an.</li>
<li>Navigieren Sie zu <strong>[!UICONTROL System] &gt; Store Fulfillment App-Berechtigungen &gt; Alle Store Fulfillment-App-Benutzer</strong></li>
<li><strong>Neuen Benutzer hinzufügen.</strong></li>
</ol>
<td>
<ul>
<li>Konto wurde erfolgreich erstellt.</li>
<li>Neues Benutzerkonto wird auf der Seite [!UICONTROL Store Fulfillment Users] Dashboard.</li>
<li><strong>Store Associate</strong> Melden Sie sich mit dem neuen Benutzerkonto bei der Store Assist-App an.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Benutzerkontoverwaltung - Vorhandenes Benutzerkonto aktualisieren</strong>
</td>
<td>
<ol>
<li>Melden Sie sich mit dem Administratorkonto bei Adobe Commerce Admin an.</li>
<li>Navigieren Sie zu <strong>[!UICONTROL System] &gt; Store Fulfillment App-Berechtigungen &gt; Alle Store Fulfillment-App-Benutzer</strong>.</li>
<li>Öffnen Sie in der Liste Benutzerkonto ein vorhandenes aktives Benutzerkonto, indem Sie <strong>[!UICONTROL Edit]</strong>.
<li>Deaktivieren Sie das Konto, indem Sie <strong>[!UICONTROL Is Active]</strong> nach <strong>Nein</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>Im <strong>[!UICONTROL Store Fulfillment App Users]</strong> Dashboard, der Status des aktualisierten Kontos geändert in <strong>[!UICONTROL Inactive]</strong>.</li>
<li>Store Associate kann sich nicht bei der Store Assist-App mit den inaktiven Kontoanmeldeinformationen anmelden.</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce-Produkttypen

Die Testszenarios für Adobe Commerce-Produkttypen überprüfen, ob Kunden die richtigen Produkt-, Lager- und Bereitstellungsmethodeninformationen für verschiedene Produkttypen sehen:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] in der Adobe Commerce-Storefront.

**Funktionaler Bereich:** Adobe Commerce Frontend</br>
**Rolle:** Store Assist App User (Store Associate)</br>
**Testtyp:** Alle positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Kommentare</th>
</tr>
<tr>
<td><strong>Konfigurierbare Produkte</strong>
</td>
<td>
<ul>
<li>Vergewissern Sie sich, dass der Benutzer nur die konfigurierbaren Optionen sehen kann, welche Quelle aktiviert ist, Lager zugewiesen wird und dass einige Elemente auf Lager sind - überprüfen Sie untergeordnete Produkte.</li>
<li>Stellen Sie sicher, dass bei der Auswahl eines anderen Stores die nicht verfügbaren Optionen als durchkreuzt angezeigt werden.</li>
<li>Stellen Sie sicher, dass bei Auswahl eines anderen Stores die konfigurierbaren Optionen deaktiviert werden.</li>
<li>Stellen Sie sicher, dass ein konfigurierbares Produkt bereits im Warenkorb ist und ein Benutzer einen anderen Speicher auswählt, das Produkt als nicht vorrätig angezeigt wird.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Gruppierungsprodukte</strong>
</td>
<td>
<ul>
<li>Vergewissern Sie sich, dass die Versandmethoden und [!UICONTROL Add to cart] -Schaltfläche für den Kunden deaktiviert ist, wenn alle untergeordneten Produkte
<code>qty</code> auf <code>0</code>.</li>
<li>Stellen Sie sicher, dass die Versandmethoden für den Kunden aktiviert sind, wenn mindestens eines der untergeordneten Produkte <code>qty</code> auf <code>0.</code></li>
<li>Stellen Sie sicher, dass [!UICONTROL Store Pickup Delivery] -Methode nur für Produkte sichtbar und aktiv, die [!UICONTROL Available for Store Pickup] aktiviert. (Untergeordnetes Produkt überprüfen.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Virtuelle Produkte</strong>
</td>
<td>
Vergewissern Sie sich, dass virtuelle Produkte die  [!UICONTROL In-store Pickup] Versandmethode.
<td></td>
</td>
</tr>
<tr>
<td><strong>Bundle-Produkte</strong>
</td>
<td>
<ul>
<li>Stellen Sie sicher, dass mindestens ein untergeordnetes Produkt [!UICONTROL Available for Store Pickup] deaktiviert ist, ist die Option Abholung speichern für den Kunden nicht verfügbar.</li>
<li>Stellen Sie sicher, dass mindestens ein untergeordnetes Produkt [!UICONTROL Available for Home Delivery] deaktiviert ist, ist die Option Home Delivery für den Kunden nicht verfügbar.</li>
<li>Überprüfen Sie, ob mindestens eines der untergeordneten Produkte in einem Bundle nicht vorrätig ist. Das Bundle (übergeordnete Produkt) wird auch als [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Eincheckerlebnis

In diesem Abschnitt des Testplans wird das Check-in-Erlebnis für Store-Abholaufträge für die folgenden Funktionen behandelt:

- Alternativer Abruf-Kontakt - Überprüfen Sie den Workflow für das Hinzufügen eines [!UICONTROL Alternate Pickup Contact] und wählen Sie eine [!UICONTROL Preferred Contact] bei Bestellungen zur Reservierung.

- Formular für die Anmeldung - Überprüfen Sie den Workflow für die Übermittlung einer Eincheckanfrage für Store-Abholaufträge.

**Funktionsbereiche:** Warenkorb zur Kasse, Formular zum Einchecken für Bestellungen zur Abholung von Geschäften</br>
**Rolle:** Admin, Kunde, Store Associate</br>
**Testtyp:** Alle positiv

### Alternativer Ansprechpartner


**Funktionaler Bereich:** Warenkorb zur Kasse</br>
**Rolle:** Kunde</br>
**Testtyp:** Alle positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Alternativer Ansprechpartner</br>
Einchecken</br><strong>
</td>
<td>
Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung .</td>
<td>Während des Checkout-Prozesses sieht der Kunde die [!UICONTROL Alternate Pickup Contact] die Option im Versandschritt.
</td>
</tr>
<tr>
<td><strong>Alternativer Kontakt zur Auswahl bevorzugte Kontakte, Einchecken</strong>
<td>
Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung . Beim Checkout fügt der Kunde eine [!UICONTROL Alternate Pickup Contact].</td>
<td>Während des Checkout-Prozesses sieht der Kunde die [!UICONTROL Preferred Contact] im Versandschritt.</td>
</td>
</tr>
<tr>
<td><strong>Alternative Kontaktinformationen zur Abholung, Einchecken</strong>
</td>
<td>
Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung . Beim Checkout wählt der Kunde [!UICONTROL Alternate Pickup Contact] im Versandschritt.
</td>
<td>Der Kunde sieht Eingabeoptionen zur Eingabe von Kontaktdetails: [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]und [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Alternative Abholung, E-Mail einchecken</strong>
</td>
<td>Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung . Beim Checkout wählt der Kunde [!UICONTROL Alternate Pickup Contact] im Versandschritt die Kontaktdaten hinzu und sendet die Bestellung.</td>
<td>Sowohl der Kunde als auch der alternative Kontakt erhalten eine Check-In-E-Mail für die Bestellung.</td>
</tr>
<td><strong>Alternative Auswahl, Auftragsdetails</strong></td>
<td>Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung . Beim Checkout wählt der Kunde [!UICONTROL Alternate Pickup Contact] im Versandschritt die Kontaktdaten hinzu und sendet die Bestellung.</td>
<td>Der Administrator sieht die zusätzlichen Kontaktinformationen zur gespeicherten Bestellung.</td>
</tr>
<tr>
<td><strong>Alternative Abholkontakte, Ansicht "Store Associate Order"</strong>
</td>
<td>Ein Kunde sendet eine Bestellung mit der Option In-Store-Abholung . Beim Checkout wählt der Kunde [!UICONTROL Alternate Pickup Contact] im Versandschritt die Kontaktdaten hinzu und sendet die Bestellung.</td>
<td>Der Store Associate kann die zusätzlichen Kontaktinformationen über die Bestellung in FaaS/ChaaS sehen.</td>
</td>
</tr>
</tbody>
</table>

### Formular für das Einchecken


**Funktionaler Bereich:** Formular für das Einchecken</br>
**Rolle:** Kunde</br>
**Testtyp:** Alle positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td><strong>Check in Action - Submit request</strong>
</td>
<td>Im Formular zum Einchecken füllt ein Kunde alle erforderlichen Felder aus und sendet die Anfrage.</td>
<td>Der Kunde erhält eine Erfolgsantwort.</td>
</tr>
<tr>
<td><strong>Aktivieren in Aktion - Anforderungsdetails anzeigen</strong></td>
<td>Ein Kunde sendet erfolgreich eine Eincheckanfrage.</td>
<td>Der Bestellstatus wird im FAAS-System aktualisiert und der Store Associate kann die Details der Eincheckanfrage in der FAAs sehen.
</td>
</tr>
<tr>
<td><strong>Check in Action - Submit Request nur einmal</strong></td>
<td>Nachdem ein Kunde eine Eincheckanfrage für eine Bestellung gesendet hat, wählt er den Link aus, um ihn ein zweites Mal einzuchecken.</td>
<td>Im Formular "Einchecken"wird dem Kunden keine Option zum Bearbeiten oder erneuten Senden des Formulars angezeigt.</td>
</tr>
<tr>
<td><strong>Einchecken in Aktion - Ankunft bestätigen</strong></td>
<td>In der FAAs wird eine Lagerabholung zur Abholung markiert. Der Kunde erhält eine Bereit zum Abruf-E-Mail und wählt [!UICONTROL Confirm Arrival].</td>
<td>Der Kunde sieht das Eincheckformular für die Bestellung.</td>
</tr>
</tbody>
</table>

## Store Assist App

In diesem Abschnitt des Testplans werden Szenarien zum Testen der Reihenfolge, Auswahl und Übergabe von Workflows in der Store Assist App behandelt.

**Funktionaler Bereich:** Store Assist App</br>
**Rolle:** Store Associate</br>
**Testtyp:** Alle positiv

<table style="table-layout:auto">
<tr>
<th>Funktion</th>
<th>Szenario</th>
<th>Erwartete Ergebnisse</th>
</tr>
<tr>
<td>
<strong>Einzelbestellauswahl - Happy Path, Cumulative Pickup</strong></td>
<td>Wählen Sie einzelne und mehrere Elemente aus. Kein Nil-Picks und Cursor-Pickup (mit Staging).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Multi-Order-Picking - glücklicher Pfad, parallele Übernahme</strong></td>
<td>Einzelartikel und Artikel mit mehreren Mengen. Kein Nil-Picks und Cursor-Pickup (mit Staging)</td>
<td></td>
</tr>
<tr>
<td><strong>Einzelbestellauswahl - Happy Path In-Store-Abruf</strong></td>
<td>Einzelartikel und Artikel mit mehreren Mengen. Keine Nil-Picks und In-Store-Abholung (mit Staging)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Multi-Order-Picking - glücklicher Pfad, In-Store-Abruf</strong></td>
<td>Wählen Sie einzelne und mehrere Elemente aus. Kein Nil-Picks und Cursor-Pickup (mit Staging).</td>
<td></td>
</tr>
<tr>
<td><strong>Einzelbestellauswahl - kein glücklicher Pfad, In-Store-Abruf</strong></td>
<td>Einzel- und Mehrmengen-Elemente mit Teil- und Nilpflücken und In-Store-Abholung (mit Staging) auswählen</td>
</td>
<td></td>
</tr>
<td><strong>Auswahl mehrerer Bestellungen - nicht glückliche Pfade-Cursor-Sickup</strong></td>
<td>Einzel- und Mehrmengen-Elemente mit Teil- und Nilpflücken und In-Store-Abholung (mit Staging) auswählen</td>
<td></td>
</tr>
<td><strong>Einzelauftragsauswahl - kein glücklicher Pfad, paralleles Aufnehmen</strong></td>
<td>Einzel- und Mehrmengen-Elemente mit Teil- und Nilpick- und Cursor-Pickup auswählen (mit Staging)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Bestellung platziert - vor der Auswahl abgebrochen</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Bestellung platziert - vor Übergabe storniert</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Reihenfolge platziert - Suche im Bestellmodul</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Bestellung platziert - Suchen und manuelles Einchecken zur Übergabe</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Reihenfolge platziert - alle Elemente, die von der Auswahl nicht ausgewählt wurden oder nicht verfügbar sind</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Bestellung mit Bundle-Elementen - Auswahl und Übergabe</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Bestellung platziert - Hand mit Zurückweisung</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Reihenfolge platziert - Übergabe mit Zurückweisung aller Artikel</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## Bereitstellen

Nachdem Sie überprüft haben, ob die Lösung entsprechend Ihren Spezifikationen konfiguriert und getestet wurde, können Sie sie vom Staging zur Produktion bereitstellen.

Die Implementierung und Tests variieren je nach Infrastruktur und Funktionen.

>[!TIP]
>
>Bereitstellungsrichtlinien, Checklisten und Best Practices für Adobe Commerce bei Cloud-Infrastrukturprojekten finden Sie unter [Bereitstellen Ihres Stores](https://devdocs.magento.com/cloud/live/stage-prod-live.html) in der Adobe Commerce Developer-Dokumentation.
