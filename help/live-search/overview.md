---
title: Einführung in [!DNL Live Search]
description: "[!DNL Live Search] Adobe Commerce bietet ein blitzschnelles, superrelevantes und intuitives Sucherlebnis."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 9460d7cf2de677557ee3792665c65d2a52a52569
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Einführung in [!DNL Live Search]

[!DNL Live Search] ist ein Dienst für Adobe Commerce, der die standardmäßigen Suchfunktionen ersetzt. Die [!DNL Live Search] -Modul mit Composer installiert und verbindet Ihre [!DNL Commerce] -Installation [!DNL Live Search] [service](../landing/saas.md). Wenn es konfiguriert ist, wird das standardmäßige Suchtextfeld durch das [!DNL Live Search] Textfeld. [!DNL Live Search] installiert außerdem das Widget Product Listing Page (PLP) , das beim Durchsuchen von Suchergebnissen zuverlässige Filterfunktionen bietet.

[!DNL Live Search] wird auf der *Marketing* Menü unter *SEO und Suche* im [!DNL Commerce] *Admin*.

Die Adobe Commerce-Seite der Architektur umfasst das Hosten der Suche *Admin*, Synchronisieren Sie Katalogdaten und führen Sie den Abfragedienst aus. Nachher [!DNL Live Search] installiert und konfiguriert ist, beginnt Adobe Commerce mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Administratoren die Suche einrichten, anpassen und verwalten [facets](facets.md), [Synonyme](synonyms.md), und [Merchandisingregeln](category-merch.md).

## Live Search-Komponenten

* [!DNL Live Search] [Popover-Widget](storefront-popover.md) ist das Feld, das unter dem Suchfeld geöffnet wird, das die Suchergebnisse enthält.
* [Widget &quot;Seite für Produktauflistung&quot;](plp-styling.md) bietet eine durchsuchbare Produktlistenseite mit Facetten- und Synonym-Unterstützung.
* AEM CIF Komponenten: Die [Popover-Widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) und [PLP-Widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) ermöglichen es AEM Sites, von [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) ist der Ort, an dem Regeln, Facetten und Synonyme konfiguriert werden.

## Workflow-Übersicht

[!DNL Live Search] funktioniert durch Verschieben von Katalogdaten in die SaaS-Infrastruktur von Adobe Commerce und Erstellen von Indizes, die für die schnelle Bereitstellung von Suchergebnissen als Benutzertyp verwendet werden.

### 1. Installation

[!DNL Live Search] is [installiert](install.md) in die Adobe Commerce-Instanz über [Verfasser](https://getcomposer.org/). Dadurch werden die erforderlichen Module installiert, die eine Verbindung zum Dienst herstellen, und die Commerce-Instanz so konfiguriert, dass das Standardsuchfeld außer Kraft gesetzt wird. Außerdem werden Commerce Admin-Optionen zum Konfigurieren des Dienstes installiert.

### 2. Synchronisieren von Daten

[!DNL Live Search] verschiebt Katalogdaten in die Adobe SaaS-Infrastruktur. Die Daten werden indiziert und die Suchergebnisse werden von diesem Index direkt an die Storefront übermittelt. Je nach Größe und Komplexität kann die Indizierung zwischen 30 Minuten und einigen Stunden dauern.

### 3. Konfigurieren von Daten

Durch die korrekte Konfiguration Ihrer Produktdaten werden gute Suchergebnisse für Ihre Kunden sichergestellt. Es sind einige Einrichtungsschritte erforderlich: Zuweisen von Kategorien und Konfigurieren von Attributen.

#### Zuweisen von Kategorien

Produkt zurückgegeben in [!DNL Live Search] muss eine [category](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). In Luma beispielsweise werden Produkte in Kategorien wie &quot;Männer&quot;, &quot;Frauen&quot;und &quot;Zahnrad&quot;unterteilt. Unterkategorien sind auch &quot;Tops&quot;, &quot;Bottom&quot; und &quot;Watches&quot;. Dies ermöglicht eine bessere Granularität beim Filtern.

#### Durchsuchbare und filterbare Felder

Produkte werden zugewiesen [attributes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) die für die Suche und Filterung verwendet werden können. Attribute sind Dinge wie &quot;Farbe&quot;, &quot;Größe&quot;, &quot;Materialtyp&quot;. Mit diesen Attributen können Benutzer nach &quot;grünen Spitzen&quot;suchen. Jedes Produkt kann über viele Attribute verfügen, die im Commerce-Administrator definiert sind.

Jedes dieser Attribute kann als [&quot;searchable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) im Admin. Wenn diese Attribute als &quot;durchsuchbar&quot;festgelegt sind, können sie von [!DNL Live Search].

[Facets](facets.md) sind Produktattribute, die in [!DNL Live Search] gefilterbar sein. Jedes filterbare Attribut kann als Facette in [!DNL Live Search] Es gibt jedoch Einschränkungen dafür, wie viele Facetten gleichzeitig durchsucht werden können.

[Synonyme](synonyms.md) sind Begriffe, die Sie definieren können, um Benutzer zum richtigen Produkt zu führen. Benutzer, die nach Hosen suchen, können &quot;Hosen&quot;oder &quot;Schläge&quot;eingeben. Sie können Synonyme festlegen, sodass diese Suchbegriffe Benutzer zu den Ergebnissen der &quot;Hosen&quot;führen.

## [!DNL Live Search] Arbeitsbereich

Die [!DNL Live Search] [Arbeitsbereich](workspace.md) ist der Bereich im Amin, in dem Sie konfigurieren [!DNL Live Search] Funktionen wie Synonyme, Facetten und Kategorie-Merchandising.

## Veranstaltungen

[!DNL Live Search] uses [events](events.md) berechnet [Intelligente Merchandising](category-merch.md) und [Leistung](performance.md) Dashboards. Eventing wird mit Standardimplementierungen bereitgestellt. Eventing für Headless-Storefronts sollte manuell aktiviert werden.

## Anpassen von Widgets

Die meisten Store-Eigentümer möchten sicherstellen, dass die [!DNL Live Search] Widgets entsprechen ihrem Erscheinungsbild im Geschäft.

Die Popover- und PLP-Widgets können formatiert werden, indem benutzerdefinierte CSS-Regeln nach Bedarf definiert werden. Siehe [Formatieren von Popover-Elementen](storefront-popover-styling.md) und [Seiten-Widget &quot;Produktliste&quot;](plp-styling.md).

Wenn Sie die Funktionalität der Widgets erweitern möchten, ist der Quellcode für jedes in einem öffentlichen Repository verfügbar.
In diesem Szenario können Sie das JavaScript an Ihre eigenen Anforderungen anpassen und dann Ihren benutzerdefinierten Code auf Ihrer Site hosten. Dieses benutzerdefinierte Skript kommuniziert mit dem [!DNL Live Search] und gibt die Ergebnisse wie normal zurück, sodass Sie die Funktionalität des Widgets steuern können.

* [PLP-Widget-Repo](https://github.com/adobe/storefront-product-listing-page)
* [Suchleistensymbol](https://github.com/adobe/storefront-search-as-you-type)

Weitere Informationen finden Sie unter [!DNL Live Search] im [Technischer Überblick](technical-overview.md).

## [!DNL Live Search] Demo

In diesem Video erfahren Sie mehr über [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Ein detaillierteres Video zur Verwendung und Konfiguration der Live-Suche finden Sie unter [Vollständige Demonstration auf [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) Thema.
