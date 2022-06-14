---
title: '"[!DNL Payment Services] Versionshinweise"'
description: Informationen zu allen [!DNL Payment Services] veröffentlicht.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Siehe [Bevorstehende Versionen](https://devdocs.magento.com/release/) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://devdocs.magento.com/release/availability.html) in der Entwicklerdokumentation , um mehr über die Produktkompatibilität zu erfahren.

## v1.1.0

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[!DNL Payment Services] ist jetzt [kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist jetzt für kanadische Händler verfügbar. Merchandising kann die Zahlungskonfiguration in einer der beiden [französisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) oder [englisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Kanadische Dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) für Kreditkarten und PayPal-Transaktionen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Händler können [Onboard [!DNL Payment Services]](onboard.md) Erweiterung in englischer oder französischer Sprache.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können nun Finanzberichte anzeigen, sowohl die [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), in kanadischen Dollar (CAD).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ist jetzt kompatibel mit [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbesserter Warnhinweis im Sandbox-Modus zur Anzeige ordnungsgemäßer Warnhinweise mit mehreren Stores.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> Sie können jetzt verfügbare Zahlungsmethoden wie Venmo auf der Store-Ansichtsebene aktivieren und deaktivieren. Bisher konnten Sie nur Zahlungsmethoden pro Website konfigurieren.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2277 --> Sie können jetzt selektiv [Aktivieren oder Deaktivieren einzelner PayPal-Smart-Schaltflächen](settings.md#paypal-smart-buttons).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der _Überprüfungsreihenfolge_ Seite.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> Testen von Kreditkartentransaktionen [kann bei PayPal fehlschlagen](https://support.magento.com/hc/en-us/articles/5201041963917) bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung.

## v1.0.0

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ist jetzt kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für [[!DNL Adobe Commerce] zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [Vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt [Sandbox-Konto](sandbox.md) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](settings.md) Erweiterung mit grundlegendem Zahlungsverhalten, z. B. unter Verwendung von [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) Wechsel zwischen Sandbox- oder Produktionsumgebungen.

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Ihre Kunden können mit [!DNL Payment Services] oder über [manuelle Auftragserstellung](create-order.md).

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> Umfassende Berichterstellung über [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), sind verfügbar für [!DNL Payment Services] um Ihnen einen klaren Überblick über die Bestellungen und die damit verbundenen Zahlungen Ihres Ladens zu geben.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt flexible gestaffelte Preise, die auf dem gesamten Verarbeitungsvolumen basieren und an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Sie können [Erscheinungsbild und Verhalten anpassen](payments-options.md) von PayPal Smart-Schaltflächen und Kreditkartenfeldern für die Zahlungsdiensterweiterung.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://support.magento.com/hc/en-us/articles/4406603542541) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) mit der richtigen `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] Berichte [kann nicht sofort synchronisiert werden](https://support.magento.com/hc/en-us/articles/4406114741517).

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> Ihre [PayPal-Sandbox-Konto](https://support.magento.com/hc/en-us/articles/4406954952461) für [!DNL Payment Services] kann nicht überprüft werden, wenn Sie dieses Konto beim Onboarding erstellen.
