---
title: App-Einrichtung
description: Richten Sie die [!DNL Store Assist] App zur Verwaltung von End-to-End-Workflows und -Prozessen für Online-Käufe, Abruf von Kaufaufträgen.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# App-Einrichtung

Die Store-Hilfe ist eine Fulfillment-as-a-Service-Plattformanwendung (FaaS), die von Walmart Commerce Technologies unterstützt wird. Das Programm bietet In-Store-Funktionen zur Erfüllung von Aufgaben, die [!DNL buy online, pick up in store] Bestellungen. Mit der Store-Hilfe können Store-Mitarbeiter sehen, welche Artikel Kunden bestellt haben, die richtigen Artikel schneller auswählen und die ausgeführten Bestellungen für den In-Store- oder Cumulative Pickup-Versand an Kunden einrichten.

Die Store-Hilfe-App empfängt alle Bestellungen- und Kundeninformationen - von Bestelldetails bis zur Abholung von Zeiten - und stellt die Daten über Mobilgeräte für die Online-Speicherung von Assoziationen zur Verfügung. Die App enthält [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], und [!UICONTROL Orders] -Module zur Unterstützung von Store-Zuordnungen zu Fulfillment-Aktivitäten wie den folgenden:

- Datum und Uhrzeit des Bestellversands zuweisen.
- Erhalten Sie Benachrichtigungen von Kunden, wenn sie zur Bestellabnahme eintreffen.
- Staging-Bestellungen für die Übergabe an Kunden.
- Verfolgen Sie den Bestellstatus für alle Bestellungen an ihren zugewiesenen Speicherorten.

>[!NOTE]
>
>Weitere Informationen zur Store Assist-App finden Sie unter [Workflows zur Erfüllung von Store-Hilfe](store-assist-modules.md) Thema.

## Konfigurieren der Store Assist App

Die Store-Hilfe-App erfordert zwei Arten von Konfiguration:

- Systemeinstellungen von Adobe Commerce Admin auf [Verwalten von Benutzerkonten, Benutzerrollen, Ressourcenberechtigungen](user-setup.md), und [die Automarken- und Modellauswahlen, die den Kunden während des Eincheckvorgangs zur Verfügung stehen](check-in-experience-setup.md).

- Frontend-Konfigurationseinstellungen zum Anpassen der Benutzeroberfläche der Store-Hilfe-App und anderer Einstellungen, darunter:

   - **Brand the Store Assist app**- Passen Sie die Benutzeroberfläche des Programms mit Ihrem Firmenlogo und Ihren Farben an.

   - **Standardanweisungen aktualisieren**—Passen Sie die Anweisungen in den Modulen &quot;Store-Hilfe&quot;, &quot;Staging&quot;, &quot;Übergabe&quot;und &quot;Bestellung&quot;an, um Store-Associates durch jeden Schritt des Erfüllung-Workflows für Ihr Unternehmen zu führen.

   - **Lokalisierung**- Wählen Sie die für die App verfügbare Sprache aus. Wählen Sie das Datums- und Uhrzeitformat und dann die Standardmaßeinheiten und die Standardwährung aus.

   - **Inaktivitätszeit**- Geben Sie die Zeit an, die die App inaktiv sein muss, bevor sie sich abmeldet.

   - **Abbruch aus dem Store**—Geben Sie an, ob Bestellungen im Store abgebrochen werden können und welche Rollen über Abbruchsberechtigungen verfügen

   - **Bestellbereinigungsfenster**—Geben Sie an, wie lange die [Geschätzte Abruf-Vorlaufzeit](enable-general.md#delivery-method-title-configuration) dass eine abgerufene Bestellung im Staging verbleibt, bevor sie wieder aufgestockt wird, z. B. drei Tage. Der Standardwert ist sieben Tage. Wenn diese Konfiguration aktiviert ist, wird die Bestellung automatisch abgebrochen, wenn diese Zeit abläuft. Die Artikel werden wieder aufgestockt und der Händler erhält eine Abmelde-E-Mail.

   - Passen Sie alle Anweisungen in der App an (Auswählen, Staging, Übergabe).

   - **Benachrichtigungen auswählen**—Geben Sie an, ob eine Push-Benachrichtigung gesendet werden soll, um den Pickingprozess zu starten, nachdem ein Kunde eine Bestellung aufgegeben hat.

   - **Benachrichtigungen einchecken**—Geben Sie an, ob eine Push-Benachrichtigung während des Eincheckvorgangs für die Bestellabholung nach dem Einchecken gesendet werden soll, nachdem die Wartezeit des Kunden einen bestimmten Zeitraum überschreitet. Oder deaktivieren Sie die Benachrichtigung.

   - **Übergabe-Prozess**—Aktivieren Sie optionale Prozesse, wenn Store Associate die Bestellung an den Kunden bereitstellt, z. B. eine Kundenunterschrift erforderlich ist oder die Zuordnung zur Prüfung der Kunden-ID auffordert.

   - **Elementabweisung bei Übergabe aktivieren**- Ermöglichen Sie Kunden, während der Bestellübergabe Bestellartikel zurückzugeben oder abzubrechen.

  Arbeiten Sie mit dem Team von Walmart Commerce Technologies Client Services zusammen, um die Frontend-Konfiguration für die Store Assist App abzuschließen.

## App-Download und -Installation

Nachdem die Store-Assist-App eingerichtet und konfiguriert wurde, können Store Associates von ihren Mobilgeräten aus die Store-Hilfe-App herunterladen, installieren und sich bei ihr anmelden.

- Stellen Sie sicher, dass das Mobilgerät die [Hardware- und Softwareanforderungen](solution-requirements.md#store-assist-app-requirements) für die Lösung Store Fulfillment .

- Laden Sie die Store-Hilfe-App aus dem [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Für die Anmeldung bei Store Associates sind die folgenden Informationen erforderlich:

   - **[!UICONTROL Company name]** mit dem Store Assist-Konto verknüpft ist

   - **Anmeldeinformationen des Store-Assist-Kontos**—Benutzername und Passwort für ihr Konto.

  Ein Adobe Commerce-Administrator kann [!DNL Store Assist app] Benutzerkonten für alle Speicherorte mit [In-Store-Abruf](merchant-store-configuration.md#pickup-location-configuration) in den Admin Stores-Einstellungen aktiviert wurde.
