---
title: Commerce Services Connector
description: Erfahren Sie, wie Sie Ihre Adobe Commerce- oder Magento Open Source-Instanz mithilfe von Produktions- und Sandbox-API-Schlüsseln in Dienste integrieren.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 3eb873c84edb56d2fc399c72296f2b545a78064e
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Einige Adobe Commerce- und Magento Open Source-Funktionen werden von [!DNL Commerce Services] unterstützt und als SaaS (Software as a service) bereitgestellt. Um diese Dienste zu verwenden, müssen Sie Ihre [!DNL Commerce] -Instanz mithilfe der Produktions- und Sandbox-API-Schlüssel verbinden und den Datenraum in der [Konfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) angeben. Sie müssen dies nur einmal einrichten.

## Verfügbare Dienste {#availableservices}

In der folgenden Liste sind die [!DNL Commerce]-Funktionen aufgeführt, auf die Sie über die [!DNL Commerce Services Connector] zugreifen können:

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

Auf hoher Ebene besteht der [!DNL Commerce Services Connector] aus den folgenden Kernelementen:

![Commerce Services Connector-Architektur](assets/saas-config-sync-workflow.png)

In den folgenden Abschnitten werden die einzelnen Elemente ausführlicher erläutert.

## Anmeldeinformationen {#apikey}

Die Produktions- und Sandbox-API-Schlüssel werden aus dem [!DNL Commerce]-Konto des [Lizenzinhabers](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding) generiert, das durch eine eindeutige [!DNL Commerce]-ID (MageID) identifiziert wird. Um die Berechtigungsprüfung für Dienste wie [!DNL Product Recommendations] oder [!DNL Live Search] zu übergeben, kann der Lizenzinhaber für die Organisation des Händlers den Satz an API-Schlüsseln generieren, sofern das Konto gut aufgestellt ist.

Die Schlüssel können &quot;bedarfsorientiert&quot;an den Systemintegrator oder das Entwicklungsteam weitergegeben werden, der im Auftrag des Lizenzinhabers Projekte und Umgebungen verwaltet. Entwickler, denen der Lizenzinhaber [!DNL Shared Access] gewährt hat, können die Schlüssel nicht in ihrem Namen generieren, selbst wenn die Organisation des Händlers in der Dropdown-Liste [!DNL Switch Accounts] auf ihrem Konto vorhanden ist.

Darüber hinaus sind Lösungsintegratoren auch berechtigt, [!DNL Commerce Services] zu verwenden. Wenn Sie Lösungsintegrator sind, sollte der Unterzeichner des [!DNL Commerce] -Partnervertrags die API-Schlüssel generieren.

>[!NOTE]
>
>Der Lizenzinhaber ist in der Regel der Primäre Ansprechpartner für das Adobe Commerce-Konto und nicht immer derselbe wie der Projekteigentümer des Adobe Commerce-Projekts für Cloud-Infrastruktur.

### Generieren der Produktions- und Sandbox-API-Schlüssel {#genapikey}

1. Melden Sie sich bei Ihrem [!DNL Commerce]-Konto unter [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;} an.

1. Wählen Sie auf der Registerkarte **Magento** in der Seitenleiste die Option **API-Portal** aus.

1. Wählen Sie im Menü _Umgebung_ die Option **Produktion** oder **Sandbox** aus.

1. Geben Sie im Abschnitt _API-Schlüssel_ einen Namen ein und klicken Sie auf **Neu hinzufügen**.

   Dadurch wird ein Dialogfeld zum Herunterladen des neuen Schlüssels geöffnet.

   ![Privaten Schlüssel herunterladen](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Dies ist die einzige Möglichkeit, dass Sie Ihre Schlüssel kopieren oder herunterladen müssen.

1. Klicken Sie auf **Herunterladen** und dann auf **Abbrechen**.

1. Wiederholen Sie die obigen Schritte für jede Umgebung (Produktion und Sandbox).

   Im Abschnitt **API-Schlüssel** werden jetzt Ihre API-Schlüssel (öffentlichen) angezeigt. Sie benötigen sowohl die Produktions- als auch die Sandbox-Schlüssel (öffentlich+privat), wenn Sie [ein SaaS-Projekt auswählen oder erstellen](#createsaasenv).

## SaaS-Konfiguration {#saasenv}

[!DNL Commerce] -Instanzen müssen mit einem SaaS-Projekt und einem SaaS-Datenspeicher konfiguriert werden, damit [!DNL Commerce Services] Daten an den richtigen Speicherort senden kann. Ein SaaS-Projekt gruppiert alle SaaS-Datenräume. Die SaaS-Datenräume werden verwendet, um Daten zu erfassen und zu speichern, die das Funktionieren von [!DNL Commerce Services] ermöglichen. Einige dieser Daten können aus der [!DNL Commerce] -Instanz exportiert werden, andere aus dem Kaufverhalten in der Storefront. Diese Daten werden dann beibehalten, um den Cloud-Speicher zu sichern.

Für [!DNL Product Recommendations] enthält der SaaS-Datenraum Katalog- und Verhaltensdaten. Sie können eine [!DNL Commerce] -Instanz auf einen SaaS-Datenraum verweisen, indem Sie [sie in der [!DNL Commerce] -Konfiguration auswählen.](https://docs.magento.com/user-guide/configuration/services/saas.html)

>[!WARNING]
>
> Verwenden Sie Ihren Produktions-SaaS-Datenraum nur in Ihrer Produktions- [!DNL Commerce]-Installation, um Datenkollisionen zu vermeiden. Andernfalls riskieren Sie, Ihre Produktionsstandortdaten mit Testdaten zu verschmutzen, was zu Bereitstellungsverzögerungen führt. Beispielsweise können Ihre Produktionsproduktdaten fälschlicherweise aus Staging-Daten wie Staging-URLs überschrieben werden.

### Auswählen oder Erstellen eines SaaS-Projekts {#createsaasenv}

Um ein SaaS-Projekt auszuwählen oder zu erstellen, fordern Sie den API-Schlüssel [!DNL Commerce] vom Inhaber der [!DNL Commerce]-Lizenz für Ihren Store an:

>[!NOTE]
>
> Wenn der Abschnitt **[!UICONTROL Commerce Services Connector]** nicht in der [!DNL Commerce] -Konfiguration angezeigt wird, müssen Sie die [!DNL Commerce] -Module für den gewünschten [[!DNL Commerce] Dienst](#availableservices) installieren.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **System** > Dienste > **Commerce Services Connector**.

   Wenn der Abschnitt **[!UICONTROL Commerce Services Connector]** nicht in der [!DNL Commerce] -Konfiguration angezeigt wird, installieren Sie die [!DNL Commerce] -Module für den gewünschten [[!DNL Commerce] Dienst](#availableservices). Stellen Sie außerdem sicher, dass das Paket `magento/module-services-id` installiert ist.

1. Fügen Sie in den Abschnitten _Sandbox-API-Schlüssel_ und _Produktions-API-Schlüssel_ Ihre Schlüsselwerte ein.

   Private Schlüssel müssen &quot;`----BEGIN PRIVATE KEY---`&quot; am Anfang des Schlüssels und &quot;`----END PRIVATE KEY----`&quot; am Ende des privaten Schlüssels enthalten.

1. Klicken Sie auf **Speichern**.

Alle SaaS-Projekte, die mit Ihren Schlüsseln verknüpft sind, werden im Feld **Projekt** im Abschnitt **SaaS-Kennung** angezeigt.

1. Wenn keine SaaS-Projekte vorhanden sind, klicken Sie auf **Projekt erstellen**. Geben Sie dann im Feld **Projekt** einen Namen für Ihr SaaS-Projekt ein.

   Wenn Sie ein SaaS-Projekt erstellen, generiert [!DNL Commerce] je nach Ihrer [!DNL Commerce]-Lizenz einen oder mehrere SaaS-Datenräume:
   - Adobe Commerce - Ein Produktionsdatenraum, nur zwei Testdatenbereiche. Bei Cloud Pro-Projekten mit mehreren Staging-Umgebungen können Sie zusätzliche Testdatenbereiche für jede Staging-Umgebung anfordern, indem Sie [eine Support-Anfrage senden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
   - Magento Open Source - Ein Produktionsdatenraum; keine Testdatenbereiche

1. Wählen Sie den **Datenraum** aus, der für die aktuelle Konfiguration Ihres [!DNL Commerce]-Stores verwendet werden soll.

>[!NOTE]
>
>Wenn Sie separate Instanzen zur Integration mit Commerce Services haben, senden Sie [ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket), um ein neues SaaS-Projekt für jede zusätzliche Instanz anzufordern. Nachdem der Support das SaaS-Projekt erstellt hat, konfigurieren Sie die Commerce Services-Integration für die Instanz mit demselben API-Schlüssel und wählen Sie das neue SaaS-Projekt für den Datenraum aus.

>[!WARNING]
>
> Wenn Sie im Abschnitt &quot;Mein Konto&quot;im API-Portal neue Schlüssel generieren, aktualisieren Sie sofort die API-Schlüssel in der Admin-Konfiguration. Wenn Sie neue Schlüssel generieren und diese nicht im Admin aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Um die Namen Ihres SaaS-Projekts oder Ihres Datenraums zu ändern, klicken Sie neben einem der beiden Elemente auf **Umbenennen** . Das Ändern des Namens wirkt sich nicht auf Ihren Dienst aus, da der Name nur eine Bezeichnung ist, mit der Sie Projekte und Datenräume identifizieren und unterscheiden können.

## IMS-Organisation (optional) {#organizationid}

Um Ihre Adobe Commerce-Instanz mit Adobe Experience Platform zu verbinden, melden Sie sich mit Ihrem Adobe-Konto bei Ihrem Adobe ID an. Nach der Anmeldung wird die mit Ihrem Adobe-Konto verknüpfte IMS-Organisation in diesem Abschnitt angezeigt.

## SaaS-Datenexport

Wenn Ihre [!DNL Commerce] -Instanz erfolgreich eine Verbindung zu [!DNL Commerce Services] herstellt, exportiert der SaaS-Datenexportprozess Commerce-Daten von Ihrem [!DNL Commerce] -Server nach [!DNL Commerce SaaS Services], damit sie mit verbundenen Commerce-Services synchronisiert werden können. Im Admin können Sie den Synchronisierungsstatus mithilfe des [Daten-Management-Dashboards](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) überprüfen. Weitere Informationen finden Sie im [SAAS-Datenexport-Handbuch](../data-export/overview.md).
