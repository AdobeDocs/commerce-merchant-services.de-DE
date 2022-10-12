---
title: Commerce-Daten mit Adobe Experience Platform verbinden
description: Erfahren Sie, wie Sie Ihre Commerce-Daten mit der Adobe Experience Platform verbinden.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Commerce-Daten mit Adobe Experience Platform verbinden {#connectaep}

Um Ihre Adobe Commerce-Instanz mit der Adobe Experience Platform zu verbinden, müssen Sie eine Organisations-ID und eine Datastraam-ID angeben.

![Experience Platform-Connector-Konfiguration](assets/epc-config.png)

1. Melden Sie sich bei Ihrem Adobe-Konto im [Commerce Services Connector](../landing/saas.md#organizationid) und wählen Sie Ihre Organisations-ID aus.

1. Navigieren Sie im Admin zu **System** > Dienste > **Experience Platform Connector**.

1. Im **Anwendungsbereich** in der Dropdown-Liste festlegen, setzen Sie den Kontext auf **Webseite**.

1. Im **Organisations-ID** angezeigt, sehen Sie die Ihrem Adobe Experience Platform-Konto zugeordnete ID, wie in der [Commerce Services Connector](../landing/saas.md#organizationid). Die Organisations-ID ist global. Pro Adobe Commerce-Instanz kann nur eine Organisations-ID zugeordnet werden.

1. Im **Datenspeicher-ID** -Feld die ID des von Ihnen verwendeten Datastreams einfügen [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) in der Adobe Experience Platform.

   >[!NOTE]
   >
   >Der Umfang der Datastream-ID muss auf Website-Ebene oder höher festgelegt werden. Auf dieser Ebene wird für jede Website in der Hierarchie dieselbe Datastream-ID verwendet. Sie können den Datensatz-ID-Umfang nicht auf der Storeüberprüfungsebene festlegen.

1. (Optional) Wenn auf Ihrer Site kein AEP Web SDK bereitgestellt ist, lassen Sie dieses Feld leer, und der Experience Platform Connector stellt eines für Sie bereit. Fügen Sie andernfalls den Namen Ihres AEP Web SDK hinzu.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anwendungsbereich | Bestimmte Website, auf die die Konfigurationseinstellungen angewendet werden sollen. |
| Organisations-ID (global) | ID, die zu der Organisation gehört, die das Adobe DX-Produkt erworben hat. Diese ID verknüpft Ihre Adobe Commerce-Instanz mit Adobe Experience Platform. |
| Datastream-ID (Website) | ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe-DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft sein. |
| AEP Web SDK Name (Global) | Wenn auf Ihrer Site kein AEP Web SDK bereitgestellt ist, lassen Sie dieses Feld leer, und der Experience Platform Connector stellt eines für Sie bereit. Wenn Sie bereits ein AEP Web SDK auf Ihrer Site bereitgestellt haben, geben Sie den Namen dieses SDK in dieses Feld ein. Dadurch kann der Storefront Event Collector und das Storefront Event SDK Ihr AEP Web SDK anstelle der vom Experience Platform Connector bereitgestellten Version verwenden. |

Nachdem die Experience Platform Connector-Erweiterung installiert, die Verknüpfung zwischen Adobe Commerce und Adobe Experience Platform erstellt und die angegebene Datastream-ID angegeben wurde, fließen die Commerce-Daten an den Adobe Experience Platform-Edge und an andere Adobe-DX-Produkte.

>[!NOTE]
>
> Die Zeit, die benötigt wird, um Daten vom Edge zu anderen Adobe DX-Produkten zu übertragen, kann variieren.

## Commerce-Daten am Rande

Wenn Commerce-Daten an den Adobe Experience Platform-Edge gesendet werden, können Sie Berichte wie die folgenden erstellen:

![Commerce-Daten in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce-Daten in Adobe Experience Manager_
