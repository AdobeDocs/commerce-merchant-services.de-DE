---
title: App-Einrichtung
description: Richten Sie die [!DNL Store Assist] App ein, um die End-to-End-Workflows und -Prozesse zur Store-Erfüllung zu verwalten, damit Sie online kaufen und Bestellungen im Geschäft abrufen können.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# App-Einrichtung

Die Store-Hilfe ist eine Fulfillment-as-a-Service-Plattformanwendung (FaaS) mit Unterstützung von Walmart Commerce Technologies. Die App bietet In-Store-Funktionen zur Erfüllung von [!DNL buy online, pick up in store] -Bestellungen (BOPIS). Mit der Store-Hilfe können Store-Mitarbeiter sehen, welche Artikel Kunden bestellt haben, die richtigen Artikel schneller auswählen und die ausgeführten Bestellungen für den In-Store- oder Cumulative Pickup-Versand an Kunden einrichten.

Die Store-Hilfe-App empfängt alle Bestellungen- und Kundeninformationen - von Bestelldetails bis zur Abholung von Zeiten - und stellt die Daten über Mobilgeräte für die Online-Speicherung von Assoziationen zur Verfügung. Die App enthält die Module [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff] und [!UICONTROL Orders], um Store-Zuordnungen zu Erfüllungsaktivitäten wie den folgenden zu unterstützen:

- Datum und Uhrzeit des Bestellversands zuweisen.
- Erhalten Sie Benachrichtigungen von Kunden, wenn sie zur Bestellabnahme eintreffen.
- Staging-Bestellungen für die Übergabe an Kunden.
- Verfolgen Sie den Bestellstatus für alle Bestellungen an ihren zugewiesenen Speicherorten.

>[!NOTE]
>
>Erfahren Sie mehr über die Store-Hilfe-App, indem Sie sich das Thema [Workflows zur Unterstützung von Store-Anfragen](store-assist-modules.md) ansehen.

## Konfigurieren der Store Assist App

Die Store-Hilfe-App erfordert zwei Arten von Konfiguration:

- Adobe Commerce Admin-Systemeinstellungen für [Verwalten von Benutzerkonten, Benutzerrollen, Ressourcenberechtigungen](user-setup.md) und [die Automarken- und Modellauswahlen, die Kunden während des Eincheckvorgangs zur Verfügung stehen](check-in-experience-setup.md).

- Frontend-Konfigurationseinstellungen zum Anpassen der Benutzeroberfläche der Store-Hilfe-App und anderer Einstellungen, darunter:

   - **Brand the Store Assist app** - Passen Sie die Benutzeroberfläche der App mit Ihrem Firmenlogo und Ihren Farben an.

   - **Standardanweisungen aktualisieren**: Passen Sie die Anweisungen in den Modulen &quot;Store-Hilfe&quot;, &quot;Staging&quot;, &quot;Übergabe&quot;und &quot;Bestellung&quot;an, um Store-Associates durch jeden Schritt des Erfüllung-Workflows für Ihr Unternehmen zu führen.

   - **Lokalisierung**: Wählen Sie die für die App verfügbare Sprache aus. Wählen Sie das Datums- und Uhrzeitformat und dann die Standardmaßeinheiten und die Standardwährung aus.

   - **Inaktivitätszeit**: Geben Sie die Zeit an, die die App inaktiv sein muss, bevor sie sich abmeldet.

   - **Abbruch aus dem Store** - Geben Sie an, ob Bestellungen aus dem Store abgebrochen werden können und welche Rollen über Abbruchsberechtigungen verfügen

   - **Auftragsbereinigungsfenster**: Geben Sie an, wie lange die [Geschätzte Abruf-Lead-Zeit](enable-general.md#delivery-method-title-configuration) vergangen ist, die eine abgerufene Bestellung im Staging verbleibt, bevor sie wieder aufgestockt wird, z. B. drei Tage. Der Standardwert ist sieben Tage. Wenn diese Konfiguration aktiviert ist, wird die Bestellung nach Ablauf dieser Zeit automatisch abgebrochen. Die Artikel werden wieder aufgestockt und der Händler erhält eine Abmelde-E-Mail.

   - Passen Sie alle Anweisungen in der App an (Auswählen, Staging, Übergabe).

   - **Benachrichtigungen auswählen**: Geben Sie an, ob eine Push-Benachrichtigung gesendet werden soll, um den Pickingprozess zu starten, nachdem ein Kunde eine Bestellung aufgegeben hat.

   - **In-Benachrichtigungen einchecken** - Geben Sie an, ob eine Push-Benachrichtigung während des Eincheckvorgangs für die Bestellabholung gesendet werden soll - nach dem Einchecken, nachdem die Kundenwartezeit einen bestimmten Zeitraum überschreitet. Oder deaktivieren Sie die Benachrichtigung.

   - **Übergabe-Prozess**: Aktivieren Sie optionale Prozesse, wenn Store Associate Aufträge für Kunden bereitstellt, z. B. eine Kundensignatur oder eine Aufforderung zur Überprüfung der Kunden-ID durch den Mitarbeiter erforderlich ist.

   - **Elementabweisung bei Übergabe aktivieren** - Ermöglichen Sie Kunden, Bestellartikel während der Auftragsübergabe zurückzugeben oder abzubrechen.

  Arbeiten Sie mit dem Team von Walmart Commerce Technologies Client Services zusammen, um die Frontend-Konfiguration für die Store Assist App abzuschließen.

## App-Download und -Installation

Nachdem die Store-Assist-App eingerichtet und konfiguriert wurde, können Store Associates von ihren Mobilgeräten aus die Store-Hilfe-App herunterladen, installieren und sich bei ihr anmelden.

- Stellen Sie sicher, dass das Mobilgerät die [Hardware- und Softwareanforderungen](solution-requirements.md#store-assist-app-requirements) für die Store Fulfillment-Lösung erfüllt.

- Laden Sie die Store Assist App vom [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} oder vom [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"} herunter.

- Für die Anmeldung bei Store Associates sind die folgenden Informationen erforderlich:

   - **[!UICONTROL Company name]** im Zusammenhang mit dem Store Assist-Konto

   - **Anmeldeinformationen des Assist-Kontos speichern** - Benutzername- und Kennwortberechtigungen für ihr Konto.

  Ein Adobe Commerce-Administrator kann [!DNL Store Assist app]-Benutzerkonten für alle Speicherorte erstellen und verwalten, für die in den Einstellungen für &quot;Admin Stores&quot;die Option [In-Store-Abruf](merchant-store-configuration.md#pickup-location-configuration) aktiviert ist.
