---
title: Versionshinweise
description: Die neuesten Versionsinformationen für die [!DNL Data Connection] Erweiterung von Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 15b1c90cb60094d7f4a4da6435c5262f75cf0081
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Versionshinweise

>[!IMPORTANT]
>
>Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.

Diese Versionshinweise enthalten Aktualisierungen der [!DNL Data Connection] -Erweiterung und umfassen:

![Neu](../assets/new.svg) - Neue Funktionen
![Korrektur](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) - Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen, die von der Erweiterung [!DNL Data Connection] verwendet werden, finden Sie unter **Unterstützte Dienstaktualisierungen**.

Unter [Bevorstehende Versionen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) erfahren Sie mehr über die Veröffentlichungszeitpläne und die Unterstützung.

Informationen dazu, welche Commerce-Versionen dieses Modul unterstützen, finden Sie in der Entwicklerdokumentation von [.](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)

## Unterstützte Dienstaktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen beschrieben, die von der [!DNL Data Connection] -Erweiterung verwendet werden.

+++Unterstützte Dienstaktualisierungen

_2. August 2024_

![Korrektur](../assets/fix.svg) - Korrektur des Gesamtbetrags der Zahlungen, wenn die Bestellsumme so konfiguriert ist, dass Steuern einbezogen werden.
![Neu](../assets/new.svg) - Ein `taxAmount` -Feld wurde hinzugefügt, um Kaufereignisse zu bestellen.
![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, benutzerspezifische Daten zu Ereignissen hinzuzufügen. Im Folgenden finden Sie ein [Beispiel](https://github.com/adobe/commerce-events/blob/main/examples/events/custom-event-override.md).

_24. Januar 2024_

![Neu](../assets/new.svg) - Die Erweiterung `data-services-b2b` wurde aktualisiert und enthält jetzt ein neues Anforderungsereignis namens [deleteRequisitionList](events.md#deleterequisitionlist) für B2B-Händler.

_16. November 2023_

![Korrektur](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem eine Fehlermeldung fälschlicherweise angezeigt wurde, wenn Sie eine Bestellung aufgegeben haben, die mehrere Versandadressen hatte.
![Korrektur](../assets/fix.svg) - Es wurde ein Problem im Ereignis [productPageView](events.md#productpageview) behoben, bei dem das Ereignisfeld `productListItems.priceTotal` den Preis nach dem Wechseln der Währung in der Store-Ansicht nicht konvertierte.
![Korrektur](../assets/fix.svg) - Es wurde ein Problem im Ereignisfeld `productListItems` behoben, bei dem der Währungscode nicht aktualisiert wurde, wenn der Händler die Store-Ansicht wechselte.

_10. Oktober 2023_

![Neu](../assets/new.svg) - Es wurden neue Bestellstatusereignisse hinzugefügt: [Bestellungen angefordert](events-backoffice.md#orderinvoiced), [Auftragselementrückgabe initiiert](events-backoffice.md#orderitemsreturninitiated) und [Bestellartikel zurückgegeben abgeschlossen](events-backoffice.md#orderitemreturncompleted).
![Korrektur](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem Währungskonfigurationsänderungen nach der Aktualisierung des Caches nicht in den Ereignissen übernommen wurden.
![Fehlerbehebung](../assets/fix.svg) - Es wurde ein Fehler behoben, der auftrat, wenn bei Aktivierung der asynchronen Bestellplatzierung keine Bestellbestätigungsmeldung angezeigt wurde.
![Neu](../assets/new.svg) - Daten wurden zum Ereignis [addToRequisitionList](events.md#addtorequisitionlist) für einfache Produkte auf der Seite &quot;Kategorieansicht&quot;hinzugefügt.
![Korrektur](../assets/fix.svg) - Es wurde ein Problem in den `selectedOptions` -Daten im [addToRequisitionList](events.md#addtorequisitionlist) -Ereignis behoben, das auftrat, wenn Produkte von der Bestellbestätigungsseite hinzugefügt wurden.
![Neu](../assets/new.svg) - Produktdaten wurden zum Ereignis [addToRequisitionList](events.md#addtorequisitionlist) hinzugefügt, wenn Produkte von der Seite &quot;Kategorieansicht&quot;zur Anforderungsliste hinzugefügt werden.
![Neu](../assets/new.svg) - Das Ereignis [addToRequisitionList](events.md#addtorequisitionlist) wurde hinzugefügt, wenn konfigurierbare Produkte von der Produktansichtsseite zur Anforderungsliste hinzugefügt werden.
![Neu](../assets/new.svg) - Es wurden die Ereignisse [addToRequisitionList](events.md#addtorequisitionlist) und [removeFromRequisitionList](events.md#removefromrequisitionlist) hinzugefügt, wenn die Produktmenge von einer Anforderungsliste erhöht und/oder verringert wird.

_10. Juni 2023_

![Korrektur](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem `orderId` aufgrund von Präfixen in der Commerce-Bestellkennung nicht im Kontext übergeben wurde.
![Fehlerbehebung](../assets/fix.svg) - Aktualisierte Konfigurationen für Inhaltssicherheitsrichtlinien.

_30. März 2023_

![Neu](../assets/new.svg) - Es wurde eine Erweiterung mit dem Namen `data-services-b2b` hinzugefügt, die [Ereignisse auf der Anforderungsliste](events.md#b2b-events) für B2B-Händler enthält.
![Neu](../assets/new.svg) - Das Feld `uniqueIdentifier` wurde zu den Ereignissen [Suche](events.md#search-events) hinzugefügt. Dieses neue Feld ermöglicht Händlern, auf Suchanfragen und Suchantworten zu verweisen.

_12. Oktober 2022_

![Neu](../assets/new.svg) - Dem Adobe Commerce Storefront Events SDK und Collector wurden zwei [Storefront-Ereignisse](events.md), `openCart` und `removeFromCart` hinzugefügt.
![Neu](../assets/new.svg) - Unterstützung für eine [AEM Storefront](overview.md#aem-support) hinzugefügt.

+++

## 3.2.0

_7. Oktober 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, [benutzerdefinierte Bestellattribute](custom-attributes.md) zu erstellen, um Bürodaten zu sichern.
![Neu](../assets/new.svg) - Die neue Tabelle [Benutzerdefinierte Bestellattribute](connect-data.md#data-customization) wurde hinzugefügt, damit Sie alle benutzerdefinierten Attribute anzeigen können, die in [!DNL Commerce] konfiguriert und an Experience Platform gesendet wurden.
![Neu](../assets/new.svg) - [Möglichkeit zum Sammeln und Senden von Profildatensätzen](connect-data.md#send-customer-profile-data) und Daten an Experience Platform hinzugefügt.

## 3.2.0-beta3

_27. August 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Wenn Sie an der Beta-Phase teilnehmen, stellen Sie sicher, dass Ihre `composer.json`-Datei auf der Stammebene Folgendes aufweist: ` "minimum-stability": "beta"`. Fügen Sie außerdem `composer require "magento/customers-connector: ^1.2.0"` hinzu, um Kundenprofile von Ihrer Commerce-Instanz an SaaS zu senden.
![Neu](../assets/new.svg) - Diese Version enthält die in Version 3.1.1, 3.1.2, 3.1.3 und 3.1.4 veröffentlichten Patches.

## 3.1.4

_9. August 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Korrektur](../assets/fix.svg) - Das `experience-platform-connector` -Metapaket wurde aktualisiert, um zusätzliche nicht verwendete Datenexporteure und -indizierer zu entfernen.

## 3.1.3

_22. Juli 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Korrektur](../assets/fix.svg) - Das `experience-platform-connector` -Metapaket wurde aktualisiert, um nicht verwendete Datenexporteure und Indexer zu entfernen.

## 3.1.2

_5. Juni 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Korrektur](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem beim Initiieren einer [historischen Synchronisierung](connect-data.md#specify-order-history-date-range) das falsche Datumsformat verwendet wurde.
![Korrektur](../assets/fix.svg) - Es wurde ein Problem behoben, bei dem das [startCheckout](events.md#startcheckout) -Ereignis nicht in Adobe Commerce 2.4.7 gesendet wurde.

## 3.1.1

_4. April 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Unterstützung für PHP 8.3 für alle [!DNL Data Connection] Erweiterungen hinzugefügt.
![Neu](../assets/new.svg) - Es wurde ein Artikel zur [Integration](mobile-sdk-epc.md) des Adobe Experience Platform Mobile SDK mit Commerce hinzugefügt.

## 3.2.0-beta2

_4. März 2024_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Wenn Sie an der Beta-Phase teilnehmen, stellen Sie sicher, dass Ihre `composer.json`-Datei auf der Stammebene Folgendes aufweist: ` "minimum-stability": "beta"`. Fügen Sie außerdem `composer require "magento/customers-connector: ^1.2.0"` hinzu, um Kundenprofile von Ihrer Commerce-Instanz an SaaS zu senden.
![Neu](../assets/new.svg) - Zusätzliche Funktion zum Hinzufügen benutzerdefinierter Attribute [](custom-attributes.md).
![Neu](../assets/new.svg) - [Möglichkeit zum Sammeln und Senden von Profildatensätzen](connect-data.md#send-customer-profile-data) und Daten an Experience Platform hinzugefügt.

## 3.1.0

_16. November 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) - Der Experience Platform-Connector wurde in [!DNL Data Connection] umbenannt.
![Fehlerbehebung](../assets/fix.svg) - Es wurde die Möglichkeit hinzugefügt, Fehlerantworten zu protokollieren, wenn Adobe IMS das Zugriffstoken nicht generieren kann.
![Fehlerbehebung](../assets/fix.svg) - Es wurde eine Benachrichtigungsmeldung hinzugefügt, wenn Sie versuchen, historische Bestellungen zu synchronisieren, aber keine Kontoanmeldeinformationen angegeben haben.

## 3,0,0

_10. Oktober 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

Dies ist eine Hauptversion. [Bearbeiten Sie](install.md#update-the-data-connection) die Datei &quot;root composer.json&quot;Ihres Projekts.

![Neu](../assets/new.svg) - Allgemeine Verfügbarkeit, um [historische Bestelldaten und -status](connect-data.md#send-historical-order-data) an die Experience Platform zu senden.
![Neu](../assets/new.svg) - Unterstützung für OAuth 2.0 bei der [Konfiguration](connect-data.md#connect-commerce-data-to-adobe-experience-platform) der Erweiterung [!DNL Data Connection] hinzugefügt.
![Neu](../assets/new.svg) - Die Unterstützung für Adobe Commerce 2.4.3 wurde eingestellt.

## 2,3,0

_27. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - [Möglichkeit zum Deaktivieren des Versands von Storefront-Ereignissen](connect-data.md#data-collection) an die Experience Platform wurde hinzugefügt.
![Fehlerbehebung](../assets/fix.svg) - Aktualisierte Konfigurationen für Inhaltssicherheitsrichtlinien.
![Fehlerbehebung](../assets/fix.svg) - Die Unterstützung für Backoffice-Ereignisse in Commerce 2.4.7 wird jetzt nicht mehr unterstützt.
![Neu](../assets/new.svg) - Es wurde eine Benachrichtigung zur Cache-Invalidierung hinzugefügt, wenn Sie Änderungen am [!DNL Data Connection]-Erweiterungsformular speichern.

## 3.0.0-beta1 (nur intern)

_13. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - (Beta) Es wurde die Möglichkeit hinzugefügt, [historische Bestelldaten und -status](connect-data.md#beta-send-historical-order-data) an die Experience Platform zu senden.

## 2,2,0

_30. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Bündelt die Abhängigkeiten `commerce-data-export` und `saas-export` mit der Erweiterung `experience-platform-connector`. Zuvor mussten Sie diese Abhängigkeiten separat installieren. Diese Abhängigkeiten ermöglichen zusammen mit der Händlerkonfiguration die serverseitige Verarbeitung von [Back-Office-Ereignissen](events-backoffice.md).
![Neu](../assets/new.svg) - Es wurde ein neues Back-Office-Ereignis namens [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted) hinzugefügt.

## 2.1.1

_28. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Unterstützung für PHP 8.2 für alle [!DNL Data Connection] Erweiterungen hinzugefügt.

## 2.1.0

_17. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Die [[!DNL Data Connection] Erweiterung Admin](connect-data.md) wurde aktualisiert, sodass Sie Ihr eigenes AEP Web SDK (Legierung) angeben können.
![Korrektur](../assets/fix.svg) Änderung an der Verwendung von `identityMap` anstelle von `personID`, wenn die primäre Identität für alle Daten festgelegt wird, die an die Kante gesendet werden.

## 2,0,1

_10. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) - Jetzt wird der Adobe Experience Platform-Kontext erst festgelegt, nachdem das Storefront Event Collector und Storefront Event SDK erfolgreich geladen wurden.

## 2,0,0

_12. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Es wurde die Möglichkeit hinzugefügt, Ihr eigenes AEP-Web-SDK anzugeben, wenn [Ihre Adobe Commerce-Instanz mit dem Experience Platform verbindet](connect-data.md).
![Fehlerbehebung](../assets/fix.svg) - Aktualisierte Datenastream-Reichweitenanforderung, sodass die Datastream-IDs auf die Website übertragen werden müssen, anstatt sie zu überprüfen.

## 1,0,0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) - Allgemeine Verfügbarkeit
