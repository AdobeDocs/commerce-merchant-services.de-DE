---
title: '[!DNL Live Search] Best Practices'
description: Erfahren Sie mehr über die Best Practices zur Implementierung von [!DNL Live Search] in Ihrem Store.
role: Admin, Developer
exl-id: 69b2c2a6-c8a9-4640-8d2b-08fcd7a96034
source-git-commit: ba2b798f2e7d5716be0d1686359ac8382f6cf8e4
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 0%

---

# Best Practices

Dieser Artikel hilft Merchandisern, ihre Site-Suchfunktion zu verbessern und ein nahtloses und effizientes Kundenerlebnis zu gewährleisten, das Konversionsraten maximiert. Indem Sie die beschriebenen Strategien befolgen, erfahren Sie, wie Sie erweiterte Suchfunktionen implementieren und Ihr Suchtool kontinuierlich für eine optimale Leistung mit Adobe Commerce [!DNL Live Search] optimieren können.

Es gibt mehrere Schlüsselfaktoren, die die Relevanz und Effektivität von Suchergebnissen bestimmen:

- Gut strukturierte Produktdaten stellen sicher, dass Suchalgorithmen Produkte effektiv mit Abfragen verknüpfen können. Produktdaten mit geringer Qualität führen zu niedrigen relevanten Suchergebnissen. So beeinflussen Sie direkt den Erfolg Ihrer Merchandising-Strategie:
   - Richten Sie die richtigen Attribute mit der entsprechenden Gewichtung als durchsuchbar ein.
   - Stellen Sie sicher, dass die Daten in diesen Attributen relevant sind.
- Eine gut durchdachte Sucherfahrung schafft Vertrauen zu Kunden und gibt ihnen die Gewissheit, dass sie das finden, was sie benötigen.
- Suchregeln sind von entscheidender Bedeutung, da sie die Sichtbarkeit bestimmter Produkte basierend auf Beliebtheit, Neuankündigungen, Werbekriterien oder einer anderen Merchandising-Strategie erhöhen können, um Ihre Geschäftsanforderungen zu erfüllen.
- Die facettierte Navigation ermöglicht es Käufern, ihre Suche zu verfeinern und schnell relevante Ergebnisse zu erhalten.

Um [!DNL Live Search] zu verwalten, gehen Sie zu **Marketing** > *SEO &amp; Suche* > **[!DNL Live Search]** in der Adobe [!DNL Commerce] Admin. 

## Optimieren der Suchfunktion

In diesem Abschnitt erfahren Sie, wie Sie Ihre Suchfunktion optimieren können, indem Sie Funktionen wie autocomplete verwenden, um Echtzeitvorschläge wie den Käufertyp, Synonyme und Rechtschreibungen bereitzustellen und sicherzustellen, dass Käufer Produkte finden, selbst wenn sie unterschiedliche Wörter verwenden, Facetten, mit denen Käufer Suchergebnisse eingrenzen können, und Suchumleitungen nutzen, um Käufer von einer Suchabfrage automatisch zu einer bestimmten Seite umzuleiten.

### Automatische Vervollständigung

Autocomplete, auch &quot;type-ahead&quot;oder &quot;AutoRecommendations&quot;genannt, ist eine interaktive Suchfunktion, mit der Käufern beim Eingeben ihrer Suchbegriffe dynamisch Vorschläge angezeigt werden. Dies hilft Käufern, Produkte schnell und einfach zu finden, indem sie Echtzeitvorschläge basierend auf ihren Inhalten anbieten.

Das Widget [!DNL Live Search] [[!DNL popover]](storefront-popover.md) ermöglicht die automatische Vervollständigung von Suchoptionen, um beliebte Produkte vorzuschlagen. Mit jedem vom Käufer eingegebenen Zeichen aktualisiert das Popover die vorgeschlagenen Produkte und Miniaturansichten der Top-Suchergebnisse.

[!DNL Live Search] gibt Ergebnisse zurück, wenn der Benutzer zwei Zeichen eingegeben hat. Bei einer teilweisen Übereinstimmung beträgt die maximale Anzahl von Zeichen pro Wort 20. Die Anzahl der Zeichen in einer Abfrage vom Typ &quot;Suche beim Eingeben&quot; ist nicht konfigurierbar.

Erfahren Sie mehr über das Widget [popover](storefront-popover.md) .

### Synonyme und Rechtschreibfehler

Die Live-Suche verwaltet Rechtschreibfehler standardmäßig. Sie können Synonyme einrichten, um Wörter einzuschließen, die von den in Ihrem Katalog angegebenen Wörtern abweichen. Sie wollen keinen Verkauf verlieren, weil jemand nach einem &quot;Sofa&quot; sucht, während Ihr Produkt als &quot;Sofa&quot; aufgeführt ist. Sie können eine breite Palette von Suchbegriffen erfassen, indem Sie alle möglichen Wörter eingeben, die Kunden bei der Suche nach Ihren Produkten verwenden können. Sie können [Synonyme auf eine oder zwei Arten setzen](synonyms-add.md#step-2-define-the-synonym-by-type), um die Ergebnisse zu verbessern.

#### Tipps zur Optimierung von Synonymen

- Ordnen Sie den vollständigen Namen von Marken und Abkürzungen zu, z. B. &quot;HP&quot;zu &quot;Hewlett-Packard&quot;und allgemeinen Produktnamen, z. B. &quot;iPhone&quot;zu &quot;Apple iPhone&quot;.
- Schließen Sie branchenspezifische Fachbegriffe und Begriffe ein, die Käufer austauschbar verwenden könnten, z. B. &quot;Turnschuhe&quot;und &quot;Laufschuhe&quot;.
- Aktualisieren Sie regelmäßig die Synonym-Liste basierend auf neuen Suchtrends, Produktadditionen und dem Kaufverhalten.
- Testen Sie die Effektivität von Synonym-Mappings, indem Sie Suchergebnisse und Feedback von Käufern analysieren. Präzisieren Sie Zuordnungen, um Genauigkeit und Relevanz zu verbessern.

Weitere Informationen zu Synonymen:

- [Arten von Synonymen](synonyms-type.md)
- [Synonyme erstellen](synonyms-add.md)
- [Synonyme verwalten](synonyms-manage.md)
- [Sprachunterstützung](settings.md#language)

### Facets

Die Filter- und Facettenfunktionalität ist eine wichtige Komponente Ihrer [!DNL Commerce]-Site. Sie soll das Kundenerlebnis verbessern, indem sie es Käufern ermöglicht, Suchergebnisse einzugrenzen und Produkte effizienter zu finden. Diese Funktion hilft Käufern, durch große Kataloge von Artikeln zu sortieren, indem sie bestimmte Kriterien anwendet, wodurch der Einkaufsprozess schneller, einfacher und befriedigender wird. Durch die Implementierung effektiver und benutzerfreundlicher Filter und Facetten können Sie Kunden dabei helfen, schnell und effizient das zu finden, was sie benötigen, und dadurch die Zufriedenheit und Konversionsraten steigern.

Um ein Produktattribut als Facette einzurichten, muss es die folgenden [Eigenschaften festlegen](facets-add.md#step-1-add-a-facet):

- **[!UICONTROL Use in Search]** -  `Yes`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### Tipps zur Optimierung von Facetten

- Bestimmen Sie die relevantesten und nützlichsten Attribute für Ihre Produkte, wie Titel, Kategorie, Marke, Preisbereich, Farbe und Größe und legen Sie sie als [dynamische Facetten](facets-type.md) fest. 
- Legen Sie Produktattribute fest und sortieren Sie sie, die in Ihrem Katalog konsistent und für Ihre Produkte äußerst relevant sind, um die Relevanz und Filterfunktionen für Ihre Kunden zu verbessern.
- Stellen Sie sicher, dass die Facettenbeschriftungen auf der gesamten Site leicht verständlich und konsistent benannt sind. Verwenden Sie beispielsweise &quot;Preisbereich&quot;anstelle von &quot;Kosten&quot;.
- Vermeiden Sie überwältigende Käufer, indem Sie die Anzahl der Facetten auf die wichtigsten begrenzen. Zu viele Optionen können Entscheidungsmüdigkeit verursachen. Standardmäßig ist [!DNL Live Search] auf maximal 100 Attribute beschränkt, die als Facetten konfiguriert sind, und 30 Behälter, die in jeder Facette zurückgegeben werden. Erfahren Sie mehr über [Facettenbeschränkungen](boundaries-limits.md#facets). 
- Käufer können mehrere Filterkriterien gleichzeitig auswählen, um die Ergebnisse zu verfeinern. Beispielsweise können Käufer die Farben &quot;Rot&quot;und &quot;Blau&quot;auswählen.
- Zeigen Sie die Anzahl der verfügbaren Produkte neben jeder Facettenoption an, um den Käufern eine Vorstellung von den erwarteten Suchergebnissen zu geben.
- Implementieren Sie ausblendbare Facettenabschnitte, um die Benutzeroberfläche sauber und insbesondere auf Mobilgeräten verwaltbar zu halten.
- Mit dieser Option können Käufer einzelne Facetten oder alle ausgewählten Filter einfach zurücksetzen, um eine neue Suche zu starten.

Weitere Informationen zu Facetten:

- [Facettentypen](facets-type.md)
- [Hinzufügen von Facetten](facets-add.md)
- [Facetten verwalten](facets-manage.md) (Bearbeiten, Facetten veröffentlichen, löschen, veröffentlichen)
- [Preisfacetten](settings.md#price-faceting)

### Suchumleitungen

Mit einer Suchumleitung können Sie Käufer automatisch von einer Suchabfrage zu einer bestimmten Seite umleiten. Suchumleitungen können das Kundenerlebnis verbessern und Kunden zu den relevantesten Inhalten führen, wie Produktseite, Kategorie, Landingpage oder einem angepassten Satz von Suchergebnissen. Suchumleitungen helfen dabei, das Einkaufserlebnis zu optimieren und sicherzustellen, dass Käufer schnell und effizient finden, wonach sie suchen.

Empfohlene Anwendungsfälle zum Einrichten von Suchumleitungen:

- **Beliebte Produkte oder Kategorien** - Leitet Käufer bei der Suche nach allgemeinen oder beliebten Begriffen zu einer bestimmten Produktseite oder Kategorie um. Die Suche nach &quot;iPhone&quot;könnte beispielsweise direkt zur iPhone-Kategorieseite oder zu einer bestimmten Modellseite weiterleiten.

- **Werbekampagnen** - Während Werbeveranstaltungen oder Verkaufen leiten Sie relevante Suchbegriffe auf Landingpages um, auf denen Sonderangebote oder vorgestellte Produkte hervorgehoben werden.

- **Marken-Suchvorgänge** - Wenn Käufer nach einem Markennamen suchen, leiten sie diese auf die dedizierte Seite der Marke weiter, auf der alle Produkte dieser Marke aufgelistet sind.

- **Produktabbruch** - Wenn ein Produkt eingestellt wird, können Sie die Suche nach diesem Produkt an ähnliche Produkte oder die neue Version des Produkts weiterleiten.

Testen Sie immer Suchumleitungen, um sicherzustellen, dass sie ordnungsgemäß funktionieren und zu den relevantesten Seiten führen. Überwachen Sie kontinuierlich ihre Leistung und nehmen Sie bei Bedarf Anpassungen vor.

Erfahren Sie, wie Sie [Suchumleitungen verwalten](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms).

## Relevanz der Suchergebnisse verbessern

In diesem Abschnitt wird erläutert, wie Sie die Relevanz der Suchergebnisse verbessern können, indem Sie effektive Suchregeln implementieren und Produktmetadaten verwenden, um sicherzustellen, dass genaue und detaillierte Attribute durchsuchbar sind.

### Bilder

Stellen Sie sicher, dass die untergeordneten Produkte konfigurierbarer Produkte über Bilder mit den richtigen Rollen verfügen. Das Vorhandensein von übergeordneten oder untergeordneten Produkten kann dazu führen, dass das Suchergebnis keine Bilder enthält.

>[!NOTE]
>
>Bilder in Suchergebnissen können je nach Suchbegriff unterschiedlich sein. Wenn der Suchbegriff feststellt, dass ein untergeordnetes Produkt relevanter ist, werden Bilder vom untergeordneten Produkt anstelle von Bildern vom übergeordneten Produkt verwendet.

### Suchregeln

Um Ihre Konversionsrate und Ihren Umsatz zu optimieren, müssen Sie effektive Suchregeln implementieren. Passen Sie Produktbewertungen anhand von Verkaufsdaten, Lagerbeständen und Promotions mit [Merchandising durchsuchen](rules.md) an.

Es ist von entscheidender Bedeutung, eine gut durchdachte Standardsuchregel zu erstellen. Ihre [Standardregel](rules.md#default-rule) bestimmt, wie Suchergebnisse anfänglich sortiert und den Käufern angezeigt werden, wodurch ihr Gesamterlebnis verbessert und die Kaufwahrscheinlichkeit erhöht wird. Die regelmäßige Überwachung und Anpassung dieser Regel stellt sicher, dass die Anforderungen der Käufer und die Geschäftsziele weiterhin wirksam erfüllt werden.

#### Tipps zur Optimierung von Suchregeln

- Pin oder Booten Sie Produkte mit hohen Verkaufsmengen oder aktuellen Verkaufsaktivitäten.
- Priorisieren Sie Produkte mit hohen Bewertungen und positiven Bewertungen.
- Stellen Sie sicher, dass Lagerpositionen höher eingestuft werden.
- Sorgfältige Priorisierung von Produkten mit höheren Gewinnspannen ohne Beeinträchtigung der Relevanz.
- Markieren Sie Produkte, die zum Verkauf stehen oder Teil von Sonderaktionen sind.
- Legen Sie Suchregeln während der Promotion- oder Verkaufszeiträume automatisch fest, indem Sie den Datumsbereich während Ihres Promotion-Zeitraums verwenden.
- Sie können Suchergebnisse auf Grundlage des individuellen Kaufverhaltens mit dem [intelligenten Ranking](rules-add.md#intelligent-ranking) anpassen, z. B. &quot;empfohlen für Sie&quot;, &quot;am häufigsten angezeigt&quot;usw. Um das Kaufverhalten anzupassen, müssen Sie sicherstellen, dass Eventing korrekt implementiert ist. Für Luma-Händler ist das Eventing standardmäßig verfügbar. Bei Headless- oder benutzerdefinierten Implementierungen müssen Sie [eventing](events.md) entsprechend Ihren spezifischen Anforderungen implementieren.

Weitere Informationen zu Suchregeln:

- [Merchandising-Arbeitsbereich](rules-workspace.md#set-the-scope)
- [Voraussetzungen](rules.md#requirements)
- [Standardsuchregel](rules.md#default-rule)
- Suchregeln verwalten
   - [Erstellen](rules-add.md)
   - [Bearbeiten, Anzeigen und Löschen](rules-manage.md)
- Datenerfassung
   - [[!DNL Live Search] Ereignisse](events.md)
   - [Adobe Commerce-Ereignisabruf](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/)
   - [GitHub-Commerce-Ereignisse](https://github.com/adobe/commerce-events/tree/main/examples) 

### Nutzung von Produktmetadaten

Stellen Sie sicher, dass genaue und detaillierte Produktattribute [als durchsuchbar ](workspace.md#set-attributes-as-searchable) eingerichtet sind. Beachten Sie, dass SKU-, Name- und Kategorieattribute standardmäßig durchsuchbar sind und nicht von der Suche ausgeschlossen werden können. Verwenden Sie für optimale Ergebnisse keine Leerzeichen in Ihren SKUs.

Um die Suchrelevanz zu erhöhen, weisen Sie jedem durchsuchbaren Attribut eine Gewichtung zu. Attribute mit einer höheren Gewichtung sollten in den Suchergebnissen höher angezeigt werden. Die Sortierung nach Relevanz wird durch mehrere Kriterien beeinflusst, z. B. die Suchgewichtung. Das bedeutet, dass Attribute mit geringerer Suchgewichtung manchmal immer noch eine größere Relevanz haben können als Attribute mit höherer Suchgewichtung. Andere Kriterien können die Anzahl der Übereinstimmungen in einem beliebigen Attribut, die Position des gefundenen Suchbegriffs und die gesamte Textstruktur vor und nach einem Suchbegriff sein.

Stellen Sie sicher, dass jedes Produkt über relevante Inhalte in jedem durchsuchbaren Attribut verfügt. Es wird nicht empfohlen, ein Attribut als durchsuchbar festzulegen, wenn es große Mengen an Inhalt enthält, da dies die Relevanz der Suchergebnisse verringern kann.

Weitere Informationen zu Produktattributen für die Suche:

- [Festlegen von Attributen als durchsuchbar](workspace.md#set-attributes-as-searchable)
- [Gewichtung Attributen zuweisen](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search)

## Überwachen von Suchergebnissen

Um Suchergebnisse mit [!DNL Live Search] zu optimieren, überwachen Sie relevante KPIs (Key Performance Indicators) wie eindeutige Abfragen, durchschnittliche Klickposition, Clickthrough-Raten, Konversionsrate und Nullergebnisrate, um zu verstehen, wie Kunden mit Ihrer Suchfunktion interagieren. Diese Daten helfen Ihnen, Ihre Suchregeln regelmäßig zu aktualisieren und zu verfeinern.

Sie können diese KPIs im Arbeitsbereich [!DNL Live Search] [Leistung](performance.md) überwachen, wo Sie die folgenden Metriken finden: 

- **Eindeutige Suchvorgänge** - Die Anzahl der einzelnen Suchabfragen, die auf Ihrer [!DNL Commerce] -Site durchgeführt werden. Jede individuelle Suche wird nur einmal gezählt, auch wenn sie von demselben oder mehreren Käufern mehrmals wiederholt wird. Diese Metrik hilft Ihnen, die Vielfalt der von Kunden verwendeten Suchbegriffe zu verstehen, und bietet Einblicke in die Suche nach Produkten oder Informationen, die von Käufern verwendet werden. Das Tracking eindeutiger Suchvorgänge ermöglicht Ihnen Folgendes:

   - Identifizieren Sie beliebte Suchtrends und häufig gesuchte Elemente.
   - Erkennen möglicher Lücken in Ihrem Produktkatalog oder Ihren Inhalten.
   - Optimieren Sie die Suchfunktion, indem Sie [Synonyme](synonyms.md) hinzufügen, Suchregeln erstellen oder aktualisieren.

- **Durchschnittliche Klickposition** - Gibt an, dass die durchschnittliche Position der Suchergebnisse, die von Käufern nach einer Suchabfrage auf Ihrer Site angeklickt wurden. Diese Metrik bietet Einblicke in die Relevanz und Effektivität Ihrer Suchergebnisse.

  Eine niedrigere durchschnittliche Klickposition (näher an 1) deutet darauf hin, dass Käufer relevante Ergebnisse schnell finden, was darauf hinweist, dass Ihre Suchstrategie effektiv ist. Dies hilft Ihnen, das Verhalten von Käufern zu verstehen und zu verstehen, wie weit sie bereit sind, einen Bildlauf durchzuführen, um das gewünschte Produkt zu finden. Wenn die durchschnittliche Klickposition hoch ist, kann dies darauf hinweisen, dass die relevantesten Ergebnisse nicht oben angezeigt werden. Dies erfordert eine Überprüfung und Optimierung Ihrer Suchstrategie.

- **Clickthrough-Rate (CTR)** - Misst den Prozentsatz der Käufer, die nach Durchführung einer Suchabfrage auf ein Suchergebnis klicken. Eine hohe CTR zeigt an, dass die Suchergebnisse relevant sind und für Käufer attraktiv sind, da sie auf die Ergebnisse klicken, die sie finden. Die Überwachung der CTR kann dabei helfen, Verbesserungsbereiche zu identifizieren. Eine niedrige CTR kann darauf hindeuten, dass die Suchergebnisse nicht mit der Absicht der Käufer übereinstimmen. Daher müssen die Suchregeln verfeinert, die Produktdaten verbessert oder die Ergebnisdarstellung verbessert werden.

- **Konversionsrate** - Gibt die Effektivität Ihrer Suchfunktion bei der Förderung von Umsatz und der Erreichung von Geschäftszielen an. Es spiegelt die allgemeine Effektivität Ihrer Suchfunktion bei der Erfüllung von Kundenanforderungen und der Erleichterung eines reibungslosen Einkaufserlebnisses wider. Eine hohe Konversionsrate zeigt an, dass Ihre Suchergebnisse hochgradig relevant und überzeugend sind, was dazu führt, dass Käufer Einkäufe abschließen. Wenn die Konversionsrate niedrig ist, kann dies auf Probleme mit Suchrelevanz, Produktverfügbarkeit oder dem gesamten Journey von der Suche zum Kauf hinweisen.

- **Null Ergebnisse** - Misst den Prozentsatz der Suchabfragen auf Ihrer [!DNL Commerce]-Site, die keine Ergebnisse zurückgeben. Diese Metrik ist von entscheidender Bedeutung, um zu verstehen, wie oft die Suchvorgänge von Käufern nicht erfolgreich sind, und kann Einblicke in potenzielle Lücken in Ihrem Produktkatalog oder Suchsetup bieten. Eine hohe Null-Ergebnisrate kann Kunden frustrieren, was zu einem schlechten Einkaufserlebnis und einem potenziellen Verlust von Kunden führt. Es kann auf fehlende Produkte oder Kategorien in Ihrem Katalog hinweisen, nach denen Käufer suchen, und Entscheidungen zu Inventar und Produktliste leiten.

  Um die Nullergebnisrate zu reduzieren, können Sie:

   - Bieten Sie alternative oder verwandte Suchbegriffe an, z. B. [Synonyme](synonyms.md), wenn keine exakten Übereinstimmungen gefunden werden.
   - Stellen Sie den Käufern mit verwandten oder alternativen Vorschlägen zur Verfügung, wenn ihre Suche keine Ergebnisse liefert, indem Sie Suchumleitungen festlegen.
   - Prüfen Sie regelmäßig Nullergebnisabfragen, um Muster zu identifizieren und erforderliche Anpassungen an Ihrem Produktkatalog und Ihren Sucheinstellungen vorzunehmen.

- **Beliebte Ergebnisse** - Können Ihre Suchergebnisse erheblich verbessern, indem sie an den Vorlieben und Verhalten der Käufer ausgerichtet werden.

Sie können diese Metrikdaten wie folgt verwenden, um Ihre Suchfunktion zu optimieren:

- Implementieren Sie Regeln, um beliebte Produkte in den Suchergebnissen automatisch höher zu stufen. Produkte, auf die häufig geklickt oder gekauft wurde, können vorrangig angezeigt werden. Kuratieren Sie Listen beliebter Produkte für spezifische Suchabfragen manuell und stellen Sie sicher, dass diese Elemente hervorgehoben angezeigt werden.
- Markieren Sie Produkte, die derzeit eine Trendansicht aufweisen oder in letzter Zeit einen Anstieg der Beliebtheit zu verzeichnen haben. Dies kann besonders bei saisonalen Veranstaltungen, Feiertagen oder Werbezeiten wirksam sein. Verwenden Sie dazu das intelligente Ranking, das bei der Einrichtung einer Suchregel besser zu Ihrem Anwendungsfall und geschäftlichen Anforderungen passt.
- Markieren Sie beliebte Filter oder Facetten, wenn Kunden häufig nach bestimmten Marken oder Preisbereichen filtern, machen Sie diese Optionen auffälliger, indem Sie diese Facetten fixieren und entsprechend sortieren.
- Wenn eine Suche keine Ergebnisse liefert, verwenden Sie beliebte Ergebnisdaten, um alternative Produkte oder verwandte Kategorien vorzuschlagen, die eine hohe Kundeninteraktion aufweisen.
- Analysieren Sie beliebte Suchbegriffe und Produktdaten, um wichtige Suchbegriffe zu identifizieren. Optimieren Sie Ihre Produktsuchattribute mit diesen Suchbegriffen, um die Suchrelevanz zu verbessern.
- Analysieren Sie regelmäßig Ihre Ergebnisdaten, um sich ändernde Trends, Kaufpräferenzen und -verhalten zu verstehen, die wichtigsten Suchbegriffe zu identifizieren und Probleme zu erkennen. Verwenden Sie diese Feedback-Schleife, um Ihre Suchregeln und Produktangebote kontinuierlich zu verfeinern und zu verbessern.

Um korrekte Daten in Ihrem [!DNL Live Search] -Bericht zu erhalten, müssen Sie sicherstellen, dass Eventing korrekt implementiert ist. Für Luma-Händler ist das Eventing standardmäßig verfügbar. Bei Headless- oder benutzerdefinierten Implementierungen müssen Sie [eventing](events.md) entsprechend Ihren spezifischen Anforderungen implementieren.
