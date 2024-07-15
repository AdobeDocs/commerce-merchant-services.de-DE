---
title: Verhaltensereignisse
description: Erfahren Sie, welche Daten von den einzelnen Verhaltensereignissen erfasst werden.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: ace61fa579404962a9ca3eb97f61ed50bc43db52
workflow-type: tm+mt
source-wordcount: '4516'
ht-degree: 0%

---

# [!DNL Data Connection] Verhaltensereignisse

Im Folgenden werden die bei der Installation der Erweiterung [!DNL Data Connection] verfügbaren Verhaltensereignisse von Commerce aufgeführt. Die von diesen Ereignissen erfassten Daten werden an die Adobe Experience Platform gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) erstellen, um zusätzliche Daten zu erfassen, die nicht standardmäßig bereitgestellt werden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [andere Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) vom Adobe Experience Platform Web SDK.

Die Verhaltensereignisse erfassen anonymisierte Verhaltensdaten von Ihren Käufern beim Durchsuchen Ihrer Site. Sie können die von diesen Ereignissen erfassten Daten verwenden, um Promotions und Kampagnen zu erstellen, die auf einen bestimmten Satz von Käufern ausgerichtet sind.

>[!NOTE]
>
>Alle Verhaltensereignisse umfassen das Feld [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , das die E-Mail-Adresse des Käufers enthält, sofern verfügbar, sowie die ECID.

## Storefront-Ereignisse

Storefront-Ereignisse erfassen Daten aus den Interaktionen der Käufer auf der Site und umfassen Ereignisse wie [`addToCart`](#addtocart), [`pageView`](#pageview), [`createAccount`](#createaccount), [`editAccount`](#editaccount), [`startCheckout`](#startcheckout), [`completeCheckout`](#completecheckout), [`signIn`](#signin), [`signOut`](#signout) usw. Storefront-Ereignisse gelten nur für einfache und konfigurierbare Produkte.

### addToCart

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Produkt zum Warenkorb hinzugefügt oder die Menge eines Produkts im Warenkorb erhöht wird. | `commerce.productListAdds` |

#### Aus addToCart erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListAdds` | Gibt an, ob einem Warenkorb ein Produkt hinzugefügt wurde. Der Wert `1` zeigt an, dass ein Produkt hinzugefügt wurde. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListOpens` | Gibt an, ob ein Warenkorb erstellt wurde. Der Wert `1` zeigt an, dass ein Warenkorb erstellt wurde. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListRemovals` | Gibt an, ob ein Produkt aus dem Warenkorb entfernt wurde. Der Wert `1` zeigt an, dass ein Produkt aus dem Warenkorb entfernt wurde. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListViews` | Gibt an, ob eine Produktliste angezeigt wurde. |
| `commerce.cart.cartID` | Die eindeutige ID, die den Warenkorb des Kunden identifiziert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `commerce.order` | Enthält Informationen zur ausstehenden Bestellung für ein oder mehrere Produkte. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wird. |
| `productListItems` | Eine Reihe von Produkten, die zum Warenkorb hinzugefügt wurden. |
| `productListItems.SKU` | Lagereinheit. Die eindeutige Kennung für das Produkt. |
| `productListItems.name` | Der Anzeigename oder für Menschen lesbare Name des Produkts. |
| `productListItems.priceTotal` | Der Gesamtpreis für den Produktzeileneintrag. |
| `productListItems.quantity` | Die Anzahl der Produkteinheiten im Warenkorb. |
| `productListItems.discountAmount` | Gibt den angewendeten Rabattbetrag an. |
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `web.webPageDetails.pageViews` | Gibt an, ob eine Seite geladen wurde. Ein `value` von `1` gibt an, dass die Seite geladen wurde. |
| `web.webPageDetails.URL` | Die normative oder übliche URL der Webseite. Dies kann die tatsächliche URL sein, die zum Erreichen der Seite verwendet wird und mit `Web Link` aufgezeichnet wird. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
| `productListItems.productImageUrl` | Hauptbild-URL des Produkts. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### completeCheckout

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn der Käufer eine Bestellung aufgibt. | `commerce.purchases` |

#### Von completeCheckout erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.purchases` | Gibt an, ob eine Bestellung akzeptiert wurde. |
| `commerce.order` | Enthält Informationen über die platzierte Bestellung für ein oder mehrere Produkte. |
| `commerce.order.purchaseID` | Vom Verkäufer für diesen Kauf oder Vertrag zugewiesene eindeutige Kennung. Es gibt keine Garantie dafür, dass die ID eindeutig ist. |
| `commerce.order.payments` | Die Liste der Zahlungen für diese Bestellung. |
| `commerce.order.payments.paymentTransactionID` | Eindeutige Kennung für diesen Zahlungsvorgang. |
| `commerce.order.payments.paymentAmount` | Der Wert der Zahlung. |
| `commerce.order.payments.paymentType` | Die Zahlungsmethode für diese Bestellung. Optionen sind: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
| `commerce.order.taxAmount` | Der vom Käufer im Rahmen der Abschlusszahlung entrichtete Steuerbetrag. |
| `commerce.order.discountAmount` | Gibt den Rabattbetrag an, der auf die gesamte Bestellung angewendet wird. |
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel: `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.shippingMethod` | Die vom Kunden gewählte Versandmethode, z. B. Standardversand, beschleunigte Auslieferung, Abholung im Geschäft usw. |
| `commerce.shipping.shippingAmount` | Der Betrag, den der Kunde für den Versand zahlen musste. |  | `shipping` | Versanddetails für ein oder mehrere Produkte. |
| `commerce.shipping.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
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

## Kundenprofilereignisse

Zu den aus der Storefront erfassten Profilereignissen gehören Kontoinformationen wie `signIn`, `signOut`, `createAccount` und `editAccount`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die für eine bessere Definition von Segmenten oder die Ausführung von Marketing-Kampagnen benötigt werden, z. B. das Senden von Rabattangeboten zur Anmeldung, von Kontoänderungsbestätigungen usw. Es gibt ähnliche Profilereignisse, die vom [Server-seitigen](events-backoffice.md#customer-profile-events) erfasst werden.

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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp (z. B. `Personal` oder `Company`). |
| `person.personalEmailID` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp (z. B. `Personal` oder `Company`). |
| `person.personalEmailID` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Ein einzelner Schauspieler, Kontakt oder Besitzer. |
| `person.accountID` | Erfasst die Benutzerkonto-ID. |
| `person.accountType` | Erfasst den Benutzerkontotyp (z. B. `Personal` oder `Company`). |
| `person.personalEmailID` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
| `personalEmail` | Erfasst Kontaktdaten - eine E-Mail und zugehörige Informationen. |
| `personalEmail.address` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.updateProfile` | Gibt an, ob ein Benutzer sein Kontoprofil aktualisiert hat. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

## Suchereignisse

Die Suchereignisse stellen Daten bereit, die für die Absicht des Käufers relevant sind. Einblicke in die Absichten eines Käufers helfen den Händlern zu sehen, wie Käufer nach Artikeln suchen, auf was sie klicken und letztlich kaufen oder aufgeben. Ein Beispiel dafür, wie Sie diese Daten verwenden können, ist, wenn Sie bestehende Käufer ansprechen möchten, die nach Ihrem Top-Produkt suchen, das Produkt jedoch nie kaufen. Sie müssen die Erweiterung [[!DNL Live Search]](../live-search/install.md) installieren, um auf diese Ereignisse zugreifen zu können.

Verwenden Sie die Felder `searchRequest.id` und `searchResponse.id`, die sowohl in den Ereignissen `searchRequestSent` als auch in den Ereignissen `searchResponseReceived` vorhanden sind, um eine Suchanfrage mit der entsprechenden Suchanfrage zu vergleichen.

### searchRequestSent

| Beschreibung | XDM-Ereignisname |
|---|---|
| Ausgelöst durch die folgenden Ereignisse im Popup &quot;Suche beim Eingeben&quot;:<br><br>Enter, Klicken Sie auf _Alle anzeigen_<br><br> ausgelöst durch die folgenden Ereignisse auf den Suchergebnisseiten:<br><br>Wählen Sie einen Filter, ändern Sie die Sortierreihenfolge (_Navigieren nach_), ändern Sie die Sortierrichtung (aufsteigend oder absteigend), ändern Sie die Anzahl der Ergebnisse pro Seite (_Anzeigen # pro Seite_), zur nächsten Seite wechseln, zur vorherigen Seite navigieren und zu einer anderen Seite navigieren | `searchRequest` |

>[!NOTE]
>
>Suchereignisse werden in einer Adobe Commerce Enterprise Edition nicht unterstützt, wenn die B2B-Erweiterung installiert ist.

#### Aus searchRequestSent erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchRequest` | Gibt an, ob eine Suchanfrage gesendet wurde. |
| `searchRequest.id` | Die eindeutige ID für diese bestimmte Suchanfrage. |
| `searchRequest.value` | Der quantifizierbare Wert des Antrags. |
| `siteSearch` | Enthält Informationen zur Suche. |
| `siteSearch.filter` | Gibt an, ob Filter angewendet wurden, um Suchergebnisse zu begrenzen. |
| `siteSearch.filter.attribute` (Filter) | Die Facette eines Elements, mit der bestimmt wird, ob es in Suchergebnisse aufgenommen werden soll. |
| `siteSearch.filter.isRange` | Wenn &quot;true&quot;, zeigen Werte Endpunkte eines akzeptablen Wertebereichs an. |
| `siteSearch.filter.value` | Attributwert, mit dem bestimmt wird, welche Elemente in den Suchergebnissen enthalten sind. |
| `siteSearch.sort` | Gibt an, wie Suchergebnisse sortiert werden sollen. |
| `siteSearch.sort.attribute` (sort) | Ein Attribut zum Sortieren von Elementen in Suchergebnissen. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

![B2B für Adobe Commerce](../assets/b2b.svg) Für B2B-Händler müssen Sie die [install](install.md#install-the-b2b-extension) -Erweiterung `experience-platform-connector-b2b` verwenden, um auf diese Ereignisse zuzugreifen.

Die B2B-Ereignisse enthalten Informationen zur [Anforderungsliste](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html), z. B. ob eine Anforderungsliste erstellt, hinzugefügt oder gelöscht wurde. Durch die Verfolgung von Ereignissen, die speziell für Anforderungslisten gelten, können Sie sehen, welche Produkte Ihre Kunden häufig kaufen, und auf dieser Grundlage Kampagnen erstellen.

### createRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Anforderungsliste erstellt. | `commerce.requisitionListOpens` |

#### Von createRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
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
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `productListItems.currencyCode` | Der verwendete Währungscode [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217), z. B. `USD` oder `EUR`. |
| `productListItems.selectedOptions` | Feld für ein konfigurierbares Produkt. |
| `productListItems.selectedOptions.attribute` | Identifiziert ein Attribut des konfigurierbaren Produkts, z. B. `size` oder `color`. |
| `productListItems.selectedOptions.value` | Identifiziert den Wert des Attributs, z. B. `small` oder `black`. |

### deleteRequisitionList

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer eine Anforderungsliste löscht. | `commerce.requisitionListDeletes` |

#### Aus deleteRequisitionList erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListDeletes` | Gibt an, dass eine Anforderungsliste gelöscht wurde. |
| `commerce.requisitionList` | Die Eigenschaften der vom Kunden erstellten Anforderungsliste. |
| `commerce.requisitionList.ID` | Eindeutige Kennung der Anforderungsliste. |
| `commerce.requisitionList.name` | Name der vom Kunden angegebenen Anforderungsliste. |
| `commerce.requisitionList.description` | Beschreibung der vom Kunden angegebenen Anforderungsliste. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
