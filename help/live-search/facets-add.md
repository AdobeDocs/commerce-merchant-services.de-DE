---
title: Facets hinzufügen
description: Erfahren Sie, wie Sie filterbare Produktattribute als Live-Suchfacetten hinzufügen.
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: f31c76404315a9fe142bf0c72ff9999c4a87365d
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Facets hinzufügen

Jedes filterbare Produktattribut kann als Facette verwendet werden. Die *Hinzufügen von Facetten* -Bedienfeld listet die aktuellen Facetten auf und erleichtert die Zuweisung zusätzlicher Produktattribute als Facetten. Während dieses dreistufigen Prozesses wird ein Attribut ausgewählt, das als Facette verwendet werden soll, Eigenschaften werden bei Bedarf bearbeitet und die Änderungen werden in der Storefront veröffentlicht.

![Factory-Arbeitsbereich](assets/facets-add.png)

## Schritt 1: Facette hinzufügen

1. Navigieren Sie im Admin zu **Marketing** > SEO &amp; Suche > **[!DNL Live Search]**.
1. Im *Facebook* Registerkarte, klicken Sie auf **Hinzufügen von Facetten**.
1. Im *Hinzufügen von Facetten* enthält jedes verfügbare Attribut eine separate *Hinzufügen* Schaltfläche. Führen Sie einen der folgenden Schritte aus:

   ![Facette hinzugefügt](assets/facets-list-add.png)

   * Im *Facettenattribute* auflisten, das Produktattribut auswählen, das Sie als Facette verwenden möchten, und auf **Hinzufügen**.
   * Um ein bestimmtes Produktattribut zu finden, geben Sie die ersten Zeichen des Attributnamens in die *Suche* ankreuzen. Klicken Sie anschließend auf **Hinzufügen**.

      Informationen zum Konfigurieren von Preisfacettenintervallen und -gruppierungen finden Sie unter [Einstellungen](settings.md). Weitere Informationen finden Sie unter [Facettentypen](facets-type.md).
Die Facette wird am unteren Rand des *Dynamische Facetten* und *Veröffentlichungsänderungen* -Schaltfläche verfügbar.
   ![Facette hinzugefügt](assets/facet-added.png)

1. Wenn die Facette, die Sie hinzufügen möchten, nicht gefunden werden kann, gehen Sie zu **Stores** > Attribute > **Produkt** und überprüfen Sie, ob das -Attribut die [erforderliche Eigenschaften](facets.md) als Facette verwendet werden. Aktualisieren Sie bei Bedarf die folgenden Storefront-Eigenschaften des Attributs:

   * Verwenden in der Suche - `Yes`
   * Verwendung in der Navigation mit Suchergebnisebenen - `Yes`
   * Verwendung in mehrschichtiger Navigation - `Filterable (with results)`

1. Wenn Sie dazu aufgefordert werden, aktualisieren Sie den Cache.

   Die Facette wird in der Storefront verfügbar, wenn der Katalog das nächste Mal mit [!DNL Live Search]. Wenn die Facette nach zwei Stunden nicht verfügbar ist, lesen Sie [Katalogdaten synchronisieren](install.md#synchronize-catalog-data).

## Schritt 2: Eigenschaften von Facetten bearbeiten (optional)

1. Um die Facetteneigenschaften zu bearbeiten, klicken Sie auf **Mehr** (![Mehr Auswahl](assets/btn-more.png)) in der Spalte ganz rechts.
1. Klicken Sie im Menü auf **Bearbeiten**. Passen Sie dann die folgenden Eigenschaften nach Bedarf an.

   * Titel - ([Headless](facets-type.md) nur) Geben Sie die Facettenbeschriftung ein, die Sie verwenden möchten.
   * Typ auswählen - die *Typ auswählen* für alle [!DNL Commerce] storefronts is `single select`. Bei Headless-Implementierungen: `multi-select` Typ kann mit einem logischen Operator (`or` oder `and`), um den Satz der zurückgegebenen Produkte zu bestimmen.
   * Sortiertyp - Facets werden alphabetisch für alle sortiert [!DNL Commerce] Storefronts. Bei Headless-Implementierungen können Facetten entweder alphabetisch oder nach Anzahl sortiert werden. Optionen: Alphabetisch, Anzahl (nur Headless)
   * Max. Wert - Geben Sie die maximale Anzahl an Facettenwerten ein, die in der Storefront angezeigt werden. Gültige Einträge: 0-30; Standard: 8

1. Wenn Sie fertig sind, klicken Sie auf **Speichern**.

   ![Factory-Arbeitsbereich](assets/facet-edit.png)

1. So veröffentlichen Sie die Facette am oberen Rand des *Filter* Liste, klicken Sie auf die graue Push-Taste (![Pin-Auswahl](assets/btn-pin-gray.png)).
1. Um die Reihenfolge der fixierten Facette zu ändern, klicken Sie auf die **Verschieben** (![Auswahl verschieben](assets/btn-move.png)) und ziehen Sie die Zeile an eine neue Position im *Angeheftete Facetten* Abschnitt.

## Schritt 3: Veröffentlichungsänderungen

1. Wenn die Facette abgeschlossen ist, klicken Sie auf **Veröffentlichungsänderungen**.
1. Warten Sie, bis die Facette im Store angezeigt wird.
Wenn die Facette nach zwei Stunden nicht verfügbar ist, lesen Sie [Export überprüfen](install.md#synchronize-catalog-data) in den Installationsanweisungen.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Titel | ([Headless](facets-type.md) nur) Die [Facet-Bezeichnung](facets-type.md) die in der Storefront sichtbar sind, können zur Konsistenz mit Ihrer Marke bearbeitet werden. |
| Typ auswählen | Zeigt die [Auswahlmethode](facets-type.md) das mit dem Produktattribut verknüpft ist. Alle Facetten im [!DNL Commerce] Storefronts sind `Single select` nur. Headless-Implementierungen unterstützen auch `Multi-select` mit den logischen Operatoren `OR` und `AND`. |
| Sortiertyp | Die Methode, mit der [sort](facets-type.md) Facetten. Alle [!DNL Commerce] storefronts sortiert Facetten nur alphabetisch. Headless-Implementierungen können auch nach `Count`. Optionen:<br />Alphabetisch - Sortiert Facetten alphabetisch.<br />Anzahl - (nur Headless) Sortiert Facetten basierend auf der Anzahl der gefundenen Übereinstimmungen. |
| Max. Wert | Die maximale Anzahl von Werten, die in der Storefront für jede Facette angezeigt werden können. Facets, die einen Wertebereich darstellen, sind gleichmäßig verteilt. Gültige Einträge: 0-30; Standard: 8 |

### Steuerelemente

| Kontrolle | Beschreibung |
|--- |--- |
| ![Pin-Auswahl](assets/btn-pin-blue.png) | Pinnt eine Facette an die Oberseite an oder hebt sie auf *Filter* Liste. |
| ![Mehr Auswahl](assets/btn-more.png) | Zeigt ein Menü mit weiteren Aktionen an, die auf die ausgewählte Facette angewendet werden können. Optionen: Bearbeiten, Löschen |
| ![Auswahl verschieben](assets/btn-move.png) | Verwenden Sie die *Verschieben* Symbol, um eine fixierte Facette an eine andere Position im *Angeheftete Facetten* Abschnitt. |
