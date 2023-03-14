---
title: "Commerce-Konfigurationseinstellungen und [!DNL Live Search] "
description: "Beschreibt die Adobe Commerce-Konfigurationseinstellungen, die [!DNL Live Search] kann lesen."
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# [!DNL Live Search] und Adobe Commerce-Konfigurationseinstellungen

Es gibt Commerce-Konfigurationseinstellungen, die [!DNL Live Search] unterstützt. In diesem Thema werden diese Konfigurationswerte aufgelistet.

## Unterstützte Konfigurationswerte

| Commerce-Konfigurationseinstellungen | Unterstützt von Popover | Vom Adapter unterstützt |
|---|---|---|
| Stores -> Konfiguration -> Katalog -> Katalog -> Katalogsuche -> Minimale Abfragelänge | Ja | Ja |
| Stores -> Konfiguration -> Katalog -> Inventar -> Nicht vorrätige Produkte anzeigen | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Stores -> Konfiguration -> Allgemein -> Währungseinstellungen -> Währungsoptionen -> Basiswährung | Ja | Ja |

## Nicht unterstützte Konfigurationswerte

[!DNL Live Search] kann nicht alle Konfigurationswerte lesen. Diese Tabelle listet Werte auf, die für Entwickler von größerem Interesse sein können.

| Magento-Konfigurationseinstellungen | Hinweise |
|---|---|
| Stores -> Konfiguration -> Katalog -> Storefront -> Listenmodus | Wird korrekt gerendert, aber für einige Seiteninteraktionen werden keine Ereignisse gesendet |
| Stores -> Konfiguration -> Katalog -> Storefront -> Alle Produkte pro Seite zulassen | nicht umgesetzt; sendet Anforderungen an den Suchdienst ohne Seitengröße und [!DNL Live Search] gibt eine standardmäßige Seitengröße von 20 zurück |
| Stores -> Konfiguration -> Katalog -> Katalog -> Katalogsuche -> Maximale Abfragelänge | nicht umgesetzt; Search Services akzeptiert bis zu 255 Zeichen |
| Stores -> Konfiguration -> Allgemein -> Währungseinstellungen -> Währungsoptionen -> Standardanzeigewährung | nicht umgesetzt; [!DNL Live Search] nur Zugriff auf die Basiswährung hat |
| Konfiguration -> Vertrieb -> Steuern -> Preisanzeigeeinstellungen -> Produktpreise im Katalog anzeigen |  |
