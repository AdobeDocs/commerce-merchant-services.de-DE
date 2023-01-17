---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] für Adobe Commerce bietet eine Möglichkeit, den Inhalt von Produktansichtsseiten und Produktlistenseiten viel schneller abzurufen als die nativen Adobe Commerce GraphQL-Abfragen."'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 489de0f56cba06620c334e2b17040b32a72968ef
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---

# [!DNL Catalog Service] für Adobe Commerce

Die [!DNL Catalog Service] für die Adobe Commerce-Erweiterung bietet Rich-View-Modell-Katalogdaten (schreibgeschützt), um produktbezogene Storefront-Erlebnisse schnell und vollständig zu rendern, darunter:

* Produktdetailseiten
* Produktlisten- und Kategorieseiten
* Suchergebnisseiten
* Karusselle
* Produktvergleichsseiten
* Alle anderen Seiten, die Produktdaten rendern, wie z. B. Warenkorb-, Bestell- und Wunschlistenseiten

Die [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) , um Produktdaten anzufordern und zu empfangen. GraphQL ist eine Abfragesprache, die ein Frontend-Client verwendet, um mit der in einem Backend wie Adobe Commerce definierten Anwendungsprogrammierschnittstelle (API) zu kommunizieren. GraphQL ist eine beliebte Kommunikationsmethode, da es einfach ist und es einem Systemintegrator ermöglicht, den Inhalt und die Reihenfolge jeder Antwort anzugeben.

Adobe Commerce verfügt über zwei GraphQL-Systeme. Das GraphQL-Kernsystem bietet eine breite Palette von Abfragen (Lese-Vorgänge) und Mutationen (Schreibvorgänge), mit denen ein Käufer mit vielen Seitentypen interagieren kann, darunter Produkt, Kundenkonto, Warenkorb, Checkout und mehr. Die Abfragen, die Produktinformationen zurückgeben, sind jedoch nicht für die Geschwindigkeit optimiert. Das GraphQL-System für Dienste kann nur Abfragen zu Produkten und zugehörigen Informationen durchführen. Diese Abfragen sind leistungsfähiger als ähnliche Core-Abfragen.

Sie führen diese Abfragen aus, indem Sie sie an das Gateway unter https://catalog-service.adobe.io/graphql senden.

## Architektur

Das folgende Diagramm zeigt die beiden GraphQL-Systeme:

![Katalogarchitekturdiagramm](assets/catalog-service-architecture.png)

Im Core-GraphQL-System sendet die PWA eine Anfrage an die Commerce-Anwendung, die jede Anfrage empfängt, verarbeitet sie, möglicherweise eine Anfrage über mehrere Subsysteme sendet und dann eine Antwort an die Storefront zurückgibt. Dieser Rundgang kann zu langsamen Seitenladezeiten führen, was möglicherweise zu niedrigeren Konversionsraten führt.

[!DNL Catalog Service] ist ein Storefront Services Gateway. Der Dienst greift auf eine separate Datenbank zu, die Produktdetails und zugehörige Informationen wie Produktattribute, Varianten, Preise und Kategorien enthält. Der Dienst synchronisiert die Datenbank durch Indexierung mit der Adobe Commerce.
Da der Dienst die direkte Kommunikation mit der Anwendung umgeht, kann er die Latenz des Anforderungs- und Antwortzyklus reduzieren.

>[!NOTE]
>
>Das Gateway dient der zukünftigen Integration mit Product Recommendations. In dieser Version können Sie auf die [!DNL Catalog Service GraphQL] und [!DNL Live Search] Abfragen vom selben Endpunkt aus, wenn Sie einen gültigen Lizenzschlüssel für beide Produkte haben.

Die Core- und Service-GraphQL-Systeme kommunizieren nicht direkt miteinander. Sie greifen von einer anderen URL auf jedes System zu und Aufrufe erfordern unterschiedliche Kopfzeileninformationen. Die beiden GraphQL-Systeme sind für die gemeinsame Nutzung konzipiert. Die [!DNL Catalog Service] Das GraphQL-System erweitert das Kernsystem um schnellere Produkterlebnisse.

Sie können optional [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) Integration der beiden Adobe Commerce GraphQL-Systeme in private und Drittanbieter-APIs und andere Softwareschnittstellen mithilfe von Adobe Developer. Das Gitter kann so konfiguriert werden, dass an jeden Endpunkt gesendete Aufrufe die richtigen Autorisierungsinformationen in den Kopfzeilen enthalten.

## Architektonische Details

In den folgenden Abschnitten werden einige der Unterschiede zwischen den beiden GraphQL-Systemen beschrieben.

### Schema-Verwaltung

Da Catalog Service als Dienst fungiert, müssen sich Integratoren nicht um die zugrunde liegende Version von Commerce kümmern. Die Syntax der Abfragen ist für alle Versionen identisch. Darüber hinaus ist das Schema für alle Händler konsistent. Diese Konsistenz erleichtert die Einrichtung von Best Practices und die deutliche Erhöhung der Wiederverwendung von Storefront-Widgets.

### Vereinfachung der Warentypen

Das Schema reduziert die Vielfalt der Produktarten auf zwei Anwendungsfälle:

* Einfache Produkte sind Produkte, die mit einem einzigen Preis und einer einzigen Menge definiert sind. Catalog Service ordnet die einfachen, virtuellen, herunterladbaren und Geschenkkarten-Produktarten zu `simpleProductViews`.

* Komplexe Produkte bestehen aus mehreren einfachen Produkten. Die Komponenten einfache Produkte können unterschiedliche Preise haben. Ein komplexes Produkt kann auch so definiert werden, dass der Käufer die Menge an Komponenten für einfache Produkte angeben kann. Catalog Service ordnet die konfigurierbaren, Bundle- und gruppierten Produktarten zu `complexProductViews`.

Komplexe Produktoptionen sind vereinheitlicht und unterscheiden sich durch ihr Verhalten, nicht durch ihren Typ. Jeder Optionswert stellt ein einfaches Produkt dar. Dieser Optionswert hat Zugriff auf die einfachen Produktattribute, einschließlich Preis. Wenn der Käufer alle Optionen für ein komplexes Produkt auswählt, verweist die Kombination der ausgewählten Optionen auf ein bestimmtes einfaches Produkt. Das einfache Produkt bleibt mehrdeutig, bis der Käufer einen Wert für alle verfügbaren Optionen auswählt.

### Preise

Einfache Produkte stellen die Basis-Verkaufseinheit dar, die einen Preis hat. Catalog Service berechnet den regulären Preis vor Rabatten sowie den Endpreis nach Rabatten. Preisberechnungen können feste Produktsteuern enthalten. Sie schließen personalisierte Promotions aus.

Ein komplexes Produkt hat keinen festgelegten Preis. Stattdessen gibt Catalog Service die Preise verknüpfter Simples zurück. Beispielsweise kann ein Händler zunächst allen Varianten eines konfigurierbaren Produkts dieselben Preise zuweisen. Wenn bestimmte Größen oder Farben unbeliebt sind, kann der Händler die Preise dieser Varianten reduzieren. So zeigt der Preis des komplexen (konfigurierbaren) Produkts zunächst eine Preisspanne, die den Preis sowohl von Standard- als auch von unpopulären Varianten widerspiegelt. Nachdem der Käufer einen Wert für alle verfügbaren Optionen ausgewählt hat, zeigt die Storefront einen einzelnen Preis an.

## Implementierung

Der Installationsprozess erfordert die Konfiguration der [Commerce Services Connector](../landing/saas.md). Sobald dies erreicht ist, muss ein Systemintegrator den Storefront-Code aktualisieren, um die [!DNL Catalog Service] Abfragen. Alle [!DNL Catalog Service] -Abfragen werden an das GraphQL-Gateway weitergeleitet. Die URL wird während des Onboarding-Prozesses bereitgestellt.
