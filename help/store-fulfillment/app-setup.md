---
title: App-Einrichtung
description: '"Richten Sie die [!DNL Store Assist] App zur Verwaltung von End-to-End-Workflows und -Prozessen für den Online-Kauf, Abruf von Bestellungen im Geschäft." '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# App-Einrichtung

Die Store-Hilfe ist eine Fulfillment-as-a-Service-Plattformanwendung (FaaS), die von Walmart Commerce Technologies unterstützt wird. Das Programm bietet In-Store-Funktionen zur Erfüllung von Aufgaben, die [!DNL buy online], [!DNL pick up in store] (BOPIS) Bestellungen.

Das Programm erhält alle Bestellungen- und Kundeninformationen - von Bestelldetails bis hin zur Erfassung der Zeiten - und stellt die Daten über Mobilgeräte zur Online-Speicherung von Assoziationen bereit. Mit der Store-Hilfe können Store-Mitarbeiter sehen, welche Artikel Kunden bestellt haben, die richtigen Artikel schneller auswählen und die ausgeführten Bestellungen für den In-Store- oder Cumulative Pickup-Versand an Kunden einrichten.

Store Associates verwenden die Store-Hilfe [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]und [!UICONTROL Orders] um den Versand- und Übermittlungsprozess wie folgt abzuschließen:

- Lieferdaten und -zeiten der Bestellung zuweisen
- Erhalt von Benachrichtigungen von Kunden, wenn sie zur Bestellabnahme in den Speicher eintreffen
- Staging-Aufträge für die Übergabe an Kunden
- Tracking des Bestellstatus für alle Bestellungen in ihren zugewiesenen Store-Standorten

Siehe [Workflows zur Erfüllung von Store-Hilfe](store-assist-modules.md) , um mehr über die Store Assist-App zu erfahren.


## Konfigurieren der Store Assist App

Die Store-Hilfe-App erfordert zwei Arten von Konfiguration:

- Adobe Commerce-Konfigurationseinstellungen in [Verwalten Sie Benutzerkonten, Benutzerrollen und Ressourcenberechtigungen über die Adobe Commerce Admin-Systemeinstellungen.](user-setup.md).

- Frontend-Konfigurationseinstellungen zum Anpassen der Benutzeroberfläche der Store-Hilfe-App und anderer Einstellungen, darunter:

   - **Brand the Store Assist app**—Passen Sie die Benutzeroberfläche des Programms mit Ihrem Firmenlogo und Ihren Farben an.

   - **Standardanweisungen aktualisieren**—Passen Sie die Anweisungen an, die in den Store-Assist-Schnittstellen für die Module &quot;Auswählen&quot;, &quot;Staging&quot;, &quot;Übergabe&quot;und &quot;Bestellung&quot;angezeigt werden, damit Ihre Partner genau wissen, was während jedes Schritts des Ausführungsprozesses zu tun ist.

   - **Lokalisierung**—Wählen Sie die verfügbare Sprache für die App aus, wählen Sie Ihr Datums- und Uhrzeitformat, wählen Sie die Standardmaßeinheiten und wählen Sie die Standardwährung aus.

   - **Inaktivitätszeit**—Geben Sie die Zeit an, die die App inaktiv sein muss, bevor sie sich abmeldet.

   - **Abbruch aus dem Store**—Geben Sie an, ob Bestellungen aus dem Store storniert werden können und welche Rollen über Abbruchsberechtigungen verfügen

   - **Bestellbereinigungsfenster**—Geben Sie an, wie lange die geplante Abholzeit vergangen ist, bis eine abgerufene Bestellung im Staging verbleibt, bevor sie wieder aufgestockt wird, z. B. drei Tage.

   - Alle In-App-Anweisungen anpassen (Auswählen, Staging, Übergabe)

   - **Benachrichtigungen auswählen**-Richten Sie ein, ob Sie Push-Benachrichtigungen verwenden möchten, um die Auswahl zu starten, sobald eine Bestellung aufgegeben wurde.

   - **Benachrichtigungen einchecken**-Richten Sie ein, ob Sie Push-Benachrichtigungen erhalten möchten, sobald ein Kunde eingecheckt hat/auf X Minuten wartet / oder gar keine Benachrichtigungen

   - **Übergabe**—Aktivieren Sie die Kundensignatur und aktivieren Sie eine Eingabeaufforderung, um die Kunden-ID zu überprüfen, bevor Sie die Bestellung abgeben.

   - **Elementabweisung bei Übergabe aktivieren**

   Arbeiten Sie mit dem Team von Walmart Commerce Technologies Client Services zusammen, um die Frontend-Konfiguration für die Store Assist App abzuschließen.

## App-Download und -Installation

Nachdem die Konfiguration der Store-Hilfe-App abgeschlossen wurde, können Store-Associates die Store-Hilfe-App auf ihre Mobilgeräte herunterladen und installieren und sich anmelden.

- Laden Sie die Store-Hilfe-App aus dem [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) oder im Google Play Store.

- Für die Anmeldung bei Store Associates sind die folgenden Informationen erforderlich:

   - Der Firmenname, der mit Ihrem Store Assist-Konto verknüpft ist

   - Speichern Sie die Anmeldeinformationen des Assist-Kontos - Benutzername und Kennwort-Anmeldeinformationen für das Konto.
   Ein Adobe Commerce-Administrator kann für Speicherorte mit [In-Store-Abruf](merchant-store-configuration.md#pickup-location-configuration) in den Admin Stores-Einstellungen aktiviert wurde.

