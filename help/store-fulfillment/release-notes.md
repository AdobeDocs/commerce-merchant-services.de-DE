---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Versionshinweise'
description: "In den Versionshinweisen finden Sie Informationen zu allen [!DNL Store Fulfillment by Walmart Commerce Technologies] Versionen."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Store Fulfillment Services by Walmart Commerce Technologies] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Korrektur des Problems](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Unter [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) erfahren Sie mehr über die Veröffentlichungszeitpläne und die Unterstützung.

Unter [Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) erfahren Sie, welche Adobe Commerce-Versionen diese Erweiterung unterstützen.

## v1.5.0

*3. August 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}[Adobe Commerce 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), einschließlich der Sicherheits-Patch-Versionen 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4

Diese Version enthält die folgenden Aktualisierungen:

![Neu](../assets/fix.svg) Die Erweiterung wurde aktualisiert, um die [Adobe Commerce-Sicherheits-Patch-Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4 zu unterstützen.

![Neu](../assets/new.svg)<!-- WMTP-918 --> Unterstützung für die Konfigurationsoption [Asynchrones Senden](sales-emails.md) für Verkaufs-E-Mails hinzugefügt. Merchants, die auf Version 1.5.0 aktualisieren, haben die Möglichkeit, E-Mails sofort (Standard) oder asynchron zu senden.

![Neu](../assets/new.svg)<!-- WMTP-916--> Die [Quellenkonfiguration](merchant-store-configuration.md) wurde aktualisiert, um internationale Telefonnummernformate zu unterstützen.

![Neu](../assets/new.svg) Es wurde eine Logik hinzugefügt, um zu verhindern, dass Erstattungsbeträge den verbleibenden oder fakturierten Betrag überschreiten.

![Neu](../assets/new.svg)<!-- WMTP-882 --> Das `google.map.LatLng` -Objekt wurde durch JSON-Literale ersetzt, um die Kompatibilität mit älteren Versionen von [!DNL Google Maps] zu unterstützen.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP- --> Das Skript, das die Produktattribute `[!DNL Available for Store Pickup]` und `[!DNL Available for Home Delivery]` erstellt, wurde aktualisiert, um Konflikte mit Attributkategorien zu vermeiden.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP-915 --> Korrektur eines Kompatibilitätsproblems, das beim Laden und Speichern einiger Entitäten zu einer Endlosschleife führte.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP-921 --> Korrektur des Fehlers, der verhindert hat, dass eine [!DNL Ship to Store] Anführungszeichenvalidierung ausgelöst wird, wenn ein Artikel über eine Produktdetailseite (PDP) zum Warenkorb hinzugefügt wird.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP- 932 --> Korrektur eines Checkout-Problems, das Kunden die Auswahl der Methode des Home-Versands für Artikel ermöglichte, die nicht für den Home-Versand infrage kommen.

![Problem behoben](../assets/fix.svg) Aktualisierungen der Installation:

- <!-- WMTP-880--> Es wurde ein Problem behoben, bei dem bei der Installation der Erweiterung [!DNL Store Fulfillment] ein falscher Website-Code zurückgegeben wurde.

- <!-- WMTP-878--> Es wurde ein Problem bei SKU-Ganzzahlen behoben, bei dem der Datentyp während der Installation in den String-Typ umgewandelt werden musste.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP-915--> Korrektur eines Fehlers, der durch einen fehlenden Checkin-Fehlercode verursacht wurde.

![Korrektur des Fehlers](../assets/fix.svg)<!-- WMTP-932 --> Fehlerkorrektur - Es wurde ein Fehler behoben, der bei Ausgabevorgängen zur teilweisen Zurückweisung führte.

![Neu](../assets/new.svg)<!-- WMTP-953 --> Der API-Endpunkt Abbrechen wurde aktualisiert, um den Statusparameter als optionales Objekt zu verwenden.

![Neu](../assets/new.svg)<!-- WMTP-960 --> Verbesserte Protokollierungsdetails für den API-Endpunkt &quot;Trennen&quot;.

## v1.4.0

*13. April 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit  [!DNL Adobe Commerce] 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27. Februar 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg)<!-- WMTP-795 --> Es wurde die Möglichkeit hinzugefügt, die Lösung zur Speicherbearbeitung für eine bestimmte Site zu deaktivieren, indem der Standardbereich für die Einstellung &quot;Systemkonfiguration&quot;von der Website in &quot;global&quot;geändert wird.

## v1.2.0

*27. September 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit  [!DNL Adobe Commerce] 2.4.4 bis 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15. Juli 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/fix.svg)<!-- WMTP-731 --> Die Konfiguration des Eincheckerlebnisses [3} für die Store Assist-App wurde vereinfacht, indem standardmäßige Automarken- und Modellauswahlen hinzugefügt wurden. ](check-in-experience-setup.md) In der vorherigen Version mussten Händler die Automobil- und Modellauswahl manuell konfigurieren.

## v1.0.0

*4. März 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

## Store Assist App

Informationen zu neuen Versionen der Store-Hilfe-App finden Sie in den App-Informationen im [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} oder im [Google Play Store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
