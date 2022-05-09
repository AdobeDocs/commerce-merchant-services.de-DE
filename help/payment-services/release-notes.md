---
title: '"[!DNL Payment Services] Versionshinweise"'
description: Informationen zu allen [!DNL Payment Services] veröffentlicht.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

## v1.1.0

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ist jetzt kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.4.

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist für kanadische Händler verfügbar. Merchandising kann die Zahlungskonfiguration in einer der beiden [französisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) oder [englisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Kanadische Dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) mit Kreditkarte und Paypal. Käufer können ein Einkaufserlebnis in ihrer bevorzugten Sprache haben, je nach Gebietsschema des Geschäfts, in dem sie einkaufen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Händler können [Onboard [!DNL Payment Services]](onboard.md) Erweiterung in der gewünschten Sprache.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können jetzt anzeigen [Finanzberichte](order-payment-status.md) in kanadischen Dollar (CAD).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ist jetzt kompatibel mit [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3035 --> Verbessertes Auschecken von Administratoren für die [!DNL Payment Services] -Erweiterung.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbesserter Warnhinweis im Sandbox-Modus zur Anzeige ordnungsgemäßer Warnhinweise mit mehreren Stores.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] ermöglicht die Aktivierung/Deaktivierung der verfügbaren Zahlungsmethoden wie Venmo auf der Storeebene.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2277 --> Die Fähigkeit des Händlers im Admin zur selektiven Deaktivierung/Aktivierung von PayPal-Smart-Schaltflächen wurde verbessert.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der _Überprüfungsreihenfolge_ Seite.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] verbessert die Bezeichnungen der Zahlungsmethoden im Admin.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://support.magento.com/hc/en-us/articles/4406603542541) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) korrekt `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [Berichte](https://support.magento.com/hc/en-us/articles/4406114741517) für die Zahlungsauszahlung und den Status der Bestellauszahlung kann nicht sofort synchronisiert werden.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal-Sandbox-Konto](https://support.magento.com/hc/en-us/articles/4406954952461) für [!DNL Payment Services] kann nicht überprüft werden, ob das Konto beim Onboarding erstellt wurde.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> [Testen der Kreditkarte](https://support.magento.com/hc/en-us/articles/5201041963917) mit PayPal bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung.

## v1.0.0

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeines Release zur Verfügbarkeit. [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html) ist jetzt kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für [[!DNL Adobe Commerce] zur Cloud-Infrastruktur](install.md#magento-commerce-cloud) oder [Vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt [Sandbox-Konto](onboard.md#enable-sandbox-testing) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](settings.md) Erweiterung mit grundlegenden Zahlungsverhaltensweisen (wie z. B. der gemeinsamen Auth-Erfassung und dem Wechsel zwischen Sandbox- oder Produktionsumgebungen).

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Käufer können mit [!DNL Payment Services] oder Sie können die Bestellung über das Telefon und [Erstellen einer ganzen Bestellung](create-order.md) im Admin für sie.

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] bieten Händlern umfassende Berichte, sodass Sie einen klaren Überblick über Ihre Bestellungen und Zahlungen erhalten.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt mehrstufige Preise (basierend auf TPV), die an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Es ist möglich, das Erscheinungsbild der PayPal-Schaltflächen und der CC-Felder für die [Zahlungsdienste](payments-options.md) -Erweiterung.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://support.magento.com/hc/en-us/articles/4406603542541) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) korrekt `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [Berichte](https://support.magento.com/hc/en-us/articles/4406114741517) für die Zahlungsauszahlung und den Status der Bestellauszahlung kann nicht sofort synchronisiert werden.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal-Sandbox-Konto](https://support.magento.com/hc/en-us/articles/4406954952461) für [!DNL Payment Services] kann nicht überprüft werden.
