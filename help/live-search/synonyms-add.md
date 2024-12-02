---
title: Synonyme hinzufügen
description: Fügen Sie  [!DNL Live Search] Synonyme hinzu, um die Antwort auf Suchanfragen zu verbessern.
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 63318e2eb75bc5fb0a243b6430751b076e541b72
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Synonyme hinzufügen

Erhöhen Sie die Kundeninteraktion, indem Sie Ihre eigene kuratierte Liste mit [!DNL Live Search] -Synonymen hinzufügen. [!DNL Live Search] kann bis zu 200 Synonyme pro `Data Space ID` verwalten.

![[!DNL Live Search] synonyme](assets/synonym-workspace.png)

## Schritt 1: Synonym hinzufügen

1. Wechseln Sie im Admin zu **Marketing** > SEO &amp; Suche > **[!DNL Live Search]**.
1. Legen Sie für mehrere Stores **Umfang** auf die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) fest, für die die Synonym-Einstellungen gelten.
1. Klicken Sie auf die Registerkarte **Synonyme**.
1. Klicken Sie auf die Schaltfläche **Synonyme hinzufügen** .

## Schritt 2: Synonym nach Typ definieren

Befolgen Sie die Anweisungen für den [Typ des Synonyms](synonyms-type.md), den Sie erstellen möchten.

### Zweiwegsynonym

1. Akzeptieren Sie die Standardoption **Zwei-Wege** .

   ![Zweiweg-Synonym hinzufügen](assets/synonym-add-two-way.png)


1. Geben Sie den Begriff oder die Phrase **Schlüsselwort** ein, der abgeglichen werden soll.
1. Geben Sie die Begriffe **Erweiterung** ein, die Sie als Synonyme für den Suchbegriff hinzufügen möchten. Trennen Sie mehrere Begriffe durch ein Komma.
In diesem Beispiel lautet das passende Keyword &quot;Hosen&quot;und die Erweiterungsbegriffe lauten &quot;Hosen, Schläge&quot;.

   ![Synonym-Beispiel für Zweiwege](assets/synonym-add-two-way-example.png)

1. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.
Der Satz von Synonymen erscheint in der Liste mit einem Zwei-Wege-Pfeil zwischen jedem Begriff, was bedeutet, dass die Begriffe austauschbar sind.

   ![Zweiweg-Synonym](assets/synonym-two-way.png)

### Einwegsynonym

1. Klicken Sie auf den Synonym-Typ **Einweg** .

   ![Einweg-Synonym hinzufügen](assets/synonym-add-one-way.png)

1. Geben Sie die Begriffe **Schlüsselwort** und **Erweiterung** ein. Trennen Sie mehrere Begriffe durch ein Komma.

   ![Beispiel für Einweg-Synonym](assets/synonym-add-one-way-example.png)

   In diesem Beispiel ist das Keyword &quot;Hosen&quot;und die unidirektionalen Erweiterungsbegriffe &quot;Capris, Peddle-Pushers&quot;sind jeweils eine Untergruppe von &quot;Hots&quot;, jedoch mit einer bestimmten Bedeutung.

1. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.
Die Gruppe von Synonymen wird in der Liste mit einem einseitigen Pfeil angezeigt, der von den Erweiterungsbegriffen zum Keyword zeigt, um anzugeben, dass es sich bei den Begriffen um Untergruppen des Keywords handelt. Ein Pluszeichen trennt jeden Erweiterungsbegriff.

   ![Einweg-Synonym](assets/synonym-one-way.png)

## Schritt 3: Publish-Änderungen

1. Wenn Ihre Synonyme abgeschlossen sind, klicken Sie auf **Publish changes**.
1. Warten Sie bis zu zwei Stunden, bis Ihre Updates in der Storefront verfügbar sind.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| [Typ](synonyms.md) | Bestimmt, ob die Synonyme dieselbe Bedeutung wie das Keyword haben oder eine Untergruppe des Keywords sind. Optionen:<br />Zweiweg (Standard) - Begriffe, die dieselbe Bedeutung wie der Suchbegriff haben und dieselben Suchergebnisse zurückgeben<br />Einweg - Begriffe, die eine Untergruppe des Suchbegriffs sind. Einwegsynonyme geben eine engere Liste spezifischer Produkte zurück. |
| Schlüsselwort | Ein Wort, das häufig mit einer Auswahl von Produkten in Ihrem Katalog verknüpft ist. |
| Erweiterung | Zusätzliche Begriffe, die dieselbe oder eine ähnliche Bedeutung wie der Suchbegriff haben. |
