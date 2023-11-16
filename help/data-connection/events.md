---
title: Veranstaltungen
description: Erfahren Sie, welche Daten die einzelnen Ereignisse erfassen.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f90ef4d2732a0b0676e0899712f94b41a1c2d85a
workflow-type: tm+mt
source-wordcount: '6894'
ht-degree: 0%

---

# [!DNL Data Connection] Veranstaltungen

Im Folgenden werden die Commerce-Ereignisse aufgeführt, die bei der Installation der [!DNL Data Connection] -Erweiterung. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

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
| `commerce.productListAdds` | Gibt an, ob einem Warenkorb ein Produkt hinzugefügt wurde. Ein Wert von `1` gibt an, dass ein Produkt hinzugefügt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### openCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein neuer Warenkorb erstellt wird, bei dem ein Produkt einem leeren Warenkorb hinzugefügt wird. | `commerce.productListOpens` |

#### Aus openCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.productListOpens` | Gibt an, ob ein Warenkorb erstellt wurde. Ein Wert von `1` gibt an, dass ein Warenkorb erstellt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### removeFromCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird jedes Mal ausgelöst, wenn ein Produkt entfernt oder die Menge eines Produkts im Warenkorb verringert wird. | `commerce.productListRemovals` |

#### Aus removeFromCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.productListRemovals` | Gibt an, ob ein Produkt aus dem Warenkorb entfernt wurde. Ein Wert von `1` zeigt an, dass ein Produkt aus dem Warenkorb entfernt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### shoppingCartView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine beliebige Warenkorbseite geladen wird. | `commerce.productListViews` |

#### Aus shoppingCartView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.productListViews` | Gibt an, ob eine Produktliste angezeigt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### pageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Seite geladen wird. | `web.webpagedetails.pageViews` |

#### Von pageView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `web.webPageDetails.pageViews` | Gibt an, ob eine Seite geladen wurde. A `value` von `1` gibt an, dass die Seite geladen wurde. |
| `web.webPageDetails.URL` | Die normative oder übliche URL der Webseite. Dies kann die tatsächliche URL sein, die zum Erreichen der Seite verwendet wird und die mithilfe von aufgezeichnet würde. `Web Link`. |
| `web.webPageDetails.name` | Der normative Name der Webseite. Dieser Name ist nicht notwendigerweise der Seitentitel oder direkt mit dem Seiteninhalt verknüpft, sondern dient zum Organisieren der Seiten einer Site zu Klassifizierungszwecken. |
| `web.webReferrer.URL` | Die URL der Webseite, die ein Käufer besucht hat, bevor er auf einen Link zu Ihrer Site klickt. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

### productPageView

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Produktseite geladen wird. | `commerce.productViews` |

#### Von productPageView erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.productViews` | Gibt an, ob das Produkt angezeigt wurde. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### startCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer auf eine Schaltfläche zum Auschecken klickt. | `commerce.checkouts` |

#### Von startCheckout erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.checkouts` | Gibt an, ob während des Checkout-Prozesses eine Aktion aufgetreten ist. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### completeCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt. | `commerce.order` |

#### Von completeCheckout erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.purchases` | Gibt an, ob eine Bestellung akzeptiert wurde. |
| `commerce.order` | Enthält Informationen über die platzierte Bestellung für ein oder mehrere Produkte. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diesen Zahlungsvorgang. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Optionen sind: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer im Rahmen der Abschlusszahlung entrichtete Steuerbetrag. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wird. |
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |  | `shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

## Profilereignisse

Profilereignisse umfassen Kontoinformationen, z. B. `signIn`, `signOut`, `createAccount`, und `editAccount`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die zur besseren Definition von Segmenten oder zur Durchführung von Marketing-Kampagnen benötigt werden, z. B. wenn Sie Kunden ansprechen möchten, die in New York leben.

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
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.login` | Gibt an, ob ein Besucher versucht hat, sich anzumelden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

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
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.logout` | Gibt an, ob ein Besucher versucht hat, sich abzumelden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

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
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

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
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp, z. B. `Personal` oder `Company`, falls zutreffend. |
| `person.personalEmailID` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

## Suchereignisse

Die Suchereignisse stellen Daten bereit, die für die Absicht des Käufers relevant sind. Einblicke in die Absichten eines Käufers helfen den Händlern zu sehen, wie Käufer nach Artikeln suchen, auf was sie klicken und letztlich kaufen oder aufgeben. Ein Beispiel dafür, wie Sie diese Daten verwenden können, ist, wenn Sie bestehende Käufer ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen.

Verwenden Sie die `searchRequest.id` und `searchResponse.id` Felder, die in beiden `searchRequestSent` und `searchResponseReceived` -Ereignisse, um eine Suchanfrage mit der entsprechenden Suchanfrage zu vergleichen.

### searchRequestSent

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird durch die folgenden Ereignisse im Popup &quot;Suche beim Eingeben&quot;ausgelöst:<br><br>Drücken Sie die Eingabetaste, klicken Sie auf _Alle anzeigen_<br><br> Wird durch die folgenden Ereignisse auf den Suchergebnisseiten ausgelöst:<br><br>Wählen Sie einen Filter und ändern Sie die Sortierreihenfolge (_Sortieren nach_), Ändern der Sortierrichtung (aufsteigend oder absteigend), Ändern der Anzahl der Ergebnisse pro Seite (_Anzahl pro Seite anzeigen_), zur nächsten Seite navigieren, zur vorherigen Seite navigieren, zu einer anderen Seite navigieren | `searchRequest` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn die B2B-Erweiterung installiert ist.

#### Aus searchRequestSent erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `searchRequest` | Gibt an, ob eine Suchanfrage gesendet wurde. |
| `searchRequest.id` | Die eindeutige ID für diese bestimmte Suchanfrage. |
| `searchRequest.value` | Der quantifizierbare Wert des Antrags. |
| `siteSearch` | Enthält Informationen zur Suche. |
| `siteSearch.filter` | Gibt an, ob Filter angewendet wurden, um Suchergebnisse zu begrenzen. |
| `siteSearch.filter.attribute` (Filter) | Die Facette eines Elements, mit der bestimmt wird, ob es in Suchergebnisse aufgenommen werden soll. |
| `siteSearch.filter.isRange` | Wenn &quot;true&quot;, zeigen Werte Endpunkte eines akzeptablen Wertebereichs an. |
| `siteSearch.filter.value` | Attributwert, mit dem bestimmt wird, welche Elemente in den Suchergebnissen enthalten sind. |
| `siteSearch.sort` | Gibt an, wie Suchergebnisse sortiert werden sollen. |
| `siteSearch.sort.attribute` (sortieren) | Ein Attribut zum Sortieren von Elementen in Suchergebnissen. |
| `siteSearch.sort.order` | Die Reihenfolge, in der Suchergebnisse zurückgegeben werden. |
| `siteSearch.query` | Die gesuchten Begriffe. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

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
| `searchResponse` | Gibt an, ob eine Suchanfrage empfangen wurde. |
| `searchResponse.id` | Die eindeutige ID für diese bestimmte Suchantwort. |
| `searchResponse.value` | Der quantifizierbare Wert der Antwort. |
| `siteSearch.numberOfResults` | Die Anzahl der zurückgegebenen Produkte. |
| `siteSearch.suggestions` | Ein Array von Zeichenfolgen, die die Namen der Produkte und Kategorien enthalten, die im Katalog vorhanden sind und der Suchabfrage ähnlich sind. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

## B2B-Ereignisse

![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler müssen Sie [install](install.md#install-the-b2b-extension) die `experience-platform-connector-b2b` -Erweiterung, um diese Ereignisse zu aktivieren.

B2B-Ereignisse enthalten [Anforderungsliste](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) Informationen, z. B. ob eine Anforderungsliste erstellt, hinzugefügt oder gelöscht wurde. Durch die Verfolgung von Ereignissen, die speziell für Anforderungslisten gelten, können Sie sehen, welche Produkte Ihre Kunden häufig kaufen, und auf dieser Grundlage Kampagnen erstellen.

### createRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Anforderungsliste erstellt. | `commerce.requisitionListOpens` |

#### Von createRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.requisitionListOpens` | Gibt die Initialisierung einer neuen Anforderungsliste an. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

### addToRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Produkt zu einer bestehenden Anforderungsliste hinzufügt oder eine Liste erstellt. | `commerce.requisitionListAdds` |

#### Von addToRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.requisitionListAdds` | Gibt das Hinzufügen eines oder mehrerer Produkte zu einer Anforderungsliste an. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die der Anforderungsliste hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### removeFromRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer ein Produkt aus einer Anforderungsliste entfernt. | `commerce.requisitionListRemovals` |

#### Von removeFromRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.requsitionListRemovals` | Gibt das Entfernen eines oder mehrerer Produkte aus einer Anforderungsliste an. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `productListItems` | Eine Reihe von Produkten, die der Anforderungsliste hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

## Back-Office-Ereignisse

Die Backoffice-Ereignisse enthalten Informationen über den Status einer Bestellung, z. B. ob eine Bestellung aufgegeben, storniert, rückerstattet, versandt oder abgeschlossen wurde. Die Daten, die von diesen serverseitigen Ereignissen erfasst werden, zeigen eine 360-Grad-Ansicht der Bestellung des Käufers. Diese Ansicht hilft Händlern, bei der Entwicklung von Marketing-Kampagnen den gesamten Bestellstatus besser zu erreichen oder zu analysieren. Sie können beispielsweise Trends in bestimmten Produktkategorien erkennen, die zu unterschiedlichen Jahreszeiten gut abschneiden. Zum Beispiel Winterbekleidung, die sich in kalten Monaten besser verkauft, oder bestimmte Produktfarben, an denen die Käufer über die Jahre interessiert sind. Darüber hinaus können Sie mithilfe von Bestellstatusdaten den Kundenwert über die gesamte Lebensdauer berechnen, indem Sie die Tendenz eines Käufers verstehen, basierend auf früheren Bestellungen zu konvertieren.

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
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diesen Zahlungsvorgang. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Zählte, zulässige benutzerdefinierte Werte. |
| `commerce.order.payments.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer im Rahmen der Abschlusszahlung entrichtete Steuerbetrag. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wird. |
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel, `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | Der für die Bestellsummen verwendete Währungscode nach ISO 4217. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.currencyCode` | Der für die Versandsumme verwendete Währungscode nach ISO 4217. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `commerce.billing.address` | Postadresse der Rechnungsstellung. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Informationen auf Straßenebene. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.id` | Die Zeileneintrag-ID für diesen Produkteintrag. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |

### orderInvoiced

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Händler eine Rechnung zur Zahlungsaufforderung einreicht. | `commerce.backofficeOrderInvoiced` |

#### Von orderInvoiced erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.priceTotal` | Der Gesamtpreis dieser Bestellung nach Anwendung aller Rabatte und Steuern. |
| `commerce.order.currencyCode` | Der für die Bestellsummen verwendete Währungscode nach ISO 4217. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Zählte, zulässige benutzerdefinierte Werte. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.id` | Die Zeileneintrag-ID für diesen Produkteintrag. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderItemsShipped

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Bestellung versandt wird. | `commerce.backofficeOrderItemsShipped` |

#### Von orderItemsShipped erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diesen Zahlungsvorgang. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Zählte, zulässige benutzerdefinierte Werte. |
| `commerce.order.payments.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.priceTotal` | Der Gesamtpreis dieser Bestellung nach Anwendung aller Rabatte und Steuern. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.address` | Die physische Lieferadresse. |
| `commerce.shipping.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `commerce.shipping.address.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `commerce.shipping.address.city` | Der Name der Stadt. |
| `commerce.shipping.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.shipping.address.postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `commerce.shipping.address.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `commerce.shipping.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.shipping.trackingNumber` | Die vom Versandunternehmen für die Lieferung eines Bestellartikels angegebene Trackingnummer. |
| `commerce.shipping.trackingURL` | Die URL zur Verfolgung des Versandstatus eines Bestellartikels. |
| `commerce.shipping.shipDate` | Das Datum, an dem ein oder mehrere Artikel aus einer Bestellung versandt werden. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `commerce.billing.address` | Postadresse der Rechnungsstellung. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Informationen auf Straßenebene. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderCancelled

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Bestellung abbricht. | `commerce.backofficeOrderCancelled` |

#### Von orderCancelled erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.order.cancelDate` | Datum und Uhrzeit der Stornierung einer Bestellung durch einen Käufer. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |

### orderLineItemRefund

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer für einen zurückgegebenen Artikel zurückerstattet wird. | `commerce.backofficeCreditMemoIssued` |

#### Von orderLineItemRefund erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.lastUpdatedDate` | Der Zeitpunkt, zu dem ein bestimmter Bestelldatensatz zuletzt im Commerce-System aktualisiert wird. |
| `commerce.order.purchaseOrderNumber` | Vom Käufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. |
| `commerce.refunds` | Die Liste der Erstattungen für diese Bestellung. |
| `commerce.refunds.transactionID` | Eindeutige Kennung für diese Erstattung. |
| `commerce.refunds.refundAmount` | Der Wert der Erstattung. |
| `commerce.refunds.refundPaymentType` | Die Zahlungsmethode für diese Bestellung. Zählte, zulässige benutzerdefinierte Werte. |
| `commerce.refunds.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |

### orderItemsReturnInitiated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer die Rückgabe eines Elements anfordert. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Von orderItemsReturnInitiated erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.returns` | Informationen zur RMA (Return Merchandise Authorization) für diese Bestellung. |
| `commerce.order.returns.returnID` | Die eindeutige Kennung für diese RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | Der Status der RMA (Authorization of Return Merchandise), z. B. &quot;Ausstehend&quot;, &quot;Geschlossen&quot;usw. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.returnItem` | Informationen zur RMA (Return Merchandise Authorization) für dieses Element. |
| `productListItems.returnItem.returnStatus` | Der Status des zurückgegebenen Elements, z. B. &quot;Ausstehend&quot;, &quot;Genehmigt&quot;usw. |
| `productListItems.returnItem.returnReason` | Der Grund, warum eine Rückgabe für dieses Element angefordert wird. |
| `productListItems.returnItem.returnItemCondition` | Die Bedingung des Elements, für das die Rückgabe angefordert wird. |
| `productListItems.returnItem.returnResolution` | Die angeforderte Lösung des zurückgegebenen Artikels, z. B. Rückerstattung, Exchange usw. |
| `productListItems.returnItem.returnQuantityRequested` | Die Nummer dieses Artikels, die der Käufer zur Rückgabe angefordert hat. |
| `productListItems.returnItem.returnQuantityAuthorized` | Die Nummer dieses Elements, das zurückgegeben werden darf. |
| `productListItems.returnItem.eturnQuantityReceived` | Die Anzahl der empfangenen zurückgegebenen Elemente. |
| `productListItems.returnItem.returnQuantityApproved` | Die Nummer dieses Elements mit der Rückgabe ist vollständig abgeschlossen und genehmigt. |

### orderItemReturnCompleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Artikel abgeschlossen ist, den ein Käufer zurückgeben möchte. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Von orderItemReturnCompleted erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.returns` | Informationen zur RMA (Return Merchandise Authorization) für diese Bestellung. |
| `commerce.order.returns.returnID` | Die eindeutige Kennung für diese RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | Der Status der RMA (Authorization of Return Merchandise), z. B. &quot;Ausstehend&quot;, &quot;Geschlossen&quot;usw. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
| `productListItems.returnItem` | Informationen zur RMA (Return Merchandise Authorization) für dieses Element. |
| `productListItems.returnItem.returnStatus` | Der Status des zurückgegebenen Elements, z. B. &quot;Ausstehend&quot;, &quot;Genehmigt&quot;usw. |
| `productListItems.returnItem.returnReason` | Der Grund, warum eine Rückgabe für dieses Element angefordert wird. |
| `productListItems.returnItem.returnItemCondition` | Die Bedingung des Elements, für das die Rückgabe angefordert wird. |
| `productListItems.returnItem.returnResolution` | Die angeforderte Lösung des zurückgegebenen Artikels, z. B. Rückerstattung, Exchange usw. |
| `productListItems.returnItem.returnQuantityRequested` | Die Nummer dieses Artikels, die der Käufer zur Rückgabe angefordert hat. |
| `productListItems.returnItem.returnQuantityAuthorized` | Die Nummer dieses Elements, das zurückgegeben werden darf. |
| `productListItems.returnItem.eturnQuantityReceived` | Die Anzahl der empfangenen zurückgegebenen Elemente. |
| `productListItems.returnItem.returnQuantityApproved` | Die Nummer dieses Elements mit der Rückgabe ist vollständig abgeschlossen und genehmigt. |

### orderShippingCompleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn eine Sendung abgeschlossen ist. | `commerce.backofficeOrderShipmentCompleted` |

#### Von orderShippingCompleted erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `commerce.order` | Enthält Informationen zur Bestellung. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diesen Zahlungsvorgang. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Zählte, zulässige benutzerdefinierte Werte. |
| `commerce.order.payments.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer im Rahmen der Abschlusszahlung entrichtete Steuerbetrag. |
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |
| `commerce.shipping.shipDate` | Das Datum, an dem ein oder mehrere Artikel aus einer Bestellung versandt werden. |
| `commerce.shipping.address` | Die physische Lieferadresse. |
| `commerce.shipping.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `commerce.shipping.address.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `commerce.shipping.address.city` | Der Name der Stadt. |
| `commerce.shipping.address.state` | Der Name des Staates. Dies ist ein Freiformfeld. |
| `commerce.shipping.address.postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `commerce.shipping.address.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `commerce.billing.address` | Postadresse der Rechnungsstellung. |
| `commerce.billing.address.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname |
| `commerce.billing.address.street2` | Zusätzliches Feld für Informationen auf Straßenebene. |
| `commerce.billing.address.city` | Der Name der Stadt. |
| `commerce.billing.address.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `commerce.billing.address.postalCode` | Die Postleitzahl des Ortes. Postleitzahlen sind nicht für alle Länder verfügbar. In einigen Ländern wird dies nur einen Teil der Postleitzahl enthalten. |
| `commerce.billing.address.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `productListItems` | Ein Array von Produkten in der Reihenfolge. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Die [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) verwendeter Währungscode, z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |
| `productListItems.categories` | Enthält Informationen zur Kategorie eines Produkts. |
| `productListItems.categories.id` | Die eindeutige Kennung der Kategorie. |
| `productListItems.categories.name` | Der Name der Kategorie. |
| `productListItems.categories.path` | Der Pfad zur Kategorie. |
