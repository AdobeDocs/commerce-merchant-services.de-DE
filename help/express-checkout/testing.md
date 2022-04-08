---
title: Testen der [!DNL Express Checkout] für die Adobe Commerce-Erweiterung
description: Durch Tests und Validierung wird sichergestellt, dass die [!DNL Express Checkout] -Erweiterung funktioniert erwartungsgemäß.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Testen der [!DNL Express Checkout] für die Adobe Commerce-Erweiterung

>[!IMPORTANT]
>
> Diese Funktion ist nur für Benutzer des Early Adopter Program (EAP) gedacht und steht noch nicht allen Kunden zur Verfügung. Derzeit auf US-Kunden beschränkt. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

Bevor Sie die [!DNL Express Checkout] Für Adobe Commerce-Erweiterungen für Ihre Kunden wird empfohlen, Tests in einer Sandbox-Umgebung und in Ihrer Produktionsumgebung durchzuführen. Durch Tests und Validierung wird sichergestellt, dass die [!DNL Express Checkout] funktioniert erwartungsgemäß und bietet ein nahtloses Checkout-Erlebnis für Ihren Store und Ihre Kunden.

Vor der Konfiguration [!DNL Express Checkout] In Ihrem Adobe Commerce-Administrator muss eine [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} und [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} Handelskonto in Bolt.

## Test in Sandbox

Testen der [!DNL Express Checkout] in einer Sandbox-Umgebung ist ein sehr wichtiger Validierungsschritt, obwohl es sich um eine simulierte Umgebung handelt, die nur mit dem Bolt-Sandbox-Konto verbunden ist, nicht mit echten Banken oder Händlern.

### Sandbox-Konto verwenden

Wenn Sie Ihre Sandbox testen und validieren, müssen Sie eine falsche Kreditkartennummer und eine [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} Handelskonto in [!DNL Bolt], sodass Sie keine echten Gebühren für ein bestehendes Kreditkartenkonto erstellen.

## Test in Produktion

>[!NOTE]
>
> Es wird dringend empfohlen, die [!DNL Express Checkout] in einem Produktionsumfeld mit echten Kreditkarten und Banken, bevor die Erweiterung den Käufern zur Verfügung gestellt wird. Obwohl Tests in Sandboxes wichtig sind, ist der Produktionstest die am wenigsten sichere Methode, um sicherzustellen, dass sie wie erwartet funktioniert.

Es wird empfohlen, Tests in der Produktion auf zwei Arten durchzuführen:

- Wählen Sie einen Zeitpunkt aus, zu dem Sie wissen, dass die Käufer keine Bestellungen tätigen.
- Verwenden Sie einen Webstore, auf den Kunden vorübergehend nicht zugreifen können, der Ihnen aber zum Testen zur Verfügung steht.

Führen Sie Ihre Produktionstests mit echten Kreditkarten- und Bolt-Produktionskonten durch und testen Sie den gesamten Lebenszyklus eines Checkouts. Wenn Sie den gesamten Checkout-Fluss während des Tests abschließen, erhalten Sie ein klares Bild davon, wie Ihre Funktionalität funktioniert, wenn Live-Käufer sie verwenden.

Überprüfen Sie außerdem, ob die in den Bankausweisen angezeigten Informationen für die Zahlungsmethoden, die Sie in Produktionstests verwenden, korrekt und erwartet sind (einschließlich der Beschreibung Ihres Unternehmens).

## Testen der [!DNL Express Checkout] Erweiterung

Führen Sie einen erfolgreichen Checkout aus Ihrem Store durch, indem Sie die folgenden Schritte ausführen:

1. Gehen Sie in Ihre Storefront und platzieren Sie die gewünschten Artikel in Ihren Warenkorb.
1. Fahren Sie mit dem Checkout fort.
1. Geben Sie eine E-Mail-Adresse ein, die mit einer [!DNL Bolt] Konto bei Aufforderung
1. Geben Sie das einmalige Passwort (OTP) ein, das an die E-Mail-Adresse des Kontos gesendet wird.
1. Wählen Sie das Umgebungs-Dashboard aus:

   - Sandbox
   - Produktion

1. Bestellung aufgeben.

Sobald eine Bestellung aufgegeben wurde, können Sie Details zu Ihren Bestellungen in Ihrer _Raster für Bestellungen_ Ansicht:

1. Navigieren Sie zu _Vertrieb_ > _Bestellungen_.
1. Siehe Liste aller aufgegebenen Bestellungen.

Siehe [Bestellungen](https://docs.magento.com/user-guide/sales/orders.html) Thema für weitere Informationen zu Ihrer _Raster für Bestellungen_ anzeigen.
