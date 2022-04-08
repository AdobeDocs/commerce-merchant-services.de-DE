---
title: Verhaltensdaten
description: Erfahren Sie mehr über Verhaltensdaten und wann Sie mit der Verwendung beginnen können.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Verhaltensdaten

Einige Empfehlungstypen verwenden Verhaltensdaten Ihrer Kunden, um Modelle für maschinelles Lernen zu trainieren und so personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie schnell anfangen möchten, können Sie die folgenden, rein katalogbezogenen Empfehlungstypen verwenden:

- `More like this`
- `Visual similarity`

Wann können Sie also mit der Verwendung von Empfehlungstypen beginnen, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als _Kaltstart_ Problem.

Die _Kaltstart_ -Problem ist ein Maß dafür, wie viel Zeit ein Modell trainieren muss, bevor es als qualitativ hochwertig betrachtet werden kann. In Produktempfehlungen bedeutet dies, dass darauf gewartet wird, dass Adobe Sensei seine maschinellen Lernmodelle trainiert, bevor Empfehlungseinheiten auf Ihrer Site bereitgestellt werden. Je mehr Daten diese Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Die Erfassung dieser Daten nimmt Zeit in Anspruch und variiert je nach Traffic-Volumen. Da diese Daten nur auf einer Produktionssite erfasst werden können, ist es in Ihrem Interesse, die Datenerfassung dort so früh wie möglich bereitzustellen. Sie können dies tun, indem Sie [Installation und Konfiguration](install-configure.md) die `magento/production-recommendations` -Modul.

Die folgende Tabelle enthält einige allgemeine Anleitungen für die Zeit, die benötigt wird, um genügend Daten für jeden Empfehlungstyp zu sammeln:

| Empfehlungstyp | Schulungszeit | Hinweise |
|---|---|---|
| Popularitätsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Varianten | Hängt vom Ereignisvolumen ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu, dann Käufe |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Die Produktansichten sind relativ umfangreich |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meisten Schulungen | Kaufereignisse sind die seltensten Ereignisse auf der Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Beliebtheitsgrundlinie zu erstellen | Die Trends sind ein Messwert für die aktuelle Beliebtheit eines Produkts im Vergleich zu seiner Beliebtheitsgrundlinie. Der Trendwert eines Produkts wird mithilfe eines Vordergrundsatzes (aktuelle Beliebtheit über 24 Stunden) und eines Hintergrundsatzes (Beliebtheitsgrundlinie über 72 Stunden) berechnet. Wenn ein Artikel in den letzten 24 Stunden im Vergleich zur Grundbeliebtheit viel beliebter geworden ist, erhält es einen hohen Trendwert. Jedes Produkt hat diese Punktzahl, und die höchsten zu jeder Zeit bilden den Satz von Top-Trend-Produkten. |

Andere Variablen, die sich auf die zum Trainieren benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- Adobe Commerce berechnet Verhaltensdaten alle vier Stunden neu. Sie können Ihre Empfehlungseinheiten zwar technisch zu diesem Zeitpunkt bereitstellen, wissen jedoch, dass die Empfehlungen genauer werden, je länger sie auf Ihrer Site verwendet werden.

Während Daten auf Produktions- und maschinellen Lernmodellen erfasst werden, können Sie die [verbleibende Aufgaben](implementation-workflow.md) erforderlich, um Empfehlungen für Ihre Storefront bereitzustellen. Wenn Sie die Tests und Konfiguration von Empfehlungen abgeschlossen haben, haben die Modelle für maschinelles Lernen genügend Daten gesammelt und berechnet, um relevante Empfehlungen zu erstellen, sodass Sie die Empfehlungen in Ihrer Storefront bereitstellen können.

## Reserveempfehlungen

Wenn nicht genügend Eingabedaten vorhanden sind, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet Adobe Commerce Ersatzempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise die `Recommended for you` Empfehlungstyp auf Ihrer Homepage verwenden, hat ein Erstkäufer Ihrer Site nicht genügend Verhaltensdaten generiert, um genau empfohlene personalisierte Produkte zu erzielen. In diesem Fall überdeckt Adobe Commerce Elemente basierend auf dem `Most viewed` Empfehlungstyp an diesen Kunden.

Die folgenden Empfehlungstypen fallen auf `Most viewed` Empfehlungstyp, wenn nicht genügend Eingabedaten erfasst wurden:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
