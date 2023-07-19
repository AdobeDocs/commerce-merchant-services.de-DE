---
title: Veranstaltungen
description: Erfahren Sie, welche Daten von den einzelnen Ereignissen erfasst werden.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '4779'
ht-degree: 0%

---

# Experience Platform Connector-Ereignisse

Im Folgenden werden die Commerce-Ereignisse aufgelistet, die bei der Installation der Experience Platform Connector-Erweiterung verfügbar sind. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [sonstige Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt vom Adobe Experience Platform Web SDK.

## Storefront-Ereignisse

Die Storefront-Ereignisse erfassen anonymisierte Verhaltensdaten von Ihren Käufern beim Durchsuchen Ihrer Site. Sie können die von diesen Ereignissen erfassten Daten verwenden, um Promotions und Kampagnen zu erstellen, die auf einen bestimmten Satz von Käufern ausgerichtet sind. Storefront-Ereignisdaten umfassen nur einfache und konfigurierbare Produkte.

>[!NOTE]
>
>Alle Storefront-Ereignisse enthalten [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -Feld, das die E-Mail-Adresse des Käufers, sofern verfügbar, sowie die ECID enthält. Wenn Sie diese Profildaten in jedes Ereignis einbeziehen, benötigen Sie keinen separaten Benutzerkontoimport aus Adobe Commerce.

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

## Profilereignisse

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
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend |
| `personalEmailID` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen |
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
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend |
| `personalEmailID` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen |
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
| `person` | Ein einzelner Schauspieler, Kontakt oder Eigentümer |
| `accountID` | Erfasst die Benutzerkonto-ID |
| `accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend |
| `personalEmailID` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen |
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an |
| `updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat |

## Suchereignisse

Die Suchereignisse stellen Daten bereit, die für die Absicht des Käufers relevant sind. Einblicke in die Absichten eines Käufers helfen den Händlern zu sehen, wie Käufer nach Artikeln suchen, worauf sie klicken und letztlich kaufen oder aufgeben. Ein Beispiel dafür, wie Sie diese Daten verwenden können, ist, wenn Sie bestehende Käufer ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen.

Verwenden Sie die `uniqueIdentifier` -Feld in beiden `searchRequestSent` und `searchResponseReceived` -Ereignisse, um eine Suchanfrage mit der entsprechenden Suchanfrage zu vergleichen.

### searchRequestSent

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird durch die folgenden Ereignisse im Popup &quot;Suche beim Eingeben&quot;ausgelöst:<br><br>Drücken Sie die Eingabetaste, klicken Sie auf _Alle anzeigen_<br><br> Wird durch die folgenden Ereignisse auf den Suchergebnisseiten ausgelöst:<br><br>Wählen Sie einen Filter und ändern Sie die Sortierreihenfolge (_Sortieren nach_), Ändern Sie die Sortierrichtung (aufsteigend oder absteigend), ändern Sie die Anzahl der Ergebnisse pro Seite (_Anzahl pro Seite anzeigen_), zur nächsten Seite navigieren, zur vorherigen Seite navigieren, zu einer anderen Seite navigieren | `searchRequest` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn die B2B-Erweiterung installiert ist.

#### Aus searchRequestSent erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchRequest` | Gibt an, ob eine Suchanfrage gesendet wurde |
| `id` | Die eindeutige ID für diese bestimmte Suchanfrage |
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
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn die B2B-Erweiterung installiert ist.

#### Von searchResponseReceived erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchResponse` | Gibt an, ob eine Suchanfrage empfangen wurde |
| `id` | Die eindeutige ID für diese bestimmte Suchantwort |
| `suggestions` | Ein Array von Zeichenfolgen, die die Namen der Produkte und Kategorien enthalten, die im Katalog vorhanden sind und der Suchabfrage ähnlich sind |
| `numberOfResults` | Die Anzahl der zurückgegebenen Produkte |
| `productListItems` | Eine Reihe von Produkten im Warenkorb. |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `productImageUrl` | Hauptbild-URL des Produkts |

## B2B-Ereignisse

![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler müssen Sie [install](install.md#install-the-b2b-extension) die `experience-platform-connector-b2b` -Erweiterung, um diese Ereignisse zu aktivieren.

B2B-Ereignisse enthalten [Anforderungsliste](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) Informationen, z. B. ob eine Anforderungsliste erstellt, hinzugefügt oder gelöscht wurde. Durch die Verfolgung von Ereignissen, die speziell für Anforderungslisten gelten, können Sie sehen, welche Produkte Ihre Kunden häufig kaufen, und auf dieser Grundlage Kampagnen erstellen.

### createRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine neue Anforderungsliste erstellt. | `commerce.requisitionListOpens` |

#### Von createRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste |
| `ID` | Eindeutige Kennung der Anforderungsliste |
| `name` | Name der vom Kunden angegebenen Anforderungsliste |
| `description` | Beschreibung der vom Kunden angegebenen Anforderungsliste |

### addToRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Produkt zu einer vorhandenen Anforderungsliste hinzufügt oder wenn er eine neue Liste erstellt. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` wird nicht auf Kategorieansichtsseiten oder für konfigurierbare Produkte unterstützt. Sie wird auf Produktansichtsseiten und für einfache Produkte unterstützt.

#### Von addToRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste |
| `ID` | Eindeutige Kennung der Anforderungsliste |
| `name` | Name der vom Kunden angegebenen Anforderungsliste |
| `description` | Beschreibung der vom Kunden angegebenen Anforderungsliste |
| `productListItems` | Eine Reihe von Produkten, die der Anforderungsliste hinzugefügt wurden |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `quantity` | Anzahl der hinzugefügten Produkteinheiten |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |

### removeFromRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Produkt aus einer Anforderungsliste entfernt. | `commerce.requisitionListRemovals` |

#### Von removeFromRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste |
| `ID` | Eindeutige Kennung der Anforderungsliste |
| `name` | Name der vom Kunden angegebenen Anforderungsliste |
| `description` | Beschreibung der vom Kunden angegebenen Anforderungsliste |
| `productListItems` | Eine Reihe von Produkten, die der Anforderungsliste hinzugefügt wurden |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `quantity` | Anzahl der hinzugefügten Produkteinheiten |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement |
| `selectedOptions` | Feld, das für ein konfigurierbares Produkt verwendet wird. `attribute` identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color` und `value` gibt den Wert des Attributs an, z. B. `small` oder `black`. |

## Backoffice-Ereignisse

Die Backoffice-Ereignisse enthalten Informationen über den Status einer Bestellung, z. B. ob eine Bestellung aufgegeben, storniert, rückerstattet, versandt oder abgeschlossen wurde. Die Daten, die von diesen serverseitigen Ereignissen erfasst werden, zeigen eine 360-Grad-Ansicht der Bestellung des Käufers. Diese Ansicht hilft Händlern, bei der Entwicklung von Marketing-Kampagnen den gesamten Bestellstatus besser zu erreichen oder zu analysieren. Sie können beispielsweise Trends in bestimmten Produktkategorien erkennen, die zu unterschiedlichen Jahreszeiten gut abschneiden. Zum Beispiel Winterkleidung, die sich in kalten Monaten besser verkauft, oder bestimmte Produktfarben, an denen sich Kunden über die Jahre interessieren. Darüber hinaus können Sie mithilfe von Bestellstatusdaten den Kundenwert über die gesamte Lebensdauer berechnen, indem Sie die Tendenz eines Käufers verstehen, basierend auf früheren Bestellungen zu konvertieren.

>[!NOTE]
>
>Alle Backoffice-Ereignisse enthalten [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -Feld, das die E-Mail-Adresse des Käufers angibt. Wenn Sie diese Profildaten in jedes Ereignis einbeziehen, benötigen Sie keinen separaten Benutzerkontoimport aus Adobe Commerce.

### orderPlaced

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung aufgibt. | `commerce.backofficeOrderPlaced` |

#### Von orderPlaced erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `address` | Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert |
| `productListItems` | Eine Reihe von Produkten in der Reihenfolge |
| `id` | Die Zeileneintrag-ID für diesen Produkteintrag. Das Produkt selbst wird durch die `product` -Feld. |
| `name` | Der Anzeigename oder der für Menschen lesbare Name des Produkts |
| `SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `quantity` | Die Anzahl der Produkteinheiten im Warenkorb |
| `priceTotal` | Der Gesamtpreis für den Produktzeileneintrag |
| `discountAmount` | Gibt den angewendeten Rabattbetrag an |
| `commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `order` | Enthält Informationen zur Bestellung |
| `purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist |
| `priceTotal` | Der Gesamtpreis dieser Bestellung nach Anwendung aller Rabatte und Steuern |
| `currencyCode` | Der für die Bestellsummen verwendete Währungscode nach ISO 4217 |
| `purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung |
| `payments` | Liste der Zahlungen für diese Bestellung |
| `paymentType` | Die Zahlungsmethode für diese Bestellung. Aufzählte, zulässige benutzerdefinierte Werte. |
| `currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement |
| `paymentAmount` | Wert der Zahlung |
| `taxAmount` | Der vom Käufer im Rahmen der Abschlusszahlung gezahlte Steuerbetrag |
| `createdDate` | Datum und Uhrzeit der Erstellung einer neuen Bestellung im Commerce-System. Beispiel: `2022-10-15T20:20:39+00:00` |
| `shipping` | Versanddetails für ein oder mehrere Produkte |
| `shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `address` | Lieferadresse |
| `street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `street2` | Zusätzliche Felder für Informationen auf Straßenebene |
| `city` | Der Name der Stadt |
| `state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `country` | Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `billingAddress` | Postadresse der Rechnungsstellung |
| `street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `street2` | Zusätzliche Felder für Informationen auf Straßenebene |
| `city` | Der Name der Stadt |
| `state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `country` | Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse |
| `address` | Die technische Adresse, z. B. &quot;name@domain.com&quot;, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist |

### orderItemsShipped

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Bestellung versandt wird. | `commerce.backofficeOrderItemsShipped` |

#### Von orderItemsShipped erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`id`|Die Zeileneintrag-ID für diesen Produkteintrag. Das Produkt selbst wird durch die `product` -Feld.| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`commerceScope`|Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.).| |`environmentID`|Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche.| |`storeCode`|Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben.| |`storeViewCode`|Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben.| |`websiteCode`|Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben.| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`priceTotal`|Der Gesamtpreis dieser Bestellung nach Anwendung aller Rabatte und Steuern| |`currencyCode`|Der für die Bestellsummen verwendete Währungscode nach ISO 4217 | |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung| |`payments`|Liste der Zahlungen für diesen Auftrag| |`paymentType`|Die Zahlungsmethode für diese Bestellung. Aufzählte, zulässige benutzerdefinierte Werte.| |`currencyCode`|Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement | |`paymentAmount`|Wert der Zahlung| |`lastUpdatedDate`|Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird| |`shipping`|Versanddetails für ein oder mehrere Produkte| |`shippingMethod`|Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Lieferung, Abholung im Geschäft usw.| |`trackingNumber`|Die von der Reederei für die Lieferung eines Bestellartikels angegebene Trackingnummer| |`trackingURL`|URL zur Verfolgung des Versandstatus eines Bestellartikels| |`shipDate`|Das Datum, an dem ein oder mehrere Artikel aus einer Bestellung versandt werden| |`address`|Lieferadresse | |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`street2`|Zusätzliches Feld für Informationen auf Straßenebene| |`city`|Name der Stadt| |`state`|Der Name des Status. Dies ist ein Freiformfeld.| |`postalCode`|Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten.| |`country`|Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann.| |`shippingAmount`|Der Betrag, den der Kunde für den Versand zahlen musste.| |`billingAddress`|Abrechnungs-Postanschrift| |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`street2`|Zusätzliches Feld für Informationen auf Straßenebene| |`city`|Name der Stadt| |`state`|Der Name des Status. Dies ist ein Freiformfeld.| |`postalCode`|Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten.| |`country`|Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann.| |`personalEmail`|Eine persönliche E-Mail-Adresse| |`address`|Die technische Adresse, z. B. &quot;name@domain.com&quot;, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist|

### orderCancelled

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung abbricht. | `commerce.backofficeOrderCancelled` |

#### Von orderCancelled erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`id`|Die Zeileneintrag-ID für diesen Produkteintrag. Das Produkt selbst wird durch die `product` -Feld.| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`commerceScope`|Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.).| |`environmentID`|Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche.| |`storeCode`|Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben.| |`storeViewCode`|Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben.| |`websiteCode`|Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben.| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung| |`cancelDate`|Datum und Uhrzeit der Stornierung einer Bestellung durch einen Käufer| |`lastUpdatedDate`|Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird| |`personalEmail`|Eine persönliche E-Mail-Adresse| |`address`|Die technische Adresse, z. B. &quot;name@domain.com&quot;, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist|

### creditMemoIssued

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Element in einer Reihenfolge zurückgibt. | `commerce.backofficeCreditMemoIssued` |

#### Von CreditMemoIssued erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`id`|Die Zeileneintrag-ID für diesen Produkteintrag. Das Produkt selbst wird durch die `product` -Feld.| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung| |`lastUpdatedDate`|Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird| |`personalEmail`|Eine persönliche E-Mail-Adresse| |`address`|Die technische Adresse, z. B. &quot;name@domain.com&quot;, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist|

### orderShippingCompleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Element in einer Reihenfolge zurückgibt. | `commerce.backofficeOrderShipmentCompleted` |

#### Von orderShippingCompleted erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.
|Feld|Beschreibung| |—|—| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`productListItems`|Ein Array von Produkten in der Reihenfolge| |`id`|Die Zeileneintrag-ID für diesen Produkteintrag. Das Produkt selbst wird durch die `product` -Feld.| |`name`|Anzeigename oder für Menschen lesbarer Name des Produkts| |`SKU`|Lagereinheit. Die eindeutige Kennung für das Produkt.| |`quantity`|Anzahl der Produkteinheiten im Warenkorb| |`priceTotal`|Der Gesamtpreis für den Produktposten| |`discountAmount`|Gibt den angewendeten Abzinsungsbetrag an| |`order`|Enthält Informationen zur Bestellung| |`purchaseID`|Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist| |`priceTotal`|Der Gesamtpreis dieser Bestellung nach Anwendung aller Rabatte und Steuern| |`currencyCode`|Der für die Bestellsummen verwendete Währungscode nach ISO 4217 | |`purchaseOrderNumber`|Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung| |`taxAmount`|Steuerbetrag, der vom Käufer im Rahmen der Abschlusszahlung gezahlt wurde.| |`createdDate`|Zeitpunkt und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel: `2022-10-15T20:20:39+00:00`| |`payments`|Liste der Zahlungen für diesen Auftrag| |`paymentType`|Die Zahlungsmethode für diese Bestellung. Aufzählte, zulässige benutzerdefinierte Werte.| |`currencyCode`|Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) Währungscode für dieses Zahlungselement | |`paymentAmount`|Wert der Zahlung| |`shipping`|Versanddetails für ein oder mehrere Produkte| |`shippingMethod`|Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Lieferung, Abholung im Geschäft usw.| |`address`|Lieferadresse | |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`street2`|Zusätzliches Feld für Informationen auf Straßenebene| |`city`|Name der Stadt| |`state`|Der Name des Status. Dies ist ein Freiformfeld.| |`postalCode`|Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten.| |`country`|Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann.| |`shippingAmount`|Der Betrag, den der Kunde für den Versand zahlen musste.| |`address`|Die technische Adresse, z. B. `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert| |`billingAddress`|Abrechnungs-Postanschrift| |`street1`|Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname| |`street2`|Zusätzliches Feld für Informationen auf Straßenebene| |`city`|Name der Stadt| |`state`|Der Name des Status. Dies ist ein Freiformfeld.| |`postalCode`|Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern enthalten diese Daten nur einen Teil der Postleitzahl.| |`country`|Der Name des von der Regierung verwalteten Gebiets. Sonstige `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann.| |`personalEmail`|Eine persönliche E-Mail-Adresse| |`address`|Die technische Adresse, z. B. &quot;name@domain.com&quot;, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist|
