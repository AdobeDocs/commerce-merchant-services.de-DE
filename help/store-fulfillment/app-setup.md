---
title: App-Einrichtung
description: Richten Sie die [!DNL Store Assist] App zur Verwaltung von End-to-End-Workflows und -Prozessen für Online-Käufe, Abruf von Kaufaufträgen.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 68e615671f4e465d7fe89794613dbf129ae66dbf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# App-Einrichtung

Die Store-Hilfe ist eine Fulfillment-as-a-Service-Plattformanwendung (FaaS), die von Walmart Commerce Technologies unterstützt wird. Das Programm bietet In-Store-Funktionen zur Erfüllung von Aufgaben, die [!DNL buy online], [!DNL pick up in store] (BOPIS) Bestellungen.  Mit der Store-Hilfe können Store-Mitarbeiter sehen, welche Artikel Kunden bestellt haben, die richtigen Artikel schneller auswählen und die ausgeführten Bestellungen für den In-Store- oder Cumulative Pickup-Versand an Kunden einrichten.

Die Store-Hilfe-App empfängt alle Bestellungen- und Kundeninformationen - von Bestelldetails bis zur Abholung von Zeiten - und stellt die Daten über Mobilgeräte für die Online-Speicherung von Assoziationen zur Verfügung. Die App enthält [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]und [!UICONTROL Orders] -Module zur Unterstützung von Store-Zuordnungen zu Fulfillment-Aktivitäten wie den folgenden:

- Weisen Sie Lieferdaten und -zeiten der Bestellung zu.
- Erhalten Sie Benachrichtigungen von Kunden, wenn sie zur Bestellabnahme eintreffen.
- Staging-Bestellungen für die Übergabe an Kunden.
- Verfolgen Sie den Bestellstatus für alle Bestellungen an ihren zugewiesenen Speicherorten.

>[!NOTE]
>
>Siehe [Workflows zur Erfüllung von Store-Hilfe](store-assist-modules.md) , um mehr über die Store Assist-App zu erfahren.

## Konfigurieren der Store Assist App

Die Store-Hilfe-App erfordert zwei Arten von Konfiguration:

- Adobe Commerce-Konfigurationseinstellungen in [Verwalten von Benutzerkonten, Benutzerrollen und Ressourcenberechtigungen über die Adobe Commerce Admin-Systemeinstellungen](user-setup.md).

- Frontend-Konfigurationseinstellungen zum Anpassen der Benutzeroberfläche der Store-Hilfe-App und anderer Einstellungen, darunter:

   - **Brand the Store Assist app**- Passen Sie die Benutzeroberfläche des Programms mit Ihrem Firmenlogo und Ihren Farben an.

   - **Standardanweisungen aktualisieren**—Passen Sie die Anweisungen in den Store-Assist-Schnittstellen für die Module &quot;Auswählen&quot;, &quot;Staging&quot;, &quot;Übergabe&quot;und &quot;Bestellung&quot;an, um Ihren Unternehmensrichtlinien und -verfahren zu entsprechen, und leiten Sie Store-Verknüpfungen durch jeden Schritt des Erfüllung-Workflows.

   - **Lokalisierung**- Wählen Sie die für die App verfügbare Sprache aus. Wählen Sie das Datums- und Uhrzeitformat und dann die Standardmaßeinheiten und die Standardwährung aus.

   - **Inaktivitätszeit**- Geben Sie die Zeit an, die die App inaktiv sein muss, bevor sie sich abmeldet.

   - **Abbruch aus dem Store**—Geben Sie an, ob Bestellungen aus dem Store storniert werden können und welche Rollen über Abbruchsberechtigungen verfügen

   - **Bestellbereinigungsfenster**—Geben Sie an, wie lange die geplante Abholzeit vergangen ist, bis eine abgerufene Bestellung im Staging verbleibt, bevor sie wieder aufgestockt wird, z. B. drei Tage.

   - Passen Sie alle Anweisungen in der App an (Auswählen, Staging, Übergabe).

   - **Benachrichtigungen auswählen**—Geben Sie an, ob eine Push-Benachrichtigung gesendet werden soll, um den Pickingprozess zu starten, nachdem ein Kunde eine Bestellung aufgegeben hat.

   - **Benachrichtigungen einchecken**—Geben Sie an, ob eine Push-Benachrichtigung während des Eincheckvorgangs für die Bestellabholung nach dem Einchecken gesendet werden soll, nachdem die Wartezeit des Kunden einen bestimmten Zeitraum überschreitet. Oder deaktivieren Sie die Benachrichtigung.

   - **Übergabe**—Aktivieren Sie optionale Prozesse, wenn Store Associate die Bestellung an den Kunden bereitstellt, z. B. eine Kundenunterschrift erforderlich ist oder die Zuordnung auffordert, die Kunden-ID zu überprüfen.

   - **Elementabweisung bei Übergabe aktivieren**- Ermöglichen Sie Kunden, während der Bestellübergabe Bestellartikel zurückzugeben oder abzubrechen.
   Arbeiten Sie mit dem Team von Walmart Commerce Technologies Client Services zusammen, um die Frontend-Konfiguration für die Store Assist App abzuschließen.

## App-Download und -Installation

Nachdem die Konfiguration der Store-Hilfe-App abgeschlossen ist, können Store-Associates von ihren Mobilgeräten aus die Store-Hilfe-App herunterladen, installieren und sich bei ihr anmelden.

- Stellen Sie sicher, dass das Mobilgerät die [Hardware- und Softwareanforderungen](solution-requirements.md#store-assist-app-requirements) für die Lösung Store Fulfillment .

- Laden Sie die Store-Hilfe-App aus dem [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target=&quot;_blank&quot;} oder die [Google Play Store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}.

- Für die Anmeldung bei Store Associates sind die folgenden Informationen erforderlich:

   - **[!UICONTROL Company name]** mit dem Store Assist-Konto verknüpft ist

   - **Anmeldeinformationen des Store-Assist-Kontos**—Benutzername und Passwort für ihr Konto.
   Ein Adobe Commerce-Administrator kann ein Benutzerkonto erstellen und Berechtigungen für die Benutzerkonten der Store Assist App für Speicherorte mit [In-Store-Abruf](merchant-store-configuration.md#pickup-location-configuration) in den Admin Stores-Einstellungen aktiviert wurde.
