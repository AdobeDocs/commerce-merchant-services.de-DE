---
title: '''[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionshinweise

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Catalog Service].
Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

## Aktuelle Hauptversion

_25. April 2023_

![Neu](../assets/new.svg) Kunden von Catalog Service können jetzt die neue [SaaS-Preisindexer](../price-index/index.md).

### Version 1.7

_12. April 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Catalog Service bereinigt jetzt gelöschte Produktvarianten.
![Fehlerbehebung](../assets/fix.svg) Skalierbarkeit der Infrastruktur und Leistungsverbesserungen.

#### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Bundle-Produkte mit Festpreis
* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Die folgenden Einschränkungen können mithilfe des API-Gitters und der GraphQL-Core-API behoben werden:

* Mindestpreis für Werbung
* [Kategoriekosten](mesh.md)
* Herunterladbare Produkte und Geschenkkarten

### Version 1.6

_28. März 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Muster wurden zum [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) Abfrage.
![Neu](../assets/new.svg) Die Möglichkeit wurde hinzugefügt, `entityId` using [API-Mesh](mesh.md).

### Version 1.5

_6. März 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Hinzugefügt [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL-Funktionen.
![Fehlerbehebung](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Version 1.4

_7. Februar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Das Katalog-Service-Metapaket wurde veröffentlicht, um die Installationsschritte zu vereinfachen.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.3

_17. Januar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte stehen für Vorproduktionstests zur Verfügung.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.1

_18. November 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Catalog Service unterstützt jetzt die Adobe [API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fehlerbehebung](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Version 1.0

_4. Oktober 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Unterstützt jetzt gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Sichtbarkeitsüberschreibungen für B2B hinzugefügt. Produkte sind nun durchsuchbar und können für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fehlerbehebung](../assets/fix.svg) Der Dienst ist jetzt stabiler und hat eine verbesserte Leistung.

## Frühere Versionen

+++Beta-Versionen

### Version 0.3 - Beta+

_12. September 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Bilder für Varianten unterstützen: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) Preisstützung: nur Mitgliedern bestimmter Kundengruppen erlauben, den Preis der Produkte zu sehen
![Fehlerbehebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Dienstes
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Beta-Version

_9. August 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Die `products` und `refineProduct` -Abfragen geben die folgenden Daten zurück:

* Vordefinierte (System-)Produktattribute
* Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigen-Seite/Produktlistenseite).
* Produktoptionen.
* Produktbilder und deren Filterung nach Rolle (PDP/PLP).
* Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
* Kundengruppenpreise und Preisspannen. Sie geben einen Fallback-Standardpreis für Käufer ohne Kundengruppe zurück.
* Produktarten, die B2B-kundenspezifische Preise verwenden.

+++
