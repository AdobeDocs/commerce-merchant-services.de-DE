---
title: "Regelkomponenten"
description: "Erfahren Sie mehr über [!DNL Live Search] Regelkomponenten und -operatoren."
exl-id: 4065aec3-a8d4-4d55-b939-16ad7b0f33ee
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Regelkomponenten

Eine Regel beschreibt die Bedingungen, die zum Trigger von Ereignissen erforderlich sind, die die Suchergebnisse ändern, die als Antwort auf die Abfrage eines Käufers zurückgegeben werden.

## Voraussetzungen

Eine einfache Regel kann eine einzelne Bedingung und ein einzelnes Ereignis enthalten, während eine komplexe Regel bis zu zehn Bedingungen haben kann, die bis zu 25 Ereignisse Trigger.
Regeln können Folgendes enthalten:

* Bis zu zehn Bedingungen
* Bis zu 25 Ereignisse

Der Abfragetext kann Folgendes enthalten:

* Alphanumerische Zeichen (Buchstaben und Zahlen)
* Großbuchstaben oder Kleinbuchstaben

## Logische Operatoren

Logische Operatoren `AND` und `OR` zwei Bedingungen verbinden und unterschiedliche Ergebnisse zurückgeben. Alle logischen Operatoren, die in einer Regel mit mehreren Bedingungen verwendet werden, sind identisch. Es ist nicht möglich, beide `AND` und `OR` in derselben Regel.

### Übereinstimmungsoperatoren

Die Match-Operatoren `All` und `Any` den logischen Operator bestimmen, der zum Verbinden mehrerer Bedingungen in der Regel verwendet wird und zum Ändern des vorhandenen Operators verwendet werden kann.

* `All` - Verwendet die `AND` logischen Operators, um mehrere Bedingungen zu verknüpfen. Eine Regel, die die `All` Der Übereinstimmungsoperator kann nur eine haben `Search query is` Bedingung.
* `Any` - Verwendet die `OR` logischen Operators, um mehrere Bedingungen zu verknüpfen.

Beim Erstellen einer komplexen Regel kann es hilfreich sein, diese mit einem Einzug zu schreiben, um die Bedingungen, verknüpften Ereignisse sowie Produktnamen oder SKUs zu beschreiben, die zum Zurückgeben der gewünschten Ergebnisse erforderlich sind. Erstellen Sie dann die Regel und testen Sie das Ergebnis.
