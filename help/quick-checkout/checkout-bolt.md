---
title: '"Checkout-Fluss"'
description: '"Überblick über die [!DNL Quick Checkout] Fluss für einen Bolt-Benutzer in Adobe Commerce."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# Gastbenutzer

Das Gastcheckout-Erlebnis unterscheidet sich vom Adobe-Benutzererlebnis. Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Quick Checkout] validiert es und findet ein vorhandenes [!DNL Bolt] -Konto.

## Angemeldet [!DNL Bolt] account

Wenn eine [!DNL Bolt] -Konto gefunden werden, setzen die Käufer mit ihrer [!DNL Quick Checkout] nahtloses Checkout-Erlebnis:

1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse des Kontos oder Mobilgerät, je nach [Benutzereinstellungen in der [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Nach der Anmeldung bei [!DNL Bolt] -Konto, werden die Details automatisch hinzugefügt:

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
- Überprüfungszahlungsmethode
- Ein Kontrollkästchen erscheint bei [!DNL Bolt] für schnellere Checkouts vor der Bestellung. Der Käufer kann den Geschäftsbedingungen zustimmen, um seine [!DNL Bolt] -Konto.

   ![Angaben [!DNL Bolt]](assets/checked-bolt.png)

- Der Gastbenutzer gibt die Bestellung auf und kann sich optional in Adobe Commerce registrieren.
