---
title: "Regeln"
description: "[!DNL Live Search] Regeln kombinieren Logik mit Aktionen, um das Einkaufserlebnis zu gestalten."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 7307702a62a6b2c3e6c6083a59f2ac3587b0985e
workflow-type: tm+mt
source-wordcount: '588'
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

## Rangfolge mit mehreren Regeln

Es wird immer nur eine Regel auf einen Suchbegriff angewendet.
Wenn festgestellt wird, dass mehrere Regeln auf einen Suchbegriff anwendbar sind, werden alle diese Regeln angewendet. Bei Kollision zwischen zwei Regeln:`rule 1` das die SKU1 erhöht, aber `rule 2` blendet dieselbe SKU aus - dann die zuletzt angewendete Regel (`rule 2`) hat Vorrang.

* Regeln werden nach dem Zeitstempel &quot;Zuletzt geändert&quot;geordnet. Die zuletzt geänderte Regel wird zuerst angewendet und ältere Regeln danach in der Zeitstempelreihenfolge.
* Die `query is` -Bedingung Vorrang vor anderen Bedingungen hat. Wenn eine neuere Regel eine `query contains` -Bedingung, aber eine ältere Regel hat eine `query is` -Bedingung, die `query is` -Regel angewendet wird.

### Storefront-Anforderungen

Wenn eine aktive Regel eine `query is` -Bedingung mit dem Suchbegriff übereinstimmt, wird er angewendet. Wenn mehrere übereinstimmende Regeln mit einer `query is` -Bedingung, wird die zuletzt aktualisierte aktive Regel angewendet.
Andernfalls wird die zuletzt aktualisierte aktive Regel angewendet.

### Vorschau von Anforderungen

Die in der Admin-Konsole gestellten Anforderungen funktionieren etwas anders. Bei der Vorschau in der Admin-Konsole werden alle Regeln angewendet, einschließlich der abgelaufenen und geplanten.

* Wenn eine Regel in der Vorschau eine `query is` -Bedingung, wird sie angewendet.
* Wenn die Vorschau einer Regel keine `query is` und einer nachfolgenden aktiven, übereinstimmenden Regel mit einer `query is` -Bedingung gefunden wird, wird die `query is` -Regel angewendet wird.
* Wenn die Vorschau einer Regel keine `query is` und keine andere Regel mit einer `query is` gefunden wird, wird die in der Vorschau angezeigte Regel angewendet.

## Kategorieregeln und Kategorieproduktzuweisungen

[!DNL Live Search] ermöglicht Ihnen, nach Kategorien zu filtern.
In Adobe Commerce können Sie jedoch eine virtuelle Kategorie mit [Kategorieproduktzuweisungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Dieser Kategorietyp wird zur Laufzeit erstellt und existiert nicht in der Kategoriedatenbank. Daher [!DNL Live Search] kann diesen Kategorietyp nicht lesen oder verwenden.
