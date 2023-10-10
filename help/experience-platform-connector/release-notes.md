---
title: Versionshinweise
description: Die aktuellen Versionsinformationen zum Adobe Experience Platform Connector von Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 5e6cf955080338e00f23eaadeaa0192798126151
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise enthalten Aktualisierungen des Experience Platform-Connectors und umfassen:

![Neu](../assets/new.svg) - Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) - Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit vom Experience Platform-Connector verwendeten Erweiterungen finden Sie unter **Unterstützte Dienstaktualisierungen**.

Siehe [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe die Entwicklerdokumentation zu [erfahren, welche Commerce-Versionen dieses Modul unterstützen.](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Unterstützte Dienstaktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit vom Experience Platform-Connector verwendeten Erweiterungen beschrieben.

+++Unterstützte Dienstaktualisierungen

_10. Oktober 2023_

![Neu](../assets/new.svg) - Neue Bestellstatus-Ereignisse hinzugefügt: [Rechnungsstellung](events.md#orderinvoiced), [Rückgabe des Bestellartikels initiiert](events.md#orderitemsreturninitiated), und [Auftragsgegenstandsrückgabe abgeschlossen](events.md#orderitemreturncompleted).
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem Änderungen der Währungskonfiguration nach der Aktualisierung des Caches nicht in den Ereignissen übernommen wurden.
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Fehler behoben, der auftrat, wenn bei Aktivierung der asynchronen Bestellplatzierung keine Bestellbestätigungsmeldung angezeigt wurde.
![Neu](../assets/new.svg) - Daten hinzugefügt zu [addToRequisitionList](events.md#addtorequisitionlist) -Ereignis für einfache Produkte auf der Seite &quot;Kategorieansicht&quot;ein.
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem im `selectedOptions` Daten in der [addToRequisitionList](events.md#addtorequisitionlist) -Ereignis, wenn Produkte von der Bestellbestätigungsseite hinzugefügt werden.
![Neu](../assets/new.svg) - Produktdaten wurden hinzugefügt zu [addToRequisitionList](events.md#addtorequisitionlist) -Ereignis, wenn Produkte von der Seite &quot;Kategorieansicht&quot;zur Anforderungsliste hinzugefügt werden.
![Neu](../assets/new.svg) - hinzugefügt [addToRequisitionList](events.md#addtorequisitionlist) -Ereignis, wenn konfigurierbare Produkte der Anforderungsliste auf der Produktansichtsseite hinzugefügt werden.
![Neu](../assets/new.svg) - hinzugefügt [addToRequisitionList](events.md#addtorequisitionlist) und [removeFromRequisitionList](events.md#removefromrequisitionlist) Ereignisse, wenn die Produktmenge von einer Beschreibungsliste erhöht und/oder verringert wird.

_10. Juni 2023_

![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem behoben, das bei `orderId` im Kontext aufgrund von Präfixen in der Commerce-Bestellkennung nicht übergeben wurde.
![Fehlerbehebung](../assets/fix.svg) - Konfigurationen der Inhaltssicherheitsrichtlinie wurden aktualisiert.

_30. März 2023_

![Neu](../assets/new.svg) - Eine neue Erweiterung namens wurde hinzugefügt. `data-services-b2b` , die [Ereignisse in der Anforderungsliste](events.md#b2b-events) für B2B-Händler.
![Neu](../assets/new.svg) - Der `uniqueIdentifier` -Feld zu [suchen](events.md#search-events) -Ereignisse. Dieses neue Feld ermöglicht Händlern, auf Suchanfragen und Suchantworten zu verweisen.

_12. Oktober 2022_

![Neu](../assets/new.svg) - Zwei wurden hinzugefügt [Storefront-Ereignisse](events.md), `openCart` und `removeFromCart`, um das Adobe Commerce Storefront Events SDK und Collector aufzurufen.
![Neu](../assets/new.svg) - Unterstützung für eine [AEM](overview.md#aem-support).

+++

## 3.0.0

_10. Oktober 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Allgemeine Verfügbarkeit [historische Reihenfolge senden](connect-data.md#send-historical-order-data) -Daten und -Status auf der Experience Platform.
![Neu](../assets/new.svg) - Unterstützung für OAuth 2.0 bei [konfigurieren](connect-data.md#connect-commerce-data-to-adobe-experience-platform) den Experience Platform-Connector.
![Neu](../assets/new.svg) - Der Support für Adobe Commerce 2.4.3 wurde eingestellt.

## 2.3.0

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Zusätzliche Funktion für [Deaktivieren des Versands von Storefront-Ereignissen](connect-data.md#data-collection) auf die Experience Platform.
![Fehlerbehebung](../assets/fix.svg) - Konfigurationen der Inhaltssicherheitsrichtlinie wurden aktualisiert.
![Fehlerbehebung](../assets/fix.svg) - Die Unterstützung für Back-Office-Ereignisse in Commerce 2.4.7 wurde korrigiert.
![Neu](../assets/new.svg) - Es wurde eine Benachrichtigung zur Cache-Invalidierung hinzugefügt, wenn Sie Änderungen am Experience Platform Connector-Formular speichern.


## 3.0.0-beta1 (nur intern)

_13. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - (Beta) Neue Möglichkeit zu [historische Reihenfolge senden](connect-data.md#beta-send-historical-order-data) -Daten und -Status auf der Experience Platform. Diese Funktion ist nur für Beta-Benutzer verfügbar. Sie können der Beta-Phase beitreten, indem Sie eine E-Mail an folgende Adresse senden: `dataconnection@adobe.com`.

## 2.2.0

_30. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Die `commerce-data-export` und `saas-export` Abhängigkeiten mit `experience-platform-connector` -Erweiterung. Zuvor mussten Sie diese Abhängigkeiten separat installieren. Diese Abhängigkeiten ermöglichen zusammen mit der Merchant-Konfiguration die serverseitige Verarbeitung von [Backoffice-Ereignisse](events.md#back-office-events).
![Neu](../assets/new.svg) - Es wurde ein neues Backoffice-Ereignis namens [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Unterstützung für PHP 8.2 für alle Experience Platform-Connector-Erweiterungen hinzugefügt.

## 2.1.0

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Die [Experience Platform-Connector-Admin](connect-data.md) damit Sie Ihr eigenes AEP Web SDK (Legierung) angeben können.
![Fehlerbehebung](../assets/fix.svg) Geändert zu mithilfe von `identityMap` anstelle von `personID` beim Festlegen der primären Identität für alle Daten, die an die Kante gesendet werden.

## 2.0.1

_10. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Fehlerbehebung](../assets/fix.svg) - Jetzt wird der Adobe Experience Platform-Kontext erst festgelegt, nachdem das Storefront Event Collector und Storefront Event SDK erfolgreich geladen wurden.

## 2.0.0

_12. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, Ihr eigenes AEP Web SDK anzugeben, wenn [Verbindung](connect-data.md) Ihre Adobe Commerce-Instanz auf der Experience Platform.
![Fehlerbehebung](../assets/fix.svg) - Die Anforderung zum Datenspeicherbereich wurde aktualisiert, sodass die Datastream-IDs auf die Website übertragen werden müssen, anstatt sie zu überprüfen.

## 1.0.0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Allgemeines Release zur Verfügbarkeit
