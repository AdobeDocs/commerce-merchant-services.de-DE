---
title: Entwicklung von Recommendations-Administratoren
description: Eine Übersicht über die Architektur und Entwicklungsfunktionen von Product Recommendations.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Entwicklung von Recommendations-Administratoren

Product Recommendations ist ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, den Umsatz steigern und die Interaktion mit Kunden fördern können. Produkt-Recommendations wird auf der Storefront in Form von Einheiten wie &quot;Kunden, die dieses Produkt angesehen haben, haben auch angesehen&quot;, &quot;Kunden, die dieses Produkt gekauft haben, haben auch gekauft&quot;, &quot;Für Sie empfohlen&quot;usw. angezeigt. Adobe Commerce Product Recommendations basiert auf [Adobe Sensei](https://www.adobe.com/sensei.html), das künstliche Intelligenz und Algorithmen des maschinellen Lernens verwendet, um eine tiefgehende Analyse aggregierter Kundendaten durchzuführen. Diese Daten führen in Kombination mit Ihrem Commerce-Katalog zu sehr ansprechenden, relevanten und personalisierten Erlebnissen für den Käufer.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie den Abschnitt [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie im Benutzerhandbuch , wie Sie Product Recommendations in eine [Headless](headless.md) Umgebung. Headless-Instanzen müssen Eventing implementieren, um den Arbeitsbereich &quot;Produktempfehlungen&quot;zu erweitern.

## Architektonischer Überblick

Auf hoher Ebene werden Commerce Product Recommendations als SaaS bereitgestellt. Die Commerce-Seite enthält die Storefront mit der Vorlage für den Event-Wächter und das Recommendations-Layout sowie das Backend, das das Data Services-, SaaS-Export- und die Admin-Benutzeroberfläche umfasst. Adobe Sensei-Nachrichtendienste werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe Sensei verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktzuordnungen, die vom Recommendations-Dienst genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für sein Storefront erstellen, verwalten und bereitstellen.

## Datentypen

Für Produkt-Recommendations sind die folgenden Daten erforderlich:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, zu einem Warenkorb hinzugefügte Artikel und Käufe. Commerce und Adobe Sensei erfassen keine personenbezogenen Daten.

- **Katalog** - Produktmetadaten wie Name, Preis, Verfügbarkeit usw.

Wenn Sie die `magento/product-recommendations` -Modul aggregiert Adobe Sensei die Verhaltens- und Katalogdaten und erstellt so für jeden Empfehlungstyp eine Produkt-Recommendations. Der Product Recommendations-Dienst stellt diese Empfehlungen dann in Ihrem Storefront bereit.

>[!NOTE]
>
>Für konfigurierbare Produkte verwendet Product Recommendations das Bild des übergeordneten Produkts in der Empfehlungseinheit. Wenn für das konfigurierbare Produkt kein Bild angegeben ist, ist die Empfehlungseinheit für dieses bestimmte Produkt leer.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Product Recommendations zu beginnen:

- [Implementieren von Recommendations](implementation-workflow.md)

- [Installieren und Konfigurieren von Product Recommendations](install-configure.md)

- [Produkt-Recommendations erstellen](create.md)
