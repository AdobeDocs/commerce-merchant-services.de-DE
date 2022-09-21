---
title: '[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 372dc1cb567121ab86f606d2ace9f19d8e01170b
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 1%

---

# [!DNL Catalog Service] Versionshinweise

{{catalog-service-beta}}

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Catalog Service] und umfassen:

* ![Neu](../assets/new.svg) - Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) - Bekannte Probleme

## Version 0.3 - Beta+

Releasedatum: 2022-09-12 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Beta

![Neu](../assets/new.svg) - Bilder für Variantenunterstützung: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) - Preisstützung: nur Mitgliedern bestimmter Kundengruppen erlauben, den Preis der Produkte zu sehen
![Fehlerbehebung](../assets/fix.svg) - Verbesserte Stabilität und Leistung des Dienstes
![Neu](../assets/new.svg) - Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Kategoriekosten
* Bundle und gruppierte Produkte
* Beim Löschen von Varianten aus dem Katalog werden keine Aktualisierungen empfangen
* Sichtbarkeitsüberschreibungen für B2B: Produkte können durchsucht werden oder zum Warenkorb für bestimmte Kundengruppen hinzugefügt werden.

## Beta-Version

Releasedatum: 2022-08-09 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Beta

* ![Neu](../assets/new.svg) - die `products` und `refineProduct` -Abfragen geben die folgenden Daten zurück:
* Vordefinierte (System-)Produktattribute
* Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigen-Seite/Produktlistenseite).
* Produktoptionen.
* Produktbilder und deren Filterung nach Rolle (PDP/PLP).
* Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
* Kundengruppenpreise und Preisspannen. Sie geben einen Fallback-Standardpreis für Käufer ohne Kundengruppe zurück.
* Produktarten, die B2B-kundenspezifische Preise verwenden.

### Bekannte Einschränkungen

* Pakete und gruppierte Produkte werden nicht unterstützt.
* Tier-Preise werden nicht unterstützt.
* In einem Bildbereich enthält nur das erste Bild Rollen.
* Bilder für Varianten werden nicht abgerufen.
* Updates werden nicht empfangen, wenn Produkte oder Varianten aus dem Katalog gelöscht werden.
