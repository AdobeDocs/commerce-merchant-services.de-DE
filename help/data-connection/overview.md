---
title: Handbuch-Übersicht
description: Erfahren Sie, wie Sie Adobe Commerce-Daten mit Adobe Experience Platform mithilfe der  [!DNL Data Connection] -Erweiterung integrieren.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: eb98389cfdd7a0492a4437e9de9412f2d2e5401c
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 0%

---

# [!DNL Data Connection]

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.

Die [!DNL Data Connection]-Erweiterung verbindet Ihre Adobe Commerce-Webinstanz mit der Adobe Experience Platform und dem Edge Network. Für Entwickler mobiler Apps verwenden Sie die Adobe Experience Platform Mobile SDK mit Commerce , um Commerce-Daten zu erfassen und an die Experience Platform zu senden. [Weitere Informationen](./mobile-sdk-epc.md).

Ihr Commerce-Store enthält eine Fülle von Daten. Informationen darüber, wie Kundinnen und Kunden die Produkte auf Ihrer Site durchsuchen, anzeigen und schließlich kaufen, können Möglichkeiten aufzeigen, ein personalisierteres Einkaufserlebnis zu schaffen. Diese Daten können zwar native Commerce-Funktionen wie Warenkorbpreisregeln und dynamische Blöcke enthalten, die Daten bleiben jedoch in Ihrer Commerce-Instanz isoliert.

Der Adobe Experience Platform bietet eine Reihe von Technologien, die, wenn sie mit Daten aus Ihrem Commerce-Store hydriert sind, diese Daten über das Edge Network an andere Adobe-DX-Produkte verteilen können, um Einblicke in das Kaufverhalten Ihrer Kunden zu erschließen. Mit diesen tiefen Einblicken können Sie auf allen Kanälen ein personalisierteres Einkaufserlebnis schaffen.

Die folgende Abbildung zeigt, wie Ihre Commerce-Daten von Ihrem Store zu anderen Adobe DX-Produkten fließen, wenn die [!DNL Data Connection] installiert und konfiguriert ist.

![Datenfluss zum Experience Platform-Edge](assets/commerce-edge.png)

In der obigen Abbildung werden Ihre Verhaltens-, Back-Office- und Kundenprofildaten mithilfe einer SDK, einer API und eines Quell-Connectors an den Experience Platform-Edge gesendet. Sie müssen nicht vollständig verstehen, wie diese Teile funktionieren, da die Erweiterung die Komplexität der Datenfreigabe für Sie handhabt. Wenn die Ereignisdaten am Edge sind, können Sie diese Daten in andere Experience Platform-Anwendungen übertragen. Beispiel:

| Anwendung | Zweck | Anwendungsfälle |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=de) | Profil-Management und Segmentierungs-Service | **Segmentierung des Kaufverlaufs**: Händler können Kunden identifizieren, die einen Artikel über einen bestimmten Zeitraum kaufen (monatlich, vierteljährlich, jährlich usw.). Händler können dann Segmente für diese Kunden erstellen und sie auf Promotions, Kampagnen und _Trichterdaten)_ Leads für Abonnementdienste ausrichten<br> **Kategoriebasierte Segmentierung**: Händler können sehen, welche Produktkategorie gekauft wurde.<br> **Angebotsbasierte Segmentierung**: Händler können Kunden identifizieren, die konsequent Produkte zurückgeben. Die Angebote und Rabatte, die ihnen gegeben werden, können jetzt intelligenter sein. So kann beispielsweise der kostenlose Versand für einen Kunden entfernt werden, der Produkte die ganze Zeit zurückgibt.<br> **Lookalike-Targeting**: Eine _Lookalike-Zielgruppe_ ist eine Methode, die ein Händler für seine Werbeaktionen anwendet, um neue Personen zu erreichen, die wahrscheinlich an seinem Geschäft interessiert sind, weil sie ähnliche Merkmale wie Ihre bestehenden Kunden aufweisen. Lookalike-Segmente können auf der Grundlage von Verhaltens- und Transaktionsdaten erstellt werden.<br> **Kundentendenz**: Änderungen im Kundenverhalten können als Ergebnis der tieferen Kundenprofile identifiziert werden, die aus den Transaktionsdaten erstellt werden können. Das Vertrauen in den Neigungs-Score wird erhöht, da mehr Daten in die Berechnungen fließen, wie z. B. Produktrückgaben und Produktkonfigurationen.<br> **Crosssell**: Ein Händler kann anhand der in Commerce erfassten granularen Informationen starke Crosssell- und Upsell-Möglichkeiten erkennen. |
| [Kunde [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Detaillierte Analyse der vollständigen Commerce-Journey | **Saisonale Trends**: Ein Händler kann saisonale Trends identifizieren, was ihm hilft, sich auf die periodische Änderung der Nachfrage nach bestimmten Produkten vorzubereiten. Außerdem können Händler über Jahre hinweg Änderungen bei der allgemeinen Popularität jedes Produkts feststellen.<br> **Konversionsanalyse**: Indem Sie wissen, wann ein Produkt gekauft wurde, und gleichzeitig Zugriff auf Storefront-Impressionsereignisse haben, können Händler ein umfangreiches Kundenprofil erstellen, um Konversionsanalysen durchzuführen. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Detaillierte Analyse des Kundenverhaltens und der Kampagnenleistung | **Bestellrücksendungen**: Händler können Kunden und die größeren Kundensegmente identifizieren, die über ein Muster von zurückgegebenen Produkten verfügen. Dies hilft den Händlern, ihre Commerce-Strategie zu verbessern, da sie verstehen, wie das Verhalten ihres Kundenstamms aussieht.<br> **Bestelladresse**: Basierend auf der Lieferadresse kann ein Händler verstehen, ob die Bestellungen von den Kunden selbst aufgegeben werden oder ob es sich um eine andere Person oder Entität handelt.<br> **Saisonalität**: Ein Händler kann saisonale Trends identifizieren, was ihm hilft, sich auf die periodische Änderung der Nachfrage nach bestimmten Produkten vorzubereiten. Außerdem können Händler über Jahre hinweg Änderungen bei der allgemeinen Popularität jedes Produkts feststellen.<br> **Konversionsanalyse**: Indem Sie wissen, wann ein Produkt gekauft wurde, und gleichzeitig Zugriff auf Storefront-Impressionsereignisse haben, können Händler ein umfangreiches Kundenprofil erstellen, um Konversionsanalysen durchzuführen. **Hinweis** Adobe Analytics unterstützt nur verhaltensbezogene Ereignisdaten (Storefront). Adobe Analytics unterstützt keine Transaktionsereignisdaten (BackOffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Kampagnenorchestrierung über Kanäle hinweg | **Verhaltensbasierte Journey**: Händler können einen Kunden ansprechen, der vor zwei Jahren ein Mobiltelefon gekauft hat, indem sie ihm vorschlagen, das neue Modell zu kaufen. Händler können für diese Kunden personalisierte Kampagnen und Angebote erstellen und E-Mail- und SMS-Funktionen verwenden, um sich zu melden. Außerdem können Händler historische Bestell- und Verhaltensdaten verwenden, um Trends zu identifizieren. Wenn beispielsweise ein Kunde, der in der Vergangenheit einen Artikel mit einer bestimmten Konfiguration gekauft hat und jetzt dasselbe Produkt erneut kaufen möchte, kann seine Kauf-Journey verbessert werden, indem er ihnen Einblick und Zugriff auf dieselben Produktkonfigurationen gewährt.<br> **Personalization**: Mit dem Zugriff auf Kundenprofilinformationen können [!DNL Journey Optimizer] hochgradig personalisierte Journey freischalten, sodass Händler über mehrere verschiedene Kanäle mit den Kunden in Kontakt treten können.<br> **Neues Profil erstellt**: Begrüßungs-E-Mails und Werbeaktivitäten können neue Kunden in ihren Shopping-Journey ermutigen und beeinflussen.<br> **Profil gelöscht**: Händler können festlegen, keine Werbe-E-Mails mehr an Kunden zu senden, die ihr Konto geschlossen haben. Alternativ können Händler auch Kampagnen erstellen, um verlorene Kunden zurückzugewinnen. |

## Experience Platform-Daten zurück in Commerce ziehen

Das Senden Ihrer Commerce-Daten mit der [!DNL Data Connection]-Erweiterung an den Experience Platform ist eine Seite der Datenfreigabefunktionen von Commerce. Die andere Seite, bei der es sich um eine optionale Erweiterung handelt, heißt [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Mit dieser Erweiterung können Sie Zielgruppen in Real-Time CDP erstellen und diese Zielgruppen in Ihrem Commerce-Store bereitstellen, um über Warenkorbpreisregeln, zugehörige Produktregeln und dynamische Blöcke zu informieren.

Der Datenfluss von Ihrem Commerce-Store zum Experience Platform und zurück über die Audience Activation-Erweiterung sieht im Großen und Ganzen wie folgt aus:

![[!DNL Data Connection] Fluss](assets/data-connection.png)

Nachdem Sie die Verbindung zwischen Commerce zu Experience Platform und Experience Platform zu Commerce eingerichtet haben, fließen die Daten weiter. Sie müssen die Verbindung nicht erneut herstellen, es sei denn, dies wird durch ein Upgrade erforderlich.

## Konzepte

Für die Datenfreigabe zwischen diesen beiden Systemen müssen Sie mehrere Konzepte verstehen.

- **Daten** - Die Daten, die für die Experience Platform freigegeben werden, sind Daten, die von Browser-Ereignissen in Ihrer Storefront, Back-Office-Ereignissen auf dem Server und Profildatensatzdaten erfasst wurden. Storefront-Ereignisse werden aus den Interaktionen von Käufern auf der Website erfasst und umfassen Ereignisse wie [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout) usw. Siehe [Storefront-Ereignisse](events.md#storefront-events) für die vollständige Liste der Storefront-Ereignisse. Server-seitige oder Back-Office-Ereignisse umfassen [Bestellstatus](events-backoffice.md#order-status) Informationen wie [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled) usw. Siehe [Backoffice-Ereignisse](events-backoffice.md) für die vollständige Liste der Backoffice-Ereignisse. Profildatensatzdaten enthalten Informationen, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird. Weitere Informationen [ Sie unter ](events-profilerecord.md) von Profildatensätzen .

- **Experience Platform und Edge Network** - Das Data Warehouse für die meisten Adobe DX-Produkte. Daten, die an den Experience Platform gesendet werden, werden über das Experience Platform-Edge Network auf Adobe DX-Produkte übertragen. Sie können beispielsweise Journey Optimizer starten, Ihre spezifischen Commerce-Ereignisdaten vom Edge abrufen und in Journey Optimizer eine E-Mail zu einem Transaktionsabbruch erstellen. Journey Optimizer kann diese E-Mail dann senden, wenn sich im Commerce-Store Transaktionsabbrüche befinden. Weitere Informationen über die [Experience Platform und das Edge Network ](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

- **Schema** - Das Schema beschreibt die Struktur der gesendeten Daten. Bevor Experience Platform Ihre Commerce-Daten aufnehmen kann, müssen Sie ein Schema erstellen, das die Datenstruktur beschreibt und Einschränkungen für den Datentyp bereitstellt, der in den einzelnen Feldern enthalten sein kann. Schemata bestehen aus einer Basisklasse und keiner oder mehreren Schemafeldgruppen. Das Schema verwendet die XDM-Struktur, die alle Adobe-DX-Produkte lesen können. Das Schema stellt sicher, dass die an den Experience Platform gesendeten Daten in allen DX-Produkten verstanden werden. Weitere Informationen zu [Schemata](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

- **Dataset** - Ein Konstrukt zur Speicherung und Verwaltung von Daten, normalerweise eine Tabelle, die ein Schema (Spalten) und Felder (Zeilen) enthält. Datensätze enthalten auch Metadaten, die verschiedene Aspekte der in ihnen gespeicherten Daten beschreiben. Alle Daten, die erfolgreich in Adobe Experience Platform aufgenommen werden, sind in Datensätzen enthalten. Weitere Informationen zu [Datensätzen](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

- **Datastream** - ID, die den Datenfluss von Adobe Experience Platform zu anderen Adobe DX-Produkten ermöglicht. Diese ID muss mit einer bestimmten Website innerhalb Ihrer spezifischen Adobe Commerce-Instanz verknüpft sein. Wenn Sie diesen Datenstrom erstellen, geben Sie das oben erstellte XDM-Schema an. Weitere Informationen zu [Datenströmen](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Unterstützte Architektur

Die [!DNL Data Connection]-Erweiterung ist auf den folgenden Architekturen verfügbar:

- PHP/Luma
- [PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
- [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

>[!BEGINSHADEBOX]

## Voraussetzungen

Um die [!DNL Data Connection]-Erweiterung verwenden zu können, müssen Sie über Folgendes verfügen:

- Adobe Commerce 2.4.4 oder neuer
- Adobe ID und Organisations-ID
- [Adobe-Client-Datenschicht (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html) die zum Erfassen von Storefront-Ereignisdaten erforderlich ist
- Berechtigungen für andere Adobe DX-Produkte.

>[!ENDSHADEBOX]

## Onboarding-Schritte

Die Aktivierung der [!DNL Data Connection]-Erweiterung umfasst auf allgemeiner Ebene die folgenden Schritte:

1. [Installieren](install.md) der [!DNL Data Connection].
1. [Melden Sie sich ](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Ihrem Adobe-Konto an und [ Sie Ihre Organisations-ID ](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255)Ansicht zur Bestätigung anzeigen). Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von `@AdobeOrg` (zwingend erforderlich).
1. Stellen Sie sicher[ dass Sie über die Berechtigung für die Datenerfassung in Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. Überprüfen Sie die [Datentypen](data-ingestion.md) die Sie erfassen und senden können.
1. Erstellen oder aktualisieren Sie Ihr [Zeitreihen](update-xdm.md)Ereignisschema oder [Profildatensatzdatenschema](profile-data.md) mit Commerce-spezifischen Feldergruppen.
1. [Erstellen eines Datensatzes](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die Commerce-Daten, die an die Experience Platform Edge gesendet werden.
1. [Erstellen Sie einen Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
1. [Verbindung zu Commerce Services herstellen](../landing/saas.md).
1. [Verbindung zu Adobe Experience Platform herstellen](connect-data.md).

Der Rest dieses Handbuchs führt Sie durch alle diese Schritte, damit Sie sich auf den neuesten Stand bringen und die Leistungsfähigkeit von Adobe DX-Produkten in Ihrem Commerce-Store nutzen können.

>[!NOTE]
>
>Entwickler von Mobilgeräten erfahren, wie [ Adobe Experience Platform Mobile SDK ](./mobile-sdk-epc.md) Commerce integrieren.

## HIPAA-Bereitschaft

Mit der [!DNL Data Connection]-Erweiterung können Sie [!DNL Commerce] Back-Office-Daten mit der Experience Platform austauschen und die HIPAA-Konformität aufrechterhalten. [Weitere Informationen](hipaa-readiness.md).

## Zielgruppe

Dieses Handbuch richtet sich an Händler in Adobe Commerce, die ihren Commerce-Store erweitern und personalisieren möchten, um ihren Kunden ein noch besseres Einkaufserlebnis zu bieten.

## Support

Wenn Sie Informationen benötigen oder Fragen haben, die in diesem Handbuch nicht behandelt werden, verwenden Sie die folgenden Ressourcen:

- [Hilfezentrum](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Support-](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: Senden Sie ein Ticket, um zusätzliche Hilfe zu erhalten.
