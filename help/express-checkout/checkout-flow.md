---
title: Checkout
description: Übersicht über die [!DNL Express Checkout] in Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# [!DNL Express Checkout] Fluss

>[!IMPORTANT]
>
> Diese Funktion ist nur für Benutzer des Early Adopter Program (EAP) gedacht und steht noch nicht allen Kunden zur Verfügung. Derzeit auf US-Kunden beschränkt. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

In diesem Abschnitt erhalten Sie einen Überblick über das typische Checkout-Erlebnis mit der [!DNL Express Checkout] für die Adobe Commerce-Erweiterung.

Erfolgreich [!DNL Express Checkout] Fluss besteht aus folgenden Schritten:

1. Öffnen Sie Ihre Storefront und fügen Sie Artikel in Ihren Warenkorb ein.
1. Fahren Sie mit dem Checkout fort.

![Checkout](assets/proceed-checkout.png)

1. Geben Sie bei Aufforderung eine E-Mail-Adresse ein, die mit einer [!DNL Bolt] -Konto.
1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse oder Telefonnummer des Kontos.
1. Nach der Anmeldung bei [!DNL Bolt] -Konto, Checkout-Details werden automatisch ausgefüllt:

   - Versandinformationen
   - Zahlungsmethode

   >[!NOTE]
   >
   > Sie können Ihre vorhandenen Briefinformationen (Adresse oder Kreditkarteninformationen) auch dann verwenden, wenn Ihre Kassendetails automatisch ausgefüllt werden.

1. Bestellung aufgeben.

Die [!DNL Express Checkout] ist mit standardmäßigen zusätzlichen Adobe Commerce-Checkout-Optionen kompatibel, z. B. [Geschenkgutscheine](https://docs.magento.com/user-guide/catalog/product-gift-card.html) oder [Rabattcodes](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] Anwendungsfälle

Die [!DNL Express Checkout] ermöglicht mehrere Anwendungsfälle während eines Checkout-Vorgangs:

- Gastbenutzer mit registrierten [!DNL Bolt] -Konto.
- Gastbenutzer mit neuer [!DNL Bolt] -Konto.
- Ein bestehender Adobe Commerce-Benutzer mit/ohne Registrierung [!DNL Bolt] -Konto.

## Gastbenutzer-Checkout: Funktionsweise

Das Erlebnis beim Auschecken von Gastgebern unterscheidet sich vom angemeldeten Erlebnis. Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Express Checkout] validiert sie, um eine vorhandene [!DNL Bolt] -Konto.

### Angemeldet [!DNL Bolt] account

Wenn eine [!DNL Bolt] -Konto gefunden werden, setzen die Käufer mit ihrer [!DNL Express Checkout] nahtloses Checkout-Erlebnis:

1. Geben Sie das einmalige Kennwort (OTP) ein, das an dieses gesendet wird. [!DNL Bolt] E-Mail-Adresse oder Mobilgerät des Kontos, abhängig von den Benutzereinstellungen in der [!DNL Bolt] -Konto.
1. Nach der Anmeldung bei [!DNL Bolt] -Konto, werden die Checkout-Details automatisch ausgefüllt:

   - Versandinformationen
   - Zahlungsmethode

1. Bestellung aufgeben.

>[!TIP]
>
> Gastbenutzer geben die Bestellung auf und können sich in Adobe Commerce registrieren.

### Neu [!DNL Bolt] account

Wenn nicht [!DNL Bolt] -Konto gefunden wird, haben die Käufer weiterhin den standardmäßigen Adobe Commerce-Checkout und der Käufer stellt alle erforderlichen Informationen zur Bestellung bereit:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Ein Kontrollkästchen erscheint bei [!DNL Bolt] für schnellere Checkouts vor der Bestellung. Sie können den Nutzungsbedingungen zustimmen, um ihre [!DNL Bolt] -Konto.

   ![Angaben [!DNL Bolt]](assets/checked-bolt.png)

- Der Gastbenutzer gibt die Bestellung auf und kann sich in Adobe Commerce registrieren.

## Ein bestehender Adobe Commerce-Benutzer: Funktionsweise

Ein bestehender Benutzer kann vorhandene Details auswählen, wenn der Benutzer eine Bestellung bei der [!DNL Express Checkout] für ein schnelleres Checkout-Erlebnis.

Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Express Checkout] validiert sie, um eine vorhandene [!DNL Bolt] -Konto.

### Angemeldet [!DNL Bolt] Konto mit einem Adobe Commerce-Benutzer

Wenn eine [!DNL Bolt] -Konto gefunden wird, setzen die Käufer mit dem standardmäßigen Adobe Commerce-Checkout fort und der Käufer gibt alle erforderlichen Details an und gibt dann die Bestellung auf:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode

Siehe Abschnitt [Fehlerbehebung](../express-checkout/troubleshooting.md) finden Sie weitere Informationen, wenn Sie bei der Bestellung als bestehender Adobe Commerce-Benutzer auf Probleme stoßen.

>[!NOTE]
>
> Wenn der Benutzer [!DNL Bolt] -Konto und -E-Mail werden nicht als in Adobe Commerce registriert angezeigt, sondern als Trigger für die OTP-Anmeldung (One-Time Password). Siehe [registriert [!DNL Bolt] account](#registered-bolt-account) Fluss.

### Neu [!DNL Bolt] account

Wenn nicht [!DNL Bolt] -Konto gefunden wird, haben Käufer weiterhin ihre standardmäßige Adobe Commerce-Kasse und der Käufer wählt alle erforderlichen Informationen aus den gespeicherten Informationen aus, um die Bestellung aufzugeben:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Ein Kontrollkästchen erscheint bei [!DNL Bolt] für schnellere Checkouts vor der Bestellung. Sie können den Nutzungsbedingungen zustimmen, um ihre [!DNL Bolt] -Konto.

   ![Angaben [!DNL Bolt]](assets/checked-bolt.png)

## Hilfe erhalten

Kontakt [!DNL Adobe Commerce] Engineering-Team durch Ihren zugewiesenen Slack [Adobe Beta-Programmkanal](http://adobe-beta-programs.slack.com/) für jede Unterstützung.
