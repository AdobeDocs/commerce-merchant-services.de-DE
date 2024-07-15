---
title: "Regeln hinzufügen"
description: "Erfahren Sie, wie Sie Merchandising-Suchregeln erstellen."
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 52be82fa080474d6df81fd16d1655a421771e5e2
workflow-type: tm+mt
source-wordcount: '1536'
ht-degree: 0%

---

# Regeln hinzufügen

Um eine Regel zu erstellen, verwenden Sie zunächst den Regeleditor, um die Bedingungen im Abfragetext des Käufers zu definieren, unter denen die zugehörigen Ereignisse Trigger werden. Schließen Sie dann die Regeldetails ab, testen Sie die Ergebnisse und veröffentlichen Sie die Regel.

## Regel hinzufügen

1. Wechseln Sie im Admin zu **Marketing** > SEO &amp; Suche > **[!DNL Live Search]**.
1. Legen Sie den **Umfang** fest, um die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) zu identifizieren, in der die Regel gilt.
1. Klicken Sie auf den Arbeitsbereich **Merchandising durchsuchen** .
1. Klicken Sie auf **Regel hinzufügen** , um den Regeleditor zu starten.

## Regeltyp

In einer Suchabfrage definieren Sie einen bestimmten Suchbegriff, Bedingungen und Rangtypen.

Es kann eine Standardregel festgelegt werden, die auf alle Abfragen angewendet wird, es sei denn, eine spezifischere Suchabfrage ist definiert. Es kann nur eine Standardregel festgelegt werden, die keine Bedingungen enthalten darf. Wenn Sie &quot;Standard&quot;auswählen, wird die Benutzeroberfläche &quot;Bedingungen&quot;nicht angezeigt.
Wählen Sie den standardmäßigen Rangtyp Intelligent und alle manuellen Ranglisten aus, die auf alle Standardsuchvorgänge angewendet werden sollen. Manuelle Rankings werden immer angewendet.

## Bedingungen

Bedingungen sind die Voraussetzungen für den Trigger eines Ereignisses. Eine Regel kann bis zu zehn Bedingungen und 25 Ereignisse enthalten. Eine Standardregel kann keine Bedingungen enthalten.

![Regel - Regel erstellen](assets/rules-add-workspace.png)

>[!NOTE]
>
>Derzeit ist es nicht möglich, Regeln auf eine bestimmte Kundengruppe auszurichten.

### Einzelbedingung

1. Wählen Sie unter *Regel erstellen* die zu erfüllende **Bedingung** aus und befolgen Sie die Anweisungen, um die Anweisung abzuschließen.

   * Suchabfrage enthält - Geben Sie die Textzeichenfolge ein, die in der Abfrage des Käufers enthalten sein muss. Die Einstellung Übereinstimmung bestimmt, inwieweit die Abfrage des Käufers mit dem Katalog übereinstimmt. Optionen:<br /> Beliebig - Jeder Teil des Abfragetextes des Käufers kann mit der Bedingung übereinstimmen.<br />Alle - Die gesamte Abfrage des Käufers muss mit der Bedingung übereinstimmen.
   * Suchabfrage lautet - Geben Sie eine Textzeichenfolge ein, die genau mit der Abfrage des Käufers übereinstimmt. Beispiel: &quot;Yoga pants&quot;. Regeln mit `Search query is` und Übereinstimmung `All` können nur eine Bedingung aufweisen.
   * Suchabfrage beginnt mit - Geben Sie ein Zeichen oder eine Textzeichenfolge ein, die am Anfang der Abfrage des Käufers stehen muss.
   * Suchabfrage endet mit - Geben Sie ein Zeichen oder eine Zeichenfolge von Text ein, der am Ende der Abfrage des Käufers stehen muss.

   Die Ergebnisse werden sofort im Bereich *Regel testen* angezeigt und nach Priorität nummeriert. Sie können den Schieberegler *Ergebnisse pro Zeile* oben verwenden    , um die Anzahl der Produkte in jeder Zeile zu ändern.

   ![Regel - einfach](assets/rule-simple-test.png)

1. Um andere Abfragen zu testen, ändern Sie den Abfragetext im Suchfeld *Regel testen* und drücken Sie die Taste **Zurück**.
Zunächst rendert der Testbereich die Abfrage über das Suchfeld Bedingungen . Jetzt wird jedoch die Abfrage aus der Testabfrage gerendert. Im Testbereich wird jeweils nur eine Abfrage gerendert.
1. Wenn Ihnen das Ergebnis gefällt, aktualisieren Sie den Text im Suchfeld *Bedingungen* . Klicken Sie dann auf eine beliebige Stelle auf der Seite, um die Ergebnisse im Testbereich zu aktualisieren.
1. Um eine einfache Regel mit einer Bedingung zu erstellen, gehen Sie zu Schritt 3: [Ereignisse hinzufügen](#events).

### Mehrere Bedingungen

1. Um eine Regel mit mehreren Bedingungen zu erstellen, klicken Sie auf **Bedingung hinzufügen**.
Eine Regel kann bis zu zehn Bedingungen enthalten. Der logische Operator, der zwei Bedingungen verbindet, basiert auf der aktuellen Einstellung *Übereinstimmung* . Standardmäßig ist *Übereinstimmung* `All` und der logische Operator ist `AND`.

1. Wählen Sie die zweite Bedingung aus und geben Sie den gewünschten Abfragetext ein.

1. Um die Logik der Regel zu ändern, ändern Sie die Einstellung **Übereinstimmung** , um zu bestimmen, wie stark die Suchkriterien des Käufers mit der Abfragebedingung übereinstimmen müssen. Legen Sie **Übereinstimmung** auf einen der folgenden Werte fest:

   * Beliebig - (Standard) Alle logischen Operatoren in der Regel sind auf `OR` eingestellt und die Ergebnisse werden im Testbereich angezeigt.
   * Alle - Alle logischen Operatoren in der Regel sind auf `AND` festgelegt und die Ergebnisse werden im Testbereich angezeigt.

   Der Wert *Übereinstimmung* bestimmt den logischen Operator, der zum Verknüpfen mehrerer Bedingungen verwendet wird. Wenn Sie die Einstellung *Übereinstimmung* ändern, werden alle logischen Operatoren in der Regel geändert. Es ist nicht möglich, `AND` und `OR` in derselben Regel zu kombinieren.

   In diesem Beispiel gibt es zwei separate Abfragen, die nicht nach &quot;Yoga Hots&quot;suchen, sondern nach &quot;Yoga&quot;oder &quot;Hots&quot;. Diese Regel ist weniger spezifisch und wird häufiger in der Storefront ausgelöst als die andere.

   ![Regeln - Übereinstimmung](assets/rules-match.png)

1. Um eine weitere Bedingung hinzuzufügen, klicken Sie auf **Bedingung hinzufügen** und wiederholen Sie den Prozess.

## Intelligente Rangfolge

Das intelligente Ranking kombiniert Benutzerverhalten und Site-Statistiken, um das Produktranking zu bestimmen.
Store-Eigentümer können die folgenden Ranking-Strategien einrichten:

![Regeln - Übereinstimmung](assets/rules-ranking-type.png)

* Am häufigsten gekauft: Hiermit werden Produkte nach Gesamtkäufen pro SKU in den letzten sieben Tagen sortiert.
* Am häufigsten zum Warenkorb hinzugefügt - Dieser Wert wird in der Reihenfolge der gesamten &quot;Zum Warenkorb hinzufügen&quot;-Aktivitäten in den letzten 7 Tagen sortiert.
* Am häufigsten angezeigt: Berechnet meine Gesamtansichten pro SKU in den letzten 7 Tagen.
* Empfohlen für Sie - Verwendet den `viewed-viewed` -Datenpunkt - Käufer, die diese SKU angesehen haben, haben sich auch mit diesen anderen SKUs befasst
* Trends: Betrachtet die Seitenansichtsereignisse der letzten 72 Stunden für Hintergrundereignisse und 24 Stunden für Vordergrundereignisse
* Keine: Produkte werden nach Relevanz geordnet

1. Wählen Sie den Typ der Strategie für die Regel aus. Im Fenster Regel testen werden die erwarteten Ergebnisse angezeigt.

>[!NOTE]
>
>Apostrophe und Anführungszeichen in Abfragen können in einigen Sprachen zu kleineren Problemen mit Ranking und Relevanz führen.

## Manuelles Ranking

Bei der manuellen Rangordnung (früher als Ereignisse bezeichnet) handelt es sich um Aktionen, die die Suchergebnisse ändern, wenn definierte Bedingungen erfüllt sind. Eine einzelne Regel kann bis zu 25 Ereignisse enthalten.

* Verstärken - Verschiebt ein Produkt in den Suchergebnissen höher.
* Bury - Verschiebt eine SKU in den Suchergebnissen nach unten.
* Produkt fixieren - Das Produkt wird in der ausgewählten &quot;Position&quot;auf der Seite angezeigt.
* Produkt ausblenden - Schließt eine SKU aus den Suchergebnissen aus.

Am einfachsten können Sie ein Produkt durch Drag &amp; Drop anheften.

1. Klicken Sie auf ein Produkt und ziehen Sie es in den Bereich Test . Ziehen Sie es an die gewünschte Position. Die Felder Produkt und Option werden automatisch im Bereich Ereignisse ausgefüllt.

   ![Regeln - Übereinstimmung](assets/rule-event-pin-product.png)

Sie können auch auf das Pin-Symbol klicken, um ein Produkt an seiner aktuellen Position zu veröffentlichen. Verwenden Sie das Kontextmenü mit den Auslassungspunkten, um &quot;Nach oben pin&quot;oder &quot;Nach unten pinnen&quot;zu verwenden.

>[!NOTE]
>
>Sie können nur Produkte anheften, die in der Abfrage zurückgegeben werden.

Oder Ereignisse können manuell festgelegt werden:

1. Wählen Sie unter *Ereignisse* das **Ereignis** aus, das ausgeführt werden soll, wenn die zugehörigen Bedingungen erfüllt sind.

   Wählen Sie beispielsweise &quot;`Hide a product`&quot;. Geben Sie dann den Namen des Produkts ein, das Sie ausblenden möchten. Bei der Eingabe werden Produkte vorgeschlagen.

1. Wählen Sie für mehrere Ereignisse alle anderen Ereignisse aus, die bei Erfüllung von Bedingungen Trigger werden sollen.

## Zusätzliche Details

Die hier eingegebenen Informationen werden im Bereich [Regeldetails](rules-workspace.md) angezeigt.

1. Geben Sie unter *Details* einen **Namen** für die Regel ein. Alle Regelnamen müssen eindeutig sein.
1. Geben Sie eine kurze Beschreibung **Beschreibung** der Regel ein.
1. Geben Sie das **Startdatum** und das **Enddatum** ein, damit die Regel aktiv ist, oder wählen Sie die Daten aus dem Kalender aus.

   Um einen Datumsbereich auszuwählen, klicken Sie auf das erste Datum und ziehen Sie, um den Datumsbereich auszuwählen.

   ![Regel - Complete](assets/rule-add-details.png)

## Fertigstellen der Regel

1. Untersuchen Sie die Ergebnisse der Regel im Testbereich.
1. Wenn die Regel mehrere Abfragen enthält, testen Sie jede, die von der Regel betroffen sein könnte.
1. Klicken Sie nach Abschluss des Vorgangs auf **Speichern und veröffentlichen**.

   Die Regel wird der Liste im Arbeitsbereich *Regeln* hinzugefügt.

1. Obwohl aktive Regeln sofort in Kraft treten, müssen Sie möglicherweise bis zu 15 Minuten warten, bis die zwischengespeicherten Abfrageergebnisse im Storefront aktualisiert werden.

## Feldbeschreibungen

### Bedingungen (if)

| Bedingung | Beschreibung |
|--- |--- |
| Suchabfrage enthält | Ein Zeichen oder eine Zeichenfolge von Text, der in der Abfrage des Käufers enthalten ist. Die Abfrage des Käufers muss nur mit einem einzelnen Zeichen übereinstimmen, um diese Bedingung zu erfüllen. |
| Suchabfrage ist | Ein Zeichen oder eine Textzeichenfolge, die genau mit der Abfrage des Käufers übereinstimmt. Bei Verwendung dieser Bedingung können keine komplexen Abfragen mit mehreren Bedingungen erstellt werden. |
| Suchabfrage beginnt mit | Die Abfrage des Käufers beginnt mit diesem Zeichen oder dieser Textzeichenfolge. |
| Suchabfrage endet mit | Die Abfrage des Käufers endet mit diesem Zeichen oder dieser Zeichenfolge. |

### Logische Operatoren

| Benutzerin oder Benutzer | Beschreibung |
|--- |--- |
| ODER | (Standard) Der logische Operator `OR` vergleicht zwei Bedingungen und erfüllt die Anforderungen zum Trigger eines Ereignisses, wenn mindestens eine Bedingung wahr ist. |
| UND | Der logische Operator `AND` vergleicht zwei Bedingungen und erfüllt die Anforderungen zum Trigger eines Ereignisses, wenn beide Bedingungen erfüllt sind. |

### Übereinstimmungsoperatoren

| Benutzerin oder Benutzer | Beschreibung |
|--- |--- |
| Alle | Ändert alle logischen Operatoren in der Regel in `OR` und gibt den Satz der übereinstimmenden Produkte zurück. |
| Alle | Ändert alle logischen Operatoren in der Regel in `AND` und gibt den Satz der übereinstimmenden Produkte zurück. |

### Manuelles Ranking

| Ereignis | Beschreibung |
|--- |--- |
| Verstärken | Verschiebt eine SKU oder einen Bereich von SKUs in den Suchergebnissen höher. In den Testsuchergebnissen wird jedes mit einem &quot;verstärkten&quot;Vorschauzeichen markiert. |
| Bury | Verschiebt eine SKU oder einen Bereich von SKUs in den Suchergebnissen nach unten. Jede ist in den Testsuchergebnissen mit einem &quot;begrabenen&quot;Vorschauabzeichen markiert. |
| Produkt fixieren | Hängt eine einzelne SKU an eine bestimmte Position in den Suchergebnissen an. Das Produkt ist in den Testsuchergebnissen mit einem &quot;fixierten&quot;Vorschaukennzeichen markiert. |
| Produkt ausblenden | Schließt eine SKU oder einen SKU-Bereich aus den Suchergebnissen aus. |

### Details

| Feld | Beschreibung |
|--- |--- |
| Name | Der Name der Regel. Regelnamen müssen eindeutig sein. |
| Regeltyp | Standard oder Abfrage. Der Standardwert wird auf alle Regeln angewendet, es sei denn, es ist eine spezifischere Abfrageregel definiert. |
| Startdatum | Das Startdatum der Regel, falls geplant. |
| Enddatum | Das Enddatum der Regel, falls geplant. |
| Beschreibung | Eine kurze Beschreibung der Regel. |
