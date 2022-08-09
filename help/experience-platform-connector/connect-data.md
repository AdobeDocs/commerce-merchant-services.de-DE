---
title: Commerce-Daten mit Adobe Experience Platform verbinden
description: Erfahren Sie, wie Sie Ihre Commerce-Daten mit der Adobe Experience Platform verbinden.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Commerce-Daten mit Adobe Experience Platform verbinden {#connectaep}

Bevor Sie Ihre Adobe Commerce-Daten mit der Adobe Experience Platform verbinden, müssen Sie sich bei Ihrem Adobe-Konto im [Commerce Services Connector](../landing/saas.md#organizationid). Nachdem Sie sich angemeldet haben und Ihre Organisations-ID ausgewählt haben, können Sie den Umfang und die Datastraam-ID auf der **Experience Platform Connector** in der Admin-Seite.

1. Navigieren Sie im Admin zu **System** > Dienste > **Experience Platform Connector**.

1. Im **Anwendungsbereich** in der Dropdown-Liste den Kontext oder den &quot;Umfang&quot;der Store-Ansicht auswählen.

   Die Organisations-ID ist global. Pro Adobe Commerce-Instanz kann nur eine Organisations-ID zugeordnet werden.

1. Im **IMS-Organisation** angezeigt, sehen Sie die Ihrem Adobe Experience Platform-Konto zugeordnete ID, wie in der [Commerce Services Connector](../landing/saas.md#organizationid).

1. Im **Datenspeicher-ID** -Feld die ID des von Ihnen verwendeten Datenstreams einfügen [created](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) in Adobe Experience Platform.

## Beziehung der Datastream-ID und der Storeübersicht Ihrer Commerce-Instanz

Die Datastream-ID ermöglicht die Ereignisweiterleitung von Adobe Experience Platform zu anderen Adobe-DX-Produkten und kann mit einem bestimmten Store in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft werden. Sie können auch mehrere Storeviews mit derselben Datastream-ID verknüpfen. Das hängt davon ab, was für Ihr Unternehmen am sinnvollsten ist.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anwendungsbereich | Bestimmter Store, auf den die Konfigurationseinstellungen angewendet werden sollen. |
| IMS-Organisation (Global) | ID, die zu der Organisation gehört, die das Adobe DX-Produkt erworben hat. Diese ID verknüpft Ihre Adobe Commerce-Instanz mit Adobe Experience Platform. |
| Datastream-ID (Storeview) | ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe-DX-Produkten ermöglicht. Diese ID kann mit einer bestimmten storeView-Instanz in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft werden. |

Nachdem die Experience Platform Connector-Erweiterung installiert, die Verknüpfung zwischen Adobe Commerce und Adobe Experience Platform erstellt und die angegebene Datastream-ID angegeben wurde, fließen die Commerce-Daten an den Adobe Experience Platform-Edge und an andere Adobe-DX-Produkte.

## Commerce-Daten am Rande

Wenn Commerce-Daten an den Adobe Experience Platform-Edge gesendet werden, können Sie Berichte wie die folgenden erstellen:

![Commerce-Daten in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce-Daten in Adobe Experience Manager_
