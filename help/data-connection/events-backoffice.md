---
title: Zurück zu Office-Ereignissen
description: Erfahren Sie, welche Daten jedes Back-Office-Ereignis erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '3599'
ht-degree: 0%

---

# [!DNL Data Connection] Zurück zu Office-Ereignissen

Im Folgenden werden die Commerce-Back-Office-Ereignisse aufgelistet, die bei der Installation von [!DNL Data Connection] -Erweiterung. Die von diesen Ereignissen erfassten Daten werden an die Adobe Experience Platform gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Zusätzlich zu den Daten, die die folgenden Ereignisse erfassen, erhalten Sie auch [sonstige Daten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) bereitgestellt vom Adobe Experience Platform Web SDK.

Backoffice-Ereignisse enthalten serverseitige Daten. Diese Daten umfassen [Bestellstatus](#order-status) Informationen, z. B. ob eine Bestellung aufgegeben, storniert, zurückerstattet, versandt oder abgeschlossen wurde. Serverseitige Daten umfassen auch [Kundenprofilereignisse](#customer-profile-events-back-office) Informationen, beispielsweise ob ein Konto erstellt, aktualisiert oder gelöscht wurde.

>[!NOTE]
>
>Alle Backoffice-Ereignisse enthalten [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -Feld, das die E-Mail-Adresse des Käufers, sofern verfügbar, sowie die ECID enthält.

## Bestellstatus

Die Bestellstatusdaten zeigen eine 360-minütige Ansicht der Bestellung. Diese Ansicht hilft Händlern, bei der Entwicklung von Marketing-Kampagnen den gesamten Bestellstatus besser zu erreichen oder zu analysieren. Sie können beispielsweise Trends in bestimmten Produktkategorien erkennen, die zu unterschiedlichen Jahreszeiten gut abschneiden. Zum Beispiel Winterbekleidung, die sich in kalten Monaten besser verkauft, oder bestimmte Produktfarben, an denen die Käufer über die Jahre interessiert sind. Darüber hinaus können Sie mithilfe von Bestellstatusdaten den Kundenwert über die gesamte Lebensdauer berechnen, indem Sie die Tendenz eines Käufers verstehen, basierend auf früheren Bestellungen zu konvertieren.

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
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel: `2022-10-15T20:20:39+00:00`. |
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
| `commerce.order.createdDate` | Uhrzeit und Datum der Erstellung einer neuen Bestellung im Commerce-System. Beispiel: `2022-10-15T20:20:39+00:00`. |
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

## Kundenprofilereignisse (Back Office)

>[!NOTE]
>
>**Beta** Serverseitig generierte Profilereignisse stehen Beta-Teilnehmern zur Verfügung. Wenn Sie dem Betaprogramm beitreten möchten, senden Sie eine Anfrage an [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Von der serverseitigen Seite erfasste Profilereignisse enthalten Kontoinformationen, z. B. `accountCreated`, `accountUpdated`, und `accountDeleted`. Diese Daten werden verwendet, um wichtige Kundendetails auszufüllen, die für eine bessere Definition von Segmenten oder die Ausführung von Marketing-Kampagnen benötigt werden, z. B. das Senden von Rabattangeboten zur Anmeldung, von Kontoänderungsbestätigungen usw. Es gibt ähnliche Profilereignisse, die aus der [storefront](#customer-profile-events-storefront).

### accountCreated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu erstellen. | `userAccount.backofficeCreateProfile` |

#### Von accountCreated erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

### accountUpdated

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu bearbeiten. | `userAccount.backofficeUpdateProfile` |

#### Von accountUpdated erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |

### accountDeleted

| Beschreibung | XDM-Ereignisname |
|---|---|
| Wird ausgelöst, wenn ein Käufer versucht, ein Konto zu löschen. | `userAccount.backofficeDeleteProfile` |

#### Von accountDeleted erfasste Daten

In der folgenden Tabelle werden die für dieses Ereignis erfassten Daten beschrieben.

| Feld | Beschreibung |
|---|---|
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `commerce.commerceScope` | Gibt an, wo ein Ereignis aufgetreten ist (Store-Ansicht, Store, Website usw.). |
| `commerce.commerceScope.environmentID` | Die Umgebungs-ID. Eine 32-stellige alphanumerische ID, getrennt durch Bindestriche. |
| `commerce.commerceScope.storeCode` | Der eindeutige Store-Code. Sie können viele Geschäfte pro Website haben. |
| `commerce.commerceScope.storeViewCode` | Der eindeutige Store-Ansichtscode. Sie können viele Store-Ansichten pro Store haben. |
| `commerce.commerceScope.websiteCode` | Der eindeutige Website-Code. Sie können viele Websites in einer Umgebung haben. |
