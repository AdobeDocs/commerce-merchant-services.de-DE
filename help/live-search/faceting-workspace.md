---
title: "Faceting Workspace"
description: '"Erfahren Sie mehr über den Arbeitsbereich für die facettierte Arbeit." [!DNL Live Search] '
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Facebook Workspace

Der Arbeitsbereich *Faceting* listet alle derzeit verfügbaren Facetten auf und bietet Zugriff auf die Tools, die Sie zum Einrichten und Verwalten von Facetten benötigen. Angeheftete Facetten erscheinen zuerst in der Liste vorhandener Facetten, gefolgt von dynamischen Facetten. Die Liste kann gefiltert werden, um alle Facetten anzuzeigen, oder nur diejenigen, die fixiert oder dynamisch sind.

![Faceting-Arbeitsbereich](assets/faceting-workspace.png)

## Festlegen des Umfangs

Wenn Ihre Adobe Commerce-Installation mehrere Store-Ansichten enthält, setzen Sie **Umfang** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings), in der Ihre Facetteneinstellungen gelten.

## Liste filtern

1. Klicken Sie auf das Steuerelement **Filtern nach** .
1. Wählen Sie eine der folgenden Optionen aus:

   * Alle Filter
   * Angeheftet
   * Dynamik

## Facette hinzufügen

1. Klicken Sie auf **Facetten hinzufügen**.
1. Detaillierte Anweisungen finden Sie unter [Facets hinzufügen](facets-add.md) .

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|--- |--- |
| (erste Spalte) | Listet fixierte und dynamische Facetten mit der [Beschriftung](facets-type.md) auf, die für den Käufer sichtbar ist. |
| Sortiertyp | Die [Sortierreihenfolge](facets-type.md) der Facettenwerte. Facets werden alphabetisch nach allen [!DNL Commerce] Storefronts sortiert. Bei Implementierungen von [Headless] können Facetten entweder alphabetisch oder nach Anzahl sortiert werden. Optionen: Alphabetisch, Zählung (nur Headless) |
| Max. Wert | Die Anzahl der Facettenwerte, die in der Storefront als Filter verfügbar sind, mit einer maximalen Anzahl von 10. |

## Steuerelemente

| Kontrolle | Beschreibung |
|--- |--- |
| Hinzufügen von Facetten | Öffnet den [Facetteneditor](facets-add.md). |
| Filtern nach | Bestimmt den [Typ der in der Liste angezeigten Facetten](facets-type.md). Optionen: Alle, angeheftet, dynamisch |
