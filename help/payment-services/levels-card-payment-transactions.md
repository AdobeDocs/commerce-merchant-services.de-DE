---
title: Verarbeitung der Stufe 2 und Stufe 3
description: Kartenzahlungsstufe innerhalb von [!DNL Payment Services] Transaktionen.
role: Admin
feature: Payments
exl-id: db8993fe-dd6f-48b5-9e7b-69a0f2e08552
source-git-commit: 496817ecd0be3bffe53d8f596d922ff366212966
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Verarbeitung der Stufe 2 und Stufe 3

Es gibt drei Ebenen der Kartenverarbeitung, die über [!DNL Payment Services] verfügbar sind:

* Stufe 1 ist die häufigste, erfordert weniger Informationen und daher im Allgemeinen höhere Interbankenentgelte im Vergleich zu Transaktionen, die mit Level 2- oder Level 3-Daten verarbeitet werden, die normalerweise mit Unternehmens- und Kaufkreditkarten zusammenhängen.

* Bei Stufe 2 und Stufe 3 können [!DNL Payment Services] Kunden, die Interchange plus (IC++) Preise nutzen, die eine große Menge von Warenkorb- oder Unternehmenskartengeschäften akzeptieren, möglicherweise eine niedrigere Verarbeitungsrate erhalten, indem sie [!DNL Payment Services] die Möglichkeit bieten, weitere Informationen über eine Transaktion zu senden. Wenn die Transaktion gemäß den Anforderungen an das Kartennetz qualifiziert ist, kann der Händler eine niedrigere Verarbeitungsrate für eine bestimmte Transaktion erhalten.

>[!NOTE]
>
>Die Preise der Stufe 2 und der Stufe 3 gelten nur für Visa- und MasterCard-Transaktionen. American Express bietet nur Preise der Stufe 2 an. Discover bietet weder Preise der Stufe 2 noch der Stufe 3 an. Weitere Informationen finden Sie unter [Zahlungsverarbeitung](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} in der PayPal-Entwicklerdokumentation.

Siehe [Was ist IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} in der PayPal-Entwicklerdokumentation .

Die Verarbeitungsdaten der Stufe 2 und 3 ermöglichen es den Händlern, ihre IC+-Preise zu senken, wenn sie zusätzliche Details zum Kauf bereitstellen, die das Prozessorrisiko reduzieren und nützliche Aspekte bieten:

* Große Kunden zahlen weniger, indem sie diese Verarbeitungsdaten bereitstellen.

* Bei Kunden ist es weniger wahrscheinlich, dass sie in betrügerische Situationen geraten, da die Bestellungen mehr Informationen enthalten.

Kartennetze wie Visa und Mastercard bestimmen jedoch letztendlich, ob eine Transaktion für die Verarbeitung auf Stufe 2 oder Stufe 3 qualifiziert ist:

* Daten der Stufe 2 enthalten zusätzliche Informationen, wie den Steuerbetrag für die Bestellung, den Kundencode oder die Bestellnummer.

* Die Daten der Stufe 3 sind detailliertere Informationen über den Verkauf, was dazu beiträgt, im Vergleich zu Stufe 2 noch niedrigere Interbankenentgelte in Anspruch zu nehmen. Daten der Stufe 3 enthalten Informationen wie eine Beschreibung des gekauften Artikels, die Menge der gekauften Artikel, die Maßeinheit für die bestellten Artikel und andere spezifische Details.

[!DNL Payment Services] sammelt diese Daten und erstellt detaillierte Berichte zu Ihren Zahlungsvorgängen.

## Kartenzahlvorgänge der Stufe 2 und der Stufe 3 in [!DNL Payment Services]

Um für die Verarbeitung auf Stufe 2 oder Stufe 3 qualifiziert zu sein, müssen Händler die vorherigen Informationen übermitteln, obwohl es die Kartennetzwerke sind, die letztendlich bestimmen, für welche Stufe eine Transaktion bei der Verarbeitung qualifiziert ist.

Weitere Informationen finden Sie in der [FAQ zur Zahlungsverarbeitung](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} in der PayPal-Entwicklerdokumentation.

Die Verarbeitung auf Stufe 2 und Stufe 3 ist standardmäßig für [!DNL Payment Services] -Händler auf Store-Ebene deaktiviert.

Die Verarbeitung auf Stufe 2 und Stufe 3 ist verfügbar, wenn Sie bereits IC+-Preise verwenden. Um diese Funktion zu aktivieren, können Sie dies über die Befehlszeilenschnittstelle (CLI](configure-cli.md)) tun.[

>[!IMPORTANT]
>
>Wenden Sie sich bei Fragen an Ihren [!DNL Payment Services] -Kundenbetreuer.
