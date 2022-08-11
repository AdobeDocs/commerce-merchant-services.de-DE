---
title: '''[!DNL Catalog Service] Versionshinweise'''
description: Die neuesten Versionsinformationen für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 72913e0c0b7364e38d37fe1a8279c40a4e849c02
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 2%

---

# [!DNL Catalog Service] Versionshinweise

{{catalog-service-beta}}

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Catalog Service] und umfassen:

* ![Neu](../assets/new.svg) - Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) - Bekannte Probleme

## Beta-Version

* ![Neu](../assets/new.svg) - die `products` und `refineProduct` -Abfragen geben die folgenden Daten zurück:
   * Vordefinierte (System-)Produktattribute
   * Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigen-Seite/Produktlistenseite).
   * Produktoptionen.
   * Produktbilder und deren Filterung nach Rolle (PDP/PLP).
   * Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
   * Kundengruppenpreise und Preisspannen. Sie geben einen Fallback-Standardpreis für Käufer ohne Kundengruppe zurück.
   * Produktarten, die B2B-kundenspezifische Preise verwenden.

## Bekannte Einschränkungen

* Pakete und gruppierte Produkte werden nicht unterstützt.
* Tier-Preise werden nicht unterstützt.
* In einem Bildbereich enthält nur das erste Bild Rollen.
* Bilder für Varianten werden nicht abgerufen.
* Updates werden nicht empfangen, wenn Produkte oder Varianten aus dem Katalog gelöscht werden.
