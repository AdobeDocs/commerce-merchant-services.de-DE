---
title: Veranstaltungen
description: Erfahren Sie, welche Ereignisse Daten erfassen und sehen Sie sich die vollständige Schemadefinition an.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Experience Platform Connector-Ereignisse

Im Folgenden werden die [!DNL Commerce] Ereignisse verfügbar sind, wenn Sie die Experience Platform Connector-Erweiterung installieren. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Klicken Sie auf den Ereignisnamen, um die vollständige Schemadefinition anzuzeigen.

| Ereignis | Typ |
|---|---|
| [Zum Warenkorb hinzufügen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Storefront |
| [Warenkorb anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Storefront |
| [Seite anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Storefront |
| [Produkt anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Storefront |
| [Checkout starten](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Storefront |
| [Checkout abschließen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | Storefront |
| [Anmelden](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Profil |
| [Abmelden](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Profil |
| [Konto erstellen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Profil |
| [Konto bearbeiten](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Profil |

>[!NOTE]
>
> Die `Sign In`, `Sign Out`, `Create Account`und `Update Account` -Ereignisse ausgelöst werden, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.
