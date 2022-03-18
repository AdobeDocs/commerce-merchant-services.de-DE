---
title: '"[!DNL Payment Services] Versionshinweise"'
description: Informationen zu allen [!DNL Payment Services] veröffentlicht.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

## v1.0.0

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeines Release zur Verfügbarkeit. [Zahlungsdienste](https://marketplace.magento.com/magento-payment-services.html) ist jetzt mit den Adobe Commerce- und Magento Open Source-Versionen 2.4.0 bis 2.4.3-p1 kompatibel.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] -Erweiterung für Adobe Commerce und Magento Open Source kann entweder für [Adobe Commerce auf Cloud-Infrastruktur](install.md#magento-commerce-cloud) oder [Vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt [Sandbox-Konto](onboard.md#enable-sandbox-testing) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](configure-admin.md) Erweiterung mit grundlegenden Zahlungsverhaltensweisen (wie z. B. der gemeinsamen Auth-Erfassung und dem Wechsel zwischen Sandbox- oder Produktionsumgebungen).

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Käufer können mit [!DNL Payment Services] oder Sie können die Bestellung über das Telefon und [Erstellen einer ganzen Bestellung](create-order.md) im Admin für sie.

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] bieten Händlern umfassende Berichte, sodass Sie einen klaren Überblick über Ihre Bestellungen und Zahlungen erhalten.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt mehrstufige Preise (basierend auf TPV), die an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Es ist möglich, das Erscheinungsbild der PayPal-Schaltflächen und der CC-Felder für die [Zahlungsdienste](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) -Erweiterung.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://support.magento.com/hc/en-us/articles/4406603542541) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) korrekt `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [Berichte](https://support.magento.com/hc/en-us/articles/4406114741517) für die Zahlungsauszahlung und den Status der Bestellauszahlung kann nicht sofort synchronisiert werden.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal-Sandbox-Konto](https://support.magento.com/hc/en-us/articles/4406954952461) für [!DNL Payment Services] kann nicht überprüft werden.
