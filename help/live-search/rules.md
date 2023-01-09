---
title: "Regeln"
description: "[!DNL Live Search] Regeln kombinieren Logik mit Aktionen, um das Einkaufserlebnis zu gestalten."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 941fdc25f93679593cb3c5db0d29d7a561fcce58
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Regeln

[!DNL Live Search] -Regeln kombinieren Logik mit Aktionen, um das Sucherlebnis eines Käufers in Ihrem Store zu gestalten. Sie können Regeln verwenden, um Produkte zu steigern, zu begraben, anzuheften oder auszublenden, um Suchergebnisse in Echtzeit zu kalibrieren, um Ihre Geschäftsziele zu unterstützen.

Jede Regel umfasst drei Hauptkomponenten:

* Bedingungen - Die Bedingungen, unter denen eine Aktion Trigger wird.
* Ereignisse - Die Aktionen, die ausgeführt werden, wenn die Bedingungen erfüllt sind.
* Details - Der Name der Regel sowie der optionale Zeitrahmen und die Beschreibung.

Sie können mehrere Bedingungen und Aktionen kombinieren und eine Regel so planen, dass sie für einen bestimmten Zeitraum aktiv ist.

## Voraussetzungen

Eine einfache Regel kann eine einzelne Bedingung und ein einzelnes Ereignis enthalten, während eine komplexe Regel bis zu zehn Bedingungen haben kann, die bis zu 25 Ereignisse Trigger.
Regeln können Folgendes enthalten:

* Bis zu zehn Bedingungen
* Bis zu 25 Ereignisse

Der Abfragetext kann Folgendes enthalten:

* Alphanumerische Zeichen (Buchstaben und Zahlen)
* Groß- oder Kleinbuchstaben. Groß-/Kleinschreibung wird ignoriert.

## Logische Operatoren

Logische Operatoren `AND` und `OR` zwei Bedingungen verbinden und unterschiedliche Ergebnisse zurückgeben. Alle logischen Operatoren, die in einer Regel mit mehreren Bedingungen verwendet werden, sind identisch. Es ist nicht möglich, beide `AND` und `OR` in derselben Regel.

### Übereinstimmungsoperatoren

Die Match-Operatoren `All` und `Any` den logischen Operator bestimmen, der zum Verbinden mehrerer Bedingungen in der Regel verwendet wird und zum Ändern des vorhandenen Operators verwendet werden kann.

* `All` - Verwendet die `AND` logischen Operators, um mehrere Bedingungen zu verknüpfen. Eine Regel, die die `All` Der Übereinstimmungsoperator kann nur eine haben `Search query is` Bedingung.
* `Any` - Verwendet die `OR` logischen Operators, um mehrere Bedingungen zu verknüpfen.

Beim Erstellen einer komplexen Regel kann es hilfreich sein, diese mit einem Einzug zu schreiben, um die Bedingungen, verknüpften Ereignisse sowie Produktnamen oder SKUs zu beschreiben, die zum Zurückgeben der gewünschten Ergebnisse erforderlich sind. Erstellen Sie dann die Regel und testen Sie das Ergebnis.
