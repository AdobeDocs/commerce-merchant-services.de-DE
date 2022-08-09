---
title: Hinzufügen von Feldgruppen zum XDM-Schema
description: Erfahren Sie, wie Sie Adobe Commerce-spezifische Feldergruppen zu einem XDM-Schema hinzufügen.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Hinzufügen von Feldergruppen zum XDM-Schema

Eines der [Voraussetzungen](overview.md#prereqs) über den Experience Platform Connector auf den Arbeitsbereich &quot;Datastream&quot;zugreifen und [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) die speziell für Adobe Commerce gilt. Wenn Sie diesen Datastream erstellen, müssen Sie auch ein XDM-Schema auswählen, das die zu erfassenden Daten darstellt. Dieses Thema stellt die Feldergruppen bereit, die Ihr XDM-Schema beinhalten muss, um die von der Adobe Commerce-Storefront bereitgestellten Daten erfolgreich erfassen zu können. [events](events.md).

1. Wenn Sie noch kein XDM-Schema haben, [erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) eine. Andernfalls [edit](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) Ihr vorhandenes XDM-Schema in der Adobe Experience Platform-Benutzeroberfläche.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) die folgenden Commerce-spezifischen Feldergruppen:

   - Handel
   - Site-Suche
   - Webseite besuchen
   - Benutzeranmeldungsprozess
   - Referenzschlüssel
   - Persönliche Kontaktangaben
   - Commerce-Details
   - Adobe Analytics Experience Event Commerce (wenn Sie Daten an Adobe Analytics senden möchten)
   - Personen-ID

   >[!NOTE]
   >
   > Legen Sie keine Commerce-spezifischen Feldergruppen als `Primary identity`. Dadurch wird das Feld nach Bedarf identifiziert und die Experience Platform erwartet dieses Feld bei jedem Ereignis. Wenn dieses Feld fehlt, schlägt die Datenerfassung fehl.

   Ihr XDM-Schema enthält jetzt Commerce-spezifische Feldergruppen, sodass die aus dem Commerce-Store erfassten Daten [events](events.md) wird im XDM dargestellt.

1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
