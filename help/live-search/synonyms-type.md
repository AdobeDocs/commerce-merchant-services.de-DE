---
title: '"Arten von Synonymen"'
description: '"Einweg- und Zweiwege [!DNL Live Search] Synonyme erweitern die Definition von Keywords."'
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cd1b40ffb350a87ea1317be82789f702922881b9
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# Arten von Synonymen

Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Untergruppe des Keywords darstellen.

## Zweiweg

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort der im Katalog verwendete Suchbegriff, gefolgt von Wörtern, die dieselbe Bedeutung wie der ursprüngliche Suchbegriff haben. Sie können ein einfaches Paar aus bidirektionalen Synonymen oder eine Kette aus mehreren bidirektionalen Synonymen für dasselbe Keyword erstellen.

**Jacke** ![Zweiwegauswahl](assets/btn-two-way.png) Mantel
**pants** ![Zweiwegauswahl](assets/btn-two-way.png) Klappen ![Zweiwegauswahl](assets/btn-two-way.png) Hosenträger

## Einweg

Ein unidirektionales Synonym ist eine Teilmenge eines Suchbegriffs, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Kapriolen und Kurzhosen Hosen, aber nicht alle Hosen sind Kapriolen oder Kurzhosen. Bei der Suche nach Hosen sind auch Kapriolen und Kurzkursen enthalten. Bei der Suche nach Shorts werden jedoch keine Capris zurückgegeben.

**Pullover** ![Einwegauswahl](assets/btn-one-way.png) hoodie
**pants** ![Einwegauswahl](assets/btn-one-way.png) Capris ![Mehrere Einweg-Selektoren](assets/btn-multiple-one-way.png) calf-length-pants ![Mehrere Einweg-Selektoren](assets/btn-multiple-one-way.png) Pädagogische Schubboote

## Best Practices

Beachten Sie die folgenden Best Practices, um die Nutzung von Live Search-Synonymen optimal zu nutzen.

### Vermeiden Sie &quot;Stoppwörter&quot;

Die Live-Suche filtert häufig verwendete englische &quot;Stoppwörter&quot;aus Synonymen heraus, z. B.:

a, an und sind, wie es ist, aber durch, ob es, in, in, ist, nein, nicht, auf, oder so, dass die, ihre, dann, dort, diese, dies, zu, mit

Stoppwörter machen Synonyme nicht aussagekräftiger, erhöhen aber die Menge der zu verarbeitenden Daten.

### Verwenden einzelner Wörter

Wenn ein Begriff aus einem Synonym mehrere Wörter enthält, bewirkt der leere Abstand zwischen den Wörtern, dass sie als separate Synonyme behandelt werden. Wenn Sie beispielsweise &quot;Zeitstück&quot;als Synonym für &quot;watch&quot;definieren, werden die Wörter &quot;time&quot;und &quot;element&quot;als separate Synonyme behandelt.

### Verwendung von Singular und Plural

Es ist nicht erforderlich, sowohl die Singular- als auch die Plural eines Wortes als Synonym zu definieren. Wenn Sie eine Mischung aus Einzel- und Plural-Begriffen in Ihrem Katalog haben, findet Search den richtigen Satz von Produkten. Wenn Sie beispielsweise das Wort &quot;Pant&quot;im Produktnamen verwenden und ein Käufer nach &quot;Hosen&quot;sucht, wird der richtige Satz von Produkten zurückgegeben und das Singular &quot;Pant&quot;wird als Vorschlag angeboten. Der Singular-Begriff &quot;Hose&quot;wird oft in der Modebranche und manchmal auch im Einzelhandel verwendet, obwohl die Pluralform &quot;Hosen&quot;in einigen Bereichen häufiger verwendet wird. (Das Wort &quot;Hose&quot;bezieht sich technisch auf den Teil eines Kleidungsstücks, der ein Bein bedeckt, weshalb man ein &quot;Paar Hosen&quot;benötigt, um beide Beine zu bedecken.)

### Konsistenz

Konsistent mit der Verwendung von Terminologie in Ihrem Katalog sein. Beachten Sie, dass es regionale Unterschiede bei der Verwendung und manchmal Unterschiede innerhalb einer Branche geben kann.

### Keyword-Zuordnung

Bei dieser Technik werden anstelle von Synonymen durchsuchbare Produktattribute verwendet, um schlüsselwortbasierte Verknüpfungen zwischen Produkten zu erstellen. Daher kann ein zugeordnetes Produkt in den Suchergebnissen eines anderen Produkts angezeigt werden. Weitere Informationen finden Sie unter [Suchergebnisse](https://docs.magento.com/user-guide/catalog/search-results.html).
