---
title: Arten von Synonymen
description: Ein- und Zwei-Wege- [!DNL Live Search] Synonyme erweitern die Definition von Keywords.
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cb5db979828eb0b678d19c926de2823829717c02
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Arten von Synonymen

Ein- und Zwei-Wege-Synonyme erweitern die Definition von Keywords. Einige sind mit dem Keyword austauschbar, während andere eine Untergruppe des Keywords darstellen.

## Zweiweg

Zwei-Wege-Synonyme haben dieselbe Bedeutung und geben dieselben Suchergebnisse zurück. Im folgenden Beispiel ist das erste fett gedruckte Wort der im Katalog verwendete Suchbegriff, gefolgt von Wörtern, die dieselbe Bedeutung wie der ursprüngliche Suchbegriff haben. Sie können ein einfaches Paar aus bidirektionalen Synonymen oder eine Kette aus mehreren bidirektionalen Synonymen für dasselbe Keyword erstellen.

**Jacke** ![Zweiweg-Selektor](assets/btn-two-way.png) Mantel
**pants** ![Zweiweg-Selektor](assets/btn-two-way.png) schleicht ![Zweiweg-Selektor](assets/btn-two-way.png) Hosen

## Einweg

Ein unidirektionales Synonym ist eine Teilmenge eines Suchbegriffs, jedoch mit einer spezifischeren Bedeutung. Zum Beispiel sind Kapriolen und Kurzhosen Hosen, aber nicht alle Hosen sind Kapriolen oder Kurzhosen. Bei der Suche nach Hosen sind auch Kapriolen und Kurzkursen enthalten. Bei der Suche nach Shorts werden jedoch keine Capris zurückgegeben.

**Sweatshirt** ![Einweg-Selektor](assets/btn-one-way.png) hoodie
**pants** ![Einweg-Selektor](assets/btn-one-way.png) capris ![Mehrere Einweg-Selektoren](assets/btn-multiple-one-way.png) calf-length-pants ![Mehrere Einweg-Selektoren](assets/btn-multiple-one-way.png) Peddle-Dushers

## Best Practices

Beachten Sie die folgenden Best Practices, um das Beste aus [!DNL Live Search] -Synonymen zu erhalten.

### Vermeiden von &quot;Stoppwörtern&quot;

[!DNL Live Search] filtert gängige englische &quot;Stoppwörter&quot;aus Synonymen heraus, z. B.:

a, an und sind, wie es ist, aber durch, ob es, in, in, ist, nein, nicht, auf, oder so, dass die, ihre, dann, dort, diese, dies, zu, mit

Stoppwörter machen Synonyme nicht aussagekräftiger, erhöhen aber die Menge der zu verarbeitenden Daten.

### Verwenden einzelner Wörter

Wenn ein Begriff aus einem Synonym mehrere Wörter enthält, bewirkt der leere Abstand zwischen den Wörtern, dass sie als separate Synonyme behandelt werden. Wenn Sie beispielsweise &quot;Zeitstück&quot;als Synonym für &quot;watch&quot;definieren, werden die Wörter &quot;time&quot;und &quot;element&quot;als separate Synonyme behandelt.

### Verwendung von Singular und Plural

Es ist nicht erforderlich, sowohl die Singular- als auch die Plural eines Wortes als Synonym zu definieren. Wenn Sie eine Mischung aus Einzel- und Plural-Begriffen in Ihrem Katalog haben, findet Search den richtigen Satz von Produkten. Wenn Sie beispielsweise das Wort &quot;Pant&quot;im Produktnamen verwenden und ein Käufer nach &quot;Hosen&quot;sucht, wird der richtige Satz von Produkten zurückgegeben und das Singular &quot;Pant&quot;wird als Vorschlag angeboten. Der Singular-Begriff &quot;Hose&quot;wird oft in der Modebranche und manchmal auch im Einzelhandel verwendet, obwohl die Pluralform &quot;Hosen&quot;in einigen Bereichen häufiger verwendet wird. (Das Wort &quot;Hose&quot;bezieht sich technisch auf den Teil eines Kleidungsstücks, der ein Bein bedeckt, weshalb man ein &quot;Paar Hosen&quot;benötigt, um beide Beine zu bedecken.)

### Konsistenz

Konsistent mit der Verwendung von Terminologie in Ihrem Katalog sein. Beachten Sie, dass es regionale Unterschiede bei der Verwendung und manchmal Unterschiede innerhalb einer Branche geben kann.
