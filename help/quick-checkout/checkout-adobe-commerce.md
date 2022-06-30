---
title: '"Checkout-Fluss"'
description: '"Überblick über die [!DNL Quick Checkout] Fluss für einen Adobe Commerce-Benutzer."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Ein bestehender Adobe Commerce-Benutzer: Funktionsweise

Ein bestehender Adobe Commerce-Benutzer kann gespeicherte Versand- und Zahlungsdetails auswählen, wenn er eine Bestellung bei der [!DNL Quick Checkout] für ein schnelleres Checkout-Erlebnis.

Wenn ein Käufer seine E-Mail-Adresse beim Checkout eingibt, wird die [!DNL Quick Checkout] validiert es und findet ein vorhandenes [!DNL Bolt] -Konto.

## Angemeldet [!DNL Bolt] Konto mit einem Adobe Commerce-Benutzer

Wenn eine [!DNL Bolt] -Konto gefunden werden, setzen die Käufer mit ihrer [!DNL Quick Checkout] nahtloses Checkout-Erlebnis:

1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse des Kontos oder Mobilgerät, je nach [Benutzereinstellungen in der [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Nach der Anmeldung bei [!DNL Bolt] -Konto, werden die Details automatisch hinzugefügt:

   - Versandinformationen
   - Zahlungsmethode

1. Bestellung aufgeben.

Wenn Sie Probleme haben, wenn Sie eine Bestellung als bestehenden Adobe Commerce-Benutzer aufgeben, lesen Sie den Abschnitt [Fehlerbehebung bei Problemen mit der Schnellüberprüfung](https://support.magento.com/hc/en-us/articles/6909450342541) Artikel im Adobe Commerce Help Center.

## Neu [!DNL Bolt] account

Wenn nicht [!DNL Bolt] -Konto gefunden wird, haben die Käufer weiterhin den standardmäßigen Adobe Commerce-Checkout und der Käufer wählt alle erforderlichen Details aus den gespeicherten Informationen aus, um die Bestellung aufzugeben:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Die Option zur Registrierung in [!DNL Bolt] für schnellere Checkouts, bevor die Bestellung erscheint. Der Käufer kann den Geschäftsbedingungen zustimmen, um seine [!DNL Bolt] -Konto.

   ![Angaben [!DNL Bolt]](assets/checked-bolt.png)
