---
title: "Checkout-Fluss in Adobe Commerce"
description: "Überblick über die [!DNL Quick Checkout] Fluss in Adobe Commerce."
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] Fluss

In diesem Abschnitt erhalten Sie einen Überblick über das typische Checkout-Erlebnis mit der [!DNL Quick Checkout] für die Adobe Commerce-Erweiterung.

Erfolgreich [!DNL Quick Checkout] Fluss besteht aus folgenden Schritten:

1. Öffnen Sie Ihre Storefront und fügen Sie Artikel in Ihren Warenkorb ein.
1. Fahren Sie mit dem Checkout fort.

![Checkout](assets/proceed-checkout.png)

>[!NOTE]
>
> Sie können die automatische Anmeldung für Ihren Händler aktivieren. Siehe [Thema &quot;Automatische Anmeldung aktivieren&quot; von Bolt](https://help.bolt.com/products/embedded/direct-api/auto-login/) für weitere Informationen.

1. Geben Sie bei Aufforderung eine E-Mail-Adresse ein, die mit einer [!DNL Bolt] -Konto.
1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse oder Telefonnummer des Kontos.

![OTP-Popup](assets/new-logo-otp-email.png)

1. Nach der Anmeldung bei [!DNL Bolt] -Konto, Checkout-Details werden automatisch ausgefüllt:

   - Versandinformationen
   - Zahlungsmethode

   >[!NOTE]
   >
   > Sie können Ihre vorhandenen Briefinformationen (Adresse oder Kreditkarteninformationen) auch dann verwenden, wenn Ihre Kassendetails automatisch ausgefüllt werden.

1. Bestellung aufgeben.

Die [!DNL Quick Checkout] ist mit standardmäßigen zusätzlichen Adobe Commerce-Checkout-Optionen kompatibel, z. B. [Geschenkgutscheine](https://docs.magento.com/user-guide/catalog/product-gift-card.html) oder [Rabattcodes](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] Anwendungsfälle

Die [!DNL Quick Checkout] ermöglicht mehrere Anwendungsfälle während eines Checkout-Vorgangs:

- [Gastbenutzer](../quick-checkout/checkout-bolt.md) mit registrierten oder neuen [!DNL Bolt] -Konto.
- Ein vorhandenes [Adobe Commerce-Benutzer](../quick-checkout/checkout-adobe-commerce.md) mit oder ohne Registrierung [!DNL Bolt] -Konto.

## Hilfe erhalten

Kontaktieren Sie den Adobe Commerce-Support über [Adobe Commerce Help Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) für jede Unterstützung.
