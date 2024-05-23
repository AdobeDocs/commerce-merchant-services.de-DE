---
title: Commerce Services Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe von Produktions- und Sandbox-API-Schlüsseln in Dienste integrieren.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 5d3a89b2ef06b2c67ec715ce4f31f22249b336e0
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Einige Adobe Commerce- und Magento Open Source-Funktionen basieren auf [!DNL Commerce Services] und als SaaS (Software as a Service) bereitgestellt werden. Um diese Dienste verwenden zu können, müssen Sie Ihre [!DNL Commerce] -Instanz mithilfe von Produktions- und Sandbox-API-Schlüsseln und geben Sie den Datenraum im [Konfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Sie müssen dies nur einmal einrichten.

## Verfügbare Dienste {#availableservices}

Im Folgenden werden die [!DNL Commerce] Funktionen, auf die Sie über [!DNL Commerce Services Connector]:

| Dienst | Verfügbarkeit |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) powered by Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) powered by Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce und Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce und Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architektur

Auf hoher Ebene wird die [!DNL Commerce Services Connector] besteht aus den folgenden Kernelementen:

![Connector-Architektur für Commerce Services](assets/saas-config-sync-workflow.png)

In den folgenden Abschnitten werden die einzelnen Elemente ausführlicher erläutert.

## Anmeldeinformationen {#apikey}

Die Produktions- und Sandbox-API-Schlüssel werden aus dem [!DNL Commerce] des [Lizenzinhaber](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding) die durch eine eindeutige [!DNL Commerce] ID (MageID). So übergeben Sie die Berechtigungsprüfung für Dienste wie [!DNL Product Recommendations] oder [!DNL Live Search]festgelegt ist, kann der Lizenzinhaber für die Organisation des Händlers den Satz von API-Schlüsseln generieren, solange das Konto gut aufgestellt ist. Die Schlüssel können auf der Grundlage des &quot;Bedarfs an Wissen&quot;an den Systemintegrator oder das Entwicklungsteam weitergegeben werden, der Projekte und Umgebungen im Auftrag des Lizenzinhabers verwaltet. Darüber hinaus sind Lösungsintegratoren auch berechtigt, [!DNL Commerce Services]. Wenn Sie ein Lösungsintegrator sind, ist der Unterzeichner der [!DNL Commerce] Der Partnervertrag sollte die API-Schlüssel generieren.

>[!NOTE]
>
>Der Lizenzinhaber ist in der Regel der Primäre Ansprechpartner für das Adobe Commerce-Konto und nicht immer derselbe wie der Projekteigentümer des Adobe Commerce-Projekts für Cloud-Infrastruktur.

### Generieren der Produktions- und Sandbox-API-Schlüssel {#genapikey}

1. Melden Sie sich bei Ihrer [!DNL Commerce] Konto unter [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Unter dem **Magento** Registerkarte auswählen **API-Portal** auf der Seitenleiste.

1. Aus dem _Umgebung_ Menü auswählen **Produktion** oder **Sandbox**.

1. Geben Sie im Feld _API-Schlüssel_ und klicken Sie auf **Neu hinzufügen**.

   Dadurch wird ein Dialogfeld zum Herunterladen des neuen Schlüssels geöffnet.

   ![Privaten Schlüssel herunterladen](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Dies ist die einzige Möglichkeit, dass Sie Ihre Schlüssel kopieren oder herunterladen müssen.

1. Klicks **Herunterladen** Klicken Sie dann auf **Abbrechen**.

1. Wiederholen Sie die obigen Schritte für jede Umgebung (Produktion und Sandbox).

   Die **API-Schlüssel** -Abschnitt zeigt nun Ihre API-Schlüssel (Öffentlich) an. Sie benötigen sowohl die Produktions- als auch die Sandbox-Schlüssel (öffentlich+privat), wenn Sie [Auswählen oder Erstellen eines SaaS-Projekts](#createsaasenv).

## SaaS-Konfiguration {#saasenv}

[!DNL Commerce] -Instanzen müssen mit einem SaaS-Projekt und einem SaaS-Datenraum konfiguriert werden, damit [!DNL Commerce Services] kann Daten an den richtigen Ort senden. Ein SaaS-Projekt gruppiert alle SaaS-Datenräume. Die SaaS-Datenräume werden verwendet, um Daten zu erfassen und zu speichern, die [!DNL Commerce Services] zu arbeiten. Einige dieser Daten können aus dem [!DNL Commerce] -Instanz und einige werden möglicherweise aus dem Kaufverhalten auf der Storefront erfasst. Diese Daten werden dann beibehalten, um den Cloud-Speicher zu sichern.

Für [!DNL Product Recommendations], enthält der SaaS-Datenraum Katalog- und Verhaltensdaten. Sie können einen Punkt [!DNL Commerce] -Instanz in einen SaaS-Datenraum von [auswählen](https://docs.magento.com/user-guide/configuration/services/saas.html) im [!DNL Commerce] Konfiguration.

>[!WARNING]
>
> Verwenden Sie Ihren Produktions-SaaS-Datenraum nur in Ihrer Produktion. [!DNL Commerce] Installation, um Datenkollisionen zu vermeiden. Andernfalls riskieren Sie, Ihre Produktionsstandortdaten mit Testdaten zu verschmutzen, was zu Bereitstellungsverzögerungen führt. Beispielsweise können Ihre Produktionsproduktdaten fälschlicherweise aus Staging-Daten wie Staging-URLs überschrieben werden.

### Auswählen oder Erstellen eines SaaS-Projekts {#createsaasenv}

Um ein SaaS-Projekt auszuwählen oder zu erstellen, fordern Sie die [!DNL Commerce] API-Schlüssel aus der [!DNL Commerce] Lizenzinhaber für Ihr Geschäft.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **System** > Dienste > **Commerce Services Connector**.

   Wenn die Variable **[!UICONTROL Commerce Services Connector]** im Abschnitt [!DNL Commerce] -Konfiguration, installieren Sie die [!DNL Commerce] Module für Ihre gewünschten [[!DNL Commerce] service](#availableservices). Stellen Sie außerdem sicher, dass die Variable `magento/module-services-id` installiert ist.

1. Im _Sandbox-API-Schlüssel_ und _Schlüssel der Produktions-API_ -Abschnitte, fügen Sie Ihre Schlüsselwerte ein.

   Private Schlüssel müssen enthalten sein `----BEGIN PRIVATE KEY---` am Anfang des Schlüssels und `----END PRIVATE KEY----` am Ende des privaten Schlüssels.

1. Klicks **Speichern**.

Sämtliche SaaS-Projekte, die mit Ihren Schlüsseln verknüpft sind, werden im **Projekt** im Feld **SaaS-Kennung** Abschnitt.

1. Wenn keine SaaS-Projekte vorhanden sind, klicken Sie auf **Projekt erstellen**. Dann in der **Projekt** ein, geben Sie einen Namen für Ihr SaaS-Projekt ein.

   Wenn Sie ein SaaS-Projekt erstellen, [!DNL Commerce] generiert je nach Ihrer [!DNL Commerce] -Lizenz:
   - Adobe Commerce - Ein Produktionsdatenraum; zwei Testdatenbereiche
   - Magento Open Source - Ein Produktionsdatenraum; keine Testdatenbereiche

1. Wählen Sie die **Datenraum** zur Verwendung für die aktuelle Konfiguration Ihrer [!DNL Commerce] speichern.

>[!WARNING]
>
> Wenn Sie im Abschnitt &quot;Mein Konto&quot;im API-Portal neue Schlüssel generieren, aktualisieren Sie sofort die API-Schlüssel in der Admin-Konfiguration. Wenn Sie neue Schlüssel generieren und diese nicht im Admin aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Um die Namen Ihres SaaS-Projekts oder Ihres Datenraums zu ändern, klicken Sie auf **Umbenennen** neben einer der beiden. Das Ändern des Namens wirkt sich nicht auf Ihren Dienst aus, da der Name nur eine Bezeichnung ist, mit der Sie Projekte und Datenräume identifizieren und unterscheiden können.

## IMS-Organisation (optional) {#organizationid}

Um Ihre Adobe Commerce-Instanz mit Adobe Experience Platform zu verbinden, melden Sie sich mit Ihrem Adobe-Konto bei Ihrem Adobe ID an. Nach der Anmeldung wird die mit Ihrem Adobe-Konto verknüpfte IMS-Organisation in diesem Abschnitt angezeigt.

## Katalogsynchronisierung

Wenn [!DNL Commerce] -Instanz stellt erfolgreich eine Verbindung zu [!DNL Commerce Services], exportiert der Prozess der Katalogsynchronisierung Produktdaten aus Ihrer [!DNL Commerce] Server zu [!DNL Commerce Services]. Derzeit verwendet nur Product Recommendations den Dienst für die Katalogsynchronisierung. [Weitere Infos](catalog-sync.md) Informationen zur Katalogsynchronisierung.
