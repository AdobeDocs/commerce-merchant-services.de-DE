---
title: "[!DNL Live Search] Einstellungen"
description: "Konfigurieren Sie Preisfacettenbereiche und -intervalle für [!DNL Live Search] Facetten."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Einstellungen

Verwenden Sie die *Einstellungen* um die Preisfacettenbereiche und -intervalle zu konfigurieren, die als Suchfilter in der Storefront verfügbar sind. Preisfacetteneinstellungen sind statisch und nicht dynamisch und basieren nicht auf Suchergebnissen.

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte auf diese Gruppen festlegen. Jeder Preisbereich überschneidet die vorherige Gruppe um eins. Beispielsweise werden für fünf Gruppen mit einem Intervall von zwanzig die folgenden Preisbereiche erstellt: 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche auszufüllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

![Einstellungen](assets/settings.png)

## Preisfacettengruppierungen konfigurieren

1. Navigieren Sie im Admin zu **Marketing** > *SEO und Suche* > **[!DNL Live Search]**.
1. Im **Einstellungen** Registerkarte unter *Preisfacetten* führen Sie folgende Schritte aus:
   * Geben Sie die **Anzahl der Auswahlen**, oder Preisgruppierungen, die verfügbar sein sollen. Es können bis zu 50 Preisgruppierungen definiert werden.
   * Geben Sie die **Intervallwert** oder Preisbereich für jede Gruppe. Der Höchstwert beträgt 10.000.
1. Klicken **Speichern**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

## Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Maximum value: 50 |
| Intervallwert | Gibt das Preisbereichsintervall für jede Gruppe an. Beispielsweise werden bei fünf Auswahlen mit einem Intervallwert von 20 fünf Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80 erstellt. Standardwert: 5, Maximum value: 10.000 |
