---
title: Veranstaltungen
description: Erfahren Sie, welche Daten von den einzelnen Ereignissen erfasst werden.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: aaaab3d11c15a69856711a41e889a5d0208aedd2
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 0%

---

# Experience Platform Connector-Ereignisse

Im Folgenden werden die Commerce-Ereignisse aufgelistet, die bei der Installation der Experience Platform Connector-Erweiterung verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [sonstige Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt vom Adobe Experience Platform Web SDK.

>[!NOTE]
>
>Alle Storefront-Ereignisse enthalten `personID` -Feld, das eine eindeutige Kennung der Person darstellt.

## addToCart

Wird ausgelöst, wenn ein Produkt zum Warenkorb hinzugefügt oder die Menge eines Produkts im Warenkorb erhöht wird.

### XDM-Ereignisname

`commerce.productListAdds`

### Typ

Storefront

### Erfasste Daten

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

## openCart

Wird ausgelöst, wenn ein neuer Warenkorb erstellt wird, d. h. wenn ein Produkt einem leeren Warenkorb hinzugefügt wird.

### XDM-Ereignisname

`commerce.productListOpens`

### Typ

Storefront

### Erfasste Daten

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

## removeFromCart

Wird jedes Mal ausgelöst, wenn ein Produkt entfernt oder die Menge eines Produkts im Warenkorb verringert wird.

### XDM-Ereignisname

`commerce.productListRemovals`

### Typ

Storefront

### Erfasste Daten

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

## shoppingCartView

Wird ausgelöst, wenn eine beliebige Warenkorbseite geladen wird.

### XDM-Ereignisname

`commerce.productListViews`

### Typ

Storefront

### Erfasste Daten

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

## pageView

Wird ausgelöst, wenn eine Seite geladen wird.

### XDM-Ereignisname

`web.webpagedetails.pageViews`

### Typ

Storefront

### Erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `pageViews` | Gibt an, ob eine Seite geladen wurde. A `value` von `1` gibt an, dass die Seite geladen wurde. |

## productPageView

Wird ausgelöst, wenn eine Produktseite geladen wird.

### XDM-Ereignisname

`commerce.productViews`

### Typ

Storefront

### Erfasste Daten

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

## startCheckout

Wird ausgelöst, wenn der Käufer auf eine Schaltfläche zum Auschecken klickt.

### XDM-Ereignisname

`commerce.checkouts`

### Typ

Storefront

### Erfasste Daten

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

## completeCheckout

Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt.

### XDM-Ereignisname

`commerce.order`

### Typ

Storefront

### Erfasste Daten

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
| `productListItems` | Eine Reihe von Produkten im Warenkorb |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode, der für die Bestellsummen verwendet wird. |
| `productImageUrl` | Hauptbild-URL des Produkts |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |

## signIn

Wird ausgelöst, wenn ein Käufer versucht, sich anzumelden.

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

### XDM-Ereignisname

`userAccount.login`

### Typ

Profil

### Erfasste Daten

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

## signOut

Wird ausgelöst, wenn ein Käufer versucht, sich abzumelden.

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

### XDM-Ereignisname

`userAccount.logout`

### Typ

Profil

### Erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `eventType` | Der primäre Ereignistyp für diesen Zeitreihendatensatz, z. B.: `userAccount.logout` |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `logout` | Gibt an, ob ein Besucher versucht hat, sich abzumelden |

## createAccount

Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen.

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

### XDM-Ereignisname

`userAccount.createProfile`

### Typ

Profil

### Erfasste Daten

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

## editAccount

Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten.

>[!NOTE]
>
> Dieses Ereignis wird ausgelöst, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.

### XDM-Ereignisname

`userAccount.updateProfile`

### Typ

Profil

### Erfasste Daten

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

## searchRequestSent

Wird durch die folgenden Ereignisse im Popup &quot;Suche beim Eingeben&quot;ausgelöst:

- Drücken Sie die Eingabetaste
- Klicken _Alle anzeigen_

Wird durch die folgenden Ereignisse auf den Suchergebnisseiten ausgelöst:

- Filter auswählen
- Ändern Sie die Sortierreihenfolge (_Sortieren nach_)
- Ändern der Sortierrichtung (aufsteigend oder absteigend)
- Die Anzahl der Ergebnisse pro Seite ändern (_Anzahl pro Seite anzeigen_)
- Zur nächsten Seite navigieren
- Zur vorherigen Seite navigieren
- Navigieren zu einer anderen Seite

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn das B2B-Modul installiert ist.

### XDM-Ereignisname

`searchRequest`

### Typ

Suche

### Erfasste Daten

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

## searchResponseReceived

Wird ausgelöst, wenn die Live-Suche Ergebnisse für die Popup- oder Suchergebnisseite &quot;Suche beim Eingeben&quot;zurückgibt.

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn das B2B-Modul installiert ist.

### XDM-Ereignisname

`searchResponse`

### Typ

Suche

### Erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchResponse` | Gibt an, ob eine Suchanfrage empfangen wurde |
| `suggestions` | Ein Array von Zeichenfolgen, die die Namen der Produkte und Kategorien enthalten, die im Katalog vorhanden sind und der Suchabfrage ähnlich sind |
| `numberOfResults` | Die Anzahl der zurückgegebenen Produkte |
| `productListItems` | Eine Reihe von Produkten im Warenkorb. Umfasst die `SKU`(Bestandseinheit) und `name` des Produkts (Anzeigename oder für Menschen lesbarer Name) |
