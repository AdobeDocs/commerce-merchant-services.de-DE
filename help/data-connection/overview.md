---
title: Handbuch-Übersicht
description: Erfahren Sie, wie Sie mit der Erweiterung [!DNL Data Connection] Adobe Commerce-Daten in Adobe Experience Platform integrieren.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: b5727c90737ecfd237dd143801152f25600c3f97
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 0%

---

# [!DNL Data Connection] Einführung

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.

Die Erweiterung [!DNL Data Connection] verbindet Ihre Adobe Commerce-Webinstanz mit der Adobe Experience Platform und dem Edge Network. Für Entwickler mobiler Apps verwenden Sie das Adobe Experience Platform Mobile SDK mit Commerce, um Commerce-Daten zu erfassen und an die Experience Platform zu senden. [Weitere Infos](./mobile-sdk-epc.md).

Ihr Commerce-Store enthält eine Vielzahl von Daten. Informationen darüber, wie Ihre Kunden die Produkte auf Ihrer Site durchsuchen, anzeigen und letztendlich kaufen, können Möglichkeiten zur Schaffung eines personalisierteren Einkaufserlebnisses aufzeigen. Diese Daten können zwar zu nativen Commerce-Funktionen wie Warenkorbpreisregeln und dynamischen Bausteinen beitragen, doch bleiben die Daten in Ihrer Commerce-Instanz siloliert.

Die Adobe Experience Platform bietet eine Reihe von Technologien, die diese Daten über das Edge Network an andere Adobe DX-Produkte verteilen können, wenn sie mit Daten aus Ihrem Commerce-Store hydriert werden, um Einblicke in das Kaufverhalten Ihres Käufers zu gewinnen. Mit diesen tiefen Einblicken können Sie über alle Kanäle hinweg ein personalisierteres Einkaufserlebnis schaffen.

Die folgende Abbildung zeigt, wie Ihre Commerce-Daten von Ihrem Store zu anderen Adobe DX-Produkten übertragen werden, wenn die [!DNL Data Connection] -Erweiterung installiert und konfiguriert ist.

![Datenfluss zum Experience Platform Edge](assets/commerce-edge.png)

In der obigen Abbildung werden Ihre Verhaltens-, Back-Office- und Kundenprofildaten mithilfe eines SDK, einer API und eines Quell-Connectors an die Experience Platform Edge gesendet. Sie müssen nicht vollständig verstehen, wie diese Teile funktionieren, da die Erweiterung die Komplexität der Datenweitergabe für Sie handhabt. Wenn sich die Ereignisdaten am Rand befinden, können Sie diese Daten in andere Experience Platform-Anwendungen ziehen. Beispiel:

| Anwendung | Zweck | Nutzungsszenarios |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=de) | Profilverwaltung und Segmentierungsdienst | **Segmentierung des Einkaufsverlaufs**: Die Händler können Kunden identifizieren, die einen Artikel über einen bestimmten Zeitraum (monatlich, vierteljährlich, jährlich usw.) erwerben. Händler können dann Segmente für diese Kunden erstellen und sie für Promotions, Kampagnen und als _oberste der Trichterdaten_ für Leads für Abonnementdienste auswählen.<br> **Kategoriebasierte Segmentierung**: Händler können sehen, welche Produktkategorie gekauft wurde.<br> **Angebotsbasierte Segmentierung**: Händler können Kunden identifizieren, die Produkte konsistent zurückgeben. Die ihnen gebotenen Angebote und Rabatte können nun intelligenter sein. Beispielsweise kann der kostenlose Versand für einen Kunden entfernt werden, der ständig Produkte zurückgibt.<br> **Lookalike-Targeting**: Ein _Look-alike-Audience_ ist eine Methode, die ein Händler für seine Promotions anwendet, um neue Personen zu erreichen, die wahrscheinlich an seinem Geschäft interessiert sind, da sie ähnliche Merkmale wie Ihre bestehenden Kunden aufweisen. Lookalike-Segmente können basierend auf Verhaltens- und Transaktionsdaten erstellt werden.<br> **Kundenneigung**: Änderungen im Kundenverhalten können durch tiefere Kundenprofile identifiziert werden, die aus den Transaktionsdaten erstellt werden können. Der Tendenzwert wird stärker konfisiv sein, da mehr Daten in die Berechnungen fließen, z. B. Produktrückgaben und Produktkonfigurationen.<br> **Cross-Sell**: Ein Händler kann aus den in Commerce erfassten detaillierten Informationen starke Crosssell- und Up-Sell-Chancen erkennen. |
| [Kunde [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Detaillierte Analyse der vollständigen Commerce-Journey | **Saisonale Trends**: Ein Händler kann saisonale Trends identifizieren, was ihm hilft, sich auf die periodische Änderung der Nachfrage nach bestimmten Produkten vorzubereiten. Außerdem können Händler Änderungen der allgemeinen Beliebtheit jedes Produkts über Jahre hinweg identifizieren.<br> **Konversionsanalyse**: Indem sie wissen, wann ein Produkt gekauft wurde, können Händler in Verbindung mit dem Zugriff auf Store-Impressionsereignisse ein umfangreiches Profil des Kunden generieren, um Konversionsanalysen durchzuführen. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Detaillierte Analyse des Kundenverhaltens und der Kampagnenleistung | **Auftragsrückgaben**: Händler können Kunden und die größeren Kundensegmente identifizieren, die ein Muster wiederkehrender Produkte aufweisen. Dies hilft Händlern, ihre Commerce-Strategie zu verbessern, da sie verstehen, wie ihr Kundenbase-Verhalten aussieht.<br> **Bestelladresse**: Basierend auf der Lieferadresse kann ein Händler nachvollziehen, ob die Bestellungen von den Kunden selbst aufgegeben werden oder ob sie für eine andere Person oder Organisation bestimmt sind.<br> **Seasonalität-Trends**: Ein Händler kann saisonale Trends identifizieren, was ihm hilft, sich auf die periodische Änderung der Nachfrage nach bestimmten Produkten vorzubereiten. Außerdem können Händler Änderungen der allgemeinen Beliebtheit jedes Produkts über Jahre hinweg identifizieren.<br> **Konversionsanalyse**: Indem sie wissen, wann ein Produkt gekauft wurde, können Händler in Verbindung mit dem Zugriff auf Store-Impressionsereignisse ein umfangreiches Profil des Kunden generieren, um Konversionsanalysen durchzuführen. **Hinweis** Adobe Analytics unterstützt nur verhaltensbezogene Ereignisdaten (Storefront). Adobe Analytics unterstützt keine Transaktionsdaten (Backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Kanalübergreifende Kampagnenverwaltung | **Verhaltensbasierte Journey**: Händler können Kunden ansprechen, die vor zwei Jahren ein Mobiltelefon gekauft haben, indem sie vorschlagen, das neue Modell zu kaufen. Händler können personalisierte Kampagnen und Promotions für diese Kunden erstellen und E-Mail- und SMS-Funktionen nutzen, um Kontakt herzustellen. Außerdem können Händler historische Daten zur Reihenfolge und zum Verhalten verwenden, um Trends zu identifizieren. Beispielsweise kann ein Kunde, der in der Vergangenheit einen Artikel mit einer bestimmten Konfiguration gekauft hat und jetzt wieder dasselbe Produkt kauft, seine Journey erweitern, indem er ihm Sichtbarkeit und Zugriff auf dieselben Produktkonfigurationen gewährt.<br> **Personalization**: Mit Zugriff auf Kundenprofilinformationen kann [!DNL Journey Optimizer] hochgradig personalisierte Journey freigeschaltet werden, sodass Händler über verschiedene Kanäle Kontakt zu den Kunden aufnehmen können.<br> **Neues Profil erstellt**: Begrüßungs-E-Mails und Werbeaktivitäten können neue Kunden in ihren Einkaufs-Journey ermutigen und beeinflussen.<br> **Profil gelöscht**: Händler können festlegen, dass keine Werbe-E-Mails mehr an Kunden gesendet werden, die ihr Konto geschlossen haben. Alternativ können Händler auch Kampagnen erstellen, um verlorene Kunden zurückzugewinnen. |

## Experience Platform-Daten zurück in Commerce abrufen

Das Senden Ihrer Commerce-Daten an die Experience Platform mithilfe der Erweiterung [!DNL Data Connection] ist eine Seite der Datenfreigabe-Funktionen von Commerce. Die andere Seite, die eine optionale Erweiterung ist, heißt [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Mit dieser Erweiterung können Sie Zielgruppen in Real-Time CDP erstellen und diese Zielgruppen in Ihrem Commerce-Store bereitstellen, um über Warenkorbpreisregeln, zugehörige Produktregeln und dynamische Bausteine zu informieren.

Auf hoher Ebene sieht der Datenfluss von Ihrem Commerce-Store zum Experience Platform und zurück durch die Audience Activation-Erweiterung wie folgt aus:

![[!DNL Data Connection] flow](assets/data-connection.png)

Nachdem Sie die Verbindung zwischen Commerce und Experience Platform und Experience Platform mit Commerce eingerichtet haben, fließen die Daten weiter. Sie müssen keine erneute Verbindung herstellen, es sei denn, dies ist durch ein Upgrade erforderlich.

## Konzepte

Für die Freigabe von Daten zwischen diesen beiden Systemen müssen Sie verschiedene Konzepte kennen.

* **Daten** - Die Daten, die für die Experience Platform freigegeben werden, sind Daten, die aus Browserereignissen in Ihrer Storefront, Backoffice-Ereignissen auf dem Server und Profildatensatzdaten erfasst werden. Storefront-Ereignisse werden aus den Interaktionen der Käufer auf der Site erfasst und umfassen Ereignisse wie [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout) usw. Eine vollständige Liste der Storefront-Ereignisse finden Sie unter [ storefront events](events.md#storefront-events) . Serverseitige oder Back-Office-Ereignisse enthalten [Bestellstatus](events-backoffice.md#order-status)-Informationen wie [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled) usw. Eine vollständige Liste der Backoffice-Ereignisse finden Sie unter [Backoffice-Ereignisse](events-backoffice.md) . Profildatensatzdaten enthalten Informationen, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird. Weitere Informationen finden Sie unter [Profildatensatzdaten](events-profilerecord.md) .

* **Experience Platform und Edge Network** - Das Data Warehouse für die meisten Adobe DX-Produkte. An die Experience Platform gesendete Daten werden dann über das Experience Platform-Edge Network an die Adobe DX-Produkte übertragen. Sie können beispielsweise Journey Optimizer starten, Ihre spezifischen Commerce-Ereignisdaten vom Edge abrufen und in Journey Optimizer eine E-Mail zum abgebrochenen Warenkorb erstellen. Journey Optimizer kann diese E-Mail dann senden, wenn sich in Ihrem Commerce-Store ein Warenkorb befindet. Erfahren Sie mehr über die [Experience Platform und das Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Schema** - Das Schema beschreibt die Struktur der gesendeten Daten. Bevor Experience Platform Ihre Commerce-Daten erfassen kann, müssen Sie ein Schema erstellen, um die Datenstruktur zu beschreiben und Einschränkungen für den Datentyp bereitzustellen, der in jedem Feld enthalten sein kann. Schemas bestehen aus einer Basisklasse und keiner oder mehr Schemafeldgruppen. Das Schema verwendet die XDM-Struktur, die alle Adobe DX-Produkte lesen können. Wenn Sie also Ihre Daten an die Experience Platform senden, können Sie sicherstellen, dass Ihre Daten über alle DX-Produkte hinweg verstanden werden. Erfahren Sie mehr über [Schemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Datensatz** - Ein Speicher- und Verwaltungskonstrukt für eine Datenerfassung, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen wurden, sind in Datensätzen enthalten. Erfahren Sie mehr über [Datensätze](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe-DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website in Ihrer jeweiligen Adobe Commerce-Instanz verknüpft sein. Wenn Sie diesen Datastream erstellen, geben Sie das oben erstellte XDM-Schema an. Erfahren Sie mehr über [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Unterstützte Architektur

Die Erweiterung [!DNL Data Connection] ist in den folgenden Architekturen verfügbar:

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

>[!BEGINSHADEBOX]

## Voraussetzungen

Um die Erweiterung [!DNL Data Connection] zu verwenden, müssen Sie über Folgendes verfügen:

* Adobe Commerce 2.4.4 oder höher
* Adobe ID- und Organisations-ID
* [Adobe Client-Datenschicht (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), die zum Erfassen von Storefront-Ereignisdaten erforderlich ist
* Berechtigungen für andere Adobe DX-Produkte.

>[!ENDSHADEBOX]

## Onboarding-Schritte

Auf hoher Ebene umfasst die Aktivierung der Erweiterung [!DNL Data Connection] die folgenden Schritte:

1. [Installieren Sie](install.md) die Erweiterung [!DNL Data Connection] .
1. [Melden Sie sich ](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) bei Ihrem Adobe-Konto an und [zeigen Sie an, um Ihre Organisations-ID zu bestätigen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge, gefolgt von `@AdobeOrg` (und muss enthalten).
1. Stellen Sie sicher, dass Sie über [Berechtigung für die Datenerfassung in Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html) verfügen.
1. Überprüfen Sie die [Datentypen](data-ingestion.md), die Sie erfassen und senden können.
1. Erstellen oder aktualisieren Sie Ihr [Zeitreihenereignis-Schema](update-xdm.md) oder Ihr [Profildatensatzschema](profile-data.md) mit Commerce-spezifischen Feldgruppen.
1. [Erstellen Sie einen Datensatz](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die Commerce-Daten, die an die Experience Platform Edge gesendet werden.
1. [Erstellen Sie einen Datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. [Verbindung zu Commerce Services herstellen](../landing/saas.md).
1. [Verbindung zu Adobe Experience Platform herstellen](connect-data.md).

Der Rest dieses Leitfadens führt Sie durch all diese Schritte, um sich auf den neuesten Stand zu bringen und die Leistungsfähigkeit von Adobe DX-Produkten in Ihrem Commerce Store zu nutzen.

>[!NOTE]
>
>Erfahren Sie für Entwickler von Mobilgeräten, wie Sie das Adobe Experience Platform Mobile SDK mit Commerce [integrieren](./mobile-sdk-epc.md).

## Zielgruppe

Dieses Handbuch richtet sich an Adobe Commerce-Händler, die ihren Commerce-Store anreichern und personalisieren möchten, um das Einkaufserlebnis für ihre Kunden zu verbessern.

## Support

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

* [Hilfezentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
