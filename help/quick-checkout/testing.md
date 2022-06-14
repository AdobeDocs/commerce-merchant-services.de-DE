---
title: '"Testen der [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"'
description: '"Tests und Validierung stellen sicher, dass die [!DNL Quick Checkout] -Erweiterung funktioniert wie erwartet."'
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Testen Sie die [!DNL Quick Checkout] Erweiterung

Bevor Sie die [!DNL Quick Checkout] Für Adobe Commerce-Erweiterungen für Ihre Kunden wird empfohlen, Tests in einer Sandbox-Umgebung und in Ihrer Produktionsumgebung durchzuführen. Durch Tests und Validierung wird sichergestellt, dass die [!DNL Quick Checkout] funktioniert erwartungsgemäß und bietet ein nahtloses Checkout-Erlebnis für Ihren Store und Ihre Kunden.

Vor der Konfiguration [!DNL Quick Checkout] In Ihrem Adobe Commerce-Administrator muss die  [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} und [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} Handelskonten in [!DNL Bolt].

## Test in Sandbox

Testen der [!DNL Quick Checkout] in einer Sandbox-Umgebung ist ein sehr wichtiger Validierungsschritt, auch wenn es sich um eine simulierte Umgebung handelt, die nur mit dem [!DNL Bolt] Sandbox-Konto, nicht für echte Banken oder Händler.

### Sandbox-Konto verwenden

Wenn Sie Ihre Sandbox testen und validieren, müssen Sie eine falsche Kreditkartennummer und eine [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} Handelskonto in [!DNL Bolt], sodass Sie keine echten Gebühren für ein bestehendes Kreditkartenkonto erstellen.

## Test in Produktion

>[!NOTE]
>
> Es wird dringend empfohlen, die [!DNL Quick Checkout] in einem Produktionsumfeld mit echten Kreditkarten und Banken, bevor die Erweiterung den Käufern zur Verfügung gestellt wird. Obwohl Tests in Sandboxes wichtig sind, ist der Produktionstest die am wenigsten sichere Methode, um sicherzustellen, dass sie wie erwartet funktioniert.

Testen Sie Ihre Produktionsumgebung auf eine der beiden folgenden empfohlenen Arten:

- Wählen Sie einen Zeitpunkt aus, zu dem Sie wissen, dass die Käufer keine Bestellungen tätigen.
- Verwenden Sie einen Webstore, auf den Kunden vorübergehend nicht zugreifen können, der Ihnen aber zum Testen zur Verfügung steht.

Führen Sie Ihre Produktionstests mit echten Kreditkarten durch und [!DNL Bolt] Produktionskonten, die den gesamten Lebenszyklus eines Checkouts testen. Wenn Sie den gesamten Checkout-Fluss während des Tests abschließen, erhalten Sie ein klares Bild davon, wie Ihre Funktionalität funktioniert, wenn Live-Käufer sie verwenden.

Überprüfen Sie außerdem, ob die in den Bankausweisen angezeigten Informationen für die Zahlungsmethoden, die Sie in Produktionstests verwenden, korrekt und erwartet sind (einschließlich der Beschreibung Ihres Unternehmens).

## Testen der [!DNL Quick Checkout] Erweiterung

Führen Sie einen erfolgreichen Checkout aus Ihrem Store durch:

1. Gehen Sie in Ihre Storefront und platzieren Sie die gewünschten Artikel in Ihren Warenkorb.
2. Fahren Sie mit dem Checkout fort.
3. Geben Sie eine E-Mail-Adresse ein, die mit einer [!DNL Bolt] Konto bei Aufforderung.
4. Geben Sie das einmalige Passwort (OTP) ein, das an die E-Mail-Adresse des Kontos gesendet wird.
5. Wählen Sie das Umgebungs-Dashboard aus:

   - Sandbox
   - Produktion

6. Platzieren Sie die Bestellung.

Sobald eine Bestellung aufgegeben wurde, können Sie Details zu Ihren Bestellungen in Ihrer _Raster für Bestellungen_ Ansicht:

1. Navigieren Sie zu _Vertrieb_ > _Bestellungen_.
1. Siehe Liste aller aufgegebenen Bestellungen.

Siehe [Bestellungen](https://docs.magento.com/user-guide/sales/orders.html) Thema für weitere Informationen zu Ihrer _Raster für Bestellungen_ anzeigen.