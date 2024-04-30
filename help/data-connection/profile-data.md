---
title: Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenspeicher erstellen, um Commerce-Profildatensatzdaten zu erfassen und an die Experience Platform zu senden.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 86a3ba12-7f26-4f7e-98a0-9af0d1d8d881
source-git-commit: 813be62b366b1c76a2b909079cfba31ef8000617
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung (Beta)

Wenn Ihre Kunden ein Profil auf Ihrer Commerce-Site erstellen, wird ein Profildatensatz erstellt und Daten erfasst. Sie müssen ein für diesen Profildatensatz spezifisches Schema und einen Datensatz erstellen, bevor Sie diese Profildaten an die Experience Platform streamen können.

1. [Erstellen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) ein Schema und legen Sie die Klasse auf **Individuelles Profil**.

1. [Hinzufügen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) die folgenden profilspezifischen Feldergruppen:

   - identityMap
   - Demografische Details
   - Persönliche Kontaktangaben
   - Details zum Benutzerkonto

1. [Aktivieren](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Datensatz erstellen](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

1. Erstellen Sie eine [benutzerdefinierter Namensraum](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) in Experience Platform mit den folgenden Werten ein:

   - **Anzeigename**: _Commerce-Kunden-ID_
   - **Identitätssymbol**: _CustomerId_
   - **Typ**: _Einzelne geräteübergreifende ID_

   ![Benutzerdefinierten Namespace erstellen](assets/custom-namespace.png){width="700" zoomable="yes"}

   Klicks **[!UICONTROL Create]**. Der Unified Profile Service verwendet einen benutzerdefinierten Namespace zum Zusammenfügen von Profilfragmenten.

Mit dem Schema, dem Datensatz und dem benutzerdefinierten Namensraum, der für Kundenprofildatensatzdaten konfiguriert ist, können Sie [konfigurieren](connect-data.md#data-collection) Ihre Commerce-Instanz, um diese Daten zu erfassen und an Experience Platform zu senden.

Informationen zum Erstellen eines Schemas, Datensatzes und Datastreams für Verhaltens- und Back-Office-Ereignisdaten finden Sie unter [Zeitreihenereignisschemas für die Commerce-Datenerfassung aktualisieren](update-xdm.md).
