---
title: Arbeitsbereich
description: Erfahren Sie, wie Sie die Performance von Produktempfehlungen konfigurieren, verwalten und überwachen.
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Arbeitsbereich

Die [!DNL Product Recommendations] Arbeitsbereich zeigt eine Liste der zuvor konfigurierten Empfehlungen mit Metriken an, mit denen Sie den Erfolg jeder Empfehlung verfolgen können. Die Liste kann so konfiguriert werden, dass sie Metriken für den letzten Tag, die letzte Woche oder den letzten Monat berechnet. Sie können die Metriken verwenden, um praktische Einblicke darauf zu erhalten, wie häufig eine Empfehlungseinheit angezeigt oder angeklickt wird, oder um zu analysieren, wie gut Ihre Empfehlungen funktionieren.

![Recommendations Workspace](assets/workspace.png)
_Recommendations Workspace_

## Festlegen des Umfangs

Zunächst wird die [Umfang](https://docs.magento.com/user-guide/stores/websites-stores-views.html) aller Empfehlungseinstellungen auf `Default Store View`. Wenn Ihre Commerce-Installation mehrere Store-Ansichten enthält, legen Sie **Anwendungsbereich** der [Store-Ansicht](https://docs.magento.com/user-guide/configuration/scope.html) wo Ihre Empfehlungen gelten.

## Festlegen des Datumsbereichs von Metriken

1. Klicken Sie auf **Kalender** ![Kalenderauswahl](assets/icon-calendar.png) Kontrolle.

1. Wählen Sie eine der folgenden Optionen aus:

   - Letzte 24 Stunden
   - Letzte 7 Tage
   - Letzte 30 Tage

   Die berechneten Werte in den Metrikspalten ändern sich entsprechend dem aktuellen Datumsbereich.

## Show/hide columns

1. Klicken Sie oben links auf **Einblenden/Ausblenden** ![Spaltenauswahl](assets/icon-show-hide-columns.png) Spalten.

   Die sichtbaren Spalten haben ein blaues Häkchen.

1. In the menu, do either of the following:

   - Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   - To hide a visible column, click any column name with a check mark.

   Die Tabelle wird aktualisiert und enthält nur die ausgewählten Spalten.

   ![Recommendations workspace](assets/workspace-select-columns.png)
   _Spalten ein-/ausblenden_

## Einstellungen

Die Einstellungen bestimmen den SaaS-Datenraum, der die Recommendations-Verhaltensdaten bereitstellt.

- Wählen Sie einen anderen SaaS-Datenraum aus, um zu ändern, woher Recommendations-Verhaltensdaten stammen.

- Um einen neuen SaaS-Datenraum zu konfigurieren, klicken Sie auf **Konfiguration bearbeiten**. Weitere Informationen finden Sie unter [Einstellungen](settings.md).

![Recommendations-Einstellungen](assets/settings.png)
_Recommendations-Einstellungen_

## Details anzeigen

1. In the table, click the recommendation that you want to examine.

   ![Recommendations workspace](assets/recommendation-detail.png)
   _Details zur Homepage-Konversionsrate_

1. Um den Status der Empfehlung zu ändern, klicken Sie auf **Aktivieren** oder **Deaktivieren**.

## Edit recommendation

From the recommendation details page, click **Edit**. Weitere Informationen finden Sie unter [Recommendations bearbeiten](edit.md).

## Empfehlung erstellen

From the recommendation details page, click **Create**. To learn more, go to [Create Recommendations](create.md).

## Workspace-Steuerelemente

| Kontrolle | Beschreibung |
|---|---|
| ![Kalenderauswahl](assets/icon-calendar.png) | Determines the range of time that is used for metrics calculations. Options: 24 hours / 7 days / 30 days |
| ![Spaltenauswahl](assets/icon-show-hide-columns.png) | Bestimmt die Spalten, die im [!DNL Product Recommendations] Tabelle. |
| Einstellungen | Determines the SaaS data space where recommendation-behavioral data is fetched, and also enables visual similarity recommendation type. |
| Empfehlung erstellen | Öffnet die [Neue Empfehlung erstellen](create.md) Seite. |

## Column Descriptions

| Column | Beschreibung |
|---|---|
| Name | Der Name der Empfehlung. |
| Seite | Die Seite, auf der die Empfehlung angezeigt wird. |
| Typ | Der Empfehlungstyp. |
| Status | Der Empfehlungsstatus. Optionen: Inaktiv/Aktiv/Entwurf |
| Erstellt | Das Datum, an dem die Empfehlung erstellt wurde. |
| Zuletzt bearbeitet | Das Datum, an dem die Empfehlung zuletzt bearbeitet wurde. |
| Impressionen | Die Häufigkeit, mit der eine Empfehlungseinheit auf einer Seite geladen und gerendert wird. A recommendation unit that is below the fold of the browser&#39;s viewport is rendered on the page, but not viewed by the shopper. In this case, the rendered unit is counted as an impression, but a view is counted only if the user scrolls the unit into view. |
| vImpressions | (Sichtbare Impressionen) Die Anzahl der Empfehlungseinheiten, die mindestens eine Ansicht registrieren. |
| Ansichten | Die Anzahl der Empfehlungseinheiten, die im Viewport des Browsers des Käufers angezeigt werden. This event can fire multiple times on a page. |
| Klicks | Die Summe der Klicks eines Käufers auf einen Artikel in der Empfehlungseinheit und der Anzahl der Klicks des Käufers auf die **Zum Warenkorb hinzufügen** Schaltfläche in der Empfehlungseinheit |
| Umsatz | The revenue driven by the recommendation for the current time range. |
| LT Umsatz | (Lebensdauerumsatz) Der durch eine Empfehlung generierte Lebenszeitumsatz. |
| Sichtbarkeit | Der Prozentsatz der Empfehlungseinheiten, die sich für die Ansicht registrieren. |
| Ctr | (Registrierter Klick-Prozentsatz) Der Prozentsatz der Einheitenimpressionen für die Empfehlung, die einen Klick registriert. |
| vCtr | (Sichtbarer registrierter Klick-Prozentsatz) Der Prozentsatz sichtbarer Impressionen für die Empfehlungseinheit, die einen Klick registriert. |
