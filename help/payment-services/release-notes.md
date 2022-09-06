---
title: '"[!DNL Payment Services] Versionshinweise"'
description: Informationen zu allen [!DNL Payment Services] veröffentlicht.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 1f88c66d0c12dcde2c8fdde1dd3b4838ae6d462d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen, die außerhalb der regulären Version der Funktionen veröffentlicht wurden, finden Sie in den Abschnitten gehostete Dienstaktualisierungen .

Siehe [Bevorstehende Versionen](https://devdocs.magento.com/release/) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://devdocs.magento.com/release/availability.html) in der Entwicklerdokumentation , um mehr über die Produktkompatibilität zu erfahren.

## Aktualisierungen gehosteter Dienste

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Versionen der gehosteten Funktionen für den gehosteten Dienst veröffentlicht wurden.

+++Hosting-Dienstaktualisierungen

_31. August 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3629 --> Wenn ein neuer Händler zum ersten Mal auf die Zahlungsdienst-Startseite zugreift, wird die Seite jetzt sofort geladen, um den Inhalt anzuzeigen, anstatt dass eine Seitenaktualisierung erforderlich ist.

_9. August 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay ist jetzt als PayPal Smart Button verfügbar. Diese [Zahlungsoption](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) ermöglicht es Kunden, die Touch-ID-Funktion auf ihrem iOS- oder macOS-Gerät zu verwenden, um Apple Pay auszuwählen. Apple Pay verarbeitet die Zahlung mit den auf dem Gerät gespeicherten Zahlungsberechtigungen für Kredit- und Debitkarten.

_28. Juni 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-1720 --> Streitigkeiten über Store-Bestellungen sind jetzt verfügbar unter [den Bericht über den Auftragszahlungsstatus](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Sie können bei Streitigkeiten direkt zum PayPal-Abwicklungszentrum navigieren von [!DNL Payment Services].

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Verbesserungen des Benutzererlebnisses aus [!DNL Payment Services] Zu den Startseiten gehören die Möglichkeit, eine Konfiguration auf der aktuellen Vererbungsebene zu ändern, sowie Verbesserungen bei der Anzeige der Kopfzeile und der Navigation.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Jetzt werden Warnungen angezeigt, wenn Sie vom Sandbox-Modus zum Produktionsmodus wechseln und versuchen, von einer Ansicht mit nicht gespeicherten Aktualisierungen weg zu navigieren.

![Neu](../assets/new.svg)<!-- Issue PAY-2761 --> Sie können jetzt die Daten anpassen, die im [Bestellstatusbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) und [Zahlungsbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) durch Einblenden oder Ausblenden von Spalten mithilfe des Steuerelements Spalteneinstellungen.

+++

## v1.3.1

_6. September 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3663 --> Wenn der Store eines Händlers eine Bestellung erfasst, die mit einer nicht globalen Währung autorisiert ist, wird der Erfassungsvorgang abgeschlossen und es wird kein Fehler angezeigt.

## v1.3.0

_9. August 2022_

![Neu](../assets/new.svg)<!-- Issue PAY-XX --> Version der allgemeinen Verfügbarkeit -[!DNL Payment Services] ist jetzt [kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ist jetzt mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop kompatibel.

## v1.2.0

_29. Juni 2022_

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay ist nicht mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop kompatibel. Bei Verwendung von Safari Version 15.5 können Sie den Checkout nicht mit Apple Pay abschließen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3264 --> Bisher ist der Checkout fehlgeschlagen, wenn ein angemeldeter Benutzer eine andere Abrechnungs-/Lieferadresse als die Standardadresse für sein Konto ausgewählt hat. Dieses Problem wurde behoben. Jetzt wird die ausgewählte Abrechnungs-/Lieferadresse gesendet (anstelle der gespeicherten Standardadresse) und der Checkout erfolgreich abgeschlossen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3314 --> Wenn Sie die PayPal Smart-Schaltflächen zum Auschecken deaktivieren, werden keine Fehler angezeigt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3330 --> Zahlungen schlagen beim Checkout nicht mehr fehl, wenn ein Gastbenutzer eine Telefonnummer mit Bindestrichen eingibt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Wenn die Anmeldedaten für Commerce Services ungültig sind, wird die [!DNL Payment Services] Die Startseite wird jetzt in der Admin-Konsole angezeigt. Es wird ein Berechtigungsfehler angezeigt, der Sie darauf hinweist, dass Ihre Anmeldedaten ungültig sind.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] ist derzeit inkompatibel mit `commerce-data-export` v101.20 und höher, wodurch sie mit dem [[!DNL Channel manager] Erweiterung](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31. März 2022_

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[!DNL Payment Services] ist jetzt [kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist jetzt für kanadische Händler verfügbar. Merchandising kann die Zahlungskonfiguration in einer der beiden [französisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) oder [englisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Kanadische Dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) für Kreditkarten und PayPal-Transaktionen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Händler können [Onboard [!DNL Payment Services]](onboard.md) Erweiterung in englischer oder französischer Sprache.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können nun Finanzberichte anzeigen, sowohl die [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), in kanadischen Dollar (CAD).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ist jetzt kompatibel mit [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbesserter Warnhinweis im Sandbox-Modus zur Anzeige ordnungsgemäßer Warnhinweise mit mehreren Stores.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> Sie können jetzt verfügbare Zahlungsmethoden wie Venmo auf der Store-Ansichtsebene aktivieren und deaktivieren. Bisher konnten Sie nur Zahlungsmethoden pro Website konfigurieren.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2277 --> Sie können jetzt selektiv [Aktivieren oder Deaktivieren einzelner PayPal-Smart-Schaltflächen](settings.md#payment-buttons).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der _Überprüfungsreihenfolge_ Seite.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> Testen von Kreditkartentransaktionen [kann bei PayPal fehlschlagen](https://support.magento.com/hc/en-us/articles/5201041963917) bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung.

## v1.0.0

_29. November 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ist jetzt kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für [[!DNL Adobe Commerce] zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [Vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt [Sandbox-Konto](sandbox.md) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](settings.md) Erweiterung mit grundlegendem Zahlungsverhalten, z. B. unter Verwendung von [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) Wechsel zwischen Sandbox- oder Produktionsumgebungen.

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Ihre Kunden können mit [!DNL Payment Services] oder über [manuelle Auftragserstellung](create-order.md).

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> Umfassende Berichterstellung über [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), sind verfügbar für [!DNL Payment Services] um Ihnen einen klaren Überblick über die Bestellungen und die damit verbundenen Zahlungen Ihres Ladens zu geben.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt flexible gestaffelte Preise, die auf dem gesamten Verarbeitungsvolumen basieren und an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Sie können [Erscheinungsbild und Verhalten anpassen](payments-options.md) von PayPal-Smart-Schaltflächen und Kreditkartenfeldern für die [!DNL Payment Services] -Erweiterung.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://support.magento.com/hc/en-us/articles/4406603542541) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) mit der richtigen `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] Berichte [kann nicht sofort synchronisiert werden](https://support.magento.com/hc/en-us/articles/4406114741517).

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> Ihre [PayPal-Sandbox-Konto](https://support.magento.com/hc/en-us/articles/4406954952461) für [!DNL Payment Services] kann nicht überprüft werden, wenn Sie dieses Konto beim Onboarding erstellen.
