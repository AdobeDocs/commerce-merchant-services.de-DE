---
title: Entwicklung von Recommendations-Administratoren
description: Eine Übersicht über die Architektur und Entwicklungsfunktionen von Recommendations.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Entwicklung von Recommendations-Administratoren

Product Recommendations ist ein leistungsstarkes Marketing-Tool, mit dem Sie Konversionen steigern, den Umsatz steigern und die Interaktion mit Kunden fördern können. Produkt-Recommendations wird auf der Storefront in Form von Einheiten wie &quot;Kunden, die dieses Produkt angesehen haben, haben auch angesehen&quot;, &quot;Kunden, die dieses Produkt gekauft haben, haben auch gekauft&quot;, &quot;Für Sie empfohlen&quot;usw. angezeigt. Adobe Commerce Product Recommendations basiert auf [Adobe Sensei](https://www.adobe.com/sensei.html), das künstliche Intelligenz und Algorithmen für maschinelles Lernen verwendet, um eine tiefgehende Analyse aggregierter Kundendaten durchzuführen. Diese Daten führen in Kombination mit Ihrem Commerce-Katalog zu sehr ansprechenden, relevanten und personalisierten Erlebnissen für den Käufer.

>[!NOTE]
>
>Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie den Abschnitt [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie im Benutzerhandbuch , wie Sie Product Recommendations in eine [Headless](headless.md) Umgebung.

## Architektonischer Überblick

Auf hoher Ebene werden Commerce Product Recommendations als SaaS bereitgestellt. Die Commerce-Seite enthält die Storefront mit der Vorlage für den Event-Wächter und das Recommendations-Layout sowie das Backend, das das Data Services-, SaaS-Export- und die Admin-Benutzeroberfläche umfasst. Adobe Sensei-Nachrichtendienste werden auf der SaaS-Seite genutzt.

![Architekturdiagramm für Produktempfehlungen](assets/arch-diag-sensei.svg)

Sobald die Empfehlungsmodule installiert und konfiguriert sind, beginnt Ihre Storefront mit der Erfassung von Verhaltensdaten. Adobe Sensei verarbeitet diese Verhaltensdaten zusammen mit Ihren Katalogdaten und berechnet Produktzuordnungen, die vom Recommendations-Dienst genutzt werden. An dieser Stelle kann der Händler Produktempfehlungseinheiten direkt über die Admin-Benutzeroberfläche für sein Storefront erstellen, verwalten und bereitstellen.

## Datentypen

Für Produkt-Recommendations sind die folgenden Daten erforderlich:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, zu einem Warenkorb hinzugefügte Artikel und Käufe. Commerce und Adobe Sensei erfassen keine personenbezogenen Daten.

- **Katalog** - Produktmetadaten wie Name, Preis, Verfügbarkeit usw.

Wenn Sie die `magento/product-recommendations` -Modul aggregiert Adobe Sensei die Verhaltens- und Katalogdaten und erstellt so für jeden Empfehlungstyp eine Produkt-Recommendations. Der Product Recommendations-Dienst stellt diese Empfehlungen dann in Ihrem Storefront bereit.

## Nächste Schritte

Lesen Sie die folgenden Themen, um mit Product Recommendations zu beginnen:

- [Implementieren von Recommendations](implementation-workflow.md)

- [Installieren und Konfigurieren von Product Recommendations](install-configure.md)

- [Produkt-Recommendations erstellen](create.md)
