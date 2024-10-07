---
title: Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenspeicher erstellen, um Commerce-Profildatensatzdaten zu erfassen und an die Experience Platform zu senden.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 86a3ba12-7f26-4f7e-98a0-9af0d1d8d881
source-git-commit: b5727c90737ecfd237dd143801152f25600c3f97
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung

Wenn Ihre Kunden ein Profil auf Ihrer Commerce-Site erstellen, wird ein Profildatensatz erstellt und Daten erfasst. Sie müssen ein für diesen Profildatensatz spezifisches Schema und einen Datensatz erstellen, bevor Sie diese Profildaten an die Experience Platform streamen können.

1. [Erstellen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) Sie ein Schema und legen Sie die Klasse auf **Individuelles Profil** fest.

1. [Fügen Sie ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) die folgenden profilspezifischen Feldergruppen hinzu:

   - identityMap
   - Demografische Details
   - Persönliche Kontaktangaben
   - Details zum Benutzerkonto

1. [Aktivieren Sie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Erstellen Sie einen Datensatz](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. Erstellen Sie einen [benutzerdefinierten Namensraum](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) im Experience Platform mit den folgenden Werten:

   - **Anzeigename**: _Commerce-Kunden-ID_
   - **Identitätssymbol**: _CustomerId_
   - **Typ**: _Individuelle geräteübergreifende ID_

   ![Benutzerdefinierten Namespace erstellen](assets/custom-namespace.png){width="700" zoomable="yes"}

   Klicken Sie auf **[!UICONTROL Create]**. Der Unified Profile Service verwendet einen benutzerdefinierten Namespace zum Zusammenfügen von Profilfragmenten.

Wenn das Schema, der Datensatz und der benutzerdefinierte Namensraum für Kundenprofildatensatzdaten konfiguriert sind, können Sie Ihre Commerce-Instanz so konfigurieren, dass diese Daten erfasst und an die Experience Platform gesendet werden.[](connect-data.md#data-collection)

Informationen zum Erstellen eines Schemas, Datensatzes und Datastreams für Verhaltens- und Back-Office-Ereignisdaten finden Sie unter [Aktualisieren von Zeitreihenereignisschemas für die Commerce-Datenerfassung](update-xdm.md).
