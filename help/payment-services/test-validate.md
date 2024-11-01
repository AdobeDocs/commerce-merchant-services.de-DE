---
title: Testen und Validieren
description: Tests und Validierungen helfen sicherzustellen, dass die [!DNL Payment Services] Funktionen erwartungsgemäß funktionieren und die besten Zahlungsoptionen für Ihre Kunden bieten
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Testen und Validieren

Bevor Sie Ihren Kunden [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bereitstellen, sollten Sie in Ihrer Sandbox-Umgebung _und_ in der Produktion testen. Tests und Validierungen helfen sicherzustellen, dass die Funktionen von [!DNL Payment Services] erwartungsgemäß funktionieren und die besten Zahlungsoptionen für Ihren Store und Ihre Kunden bieten.

## Test in Sandbox-Umgebung

Das Testen von [!DNL Payment Services] in einer Sandbox-Umgebung ist ein wichtiger Validierungsschritt, auch wenn es sich um eine simulierte Umgebung handelt, die nur mit der PayPal-Sandbox verbunden ist, nicht mit echten Banken und Händlern.

1. Führen Sie einen erfolgreichen Checkout aus Ihrem Geschäft durch, entweder mit [Kreditkartenfeldern](payments-options.md#credit-card-fields) oder mit einem der [PayPal-Zahlungsschaltflächen](payments-options.md#paypal-smart-buttons). Weitere Informationen zur Verwendung gefälschter Kreditkarten zum Testen finden Sie unter [Testen von Anmeldeinformationen](#testing-credentials) .
1. Erfassen (wenn Ihre Zahlungsaktion auf `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method) eingestellt ist), [Rückerstattung](refunds.md) oder [void](voids.md) die gerade ausgefüllte Bestellung. [ Sie können auch einfach [eine Rechnung ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} für eine Bestellung erstellen, wenn Ihre Zahlungsaktion auf `Authorize` anstelle von `Authorize and Capture` eingestellt ist.
1. Sehen Sie sich die Transaktion und andere Informationen innerhalb von 24-48 Stunden im Bericht [Auszahlungen](payouts.md) an.
1. Weitere Informationen finden Sie im Bericht [Bestellstatus-Bericht](order-payment-status.md).

### Testen von Anmeldeinformationen

Beim Testen und Validieren Ihrer Sandbox müssen Sie gefälschte Kreditkartennummern verwenden, damit Sie keine echten Gebühren für ein bestehendes Kreditkartenkonto erstellen.

Verwenden Sie den Kreditkartengenerator von PayPal, um [zufällige Kreditkarteninformationen zu generieren](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157), um sie zu testen.

So testen Sie Apple Pay im Sandbox-Modus:

* Erstellen Sie ein [Apple-Sandbox-Tester-Konto](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) mit gefälschten Kreditkarten- und Rechnungsinformationen.
* [Registrieren Sie Ihre Sandbox-Domänen](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPals Sandbox-Zahlungsverarbeitung ist manchmal langsam und der Service kann gelegentlich ausfallen. Diese Situation ist kein Hinweis auf die Geschwindigkeit und Effizienz der Verarbeitung der Zahlungen für lebende Erzeugnisse.

## Produktionstest

Es wird dringend empfohlen, [!DNL Payment Services] in der Produktion mit echten Kreditkarten und Banken zu testen, bevor Sie diese Funktion den Käufern zur Verfügung stellen. Obwohl das Testen von [!DNL Payment Services] in der Sandbox wichtig ist, ist das Testen in der Produktion die törichteste Methode, um sicherzustellen, dass [!DNL Payment Services] erwartungsgemäß funktioniert.

Sie können [!DNL Payment Services] in der Produktion auf zwei Arten testen:

* Wählen Sie einen Zeitpunkt aus, zu dem Sie wissen, dass die Käufer keine Bestellungen tätigen.
* Verwenden Sie einen Webstore, auf den Kunden vorübergehend nicht zugreifen können, der Ihnen aber zum Testen zur Verfügung steht.

Führen Sie Ihre Produktionstests mit echten Kreditkarten und PayPal-Konten durch und testen Sie den gesamten Lebenszyklus einer Zahlung, einschließlich Erfassung und Rückerstattung. Wenn Sie den gesamten Checkout- und Zahlungsfluss während des Tests abschließen, erhalten Sie ein klares Bild davon, wie Ihre [!DNL Payment Services]-Funktion funktioniert, wenn Live-Käufer sie verwenden.

Überprüfen Sie außerdem, ob die in den Bankausweisen angezeigten Informationen für die Zahlungsmethoden, die Sie in Produktionstests verwenden, korrekt und erwartet sind (einschließlich der Beschreibung Ihres Unternehmens).

Um die Apple-Zahlung im Produktionsmodus zu testen, müssen Sie [Ihre Produktionsdomänen registrieren](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
