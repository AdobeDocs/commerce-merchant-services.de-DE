---
title: Produktentwicklung für Recommendations-Admins
description: Ein Überblick über die Architektur und Entwicklungsfunktionen von Recommendations für Produkte.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Produktentwicklung für Recommendations-Admins

Product Recommendations ist ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, Umsätze steigern und die Kundenbindung steigern können. Produkt-Recommendations werden in der Storefront in Form von Einheiten wie „Kunden, die dieses Produkt angesehen haben, haben es auch angesehen“, „Kunden, die dieses Produkt gekauft haben, haben auch gekauft“, „Empfohlen für Sie“ usw. angezeigt. Adobe Commerce Product Recommendations basiert auf [Adobe Sensei](https://www.adobe.com/sensei.html), das Algorithmen für künstliche Intelligenz und maschinelles Lernen verwendet, um eine gründliche Analyse aggregierter Kundendaten durchzuführen. Wenn diese Daten mit Ihrem Commerce-Katalog kombiniert werden, ergeben sich für den Erstkäufer sehr ansprechende, relevante und personalisierte Erlebnisse.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert wird, lesen Sie die [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, lesen Sie das Benutzerhandbuch , um zu erfahren, wie Sie Produkt-Recommendations in eine &quot;[&quot;-](headless.md) integrieren. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich Produktempfehlungen zu unterstützen.

## Architektonischer Überblick

Commerce Product Recommendations wird allgemein als SaaS bereitgestellt. Auf der Commerce-Seite befindet sich die Storefront, die die Layout-Vorlage „Event Collector“ und „Recommendations“ enthält, und das Backend, das die Daten-Services, das SaaS-Exportmodul und die Admin-Benutzeroberfläche umfasst. Adobe Sensei Intelligence-Services werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe Sensei verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktverknüpfungen, die vom Recommendations-Service genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für seine Storefront erstellen, verwalten und bereitstellen.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit der Produkt-Recommendations zu beginnen:

- [Implementieren von Produkt-Recommendations](implementation-workflow.md)

- [Installieren und Konfigurieren von Recommendations](install-configure.md)

- [Produkt-Recommendations erstellen](create.md)
