---
title: "Checkout-Fluss eines Bolt-Benutzers in Adobe Commerce"
description: Übersicht über die [!DNL Quick Checkout] Fluss für einen Bolt-Benutzer in Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
feature: Checkout, Services, Storefront
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Gastbenutzer

Das Gastcheckout-Erlebnis unterscheidet sich vom Adobe-Benutzererlebnis. Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Quick Checkout] validiert es und findet ein vorhandenes [!DNL Bolt] -Konto.

>[!WARNING]
>
> Die [!DNL In-Store Pickup] (ISPU)-Funktionalität wird nicht unterstützt, wenn die [!DNL Quick Checkout] aktiviert ist.

## Angemeldet [!DNL Bolt] account

Wenn eine [!DNL Bolt] -Konto gefunden werden, setzen die Käufer mit ihrer [!DNL Quick Checkout] nahtloses Auschecken:

1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse des Kontos oder Mobilgerät, je nach [Benutzereinstellungen in der [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP-Popup](assets/new-logo-otp-email.png){width="300" zoomable="yes"}

1. Nach der Anmeldung bei Ihrem [!DNL Bolt] -Konto hinzugefügt werden, werden die Details automatisch hinzugefügt:

   - Versandinformationen
   - Zahlungsmethode

1. Bestellung aufgeben.

>[!TIP]
>
> Der Gastbenutzer gibt die Bestellung auf und kann sich optional in Adobe Commerce registrieren.

## Neu [!DNL Bolt] account

Wenn nicht [!DNL Bolt] -Konto gefunden wird, die Käufer mit ihrem standardmäßigen Adobe Commerce-Checkout fortfahren und der Käufer alle erforderlichen Informationen für die Bestellung bereitstellt:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlmethode
- Es wird ein Kontrollkästchen angezeigt, in dem Sie sich registrieren [!DNL Bolt] für schnellere Checkouts vor der Bestellung. Der Käufer kann den Geschäftsbedingungen zustimmen, um seine [!DNL Bolt] -Konto.
- Der Gastbenutzer gibt die Bestellung auf und kann sich optional in Adobe Commerce registrieren.
