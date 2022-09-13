---
title: Guide Overview
description: Erfahren Sie, wie Sie Adobe Commerce-Daten mithilfe des Experience Platform-Connectors in Adobe Experience Platform integrieren.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Übersicht über den Experience Platform Connector

Mit der Experience Platform Connector-Erweiterung können Adobe Commerce-Händler Daten an den Adobe Experience Platform-Edge senden, damit andere Adobe Experience Cloud-Produkte wie Adobe Analytics und Adobe Target diese Commerce-Daten verwenden können. Durch die Verbindung Ihrer Commerce-Daten mit anderen Produkten in der Adobe Experience Cloud können Sie Aufgaben ausführen, z. B. das Benutzerverhalten auf Ihrer Site analysieren, AB-Tests durchführen und personalisierte Kampagnen erstellen.

[Storefront-Ereignisse](events.md) Erfassen von Kundeninteraktionen, z. B. `View Page`, `View Product`, `Add to Cart`usw. Die erfassten Daten enthalten keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html).

Der Experience Platform-Connector wird in der Commerce-Admin unter **System** > Dienste > **Experience Platform Connector**.

![Admin-Ansicht der Experience Platform Connector-Erweiterung](assets/epc-adminui.png)

## Voraussetzungen {#prereqs}

Um den Experience Platform-Connector verwenden zu können, benötigen Sie Folgendes:

- Adobe Commerce 2.4.3 oder höher
- Adobe ID- und Organisations-ID
- Berechtigungen für andere Adobe DX-Produkte

## Onboarding-Schritte

1. [Installieren](install.md) die Experience Platform Connector-Erweiterung.
1. [Anmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) auf Ihr Adobe-Konto und [Ansicht](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) Ihre Organisations-ID. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von (und muss enthalten) `@AdobeOrg`.
1. [Verbinden](connect-data.md) Ihre Adobe Commerce-Instanz in der Adobe Experience Platform.
1. [Erstellen oder aktualisieren](update-xdm.md) Ihr XDM-Schema mit Commerce-spezifischen Feldergruppen.
1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. (Optional) [Hochladen von Kundenprofilen](profile.md) Adobe Experience Platform zugeordnet werden, sodass Storefront-Daten bestimmten Käufern zugeordnet werden können, um deren Einkaufserlebnis zu verbessern.

## Zielgruppe

Dieses Handbuch richtet sich an Adobe Commerce-Händler, die ihre Adobe Commerce-Storefront-Daten mit anderen Adobe DX-Produkten verbinden möchten.

### PWA Studio-Support

Siehe [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) Dokumentation für Informationen zur Verwendung des Experience Platform Connectors in einer PWA Studio-Storefront.

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

- [Hilfezentrum](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [Support-Tickets](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;}: Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
