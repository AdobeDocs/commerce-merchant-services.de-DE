---
title: Einführung in [!DNL Live Search]
description: "[!DNL Live Search] Adobe Commerce bietet ein blitzschnelles, superrelevantes und intuitives Sucherlebnis."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 4eddad715405f35ea063bab3cf4651fec3beeae5
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Einführung in [!DNL Live Search]

[!DNL Live Search] ist ein Dienst für Adobe Commerce, der die standardmäßigen Suchfunktionen ersetzt. Die [!DNL Live Search] -Modul mit Composer installiert und verbindet Ihre [!DNL Commerce] -Installation [!DNL Live Search] [service](../landing/saas.md). Wenn es konfiguriert ist, wird das standardmäßige Suchtextfeld durch das [!DNL Live Search] Textfeld.

[!DNL Live Search] wird auf der *Marketing* Menü unter *SEO und Suche* im [!DNL Commerce] *Admin*.

Die Adobe Commerce-Seite der Architektur umfasst das Hosten der Suche *Admin*, Synchronisieren Sie Katalogdaten und führen Sie den Abfragedienst aus. Nachher [!DNL Live Search] installiert und konfiguriert ist, beginnt Adobe Commerce mit der Freigabe von Such- und Katalogdaten für SaaS-Dienste. An dieser Stelle können Administratoren die Suche einrichten, anpassen und verwalten [facets](facets.md), [Synonyme](synonyms.md), und [Merchandisingregeln](category-merch.md).

![Architekturdiagramm der Live-Suche](assets/architecture-diagram.svg)

## Live Search-Komponenten

* [!DNL Live Search] [Popover](storefront-popover.md) ist das Feld, das unter dem Suchfeld geöffnet wird, das die Suchergebnisse enthält.
* [Widget &quot;Seite für Produktauflistung&quot;](plp-styling.md) bietet eine durchsuchbare Produktlistenseite mit Facetten- und Synonym-Unterstützung.
* Die AEM [CIF](https://github.com/adobe/aem-cif-guides-venia/pull/319) ermöglicht es AEM Sites, [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) ist der Ort, an dem Regeln, Facetten und Synonyme konfiguriert werden.
* Der Suchadapter ist die Standardimplementierung von [!DNL Live Search].

## [!DNL Live Search] Demo

In diesem Video erfahren Sie mehr über [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Ein detaillierteres Video zur Verwendung und Konfiguration der Live-Suche finden Sie unter [Vollständige Demonstration auf [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) Thema.
