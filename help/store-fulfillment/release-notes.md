---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Versionshinweise'
description: "Lesen Sie die Versionshinweise, um Informationen zu allen [!DNL Store Fulfillment by Walmart Commerce Technologies] veröffentlicht."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Store Fulfillment Services by Walmart Commerce Technologies] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Siehe [Bevorstehende Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Produktverfügbarkeit](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) , um zu erfahren, welche Adobe Commerce-Versionen diese Erweiterung unterstützen.

## v1.5.0

*3. August 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}[Adobe Commerce 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), einschließlich der Sicherheits-Patch-Versionen 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4

Diese Version enthält die folgenden Aktualisierungen:

![Neu](../assets/fix.svg) Die Erweiterung wurde aktualisiert, um [Adobe Commerce-Sicherheits-Patch-Versionen](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 und 2.4.4-p4.

![Neu](../assets/new.svg)<!-- WMTP-918 --> Unterstützung für die [Asynchrones Senden](sales-emails.md) Konfigurationsoption für E-Mails zum Verkauf. Merchants, die auf Version 1.5.0 aktualisieren, haben die Möglichkeit, E-Mails sofort (Standard) oder asynchron zu senden.

![Neu](../assets/new.svg)<!-- WMTP-916--> Die [Quellkonfiguration](merchant-store-configuration.md) zur Unterstützung internationaler Telefonnummernformate.

![Neu](../assets/new.svg) Es wurde eine Logik hinzugefügt, um zu verhindern, dass Erstattungsbeträge den verbleibenden oder fakturierten Betrag überschreiten.

![Neu](../assets/new.svg)<!-- WMTP-882 --> Ersetzt `google.map.LatLng` -Objekt mit JSON-Literalen zur Unterstützung der Kompatibilität mit älteren Versionen von [!DNL Google Maps].

![Problem behoben](../assets/fix.svg)<!-- WMTP- --> Das Skript zum Erstellen der `[!DNL Available for Store Pickup]` und `[!DNL Available for Home Delivery]` Produktattribute, um Konflikte mit Attributkategorien zu vermeiden.

![Problem behoben](../assets/fix.svg)<!-- WMTP-915 --> Es wurde ein Kompatibilitätsproblem behoben, das beim Laden und Speichern einiger Entitäten zu einer Endlosschleife führte.

![Problem behoben](../assets/fix.svg)<!-- WMTP-921 --> Es wurde ein Problem behoben, durch das [!DNL Ship to Store] Anführungszeichenvalidierung ausgelöst wird, wenn ein Artikel aus einer Produktdetailseite (PDP) zum Warenkorb hinzugefügt wird.

![Problem behoben](../assets/fix.svg)<!-- WMTP- 932 --> Es wurde ein Fehler beim Checkout behoben, der Kunden die Auswahl der Versandmethode für die Startseite für Artikel ermöglichte, die nicht für den Heimangebot geeignet sind.

![Problem behoben](../assets/fix.svg) Aktualisierungen der Installation:

- <!-- WMTP-880--> Fehlerkorrektur - bei der Installation der [!DNL Store Fulfillment] -Erweiterung.

- <!-- WMTP-878--> Es wurde ein Problem bei SKU-Ganzzahlen behoben, bei dem der Datentyp während der Installation in den String-Typ umgewandelt werden musste.

![Problem behoben](../assets/fix.svg)<!-- WMTP-915--> Fehlerkorrektur - kein Fehler mehr durch einen fehlenden Checkin-Fehlercode.

![Problem behoben](../assets/fix.svg)<!-- WMTP-932 --> Fehlerkorrektur - Es wurde ein Fehler behoben, der im Zusammenhang mit partiellen Ablehnungen während der Ausgabevorgänge auftrat.

![Neu](../assets/new.svg)<!-- WMTP-953 --> Aktualisierung des API-Endpunkts Abbrechen , um den Statusparameter als optionales Objekt zu verwenden.

![Neu](../assets/new.svg)<!-- WMTP-960 --> Verbesserte Protokollierungsdetails für den API-Endpunkt &quot;Trennen&quot;.

## v1.4.0

*13. April 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit [!DNL Adobe Commerce] 2.4.4 bis 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27. Februar 2023*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg)<!-- WMTP-795 --> Es wurde die Möglichkeit hinzugefügt, die Store Fulfillment-Lösung für eine bestimmte Site zu deaktivieren, indem der Standardbereich für die Systemkonfigurationseinstellung von der Website in &quot;global&quot;geändert wird.

## v1.2.0

*27. September 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Diese Version enthält die folgende Aktualisierung:

![Neu](../assets/fix.svg) [!DNL Store Fulfillment] ist jetzt [kompatibel mit [!DNL Adobe Commerce] 2.4.4 bis 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15. Juli 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

![Neu](../assets/fix.svg)<!-- WMTP-731 --> Vereinfachtes [Konfiguration des Check-in-Erlebnisses](check-in-experience-setup.md) für die Store Assist-App durch Hinzufügen der standardmäßigen Automarken- und Modellauswahl. In der vorherigen Version mussten Händler die Automobil- und Modellauswahl manuell konfigurieren.

## v1.0.0

*4. März 2022*

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Stabilität: Allgemeine Verfügbarkeit

## Store Assist App

Informationen zu neuen Versionen der Store-Hilfe-App finden Sie in den App-Informationen im [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
