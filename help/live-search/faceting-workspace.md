---
title: "Faceting Workspace"
description: '"Machen Sie sich mit dem [!DNL Live Search] Arbeitsbereich "facettieren".'
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: e166c8cb9d715dce573195a188b5335c02d8fd0c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Factory Workspace

Die [!DNL Live Search] Workspace listet alle derzeit verfügbaren Facetten auf und bietet Zugriff auf die Tools, die Sie zum Einrichten und Verwalten von Facetten benötigen. Angeheftete Facetten erscheinen zuerst in der Liste vorhandener Facetten, gefolgt von dynamischen Facetten. Die Liste kann gefiltert werden, um alle Facetten anzuzeigen, oder nur diejenigen, die fixiert oder dynamisch sind.

![Factory-Arbeitsbereich](assets/faceting-workspace.png)

## Festlegen des Umfangs

Wenn Ihre Adobe Commerce-Installation mehrere Store-Ansichten enthält, legen Sie **Anwendungsbereich** der [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) wo Ihre Facetteneinstellungen angewendet werden.

## Liste filtern

1. Klicken Sie auf **Filtern nach** Kontrolle.
1. Wählen Sie eine der folgenden Optionen aus:

   * Alle Filter
   * Angeheftet
   * Dynamik

## Facette hinzufügen

1. Klicks **Hinzufügen von Facetten**.
1. Siehe [Facets hinzufügen](facets-add.md) für detaillierte Anweisungen.

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|--- |--- |
| (erste Spalte) | Listet fixierte und dynamische Facetten von [label](facets-type.md) für den Käufer sichtbar ist. |
| Sortiertyp | Die [Sortierreihenfolge](facets-type.md) von Facettenwerten. Facets werden alphabetisch für alle sortiert [!DNL Commerce] Storefronts. Für [Headless] -Implementierungen können Facetten entweder alphabetisch oder nach Anzahl sortiert werden. Optionen: Alphabetisch, Zählung (nur Headless) |
| Max. Wert | Die Anzahl der Facettenwerte, die in der Storefront als Filter verfügbar sind, mit einer maximalen Anzahl von 10. |

## Steuerelemente

| Kontrolle | Beschreibung |
|--- |--- |
| Hinzufügen von Facetten | Öffnet die [Facetteneditor](facets-add.md). |
| Filtern nach | Bestimmt die [Facettentyp](facets-type.md) in der Liste angezeigt. Optionen: Alle, angeheftet, dynamisch |
