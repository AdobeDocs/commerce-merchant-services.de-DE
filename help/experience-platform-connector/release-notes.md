---
title: Versionshinweise
description: Die aktuellen Versionsinformationen zum Adobe Experience Platform Connector von Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: b48f9eadda233f4996f1e1d806ecc973cfd241c2
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise enthalten Aktualisierungen des Experience Platform-Connectors und umfassen:

* ![Neu](../assets/new.svg) - Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) - Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit vom Experience Platform-Connector verwendeten Erweiterungen finden Sie unter **Unterstützte Dienstaktualisierungen**.

Siehe [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe die Entwicklerdokumentation zu [Informationen zur Produktkompatibilität](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Unterstützte Dienstaktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen beschrieben, die vom Experience Platform-Connector verwendet werden.

+++Unterstützte Dienstaktualisierungen

_10. Juni 2023_

* ![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem behoben, das bei `orderId` aufgrund von Präfixen in der Commerce-Bestellkennung nicht im Kontext übergeben wurde.
* ![Fehlerbehebung](../assets/fix.svg) - Konfigurationen der Inhaltssicherheitsrichtlinie wurden aktualisiert.

_30. März 2023_

* ![Neu](../assets/new.svg) - Eine neue Erweiterung namens wurde hinzugefügt. `data-services-b2b` , die [Ereignisse in der Anforderungsliste](events.md#b2b-events) für B2B-Händler
* ![Neu](../assets/new.svg) - Der `uniqueIdentifier` -Feld zu [suchen](events.md#search-events) -Ereignisse. Dieses neue Feld ermöglicht Händlern, Querverweise darauf zu erstellen, welche Suchanfragen zu welchen Suchanfragen passen.

_12. Oktober 2022_

* ![Neu](../assets/new.svg) - Zwei wurden hinzugefügt [Storefront-Ereignisse](events.md): `openCart` und `removeFromCart` zum Adobe Commerce Storefront Events SDK und Collector
* ![Neu](../assets/new.svg) - Unterstützung für eine [AEM Storefront](overview.md#aem-support)

+++

## 2.2.0

_30. März 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Neu](../assets/new.svg) - Die `commerce-data-export` und `saas-export` Abhängigkeiten mit `experience-platform-connector` -Erweiterung. Zuvor mussten Sie diese Abhängigkeiten separat installieren. Diese Abhängigkeiten ermöglichen zusammen mit der Merchant-Konfiguration die serverseitige Verarbeitung von [Backoffice-Ereignisse](events.md#back-office-events).
* ![Neu](../assets/new.svg) - Es wurde ein neues Backoffice-Ereignis namens [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28. Februar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Neu](../assets/new.svg) - Unterstützung für PHP 8.2 für alle Experience Platform-Connector-Module hinzugefügt

## 2.1.0

_17. Januar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Neu](../assets/new.svg) - Die [Experience Platform Connector-Admin](connect-data.md) damit Sie Ihr eigenes AEP Web SDK (Legierung) angeben können.
* ![Fehlerbehebung](../assets/fix.svg) Geändert zu mithilfe von `identityMap` anstelle von `personID` beim Festlegen der primären Identität für alle Daten, die an die Kante gesendet werden.

## 2.0.1

_10. November 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Problem behoben](../assets/fix.svg) - Jetzt wird der Adobe Experience Platform-Kontext erst festgelegt, nachdem das Storefront Event Collector und Storefront Event SDK erfolgreich geladen wurden.

## 2.0.0

_12. Oktober 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Neu](../assets/new.svg) - Zusätzliche Möglichkeit zur Angabe Ihres eigenen AEP Web SDK bei [Verbindung](connect-data.md) Ihre Adobe Commerce-Instanz an die Experience Platform
* ![Fehlerbehebung](../assets/fix.svg) - Die Anforderung zum Datenspeicherbereich wurde aktualisiert, sodass die Datastream-IDs auf die Website übertragen werden müssen, anstatt sie zu speichern

## 1.0.0

_9. August 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

* ![Neu](../assets/new.svg) - Allgemeine Verfügbarkeitsversion
