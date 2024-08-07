---
title: E-Mail-Vorlagen für Vertrieb
description: Konfigurieren Sie die Transaktions-E-Mail-Vorlagen für die Kommunikation mit Kunden und Store-Administratoren während des Ausführungsprozesses für Store-Abholaufträge.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# E-Mail-Vorlagen für Vertrieb

Store Fulfillment bietet eine erweiterte Reihe von Transaktions-E-Mail-Vorlagen, um Bestell- und Erfüllungs-Workflows zu unterstützen. Sie bieten eine konsistente, automatisierte Kommunikation und Messaging über alle Kanäle hinweg - Sie informieren Kunden- und Store-Administratoren über Bestellstatusänderungen, Anweisungen für In-Store-Abholaufträge und vieles mehr.

E-Mail-Vorlagen für die Store-Erfüllung werden mit Standardnachrichten und -Einstellungen konfiguriert. Merchant-Administratoren in Adobe Commerce können Konfigurationen verwalten und ändern sowie E-Mail-Vorlagen auswählen, um mit Kunden in unterschiedlichen Szenarien zu kommunizieren. Administratoren können Vorlagen auch konfigurieren und anpassen.

Konfigurieren Sie die Vorlagen für Verkaufs-E-Mails über Admin: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## E-Mails - Allgemeine Einstellungen

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
<td><strong>Asynchrones Senden</strong></td>
<td>Bestimmt, ob Verkaufs-E-Mails asynchron gesendet werden. Optionen: <br/>*** Deaktivieren`** - (Standard) E-Mails zum Verkauf werden gesendet, wenn sie durch ein Ereignis ausgelöst werden. Verwenden Sie die Standardeinstellung, um die schnellste Kommunikations- und Reaktionszeit für die Store-Abholung zu erhalten. <br/>***`Aktivieren`** - Durch Aktivierung dieser Option werden Prozesse, die E-Mail-Benachrichtigungen zum Checkout und zur Bestellverarbeitung verarbeiten, in vordefinierten, regelmäßigen Abständen in den Hintergrund verschoben.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## Bestellung bereit für Abholung im Store

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, wenn der Store-Mitarbeiter die Auswahl seiner Bestellung abgeschlossen hat. Auf "Nein" setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert dies nicht, dass eine Bestellung vom Store-Mitarbeiter ausgewählt wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Orderbereit für Abruf-E-Mail-Absender</strong></td>
<td>Die beim Senden der E-Mail-Benachrichtigung verwendete Absenderkennung.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Auftrag bereit für Abruf-E-Mail-Vorlage</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung registrierter Kunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Bestellbereit für Pickup-E-Mail-Vorlage für Gastbenutzer</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit für Abruf-E-Mail-Vorlage für alternativen Abruf-Kontakt</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um zusätzliche Kontakte mit dem Namen in der Bestellung zu benachrichtigen. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit zum Abruf der E-Mail-Kopie an senden</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung bereit zum Abruf der E-Mail-Kopiermethode senden</strong></td>
<td>Die zu verwendende E-Mail-Copy-Methode - Carbon Copy.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>


## Die Bestellung wurde im Store abgerufen

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um zu bestätigen, dass er seine Bestellung aus dem Geschäft übernommen hat. Auf "Nein" setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert dies nicht, dass eine Bestellung vom Kunden aufgenommen wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Die Bestellung wurde vom E-Mail-Absender erfasst</strong></td>
<td>Die beim Senden der E-Mail-Benachrichtigung verwendete Absenderkennung.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung wurde in E-Mail-Vorlage aufgenommen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung registrierter Kunden verwendet wird. Eine Standardvorlage wird mit der Integration bereitgestellt</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Die E-Mail-Vorlage für den Gastbenutzer wurde ausgewählt</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Senden wurde als E-Mail-Kopie an aufgenommen</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Die Methode zum Kopieren einer E-Mail wurde erfasst.</strong></td>
<td>Die zu verwendende E-Mail-Copy-Methode - Carbon Copy.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## Reihenfolge verzögert

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn über eine Verzögerung bei der Verarbeitung oder Auswahl seiner Bestellung im Händler zu informieren. Auf "Nein" setzen, um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert die Funktion nicht, dass eine Bestellung verzögert wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Verspäteter E-Mail-Absender bestellen
</strong></td>
<td>Die beim Senden der E-Mail-Benachrichtigung verwendete Absenderkennung.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Verzögerte E-Mail-Vorlage bestellen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung registrierter Kunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Vorlagenbestellung für verzögerte E-Mail für Gastbenutzer</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Verspätete E-Mail-Kopie an senden</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Versandreihenfolge - Kopiermethode verzögert</strong></td>
<td>Die zu verwendende E-Mail-Copy-Methode - Carbon Copy.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>



## Bestellung abgebrochen

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass sein Auftrag im Kaufhaus storniert wurde. Setzen Sie dies auf <code>No</code> , um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert diese Funktion nicht, dass eine Bestellung abgebrochen wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung abgebrochen E-Mail-Absender
</strong></td>
<td>Die beim Senden der E-Mail-Benachrichtigung verwendete Absenderkennung.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Auftrag abgebrochene E-Mail-Vorlage</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung registrierter Kunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Bestellung abgebrochen für Gast</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Auftrag senden abgebrochen E-Mail-Kopie an</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Sendereihenfolge - Kopiermethode abgebrochen</strong></td>
<td>Die zu verwendende E-Mail-Copy-Methode - Carbon Copy.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>


## Teilweise stornierte Bestellung

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
<td><strong>Aktiviert</strong></td>
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass ein Teil seiner Bestellung im Kaufhaus storniert wurde. Setzen Sie dies auf <code>No</code> , um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, wird eine teilweise Stornierung einer Bestellung nicht verhindert.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise stornierter E-Mail-Absender bestellen
</strong></td>
<td>Die beim Senden der E-Mail-Benachrichtigung verwendete Absenderkennung.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise abgebrochene E-Mail-Vorlage bestellen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung registrierter Kunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<td><strong>Teilweise stornierte E-Mail-Vorlage für alternativen Abruf-Kontakt bestellen</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die verwendet wird, um zusätzliche Kontakte mit dem Namen in der Bestellung zu benachrichtigen. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise stornierte Bestellung für Gastgeber</strong></td>
<td>Die E-Mail-Nachrichtenvorlage, die zur Benachrichtigung von Gastkunden verwendet wird. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Auftrag teilweise abgebrochen E-Mail-Kopie an senden</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise abgebrochene Kopiermethode für Auftrag senden</strong></td>
<td>Die zu verwendende E-Mail-Copy-Methode - Carbon Copy.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

## Zur Kasse schicken

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
<td><strong>Auftrag enthält Versand zum Speichern von Produkten E-Mail-Absender</strong></td>
<td>E-Mail an spezifiziertes Handelspersonal als aggregierten Bericht aller offenen Aufträge, die erst dann in einem Händlerspeicher ausgewählt werden können, wenn ihr Inventar verfügbar ist. </br></br> Händler können diesen Bericht verwenden, um Lagerbestandsübertragungen oder -nachbefüllung zu initiieren und zu verwalten. </br></br>Diese Benachrichtigung gilt nur, wenn die [!DNL Ship-to-Store] -Funktionen aktiviert sind.
</br></br>Diese Bezeichnung wirkt sich nicht auf den ausgewählten Versandunternehmen oder dessen verfügbare Versandmethodenbeschriftungen aus.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Empfänger speichern</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>E-Mail-Vorlage</strong></td>
<td>Die für die Empfängerbenachrichtigung verwendete E-Mail-Nachrichtenvorlage. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Wenn Sie Aufstockungen zulassen, müssen Sie eine Administrator-E-Mail-Adresse angeben, um Benachrichtigungen zu diesen Bestellungen zu erhalten. Fügen Sie die Adresse zu den folgenden Konfigurationseinstellungen hinzu: **[!UICONTROL Send Order Delayed Email Copy To]** in der Vorlage [Auftragsverzögerung](#order-delayed) und [!UICONTROL Ship To Store Email Recipients] in der Vorlage [Zum Speicher versenden](#ship-to-store) .



