---
title: "Search Merchandising"
description: "[!DNL Live Search] Merchandising-Regeln kombinieren Logik mit Aktionen, um das Einkaufserlebnis zu gestalten."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 2b0ca3f5a68e75ef4b4e71ac7705b17534e16845
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Merchandising durchsuchen

Suchen-Merchandising bezieht sich auf einen Regelsatz, der Logik mit Aktionen kombiniert, um das Sucherlebnis eines Käufers in Ihrem Store zu gestalten. Sie können Merchandising-Regeln verwenden, um Produkte zu steigern, zu begraben, anzuheften oder auszublenden, um Suchergebnisse in Echtzeit zu kalibrieren, um Ihre Geschäftsziele zu unterstützen.

Jede Regel umfasst drei Hauptkomponenten:

* Bedingungen - Die Bedingungen, unter denen eine Aktion Trigger wird.
* Ereignisse - Die Aktionen, die ausgeführt werden, wenn die Bedingungen erfüllt sind.
* Details - Der Name der Regel sowie der optionale Zeitrahmen und die Beschreibung.

Sie können mehrere Bedingungen und Aktionen kombinieren und eine Regel so planen, dass sie für einen bestimmten Zeitraum aktiv ist. Sie können auch eine Standardregel festlegen, die auch dann angewendet wird, wenn kein Suchbegriff festgelegt ist.

## Voraussetzungen

Eine einfache Suchregel kann eine einzelne Bedingung und ein einzelnes Ereignis enthalten, während eine komplexe Regel bis zu zehn Bedingungen haben kann, die bis zu 25 Trigger umfassen.
Regeln können Folgendes enthalten:

* Bis zu zehn Bedingungen
* Bis zu 25 Ereignisse

Der Abfragetext kann Folgendes enthalten:

* Alphanumerische Zeichen (Buchstaben und Zahlen)
* Groß- oder Kleinbuchstaben. Groß-/Kleinschreibung wird ignoriert.

## Logische Operatoren

Die logischen Operatoren `AND` und `OR` verbinden zwei Bedingungen und geben unterschiedliche Ergebnisse zurück. Alle logischen Operatoren, die in einer Regel mit mehreren Bedingungen verwendet werden, sind identisch. Es ist nicht möglich, sowohl `AND` als auch `OR` in derselben Regel zu verwenden.

### Übereinstimmungsoperatoren

Die Übereinstimmungsoperatoren `All` und `Any` bestimmen den logischen Operator, der zum Verbinden mehrerer Bedingungen in der Regel verwendet wird, und können zum Ändern des vorhandenen Operators verwendet werden.

* `All` - Verwendet den logischen Operator `AND` , um mehrere Bedingungen miteinander zu verbinden. Eine Regel, die den Operator `All` Übereinstimmung verwendet, kann nur eine `Search query is` -Bedingung aufweisen.
* `Any` - Verwendet den logischen Operator `OR` , um mehrere Bedingungen miteinander zu verbinden.

Beim Erstellen einer komplexen Regel kann es hilfreich sein, diese mit einem Einzug zu schreiben, um die Bedingungen, verknüpften Ereignisse sowie Produktnamen oder SKUs zu beschreiben, die zum Zurückgeben der gewünschten Ergebnisse erforderlich sind. Erstellen Sie dann die Regel und testen Sie das Ergebnis.

## Standardregel

Sie können eine Standardregel festlegen, die angewendet wird, wenn kein Suchbegriff angegeben oder keine andere Suchregel angewendet werden kann. Wenn Sie die Standardregel auf &quot;Am häufigsten gekauft&quot;setzen, wird für alle Abfragen standardmäßig dieser Ranglistentyp verwendet, es sei denn, es wird durch einen spezifischeren Suchbegriff Super-Caching durchgeführt. Für die Standardregel kann kein Suchbegriff festgelegt werden.

## Rangfolge mit mehreren Regeln

Es wird immer nur eine Suchregel auf einen Suchbegriff angewendet.
Wenn festgestellt wird, dass mehrere Regeln auf einen Suchbegriff anwendbar sind, werden alle diese Regeln angewendet. Wenn es eine Kollision zwischen zwei Regeln -`rule 1`, die die SKU1 erhöhen, aber `rule 2` dieselbe SKU ausblendet -, hat die zuletzt angewendete Regel (`rule 2`) Vorrang.

* Regeln werden nach dem Zeitstempel &quot;Zuletzt geändert&quot;geordnet. Die zuletzt geänderte Regel wird zuerst angewendet und ältere Regeln danach in der Zeitstempelreihenfolge.
* Die `query is` -Bedingung hat Vorrang vor anderen Bedingungen. Wenn eine neuere Regel eine `query contains` -Bedingung enthält, eine ältere Regel jedoch eine `query is` -Bedingung aufweist, wird die `query is` -Regel angewendet.

### Storefront-Anforderungen

Wenn eine aktive Regel, die eine &quot;`query is`&quot;-Bedingung enthält, mit der Suchphrase übereinstimmt, wird sie angewendet. Wenn mehrere passende Regeln mit einer `query is` -Bedingung vorhanden sind, wird die zuletzt aktualisierte aktive Regel angewendet.
Andernfalls wird die zuletzt aktualisierte aktive Regel angewendet.

### Vorschau von Anforderungen

Die in der Admin-Konsole gestellten Anforderungen funktionieren etwas anders. Bei der Vorschau in der Admin-Konsole werden alle Regeln angewendet, einschließlich der abgelaufenen und geplanten.

* Wenn die in der Vorschau angezeigte Regel eine `query is` -Bedingung aufweist, wird sie angewendet.
* Wenn die in der Vorschau angezeigte Regel keine `query is` -Bedingung hat und eine nachfolgende aktive, passende Regel mit einer `query is` -Bedingung gefunden wird, wird die `query is` -Regel angewendet.
* Wenn die in der Vorschau angezeigte Regel keine `query is` -Bedingung hat und keine andere Regel mit der Bedingung `query is` gefunden wird, wird die in der Vorschau angezeigte Regel angewendet.

## KategorieMerchandising und Kategorieproduktzuweisungen

Mit [!DNL Live Search] können Sie nach Kategorien filtern. Weitere Informationen finden Sie unter [Kategorie-Merchandising](category-merch.md) .
In Adobe Commerce können Sie jedoch eine virtuelle Kategorie mit [Kategorieproduktzuweisungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html) erstellen. Dieser Kategorietyp wird zur Laufzeit erstellt und existiert nicht in der Kategoriedatenbank. Daher kann [!DNL Live Search] diesen Kategorietyp nicht lesen oder verwenden.
