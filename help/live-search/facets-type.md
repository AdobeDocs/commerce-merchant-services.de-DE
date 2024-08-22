---
title: "Facettentypen"
description: "[!DNL Live Search] Facetten sind dynamisch und werden ggf. in der Filterliste angezeigt."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Arten von Facetten

[!DNL Live Search] verwendet eine Vielzahl von Facettentypen und sie werden nur dann in der Liste *Filter* angezeigt, wenn relevant. Die Liste der verfügbaren Facetten ändert sich je nach zurückgegebenen Produkten. Die folgenden Merkmale beeinflussen ihre Darstellung und ihr Verhalten:

* Angeheftete Facetten - Die am häufigsten verwendeten Facetten können an den Anfang der Liste eingefügt werden. Die verbleibenden Facetten werden nach den eingefügten Facetten in der Reihenfolge *Sortiertyp* aufgeführt.
* Dynamische Facetten: Produktattribute, die [Adobe Sensei](https://www.adobe.com/sensei.html) für einen Produktsatz und eine Abfrage am relevantesten findet. Die Berechnung berücksichtigt die Attributmetadaten des gesamten Katalogs und bestimmt zum Zeitpunkt der Abfrage die relevantesten Facetten für die Abfrage.

  >[!NOTE]
  >
  >Wenn Sie feststellen, dass in der GraphQL-Abfrageantwort nach dem Erstellen dynamischer Facetten Timeout-Fehler auftreten, ändern Sie alle Facetten in &quot;Pinned&quot;, um festzustellen, ob dadurch die Leistungsprobleme behoben werden.

* Beliebte Facetten: Produktattribute, die am häufigsten in Suchergebnissen vorhanden sind.
* Preisfacetten - Rückgabe von Produkten nach Preisbereich. Sie können die Anzahl der Auswahlen und das Preisbereichsintervall im Arbeitsbereich [*Einstellungen*](settings.md) angeben.

Zum Zeitpunkt der Abfrage generiert [!DNL Live Search] die Suchergebnisse in Gruppen dynamischer und beliebter Facetten.

![Facets - Price](assets/storefront-search-results-run-price.png)

## Storefront- und Headless-Optionen

Facets, die für die [!DNL Commerce] -Storefront gerendert werden, werden vom Suchadapter verarbeitet, der die Anforderungen weiterleitet und die Ergebnisse in der Storefront rendert. Alle [!DNL Commerce] Storefront-Facetten werden alphabetisch mit Einzelauswahl-Optionen sortiert, unabhängig vom Eingabetyp, der dem entsprechenden Attribut zugewiesen ist. Facets, die in der Storefront verfügbar sind, werden entsprechend dem aktuellen Design gerendert und spiegeln alle Anpassungen wider, die an der Präsentation der Navigation mit Ebenen vorgenommen wurden.

Im Gegensatz dazu werden Implementierungen von [Headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) von der API verarbeitet und unterstützen zusätzliche Optionen. Headless-Facetten können alphabetisch oder nach Anzahl sortiert werden und können über Einzel- oder Mehrfachauswahloptionen verfügen.

### Facettenbeschriftungen

Bei [!DNL Commerce] -Storefronts wird die Facettenbeschriftung durch die [*Attributeigenschaften*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) bestimmt. Bei Geschäften mit mehreren Ansichten können unter *Bezeichnungen verwalten* zusätzliche Bezeichnungen definiert werden. Bei Headless-Implementierungen werden Beschriftungen aus dem [faceting-Arbeitsbereich](faceting-workspace.md) bearbeitet.

### Sortiertyp

Alle für die Storefront gerenderten Facetten werden alphabetisch sortiert. Bei Headless-Implementierungen können Facetten alphabetisch oder nach Anzahl sortiert werden.

| Sortiertyp | Beschreibung |
|--- |--- |
| Alphabetisch | In der Storefront-Liste *Filter* werden Facetten alphabetisch sortiert. |
| Count | (Nur Headless) Bei Headless-Implementierungen können Facetten auch nach der Anzahl der Werte sortiert werden, die pro Facette im aktuellen Satz der zurückgegebenen Produkte gefunden werden. |
