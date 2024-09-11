---
title: '[!DNL Catalog Service] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Catalog Service] für Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 93be63ca7a4edc2890a37a6460a123e28226301a
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionshinweise

In diesen Versionshinweisen werden die neuesten Versionen von [!DNL Catalog Service] beschrieben.
Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

## Aktuelle Hauptversion

### Version 1.23

_22. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Sie können jetzt Produktinformationen ohne Produktüberschreibungen (Preise) abrufen. In früheren Versionen haben diese Abfragen den folgenden Fehler zurückgegeben:
`The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.` <!--DATA-6121-->

### Version 1.22

_13. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Referenz zur Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/). <!--DATA-6067-->


## Frühere Versionen

+++ Frühere Versionen

### Version 1.22

_13. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung zum Abrufen aller Varianten nach Produkt-SKU hinzugefügt. Siehe die [Referenz zur Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/). <!--DATA-6067-->

### Version 1.19

_23. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}


![Korrektur](../assets/fix.svg) <!--DATA-5033-->Das `InStock` -Flag für Optionswerte berücksichtigt jetzt den Gültigkeitsstatus `enabled` der Produktvariante.

![Korrektur](../assets/fix.svg) <!--DATA-5888-->Ergänzung der Unterstützung für Produktpreise, für die große Zahlen (bis zu 16 Stellen) und eine höhere Dezimalgenauigkeit (bis zu 4 Dezimalstellen) erforderlich sind. Um die Preiskonfigurationsaktualisierungen auf Ihren vorhandenen Katalog anzuwenden, synchronisieren Sie die Katalogdaten erneut über das [Dashboard &quot;Datenverwaltung&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) oder über die Befehlszeilenschnittstelle von Adobe Commerce [3}.](../landing/catalog-sync.md#command-line-interface)

#### Bekannte Einschränkungen

Die folgenden Funktionen werden noch nicht unterstützt:

* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Der Produktpreis der Gruppe kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Beheben Sie die folgenden Einschränkungen mithilfe von API Measurement und der GraphQL-Core-API:

* Mindestpreis für Werbung
* Kategoriekosten
* Bundle-Produkte mit Fixpreisen

Weitere Informationen und Beispiele finden Sie unter [Catalog Service and API Mesh](mesh.md)

### Version 1.18

_11. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung für PHP 8.3 hinzugefügt.

![Neu](../assets/new.svg) Die Abfragen [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) und [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) geben jetzt anpassbare Optionsdaten für einfache und komplexe Produkte zurück.<!--DATA-5538-->

### Version 1.17

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service]. Unterstützung für diese Funktion wurde in Version 3.1.0 des `catalog-service` -Metapakets eingeführt.

### Version 1.16

_13. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Produktvideos werden jetzt von der Catalog Service-API unterstützt.
![Korrektur](../assets/fix.svg) Nicht vorrätige Optionen werden jetzt im PDP-Widget angezeigt.

#### Bekannte Einschränkungen

Diese Funktionen werden noch nicht unterstützt:

* Die maximale Größe für die Payload dynamischer Attribute beträgt 9 MB.
* Gruppenproduktpreis. Dieser Wert kann mit einfachen Produktpreisen berechnet werden.
* In einem Bild-Array enthält nur das erste Bild Rollen.

Die folgenden Einschränkungen können mit API Measurement und der GraphQL-Core-API behoben werden:

* Mindestpreis für Werbung
* [Kategoriekosten](mesh.md)

### Version 1.13

_12. Oktober 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalogdienst unterstützt die Markierung `inStock` für Produktvarianten.
![Neu](../assets/new.svg) Die Felder `urlKey` und `externalId` wurden dem GraphQL-Schema hinzugefügt.
![Neu](../assets/new.svg) Herunterladbare Produkte und Geschenkkarten werden jetzt unterstützt.

### Version 1.12

_19. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalogdienst verwendet jetzt die [SaaS-Preisindizierung](../price-index/price-indexing.md).
![Fehlerbehebung](../assets/fix.svg) Diese Version enthält Fehlerbehebungen und Verbesserungen auf der Dienstseite.

### Version 1.11

_18. Juli 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalogdienst unterstützt jetzt die GraphQL-Abfrage [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) für Product Recommendations.

### Version 1.10

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Catalog Service-API unterstützt jetzt `related products`.

### Version 1.7

_12. April 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Katalogdienst bereinigt jetzt gelöschte Produktvarianten.
![Korrektur](../assets/fix.svg) Verbesserungen der Skalierbarkeit und Leistung der Infrastruktur.

### Version 1.6

_28. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Zur [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) -Abfrage wurden Muster hinzugefügt.
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, `entityId` mithilfe von [API-Mesh](mesh.md) zu erhalten.

### Version 1.5

_6. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die GraphQL-Funktion [`categories`](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) wurde hinzugefügt.
![Korrektur](../assets/fix.svg) Verbesserte Leistung und API-Skalierbarkeit.

### Version 1.4

_7. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Das veröffentlichte Katalog-Service-Metapaket vereinfacht die Installationsschritte.
![Korrektur](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.3

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Onboarding-Erfahrung wurde vereinfacht und verbessert.
![Neu](../assets/new.svg) Neue Kunden-Sandbox-Endpunkte sind für Vorproduktionstests verfügbar.
![Neu](../assets/new.svg) Unterstützung für virtuelle Produkte hinzugefügt.
![Korrektur](../assets/fix.svg) API-Skalierbarkeit und Leistungsverbesserungen.

### Version 1.1

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neuer Katalogdienst](../assets/new.svg) unterstützt jetzt Adobe [API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Korrektur](../assets/fix.svg) Verbesserte API-Skalierbarkeit und Gesamtleistung.

### Version 1.0

_4. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützt jetzt gebündelte und gruppierte Produkte.
![Neu](../assets/new.svg) Es wurden Überschreibungen der B2B-Sichtbarkeit hinzugefügt. Produkte sind nun durchsuchbar und können für bestimmte Kundengruppen zum Warenkorb hinzugefügt werden.
![Fehlerbehebung](../assets/fix.svg) Der Dienst ist jetzt stabiler und hat eine verbesserte Leistung.

### Version 0.3 - Beta+

_12. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Bilder für Variantenunterstützung: Produktbilder werden basierend auf den ausgewählten Optionen zurückgegeben
![Neu](../assets/new.svg) Rollen für Preisunterstützung: Nur Mitglieder bestimmter Kundengruppen können den Preis für Produkte sehen
![Korrektur](../assets/fix.svg) Verbesserte Stabilität und Leistung des Dienstes
![Neu](../assets/new.svg) Aktualisierungen werden empfangen, wenn Produkte aus dem Katalog gelöscht werden

### Beta-Version

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Abfragen `products` und `refineProduct` geben die folgenden Daten zurück:

* Vordefinierte (System-)Produktattribute
* Dynamische Produktattribute und deren Filterung nach Rolle (Produktanzeigen-Seite/Produktlistenseite).
* Produktoptionen.
* Produktbilder und deren Filterung nach Rolle (PDP/PLP).
* Ein spezifischer Preis für einfache Produkte und Preisspannen für konfigurierbare Produkte.
* Kundengruppenpreise und Preisspannen. Sie geben einen Fallback-Standardpreis für Käufer ohne Kundengruppe zurück.
* Produktarten, die B2B-kundenspezifische Preise verwenden.
