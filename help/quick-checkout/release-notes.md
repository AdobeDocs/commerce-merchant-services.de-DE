---
title: '''[!DNL Quick Checkout] Versionshinweise'''
description: Informationen zu allen [!DNL Quick Checkout] veröffentlicht.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 27e91a640999cf83a0f0d6701e616f7ceecde12d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Quick Checkout] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Siehe [Bevorstehende Versionen](https://devdocs.magento.com/release/) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://devdocs.magento.com/release/availability.html) in der Entwicklerdokumentation , um mehr über die Produktkompatibilität zu erfahren.

## v1.1.0

_12. August 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-375 --> Verbesserungen der Benutzererfahrung in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) enthalten jetzt nur die Parameter, die sichtbar und validiert sind, wenn die Erweiterung aktiviert ist.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-349 --> Kompatibilitätsverbesserungen für bestehende Versandadressen mit der Bolt-Brieftasche.

## v1.0.0

_9. August 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-341 --> Version der allgemeinen Verfügbarkeit -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.1 bis 2.4.4 kompatibel.

![Neu](../assets/new.svg)<!-- Issue BOLT-340 --> Die [!DNL Quick Checkout] für Adobe Commerce kann entweder für Adobe Commerce installiert werden [zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce bietet eine optimierte Storefront, die eine [Kasse mit einem Klick](overview.md) ohne für den Verbraucher erforderliche Füllfelder.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce erkennt jeden Käufer im Netzwerk automatisch für [Käufe mit einem Klick](checkout-flow.md) direkt auf Ihrer Site.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce ermöglicht es einem Kunden, gleichzeitig [bei Adobe Commerce und Bolt angemeldet sein](checkout-flow.md/#quick-checkout-use-cases) bessere `one-click checkout` Erlebnis.

![Neu](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] für Adobe Commerce unterstützt eine [Sandbox-Konto](testing.md#testing-in-sandbox) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue BOLT-780 --> Ihre Kunden können über die [[!DNL Quick Checkout]](checkout-page.md) oder über eine [manuelle Auftragserstellung](create-order-admin.md).

![Neu](../assets/new.svg)<!-- Issue BOLT-666 --> Merchants können die [!DNL Quick Checkout] mit grundlegenden Zahlungsaktionen wie [`Authorize and Capture` oder `Authorize` ](onboarding.md#complete-admin-configuration)oder zwischen Sandbox- und Produktionsumgebungen wechseln.

![Neu](../assets/new.svg)<!-- Issue BOLT-288 --> Benutzerdefiniert [Lebensdauer der Benutzersitzung](user-session-lifetime.md) für [!DNL Quick Checkout] für Adobe Commerce.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-375 --> Verbesserungen der Benutzererfahrung in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) ermöglicht Ihnen, Ihre Konfiguration zu speichern, wenn alle erforderlichen Parameter angegeben sind.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue BOLT-342 --> Häufig [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/6909450342541) Probleme während der Installation [!DNL Quick Checkout].
