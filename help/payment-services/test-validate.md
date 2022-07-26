---
title: Testen und Validieren
description: Durch Tests und Validierung wird sichergestellt, dass [!DNL Payment Services] Funktionen funktionieren erwartungsgemäß und bieten beste Zahlungsoptionen für Ihre Kunden
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 41d93ffc2f9d518d9d4cf4abf2d53484821c13f2
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Testen und Validieren

Bevor Sie [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] Für Ihre Kunden ist es empfehlenswert, in Ihrer Sandbox-Umgebung zu testen. _und_ in der Produktion. Durch Tests und Validierung wird sichergestellt, dass [!DNL Payment Services] Funktionen funktionieren erwartungsgemäß und bieten die besten Zahlungsoptionen für Ihr Geschäft und Ihre Kunden.

## Test in Sandbox-Umgebung

Test [!DNL Payment Services] in einer Sandbox-Umgebung ist ein wichtiger Validierungsschritt, auch wenn es sich um eine simulierte Umgebung handelt, die nur mit der PayPal-Sandbox verbunden ist, nicht mit echten Banken und Händlern.

1. Führen Sie einen erfolgreichen Checkout aus Ihrem Store durch, indem Sie [Kreditkartenfelder](payments-options.md#credit-card-fields) oder eines der [PayPal Smart-Schaltflächen](payments-options.md#paypal-smart-buttons). Siehe [Testen von Anmeldeinformationen](#testing-credentials) für weitere Informationen zur Verwendung von gefälschten Kreditkarten zum Testen.
1. Erfassen (wenn Ihre Zahlungsaktion ausgeführt wird) [auf `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [Rückerstattung](refunds.md)oder [void](voids.md) die gerade ausgefüllte Bestellung. Sie können auch einfach [eine Rechnung erstellen](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;} für eine Bestellung, wenn Ihre Zahlungsaktion auf `Authorize` anstelle von `Authorize and Capture`.
1. Zeigen Sie die Transaktion und andere Informationen innerhalb von 24-48 Stunden im [Zahlungsbericht](payouts.md).
1. Weitere Informationen zur Bestellung finden Sie im Abschnitt [Bestellstatusbericht](order-payment-status.md).

### Testen von Anmeldeinformationen

Beim Testen und Validieren Ihrer Sandbox müssen Sie gefälschte Kreditkartennummern verwenden, damit Sie keine echten Gebühren für ein bestehendes Kreditkartenkonto erstellen.

Verwenden Sie den Kreditkartengenerator von PayPal, um [Generieren von zufälligen Kreditkarteninformationen](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) für Tests.

Zum Testen der Apple-Bezahlung im Sandbox-Modus benötigen Sie eine [Apple-Entwicklerkonto](https://developer.apple.com/programs/enroll/), inklusive gefälschter Kreditkarten- und Rechnungsinformationen.

>[!NOTE]
>
>PayPals Sandbox-Zahlungsverarbeitung ist manchmal langsam und der Service kann gelegentlich ausfallen. Diese Situation ist kein Hinweis auf die Geschwindigkeit und Effizienz der Verarbeitung der Zahlungen für lebende Erzeugnisse.

## Produktionstest

Es wird dringend empfohlen, [!DNL Payment Services] in der Produktion, mit echten Kreditkarten und Banken, bevor sie diese Funktionalität den Käufern zur Verfügung stellen. Auch bei Tests [!DNL Payment Services] In Sandboxes ist es wichtig, dass Produktionstests die am wenigsten sichere Methode sind, um sicherzustellen, dass [!DNL Payment Services] funktioniert erwartungsgemäß.

Sie können [!DNL Payment Services] in der Produktion auf zwei Arten:

* Wählen Sie einen Zeitpunkt aus, zu dem Sie wissen, dass die Käufer keine Bestellungen tätigen.
* Verwenden Sie einen Webstore, auf den Kunden vorübergehend nicht zugreifen können, der Ihnen aber zum Testen zur Verfügung steht.

Führen Sie Ihre Produktionstests mit echten Kreditkarten und PayPal-Konten durch und testen Sie den gesamten Lebenszyklus einer Zahlung, einschließlich Erfassung und Rückerstattung. Durch das Abschließen des gesamten Checkout- und Zahlungsflusses während des Tests erhalten Sie ein klares Bild davon, wie Ihre [!DNL Payment Services] -Funktion funktioniert, wenn Live-Käufer sie verwenden.

Überprüfen Sie außerdem, ob die in den Bankausweisen angezeigten Informationen für die Zahlungsmethoden, die Sie in Produktionstests verwenden, korrekt und erwartet sind (einschließlich der Beschreibung Ihres Unternehmens).

>[!NOTE]
>
>Um die Produktionstests für Apple Pay abzuschließen, müssen Sie sich an den Vertrieb wenden, um Apple Pay für Ihre Produktionsumgebung zu aktivieren.
