---
title: "Facets hinzufügen"
description: "Erfahren Sie, wie Sie filterbare Produktattribute als [!DNL Live Search] Facetten hinzufügen."
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 2439e9c2b38269e1cf9761d2b662abce76b8304e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Facets hinzufügen

Jedes filterbare Produktattribut kann als Facette verwendet werden. Das Bedienfeld *Facetten hinzufügen* listet die aktuellen Facetten auf und erleichtert die Zuweisung zusätzlicher Produktattribute als Facetten. Während dieses dreistufigen Prozesses wird ein Attribut ausgewählt, das als Facette verwendet werden soll, Eigenschaften werden bei Bedarf bearbeitet und die Änderungen werden in der Storefront veröffentlicht.

![Facets hinzufügen](assets/facets-add.png)

## Schritt 1: Hinzufügen einer Facette

1. Wechseln Sie im Admin zu **Marketing** > SEO &amp; Suche > **[!DNL Live Search]**.
1. Klicken Sie auf der Registerkarte *Faceting* auf **Facetten hinzufügen**.
1. In der Liste *Facetten hinzufügen* verfügt jedes verfügbare Attribut über eine separate Schaltfläche zum Hinzufügen ![3}. ](assets/btn-add.png) Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Liste *Faceting attributes* das Produktattribut aus, das Sie als Facette verwenden möchten, und klicken Sie auf **Hinzufügen**.
   * Um ein bestimmtes Produktattribut zu finden, geben Sie die ersten Zeichen des Attributnamens in das Feld *Suchen* ein. Klicken Sie dann auf **Hinzufügen**.

     Informationen zum Konfigurieren von Preisfacettenintervallen und -gruppierungen finden Sie unter [Einstellungen](settings.md). Weitere Informationen finden Sie unter [Facettentypen](facets-type.md).
Die Facette wird am unteren Rand der Liste *Dynamische Facets* hinzugefügt und die Schaltfläche *Publish ändert* wird verfügbar.

1. Wenn die Facette, die Sie hinzufügen möchten, nicht gefunden werden kann, gehen Sie zu **Stores** > Attribute > **Produkt** und überprüfen Sie, ob das Attribut über die [erforderlichen Eigenschaften](facets.md) verfügt, die als Facette verwendet werden sollen. Aktualisieren Sie bei Bedarf die folgenden Storefront-Eigenschaften des Attributs:

   * In Suche verwenden - `Yes`
   * Verwendung in mehrstufiger Navigation mit Suchergebnissen - `Yes`
   * Verwendung in mehrschichtiger Navigation - `Filterable (with results)`

1. Wenn Sie dazu aufgefordert werden, aktualisieren Sie den Cache.

   Die Facette wird in der Storefront verfügbar, wenn der Katalog das nächste Mal mit [!DNL Live Search] synchronisiert wird. Wenn die Facette nach zwei Stunden nicht verfügbar ist, lesen Sie den Abschnitt [Katalogdaten synchronisieren](install.md#synchronize-catalog-data).

## Schritt 2: Eigenschaften von Facetten bearbeiten (optional)

1. Um die Facetteneigenschaften zu bearbeiten, klicken Sie in der Spalte ganz rechts auf die Optionen **Mehr** (![Mehr Selektor](assets/btn-more.png)).
1. Klicken Sie im Menü auf **Bearbeiten**. Passen Sie dann die folgenden Eigenschaften nach Bedarf an.

   * Beschriftung - ([Headless](facets-type.md)) Geben Sie die Facettenbeschriftung ein, die Sie verwenden möchten.
   * Sortiertyp - Facets werden für alle [!DNL Commerce] Storefronts alphabetisch sortiert. Bei Headless-Implementierungen können Facetten entweder alphabetisch oder nach Anzahl sortiert werden. Optionen: Alphabetisch, Zählung (nur Headless)
   * Max. Wert - Geben Sie die maximale Anzahl an Facettenwerten ein, die in der Storefront angezeigt werden. Gültige Einträge: 0 - 100; Standard: 8

1. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

   ![Facets bearbeiten](assets/facet-edit.png)

1. Um die Facette am Anfang der Liste *Filter* zu veröffentlichen, klicken Sie auf den grauen Pin (![Pin-Selektor](assets/btn-pin-gray.png)).
1. Um die Reihenfolge der fixierten Facette zu ändern, klicken Sie auf das Symbol **Verschieben** (![Auswahl verschieben](assets/btn-move.png)) und ziehen Sie die Zeile an eine neue Position im Abschnitt *Angeheftete Facets* .

## Schritt 3: Publish-Änderungen

1. Wenn die Facette abgeschlossen ist, klicken Sie auf **Publish changes**.
1. Warten Sie, bis die Facette im Store angezeigt wird.
Wenn die Facette nach zwei Stunden nicht verfügbar ist, lesen Sie den Abschnitt [Export überprüfen](install.md#synchronize-catalog-data) in den Installationsanweisungen.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Titel | ([Headless](facets-type.md) only) Die in der Storefront sichtbare [Facettenbeschriftung](facets-type.md) kann bearbeitet werden, um eine Konsistenz mit Ihrer Marke zu gewährleisten. |
| Sortiertyp | Die Methode, die für [sort](facets-type.md) -Facetten verwendet wird. Alle [!DNL Commerce] -Storefronts sortieren Facetten nur alphabetisch. Headless-Implementierungen können auch nach `Count` sortiert werden. Optionen:<br />Alphabetisch - Sortiert Facetten alphabetisch.<br />Zählung - (nur Headless) Sortiert Facetten basierend auf der Anzahl der gefundenen Übereinstimmungen. |
| Max. Wert | Die maximale Anzahl von Werten, die in der Storefront für jede Facette angezeigt werden können. Facets, die einen Wertebereich darstellen, sind gleichmäßig verteilt. Gültige Einträge: 0 - 100; Standard: 8 |

### Steuerelemente

| Kontrolle | Beschreibung |
|--- |--- |
| ![Pin selector](assets/btn-pin-blue.png) | Fügt eine Facette an den Anfang der Liste *Filter* an oder hebt sie auf. |
| ![Mehr selector](assets/btn-more.png) | Zeigt ein Menü mit weiteren Aktionen an, die auf die ausgewählte Facette angewendet werden können. Optionen: Bearbeiten, Löschen |
| ![Selektor verschieben](assets/btn-move.png) | Verwenden Sie das Symbol *Verschieben* , um eine fixierte Facette an eine andere Stelle im Abschnitt *Angeheftete Facetten* zu ziehen. |
