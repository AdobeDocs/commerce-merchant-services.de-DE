---
title: Instanz verbinden
description: Verbinden Sie Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben Sie den Datenraum in der Konfiguration an.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 57b140463d457404b57dd23d33c72e48b4c3ac89
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Instanz verbinden

[!DNL Payment Services] wird von Commerce Services unterstützt und als SaaS (Software as a Service) bereitgestellt. Sie verbinden Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben den Datenraum in der Konfiguration mithilfe der [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Sie richten diese Verbindung nur einmal ein.**

* Wenn Sie *bereits mit Ihrer Instanz verbunden ist*, indem Sie Ihre API-Anmeldeinformationen abrufen und verwenden und Commerce Services konfigurieren, können Sie mit dem [Einrichten der Test-Sandbox](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Wenn Sie *muss Ihre Instanz verbinden* Informationen finden Sie in diesem Thema zu [Abrufen von API-Anmeldeinformationen](#obtain-api-credentials) und [Konfigurieren von Commerce Services](#configure-commerce-services).
* Wenn Sie *Unsicher, ob Ihre Instanz verbunden ist*, navigieren Sie zu **System** > Dienste > **Commerce Services Connector** und zeigen Sie die öffentlichen und privaten API-Schlüsselwerte im [!UICONTROL Sandbox Keys] und [!UICONTROL Production Keys] und die *Projekt* und *Datenraum* -Felder in der [!UICONTROL SaaS Identifier] Abschnitt. Wenn diese Werte vorhanden sind, ist Ihre Instanz verbunden.

>[!NOTE]
>
>Alle Händler mit Berechtigung für Zahlungsdienste können einen Produktionsdatenraum und zwei Testdatenbereiche verwenden.

## API-Anmeldeinformationen abrufen

Um einen Commerce SaaS-Dienst zu nutzen, müssen Sie die API-Schlüssel Ihrer Instanz (öffentlicher Commerce-API-Schlüssel und privater Schlüssel) sowohl für Sandbox als auch Produktion verwenden, die in Ihrer [Mein Konto-Dashboard](https://account.magento.com/customer/account/login). [Das Schlüsselpaar](https://docs.magento.com/user-guide/configuration/services/saas.html) kann für ein Commerce-Konto erstellt werden - eines für Sandbox und eines für Produktion - wobei jeweils nur ein Paar aktiv verwendet werden kann.

>[!NOTE]
>
>Sie benötigen Hilfe beim Zugriff auf Ihre [!UICONTROL My Account] Dashboard? Siehe [Erstellen eines Commerce-Kontos](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Nach der Erstellung ist in Ihrem Dashboard für Mein Konto immer ein öffentlicher API-Schlüssel verfügbar. Sie kann nach Bedarf kopiert oder gelöscht werden. Der private API-Schlüssel wird angezeigt, wenn Sie einen öffentlichen API-Schlüssel für Sandbox oder Produktion erstellen. Er ist nur zum Kopieren oder Speichern über das sich daraus ergebende Dialogfeld verfügbar und kann später nicht mehr aufgerufen werden.

Ein bestimmtes API-Schlüsselpaar gilt für alle Commerce Services in einer Umgebung. Wenn Sie also bereits Commerce Services für Ihre Instanz konfiguriert haben, ist Ihr API-Schlüsselpaar bereits im Commerce Services Connector vorhanden.

Wenn Ihr API-Schlüssel verloren geht, muss ein neues API-Schlüsselpaar [generiert](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) und [angewendet](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) zur Connector-Konfiguration für Commerce Services in der Admin-Instanz hinzugefügt. Wenn die falschen Schlüssel konfiguriert sind oder keine in der Konfiguration vorhanden sind, wird in den Zahlungsdiensten ein Dialogfeld mit einem Fehler bei der Kontoüberprüfung angezeigt, in dem Sie darüber informiert werden, dass das Konto nicht verifiziert wurde.

Siehe [Liste der verfügbaren Commerce-Services, die die API verwenden](https://docs.magento.com/user-guide/system/saas.html#available-services).

Informationen zum Generieren eines API-Schlüssels für Sandbox- oder Produktionsumgebungen finden Sie unter [Anmeldeinformationen](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Es wird empfohlen, kein API-Schlüsselpaar neu zu generieren *und* ändern Sie die SaaS-Kennung und/oder den Datenraum in einer aktiven Produktionsinstanz. Sie verlieren Daten für Ihre Instanz, wenn sie geändert werden.

## Commerce Services konfigurieren

Derselbe API-Schlüssel kann über mehrere Instanzen hinweg verwendet werden, aber jede Instanz muss über einen eigenen [SaaS-Datenraum](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Händler müssen für ihre Zahlungsansprüche dieselben Schlüssel verwenden, die für die MageID generiert wurden.

Nachdem Sie Ihre Anmeldeinformationen erhalten haben, können Sie Ihr SaaS-Projekt und den Saas-Datenraum konfigurieren.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicks **[!UICONTROL Configure Commerce Services]**.

   Diese Option ist sichtbar, wenn Sie Commerce Services noch nicht für Ihr Konto konfiguriert haben.

   Sie werden zum Konfigurationsbereich in der Admin-Konsole weitergeleitet. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, um Ihren Commerce Services Connector zu konfigurieren.

1. Gehen Sie wie in beschrieben vor, um Ihre Commerce-Services zu konfigurieren. [SaaS-Konfiguration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
