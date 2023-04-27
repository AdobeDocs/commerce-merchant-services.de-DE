---
title: Commerce-Daten mit Adobe Experience Platform verbinden
description: Erfahren Sie, wie Sie Ihre Commerce-Daten mit der Adobe Experience Platform verbinden.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Commerce-Daten mit Adobe Experience Platform verbinden

Wenn Sie den Experience Platform Connector installieren, werden im **System** Menü unter **Dienste** im Handel _Admin_.

- Commerce Services Connector
- Experience Platform Connector

Um Ihre Adobe Commerce-Instanz mit der Adobe Experience Platform zu verbinden, müssen Sie beide Connectoren konfigurieren, beginnend mit dem Commerce Services-Connector und schließlich mit dem Experience Platform-Connector.

## Connector für Commerce Services aktualisieren

Wenn Sie zuvor einen Adobe Commerce-Dienst installiert haben, haben Sie wahrscheinlich bereits den Commerce Services-Connector konfiguriert. Andernfalls müssen Sie die folgenden Aufgaben für die [Commerce Services-Connector](../landing/saas.md) Seite:

1. Melden Sie sich bei Ihrem Commerce-Konto bei [Produktions- und Sandbox-API-Schlüssel abrufen](../landing/saas.md#credentials).
1. Wählen Sie eine [SaaS-Datenraum](../landing/saas.md#saas-configuration).
1. Melden Sie sich bei Ihrem Adobe-Konto bei [Organisations-ID abrufen](../landing/saas.md#ims-organization-optional).

Nachdem Sie den Commerce Services-Connector konfiguriert haben, konfigurieren Sie den Experience Platform-Connector.

## Experience Platform Connector aktualisieren

In diesem Abschnitt verbinden Sie Ihre Adobe Commerce-Instanz mit der Adobe Experience Platform mithilfe Ihrer Organisations-ID. Anschließend können Sie den Datentyp - Storefront oder Backoffice - angeben, der an den Experience Platform Edge gesendet werden soll.

![Experience Platform-Connector-Konfiguration](assets/epc-config-dc.png)

## Allgemein

1. Melden Sie sich bei Ihrem Adobe-Konto im [Commerce Services Connector](../landing/saas.md#organizationid) und wählen Sie Ihre Organisations-ID aus.

   >[!NOTE]
   >
   >Wenn Sie den Commerce Services-Connector zuvor konfiguriert haben, können Sie diesen Schritt überspringen, da Ihre Organisations-ID bereits ausgewählt wurde.

1. Navigieren Sie im Admin zu **System** > Dienste > **Experience Platform Connector**.

1. Im **Anwendungsbereich** in der Dropdown-Liste festlegen, setzen Sie den Kontext auf **Webseite**.

1. Im **Organisations-ID** überprüfen Sie die Ihrem Adobe Experience Platform-Konto zugeordnete ID, wie in der [Commerce Services Connector](../landing/saas.md#organizationid). Die Organisations-ID ist global. Pro Adobe Commerce-Instanz kann nur eine Organisations-ID zugeordnet werden.

1. (Optional) Wenn Sie bereits über eine [AEP Web SDK (Legierung)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) auf Ihrer Site bereitgestellt, aktivieren Sie das Kontrollkästchen und fügen Sie den Namen Ihres AEP Web SDK hinzu. Lassen Sie diese Felder andernfalls leer, und der Experience Platform Connector stellt eines für Sie bereit.

   >[!NOTE]
   >
   >Wenn Sie Ihr eigenes AEP Web SDK angeben, verwendet der Experience Platform Connector die mit diesem SDK verknüpfte Datastraam-ID und nicht die auf dieser Seite angegebene Datastream-ID (falls vorhanden).

## Datenerfassung

Im **Datenerfassung** Wählen Sie Storefront- und/oder Back-Office-Daten aus, die an den Experience Platform Edge gesendet werden sollen. Um sicherzustellen, dass Ihre Adobe Commerce-Instanz mit der Datenerfassung beginnen kann, lesen Sie das [Voraussetzungen](overview.md#prerequisites).

Weitere Informationen finden Sie unter Ereignisthema . [storefront](events.md#storefront-events) und [Backoffice](events.md#back-office-events) -Ereignisse.

>[!NOTE]
>
>Alle Felder im **Datenerfassung** -Abschnitt auf die **Webseite** oder höher.

1. Auswählen **Storefront-Ereignisse** , wenn Sie Verhaltensdaten zur Storefront senden möchten.

   >[!NOTE]
   >
   >Die **Storefront-Ereignisse** wird automatisch aktiviert, wenn das AEP Web SDK und die Organisations-ID gültig sind.

1. Auswählen **Backoffice-Ereignisse** wenn Sie Bestellstatusinformationen senden möchten, z. B. wenn eine Bestellung aufgegeben, storniert, rückerstattet oder versandt wurde.

   >[!NOTE]
   >
   >Wenn Sie **Backoffice-Ereignisse**, werden alle Backoffice-Daten an den Experience Platform Edge gesendet. Wenn sich ein Kunde dafür entscheidet, die Datenerfassung abzuwählen, müssen Sie in der Experience Platform ausdrücklich die Datenschutzeinstellung des Käufers festlegen. Dies unterscheidet sich von Storefront-Ereignissen, bei denen der Sammler die Zustimmung bereits auf der Grundlage der Kundeneinstellungen verarbeitet. [Weitere Infos](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) über die Festlegung der Datenschutzeinstellungen eines Käufers in der Experience Platform.

1. So stellen Sie sicher, dass Back-Office-Ereignisdaten anhand eines Zeitplans gemäß [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) Auftrag, müssen Sie die `Sales Orders Feed` Index zu `Update by Schedule`.

   1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Aktivieren Sie das Kontrollkästchen für die `Sales Orders Feed` Indexer.

   1. Satz **[!UICONTROL Actions]** nach `Update by Schedule`.

   1. Wenn Sie zum ersten Mal Backoffice-Daten aktivieren, führen Sie die folgenden Befehle aus, um eine Neusynchronisierung neu zu indizieren und Trigger. Nachfolgende Neusynchronisierungen treten automatisch auf, solange die Variable [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) Auftrag ordnungsgemäß eingerichtet ist.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (Überspringen Sie diesen Schritt, wenn Sie Ihr eigenes AEP Web SDK verwenden.) [Erstellen](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) einen Datastream in der Adobe Experience Platform oder wählen Sie einen vorhandenen Datastream aus, den Sie für die Erfassung verwenden möchten.

1. (Überspringen Sie diesen Schritt, wenn Sie Ihr eigenes AEP Web SDK verwenden.) Im **Datenspeicher-ID** -Feld die Kennung dieses neuen oder vorhandenen Datastreams ein.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anwendungsbereich | Bestimmte Website, auf die die Konfigurationseinstellungen angewendet werden sollen. |
| Organisations-ID (global) | ID, die zu der Organisation gehört, die das Adobe DX-Produkt erworben hat. Diese ID verknüpft Ihre Adobe Commerce-Instanz mit Adobe Experience Platform. |
| Ist das AEP Web SDK bereits auf Ihrer Site bereitgestellt? | Aktivieren Sie dieses Kontrollkästchen, wenn Sie Ihr eigenes AEP Web SDK auf Ihrer Site bereitgestellt haben. |
| AEP Web SDK Name (Global) | Wenn Sie bereits ein Experience Platform Web SDK auf Ihrer Site bereitgestellt haben, geben Sie in diesem Feld den Namen dieses SDK an. Dadurch kann das Storefront Event Collector und Storefront Event SDK Ihr Experience Platform Web SDK anstelle der vom Experience Platform Connector bereitgestellten Version verwenden. Wenn auf Ihrer Site kein Experience Platform Web SDK bereitgestellt ist, lassen Sie dieses Feld leer, und der Experience Platform Connector stellt eines für Sie bereit. |
| Storefront-Ereignisse | Ist standardmäßig aktiviert, solange die Organisations-ID und die Datastream-ID gültig sind. Storefront-Ereignisse erfassen anonymisierte Verhaltensdaten von Ihren Käufern beim Durchsuchen Ihrer Site. |
| Back Office-Ereignisse | Wenn diese Option aktiviert ist, enthält die Ereignis-Payload anonymisierte Bestellstatusinformationen, z. B. ob eine Bestellung aufgegeben, storniert, zurückerstattet oder versandt wurde. |
| Datastream-ID (Website) | ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe-DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft sein. Wenn Sie Ihr eigenes Experience Platform Web SDK angeben, geben Sie in diesem Feld keine Datastream-ID an. Der Experience Platform-Connector verwendet die mit diesem SDK verknüpfte Datastream-ID und ignoriert alle in diesem Feld angegebenen Datastream-IDs (falls vorhanden). |

## Überprüfen, ob Daten an Experience Platform gesendet werden

Nach dem Onboarding fließen die Storefront-Daten an den Edge der Experience Platform. Nach dem Onboarding dauert es etwa 5 Minuten, bis die Daten an der Kante angezeigt werden. Nachfolgende Aktualisierungen sind am Rand basierend auf dem Cron-Zeitplan sichtbar.

Wenn Commerce-Daten an den Experience Platform Edge gesendet werden, können Sie Berichte wie die folgenden erstellen:

![Commerce-Daten in Adobe Experience Platform](assets/aem-data-1.png)
_Commerce-Daten in Adobe Experience Platform_
