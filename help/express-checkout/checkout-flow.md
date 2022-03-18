---
title: Checkout
description: Übersicht über die [!DNL Express Checkout] in Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
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

![Checkout](../assets/proceed-checkout.png)

1. Geben Sie bei Aufforderung eine E-Mail-Adresse ein, die mit einem Bolt-Konto verknüpft ist.
1. Geben Sie das Einmalige Passwort (OTP) ein, das an die E-Mail-Adresse oder Telefonnummer dieses Bolt-Kontos gesendet wird.
1. Nach der Anmeldung mit Ihrem Bolt-Konto werden die Details des Checkout automatisch ausgefüllt:

   - Versandinformationen
   - Zahlungsmethode

   >[!NOTE]
   >
   > Sie können Ihre vorhandenen Briefinformationen (Adresse oder Kreditkarteninformationen) auch dann verwenden, wenn Ihre Kassendetails automatisch ausgefüllt werden.

1. Bestellung aufgeben.

Die [!DNL Express Checkout] ist mit standardmäßigen zusätzlichen Adobe Commerce-Checkout-Optionen kompatibel, z. B. [Geschenkgutscheine](https://docs.magento.com/user-guide/catalog/product-gift-card.html) oder [Rabattcodes](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] Anwendungsfälle

Die [!DNL Express Checkout] ermöglicht mehrere Anwendungsfälle während eines Checkout-Vorgangs:

- Gastbenutzer mit einem registrierten Bolt-Konto.
- Gastbenutzer mit einem neuen Bolt-Konto.
- Ein bestehender Adobe Commerce-Benutzer mit/ohne registriertes Bolt-Konto.

## Gastbenutzer-Checkout: Funktionsweise

Das Erlebnis beim Auschecken von Gastgebern unterscheidet sich vom angemeldeten Erlebnis. Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Express Checkout] validiert es, um ein vorhandenes Bolt-Konto zu finden.

### Registriertes Bolt-Konto

Wenn ein Bolt-Konto gefunden wird, fahren die Käufer mit ihrer [!DNL Express Checkout] nahtloses Checkout-Erlebnis:

1. Geben Sie das Einmalige Passwort (OTP) ein, das je nach den Einstellungen des Benutzers im Bolt-Konto an die E-Mail-Adresse des jeweiligen Bolt-Kontos oder an das Mobilgerät gesendet wird.
1. Nachdem Sie sich mit Ihrem Bolt-Konto angemeldet haben, werden die Checkout-Details automatisch ausgefüllt:

   - Versandinformationen
   - Zahlungsmethode

1. Bestellung aufgeben.

>[!TIP]
>
> Gastbenutzer geben die Bestellung auf und können sich in Adobe Commerce registrieren.

### Neues Bolt-Konto

Wenn kein Bolt-Konto gefunden wird, fahren die Käufer mit ihrem standardmäßigen Adobe Commerce-Checkout fort und der Käufer stellt alle erforderlichen Details zur Bestellung bereit:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Vor der Bestellung wird in Bolt ein Kontrollkästchen für schnellere Checkouts angezeigt. Sie können den Geschäftsbedingungen zustimmen, um ihr Bolt-Konto zu erstellen.

   ![Bolt merken](../assets/checked-bolt.png)

- Der Gastbenutzer gibt die Bestellung auf und kann sich in Adobe Commerce registrieren.

## Ein bestehender Adobe Commerce-Benutzer: Funktionsweise

Ein bestehender Benutzer kann vorhandene Details auswählen, wenn der Benutzer eine Bestellung bei der [!DNL Express Checkout] für ein schnelleres Checkout-Erlebnis.

Wenn ein Käufer eine E-Mail-Adresse zum Checkout eingibt, wird die [!DNL Express Checkout] validiert es, um ein vorhandenes Bolt-Konto zu finden.

### Registriertes Bolt-Konto bei einem Adobe Commerce-Benutzer

Wenn ein Bolt-Konto gefunden wird, fahren die Käufer mit ihrem standardmäßigen Adobe Commerce-Checkout fort, und der Käufer gibt alle erforderlichen Details an und gibt dann die Bestellung auf:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode

Siehe Abschnitt [Fehlerbehebung](../express-checkout/troubleshooting.md) finden Sie weitere Informationen, wenn Sie bei der Bestellung als bestehender Adobe Commerce-Benutzer auf Probleme stoßen.

>[!NOTE]
>
> Wenn der Benutzer über ein Bolt-Konto verfügt und die E-Mail nicht als in Adobe Commerce registriert angezeigt wird, wird die OTP-Anmeldung (One-Time Password) Trigger. Siehe [eingetragenes Bolt-Konto](#registered-bolt-account) Fluss.

### Neues Bolt-Konto

Wenn kein Bolt-Konto gefunden wird, fahren die Käufer mit dem standardmäßigen Adobe Commerce-Checkout fort und der Käufer wählt alle erforderlichen Informationen aus seinen gespeicherten Informationen aus, um die Bestellung aufzugeben:

- Versand- und Rechnungsinformationen
- Versandmethode
- Überprüfungszahlungsmethode
- Vor der Bestellung wird in Bolt ein Kontrollkästchen für schnellere Checkouts angezeigt. Sie können den Geschäftsbedingungen zustimmen, um ihr Bolt-Konto zu erstellen.

   ![Bolt merken](../assets/checked-bolt.png)

## Hilfe erhalten

Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.
