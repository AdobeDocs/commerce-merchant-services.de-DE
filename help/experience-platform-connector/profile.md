---
title: Hochladen von Kundenprofilen in Adobe Experience Platform
description: Erfahren Sie, wie Sie Kundenprofile in Adobe Experience Platform hochladen.
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Hochladen des Kundenprofils in Adobe Experience Platform

Adobe Commerce-Händler können Kundenprofildaten in hochladen. [Echtzeit-Kundenprofil](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), der Teil von Adobe Experience Platform ist. Mit dem Profil können Sie Ihre Kundendaten in einer einheitlichen Ansicht zusammenfassen und so eine umsetzbare und mit Zeitstempel versehene Übersicht über jede Kundeninteraktion bereitstellen.

>[!NOTE]
>
> Profildaten müssen eine E-Mail-Adresse enthalten, da auf diese Weise die Verknüpfung zwischen einem Käufer und seinen Storefront-Verhaltensdaten erstellt wird.

Nach dem Hochladen der Profile Ihres Käufers werden Ereignisdaten, die mit allen Interaktionen verknüpft sind, die Ihre Kunden auf Ihrer Site ausführen, über den Experience Platform-Connector an das Profil gesendet und mit diesem Kundenprofil verknüpft.

>[!NOTE]
>
> Die `createAccount` [storefront-Ereignis](events.md) erstellt nicht automatisch ein Kundenprofil im Profil. Dies ist aus Sicherheitsgründen eingeschränkt und ist beabsichtigt.

In diesem Thema erfahren Sie, wie Sie in Experience Platform Ihre Adobe Commerce-Kundenprofile in das Echtzeit-Kundenprofil hochladen.

1. Bestimmen Sie, wo Sie Ihre Kundendaten speichern. Bei einigen Händlern werden diese Daten in Adobe Commerce gespeichert und können [exportiert](https://docs.magento.com/user-guide/system/data-export.html) als CSV-Datei. Für andere kann es sich in einem separaten CRM-System (Customer Relationship Management) befinden.

1. Nachdem Sie ermittelt haben, wo Sie Ihre Kundendaten speichern, suchen Sie die passende [Quell-Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en) basierend darauf, wo Ihre Kundendaten gespeichert werden. Wenn kein entsprechender Quell-Connector angezeigt wird, verwenden Sie die [lokaler Datei-Upload](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) Kundenprofile aus einer CSV-Datei importieren.

   >[!NOTE]
   >
   > Wenn Sie den lokalen Datei-Upload-Connector verwenden, müssen Sie die **Profildatensatz** Option bei [Datensatz definieren](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). Dadurch wird der Datensatz als Profildaten identifiziert.

Nachdem Sie die Kundenprofile im Profil erstellt haben, werden alle mit diesem Kunden verbundenen Storefront-Daten mit seinem Profil verknüpft.

## Häufig Profile hochladen

Um ein verbessertes Kundenerlebnis zu gewährleisten, sollten Sie Profildaten regelmäßig importieren. Mit einigen Quell-Connectoren können Sie Profildaten planmäßig importieren.
