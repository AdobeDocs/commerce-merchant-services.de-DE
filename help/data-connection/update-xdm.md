---
title: Zeitreihen-Ereignisschemata für die Commerce-Datenerfassung aktualisieren
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenspeicher erstellen, um Zeitreihenereignisdaten für die Datenerfassung in Commerce zu erfassen und zu senden.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 90ddfdd41958b254fc0c2f3e0891385193f1bb9c
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Zeitreihen-Ereignisschemata für die Commerce-Datenerfassung aktualisieren

Einer der [Onboarding-Schritte](overview.md#onboarding-steps) für die Verwendung der [!DNL Data Connection] -Erweiterung besteht darin, auf den Arbeitsbereich &quot;Datastream&quot;zuzugreifen und [einen für Adobe Commerce spezifischen Datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) zu erstellen. Wenn Sie diesen Datastream erstellen, müssen Sie auch ein Schema auswählen, das die zu erfassenden Daten beschreibt. Dieses Schema muss Commerce-spezifische Feldergruppen enthalten.

In diesem Artikel finden Sie die Feldergruppen, die Ihr Schema enthalten muss, um die folgenden Zeitreihendaten, die von den Adobe Commerce-Ereignissen bereitgestellt werden, erfolgreich erfassen zu können:

- [Verhalten](events.md) - Umfasst Storefront-, Profil-, Such- und B2B-Ereignisse.
- [Zurück-Büro](events-backoffice.md) - Umfasst Bestellstatus- und Profilereignisse.

Erfahren Sie mehr über [Zeitreihendaten](data-ingestion.md).

Erfahren Sie mehr über die [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Schema mit Zeitreihen-Verhaltens- und Back-Office-Ereignisdaten aktualisieren

In diesem Abschnitt erfahren Sie, wie Sie Ihr vorhandenes Schema aktualisieren oder ein Schema erstellen, um Verhaltens- und Back-Office-Ereignisdaten einzuschließen.

>[!NOTE]
>
>Informationen zum Hinzufügen profilspezifischer Felder finden Sie unter [Zeitreihenereignisdaten](#time-series-profile-event-data) .

1. Wenn Sie noch kein Schema haben, erstellen Sie [ein Schema mit der Klasse **Erlebnisereignis**.](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create)

1. [Fügen Sie ](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden Commerce-spezifischen Feldergruppen hinzu (oder bearbeiten Sie Ihr vorhandenes Schema und fügen Sie diese Feldergruppen hinzu):

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
   > Setzen Sie keine Commerce-spezifischen Feldergruppen auf &quot;`Primary identity`&quot;. Dadurch wird das Feld nach Bedarf identifiziert und Experience Platform erwartet dieses Feld bei jedem Ereignis. Wenn dieses Feld fehlt, schlägt die Datenerfassung fehl.

   Ihr Schema enthält jetzt Commerce-spezifische Feldergruppen, sodass die Zeitreihendaten, die aus den Commerce-Ereignissen [Verhalten](events.md) und [Zurück-Büro](events-backoffice.md) erfasst wurden, im Schema dargestellt werden.

1. [Aktivieren Sie](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Erstellen Sie einen Datensatz](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen Sie einen Datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenspeicher leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

Mit den für Verhaltens- und Back-Office-Daten konfigurierten Schemata, Datensätzen und Datensätzen können Sie [konfigurieren](connect-data.md#data-collection), dass Ihre Commerce-Instanz diese Daten erfasst und an die Experience Platform sendet.

Informationen zum Einschließen der Profilinformationen Ihres Käufers finden Sie unter [Ereignisdaten des Zeitreihenprofils](#time-series-profile-event-data).

### Hinzufügen benutzerdefinierter Attribute

Sie können benutzerdefinierte Attribute verwenden, wenn Sie benutzerdefinierte Back-Office-Ereignisdaten von Ihrer Commerce-Instanz an die Experience Platform übergeben möchten.

Benutzerdefinierte Attribute werden auf zwei Ebenen unterstützt:

- Bestellebene
- Bestellelementebene

>[!NOTE]
>
>Adobe Commerce unterstützt benutzerdefinierte Attribute mit einem Datentyp aus Zeichenfolge oder Zeichenfolge-Array.

1. Fügen Sie ein zusätzliches Modul in Ihrer [!DNL Commerce] -Anwendung hinzu und aktivieren Sie es. Siehe folgendes [Beispiel](https://github.com/shiftedreality/beacon-backoffice-custom-events/blob/main/BeaconDemo/Plugin/ModifyOrder.php).

   Sie müssen den Beispielcode ändern, um zusätzliche benutzerdefinierte Attribute verfügbar zu machen. Die Implementierung variiert je nachdem, wo diese Attribute gespeichert werden und welche Logik für ihre Extraktion erforderlich ist.

1. Erweitern Sie Ihr vorhandenes XDM-Schema. Im folgenden [Handbuch](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) finden Sie Informationen zum Erstellen benutzerdefinierter Attribute für die Bestellungs- und Bestellelementebenen. Das Feld Mandanten-ID wird dynamisch generiert, die Feldstruktur sollte jedoch dem angegebenen Beispiel ähneln.

   >[!IMPORTANT]
   >
   >Benutzerdefinierte XDM-Attribute müssen mit den von [!DNL Commerce] gesendeten Attributen übereinstimmen.

1. Stellen Sie sicher, dass der Ihrem XDM-Schema zugeordnete Datastream mit dem auf der Registerkarte [Datenerfassung](connect-data.md#data-collection) angegebenen Datastream übereinstimmt.

1. Klicken Sie auf der Registerkarte **Datenerfassung** auf **[!UICONTROL Save]** , um alle von Ihnen angegebenen benutzerdefinierten Attribute abzurufen.

## Zeitreihenprofilereignisdaten

Zeitreihenprofilereignisdaten werden aus den folgenden Ereignissen generiert:

- [`accountCreated`](events-backoffice.md#accountcreated)
- [`accountUpdated`](events-backoffice.md#accountupdated)
- [`accountDeleted`](events-backoffice.md#accountdeleted)

Wenn Sie die Profilereignisdaten Ihres Kunden in die Experience Platform aufnehmen möchten, können Sie Ihr bestehendes Commerce-Schema aktualisieren und denselben bereits konfigurierten Datastraam verwenden oder einen profilspezifischen Datastream und ein Schema erstellen. Diese Entscheidung basiert auf der Data Governance Ihres Unternehmens. Die nächsten beiden Abschnitte führen Sie durch beide Fälle.

### Senden von Zeitreihenereignisdaten an Experience Platform mithilfe Ihres vorhandenen Datenspeichers

Wenn Sie dem vorhandenen Commerce-Datenspeicher die Zeitreihen [serverseitige Profilereignisdaten](events-backoffice.md#customer-profile-events-server-side) hinzufügen möchten, fügen Sie Ihrem Schema die Feldergruppe `Demographic Details` hinzu. Ihr Schema enthält jetzt die folgenden Commerce-spezifischen Feldergruppen:

- Site-Suche
- Webseite besuchen
- Benutzeranmeldungsprozess
- Referenzschlüssel
- Persönliche Kontaktangaben
- Kanaldetails
- Commerce-Details
- Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)
- Neu: **Demografische Details**

Durch Hinzufügen der Feldergruppe &quot;`Demographic Details`&quot;in Ihrem bestehenden Commerce-Schema werden der Datensatz und der Datensatz, der bereits mit Ihrem Commerce-Schema verknüpft ist, für diese Zeitreihenprofildaten verwendet.

### Senden von Zeitreihenereignisdaten an Experience Platform in einem separaten Datastream

Wenn Sie [serverseitige Profilereignisdaten](events-backoffice.md#customer-profile-events-server-side) zu einem neuen profilspezifischen Datastream und Schema hinzufügen möchten, führen Sie die folgenden Schritte aus.

1. [Erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) Sie ein Schema und legen Sie die Klasse auf **Erlebnisereignis** fest.

1. [Fügen Sie ](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden profilspezifischen Feldergruppen hinzu:

   - Demografische Details
   - Persönliche Kontaktangaben
   - Kanaldetails
   - Commerce-Details

1. [Aktivieren Sie](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Erstellen Sie einen Datensatz](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen Sie einen Datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenspeicher leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.

Mit den für Kundenprofildaten konfigurierten Schemata, Datensätzen und Datenspeichern können Sie Ihre Commerce-Instanz so konfigurieren, dass diese Daten erfasst und an die Experience Platform gesendet werden.[](connect-data.md#data-collection)

Informationen zum Erstellen eines Schemas, Datensatzes und Datastreams für Profildatensatzdaten finden Sie unter [Senden von Profildatensatzdaten an die Experience Platform](profile-data.md).
