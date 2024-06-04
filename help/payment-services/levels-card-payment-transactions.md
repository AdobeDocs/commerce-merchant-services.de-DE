---
title: Verarbeitung der Stufe 2 und Stufe 3
description: Bearbeitungsstufen der Kartenzahlungen [!DNL Payment Services] Transaktionen.
role: Admin
feature: Payments
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Verarbeitung der Stufe 2 und Stufe 3

Es gibt drei Stufen der Kartenverarbeitung, die über [!DNL Payment Services]:

* Stufe 1 ist die häufigste, erfordert weniger Informationen und daher im Allgemeinen höhere Interbankenentgelte im Vergleich zu Transaktionen, die mit Level 2- oder Level 3-Daten verarbeitet werden, die normalerweise mit Unternehmens- und Kaufkreditkarten zusammenhängen.

* bei Stufe 2 und Stufe 3, [!DNL Payment Services] Kunden mit Interchange plus (IC++)-Preisen, die eine große Menge an Kundenkarte- oder Unternehmenskartengeschäften akzeptieren, können möglicherweise eine niedrigere Verarbeitungsrate erhalten, indem sie [!DNL Payment Services] , um weitere Informationen zu einer Transaktion zu senden. Wenn die Transaktion gemäß den Anforderungen an das Kartennetz qualifiziert ist, kann der Händler eine niedrigere Verarbeitungsrate für eine bestimmte Transaktion erhalten.

>[!NOTE]
>
>Die Preise der Stufe 2 und der Stufe 3 gelten nur für Visa- und MasterCard-Transaktionen. American Express bietet nur Preise der Stufe 2 an. Discover bietet weder Preise der Stufe 2 noch der Stufe 3 an. Siehe [Zahlungsverarbeitung](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} Weitere Informationen finden Sie in der PayPal Developer-Dokumentation .

Siehe [Was ist IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} Weitere Informationen finden Sie in der PayPal-Entwicklerdokumentation .

Die Verarbeitungsdaten der Stufe 2 und 3 ermöglichen es den Händlern, ihre IC+-Preise zu senken, wenn sie zusätzliche Details zum Kauf bereitstellen, die das Prozessorrisiko reduzieren und nützliche Aspekte bieten:

* Große Kunden zahlen weniger, indem sie diese Verarbeitungsdaten bereitstellen.

* Bei Kunden ist es weniger wahrscheinlich, dass sie in betrügerische Situationen geraten, da die Bestellungen mehr Informationen enthalten.

Kartennetze wie Visa und Mastercard bestimmen jedoch letztendlich, ob eine Transaktion für die Verarbeitung auf Stufe 2 oder Stufe 3 qualifiziert ist:

* Daten der Stufe 2 enthalten zusätzliche Informationen, wie den Steuerbetrag für die Bestellung, den Kundencode oder die Bestellnummer.

* Die Daten der Stufe 3 sind detailliertere Informationen über den Verkauf, was dazu beiträgt, im Vergleich zu Stufe 2 noch niedrigere Interbankenentgelte in Anspruch zu nehmen. Daten der Stufe 3 enthalten Informationen wie eine Beschreibung des gekauften Artikels, die Menge der gekauften Artikel, die Maßeinheit für die bestellten Artikel und andere spezifische Details.

[!DNL Payment Services] erfasst diese Daten und erstellt detaillierte Berichte über Ihre Zahlungsvorgänge.

## Kartenzahlvorgänge der Stufe 2 und der Stufe 3 [!DNL Payment Services]

Um für die Verarbeitung auf Stufe 2 oder Stufe 3 qualifiziert zu sein, müssen Händler die vorherigen Informationen übermitteln, obwohl es die Kartennetzwerke sind, die letztendlich bestimmen, für welche Stufe eine Transaktion bei der Verarbeitung qualifiziert ist.

Siehe [Häufig gestellte Fragen zur Zahlungsverarbeitung](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} Weitere Informationen finden Sie in der PayPal-Entwicklerdokumentation .

Die Verarbeitung der Stufen 2 und 3 ist standardmäßig für deaktiviert. [!DNL Payment Services] Händler auf Store-Ebene.

Die Verarbeitung auf Stufe 2 und Stufe 3 ist verfügbar, wenn Sie bereits IC+-Preise verwenden. Um diese Funktion zu aktivieren, können Sie dies über die [Befehlszeilenschnittstelle (CLI)](configure-cli.md).

>[!IMPORTANT]
>
>Bei Fragen wenden Sie sich bitte an Ihre [!DNL Payment Services] Kundenbetreuer.
