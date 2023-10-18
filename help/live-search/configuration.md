---
title: '"Commerce-Konfigurationseinstellungen und [!DNL Live Search] '''
description: Beschreibt die Adobe Commerce-Konfigurationseinstellungen, die [!DNL Live Search] kann lesen.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: 888b81683a4e139a35b771d9c573f1f5f0c3b902
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# [!DNL Live Search] und Adobe Commerce-Konfigurationseinstellungen

Es gibt Commerce-Konfigurationseinstellungen, die [!DNL Live Search] unterstützt. In diesem Thema werden diese Konfigurationswerte aufgelistet.

## Unterstützte Konfigurationswerte

| Commerce-Konfigurationseinstellungen | Unterstützt von Popover | Vom Adapter unterstützt |
|---|---|---|
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Alle Produkte pro Seite zulassen | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Minimale Abfragelänge | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite - Zulässige Werte im Raster | Ja | Ja |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Produkte pro Seite auf Raster Standardwert | Ja. Max. 500 Produkte | Ja. Max. 500 Produkte |
| Stores > Konfiguration > Katalog > Bestand > Nicht vorrätige Produkte anzeigen | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Stores > Konfiguration > Währung > Standardanzeigewährung | Ja w/3.1.0+ | Ja w/3.1.0+ |
| Stores > Konfiguration > Allgemein > Währungseinstellungen > Währungsoptionen > Basiswährung | Ja | Ja |

Die Preise auf der Produktlistungsseite des Widgets und in Popover werden jetzt unter Verwendung der konfigurierten Währungsraten in die Standardanzeigewährung konvertiert.

## Suchbegriffe

[!DNL Live Search] unterstützt [Suchbegriffumleitungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) zu Implementierungen, bei denen Adobe Commerce das Routing durchführt: Luma und andere php-basierte Designs.

## Nicht unterstützte Konfigurationswerte

[!DNL Live Search] kann nicht alle Konfigurationswerte lesen. Diese Tabelle listet Werte auf, die für Entwickler von größerem Interesse sein können.

| Commerce-Konfigurationseinstellungen | Hinweise |
|---|---|
| Stores > Konfiguration > Katalog > Storefront > Listenmodus | Wird korrekt gerendert, aber für einige Seiteninteraktionen werden keine Ereignisse gesendet |
| Stores > Konfiguration > Katalog > Katalog > Katalogsuche > Maximale Abfragelänge | Nicht implementiert. Search Services akzeptiert bis zu 255 Zeichen |
| Konfiguration > Vertrieb > Steuern > Preisanzeigeeinstellungen > Produktpreise im Katalog anzeigen |  |
