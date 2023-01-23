---
title: Versionshinweise
description: Die aktuellen Versionsinformationen zum Adobe Experience Platform Connector von Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 975854dbdae32e5e51bb57593cf122627d01571f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# Versionshinweise

Diese Versionshinweise enthalten Aktualisierungen des Experience Platform-Connectors und umfassen:

* ![Neu](../assets/new.svg) - Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) - Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit vom Experience Platform-Connector verwendeten Erweiterungen finden Sie unter **Unterstützte Dienstaktualisierungen**.

Siehe [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) , um mehr über die Produktkompatibilität zu erfahren.

## Unterstützte Dienstaktualisierungen

In diesen Versionshinweisen werden Funktionsänderungen und Fehlerbehebungen im Zusammenhang mit Erweiterungen beschrieben, die vom Experience Platform-Connector verwendet werden.

+++Unterstützte Dienstaktualisierungen

_12. Oktober 2022_

* ![Neu](../assets/new.svg) - Zwei wurden hinzugefügt [Storefront-Ereignisse](events.md): `openCart` und `removeFromCart` zum Adobe Commerce Storefront Events SDK und Collector
* ![Neu](../assets/new.svg) - Unterstützung für eine [AEM Storefront](overview.md#aem-support)

+++

## 2.1.0

_17. Januar 2023_

* ![Neu](../assets/new.svg) - Die [Experience Platform Connector-Admin](connect-data.md) damit Sie Ihr eigenes AEP Web SDK (Legierung) angeben können. Außerdem wurde eine Option für Händler hinzugefügt, die in unserem Back-Office-Betaprogramm angemeldet sind, um [Back-Office-Ereignisdaten](connect-data.md#data-collection) an die Kante. Diese Ereignisse enthalten [Bestellstatusinformationen](events.md#beta-order-status-events) über eine Bestellung, z. B. wenn eine Bestellung aufgegeben, storniert, rückerstattet oder versandt wurde. Wenn Sie am Back Office Beta Programm teilnehmen möchten, wenden Sie sich an [drios@adobe.com](mailto:drios@adobe.com).
* ![Fehlerbehebung](../assets/fix.svg) Geändert zu mithilfe von `identityMap` anstelle von `personID` beim Festlegen der primären Identität für alle Daten, die an die Kante gesendet werden.

## 2.0.1

_10. November 2022_

* ![Problem behoben](../assets/fix.svg) - Jetzt wird der Adobe Experience Platform-Kontext erst festgelegt, nachdem das Storefront Event Collector und Storefront Event SDK erfolgreich geladen wurden.

## 2.0.0

_12. Oktober 2022_

* ![Neu](../assets/new.svg) - Zusätzliche Möglichkeit zur Angabe Ihres eigenen AEP Web SDK bei [Verbindung](connect-data.md) Ihre Adobe Commerce-Instanz an die Experience Platform
* ![Fehlerbehebung](../assets/fix.svg) - Die Anforderung zum Datenspeicherbereich wurde aktualisiert, sodass die Datastream-IDs auf die Website übertragen werden müssen, anstatt sie zu speichern

## 1.0.0

_9. August 2022_

* ![Neu](../assets/new.svg) - Allgemeine Verfügbarkeitsversion

## Dokumentation

Weitere Informationen:

* [Adobe Commerce-Entwicklerdokumentation](https://devdocs.magento.com/)
* [Adobe Commerce-Benutzerhandbuch](https://docs.magento.com/user-guide/)
