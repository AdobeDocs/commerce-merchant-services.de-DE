---
title: Versionshinweise
description: Die neuesten Versionsinformationen für die [!DNL Data Connection] -Erweiterung von Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Versionshinweise

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection].

Diese Versionshinweise enthalten Aktualisierungen für [!DNL Data Connection] -Erweiterung und umfasst:

![Neu](../assets/new.svg) - Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) - Bekannte Probleme

Für Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen, die von der [!DNL Data Connection] -Erweiterung, siehe **Unterstützte Dienstaktualisierungen**.

Siehe [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe die Entwicklerdokumentation zu [erfahren, welche Commerce-Versionen dieses Modul unterstützen.](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Unterstützte Dienstaktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit den von der [!DNL Data Connection] -Erweiterung.

+++Unterstützte Dienstaktualisierungen

_24. Januar 2024_

![Neu](../assets/new.svg) - Die `data-services-b2b` Erweiterung, um ein neues Anforderungsereignis mit dem Namen [deleteRequisitionList](events.md#deleterequisitionlist) für B2B-Händler.

_16. November 2023_

![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem eine Fehlermeldung fälschlicherweise angezeigt wurde, wenn Sie eine Bestellung aufgegeben haben, die mehrere Versandadressen hatte.
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem im [productPageView](events.md#productpageview) -Ereignis, wobei `productListItems.priceTotal` -Ereignisfeld hat den Preis nach dem Wechseln der Währung in der Store-Ansicht nicht konvertiert.
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Problem im `productListItems` Ereignisfeld, in dem der Währungscode nicht aktualisiert wurde, als der Händler die Store-Ansicht wechselte.

_10. Oktober 2023_

![Neu](../assets/new.svg) - Neue Bestellstatus-Ereignisse hinzugefügt: [Rechnungsstellung](events-backoffice.md#orderinvoiced), [Rückgabe des Bestellartikels initiiert](events-backoffice.md#orderitemsreturninitiated), und [Auftragsgegenstandsrückgabe abgeschlossen](events-backoffice.md#orderitemreturncompleted).
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

![Neu](../assets/new.svg) - Es wurde eine Erweiterung namens `data-services-b2b` , die [Ereignisse in der Anforderungsliste](events.md#b2b-events) für B2B-Händler.
![Neu](../assets/new.svg) - Der `uniqueIdentifier` -Feld zu [suchen](events.md#search-events) -Ereignisse. Dieses neue Feld ermöglicht Händlern, auf Suchanfragen und Suchantworten zu verweisen.

_12. Oktober 2022_

![Neu](../assets/new.svg) - Zwei wurden hinzugefügt [Storefront-Ereignisse](events.md), `openCart` und `removeFromCart`, um das Adobe Commerce Storefront Events SDK und Collector aufzurufen.
![Neu](../assets/new.svg) - Unterstützung für eine [AEM](overview.md#aem-support).

+++

## 3.2.0-beta1

_16. Februar 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Wenn Sie an der Beta-Phase teilnehmen, stellen Sie sicher, dass Ihre `composer.json` -Datei hat Folgendes auf der Stammebene: ` "minimum-stability": "beta"`.
![Neu](../assets/new.svg) - Zusätzliche Funktion für [Hinzufügen benutzerdefinierter Attribute](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Neu](../assets/new.svg) - Zusätzliche Funktion für [Profildatensätze erfassen und senden](connect-data.md#send-customer-profile-data) und Daten an Experience Platform.

## 3.1.0

_16. November 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Der Experience Platform-Connector wurde in [!DNL Data Connection].
![Fehlerbehebung](../assets/new.svg) - Zusätzliche Möglichkeit zur Protokollierung der Fehlerantwort, wenn Adobe IMS das Zugriffstoken nicht generieren kann.
![Fehlerbehebung](../assets/new.svg) - Es wurde eine Benachrichtigung hinzugefügt, wenn Sie versuchen, historische Bestellungen zu synchronisieren, aber keine Kontoanmeldeinformationen angegeben haben.

## 3,0,0

_10. Oktober 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

Dies ist eine Hauptversion. [Bearbeiten](install.md#update-the-data-connection) die Datei &quot;root composer.json&quot;Ihres Projekts.

![Neu](../assets/new.svg) - Allgemeine Verfügbarkeit [historische Reihenfolge senden](connect-data.md#send-historical-order-data) -Daten und -Status auf der Experience Platform.
![Neu](../assets/new.svg) - Unterstützung für OAuth 2.0 bei [konfigurieren](connect-data.md#connect-commerce-data-to-adobe-experience-platform) die [!DNL Data Connection] -Erweiterung.
![Neu](../assets/new.svg) - Der Support für Adobe Commerce 2.4.3 wurde eingestellt.

## 2,3,0

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Zusätzliche Funktion für [Deaktivieren des Versands von Storefront-Ereignissen](connect-data.md#data-collection) auf die Experience Platform.
![Fehlerbehebung](../assets/fix.svg) - Konfigurationen der Inhaltssicherheitsrichtlinie wurden aktualisiert.
![Fehlerbehebung](../assets/fix.svg) - Die Unterstützung für Back-Office-Ereignisse in Commerce 2.4.7 wurde korrigiert.
![Neu](../assets/new.svg) - Es wurde eine Benachrichtigung zur Cache-Invalidierung hinzugefügt, wenn Sie Änderungen an der [!DNL Data Connection] Erweiterungsformular.


## 3.0.0-beta1 (nur intern)

_13. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - (Beta) Neue Möglichkeit zu [historische Reihenfolge senden](connect-data.md#beta-send-historical-order-data) -Daten und -Status auf der Experience Platform.

## 2,2,0

_30. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Die `commerce-data-export` und `saas-export` Abhängigkeiten mit `experience-platform-connector` -Erweiterung. Zuvor mussten Sie diese Abhängigkeiten separat installieren. Diese Abhängigkeiten ermöglichen zusammen mit der Merchant-Konfiguration die serverseitige Verarbeitung von [Backoffice-Ereignisse](events-backoffice.md).
![Neu](../assets/new.svg) - Es wurde ein neues Backoffice-Ereignis namens [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Unterstützung für PHP 8.2 für alle hinzugefügt [!DNL Data Connection] Erweiterungen.

## 2.1.0

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Die [[!DNL Data Connection] Erweiterungsadministrator](connect-data.md) damit Sie Ihr eigenes AEP Web SDK (Legierung) angeben können.
![Fehlerbehebung](../assets/fix.svg) Geändert zu mithilfe von `identityMap` anstelle von `personID` beim Festlegen der primären Identität für alle Daten, die an die Kante gesendet werden.

## 2,0,1

_10. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Fehlerbehebung](../assets/fix.svg) - Jetzt wird der Adobe Experience Platform-Kontext erst festgelegt, nachdem das Storefront Event Collector und Storefront Event SDK erfolgreich geladen wurden.

## 2,0,0

_12. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, Ihr eigenes AEP Web SDK anzugeben, wenn [Verbindung](connect-data.md) Ihre Adobe Commerce-Instanz auf der Experience Platform.
![Fehlerbehebung](../assets/fix.svg) - Die Anforderung zum Datenspeicherbereich wurde aktualisiert, sodass die Datastream-IDs auf die Website übertragen werden müssen, anstatt sie zu überprüfen.

## 1,0,0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Allgemeines Release zur Verfügbarkeit
