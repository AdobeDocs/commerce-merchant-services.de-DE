---
title: Handbuch-Übersicht
description: Erfahren Sie, wie Sie Adobe Commerce-Daten mithilfe des [!DNL Data Connection] -Erweiterung.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: af54529ad037dc99dbc07cf1a6ac270d17f16870
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 0%

---

# [!DNL Data Connection] Einführung

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection].

Die [!DNL Data Connection] -Erweiterung verbindet Ihre Adobe Commerce-Webinstanz mit Adobe Experience Platform und dem Edge-Netzwerk. Erfahren Sie, wie [integrieren](./mobile-sdk-epc.md) das Adobe Experience Platform Mobile SDK mit Commerce.

Ihr Commerce-Store enthält eine Vielzahl von Daten. Informationen darüber, wie Ihre Kunden die Produkte auf Ihrer Site durchsuchen, anzeigen und letztendlich kaufen, können Möglichkeiten zur Schaffung eines personalisierteren Einkaufserlebnisses aufzeigen. Diese Daten können zwar zu nativen Commerce-Funktionen wie Warenkorbpreisregeln und dynamischen Bausteinen beitragen, doch bleiben die Daten in Ihrer Commerce-Instanz siloliert.

Die Adobe Experience Platform bietet eine Reihe von Technologien, die diese Daten über das Edge-Netzwerk an andere Adobe DX-Produkte verteilen können, wenn sie mit Daten aus Ihrem Commerce-Store bereitgestellt werden, um Einblicke in das Kaufverhalten Ihrer Kunden zu erhalten. Mit diesen tiefen Einblicken können Sie über alle Kanäle hinweg ein personalisierteres Einkaufserlebnis schaffen.

Die folgende Abbildung zeigt, wie Ihre Commerce-Daten von Ihrem Store zu anderen Adobe DX-Produkten übertragen werden:

![Datenfluss zum Experience Platform-Edge](assets/commerce-edge.png)

In der obigen Abbildung werden Ihre Verhaltens-, Back-Office- und Kundenprofildaten mithilfe eines SDK, einer API und eines Quell-Connectors an die Experience Platform Edge gesendet. Sie müssen nicht vollständig verstehen, wie diese Teile funktionieren, da die Erweiterung die Komplexität der Datenweitergabe für Sie handhabt. Wenn sich die Ereignisdaten am Rand befinden, können Sie diese Daten in andere Experience Platform-Anwendungen ziehen. Beispiel:

| Anwendung | Zweck | Nutzungsszenarios |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html) | Profilverwaltung und Segmentierungsdienst | **Segmentierung des Kaufverlaufs**: Händler können Kunden identifizieren, die einen Artikel über einen bestimmten Zeitraum (monatlich, vierteljährlich, jährlich usw.) erwerben. Händler können dann Segmente für diese Kunden erstellen und sie für Promotions, Kampagnen und als _oberste Ebene des Trichters_ Daten für Leads für Anmeldedienste.<br> **Kategoriebasierte Segmentierung**: Händler können sehen, welche Produktkategorie gekauft wurde.<br> **Angebotsbasierte Segmentierung**: Händler können Kunden identifizieren, die Produkte konsistent zurückgeben. Die ihnen gebotenen Angebote und Rabatte können nun intelligenter sein. Beispielsweise kann der kostenlose Versand für einen Kunden entfernt werden, der ständig Produkte zurückgibt.<br> **Lookalike-Targeting**: A _Lookalike-Zielgruppe_ ist eine Methode, die ein Händler für seine Promotions verwendet, um neue Personen zu erreichen, die wahrscheinlich an seinem Geschäft interessiert sind, da sie ähnliche Merkmale wie Ihre bestehenden Kunden aufweisen. Lookalike-Segmente können basierend auf Verhaltens- und Transaktionsdaten erstellt werden.<br> **Kundenneigung**: Änderungen am Kundenverhalten können durch tiefere Kundenprofile identifiziert werden, die anhand der Transaktionsdaten erstellt werden können. Der Tendenzwert wird stärker konfisiv sein, da mehr Daten in die Berechnungen fließen, wie z. B. Produktrückgaben und Produktkonfigurationen.<br> **Cross-Sell**: Ein Händler kann aus den detaillierten Informationen, die in Commerce erfasst werden, starke Crosssell- und Up-Sell-Chancen erkennen. |
| [Kunde [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Detaillierte Analyse der vollständigen Commerce-Journey | **Saisonale Trends**: Ein Händler kann saisonale Trends identifizieren, die ihn bei der Vorbereitung auf die periodische Nachfrage nach bestimmten Produkten unterstützen. Außerdem können Händler Änderungen der allgemeinen Beliebtheit jedes Produkts über Jahre hinweg identifizieren.<br> **Konversionsanalyse**: Wenn Händler wissen, wann ein Produkt gekauft wurde, können sie in Verbindung mit dem Zugriff auf Store-Impressionsereignisse ein umfangreiches Profil des Kunden generieren, um Konversionsanalysen durchzuführen. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Detaillierte Analyse des Kundenverhaltens und der Kampagnenleistung | **Auftragseingabe**: Händler können Kunden und die größeren Kundensegmente identifizieren, die ein Muster wiederkehrender Produkte aufweisen. Dies hilft Händlern, ihre Commerce-Strategie zu verbessern, da sie verstehen, wie ihr Kundenbase-Verhalten aussieht.<br> **Bestelladresse**: Basierend auf der Lieferadresse kann ein Händler nachvollziehen, ob die Bestellungen von den Kunden selbst aufgegeben werden oder ob sie für eine andere Person oder Organisation bestimmt sind.<br> **Saisonabhängigkeit**: Ein Händler kann saisonale Trends identifizieren, die ihn bei der Vorbereitung auf die periodische Nachfrage nach bestimmten Produkten unterstützen. Außerdem können Händler Änderungen der allgemeinen Beliebtheit jedes Produkts über Jahre hinweg identifizieren.<br> **Konversionsanalyse**: Wenn Händler wissen, wann ein Produkt gekauft wurde, können sie in Verbindung mit dem Zugriff auf Store-Impressionsereignisse ein umfangreiches Profil des Kunden generieren, um Konversionsanalysen durchzuführen. **Hinweis** Adobe Analytics unterstützt nur verhaltensbezogene Ereignisdaten (Storefront). Adobe Analytics unterstützt keine Transaktionsdaten (Backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Kanalübergreifende Kampagnenverwaltung | **Verhaltensbasierte Journey**: Händler können Kunden ansprechen, die vor zwei Jahren ein Mobiltelefon gekauft haben, indem sie vorschlagen, das neue Modell zu kaufen. Händler können personalisierte Kampagnen und Promotions für diese Kunden erstellen und E-Mail- und SMS-Funktionen nutzen, um Kontakt herzustellen. Außerdem können Händler historische Daten zur Reihenfolge und zum Verhalten verwenden, um Trends zu identifizieren. So kann beispielsweise ein Kunde, der in der Vergangenheit einen Artikel mit einer bestimmten Konfiguration gekauft hat und jetzt wieder dasselbe Produkt kauft, seine Journey erweitern, indem er ihm Sichtbarkeit und Zugriff auf dieselben Produktkonfigurationen gewährt.<br> **Personalisierung**: Mit Zugriff auf Kundenprofilinformationen, [!DNL Journey Optimizer] kann hochgradig personalisierte Journey entsperren, sodass Händler über verschiedene Kanäle Kontakt zu den Kunden aufnehmen können.<br> **Neues Profil erstellt**: Willkommens-E-Mails und Werbeaktivitäten können neue Kunden in ihren Einkaufs-Journey ermutigen und beeinflussen.<br> **Profil gelöscht**: Händler können festlegen, dass sie keine Werbe-E-Mails mehr an Kunden senden, die ihr Konto geschlossen haben. Alternativ können Händler auch Kampagnen erstellen, um verlorene Kunden zurückzugewinnen. |

## Experience Platform-Daten zurück in Commerce abrufen

Senden Ihrer Commerce-Daten an die Experience Platform mithilfe der [!DNL Data Connection] -Erweiterung ist eine Seite der Datenfreigabe-Funktionen von Commerce. Die andere Seite, die eine optionale Erweiterung ist, wird als [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Mit dieser Erweiterung können Sie Zielgruppen in Real-Time CDP erstellen und diese Zielgruppen in Ihrem Commerce-Store bereitstellen, um über Warenkorbpreisregeln, zugehörige Produktregeln (Beta) und dynamische Bausteine zu informieren.

Auf hoher Ebene sieht der Datenfluss von Ihrem Commerce-Store zum Experience Platform und zurück durch die Audience Activation-Erweiterung wie folgt aus:

![[!DNL Data Connection] Fluss](assets/data-connection.png)

Nachdem Sie die Verbindung zwischen Commerce zu Experience Platform und Experience Platform zu Commerce eingerichtet haben, fließen die Daten weiter. Sie müssen keine erneute Verbindung herstellen, es sei denn, dies ist durch ein Upgrade erforderlich.

## Konzepte

Für die Freigabe von Daten zwischen diesen beiden Systemen müssen Sie verschiedene Konzepte kennen.

* **Daten** - Die Daten, die für die Experience Platform freigegeben werden, sind Daten, die aus Browserereignissen in Ihrer Storefront, Backoffice-Ereignissen auf dem Server und Profildatensätzen erfasst werden. Storefront-Ereignisse werden aus den Interaktionen der Kunden auf der Site erfasst und umfassen Ereignisse wie [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout)usw. Siehe [Storefront-Ereignisse](events.md#storefront-events) für die vollständige Liste der Storefront-Ereignisse. Serverseitige oder Back-Office-Ereignisse umfassen [Bestellstatus](events-backoffice.md#order-status) Informationen, wie [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled)usw. Siehe [Backoffice-Ereignisse](events-backoffice.md) für die vollständige Liste der Backoffice-Ereignisse. Profildatensatzdaten enthalten Informationen, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird. Siehe [Profildatensatzdaten](events-profilerecord.md) , um mehr zu erfahren.

* **Experience Platform und Edge Network** - Das Data Warehouse für die meisten Adobe DX-Produkte. An die Experience Platform gesendete Daten werden dann über das Experience Platform Edge Network an die Adobe-DX-Produkte übertragen. Sie können beispielsweise Journey Optimizer starten, Ihre spezifischen Commerce-Ereignisdaten vom Edge abrufen und in Journey Optimizer eine E-Mail zum abgebrochenen Warenkorb erstellen. Journey Optimizer kann diese E-Mail dann senden, wenn in Ihrem Commerce-Store Warenkörbe stehen. Weitere Informationen zum [Experience Platform und Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Schema** - Das Schema beschreibt die Struktur der gesendeten Daten. Bevor Experience Platform Ihre Commerce-Daten erfassen kann, müssen Sie ein Schema erstellen, um die Datenstruktur zu beschreiben und Einschränkungen für den Datentyp bereitzustellen, der in jedem Feld enthalten sein kann. Schemas bestehen aus einer Basisklasse und keiner oder mehr Schemafeldgruppen. Das Schema verwendet die XDM-Struktur, die alle Adobe DX-Produkte lesen können. Wenn Sie also Ihre Daten an die Experience Platform senden, können Sie sicherstellen, dass Ihre Daten über alle DX-Produkte hinweg verstanden werden. Weitere Informationen [Schemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Datensatz** - Ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen wurden, sind in Datensätzen enthalten. Weitere Informationen [Datensätze](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft sein. Wenn Sie diesen Datastream erstellen, geben Sie das oben erstellte XDM-Schema an. Weitere Informationen [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Unterstützte Architektur

Die [!DNL Data Connection] -Erweiterung ist in den folgenden Architekturen verfügbar:

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## Voraussetzungen

So verwenden Sie die [!DNL Data Connection] -Erweiterung verwenden, müssen Sie über Folgendes verfügen:

* Adobe Commerce 2.4.4 oder höher
* Adobe ID- und Organisations-ID
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), die zur Erfassung von Storefront-Ereignisdaten erforderlich ist
* Berechtigungen für andere Adobe DX-Produkte.

## Onboarding-Schritte

Auf hoher Ebene ermöglicht die [!DNL Data Connection] -Erweiterung umfasst die folgenden Schritte:

1. [Installieren](install.md) die [!DNL Data Connection] -Erweiterung.
1. [Anmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) auf Ihr Adobe-Konto und [Bestätigung anzeigen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) Ihre Organisations-ID. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von (und muss enthalten) `@AdobeOrg`.
1. Stellen Sie sicher, dass [Berechtigung für die Datenerfassung in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. Überprüfen Sie die [Datentypen](data-ingestion.md) Sie können sammeln und versenden.
1. Erstellen oder aktualisieren Sie Ihre [Zeitreihenereignisschema](update-xdm.md) oder [Profildatensatzschema](profile-data.md) mit Commerce-spezifischen Feldergruppen.
1. [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die Commerce-Daten, die an Experience Platform Edge gesendet werden.
1. [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. [Verbindung zu Commerce Services herstellen](../landing/saas.md).
1. [Verbindung zu Adobe Experience Platform herstellen](connect-data.md).

Der Rest dieses Leitfadens führt Sie durch all diese Schritte, um sich auf den neuesten Stand zu bringen und die Leistungsfähigkeit von Adobe DX-Produkten in Ihrem Commerce-Geschäft zu nutzen.

>[!NOTE]
>
>Erfahren Sie für Entwickler von Mobilgeräten, wie Sie [integrieren](./mobile-sdk-epc.md) das Adobe Experience Platform Mobile SDK mit Commerce.

## Zielgruppe

Dieses Handbuch richtet sich an Adobe Commerce-Händler, die ihren Commerce-Store anreichern und personalisieren möchten, um das Einkaufserlebnis für ihre Kunden zu verbessern.

## Support

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

* [Hilfezentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
