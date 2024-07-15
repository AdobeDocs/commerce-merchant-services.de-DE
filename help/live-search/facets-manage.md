---
title: "Facets verwalten"
description: "Erfahren Sie, wie Sie vorhandene [!DNL Live Search] Facetten verwalten."
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: bce69f952e70e2e8dcb892357dea41e18f61e5f6
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Facets verwalten

Befolgen Sie diese Anweisungen, um die Eigenschaften vorhandener Facetten zu aktualisieren oder ihre Darstellung im Storefront zu ändern.

## Preisfacettengruppierungen konfigurieren

Informationen zum Konfigurieren von Preisfacettierungsintervallen und -gruppierungen finden Sie unter [Einstellungen](settings.md) .

## Facette bearbeiten

1. Suchen Sie die Facette, die Sie bearbeiten möchten.
1. Wenn die Liste viele Facetten enthält, setzen Sie *Filtern nach* auf eine der folgenden Optionen:

   * Angeheftet
   * Dynamik

   Weitere Informationen finden Sie unter [Facettentypen](facets-type.md).

   ![Filterfacetten](assets/facets-filter-by-cropped.png)

1. Um die Facetteneigenschaften zu bearbeiten, klicken Sie auf die Optionen **Mehr** (...) .
1. Klicken Sie auf **Bearbeiten**

   ![Bearbeitungsoptionen](assets/facet-edit-menu.png)

1. Führen Sie einen der folgenden Schritte aus, um die Facettenbeschriftung zu bearbeiten:

   * Bearbeiten Sie für eine [!DNL Commerce] -Storefront die [Attributbezeichnung](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * Klicken Sie bei einer Headless-Implementierung auf den Wert in der ersten Spalte und bearbeiten Sie den Text nach Bedarf.

   ![Titel bearbeiten](assets/facet-edit-label.png)

1. (Nur Headless) Um die Methode zu ändern, die zum Sortieren von Facettenwerten verwendet wird, klicken Sie auf den Wert in der Spalte *Sortiertyp* und wählen Sie eine der folgenden Optionen:

   * Alphabetisch
   * Count

   ![Anzahl bearbeiten](assets/facets-edit-count.png)

1. Legen Sie in der Spalte **Max. Wert** die maximale Anzahl (von 0 bis 10) der Facettenfilterwerte fest, die im Storefront angezeigt werden sollen.
1. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.
Ihre Änderungen werden erst dann in der Storefront angezeigt, nachdem sie veröffentlicht wurden.

## Facette des Pins/Entpin

Der Pin ändert die Farbe, wenn darauf geklickt wird, und wird verwendet, um die Facette in den Abschnitt *Pinned Facets* oder *Dynamische Facets* zu verschieben.

1. Um eine Facette am Anfang der Liste *Filter* zu veröffentlichen, suchen Sie die Facette in der Liste *Dynamische Facets* und klicken Sie auf den grauen Pin (![Pin-Selektor](assets/btn-pin-gray.png)).
Der Stift wird blau und die Facette wechselt zum Abschnitt *Angeheftete Facets* .
1. Um die Facette zu entsperren, suchen Sie die Facette in der Liste *Angeheftete Facets* und klicken Sie auf den blauen Pin (![Pin-Selektor](assets/btn-pin-blue.png)).
Der Pin wird grau und die Facette wechselt zum Abschnitt *Dynamische Facets* .

   ![Verpinnte und dynamische Facetten](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>Die Reihenfolge von fixierten Facetten kann inkonsistent sein, wenn es zwei Bezeichnungen mit demselben Namen gibt.

## Fixierte Facette verschieben

>[!NOTE]
>
>Die Reihenfolge von fixierten Facetten wird nur in Headless-Implementierungen unterstützt. Wenn geordnete Facetten benötigt werden, verwenden Sie das PLP-Widget [!DNL Live Search] .

Die Reihenfolge der fixierten Facetten kann geändert werden, indem die Zeile an eine andere Position verschoben wird. Versteckte Facetten haben am Anfang der Zeile ein *Verschieben* -Symbol (![Verschieben-Selektor](assets/btn-move.png)). Im Gegensatz zu fixierten Facetten können dynamische Facetten nicht verschoben werden.

1. Suchen Sie die Facette im Abschnitt *Angeheftete Facets* der Liste.
1. Verwenden Sie das Symbol **Verschieben** (![Auswahl verschieben](assets/btn-move.png)), um die Zeile an eine neue Position im Abschnitt *Angeheftete Facets* zu ziehen.
Nachdem die Änderungen veröffentlicht wurden, werden die neu sortierten Facetten in der Storefront-Liste *Filter* angezeigt.

## Facette löschen

1. Suchen Sie die Facette in der Liste und klicken Sie auf die Optionen **Mehr** (...).
1. Klicken Sie auf **Löschen**.
1. Wenn Sie zur Bestätigung aufgefordert werden, klicken Sie auf **Facette löschen**.
Die Facette wird aus der Storefront entfernt, nachdem die Änderungen veröffentlicht wurden.

## Publish-Änderungen

1. Um die Storefront mit Ihren Änderungen zu aktualisieren, klicken Sie auf **Publish changes**.
1. Warten Sie etwa 15 Minuten, bis die Aktualisierungen in Ihrem Store angezeigt werden.
