---
title: Arbeitsbereich
description: Erfahren Sie, wie Sie die Performance von Produktempfehlungen konfigurieren, verwalten und überwachen.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
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

## Spalten ein-/ausblenden

1. Klicken Sie oben links auf **Einblenden/Ausblenden** ![Spaltenauswahl](assets/icon-show-hide-columns.png) Spalten.

   Die sichtbaren Spalten haben ein blaues Häkchen.

1. Führen Sie im Menü einen der folgenden Schritte aus:

   - Um eine ausgeblendete Spalte anzuzeigen, klicken Sie auf einen beliebigen Spaltennamen ohne Häkchen.
   - Um eine sichtbare Spalte auszublenden, klicken Sie auf einen beliebigen Spaltennamen mit einem Häkchen.

   Die Tabelle wird aktualisiert und enthält nur die ausgewählten Spalten.

   ![Recommendations Workspace](assets/workspace-select-columns.png)
   _Spalten ein-/ausblenden_

## Einstellungen

Die Einstellungen bestimmen den SaaS-Datenraum, der die Recommendations-Verhaltensdaten bereitstellt.

- Wählen Sie einen anderen SaaS-Datenraum aus, um zu ändern, woher Recommendations-Verhaltensdaten stammen.

- Um einen neuen SaaS-Datenraum zu konfigurieren, klicken Sie auf **Konfiguration bearbeiten**. Weitere Informationen finden Sie unter [Einstellungen](settings.md).

![Recommendations-Einstellungen](assets/settings.png)
_Recommendations-Einstellungen_

## Details anzeigen

1. Klicken Sie in der Tabelle auf die Empfehlung, die Sie untersuchen möchten.

   ![Recommendations Workspace](assets/recommendation-detail.png)
   _Details zur Homepage-Konversionsrate_

1. Um den Status der Empfehlung zu ändern, klicken Sie auf **Aktivieren** oder **Deaktivieren**.

## Empfehlung bearbeiten

Klicken Sie auf der Seite mit den Empfehlungsdetails auf **Bearbeiten**. Weitere Informationen finden Sie unter [Recommendations bearbeiten](edit.md).

## Empfehlung erstellen

Klicken Sie auf der Seite mit den Empfehlungsdetails auf **Erstellen**. Weitere Informationen finden Sie unter [Recommendations erstellen](create.md).

## Workspace-Steuerelemente

| Kontrolle | Beschreibung |
|---|---|
| ![Kalenderauswahl](assets/icon-calendar.png) | Bestimmt den Zeitraum, der für Metrikberechnungen verwendet wird. Optionen: 24 Stunden / 7 Tage / 30 Tage |
| ![Spaltenauswahl](assets/icon-show-hide-columns.png) | Bestimmt die Spalten, die im [!DNL Product Recommendations] Tabelle. |
| Einstellungen | Bestimmt den SaaS-Datenraum, aus dem Recommendations-Verhaltensdaten abgerufen werden, und ermöglicht auch den Empfehlungstyp für visuelle Ähnlichkeit. |
| Empfehlung erstellen | Öffnet die [Neue Empfehlung erstellen](create.md) Seite. |

## Spaltenbeschreibungen

| Spalte | Beschreibung |
|---|---|
| Name | Der Name der Empfehlung. |
| Seite | Die Seite, auf der die Empfehlung angezeigt wird. |
| Typ | Der Empfehlungstyp. |
| Status | Der Empfehlungsstatus. Optionen: Inaktiv/Aktiv/Entwurf |
| Erstellt | Das Datum, an dem die Empfehlung erstellt wurde. |
| Zuletzt bearbeitet | Das Datum, an dem die Empfehlung zuletzt bearbeitet wurde. |
| Impressionen | Die Häufigkeit, mit der eine Empfehlungseinheit auf einer Seite geladen und gerendert wird. Eine Empfehlungseinheit, die sich unterhalb des Darstellungsbereichs des Browsers befindet, wird auf der Seite gerendert, aber nicht vom Käufer angezeigt. In diesem Fall wird die gerenderte Einheit als Impression gezählt, eine Ansicht wird jedoch nur gezählt, wenn der Benutzer die Einheit in die Ansicht scrollt. |
| vImpressions | (Sichtbare Impressionen) Die Anzahl der Empfehlungseinheiten, die mindestens eine Ansicht registrieren. |
| Ansichten | Die Anzahl der Empfehlungseinheiten, die im Viewport des Browsers des Käufers angezeigt werden. Dieses Ereignis kann mehrmals auf einer Seite ausgelöst werden. |
| Klicks | Die Summe der Klicks eines Käufers auf einen Artikel in der Empfehlungseinheit und der Anzahl der Klicks des Käufers auf die **Zum Warenkorb hinzufügen** Schaltfläche in der Empfehlungseinheit |
| Umsatz | Der Umsatz, der durch die Empfehlung für den aktuellen Zeitraum bedingt ist. |
| LT Umsatz | (Lebensdauerumsatz) Der durch eine Empfehlung generierte Lebenszeitumsatz. |
| Sichtbarkeit | Der Prozentsatz der Empfehlungseinheiten, die sich für die Ansicht registrieren. |
| Ctr | (Registrierter Klick-Prozentsatz) Der Prozentsatz der Einheitenimpressionen für die Empfehlung, die einen Klick registriert. |
| vCtr | (Sichtbarer registrierter Klick-Prozentsatz) Der Prozentsatz sichtbarer Impressionen für die Empfehlungseinheit, die einen Klick registriert. |
