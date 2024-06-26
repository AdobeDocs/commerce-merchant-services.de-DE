---
title: "Search Merchandising Workspace"
description: '"Erfahren Sie mehr über den Arbeitsbereich "Merchandising durchsuchen".'
exl-id: a52839fb-2264-4443-83c3-9eaa2ccb6996
source-git-commit: 52be82fa080474d6df81fd16d1655a421771e5e2
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# Search Merchandising Workspace

Die *Merchandising durchsuchen* Der Arbeitsbereich listet die aktuelle Auswahl an Regeln und deren Status auf und bietet Zugriff auf Tools, die Sie zum Erstellen und Verwalten von Regeln benötigen. Im Arbeitsbereich haben Sie folgende Möglichkeiten:

* Nach Regeln suchen
* Anzeigen von Regeldetails
* Aktivieren/Deaktivieren von Regeln
* Regeln löschen
* Zugriff auf den Regeleditor

![Search Merchandising Workspace](assets/rules-workspace.png)

## Festlegen des Umfangs

Wenn Ihre Adobe Commerce-Installation mehrere Store-Ansichten enthält, legen Sie **Anwendungsbereich** der [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) wo Ihre Regeln gelten.

## Spalten ein-/ausblenden

1. Klicken Sie oben rechts auf **Einblenden/Ausblenden** ![Spaltenauswahl](assets/btn-show-hide-columns.png) Spalten.
Die sichtbaren Spalten haben ein blaues Häkchen im Menü &quot;Optionen&quot;. Der Regelname ist die einzige Spalte, die nicht ausgeblendet werden kann.

1. Führen Sie im Menü einen der folgenden Schritte aus:

   * Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   * Um eine sichtbare Spalte auszublenden, klicken Sie auf einen beliebigen Spaltennamen mit einem Häkchen.

## Regeln nach Status filtern

1. Wenn Ihr Store viele Regeln enthält, können Sie die Regeln nach Status filtern, um die Liste zu verkürzen. Standardmäßig werden in der Liste Regeln alle Regeln angezeigt.

1. Um nur Regeln mit einer bestimmten Statuseinstellung aufzulisten, legen Sie **Status** auf einen der folgenden Werte zu:

   * Alle
   * Aktiv
   * Inaaktiv
   * Geplant

## Suchen nach Suchregeln nach Namen

Beginnen Sie mit der Eingabe des Regelnamens oder eines beliebigen Wortes im Regelnamen.
Die Suche findet die entsprechenden Regeln während der Eingabe. Die Zeichenfolge der übereinstimmenden Zeichen wird im Namen jeder gefundenen Regel hervorgehoben.

![Regeln - nach Namen suchen](assets/rules-workspace-search-name.png)

## Details anzeigen

Im Detailbereich werden der Regelname, der Status, die Bedingungen und Ereignisse, das Start- und Enddatum, die Beschreibung und das Datum der letzten Bearbeitung angezeigt. Regeln können im Detailbereich aktiviert, bearbeitet und gelöscht werden.

1. Im *Merchandising durchsuchen* Arbeitsbereich die Regel im Raster suchen, das Sie anzeigen möchten, und auf **Mehr** (...).
1. Klicks **Details anzeigen**.
Im Bereich Details anzeigen können Sie Folgendes tun:

   * Regel bearbeiten
   * Regel löschen
   * Regel aktivieren/deaktivieren

1. So schließen Sie die *Details anzeigen* Bereich, klicken Sie **Schließen** (X) in der oberen rechten Ecke.

   ![Regel - Details](assets/rules-workspace-details.png)

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|--- |--- |
| Name | Der Name der Regel. |
| Zuletzt aktualisiert | Das Datum der letzten Aktualisierung der Regel. |
| Startdatum | Das Startdatum einer geplanten Regel. |
| Enddatum | Das Enddatum einer geplanten Regel. |
| Status | Der farbkodierte Status gibt den aktuellen Status der Regel an. Verwenden Sie das Steuerelement Status oberhalb des Rasters, um Regeln nach Status zu filtern. Werte:<br />Gesamter Status - Zeigt alle Regeln unabhängig vom Status an.<br />Aktiv (blau) - Zeigt nur aktive Regeln an.<br />Geplant (orange) - zeigt nur geplante Regeln an.<br />Inaktiv (grau) - zeigt nur inaktive Regeln an. |

## Steuerelemente

| Kontrolle | Beschreibung |
|--- |--- |
| Regel hinzufügen | Öffnet die [Regeleditor](rules-add.md). |
| Status | Filtert die Liste der Regeln nach Status. Optionen: Alle, aktiv, inaktiv, Geplant |
| ![Spaltenauswahl](assets/btn-show-hide-columns.png) | Gibt die im Raster sichtbaren Spalten an. Optionen: Zuletzt aktualisiert, Startdatum, Enddatum, Status |
| Suche | Sucht nach einer Regel mit vollständigem Namen oder teilweiser Übereinstimmung. |
| ![Mehr Auswahl](assets/btn-more.png) | Zeigt ein Menü mit weiteren Aktionen an, die auf die ausgewählte Regel angewendet werden können. Optionen: Bearbeiten, Details anzeigen, Löschen |

## Regeldetails

| Feld | Beschreibung |
|--- |--- |
| Status | Der aktuelle Status der Regel. |
| Bedingungen | Die Suchabfrage, die die mit der Regel verknüpften Bedingungen beschreibt. |
| Startdatum | Das Datum, an dem die Regel in Kraft tritt, falls geplant. |
| Enddatum | Das Datum, an dem die Regel abläuft, falls geplant. |
| Beschreibung | Eine kurze Beschreibung der Regel. |
| Letzte Aktualisierung | Datum und Uhrzeit der letzten Aktualisierung der Regel. |
| Aktiviert | Ein Steuerelement, das den Status der Regel ändert. Optionen: aktiviert/deaktiviert |
