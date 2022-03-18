---
title: Arten von Facetten
description: Live-Suchfacetten sind dynamisch und erscheinen bei Bedarf in der Filterliste.
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Facettentypen

Alle [!DNL Live Search] -Facetten sind dynamisch und werden im *Filter* nur wenn relevant. Die Liste der verfügbaren Facetten ändert sich je nach zurückgegebenen Produkten. Die folgenden Merkmale beeinflussen ihre Darstellung und ihr Verhalten:

* Angeheftete Facetten - Die am häufigsten verwendeten Facetten können an den Anfang der Liste eingefügt werden. Die verbleibenden Facetten sind in *Sortiertyp* nach den fixierten Facetten.
* Intelligente Facetten - Produktattribute, die [Adobe Sensei](https://www.adobe.com/sensei.html) findet am relevantesten für einen Produktsatz und eine Abfrage. Die Berechnung berücksichtigt die Attributmetadaten des gesamten Katalogs und bestimmt zum Zeitpunkt der Abfrage die relevantesten Facetten für die Abfrage.
* Beliebte Facetten: Produktattribute, die am häufigsten in Suchergebnissen vorhanden sind.
* Preisfacetten - Rückgabe von Produkten nach Preisbereich. Sie können die Anzahl der Auswahlen und das Preisbereichsintervall im [*Einstellungen*](settings.md) Registerkarte.

Zum Zeitpunkt der Abfrage [!DNL Live Search] generiert die Suchergebnisse in Gruppen intelligenter und beliebter Facetten.

![Facets - Price](assets/storefront-search-results-run-price.png)

## Storefront- und Headless-Optionen

Facets, die für die [!DNL Commerce] Storefront wird vom Suchadapter verarbeitet, der die Anforderungen weiterleitet und die Ergebnisse in der Storefront rendert. Alle [!DNL Commerce] Storefront-Facetten werden alphabetisch mit Einzelauswahl-Optionen sortiert, unabhängig vom Eingabetyp, der dem entsprechenden Attribut zugewiesen ist. Facets, die in der Storefront verfügbar sind, werden entsprechend dem aktuellen Design gerendert und spiegeln alle Anpassungen wider, die an der Präsentation der Navigation mit Ebenen vorgenommen wurden.

Im Gegensatz dazu [Headless](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/webapi-vision.html) -Implementierungen werden von der API verarbeitet und unterstützen zusätzliche Optionen. Headless-Facetten können alphabetisch oder nach Anzahl sortiert werden und können über Einzel- oder Mehrfachauswahloptionen verfügen.

### Typ auswählen

Bei Headless-Implementierungen können Facetten als `single select` oder `multi-select` mit logischen Operatoren, die den zurückgegebenen Produktsatz bestimmen. Beispiel: `green AND blue` oder `green OR blue`.

![Facetten - Typ auswählen](assets/facets-select-type.png)

| Typ auswählen | Beschreibung |
|--- |--- |
| Einzelauswahl | Eine Einzelauswahl-Facette bietet mehrere Optionen, ermöglicht es dem Käufer jedoch, nur einen Wert auszuwählen. |
| Mehrfachauswahl (oder) | (Nur Headless) Käufer können mehrere Optionen auswählen und zurückgegebene Produkte können mit jedem ausgewählten Wert übereinstimmen. Beispiel: `green OR blue` |
| Mehrfachauswahl (und) | (Nur Headless) Käufer können mehr als eine Option auswählen. Die zurückgegebenen Produkte müssen mit allen ausgewählten Werten übereinstimmen. Beispiel: `green AND blue` |

### Facettenbeschriftungen

Für [!DNL Commerce] Storefronts, wird die Facettenbeschriftung durch die [*Attributeigenschaften*](https://docs.magento.com/user-guide/stores/attribute-product-create.html). Bei Geschäften mit mehreren Ansichten können unter zusätzliche Beschriftungen definiert werden. *Verwalten von Bezeichnungen*. Bei Headless-Implementierungen werden Beschriftungen über die [facettierte Arbeitsfläche](faceting-workspace.md).

### Sortiertyp

Alle für die Storefront gerenderten Facetten werden alphabetisch sortiert. Bei Headless-Implementierungen können Facetten alphabetisch oder nach Anzahl sortiert werden.

| Sortiertyp | Beschreibung |
|--- |--- |
| Alphabetisch | In der Storefront *Filter* -Liste, werden Facetten alphabetisch sortiert. |
| Count | (Nur Headless) Bei Headless-Implementierungen können Facetten auch nach der Anzahl der Werte sortiert werden, die pro Facette im aktuellen Satz der zurückgegebenen Produkte gefunden werden. |
