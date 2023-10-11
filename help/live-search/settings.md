---
title: "[!DNL Live Search] Einstellungen"
description: "Konfigurieren Sie die Einstellungen für [!DNL Live Search] Dienst."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 5e3cdae0e7362b921c51dc6edb12f4b58ffeb31e
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Einstellungen

Verwenden Sie die *Einstellungen* um die Preisfacettenbereiche und -intervalle sowie die Standardsprache für den Index zu konfigurieren.

Preisfacetten geben die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte auf sie an.

Die Spracheinstellung gibt die [!DNL Live Search] Dienst, der beim Schreiben des Index erwartet werden soll.

![Einstellungen](assets/settings.png)

## Preisfacetten

Sie können die Anzahl der Preisbereichsgruppen und die Verteilung der Preiswerte auf diese Gruppen festlegen. Jeder Preisbereich überschneidet die vorherige Gruppe um eins. Beispielsweise werden für fünf Gruppen mit einem Intervall von 20 die folgenden Preisbereiche erstellt: 0-20, 20-40, 40-60, 60-80 und >80. Wenn nicht genügend Produkte im Katalog vorhanden sind, um alle definierten Bereiche auszufüllen, wird die Anzeige der verfügbaren Gruppen entsprechend angepasst. Beispiel: 0-20, 60-80, >80.

1. Navigieren Sie im Admin zu **Marketing** > *SEO und Suche* > **[!DNL Live Search]**.
1. Im **Einstellungen** Registerkarte unter *Preisfacetten* führen Sie folgende Schritte aus:
   * Geben Sie die **Anzahl der Auswahlen**, oder Preisgruppierungen, die verfügbar sein sollen. Es können bis zu 50 Preisgruppierungen definiert werden.
   * Geben Sie die **Intervallwert** oder Preisbereich für jede Gruppe. Der Höchstwert beträgt 10.000.
1. Klicks **Speichern**.

   Es dauert etwa 15 Minuten, bis die aktualisierten Einstellungen in der Storefront verfügbar sind.

### Feldbeschreibungen

| Feld | Beschreibung |
|--- |--- |
| Anzahl der Auswahlen | Gibt die Anzahl der Preisbereichsgruppen an, die als Suchfilter in der Storefront verwendet werden können. Standardwert: 8, Maximum value: 50 |
| Intervallwert | Gibt das Preisbereichsintervall für jede Gruppe an. Beispielsweise werden bei fünf Auswahlen mit einem Intervallwert von 20 fünf Gruppierungen von 0-20, 20-40, 40-60, 60-80 und >80 erstellt. Standardwert: 5, Maximum value: 10.000 |

## Sprache

Die Spracheinstellung gibt Folgendes an: [!DNL Live Search] welche Sprache zu erwarten ist, wenn der Katalog gelesen und der Index geschrieben wird.

Sprachen haben unterschiedliche Regeln für die Grammatik: wie Wörter getrennt werden, Verb-Sätze und Wortformen, zum Beispiel.
Die Einstellung Sprache stellt sicher, dass der richtige Regelsatz auf den Indizierungsmechanismus angewendet wird.

Legen Sie die Einstellung Sprache auf die primäre Sprache des Katalogs fest. Wenn Sie die Sprache des Index ändern, kann es je nach Größe und Komplexität des Katalogs zwischen 5 und 60 Minuten dauern, bis die Änderung an der Storefront berücksichtigt wird.

| Sprache | Code |
|----|----|
| Arabisch | ar |
| Armenisch | hy |
| Baskisch | eu |
| Bengalisch | bn |
| Brasilianisch | pt-br |
| bulgarisch | bg |
| Katalan | ca |
| Chinesisch (vereinfacht) | zh-cn |
| Chinesisch (traditionell) | zh-tw |
| tschechisch | cs |
| dänisch | da |
| holländisch | nl |
| englisch | en |
| estnisch | et |
| finnisch | fi |
| französisch | fr |
| Galizisch | gl |
| deutsch | de |
| griechisch | el |
| Hindi | hi |
| ungarisch | hu |
| Indonesisch | id |
| irisch | ga |
| italienisch | it |
| Japanisch | ja |
| Koreanisch | ko |
| lettisch | lv |
| litauisch | lt |
| norwegisch | no |
| Persisch | fa |
| portugiesisch | pt |
| rumänisch | ro |
| Russisch | ru |
| Sorani | ku |
| spanisch | es |
| schwedisch | sv |
| türkisch | tr |
| Thailändisch | th |
