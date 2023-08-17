---
title: Handbuch-Übersicht
description: Erfahren Sie, wie Sie Adobe Commerce-Daten mithilfe des Experience Platform-Connectors in Adobe Experience Platform integrieren.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Übersicht über den Experience Platform-Connector

Die Experience Platform-Connector-Erweiterung ermöglicht es Adobe Commerce-Händlern, [storefront](events.md#storefront-events) und [Backoffice](events.md#back-office-events) -Daten an den Adobe Experience Platform-Edge übermittelt, sodass andere Adobe Experience Cloud-Produkte wie Adobe Analytics und Adobe Target diese Commerce-Daten verwenden können. Durch die Verbindung Ihrer Commerce-Daten mit anderen Produkten in der Adobe Experience Cloud können Sie Aufgaben ausführen, z. B. das Benutzerverhalten auf Ihrer Site analysieren, AB-Tests durchführen und personalisierte Kampagnen erstellen.

[Storefront-Ereignisse](events.md#storefront-events) Erfassen von Kundeninteraktionen, z. B. `View Page`, `View Product`, `Add to Cart`, und [Anforderungsliste](events.md#b2b-events) Informationen (für B2B-Händler). [Back Office](events.md#back-office-events) -Ereignisse erfassen Informationen zum Status einer Bestellung, z. B. wenn eine Bestellung aufgegeben, storniert, rückerstattet, versandt oder abgeschlossen wurde. Die erfassten Daten enthalten keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html).

Der Experience Platform-Connector wird in Commerce Admin unter **System** > Dienste > **Experience Platform-Connector**.

![Admin-Ansicht der Experience Platform-Connector-Erweiterung](assets/epc-adminui.png)

## Voraussetzungen {#prereqs}

Um den Experience Platform-Connector zu verwenden, müssen Sie über Folgendes verfügen:

- Adobe Commerce 2.4.3 oder höher
- Adobe ID- und Organisations-ID
- [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ACDL ist erforderlich, um Storefront-Ereignisdaten zu erfassen.
- Berechtigungen für andere Adobe DX-Produkte

## Onboarding-Schritte

1. [Installieren](install.md) die Experience Platform-Connector-Erweiterung.
1. [Anmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) auf Ihr Adobe-Konto und [Bestätigung anzeigen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) Ihre Organisations-ID. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von (und muss enthalten) `@AdobeOrg`.
1. [Erstellen oder aktualisieren](update-xdm.md) Ihr XDM-Schema mit Commerce-spezifischen Feldergruppen.
1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die von Ihnen gesendeten Commerce-Daten.
1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. [Verbindung zu Commerce Services herstellen](../landing/saas.md).
1. [Verbindung zu Adobe Experience Platform herstellen](connect-data.md).

## Zielgruppe

Dieses Handbuch richtet sich an Adobe Commerce-Händler, die ihre Adobe Commerce-Daten mit anderen Adobe DX-Produkten verbinden möchten.

### PWA Studio-Support

Siehe [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) Dokumentation für Informationen zur Verwendung des Experience Platform-Connectors in einer PWA Studio-Storefront.

### AEM {#aem-support}

Siehe [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) Dokumentation , um zu erfahren, wie Sie mit dem CIF - Experience Platform Connector Storefront-Ereignisdaten von einer AEM gerenderten Produktseite an die Experience Platform senden.

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

- [Hilfezentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
