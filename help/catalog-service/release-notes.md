---
title: '''[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionshinweise für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: a439df188f72d17a6a41fa248aa9957aaabd9e02
workflow-type: tm+mt
source-wordcount: '581'
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

### Version 1.17

_22.02.2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search], und [!DNL Catalog Service]. Die Unterstützung für diese Funktion wurde in Version 3.1.0 der `catalog-service` Metapaket.

## Frühere Versionen

+++ Frühere Versionen

### Version 1.16

_13. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Produktvideos werden jetzt von der Catalog Service-API unterstützt.
![Fehlerbehebung](../assets/fix.svg) Bundle-Produkte mit festen Preisen werden jetzt unterstützt.
![Fehlerbehebung](../assets/fix.svg) Nicht vorrätige Optionen werden jetzt im PDP-Widget angezeigt.

#### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Die folgenden Einschränkungen können mithilfe des API-Gitters und der GraphQL-Core-API behoben werden:

* Mindestpreis für Werbung
* [Kategoriekosten](mesh.md)

### Version 1.13

_12. Oktober 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Catalog Service unterstützt die `inStock` Markierung für Produktvarianten.
![Neu](../assets/new.svg) `urlKey` und `externalId` wurden zum GraphQL-Schema hinzugefügt.
![Neu](../assets/new.svg) Herunterladbare Produkte und Geschenkkarten werden jetzt unterstützt.

### Version 1.12

_19. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Catalog Service verwendet jetzt [SaaS-Preisindizierung](../price-index/price-indexing.md).
![Fehlerbehebung](../assets/fix.svg) Diese Version enthält Fehlerbehebungen und Verbesserungen auf der Dienstseite.

### Version 1.11

_18. Juli 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Catalog Service unterstützt jetzt die [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) GraphQL-Abfrage für Product Recommendations.

### Version 1.10

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Catalog Service API unterstützt jetzt &quot;verwandte Produkte&quot;.

### Version 1.7

_12. April 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Catalog Service bereinigt jetzt gelöschte Produktvarianten.
![Fehlerbehebung](../assets/fix.svg) Skalierbarkeit der Infrastruktur und Leistungsverbesserungen.

### Version 1.6

_28. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Muster wurden zum [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) Abfrage.
![Neu](../assets/new.svg) Zusätzliche Funktion für `entityId` using [API-Mesh](mesh.md).

### Version 1.5

_6. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) hinzugefügt [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) GraphQL-Funktionen.
![Fehlerbehebung](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Version 1.4

_7. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Das Katalog-Service-Metapaket wurde veröffentlicht, um die Installationsschritte zu vereinfachen.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.3

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Das Onboarding wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte stehen für Vorproduktionstests zur Verfügung.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Fehlerbehebung](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.1

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Catalog Service unterstützt jetzt Adobe [API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fehlerbehebung](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Version 1.0

_4. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützt jetzt gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Sichtbarkeitsüberschreibungen für B2B hinzugefügt. Produkte sind nun durchsuchbar und können für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fehlerbehebung](../assets/fix.svg) Der Dienst ist jetzt stabiler und hat eine verbesserte Leistung.

### Version 0.3 - Beta+

_12. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Bilder für Variantenunterstützung: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) Preisstützung durch Rollen: Ermöglicht es nur Mitgliedern bestimmter Kundengruppen, den Preis von Produkten zu sehen
![Fehlerbehebung](../assets/fix.svg) Verbesserte Stabilität und Leistung des Dienstes
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Beta-Version

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die `products` und `refineProduct` -Abfragen geben die folgenden Daten zurück:

* Vordefinierte (System-)Produktattribute
* Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigen-Seite/Produktlistenseite).
* Produktoptionen.
* Produktbilder und deren Filterung nach Rolle (PDP/PLP).
* Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
* Kundengruppenpreise und Preisspannen. Sie geben einen Fallback-Standardpreis für Käufer ohne Kundengruppe zurück.
* Produktarten, die B2B-kundenspezifische Preise verwenden.

+++
