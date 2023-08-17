---
title: Hinzufügen von Feldgruppen zum XDM-Schema
description: Erfahren Sie, wie Sie Adobe Commerce-spezifische Feldergruppen zu einem XDM-Schema hinzufügen.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Hinzufügen von Feldergruppen zum XDM-Schema

Eines der [Onboarding-Schritte](overview.md#onboarding-steps) über den Experience Platform-Connector auf den Arbeitsbereich &quot;Datastream&quot;zugreifen und [Erstellen eines Datastreams](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) die speziell für Adobe Commerce gilt. Wenn Sie diesen Datastream erstellen, müssen Sie auch ein XDM-Schema auswählen, das die zu erfassenden Daten darstellt. Dieses Thema stellt die Feldergruppen bereit, die Ihr XDM-Schema beinhalten muss, um die von der Adobe Commerce-Storefront bereitgestellten Daten erfolgreich erfassen zu können. [events](events.md).

1. Wenn Sie noch kein XDM-Schema haben, [erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) eine. Andernfalls [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Ihr vorhandenes XDM-Schema in der Adobe Experience Platform-Benutzeroberfläche.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden Commerce-spezifischen Feldergruppen:

   - Site-Suche
   - Webseite besuchen
   - Benutzeranmeldungsprozess
   - Referenzschlüssel
   - Persönliche Kontaktangaben
   - Commerce-Details
   - Adobe Analytics ExperienceEvent Commerce (wenn Sie Daten an Adobe Analytics senden möchten)
   - Identity Map

   >[!NOTE]
   >
   > Legen Sie keine Commerce-spezifischen Feldergruppen als `Primary identity`. Dadurch wird das Feld nach Bedarf identifiziert und Experience Platform erwartet dieses Feld bei jedem Ereignis. Wenn dieses Feld fehlt, schlägt die Datenerfassung fehl.

   Ihr XDM-Schema enthält jetzt Commerce-spezifische Feldergruppen, sodass die aus dem Commerce-Store erfassten Daten [events](events.md) wird im XDM dargestellt.

1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Sammlung von Daten, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen und den entsprechenden Datensatz enthält.

   Der Datenspeicher leitet die erfassten Daten an den Datensatz weiter. Die Daten werden im Datensatz basierend auf dem ausgewählten Schema dargestellt.
