---
title: Veranstaltungen
description: Erfahren Sie, welche Ereignisse Daten erfassen und sehen Sie sich die vollständige Schemadefinition an.
source-git-commit: 0b349ee75fac305e6ba5ea6eb74a76eb8ce1976a
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Projekt-Beacon-Ereignisse

Im Folgenden werden die [!DNL Commerce] Ereignisse verfügbar sind, wenn Sie die Experience Platform Connector-Erweiterung installieren. Die von diesen Ereignissen erfassten Daten werden an den Adobe Experience Platform-Edge gesendet. Sie können auch [benutzerspezifische Ereignisse](custom-events.md) um zusätzliche Daten zu erfassen, die nicht vorkonfiguriert bereitgestellt wurden.

Klicken Sie auf den Ereignisnamen, um die vollständige Schemadefinition anzuzeigen.

| Ereignis | Typ |
|---|---|
| [Zum Warenkorb hinzufügen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Storefront |
| [Warenkorb anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Storefront |
| [Seite anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Storefront |
| [Produkt anzeigen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Storefront |
| [Checkout starten](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Storefront |
| Checkout abschließen | Storefront |
| [Anmelden](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Profil |
| [Abmelden](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Profil |
| [Konto erstellen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Profil |
| [Konto bearbeiten](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Profil |

>[!NOTE]
>
> Die `Sign In`, `Sign Out`, `Create Account`und `Update Account` -Ereignisse ausgelöst werden, wenn die spezifische Aktion versucht wird. Es wird nicht angegeben, dass die Aktion erfolgreich war.
