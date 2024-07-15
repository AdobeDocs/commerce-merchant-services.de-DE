---
title: Empfehlung bearbeiten
description: Erfahren Sie, wie Sie eine Produktempfehlung bearbeiten.
exl-id: 36fd6d3a-74f8-4510-a187-a2a91742cd1a
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Empfehlung bearbeiten

Auf der Seite Empfehlung bearbeiten können Sie die einzelnen Einstellungen der Empfehlung anpassen. Mit Ausnahme des Seitentyps und des Empfehlungstyps können alle Einstellungen bearbeitet werden. Die folgenden Einstellungen können bearbeitet werden:

- [Empfehlungsname](#name)
- [Storefront-Bezeichnung](#label)
- [Anzahl Produkte](#number)
- [Platzierung und Position](#placement)
- [Produkte filtern](#filters)

Die Vorschau auf der rechten Seite der Seite zeigt, wie die Empfehlung mit den aktuellen Einstellungen im Storefront angezeigt werden kann. Die Vorschau _Empfohlene Produkte_ bleibt als Referenz sichtbar, wenn Sie nach unten scrollen. In der Vorschau werden ein Miniaturbild für das Produkt, der Produktname, die SKU, der Preis und der Ergebnistyp für jedes zurückgegebene Produkt angezeigt. Der Ergebnistyp gibt an, ob ausreichend primäre Verhaltensdaten vorhanden sind, um die Empfehlung zu generieren, oder ob es Sicherungsverhaltensdaten verwendet.

![Recommendations bearbeiten](assets/edit-recommendation.png)

## Empfehlungen bearbeiten

1. Wechseln Sie in der Seitenleiste _Admin_ zu **Marketing** > _Promotions_ > **Produkt-Recommendations**.

1. Wählen Sie die Empfehlung aus, die Sie bearbeiten möchten.

1. Klicken Sie auf **Bearbeiten**. Folgen Sie dann den unten stehenden Anweisungen, um die gewünschten Änderungen vorzunehmen.

1. Klicken Sie nach Abschluss des Vorgangs auf **Änderungen speichern**.

### Empfehlungsname {#name}

Wählen Sie einen beschreibenden Namen, der den Zweck der Empfehlung angibt. Der Name dient als interne Referenz und wird nicht in der Storefront angezeigt.

![Name bearbeiten](assets/edit-name.png)

### Storefront-Bezeichnung {#label}

Geben Sie den Text ein, den Sie als Beschriftung für die Empfehlungseinheit in der Storefront verwenden möchten.

![Titel bearbeiten](assets/edit-storefront-label.png)

### Anzahl Produkte {#number}

Passen Sie den Schieberegler an, um bis zu 20 Produkte in der Empfehlungseinheit anzuzeigen.

![Anzahl der Produkte bearbeiten](assets/edit-number-of-products.png)

### Platzierung und Position {#placement}

1. Wählen Sie den Speicherort der Seite aus, an der die Empfehlungseinheit in der Storefront angezeigt werden soll.

   - Am unteren Rand des Hauptinhalts
   - Oben im Hauptinhalt

   ![Platzierung bearbeiten](assets/edit-placement.png)

1. Um die Reihenfolge der Empfehlungen zu ändern, die in der Einheit enthalten sind, verwenden Sie das Steuerelement **Verschieben** ![Auswahl verschieben](assets/icon-move.png) , um die Empfehlungen an die gewünschte Position zu ziehen.

   ![Position bearbeiten](assets/edit-position.png)

### Produkte filtern {#filters}

Alle Änderungen an Produkt [filtern](filters.md) werden in der Vorschau für empfohlene Produkte _3} angezeigt._ Es dürfen nur Produkte empfohlen werden, die mit Einschlussfiltern übereinstimmen. Produkte, die mit Ausschlussfiltern übereinstimmen, werden nicht empfohlen.

Die Registerkarten _Einschlüsse_ und _Ausschlüsse_ enthalten die verfügbaren Filter für jeden Typ. In der Liste ist jeder aktive Filter mit einem blauen Punkt markiert.

- Um Details zu den einzelnen Filtern anzuzeigen, klicken Sie auf den Namen des Filters.
- Um den Filterstatus zu ändern, stellen Sie den Umschalter **Filter aktivieren** auf die Position `on` oder `off` ein.

![Filter bearbeiten](assets/edit-filters.png)

Die Filtereinstellungen beschreiben die Produkte, die in die Empfehlungseinheit aufgenommen oder ausgeschlossen werden sollen. Beispielsweise weisen die Einstellungen für die Filtereinbindung für _Kategorie_ an, dass das System nur Produkte aus den ausgewählten Kategorien einbeziehen soll.

![Kategoriefilter bearbeiten](assets/edit-filter-category.png)
