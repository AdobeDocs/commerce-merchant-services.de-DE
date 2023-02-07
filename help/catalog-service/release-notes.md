---
title: '''[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 67f9e5ce69930f3298427a103f9160f925d2ae0d
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionshinweise

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Catalog Service] und umfassen:

* ![Neu](../assets/new.svg) Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) Bekannte Probleme

## Version 1.4

Releasedatum: 2023-2-7 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/new.svg) Das Katalog-Service-Metapaket wurde veröffentlicht, um die Installationsschritte zu vereinfachen.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.


### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Bundle-Produkte mit Festpreis
* Beim Löschen von Varianten aus dem Katalog werden keine Aktualisierungen empfangen.
* Die maximale Größe für die Nutzlast dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.
* Farbmuster
* Laden der Produktdetailseite über die Produkt-URL.

Die folgenden Einschränkungen können mit der GraphQL-Core-API behoben werden:

* Mindestpreis für Werbung
* Kategoriekosten
* Herunterladbare Produkte und Geschenkkarten
* Kategorien (`categories` und `categoryList`)

## Version 1.3

Releasedatum: 2023-1-17 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte stehen für Vorproduktionstests zur Verfügung.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Bundle-Produkte mit Festpreis
* Beim Löschen von Varianten aus dem Katalog werden keine Aktualisierungen empfangen.
* Die maximale Größe für die Nutzlast dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.
* Farbmuster
* Laden der Produktdetailseite über die Produkt-URL.

Die folgenden Einschränkungen können mit der GraphQL-Core-API behoben werden:

* Mindestpreis für Werbung
* Kategoriekosten
* Herunterladbare Produkte und Geschenkkarten
* Kategorien (`categories` und `categoryList`)

## Version 1.1

Releasedatum: 2022-11-18 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/new.svg) Catalog Service unterstützt jetzt die Adobe [API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fehlerbehebung](../assets/fix.svg) Wir haben die API-Skalierbarkeit und die Gesamtleistung verbessert.

### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Bundle-Produkte mit Festpreis
* Beim Löschen von Varianten aus dem Katalog werden keine Aktualisierungen empfangen.
* Die maximale Größe für die Nutzlast dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.
* Farbmuster
* Laden der Produktdetailseite über die Produkt-URL.

Die folgenden Einschränkungen können mit der GraphQL-API behoben werden:

* Mindestpreis für Werbung
* Kategoriekosten
* Herunterladbare Produkte und Geschenkkarten
* Kategorien (`categories` und `categoryList`)

## Version 1.0

Releasedatum: 2022-10-04 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/new.svg) Unterstützt jetzt gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Sichtbarkeitsüberschreibungen für B2B hinzugefügt. Produkte sind nun durchsuchbar und können für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fehlerbehebung](../assets/fix.svg) Der Dienst ist jetzt stabiler und hat eine verbesserte Leistung.

### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Kategoriekosten
* Aktualisierungen werden nicht empfangen, wenn Varianten aus dem Katalog gelöscht werden
* Maximale Größe für die Payload der dynamischen Attribute ist &lt;9 MB
* Festpreis für Bundle-Produkte
* Gesamtpreis für gruppierte Produkte
* Unterstützung für virtuelle, herunterladbare und Geschenkkarten-Produkttypen
* Mindestpreis für Werbung (MAP)

## Version 0.3 - Beta+

Releasedatum: 2022-09-12 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Beta

![Neu](../assets/new.svg) Bilder für Varianten unterstützen: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) Preisstützung: nur Mitgliedern bestimmter Kundengruppen erlauben, den Preis der Produkte zu sehen
![Fehlerbehebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Dienstes
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Kategoriekosten
* Bundle und gruppierte Produkte
* Beim Löschen von Varianten aus dem Katalog werden keine Aktualisierungen empfangen
* Sichtbarkeitsüberschreibungen für B2B: Produkte können durchsucht werden oder zum Warenkorb für bestimmte Kundengruppen hinzugefügt werden.

## Beta-Version

Releasedatum: 2022-08-09 Kompatibel mit Adobe Commerce (EE): 2.4.x Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x Stabilität: Beta

![Neu](../assets/new.svg) Die `products` und `refineProduct` -Abfragen geben die folgenden Daten zurück:

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
