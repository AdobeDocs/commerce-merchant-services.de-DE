---
title: Guide Overview
description: Adobe Experience Platform-Connector für Adobe Commerce verbindet Ihre [!DNL Commerce] -Instanz auf andere Adobe Experience Cloud-Produkte umzustellen.
source-git-commit: dc4bb1ea7d2ffc953cca31637bf5aefba6266241
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Übersicht über den Experience Platform Connector

Mit der Experience Platform Connector-Erweiterung können Adobe Commerce-Händler Daten an den Adobe Experience Platform-Edge senden, damit andere Adobe Experience Cloud-Produkte wie Adobe Analytics und Adobe Target diese verwenden können [!DNL Commerce] Daten. Indem Sie [!DNL Commerce] Daten an andere Produkte in der Adobe Experience Cloud weiterleiten, können Sie Aufgaben ausführen, z. B. das Benutzerverhalten auf Ihrer Site analysieren, AB-Tests durchführen und personalisierte Kampagnen erstellen.

Storefront-Ereignisse erfassen Kundeninteraktionen wie `View Page`, `View Product`, `Add to Cart`usw. Die erfassten Daten enthalten keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html). Die vollständige Liste der [Storefront-Ereignisse](events.md).

## Voraussetzungen für die Verwendung des Experience Platform Connectors {#prereqs}

Um den Experience Platform-Connector zu verwenden, müssen Sie zunächst:

- Füllen Sie Folgendes aus [Formular](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) und Adobe bietet Ihnen Zugriff auf Datenspeicher und die Adobe Experience Platform (falls erforderlich).

Wenn der Zugriff gewährt wird:

1. [Anmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) auf Ihr Adobe-Konto.
1. Sehen Sie sich Ihre [Organisation](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge, gefolgt von @AdobeOrg (erforderlich).
1. Zugriff auf den Arbeitsbereich &quot;Datastream&quot;und [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en).

Die Organisations-ID und der Datastream werden verwendet, wenn Sie Ihre Adobe Commerce-Instanz mit der Adobe Experience Platform verbinden.

## Nächste Schritte

- Installieren Sie die [Experience Platform Connector-Erweiterung](install.md).

   Die Experience Platform Connector-Erweiterung wird über die Befehlszeile des Servers installiert und stellt eine Verbindung zu Ihrer Adobe Commerce-Installation als [service](../landing/saas.md). Wenn der Vorgang abgeschlossen ist, wird der Experience Platform-Connector auf der **System** Menü unter **Dienste** im [!DNL Commerce] _Admin_.

## Zielgruppe

Dieses Handbuch richtet sich an Adobe Commerce-Händler, die ihre Adobe Commerce-Storefront-Daten mit anderen Adobe DX-Produkten verbinden müssen.

## Bekannte Probleme

Derzeit weist der Experience Platform-Connector die folgenden bekannten Probleme auf:

- Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn das B2B-Modul installiert ist.
- Nach der Verbindung mit dem Adobe Experience Platform Edge dauert es etwa eine Stunde, bis die Storefront-Daten von Adobe Commerce zu den verschiedenen Zielen gelangen.

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden, können Sie Beiträge an den folgenden Slack-Kanal senden:

- `#beacon-ama`
