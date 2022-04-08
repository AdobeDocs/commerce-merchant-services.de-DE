---
title: Commerce Services Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels in Dienste integrieren können.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: ae63fed82ee68f70a107b9c0a631d223990d50e1
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Some Adobe Commerce and Magento Open Source features are powered by [!DNL Commerce Services]  and deployed as SaaS (software as a service). Um diese Dienste verwenden zu können, müssen Sie Ihre [!DNL Commerce] -Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels und geben Sie den Datenraum im [Konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html). Sie müssen dies nur einmal einrichten.

## Available services

The following lists the [!DNL Commerce] features you can access through the [!DNL Commerce Services Connector]:

| Diensleistung | Verfügbarkeit |
| ---|--- |
| [!DNL Product Recommendations] powered by Adobe Sensei | Adobe Commerce |
| [!DNL Live Search] powered by Adobe Sensei | Adobe Commerce |
| [!DNL Payment Services] | Adobe Commerce und Magento Open Source |

## Architektur

Auf hoher Ebene wird die [!DNL Commerce Services Connector] besteht aus folgenden Kernelementen:

![Connector-Architektur für Commerce Services](assets/saas-config-sync-workflow.png)

In den folgenden Abschnitten werden die einzelnen Elemente ausführlicher erläutert.

## Anmeldeinformationen {#apikey}

The API key and private key are generated from the [!DNL Commerce] account of the license holder, which is identified by a unique [!DNL Commerce] ID (MageID). So übergeben Sie die Berechtigungsprüfung für Dienste wie [!DNL Product Recommendations] oder [!DNL Live Search]festgelegt ist, kann der Lizenzinhaber der Händlerorganisation den Satz von API-Schlüsseln generieren, solange das Konto gut aufgestellt ist. The keys can be shared on a &quot;need to know&quot; basis with the systems integrator or development team that manages projects and environments on behalf of the license holder. Additionally, solution integrators are also entitled to use [!DNL Commerce Services]. If you are a solution integrator, the signer of the [!DNL Commerce] partner contract should generate the API keys.

### API-Schlüssel und privaten Schlüssel generieren {#genapikey}

1. Melden Sie sich bei Ihrer [!DNL Commerce] Konto unter [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Unter dem **Magento** Registerkarte, wählen Sie **API-Portal** auf der Seitenleiste.

1. Aus dem _Umgebung_ Menü auswählen **Produktion** oder **Sandbox**.

   >[!NOTE]
   >
   > For [!DNL _Product Recommendations_] and [!DNL _Live Search_], select **Production**. Produktionsschlüssel bieten Zugriff auf Produktions- und Nicht-Produktionsdatenbereiche. Sandbox-Schlüssel werden für diese Dienste nicht verwendet.

1. Enter a name in the _API Keys_ section and click **Add New**.

   Dadurch wird ein Dialogfeld zum Herunterladen des neuen Schlüssels geöffnet.

   ![Privaten Schlüssel herunterladen](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Dies ist die einzige Möglichkeit, dass Sie Ihren Schlüssel kopieren oder herunterladen müssen.

1. Klicken **Download** Klicken Sie dann auf **Abbrechen**.

   Die **API-Schlüssel** -Abschnitt zeigt nun Ihren API-Schlüssel an. Sie benötigen sowohl den API-Schlüssel als auch den privaten Schlüssel, wenn Sie [Auswählen oder Erstellen eines SaaS-Projekts](#createsaasenv).

## SaaS-Konfiguration {#saasenv}

[!DNL Commerce] -Instanzen müssen mit einem SaaS-Projekt und einem SaaS-Datenraum konfiguriert werden, damit [!DNL Commerce Services] kann Daten an den richtigen Ort senden. Ein SaaS-Projekt gruppiert alle SaaS-Datenräume. Die SaaS-Datenräume werden verwendet, um Daten zu erfassen und zu speichern, die [!DNL Commerce Services] arbeiten. Einige dieser Daten können aus dem [!DNL Commerce] -Instanz und einige werden möglicherweise aus dem Kaufverhalten auf der Storefront erfasst. Diese Daten werden dann beibehalten, um den Cloud-Speicher zu sichern.

Für [!DNL Product Recommendations], enthält der SaaS-Datenraum Katalog- und Verhaltensdaten. Sie können einen Punkt [!DNL Commerce] -Instanz in einen SaaS-Datenraum von [auswählen](https://docs.magento.com/user-guide/configuration/services/saas.html) im [!DNL Commerce] Konfiguration.

>[!WARNING]
>
> Verwenden Sie Ihren Produktions-SaaS-Datenraum nur in Ihrer Produktion. [!DNL Commerce] Installation, um Datenkollisionen zu vermeiden. Andernfalls riskieren Sie, Ihre Produktionsstandortdaten mit Testdaten zu verschmutzen, was zu Bereitstellungsverzögerungen führt. Beispielsweise können Ihre Produktionsproduktdaten fälschlicherweise aus Staging-Daten wie Staging-URLs überschrieben werden.

### Auswählen oder Erstellen eines SaaS-Projekts {#createsaasenv}

>[!NOTE]
>
> Wenn die Variable **Commerce Services Connector** im Abschnitt [!DNL Commerce] -Konfiguration, müssen Sie die [!DNL Commerce] Module für Ihre gewünschten [!DNL Commerce Service], z. B. [!DNL Product Recommendations].

Um ein SaaS-Projekt auszuwählen oder zu erstellen, fordern Sie die [!DNL Commerce] API-Schlüssel aus der [!DNL Commerce] Lizenzinhaber für Ihr Geschäft.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > _Einstellungen_ > **Konfiguration**.

1. Erweitern Sie im linken Bereich **Dienste** und wählen Sie **Commerce Services Connector**.

1. Im _API-Schlüssel_ Fügen Sie Ihre Schlüsselwerte für die **Produktions-API-Schlüssel** und **Privater Produktionsschlüssel**.

   Private Schlüssel müssen enthalten sein `----BEGIN PRIVATE KEY---` am Anfang des Schlüssels und `----END PRIVATE KEY----` am Ende des privaten Schlüssels.

1. Klicken **Konfiguration speichern**.

Sämtliche SaaS-Projekte, die mit Ihrem API-Schlüssel verknüpft sind, werden im **SaaS-Projekt** -Feld.

1. Wenn keine SaaS-Projekte vorhanden sind, klicken Sie auf **Projekt erstellen**. Dann in der **Projektname** ein, geben Sie einen Namen für Ihr SaaS-Projekt ein.

   Wenn Sie ein SaaS-Projekt erstellen, [!DNL Commerce] generiert je nach Ihrer [!DNL Commerce] -Lizenz:
   - Adobe Commerce - Ein Produktionsdatenraum; zwei Testdatenbereiche
   - Magento Open Source - Ein Produktionsdatenraum; keine Testdatenräume

1. Wählen Sie die **SaaS-Datenraum** zur Verwendung für die aktuelle Konfiguration Ihrer [!DNL Commerce] speichern.

>[!WARNING]
>
> Wenn Sie im Abschnitt &quot;Mein Konto&quot;im API-Portal neue Schlüssel generieren, aktualisieren Sie sofort die API-Schlüssel in der Admin-Konfiguration. Wenn Sie neue Schlüssel generieren und diese nicht im Admin aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Um die Namen des SaaS-Projekts oder der Datenspeicherorte zu ändern, klicken Sie auf das **Dieses Projekt umbenennen** oder **Umbenennen des Datenspeichers** bzw.

## Katalogsynchronisierung

When your [!DNL Commerce] instance successfully connects to [!DNL Commerce Services], the catalog sync process exports product data from your [!DNL Commerce] server to [!DNL Commerce Services]. [Learn more](catalog-sync.md) about the catalog sync process.
