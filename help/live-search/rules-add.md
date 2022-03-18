---
title: Regeln hinzufügen
description: Erfahren Sie, wie Sie Live-Suchregeln erstellen.
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '1283'
ht-degree: 0%

---

# Regeln hinzufügen

Um eine Regel zu erstellen, verwenden Sie zunächst den Regeleditor, um die Bedingungen im Abfragetext des Käufers zu definieren, die die zugehörigen Ereignisse Trigger haben. Schließen Sie dann die Regeldetails ab, testen Sie die Ergebnisse und veröffentlichen Sie die Regel.

## Schritt 1: Regel hinzufügen

1. Navigieren Sie im Admin zu **Marketing** > SEO &amp; Suche > **Live Search**.
1. Legen Sie die **Anwendungsbereich** zur Identifizierung der [Store-Ansicht](https://docs.magento.com/user-guide/configuration/scope.html) wo die Regel gilt.
1. Klicken Sie auf **Regeln** Registerkarte.
1. Klicken **Regel hinzufügen** , um den Regeleditor zu starten.

   ![Arbeitsbereich für Regeln](assets/rules-workspace-add-rule.png)

## Schritt 2: Bedingung(en) beschreiben

Bedingungen sind die Anforderungen zum Trigger eines Ereignisses. Eine Regel kann bis zu zehn Bedingungen und fünfundzwanzig Ereignisse haben.

![Regel - Regel erstellen](assets/rules-add-workspace.png)

### Einzelbedingung

1. under *Regel erstellen*, wählen Sie die **Bedingung** einzuhalten und den Anweisungen zu folgen, um die Anweisung auszufüllen.

   * Suchabfrage enthält - Geben Sie die Textzeichenfolge ein, die in der Abfrage des Käufers enthalten sein muss. Die Einstellung Übereinstimmung bestimmt, inwieweit die Abfrage des Käufers mit dem Katalog übereinstimmt. Optionen:<br /> Beliebig : Jeder Teil des Abfragetextes des Käufers kann mit der Bedingung übereinstimmen.<br />Alle - Die gesamte Abfrage des Käufers muss mit der Bedingung übereinstimmen.
   * Suchabfrage lautet - Geben Sie eine Textzeichenfolge ein, die genau mit der Abfrage des Käufers übereinstimmt. Beispiel: &quot;Yoga Hose&quot;. Regeln mit `Search query is` und Übereinstimmung `All` kann nur eine Bedingung aufweisen.
   * Suchabfrage beginnt mit - Geben Sie ein Zeichen oder eine Textzeichenfolge ein, die am Anfang der Abfrage des Käufers stehen muss.
   * Suchabfrage endet mit - Geben Sie ein Zeichen oder eine Zeichenfolge von Text ein, der am Ende der Abfrage des Käufers stehen muss.

   Die Ergebnisse erscheinen unmittelbar in der *Regel testen* und werden nach Priorität nummeriert. Sie können die *Ergebnisse pro Zeile* oben rechts, um die Anzahl der Produkte in jeder Zeile zu ändern.

   ![Regel - einfach](assets/rule-simple-test.png)

1. Um andere Abfragen zu testen, ändern Sie den Abfragetext im *Regel testen* Suchfeld und drücken Sie **Rückgabe**.
Zunächst rendert der Testbereich die Abfrage über das Suchfeld Bedingungen . Jetzt wird jedoch die Abfrage aus der Testabfrage gerendert. Im Testbereich wird jeweils nur eine Abfrage gerendert.

   ![Regel - Aktualisierungstest](assets/rule-update-test.png)

1. Wenn Ihnen das Ergebnis gefällt, aktualisieren Sie den Text im *Bedingungen* Suchfeld. Klicken Sie dann auf eine beliebige Stelle auf der Seite, um die Ergebnisse im Testbereich zu aktualisieren.
1. Um eine einfache Regel mit einer Bedingung zu erstellen, gehen Sie zu Schritt 3: [Ereignis(e) hinzufügen](#events).

### Mehrere Bedingungen

1. Um eine Regel mit mehreren Bedingungen zu erstellen, klicken Sie auf **Bedingung hinzufügen**.
Eine Regel kann bis zu 10 Bedingungen enthalten. Der logische Operator, der zwei Bedingungen verbindet, basiert auf dem aktuellen *Übereinstimmung* -Einstellung. Standardmäßig *Übereinstimmung* is `All` und der logische Operator `AND`.

   ![Regeln - Suchabfrage enthält](assets/rules-search-query-contains-and.png)

1. Wählen Sie die zweite Bedingung aus und geben Sie den gewünschten Abfragetext ein.

   ![Regelbedingungen](assets/rules-add-condition.png)

1. Um die Logik der Regel zu ändern, ändern Sie die **Übereinstimmung** -Einstellung, um zu bestimmen, wie eng die Suchkriterien des Käufers mit der Abfragebedingung übereinstimmen müssen. Satz **Übereinstimmung** auf einen der folgenden Werte:

   * Beliebig - (Standard) Alle logischen Operatoren in der Regel sind auf `OR` und die Ergebnisse werden im Testbereich angezeigt.
   * Alle - Alle logischen Operatoren in der Regel sind auf `AND` und die Ergebnisse werden im Testbereich angezeigt.

   Die *Übereinstimmung* bestimmt den logischen Operator, der zum Verknüpfen mehrerer Bedingungen verwendet wird. Ändern der *Übereinstimmung* Durch die Einstellung werden alle logischen Operatoren in der Regel geändert. Es ist nicht möglich, `AND` und `OR` in derselben Regel.
In diesem Beispiel gibt es zwei separate Abfragen, die nicht nach &quot;Yoga Hots&quot;suchen, sondern nach &quot;Yoga&quot;oder &quot;Hots&quot;. Diese Regel ist weniger spezifisch und wird häufiger im Storefront ausgelöst als die andere.

   ![Regeln - Übereinstimmung](assets/rules-match.png)

1. Um eine weitere Bedingung hinzuzufügen, klicken Sie auf **Bedingung hinzufügen** und wiederholen Sie den Vorgang.

## Schritt 3: Ereignis(e) hinzufügen

Ereignisse sind Aktionen, die die Suchergebnisse ändern, wenn die Bedingung(en) erfüllt ist. Eine einzelne Regel kann bis zu fünfundzwanzig Ereignisse umfassen.

1. under *Veranstaltungen*, wählen Sie die **Ereignis** , um zu erfolgen, wenn die damit verbundenen Bedingungen erfüllt sind.
Wählen Sie beispielsweise `Pin a product`. Geben Sie dann den Namen des Produkts ein, das Sie veröffentlichen möchten. Wenn Sie Hilfe benötigen, finden Sie den Namen im Testbereich.
Geben Sie dann die *Position* wo das eingeklemmte Produkt erscheinen soll. Das Produkt wird an die neue Position im Testbereich verschoben und mit einer *Angeheftet* Vorschau-Badge.

   ![Regeln - Übereinstimmung](assets/rule-event-pin-product.png)

1. Wählen Sie für mehrere Ereignisse alle anderen Ereignisse aus, die Trigger werden sollen, wenn die Bedingungen erfüllt sind.

   * Verstärken - Wählen Sie &quot;Verstärken&quot;. Geben Sie dann den Produktnamen oder die SKU ein, die bzw. die Sie in den Suchergebnissen weiter nach oben verschieben möchten. Im Testbereich verfügt jedes geboosterte Produkt über eine *Verstärkt* Vorschau-Badge.
   * Bury - Verschiebt eine SKU in den Suchergebnissen nach unten. Jede SKU ist mit einer *Vergraben* Vorschau-Badge im Testbereich.
   * Produkt fixieren - Geben Sie den Produktnamen oder die SKU ein. Wählen Sie dann die Position in den Suchergebnissen aus, an der das Produkt erscheinen soll. Das Produkt ist mit einer *Angeheftet* Vorschau-Badge im Testbereich.
   * Produkt ausblenden - Schließt eine SKU aus den Suchergebnissen aus.

## Schritt 4: Details ausfüllen

Die hier eingegebenen Informationen werden im [Regeldetails](rules-workspace.md) Bereich.

1. under *Details*, geben Sie einen **Name** für die Regel.
1. Kurzbeschreibung eingeben **Beschreibung** der Regel.
1. Geben Sie die **Startdatum** und **Enddatum** wann die Regel aktiv sein wird oder Sie die Daten aus dem Kalender auswählen.

   Um einen Datumsbereich auszuwählen, klicken Sie auf das erste Datum und ziehen Sie, um den Datumsbereich auszuwählen.

   ![Regel - Abgeschlossen](assets/rule-add-details.png)

## Schritt 5: Regel testen

1. Untersuchen Sie die Ergebnisse der Regel im Testbereich.
1. Wenn die Regel mehrere Abfragen enthält, testen Sie jede, die von der Regel betroffen sein könnte.

## Schritt 6: Speichern und veröffentlichen

Wenn Sie fertig sind, klicken Sie auf **Speichern und veröffentlichen**.
Die Regel wird der Liste im Arbeitsbereich &quot;Regeln&quot;hinzugefügt. Obwohl aktive Regeln sofort in Kraft treten, kann es bis zu 15 Minuten dauern, bis zwischengespeicherte Abfrageergebnisse in der Storefront aktualisiert werden.

## Feldbeschreibungen

### Bedingungen (if)

| Bedingung | Beschreibung |
|--- |--- |
| Suchabfrage enthält | Ein Zeichen oder eine Zeichenfolge von Text, der in der Abfrage des Käufers enthalten ist. Die Abfrage des Käufers muss nur mit einem einzelnen Zeichen übereinstimmen, um diese Bedingung zu erfüllen. |
| Suchabfrage ist | Ein Zeichen oder eine Textzeichenfolge, die genau mit der Abfrage des Käufers übereinstimmt. Bei Verwendung dieser Bedingung können keine komplexen Abfragen mit mehreren Bedingungen erstellt werden. |
| Suchabfrage beginnt mit | Die Abfrage des Käufers beginnt mit diesem Zeichen oder dieser Textzeichenfolge. |
| Suchabfrage endet mit | Die Abfrage des Käufers endet mit diesem Zeichen oder dieser Zeichenfolge. |

### Logische Operatoren

| Operator | Beschreibung |
|--- |--- |
| ODER | (Standard) Der logische Operator `OR` vergleicht zwei Bedingungen und erfüllt die Anforderungen zum Trigger eines Ereignisses, wenn mindestens eine Bedingung wahr ist. |
| UND | Logischer Operator `AND` Vergleicht zwei Bedingungen und erfüllt die Anforderungen zum Trigger eines Ereignisses, wenn beide Bedingungen erfüllt sind. |

### Übereinstimmungsoperatoren

| Operator | Beschreibung |
|--- |--- |
| Alle | Ändert alle logischen Operatoren in der Regel in `OR` und gibt den Satz übereinstimmender Produkte zurück. |
| Alle | Ändert alle logischen Operatoren in der Regel in `AND` und gibt den Satz übereinstimmender Produkte zurück. |

### Veranstaltungen

| Ereignis | Beschreibung |
|--- |--- |
| Verstärken | Verschiebt eine SKU oder einen Bereich von SKUs in den Suchergebnissen höher. Jede ist in den Testsuchergebnissen mit einem &quot;verstärkten&quot;Vorschauzeichen markiert. |
| Bury | Verschiebt eine SKU oder einen Bereich von SKUs in den Suchergebnissen nach unten. Jede ist in den Testsuchergebnissen mit einem &quot;begrabenen&quot;Vorschauabzeichen markiert. |
| Produkt fixieren | Hängt eine einzelne SKU an eine bestimmte Position in den Suchergebnissen an. Das Produkt ist in den Testsuchergebnissen mit einem &quot;fixierten&quot;Vorschauabzeichen markiert. |
| Produkt ausblenden | Schließt eine SKU oder einen Bereich von SKUs aus den Suchergebnissen aus. |

### Details

| Feld | Beschreibung |
|--- |--- |
| Name | Der Name der Regel. |
| Startdatum | Das Startdatum der Regel, falls geplant. |
| Enddatum | Das Enddatum der Regel, falls geplant. |
| Beschreibung | Eine kurze Beschreibung der Regel. |
