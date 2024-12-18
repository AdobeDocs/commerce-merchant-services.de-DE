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

Die Seite Empfehlung bearbeiten bietet Ihnen die Möglichkeit, die individuellen Einstellungen für die Empfehlung anzupassen. Alle Einstellungen außer dem Seitentyp und dem Empfehlungstyp können bearbeitet werden. Die folgenden Einstellungen können bearbeitet werden:

- [Name der Empfehlung](#name)
- [Storefront-Bezeichnung](#label)
- [Anzahl der Produkte](#number)
- [Platzierung und Position](#placement)
- [Produkte filtern](#filters)

Die Vorschau rechts auf der Seite zeigt, wie die Empfehlung mit den aktuellen Einstellungen in der Storefront aussehen könnte. Die _Empfohlene Produktvorschau_ bleibt beim Scrollen auf der Seite zur Referenz sichtbar. Die Vorschau zeigt ein Miniaturbild des Produkts, den Produktnamen, die SKU, den Preis und den Ergebnistyp für jedes zurückgegebene Produkt an. Der Ergebnistyp gibt an, ob genügend primäre Verhaltensdaten vorhanden sind, um die Empfehlung zu generieren, oder ob Sicherungsverhaltensdaten verwendet werden.

![Recommendations bearbeiten](assets/edit-recommendation.png)

## Bearbeiten einer Empfehlung

1. Navigieren Sie in der _Admin_-Seitenleiste zu **Marketing** > _Promotions_ > **Product Recommendations**.

1. Wählen Sie die Empfehlung aus, die Sie bearbeiten möchten.

1. Klicken Sie **Bearbeiten**. Folgen Sie dann den unten stehenden Anweisungen, um die benötigten Änderungen vorzunehmen.

1. Klicken Sie abschließend auf **Änderungen speichern**.

### Name der Empfehlung {#name}

Wählen Sie einen beschreibenden Namen, der den Zweck der Empfehlung angibt. Der Name dient als interne Referenz und wird nicht in der Storefront angezeigt.

![Name bearbeiten](assets/edit-name.png)

### Storefront-Bezeichnung {#label}

Geben Sie den Text ein, den Sie als Titel für die Empfehlungseinheit in der Storefront verwenden möchten.

![Bezeichnung bearbeiten](assets/edit-storefront-label.png)

### Anzahl der Produkte {#number}

Stellen Sie den Schieberegler ein, um bis zu 20 Produkte in der Empfehlungseinheit anzuzeigen.

![Anzahl der Produkte bearbeiten](assets/edit-number-of-products.png)

### Platzierung und Position {#placement}

1. Wählen Sie den Seitenspeicherort aus, an dem die Empfehlungseinheit in der Storefront angezeigt werden soll.

   - Am Ende des Hauptinhalts
   - Am Anfang des Hauptinhalts

   ![Platzierung bearbeiten](assets/edit-placement.png)

1. Um die Reihenfolge der Empfehlungen zu ändern, die in der Einheit enthalten sind, ziehen Sie die Empfehlungen mit dem Steuerelement **Verschieben** ![Auswahl verschieben](assets/icon-move.png) in die gewünschte Position.

   ![Position bearbeiten](assets/edit-position.png)

### Produkte filtern {#filters}

Alle Änderungen an [Filtern](filters.md) werden in der _Empfohlene Produktvorschau_ angezeigt. Es dürfen nur Produkte empfohlen werden, die mit Einschlussfiltern übereinstimmen. Produkte, die Ausschlussfiltern entsprechen, werden nicht empfohlen.

Die _Einschlüsse_ und _Ausschlüsse_ führen die verfügbaren Filter jedes Typs auf. In der Liste ist jeder aktive Filter mit einem blauen Punkt markiert.

- Um die Details der einzelnen Filter anzuzeigen, klicken Sie auf den Filternamen.
- Um den Filterstatus zu ändern, setzen Sie den Umschalter **Filter aktivieren** auf die `on` oder `off`.

![Filter bearbeiten](assets/edit-filters.png)

Die Filtereinstellungen beschreiben die Produkte, die in der Empfehlungseinheit ein- oder ausgeschlossen werden sollen. Beispielsweise weisen die Einstellungen _Kategorie_ für die Filtereinbindung das System an, nur Produkte aus den ausgewählten Kategorien einzubeziehen.

![Kategoriefilter bearbeiten](assets/edit-filter-category.png)
