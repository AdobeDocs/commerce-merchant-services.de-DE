---
title: Instanz verbinden
description: Verbinden Sie Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben Sie den Datenraum in der Konfiguration an.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 5d3a89b2ef06b2c67ec715ce4f31f22249b336e0
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Instanz verbinden

[!DNL Payment Services] wird von Commerce Services unterstützt und als SaaS (Software as a Service) bereitgestellt. Sie verbinden Ihre Commerce-Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels und geben den Datenraum in der Konfiguration mithilfe des [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) an. **Sie richten diese Verbindung nur einmal ein.**

>[!INFO]
>
> Weitere Informationen finden Sie in unserem Video [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) .

* Wenn Sie *bereits mit Ihrer Instanz verbunden haben*, können Sie mit der Einrichtung Ihrer Test-Sandbox ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html) fortfahren, indem Sie Ihre API-Anmeldeinformationen abrufen und verwenden und Commerce Services konfigurieren.[
* Wenn Sie weiterhin *Ihre Instanz verbinden müssen*, finden Sie in diesem Thema Informationen zum [Abrufen von API-Anmeldeinformationen](#obtain-api-credentials) und zum [Konfigurieren von Commerce Services](#configure-commerce-services).
* Wenn Sie *nicht sicher sind, ob Ihre Instanz verbunden ist, navigieren Sie zu **System**> Dienste >**Commerce Services Connector**und zeigen Sie die öffentlichen und privaten API-Schlüsselwerte in den Abschnitten [!UICONTROL Sandbox Keys] und [!UICONTROL Production Keys] sowie in den Abschnitten* Projekt *und* Datenraum *im Abschnitt [!UICONTROL SaaS Identifier] an.* Wenn diese Werte vorhanden sind, ist Ihre Instanz verbunden.

>[!NOTE]
>
>Alle Händler mit Berechtigung für Zahlungsdienste können einen Produktionsdatenraum und zwei Testdatenbereiche verwenden.

## API-Anmeldeinformationen abrufen

Um einen Commerce SaaS-Dienst zu nutzen, müssen Sie die API-Schlüssel Ihrer Instanz (öffentlicher Commerce-API-Schlüssel und privater Schlüssel) sowohl für die Sandbox als auch für die Produktion verwenden, die in Ihrem [Konto-Dashboard](https://account.magento.com/customer/account/login) erstellt und verwaltet werden. [Das Schlüsselpaar](https://docs.magento.com/user-guide/configuration/services/saas.html) kann für ein Commerce-Konto erstellt werden - eines für Sandbox und eines für Produktion - es kann jedoch immer nur ein Paar aktiv verwendet werden.

>[!NOTE]
>
>Benötigen Sie Hilfe beim Zugriff auf Ihr [!UICONTROL My Account] Dashboard? Siehe [Erstellen eines Commerce-Kontos](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Nach der Erstellung ist in Ihrem Dashboard für Mein Konto immer ein öffentlicher API-Schlüssel verfügbar. Sie kann nach Bedarf kopiert oder gelöscht werden. Der private API-Schlüssel wird angezeigt, wenn Sie einen öffentlichen API-Schlüssel für Sandbox oder Produktion erstellen. Er ist nur zum Kopieren oder Speichern über das sich daraus ergebende Dialogfeld verfügbar und kann später nicht mehr aufgerufen werden.

Ein bestimmtes API-Schlüsselpaar gilt für alle Commerce-Dienste in einer Umgebung. Wenn Sie Commerce Services bereits für Ihre Instanz konfiguriert haben, ist Ihr API-Schlüsselpaar bereits im Commerce Services Connector vorhanden.

Wenn Ihr API-Schlüssel verloren geht, muss ein neues API-Schlüsselpaar [generiert](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) und [angewendet](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) werden, um die Commerce Services Connector-Konfiguration in der Admin-Konsole zu konfigurieren. Wenn die falschen Schlüssel konfiguriert sind oder keine in der Konfiguration vorhanden sind, wird in den Zahlungsdiensten ein Dialogfeld mit einem Fehler bei der Kontoüberprüfung angezeigt, in dem Sie darüber informiert werden, dass das Konto nicht verifiziert wurde.

Eine [ Liste der verfügbaren Commerce-Dienste anzeigen, die die API verwenden.](https://docs.magento.com/user-guide/system/saas.html#available-services)

Informationen zum Generieren eines API-Schlüssels für Sandbox- oder Produktionsumgebungen finden Sie unter [Anmeldedaten](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Es wird empfohlen, die API-Schlüsselpaar *und* nicht neu zu generieren und die SaaS-Kennung und/oder den Datenraum in einer aktiven Produktionsinstanz zu ändern. Sie verlieren Daten für Ihre Instanz, wenn sie geändert werden.

## Konfigurieren von Commerce Services

Derselbe API-Schlüssel kann für alle Instanzen verwendet werden, aber jede Instanz muss über einen eigenen [SaaS-Datenraum](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv) verfügen.

>[!NOTE]
>
>Händler müssen für ihre Zahlungsansprüche dieselben Schlüssel verwenden, die für die MageID generiert wurden.

Nachdem Sie Ihre Anmeldeinformationen erhalten haben, können Sie Ihr SaaS-Projekt und den Saas-Datenraum konfigurieren.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicken Sie auf **[!UICONTROL Configure Commerce Services]**.

   Diese Option ist sichtbar, wenn Sie Commerce Services noch nicht für Ihr Konto konfiguriert haben.

   Sie werden zum Konfigurationsbereich unter Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**geleitet, um Ihren Commerce Services Connector zu konfigurieren.

1. Um Ihre Commerce-Dienste zu konfigurieren, führen Sie die unter [SaaS-Konfiguration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv) beschriebenen Schritte aus.

   >[!INFO]
   >
   > Weitere Informationen finden Sie in unserem Video [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) .

## Endpunkt

[!DNL Payment Services] verwendet den [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html), um eine Verbindung zu Commerce Services herzustellen und als SaaS bereitzustellen. Dieser [!DNL Commerce Services Connector] kommuniziert über den Endpunkt unter:

* `commerce-beta.adobe.io` für Sandbox-Umgebungen.
* `commerce.adobe.io for` für Live-Umgebungen.
