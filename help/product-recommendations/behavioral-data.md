---
title: Verhaltensdaten
description: Erfahren Sie mehr über Verhaltensdaten und wann Sie mit der Verwendung beginnen können.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Verhaltensdaten

Einige Empfehlungstypen verwenden Verhaltensdaten Ihrer Kunden, um Modelle für maschinelles Lernen zu trainieren und so personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie schnell anfangen möchten, können Sie die folgenden, rein katalogbezogenen Empfehlungstypen verwenden:

- `More like this`
- `Visual similarity`

Wann können Sie also mit der Verwendung von Empfehlungstypen beginnen, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als das Problem _Cold Start_ bezeichnet.

Das Problem _Cold Start_ ist ein Maß dafür, wie viel Zeit ein Modell trainieren muss, bevor es als qualitativ hochwertig betrachtet werden kann. In Produktempfehlungen bedeutet dies, dass darauf gewartet wird, dass Adobe Sensei seine maschinellen Lernmodelle trainiert, bevor Empfehlungseinheiten auf Ihrer Site bereitgestellt werden. Je mehr Daten diese Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Die Erfassung dieser Daten nimmt Zeit in Anspruch und variiert je nach Traffic-Volumen. Da diese Daten nur auf einer Produktionssite erfasst werden können, ist es in Ihrem Interesse, die Datenerfassung dort so früh wie möglich bereitzustellen. Dies können Sie tun, indem Sie [das Modul `magento/production-recommendations` installieren und konfigurieren.](install-configure.md)

Die folgende Tabelle enthält einige allgemeine Anleitungen für die Zeit, die benötigt wird, um genügend Daten für jeden Empfehlungstyp zu sammeln:

| Empfehlungstyp | Schulungszeit | Hinweise |
|---|---|---|
| Popularitätsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Varianten | Hängt vom Ereignisvolumen ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu, werden Käufe |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Die Produktansichten sind relativ umfangreich |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meisten Schulungen | Kaufereignisse sind die seltensten Ereignisse auf der Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Beliebtheitsgrundlinie zu erstellen | Die Trends sind ein Messwert für die aktuelle Beliebtheit eines Produkts im Vergleich zu seiner Beliebtheitsgrundlinie. Der Trendwert eines Produkts wird mithilfe eines Vordergrundsatzes (aktuelle Beliebtheit über 24 Stunden) und eines Hintergrundsatzes (Beliebtheitsgrundlinie über 72 Stunden) berechnet. Wenn ein Artikel in den letzten 24 Stunden im Vergleich zur Grundbeliebtheit viel beliebter geworden ist, erhält es einen hohen Trendwert. Jedes Produkt hat diese Punktzahl, und die höchsten zu jeder Zeit bilden den Satz von Top-Trend-Produkten. |

Andere Variablen, die sich auf die zum Trainieren benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- Adobe Commerce berechnet Verhaltensdaten alle vier Stunden neu. Je länger sie auf Ihrer Site verwendet werden, desto genauer wird Recommendations.

Um Ihnen bei der Visualisierung des Trainings-Fortschritts der einzelnen Empfehlungstypen zu helfen, zeigt die Seite [Empfehlung erstellen](create.md) Bereitschaftsindikatoren an.

Während Daten auf Produktions- und maschinellen Lernmodellen erfasst werden, können Sie die [verbleibenden Aufgaben](implementation-workflow.md) implementieren, die erforderlich sind, um Empfehlungen für Ihre Storefront bereitzustellen. Wenn Sie die Tests und Konfiguration von Empfehlungen abgeschlossen haben, haben die Modelle für maschinelles Lernen genügend Daten gesammelt und berechnet, um relevante Empfehlungen zu erstellen, sodass Sie die Empfehlungen in Ihrer Storefront bereitstellen können.

Wenn der Traffic für die meisten SKUs unzureichend ist (Ansichten, gekaufte Produkte, Trends), liegen möglicherweise nicht genügend Daten vor, um den Lernprozess abzuschließen. Dies kann dazu führen, dass der Bereitschaftsindikator im Admin so aussieht, als wäre er blockiert.
Die Bereitschaftsindikatoren sollen Händlern einen weiteren Datenpunkt bei der Auswahl des Empfehlungstyps bieten, der für ihren Store besser ist. Die Zahlen sind ein Leitfaden und werden möglicherweise nie 100 % erreichen.

## Reserveempfehlungen {#backuprecs}

Wenn nicht genügend Eingabedaten vorhanden sind, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet Adobe Commerce Ersatzempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise den Empfehlungstyp &quot;`Recommended for you`&quot;auf Ihrer Homepage bereitstellen, hat ein Erstkäufer Ihrer Site nicht genügend Verhaltensdaten generiert, um genau empfohlene personalisierte Produkte zu erzielen. In diesem Fall überdeckt Adobe Commerce Artikel basierend auf dem Empfehlungstyp `Most viewed` für diesen Käufer.

Die folgenden Empfehlungstypen greifen auf den Empfehlungstyp `Most viewed` zurück, wenn nicht genügend Eingabedaten erfasst wurden:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
