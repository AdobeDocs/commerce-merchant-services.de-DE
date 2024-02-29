---
title: Zeitreihen-Ereignisschemata für die Commerce-Datenerfassung aktualisieren
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenspeicher erstellen, um Zeitreihenereignisdaten für die Commerce-Datenerfassung zu erfassen und zu senden.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# Zeitreihen-Ereignisschemata für die Commerce-Datenerfassung aktualisieren

Eines der [Onboarding-Schritte](overview.md#onboarding-steps) für die Verwendung der [!DNL Data Connection] -Erweiterung für den Zugriff auf den Arbeitsbereich &quot;Datastream&quot;und [Erstellen eines Datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) die speziell für Adobe Commerce gilt. Wenn Sie diesen Datastream erstellen, müssen Sie auch ein Schema auswählen, das die zu erfassenden Daten beschreibt. Dieses Schema muss Commerce-spezifische Feldergruppen enthalten.

In diesem Artikel finden Sie die Feldergruppen, die Ihr Schema enthalten muss, um die folgenden Zeitreihendaten, die von den Adobe Commerce-Ereignissen bereitgestellt werden, erfolgreich erfassen zu können:

- [Verhalten](events.md) - Enthält Storefront-, Profil-, Such- und B2B-Ereignisse.
- [Backoffice](events-backoffice.md) - Enthält Bestellstatus- und Profilereignisse.

Weitere Informationen [Zeitreihendaten](data-ingestion.md).

Weitere Informationen zum [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Schema mit Zeitreihen-Verhaltens- und Back-Office-Ereignisdaten aktualisieren

In diesem Abschnitt erfahren Sie, wie Sie Ihr vorhandenes Schema aktualisieren oder ein Schema erstellen, um Verhaltens- und Back-Office-Ereignisdaten einzuschließen.

>[!NOTE]
>
>Siehe [Zeitreihen-Profilereignisdaten](#time-series-profile-event-data) , um zu erfahren, wie Sie profilspezifische Felder hinzufügen.

1. Wenn Sie noch kein Schema haben, [erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) , wobei die Klasse auf **Erlebnisereignis**.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden Commerce-spezifischen Feldergruppen (oder bearbeiten Sie Ihr vorhandenes Schema und fügen Sie diese Feldergruppen hinzu):

   - Site-Suche
   - Webseite besuchen
   - Benutzeranmeldungsprozess
   - Referenzschlüssel
   - Persönliche Kontaktangaben
   - Kanaldetails
   - Commerce-Details
   - Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)

   >[!NOTE]
   >
   > Legen Sie keine Commerce-spezifischen Feldergruppen als `Primary identity`. Dadurch wird das Feld nach Bedarf identifiziert und Experience Platform erwartet dieses Feld bei jedem Ereignis. Wenn dieses Feld fehlt, schlägt die Datenerfassung fehl.

   Ihr Schema enthält jetzt Commerce-spezifische Feldergruppen, sodass die aus dem Commerce erfassten Zeitreihendaten [Verhalten](events.md) und [Backoffice](events-backoffice.md) -Ereignisse werden im Schema dargestellt.

1. [Aktivieren](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenspeicher leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

1. **Beta** (Optional) Sie können benutzerdefinierte Attribute verwenden, wenn Sie benutzerdefinierte Back-Office-Ereignisdaten aus Ihrer Commerce-Instanz an die Experience Platform übergeben möchten. Diese Funktion befindet sich in der Beta-Phase. Wenn Sie dem Betaprogramm beitreten möchten, senden Sie eine Anfrage an [dataconnection@adobe.com](mailto:dataconnection@adobe.com). Schließen Sie Folgendes in Ihre Anfrage ein:

   - Ihre [Adobe-Organisations-ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Beispiel `organization_id@AdobeOrg`.
   - Liste der benutzerdefinierten Attribute auf Bestellebene.
   - Liste der Attribute auf Bestellelementebene.

   Das Adobe Commerce-Team wird Sie mit weiteren Informationen und den nächsten Schritten kontaktieren.

Mit den für Verhaltens- und Back-Office-Daten konfigurierten Schemata, Datensätzen und Datenspeichern können Sie [konfigurieren](connect-data.md#data-collection) Ihre Commerce-Instanz, um diese Daten zu erfassen und an die Experience Platform zu senden.

Informationen zum Einschließen der Profilinformationen Ihres Käufers finden Sie im nächsten Abschnitt.

## Zeitreihenprofilereignisdaten

Zeitreihenprofilereignisdaten werden aus den folgenden Ereignissen generiert:

- [`accountCreated`](events-backoffice.md#accountcreated)
- [`accountUpdated`](events-backoffice.md#accountupdated)
- [`accountDeleted`](events-backoffice.md#accountdeleted)

Wenn Sie die Profilereignisdaten Ihres Kunden in die Experience Platform aufnehmen möchten, können Sie Ihr bestehendes Commerce-Schema aktualisieren und denselben bereits konfigurierten Datastraam verwenden oder einen profilspezifischen Datastream und ein Schema erstellen. Diese Entscheidung basiert auf der Data Governance Ihres Unternehmens. Die nächsten beiden Abschnitte führen Sie durch beide Fälle.

### Senden von Zeitreihenereignisdaten an Experience Platform mithilfe Ihres vorhandenen Datenspeichers

Wenn Sie Zeitreihen hinzufügen möchten [Serverseitige Profilereignisdaten](events-backoffice.md#customer-profile-events-server-side) Fügen Sie Ihrem vorhandenen Commerce-Datastream den `Demographic Details` Feldergruppe in Ihr Schema ein. Ihr Schema enthält jetzt die folgenden Commerce-spezifischen Feldergruppen:

- Site-Suche
- Webseite besuchen
- Benutzeranmeldungsprozess
- Referenzschlüssel
- Persönliche Kontaktangaben
- Kanaldetails
- Commerce-Details
- Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)
- Neu: **Demografische Details**

Mit dem Zusatz `Demographic Details` -Feldergruppe in Ihrem vorhandenen Commerce-Schema verwenden, werden der Datensatz und der Datensatz, der bereits mit Ihrem Commerce-Schema verknüpft ist, für diese Zeitreihen-Profildaten verwendet.

### Senden von Zeitreihenereignisdaten an Experience Platform in einem separaten Datastream

Wenn Sie [Serverseitige Profilereignisdaten](events-backoffice.md#customer-profile-events-server-side) Führen Sie die folgenden Schritte aus, um einen neuen profilspezifischen Datastream und ein neues Schema zu erstellen.

1. [Erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) ein Schema und legen Sie die Klasse auf **Erlebnisereignis**.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden profilspezifischen Feldergruppen:

   - Demografische Details
   - Persönliche Kontaktangaben
   - Kanaldetails
   - Commerce-Details

1. [Aktivieren](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenspeicher leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

Mit den für Kundenprofildaten konfigurierten Schemas, Datensätzen und Datenspeichern können Sie [konfigurieren](connect-data.md#data-collection) Ihre Commerce-Instanz, um diese Daten zu erfassen und an Experience Platform zu senden.

Informationen zum Erstellen eines Schemas, Datensatzes und Datastreams für Profildatensatzdaten finden Sie unter [Profildatensatzdaten an die Experience Platform senden](profile-data.md).
