---
title: Commerce Services Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels in Dienste integrieren können.
source-git-commit: 8789bd21362109325d0d7b23d9b130067390eeae
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Einige Adobe Commerce- und Magento Open Source-Funktionen basieren auf [!DNL Commerce Services]  und als SaaS (Software as a Service) bereitgestellt werden. Um diese Dienste verwenden zu können, müssen Sie Ihre [!DNL Commerce] -Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels und geben Sie den Datenraum im [Konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html). Sie müssen dies nur einmal einrichten.

## Verfügbare Dienste

Im Folgenden werden die [!DNL Commerce] Funktionen, auf die Sie über [!DNL Commerce Services Connector]:

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

Der API-Schlüssel und der private Schlüssel werden aus dem [!DNL Commerce] Konto des Lizenzinhabers, das durch eine eindeutige [!DNL Commerce] ID (MageID). So übergeben Sie die Berechtigungsprüfung für Dienste wie [!DNL Product Recommendations] oder [!DNL Live Search]festgelegt ist, kann der Lizenzinhaber der Händlerorganisation den Satz von API-Schlüsseln generieren, solange das Konto gut aufgestellt ist. Die Schlüssel können auf der Grundlage des &quot;Bedarfs an Wissen&quot;an den Systemintegrator oder das Entwicklungsteam weitergegeben werden, der Projekte und Umgebungen im Auftrag des Lizenzinhabers verwaltet. Darüber hinaus sind Lösungsintegratoren auch berechtigt, [!DNL Commerce Services]. Wenn Sie ein Lösungsintegrator sind, ist der Unterzeichner der [!DNL Commerce] Der Partnervertrag sollte die API-Schlüssel generieren.

### API-Schlüssel und privaten Schlüssel generieren {#genapikey}

1. Melden Sie sich bei Ihrer [!DNL Commerce] Konto unter [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Unter dem **Magento** Registerkarte, wählen Sie **API-Portal** auf der Seitenleiste.

1. Aus dem _Umgebung_ Menü auswählen **Produktion** oder **Sandbox**.

   >[!NOTE]
   >
   > Für [!DNL _Produkt-Recommendations_] und [!DNL _Live Search_] auswählen **Produktion**. Produktionsschlüssel bieten Zugriff auf Produktions- und Nicht-Produktionsdatenbereiche. Sandbox-Schlüssel werden für diese Dienste nicht verwendet.

1. Geben Sie im Feld _API-Schlüssel_ und klicken Sie auf **Neu hinzufügen**.

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

Wenn [!DNL Commerce] -Instanz stellt erfolgreich eine Verbindung zu [!DNL Commerce Services], exportiert der Prozess der Katalogsynchronisierung Produktdaten aus Ihrer [!DNL Commerce] Server zu [!DNL Commerce Services]. [Weitere Infos](catalog-sync.md) Informationen zur Katalogsynchronisierung.
