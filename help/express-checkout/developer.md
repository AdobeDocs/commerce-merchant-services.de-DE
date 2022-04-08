---
title: '''[!DNL Express Checkout] für Adobe Commerce-Entwicklerinformationen"'
description: '''[!DNL Express Checkout] Entwicklerinformationen."'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Express Checkout] Entwicklerinformationen

>[!IMPORTANT]
>
> Diese Funktion ist nur für Benutzer des Early Adopter Program (EAP) gedacht und steht noch nicht allen Kunden zur Verfügung. Derzeit auf US-Kunden beschränkt. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

Dieses Thema enthält Informationen für Entwickler, die eng mit dem Adobe Commerce- und Magento Open Source-Code zusammenarbeiten und detaillierte Informationen über die [!DNL Express Checkout] -Erweiterung.

## Erweiterungspunkte

Verwenden Sie Erweiterungspunkte, um [!DNL Express Checkout].

Durch die Verwendung von Erweiterungspunkten können Sie Anpassungen vornehmen, ohne die Kernkomponenten im Anwendungscode tatsächlich zu ändern.

### Schritt &quot;Versanddetails&quot;

Ein Erweiterungspunkt kann verwendet werden, um die automatisierte Schrittnavigation nach der Anmeldung mit [!DNL Bolt].

Sobald sich ein Käufer mit [!DNL Bolt], werden alle gültigen Informationen vorausgefüllt und zum Schritt Zahlungsdetails weitergeleitet, um die Bestellung zu tätigen. Siehe [Checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) für weitere Informationen.

Dieser Erweiterungspunkt verhindert die Navigation zu einem Zahlungsschritt und kann nützlich sein, wenn es Erweiterungen gibt, bei denen ein Käufer zusätzliche Aktionen für den Versandschritt ausführen muss. Sehen Sie sich unten ein Beispiel dazu an, wie Sie den Erweiterungspunkt mit einem Mixin verwenden können:

1. Registrieren Sie ein neues Mixin im `require-config.js` Datei in `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Erweitern Sie das Modell im `can-navigate-to-payment.js` Datei in `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> Dies ist ein Beispiel für einen Käufer in Deutschland (DE), der im Schritt Versanddetails bleiben möchte.

Überprüfen [[!DNL Bolt] Entwicklerhilfe](https://help.bolt.com/developers/) Weitere Informationen zu [!DNL Bolt] für Entwickler.
