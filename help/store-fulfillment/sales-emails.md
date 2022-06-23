---
title: Verkaufs-E-Mails
description: Konfigurieren Sie die Transaktions-E-Mail-Vorlagen für die Kommunikation mit Kunden und Store-Administratoren während des Ausführungsprozesses für Store-Abholaufträge.
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 0%

---


# Verkaufs-E-Mails

Store Fulfillment bietet eine erweiterte Reihe von Transaktions-E-Mail-Vorlagen, um Bestell- und Erfüllungs-Workflows zu unterstützen. Sie bieten eine konsistente, automatisierte Kommunikation und Messaging über alle Kanäle hinweg - Sie informieren Kunden- und Store-Administratoren über Bestellstatusänderungen, Anweisungen für In-Store-Abholaufträge und vieles mehr.

E-Mail-Vorlagen für die Store-Erfüllung werden mit Standardnachrichten und -Einstellungen konfiguriert. Merchant-Administratoren in Adobe Commerce können Konfigurationen verwalten und ändern sowie E-Mail-Vorlagen auswählen, um mit Kunden in unterschiedlichen Szenarien zu kommunizieren. Administratoren können Vorlagen auch konfigurieren und anpassen.

Konfigurieren Sie die Vorlagen für Verkaufs-E-Mails über den Administrator: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

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
<td>Deaktivieren Sie diese Funktion. Der asynchrone E-Mail-Versand wird nicht unterstützt. Um die schnellste Kommunikations- und Reaktionszeit für die Store-Erfassung zu erhalten, senden Sie E-Mails sofort, anstatt sie stapelweise zu senden. </td>
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
<td>Die Absenderkennung, die beim Senden der E-Mail-Benachrichtigung verwendet wird.</td>
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
<td>Die Methode der E-Mail "Kopie mit Kohlenstoff"sendet an die Verwendung.</td>
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
<td>Die Absenderkennung, die beim Senden der E-Mail-Benachrichtigung verwendet wird.</td>
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
<td><strong>Die Methode zum Kopieren einer E-Mail wurde erfasst</strong></td>
<td>Die Methode zum Senden der E-Mail "Kopie des CO2" zur Verwendung.</td>
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
<td>Die Absenderkennung, die beim Senden der E-Mail-Benachrichtigung verwendet wird.</td>
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
<td><strong>Verspätete E-Mail-Kopie der Bestellung an senden</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Versandreihenfolge - Kopiermethode verzögert</strong></td>
<td>Die Methode zum Senden der E-Mail "Kopie des CO2" zur Verwendung.</td>
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
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass sein Auftrag im Kaufhaus storniert wurde. Legen Sie fest auf <code>No</code> , um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, verhindert diese Funktion nicht, dass eine Bestellung abgebrochen wird.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Bestellung abgebrochen E-Mail-Absender
</strong></td>
<td>Die Absenderkennung, die beim Senden der E-Mail-Benachrichtigung verwendet wird.</td>
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
<td>Die Methode zum Senden der E-Mail "Kopie des CO2" zur Verwendung.</td>
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
<td>Diese E-Mail wird an den Kunden gesendet, um ihn darüber zu informieren, dass ein Teil seiner Bestellung im Kaufhaus storniert wurde. Legen Sie fest auf <code>No</code> , um die E-Mail-Benachrichtigung zu deaktivieren. Wenn die E-Mail-Vorlage deaktiviert ist, wird eine teilweise Stornierung einer Bestellung nicht verhindert.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Teilweise stornierter E-Mail-Absender bestellen
</strong></td>
<td>Die Absenderkennung, die beim Senden der E-Mail-Benachrichtigung verwendet wird.</td>
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
<td>Die Methode zum Senden der E-Mail "Kopie des CO2" zur Verwendung.</td>
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
<td>E-Mail an spezifiziertes Handelspersonal als aggregierten Bericht aller offenen Aufträge, die erst dann in einem Händlerspeicher ausgewählt werden können, wenn ihr Inventar verfügbar ist. </br></br> Händler können diesen Bericht verwenden, um Lagerbestandsübertragungen oder -nachbefüllungen zu initiieren und zu verwalten. </br></br>Diese Benachrichtigung gilt nur, wenn die Variable [!DNL Ship-to-Store] -Funktionen aktiviert sind.
</br></br>Dieses Etikett hat keine Auswirkungen auf den ausgewählten Versandunternehmen oder dessen verfügbare Versandmethodenbeschriftungen.</br></br></td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Versand zum Speichern von E-Mail-Empfängern</strong></td>
<td>Eine kommagetrennte Liste von E-Mail-Adressen, an die eine Kopie jeder Benachrichtigung gesendet werden soll.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
<tr>
<td><strong>Email Template</strong></td>
<td>Die für die Empfängerbenachrichtigung verwendete E-Mail-Nachrichtenvorlage. Die Integration enthält eine Standardvorlage.</td>
<td>Store-Ansicht</td>
<td>Nein</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Wenn Sie Aufstockungen zulassen, müssen Sie eine Administrator-E-Mail-Adresse angeben, um Benachrichtigungen zu diesen Bestellungen zu erhalten. Fügen Sie die Adresse den folgenden Konfigurationseinstellungen hinzu: **[!UICONTROL Send Order Delayed Email Copy To]** im [Bestellverzögerung](#order-delayed) Vorlage und [!UICONTROL Ship To Store Email Recipients] im [Zur Kasse schicken](#ship-to-store) Vorlage.



