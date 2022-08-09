---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] für Adobe Commerce bietet eine Möglichkeit, die Inhalte von Produktansichtsseiten und Produktlistenseiten viel schneller abzurufen als die nativen Adobe Commerce GraphQL-Abfragen."'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# [!DNL Catalog Service] für Adobe Commerce

{{catalog-service-beta}}

Die [!DNL Catalog Service] für die Adobe Commerce-Erweiterung bietet Rich-View-Modell-Katalogdaten (schreibgeschützt), um produktbezogene Storefront-Erlebnisse schnell und vollständig zu rendern, darunter:

* Produktdetailseiten
* Produktlisten- und Kategorieseiten
* Suchergebnisseiten
* Karusselle
* Produktvergleichsseiten
* Alle anderen Seiten, die Produktdaten rendern, wie z. B. Warenkorb-, Bestell- und Wunschlistenseiten

Die [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) , um Produktdaten anzufordern und zu empfangen. GraphQL ist eine Abfragesprache, die ein Frontend-Client verwendet, um mit der in einem Backend wie Adobe Commerce definierten Anwendungsprogrammierschnittstelle (API) zu kommunizieren. GraphQL ist eine beliebte Kommunikationsmethode, da sie einfach ist und es einem Systemintegrator ermöglicht, den Inhalt und die Reihenfolge jeder Antwort anzugeben.

Adobe Commerce verfügt über zwei GraphQL-Systeme. Das GraphQL-Kernsystem bietet eine Vielzahl von Abfragen (Lesevorgänge) und Mutationen (Schreibvorgänge), die es einem Käufer ermöglichen, mit vielen Arten von Seiten zu interagieren, darunter Produkt, Kundenkonto, Warenkorb, Checkout und mehr. Die Abfragen, die Produktinformationen zurückgeben, sind jedoch nicht für die Geschwindigkeit optimiert. Das GraphQL-System der Dienste kann nur Abfragen zu Produkten und zugehörigen Informationen durchführen. Diese Abfragen sind leistungsfähiger als ähnliche Core-Abfragen.

## Architektur

Das folgende Diagramm zeigt die beiden GraphQL-Systeme:

![Katalogarchitekturdiagramm](assets/catalog-service-architecture.png)

Im Core-GraphQL-System sendet die PWA eine Anfrage an die Commerce-Anwendung, die jede Anfrage empfängt, verarbeitet sie, möglicherweise eine Anfrage über mehrere Subsysteme sendet und dann eine Antwort an die Storefront zurückgibt. Dieser Rundgang kann zu langsamen Seitenladezeiten führen, was möglicherweise zu niedrigeren Konversionsraten führt.

[!DNL Catalog Service] sendet Abfragen an ein separates GraphQL-Gateway. Der Dienst greift auf eine separate Datenbank zu, die Produktdetails und zugehörige Informationen wie Produktattribute, Varianten, Preise und Kategorien enthält. Der Dienst synchronisiert die Datenbank durch Indexierung mit der Adobe Commerce.
Da der Dienst die direkte Kommunikation mit der Anwendung umgeht, kann er die Latenz des Anforderungs- und Antwortzyklus reduzieren.

>[!NOTE]
>
>Das Gateway dient der zukünftigen Integration mit [!DNL Live Search] und [!DNL Product Recommendations]. In dieser Version können Sie auf [!DNL Catalog Service] und Live-Suchabfragen vom selben Endpunkt, wenn Sie einen gültigen Lizenzschlüssel für beide Produkte haben. Die Abfragen der beiden Produkte enthalten jedoch derzeit keine Antwortdaten.

Die Core- und Service-GraphQL-Systeme kommunizieren nicht direkt miteinander. Sie greifen von einer anderen URL auf jedes System zu und Aufrufe erfordern unterschiedliche Kopfzeileninformationen. Die beiden GraphQL-Systeme sind für die gemeinsame Verwendung konzipiert. Die [!DNL Catalog Service] Das GraphQL-System erweitert das Kernsystem, um die Erlebnisse im Produkt-Storefront zu beschleunigen.

Sie können optional [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) zur Integration der beiden Adobe Commerce GraphQL-Systeme mit privaten und Drittanbieter-APIs und anderen Softwareschnittstellen über Adobe Developer. Das Gitter kann so konfiguriert werden, dass an jeden Endpunkt gesendete Aufrufe die richtigen Autorisierungsinformationen in den Kopfzeilen enthalten.

## Implementierung

Der Installationsprozess erfordert die Konfiguration der [Commerce Services Connector](../landing/saas.md). Sobald dies erreicht ist, muss ein Systemintegrator den Storefront-Code aktualisieren, um die [!DNL Catalog Service] Abfragen. Alle [!DNL Catalog Service] -Abfragen werden an das GraphQL-Gateway weitergeleitet. Die URL wird während des Onboarding-Prozesses bereitgestellt.

[Adobe Commerce-Geräte](https://devdocs.magento.com/catalog-service/index.html) beschreibt die Unterschiede zwischen dem Kern und [!DNL Catalog Service] Abfragen. Referenzinformationen für jede Abfrage werden ebenfalls hinzugefügt.
