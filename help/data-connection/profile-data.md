---
title: Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung
description: Erfahren Sie, wie Sie ein Schema, einen Datensatz und einen Datenspeicher erstellen, um Commerce-Profildatensätze zu erfassen und an die Experience Platform zu senden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Aktualisieren des Profildatensatzschemas für die Commerce-Datenerfassung

Wenn Ihre Kunden ein Profil auf Ihrer Commerce-Site erstellen, wird ein Profildatensatz erstellt und Daten erfasst. Sie müssen ein für diesen Profildatensatz spezifisches Schema und einen Datensatz erstellen, bevor Sie diese Profildaten an die Experience Platform streamen können.

1. [Erstellen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) ein Schema und legen Sie die Klasse auf **Individuelles Profil**.

1. [Hinzufügen](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) die folgenden profilspezifischen Feldergruppen:

   - identityMap
   - Demografische Details
   - Persönliche Kontaktangaben
   - Details zum Benutzerkonto

1. [Aktivieren](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) das Schema für Profil.

   Wenn ein Schema für Profile aktiviert ist, nehmen alle Datensätze, die aus diesem Schema erstellt wurden, an Real-Time CDP teil, wo Daten aus unterschiedlichen Quellen zusammengeführt werden, um eine vollständige Ansicht der einzelnen Kunden zu erstellen.

1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema.

   Ein Datensatz ist ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben.

Wenn das Schema und der Datensatz für Kundenprofildatensätze konfiguriert sind, können Sie [konfigurieren](connect-data.md#data-collection) Ihre Commerce-Instanz, um diese Daten zu erfassen und an Experience Platform zu senden.

Informationen zum Erstellen eines Schemas, Datensatzes und Datastreams für Verhaltens- und Back-Office-Ereignisdaten finden Sie unter [Zeitreihenereignisschemas für die Commerce-Datenerfassung aktualisieren](update-xdm.md).
