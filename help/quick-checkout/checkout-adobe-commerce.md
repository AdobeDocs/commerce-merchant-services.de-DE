---
title: "Checkout-Fluss für einen Adobe Commerce-Benutzer"
description: "Überblick über die [!DNL Quick Checkout] Fluss für einen Adobe Commerce-Benutzer."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: 1f2305df7566cd77a6be161cc9d1265c0291171c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Ein bestehender Adobe Commerce-Benutzer: Funktionsweise

Ein bestehender Adobe Commerce-Benutzer kann gespeicherte Versand- und Zahlungsdetails auswählen, wenn er eine Bestellung bei der [!DNL Quick Checkout] für ein schnelleres Checkout-Erlebnis.

Wenn ein Käufer seine E-Mail-Adresse beim Checkout eingibt, wird die [!DNL Quick Checkout] validiert es und findet ein vorhandenes [!DNL Bolt] -Konto.

## Registrierter Benutzer in Adobe Commerce und [!DNL Bolt]

Wenn ein Käufer ein registrierter Benutzer in Adobe Commerce und [!DNL Bolt] Netzen, werden beide Netze mit gespeicherten Versand- und Zahlungsdetails bereitgestellt.

Wenn eine [!DNL Bolt] -Konto beim Checkout gefunden werden, können Käufer ihre [!DNL Quick Checkout] nahtloses Checkout-Erlebnis:

1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse des Kontos oder Mobilgerät, je nach [Benutzereinstellungen in der [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP-Popup](assets/pop-up.png)

1. Nach der Anmeldung bei [!DNL Bolt] -Konto, werden die Details automatisch hinzugefügt:

   - Versandinformationen
   - Zahlungsmethode

1. Bestellung aufgeben.

>[!NOTE]
>
> Das Popup &quot;Bolt OTP&quot;wird nur angezeigt, wenn sich der Käufer auf der Checkout-Seite befindet. Der Käufer kann sich von der Anmeldung bei Bolt abmelden, indem er dieses Popup-Fenster schließt.

Wenn der Käufer vor dem Checkout bei Adobe Commerce angemeldet ist, wird die [!DNL Bolt] Das OTP-Popup wird beim Checkout nicht angezeigt, aber es erscheint eine Meldung, die den Käufer anweist, sich anzumelden, um auf seine &quot;Bolt Wallet&quot; zuzugreifen.

Wenn Sie Probleme haben, wenn Sie eine Bestellung als bestehenden Adobe Commerce-Benutzer aufgeben, lesen Sie den Abschnitt [Fehlerbehebung bei Problemen mit der Schnellüberprüfung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Artikel im Adobe Commerce Help Center.

## Neu [!DNL Bolt] account

Wenn nicht [!DNL Bolt] -Konto gefunden wird, haben die Käufer weiterhin den standardmäßigen Adobe Commerce-Checkout und der Käufer wählt alle erforderlichen Details aus den gespeicherten Informationen aus, um die Bestellung aufzugeben:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Die Option zur Registrierung in [!DNL Bolt] für schnellere Checkouts, bevor die Bestellung erscheint. Der Käufer kann den Geschäftsbedingungen zustimmen, um seine [!DNL Bolt] -Konto.

   ![Angaben [!DNL Bolt]](assets/checkbox-remember-bolt.png)
