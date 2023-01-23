---
title: Veranstaltungen
description: Erfahren Sie, welche Daten von den einzelnen Ereignissen erfasst werden.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 975854dbdae32e5e51bb57593cf122627d01571f
workflow-type: tm+mt
source-wordcount: '3141'
ht-degree: 0%

---

# Experience Platform Connector-Ereignisse

Im Folgenden werden die Commerce-Ereignisse aufgelistet, die bei der Installation der Experience Platform Connector-Erweiterung verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [sonstige Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt vom Adobe Experience Platform Web SDK.

## Storefront-Ereignisse

+++ Die Storefront-Ereignisse erfassen anonymisierte Verhaltensdaten von Ihren Käufern beim Durchsuchen Ihrer Site. Die von diesen Ereignissen erfassten Daten können verwendet werden, um Promotions und Kampagnen zu erstellen, die auf einen bestimmten Satz von Käufern ausgerichtet sind.

>[!NOTE]
>
>Alle Storefront-Ereignisse enthalten `identityMap` -Feld, das eine eindeutige Kennung der Person darstellt.

### addToCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Produkt zum Warenkorb hinzugefügt oder die Menge eines Produkts im Warenkorb erhöht wird. | `commerce.productListAdds` |

#### Aus addToCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `productListAdds` | Gibt an, ob einem Warenkorb ein Produkt hinzugefügt wurde. Ein Wert von `1` gibt an, dass ein Produkt hinzugefügt wurde. |
| `productListItems` | Eine Reihe von Produkten, die dem Warenkorb hinzugefügt wurden |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der zum Warenkorb hinzugefügten Produkteinheiten. |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
| `cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert |

### openCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein neuer Warenkorb erstellt wird, d. h. wenn ein Produkt einem leeren Warenkorb hinzugefügt wird. | `commerce.productListOpens` |

#### Aus openCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `productListOpens` | Gibt an, ob ein Warenkorb erstellt wurde. Ein Wert von `1` gibt an, dass ein Warenkorb erstellt wurde. |
| `productListItems` | Eine Reihe von Produkten, die dem Warenkorb hinzugefügt wurden |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der zum Warenkorb hinzugefügten Produkteinheiten. |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
| `cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert |

### removeFromCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird jedes Mal ausgelöst, wenn ein Produkt entfernt oder die Menge eines Produkts im Warenkorb verringert wird. | `commerce.productListRemovals` |

#### Aus removeFromCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `productListRemovals` | Gibt an, ob ein Produkt aus dem Warenkorb entfernt wurde. Ein Wert von `1` zeigt an, dass ein Produkt aus dem Warenkorb entfernt wurde. |
| `productListItems` | Eine Reihe von Produkten, die aus dem Warenkorb entfernt wurden |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der aus dem Warenkorb entfernten Produkteinheiten. |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
| `cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert |

### shoppingCartView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine beliebige Warenkorbseite geladen wird. | `commerce.productListViews` |

#### Aus shoppingCartView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `productListViews` | Gibt an, ob eine Produktliste angezeigt wurde |
| `productListItems` | Eine Reihe von Produkten im Warenkorb |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
| `cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert |

### pageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Seite geladen wird. | `web.webpagedetails.pageViews` |

#### Von pageView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `pageViews` | Gibt an, ob eine Seite geladen wurde. A `value` von `1` gibt an, dass die Seite geladen wurde. |

### productPageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Produktseite geladen wird. | `commerce.productViews` |

#### Von productPageView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `productViews` | Gibt an, ob das Produkt angezeigt wurde |
| `productListItems` | Eine Reihe von Produkten im Warenkorb |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |

### startCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer auf eine Schaltfläche zum Auschecken klickt. | `commerce.checkouts` |

#### Von startCheckout erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `checkouts` | Gibt an, ob während des Checkout-Prozesses eine Aktion aufgetreten ist |
| `productListItems` | Eine Reihe von Produkten im Warenkorb |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währung für das Produkt |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
| `cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert |

### completeCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt. | `commerce.order` |

#### Von completeCheckout erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `purchases` | Gibt an, ob eine Bestellung akzeptiert wurde |
| `order` | Enthält Informationen über die platzierte Bestellung für ein oder mehrere Produkte |
| `purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `orderType` | Gibt den Typ der aufgegebenen Bestellung an, z. B. Checkout oder Sofortkauf |
| `payments` | Liste der Zahlungen für diese Bestellung |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode, der für diesen Zahlungseintrag verwendet wird. Beispiel: `USD` oder `EUR`. |
| `paymentAmount` | Wert der Zahlung |
| `paymentType` | Die Zahlungsmethode für diese Bestellung. Optionen sind: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | Die eindeutige Transaktionskennung für dieses Zahlungselement |
| `shipping` | Versanddetails für ein oder mehrere Produkte. |
| `shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `shippingAmount` | Die Gesamtversandkosten für die Artikel im Warenkorb |
| `promotionID` | Eindeutige Kennung der Promotion, falls vorhanden |
| `personalEmail` | Gibt die persönliche E-Mail-Adresse an |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `productListItems` | Eine Reihe von Produkten im Warenkorb |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode, der für die Bestellsummen verwendet wird. |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |
+++

## Profilereignisse

+++
Profilereignisse umfassen Kontoinformationen, z. B. `signIn`, `signOut`, `createAccount`und `editAccount`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die zur besseren Definition von Segmenten oder zur Durchführung von Marketing-Kampagnen benötigt werden, z. B. wenn Sie Kunden ansprechen möchten, die in New York leben.

### signIn

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, sich anzumelden. | `userAccount.login` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

#### Von SignIn erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `eventType` | Der primäre Ereignistyp für diesen Zeitreihendatensatz, z. B.: `userAccount.login` |
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `personalEmailID` | Gibt die eindeutige Kennung für die persönliche E-Mail an |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `login` | Gibt an, ob ein Besucher versucht hat, sich anzumelden |

### signOut

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, sich abzumelden. | `userAccount.logout` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

#### Von signOut erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `eventType` | Der primäre Ereignistyp für diesen Zeitreihendatensatz, z. B.: `userAccount.logout` |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `logout` | Gibt an, ob ein Besucher versucht hat, sich abzumelden |

### createAccount

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen. | `userAccount.createProfile` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

#### Von createAccount erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `eventType` | Der primäre Ereignistyp für diesen Zeitreihendatensatz, z. B.: `account.createProfile` |
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend |
| `personalEmailID` | Gibt die eindeutige Kennung für die persönliche E-Mail an |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `createProfile` | Gibt an, ob ein Benutzer ein Kontoprofil erstellt hat |

### editAccount

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten. | `userAccount.updateProfile` |

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

#### Von editAccount erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `eventType` | Der primäre Ereignistyp für diesen Zeitreihendatensatz, z. B.: `account.updateProfile` |
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend |
| `personalEmailID` | Gibt die eindeutige Kennung für die persönliche E-Mail an |
| `personalEmail` | Gibt die persönliche E-Mail-Adresse an |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat |
+++

## Suchereignisse

+++ Die Suchereignisse stellen Daten bereit, die für die Absicht des Käufers relevant sind. Einblicke in die Absichten eines Käufers helfen den Händlern zu sehen, wie Käufer nach Artikeln suchen, worauf sie klicken und letztlich kaufen oder aufgeben. Ein Beispiel dafür, wie Sie diese Daten verwenden können, ist, wenn Sie bestehende Käufer ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen.

### searchRequestSent

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird durch die folgenden Ereignisse im Popup &quot;Suche beim Eingeben&quot;ausgelöst:<br>Drücken Sie die Eingabetaste, klicken Sie auf _Alle anzeigen_<br> Wird durch die folgenden Ereignisse auf den Suchergebnisseiten ausgelöst:<br>Wählen Sie einen Filter und ändern Sie die Sortierreihenfolge (_Sortieren nach_), Ändern Sie die Sortierrichtung (aufsteigend oder absteigend), ändern Sie die Anzahl der Ergebnisse pro Seite (_Anzahl pro Seite anzeigen_), zur nächsten Seite navigieren, zur vorherigen Seite navigieren, zu einer anderen Seite navigieren | `searchRequest` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn das B2B-Modul installiert ist.

#### Aus searchRequestSent erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchRequest` | Gibt an, ob eine Suchanfrage gesendet wurde |
| `filter` | Gibt an, ob Filter angewendet wurden, um Suchergebnisse zu begrenzen |
| `attribute` (Filter) | Die Facette eines Elements, mit der bestimmt wird, ob es in Suchergebnisse aufgenommen werden soll |
| `value` | Attributwerte, mit denen bestimmt wird, welche Elemente in Suchergebnissen enthalten sind |
| `isRange` | Wenn &quot;true&quot;, zeigen Werte Endpunkte eines akzeptablen Wertebereichs an |
| `sort` | Gibt an, wie Suchergebnisse sortiert werden sollen |
| `attribute` (sortieren) | Ein Attribut, mit dem Elemente in Suchergebnissen sortiert werden |
| `order` | Die Reihenfolge, in der Suchergebnisse zurückgegeben werden |
| `query` | Die gesuchten Begriffe |

### searchResponseReceived

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn die Live-Suche Ergebnisse für die Popup- oder Suchergebnisseite &quot;Suche beim Eingeben&quot;zurückgibt. | `searchResponse` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn das B2B-Modul installiert ist.

#### Von searchResponseReceived erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchResponse` | Gibt an, ob eine Suchanfrage empfangen wurde |
| `suggestions` | Ein Array von Zeichenfolgen, die die Namen der Produkte und Kategorien enthalten, die im Katalog vorhanden sind und der Suchabfrage ähnlich sind |
| `numberOfResults` | Die Anzahl der zurückgegebenen Produkte |
| `productListItems` | Eine Reihe von Produkten im Warenkorb. |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `productImageUrl` | Hauptbild-URL des Produkts |

+++

## (Beta) Back-Office-Ereignisse

>[!NOTE]
>
>Für Händler, die sich bereits in unserem Back Office Beta Programm angemeldet haben, haben Sie Zugriff auf Backoffice-Veranstaltungen. Wenn Sie am Back Office Beta Programm teilnehmen möchten, wenden Sie sich an [drios@adobe.com](mailto:drios@adobe.com).

+++ Die Backoffice-Ereignisse enthalten Informationen über den Status einer Bestellung, z. B. ob eine Bestellung aufgegeben, storniert, rückerstattet oder versandt wurde. Die Daten, die diese serverseitigen Ereignisse erfassen, zeigen eine 360-Grad-Ansicht der Bestellung des Käufers. Dies kann Händlern bei der Entwicklung von Marketing-Kampagnen helfen, den gesamten Bestellstatus besser zu erreichen oder zu analysieren. Sie können beispielsweise Trends in bestimmten Produktkategorien erkennen, die zu unterschiedlichen Jahreszeiten gut abschneiden. Zum Beispiel Winterkleidung, die sich in kalten Monaten besser verkauft, oder bestimmte Produktfarben, an denen sich Kunden über die Jahre interessieren. Darüber hinaus können Sie mithilfe von Bestellstatusdaten den Kundenwert über die gesamte Lebensdauer berechnen, indem Sie die Tendenz eines Käufers verstehen, basierend auf früheren Bestellungen zu konvertieren.

### orderPlaced

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung aufgibt. | `commerce.orderPlaced` |

#### Von orderPlaced erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `identityMap` | Enthält die E-Mail-Adresse, die den Kunden identifiziert |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `eventType` | `commerce.orderPlaced` |
| `productListItems` | Eine Reihe von Produkten in der Reihenfolge |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `order` | Enthält Informationen zur Bestellung |
| `purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist |
| `purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung |
| `payments` | Liste der Zahlungen für diese Bestellung |
| `paymentType` | Die Zahlungsmethode für diese Bestellung. Aufzählte, zulässige benutzerdefinierte Werte. |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement |
| `paymentAmount` | Wert der Zahlung |
| `shipping` | Versanddetails für ein oder mehrere Produkte |
| `shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `shippingAddress` | Lieferadresse |
| `street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `billingAddress` | Postadresse der Rechnungsstellung |
| `street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `street2` | Zusätzliche Felder für Informationen auf Straßenebene |
| `city` | Der Name der Stadt |
| `state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `country` | Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |

### orderShipped

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Bestellung versandt wird. | `commerce.orderLineItemShipped` |

#### Von orderShipped erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`identityMap`|Enthält die E-Mail-Adresse, die den Kunden identifiziert| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`eventType`|`commerce.orderLineItemShipped`| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung| |`payments`|Liste der Zahlungen für diesen Auftrag| |`paymentType`|Die Zahlungsmethode für diese Bestellung. Aufzählte, zulässige benutzerdefinierte Werte.| |`currencyCode`|Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement | |`paymentAmount`|Wert der Zahlung| |`shipping`|Versanddetails für ein oder mehrere Produkte| |`shippingMethod`|Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Lieferung, Abholung im Geschäft usw.| |`shippingAddress`|Lieferadresse | |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`shippingAmount`|Der Betrag, den der Kunde für den Versand zahlen musste.| |`billingAddress`|Abrechnungs-Postanschrift| |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`street2`|Zusätzliches Feld für Informationen auf Straßenebene| |`city`|Name der Stadt| |`state`|Der Name des Status. Dies ist ein Freiformfeld.| |`postalCode`|Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten.| |`country`|Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann.|

### orderCancelled

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung abbricht. | `commerce.orderCancelled` |

#### Von orderCancelled erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`identityMap`|Enthält die E-Mail-Adresse, die den Kunden identifiziert| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`eventType`|`commerce.orderCancelled`| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung|

### orderRefund

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Element in einer Reihenfolge zurückgibt. | `commerce.creditMemoIssued` |

#### Daten, die bei orderRefund erfasst wurden

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`identityMap`|Enthält die E-Mail-Adresse, die den Kunden identifiziert| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`eventType`|`commerce.creditMemoIssued`| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung|
+++
