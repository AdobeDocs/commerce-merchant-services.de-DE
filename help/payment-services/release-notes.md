---
title: "[!DNL Payment Services] Versionshinweise"
description: Informationen zu allen [!DNL Payment Services] Versionen finden Sie in den Versionshinweisen .
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 153e6a82134a34737529f4e1a135eb7803b20e05
workflow-type: tm+mt
source-wordcount: '2968'
ht-degree: 0%

---


# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Korrektur des Problems](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen, die außerhalb der regulären Version der Funktionsveröffentlichung veröffentlicht wurden, finden Sie in den Abschnitten _Gehostete Dienstaktualisierungen_ .

Weitere Informationen zu künftigen Versionen, zur Produktunterstützung und dazu, welche Adobe Commerce-Versionen die Erweiterung [!DNL Payment Services] unterstützen, finden Sie in den Abschnitten zum Adobe Commerce [Veröffentlichungsplan](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) und zur [Produktverfügbarkeit](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) .

## Aktualisierungen gehosteter Dienste

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Funktionsveröffentlichungen für den gehosteten Dienst veröffentlicht wurden.

+++Hosting-Dienstaktualisierungen

_30. August 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5658 --> Jetzt können Händler Transaktionen anhand der Zahlungsdetails im [Transaktionsbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) filtern, um detailliertere und genauere Daten zu Zahlungsmethoden zu erhalten.

_15. Juli 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5571 --> Jetzt können Händler Transaktionen nach der Commerce-Kunden-E-Mail im Bericht [Transaktionen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) filtern. Geben Sie die E-Mail des Kunden ein, um Transaktionen nach dieser E-Mail zu filtern.

_9. Juli 2024_

![Neues Problem](../assets/new.svg)<!-- Issue PAY-5488 --> Jetzt können Händler die Commerce-Kunden-ID als Spalte im [Transaktionsbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) anzeigen, um Transaktionen zu identifizieren, die ein bestimmter Kunde platziert hat. Darüber hinaus können Händler den Transaktionsbericht nach dieser Commerce-Kunden-ID nach zugehörigen Bestellungen filtern.

_5. März 2024_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-5252 --> Jetzt können Händler Daten aus den Dashboard-Rastern kopieren, indem sie den Inhalt einer einzelnen Zelle auswählen.

_10. Oktober 2023_

![Neues Problem](../assets/fix.svg)<!-- Issue PAY-4888 --> Jetzt können Händler Kreditkarten- und Debitkartentransaktionen nach den letzten vier Stellen der Kartennummer im [Transaktionsbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) filtern.

_12. Juli 2023_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4587 --> Ein Problem, das in der Version [!DNL Payment Services] 2.1.0 eingeführt wurde und durch das Autorisierungslücken von früheren Erweiterungsversionen verhindert wurden, wurde jetzt behoben. Händler, die eine beliebige Version von [!DNL Payment Services] verwenden, können Autorisierungen unwirksam machen.

_9. Juni 2023_

![Neu](../assets/new.svg)<!-- Issue PAY-4288 --> Jetzt können Händler [nur _4} PayPal-Zahlungsschaltflächen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) konfigurieren - und_ nicht _die Zahlungsoption PayPal für Kreditkarten verwenden._ Auf diese Weise können Händler verschiedene Zahlungsoptionen bereitstellen, einschließlich der Zahlungsschaltflächen Venmo und PayPal, und einen vorhandenen Kreditkartenanbieter anstelle der Zahlungsoption PayPal-Kreditkarte verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-4050 --> Es wurde eine [Datenvisualisierungsansicht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view) hinzugefügt, die auf der Zahlungsdienst-Startseite für den Bericht zum Bestellzahlungsstatus angezeigt wird.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-4486--> Zuvor wurde die Schaltfläche PayPal PayLater für britische Händler nicht beim Checkout angezeigt. Dieses Problem ist gelöst.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-4485--> Visualisierungsansichten für Berichtsdaten werden jetzt auf der [!DNL Payment Services] Startseite angezeigt, wenn [!DNL Payment Services] deaktiviert ist.

_25. Januar 2023_

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-4102 --> Neue Installationen von [!DNL Payment Services] können Commerce Services nicht konfigurieren, sodass [!DNL Payment Services] nicht funktionsfähig ist. Um dieses Problem zu beheben, aktualisieren Sie Ihre [!DNL Payment Services] -Erweiterung auf Version 1.5.3.

_12. September 2022_

![Neu](../assets/new.svg)<!-- Issue PAY-3705 --> Die `increment_id` ist jetzt für die Abstimmung von Auszahlungen in externen ERP-Systemen verfügbar. Sie wird in den [`custom_id` _und den_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system) übertragen, die sowohl im PayPal-Webhook als auch in den Details zur Handelsaktivität für eine Auszahlung angezeigt werden.

_31. August 2022_

![Korrektur des Problems](../assets/fix.svg)<!-- Issue PAY-3629 --> Wenn ein neuer Händler zum ersten Mal auf die [!DNL Payment Services]-Startseite zugreift, wird die Seite jetzt sofort geladen, um den Inhalt anzuzeigen, anstatt dass eine Seitenaktualisierung erforderlich ist.

_9. August 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-3420 --> Apple-Bezahlung ist jetzt als PayPal-Smart-Schaltfläche verfügbar. Mit dieser [Zahlungsoption](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) können Kunden die Touch-ID-Funktion auf ihrem iOS- oder macOS-Gerät verwenden, um die Apple-Zahlung auszuwählen. Apple Pay verarbeitet die Zahlung mit den auf dem Gerät gespeicherten Zahlungsberechtigungen für Kredit- und Debitkarten.

_28. Juni 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-1720 --> Streitigkeiten für Store-Bestellungen sind jetzt in [dem Bestellstatusbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes) verfügbar. Sie können Streitigkeiten beilegen, indem Sie von [!DNL Payment Services] direkt zum PayPal-Abwicklungszentrum navigieren.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Verbesserungen des Benutzererlebnisses von der Startseite von [!DNL Payment Services] umfassen die Möglichkeit, eine Konfiguration auf der aktuellen Vererbungsebene zu ändern, sowie Verbesserungen bei der Anzeige der Kopfzeile und der Navigation.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Sie können jetzt Warnungen sehen, wenn Sie vom Sandbox-Modus zum Produktionsmodus wechseln und versuchen, von einer Ansicht mit nicht gespeicherten Aktualisierungen weg zu navigieren.

![Neu](../assets/new.svg)<!-- Issue PAY-2761 --> Sie können jetzt die Daten anpassen, die im Bericht [Bestellzahlstatus-Bericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) und im Bericht [Auszahlungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) angezeigt werden, indem Sie Spalten mithilfe des Steuerelements für Spalteneinstellungen ein- oder ausblenden.

+++

## v2.8.0

_13. September 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-5499 --> [!DNL Payment Services] unterstützt jetzt das Senden von Trackingnummerninformationen an PayPal, wenn in Adobe Commerce eine [Trackingnummer eingegeben wird](track-shipment.md).

![Fix](../assets/fix.svg)<!-- PAY-5626 --> [!DNL Payment Services] hat den Anforderungsprozess für die Händlerregistrierung optimiert, wenn Kunden die Commerce-Checkout-Seite besuchen. Zuvor wurden für jede Zahlungsmethode (gehostete Felder, Google-Bezahlung, Apple-Bezahlung und intelligente Schaltflächen) separate Anfragen gestellt. Diese Verbesserung reduziert die Anzahl der Aufrufe und verbessert die Leistung und Effizienz während des Checkout-Prozesses.

![Fix](../assets/fix.svg)<!-- PAY-5645 --> [!DNL Payment Services] verhindert nun, dass das Popup-Fenster für PayPal-/Google-Bezahlung geöffnet wird, wenn der Käufer nicht zugestimmt hat, dass der Händler benutzerdefinierte Geschäftsbedingungen auf der Checkout-Seite erstellt hat.

![Fix](../assets/fix.svg)<!-- PAY-5648 -->  [!DNL Payment Services] hat ein Problem im Zusammenhang mit der Aufschlüsselung des Zeileneintrags der Steuern im PayPal-Portal behoben. Wenn die Versandkosten einer Bestellung mit einer Steuer verbunden sind, wird die Steuer als Teil der Versandkosten einbezogen und auf diese Weise in den im PayPal-Portal angezeigten Zeileneinträgen angezeigt.

## v2.7.0

_2. August 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-4844 --> [!DNL Payment Services] unterstützt jetzt [Zeilenelementdaten auf Bestellebene](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/manage/line-items). Diese Funktion ermöglicht es Händlern, detaillierte Informationen zu den Artikeln in einer Bestellung anzuzeigen, wie Produktdetails, Menge und Preis (einschließlich Umsatzsteuer, Rabatte und andere relevante Informationen).

![Neu](../assets/new.svg)<!-- PAY-5380 --> [!DNL Payment Services] verbessert die [Konfiguration im Admin](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/configure/configure-admin#general-configuration) -Erlebnis für Händler und ermöglicht so einen einfacheren und intuitiveren Onboarding-Prozess. Mit dieser Funktion können Händler ihre [!DNL Payment Services] -IDs zurücksetzen.

![Neu](../assets/new.svg)<!-- PAY-5255 --> [!DNL Payment Services] enthält eine [Benachrichtigung über Zahlungsfehler](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-payment-failed-emails). Diese Funktion bietet nahezu in Echtzeit Benachrichtigungen über Zahlungsausfälle an Händler, sodass Bestellungen gespeichert werden können, indem man sich an den Käufer wendet und die Problemlösung potenziell verbessert.

![Korrektur](../assets/fix.svg)<!-- PAY-5469 --> Es wurde ein Problem behoben, bei dem das Popup-Fenster für die Bezahlung mit Google von Safari blockiert wurde **.** Käufer können jetzt ihre Google Pay-Payment-Transaktionen in Safari abschließen.

![Korrektur](../assets/fix.svg)<!-- PAY-5492 --> Korrektur eines Problems, das auftrat, wenn ein Händler der Checkout-Seite benutzerdefinierte Geschäftsbedingungen hinzufügte. Während eines [Express-Checkouts](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options#standard-vs-advanced-payments-experience) kann ein Käufer jetzt diese Bedingungen akzeptieren, um den Checkout ohne Probleme abzuschließen.

![Korrektur](../assets/fix.svg)<!-- PAY-5532 --> Verbesserte In-Store-Abruf-Funktionen (ISPU) mit **InstantPurchase**. **ISPU-Bereitstellungsmethoden** werden nicht mehr angezeigt, wenn ein Käufer eine Bestellung mit **InstantPurchase** aufgibt.

![Korrektur](../assets/fix.svg)<!-- PAY-5606 --> Korrektur eines Problems innerhalb der Länderauswahl auf der **Konfigurationsseite** , das auftrat, wenn das Land des Händlers auf **Deutschland** festgelegt war.

## v2.6.0

_4. Juni 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-4877 --> [!DNL Payment Services] unterstützt jetzt [L2/L3-Preisfunktionen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). Diese Funktion ist nur für [!DNL Payment Services] -Kunden mit aktiviertem IC+-Preis verfügbar. Wenn Sie die L2/L3-Verarbeitungsdaten für [!DNL Payment Services] verwenden möchten, wenden Sie sich an Ihren [!DNL Payment Services] -Kundenbetreuer.

Mit der ![Korrektur](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] können Sie Apple Pay direkt aus der Erweiterung aktivieren, ohne die [Domänenzuordnungsdatei](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) herunterzuladen und zu hosten.

## v2.5.0

_23. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] unterstützt jetzt die [Adobe Commerce-Richtlinien für den `--db-prefix` -Parameter](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) für Adobe Commerce-Versionen 2.4.7 und höher.

## v2.4.3

_16. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- Issue PAY-5106 --> Es wurde ein Problem behoben, durch das die Bestellsummen beim Checkout zwischen PayPal und Adobe Commerce fälschlicherweise ausgefüllt wurden. Jetzt können Merchants sicherstellen, dass die Bestellsummen bei der Bestellung korrekt sind.

## v2.4.2

_11. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue xxx --> Unterstützung für Adobe Commerce 2.4.7 hinzugefügt.

## v2.4.1

_4. April 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- PAY-5322 --> Korrektur eines PCI-Kompatibilitätsproblems mit neueren Adobe Commerce-Versionen. Jetzt ist [!DNL Payment Services] an die Checkout-Anforderungen in Adobe Commerce als Zahlungsoption angepasst.

![Korrektur](../assets/fix.svg)<!-- PAY-5323 --> PayLater und Venmo werden in Adobe Commerce korrekt angezeigt. Es wurde ein Fehler behoben, durch den der Admin die Umschalter-Optionen &quot;PayLater&quot;und &quot;Venmo&quot;nicht anzeigen konnte.

## v2.4.0

_20. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-4868 --> Händler können Google-Bezahlung erfolgreich [über das gesamte Kauferlebnis hinweg konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html), ähnlich wie andere Zahlungsschaltflächen in [!DNL Payment Services] über den Administrator.

![Neu](../assets/new.svg)<!-- PAY-4381 --> [Zahlungsdienste unterstützen Google Pay über GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/), sodass Händler Headless Commerce-Erlebnisse mit der Zahlungsmethode Google Pay haben können.

![Neu](../assets/new.svg)<!-- PAY-4878 --> Jetzt ist die grundlegende Checkout-Funktion [!DNL Payment Services] für Adobe Commerce- und Magento Open Source-Händler gebündelt.[!DNL Payment Services] kann jetzt Händler mit Unternehmen in 200 Ländern weltweit unterstützen.[!DNL Payment Services] Der grundlegende Checkout bietet Debit-/Credit-, PayPal-, Venmo- (sofern verfügbar) und PayLater-Optionen (sofern verfügbar) in einem Self-Service-Onboarding.

![Korrektur](../assets/fix.svg)<!-- PAY-5291 --> Der Empfang einer Zahlungsbestätigung für einige Transaktionen kann sich verzögern. In diesem Fall können Händler jetzt einen aktualisierten Zahlungsstatus für eine Bestellung erhalten. [Zahlungsdienste erkennen den ausstehenden Status eines Zahlungsvorgangs](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) in einer Reihenfolge, indem sie ausstehende Transaktionen aufdecken und diese Transaktionen proaktiv überwachen und aktualisieren, wenn der Status &quot;Ausstehend&quot;erfasst wurde.

## v2.3.4

_1. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-5244 --> Die Kompatibilität mit asynchronen Checkouts wurde korrigiert.

![Korrektur](../assets/fix.svg)<!-- PAY-5253 --> Es wurde ein Fehler behoben, bei dem ein Vault-Token, das nicht zu [!DNL Payment Services] gehört, nicht gelöscht werden konnte.

## v2.3.3

_14. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-5048 --> Zusätzliche Unterstützung für PHP 8.3

![Korrektur](../assets/fix.svg)<!-- PAY-5048 --> Korrektur eines Fehlers mit der `is_deleted` -Markierung. Jetzt schlagen die Bestellungen nicht aufgrund des `Rejected` -Status fehl, der von der Erweiterung gesendet wurde.

## v2.3.2

_26. Januar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- PAY-5183 --> Korrektur von REST/GraphQL-Leistungsproblemen. Jetzt wird die Kreditkartenschaltfläche gerendert, wenn sie über die API abgerufen wird.

## v2.3.1

_7. Dezember 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-5047 --> Die Marken- oder Zahlungsmethode der Kredit-/Debitkarte sind jetzt an den folgenden Orten verfügbar:

- die Kundenbestellseite auf der Storefront
- die an den Käufer gesendete Bestätigungs-E-Mail
- über die Ansicht [Bestelldetails](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) in Commerce Admin.

## v2.3.0

_1. Dezember 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-4381 --> [Zahlungsdienste unterstützen jetzt die GraphQL-Integration](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Mit GraphQL-Unterstützung für PayPal-Zahlungsschaltflächen, gehostete Felder und Apple Pay unterstützt[!DNL Payment Services] jetzt ein Headless-Commerce-Setup.

## v2.2.1

_27. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-4870 --> Korrektur des Fehlers, der beim Senden der Erweiterungsversion mit der neuesten Version das neue Kopfzeilenattribut fälschlicherweise in Storefront ausgefüllt hat. Mit der Version `1.3.0` des Commerce Services-Connectors konnten Sie bisher die Erweiterung `User-Agent header` nicht aus der Erweiterung [!DNL Payment Services] erweitern.

## v2.2.0

_30. August 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- PAY-4638 --> Eine [Integration mit Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html) wurde hinzugefügt, die automatisierte Betrugsschutzdienste bietet.

![Neu](../assets/new.svg)<!-- PAY-3981 --> [Förderte Apple-Zahlung auf eine separate Zahlungsoption](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button) außerhalb der PayPal-Zahlungsschaltflächen, um die Sichtbarkeit der Zahlungsoption für die Käufer zu erhöhen und es den Händlern zu ermöglichen, die Platzierung und Formatierung von Apple-Zahlungen zu steuern.

![Neu](../assets/new.svg)<!-- PAY-4002 --> Die Benutzererfahrung beim Checkout von Kreditkartenfeldern wurde verbessert, einschließlich Stilverbesserungen wie das Hinzufügen von Zahlungssymbolen, um die kognitive Belastung der Kunden zu verringern und Konversionen zu erhöhen.

![Neu](../assets/new.svg)<!-- PAY-4002 --> Es wurde eine Funktion hinzugefügt, die es Händlern ermöglicht, die Reihenfolge ihrer Zahlungsoptionen zu sortieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons), um bestimmte Zahlungsoptionen priorisieren zu können. [ Diese Funktion fördert eine höhere Konversationsrate beim Checkout.

![Neu](../assets/new.svg)<!-- PAY-4035 --> Händler können jetzt effizient den Zustand ihrer Geschäfte überwachen und Transaktionsprobleme mithilfe des neuen [Transaktionsberichts](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) identifizieren, der auf der Homepage von [!DNL Payment Services] Admin verfügbar ist. Der Bericht enthält auch Daten zu den Zulassungsraten von Transaktionen und zu negativen Transaktionstrends.

## v2.1.0

_9. Juni 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue xxx --> Unterstützung für Adobe Commerce 2.4.7-beta1 hinzugefügt.

![Neu](../assets/new.svg)<!-- Issue xxx --> [Verfügbarkeit in den folgenden Ländern und Währungen hinzugefügt](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australien, Frankreich, Vereinigtes Königreich.

![Neu](../assets/new.svg)<!-- Issue PAY-4296 --> Es wurden [erweiterte Ressourcen für Admin-Rollen hinzugefügt](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles), um sicherzustellen, dass Admin-Benutzer Bestellungen für Kunden erstellen und verwalten können und [!DNL Payment Services] im Menü &quot;Verkauf&quot;sehen können.

![Neu](../assets/new.svg)<!-- Issue PAY-4236 --> [Die automatische Aufhebung für Bestellungen, die beim Checkout Fehler verursachen, wurde hinzugefügt.](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error)

![Neu](../assets/new.svg)<!-- Issue PAY-4183 --> Die Funktion wurde erstellt, um [ die Schaltfläche mit der Zahlungsoption für Kredit-/Debitkarten](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) auf der Checkout-Seite anzuzeigen.

## v2.0.0

_10. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-4152 --> Unterstützung für PHP 8.2 und Adobe Commerce 2.4.6 hinzugefügt. Nicht kompatibel mit PHP 7.x.

## v1.6.1

_10. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- Issue PAY-4226 --> Es wurde ein Problem behoben, das verhinderte, dass neue [!DNL Payment Services] Händler den Checkout im Admin verwenden konnten.[!DNL Payment Services] hat zuvor die Commerce-Kunden-ID verwendet, die für neue Kunden nicht vorhanden ist.

![Korrektur](../assets/fix.svg)<!-- Issue PAY-4205 --> Korrektur eines Fehlers, der dazu führte, dass der angegebene Versandadressenstatus beim Checkout mit der Option [PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons) durch den Status in den Standardsteuereinstellungen ersetzt wurde. Jetzt können Kunden ihre Bestellungen in einen anderen Staat verschicken lassen als den, der in den Steuereinstellungen des Händlers als Standard konfiguriert wurde.

![Korrektur](../assets/fix.svg)<!-- Issue PAY-4202 --> Korrektur eines Fehlers, der Kunden daran hinderte, Kartenwerte zu verwenden, um einen Kauf abzuschließen oder eine ungültige Zahlungsmethode für einen Store zu löschen [, indem die `Authorize and Capture` Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method) verwendet wurde. Zuvor trat der Fehler &quot;Provider Vault ID not found&quot;auf, wenn der Kunde versuchte, seine ausgefüllten Kreditkarten zu verwenden oder zu ändern.

## v1.6.0

_17. Februar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-3540 --> [PCI 3DS-Compliance-Funktion für Händler, die in der Europäischen Union (EU) und Großbritannien handeln](security.md#3ds) hinzugefügt. Diese zusätzliche Sicherheitsebene, die die Authentifizierung von Käufern bei ihrem Kreditkartenaussteller erfordert, trägt zur Verhinderung von Online-Betrug bei und ist als Teil der EU-Vorschriften zur Einhaltung der Vorschriften erforderlich.

![Neu](../assets/new.svg)<!-- Issue PAY-3609 --> Die Fähigkeit [zur Aktivierung der Kartenauswertung im Admin](vaulting.md#use-vaulting-in-the-admin) wurde hinzugefügt. Auf diese Weise können Händler mit ihren bewährten Zahlungsmethoden eine Bestellung für Kunden in der Admin erstellen.

## v1.5.4

_29. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-4110 --> Fehlerkorrektur - Käufer können jetzt eine Bestellung mit Zahlungsschaltflächen auf der Produktseite, im Mini-Warenkorb und im Warenkorb platzieren. Käufer können Bestellungen nun erfolgreich abschließen.

## v1.5.3

_25. Januar 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4102 --> Korrektur eines Fehlers, der ein rückwärtsinkompatibles bekanntes Problem behebt. In dieser Version wird die Version der Dienst-ID-Erweiterung auf die neueste stabile Version festgelegt, die neue [!DNL Payment Services] -Installationen zur Konfiguration von Commerce Services ermöglicht.

## v1.5.2

_22. Dezember 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3992 --> Verbesserte Rechnungsstellung in [!DNL Payment Services], wenn eine Zahlungsmethode abgelehnt wird.

![Korrektur des Problems](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services], das jetzt die PayPal-Zahlungsschaltflächen für Händler korrekt anzeigt, indem die benutzerdefinierte Vorlage [Auslösen des Checkouts](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} für die Checkout-Seite verwendet wird. Zuvor wurden die Schaltflächen im Minicart gelegentlich angezeigt.

## v1.5.1

_23. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] enthält jetzt die Versionsnummer in der Kopfzeile des Benutzeragenten, sodass Anforderungen nicht verwendete Endpunkte verfolgen, filtern oder veralteten können.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] zeigt jetzt korrekt Bestelldaten an, wenn eine Bestellung über die Zahlungsschaltflächen auf der Produktseite platziert wird.

## v1.5.0

_18. November 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-3880 --> Ein Käufer kann jetzt [seine Kreditkarteninformationen beim Checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) speichern, um sie bei einem späteren Kauf für denselben oder einen anderen Speicher innerhalb desselben Händlers zu verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3950 --> Händler können jetzt die Funktion [Sofortiger Kauf Commerce](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) für ihre Geschäfte aktivieren, damit Käufer (mithilfe von [ausgefüllten Kreditkarteninformationen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) den Checkout beschleunigen können.

## v1.4.1

_14. Oktober 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg)<!-- Issue PAY-3766 --> Wenn die Zahlungsmethode eines Kunden abgelehnt wird, ist die sichtbare Fehlermeldung beschreibender. Es empfiehlt dem Kunden, die Zahlungsinformationen erneut einzugeben und es erneut zu versuchen, eine andere Zahlungsmethode zu versuchen oder seine Bank über die Ablehnung der Transaktion zu kontaktieren.

## v1.4.0

_30. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] beinhaltet jetzt die Möglichkeit, ein Händlerkonto einzurichten, um [mehrere PayPal-Geschäftskonten zu verwenden](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Dadurch kann der Händler Ihre Geschäfte in mehreren Ländern mit unterschiedlichen Währungen betreiben oder Adobe Commerce für einen Teil Ihres Unternehmens verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3231 --> Händler können [einen [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) zur Konfiguration von Websites oder einzelnen Store-Ansichten hinzufügen, die in Bankanweisungen von Kunden angezeigt werden, um Marken, Stores oder Produktlinien zu trennen.

![Neu](../assets/new.svg)<!-- Issue PAY-3707 --> [Aktivieren oder deaktivieren Sie Kreditkartenfelder und PayPal-Zahlungsschaltflächen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) für den Checkout in den [!DNL Payment Services] -Einstellungen.

![Korrektur des Problems](../assets/fix.svg)<!-- Issue PAY-3546 --> Wenn ein Kunde auf **[!UICONTROL Edit cart]** klickt, leitet die Seite zur Warenkorbseite um und zeigt die aktualisierten Elemente an, anstatt einen leeren Warenkorb anzuzeigen.

## v1.3.1

_6. September 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3663 --> Jetzt, wenn der Store eines Händlers eine Bestellung erfasst, die mit einer nicht globalen Währung autorisiert ist, wird der Erfassungsvorgang abgeschlossen und es wird kein Fehler angezeigt.

## v1.3.0

_9. August 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-XX --> Allgemeines Release zur Verfügbarkeit—[!DNL Payment Services] wird jetzt [ von den Versionen  [!DNL Adobe Commerce]  und [!DNL Magento Open Source] 2.4.0 bis 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility) unterstützt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ist jetzt mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop kompatibel.

## v1.2.0

_29. Juni 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay ist mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop nicht kompatibel. Bei Verwendung von Safari Version 15.5 können Sie den Checkout nicht mit Apple Pay abschließen.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3264 --> Zuvor schlug der Checkout fehl, wenn ein angemeldeter Benutzer eine Abrechnungs-/Versandadresse auswählte, die nicht die Standardadresse für sein Konto war. Jetzt wird die ausgewählte Abrechnungs-/Lieferadresse gesendet (anstelle der gespeicherten Standardadresse) und der Checkout wurde erfolgreich abgeschlossen.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3314 --> Wenn Sie die PayPal-Zahlungsschaltflächen für den Checkout deaktivieren, werden keine Fehler angezeigt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3330 --> Zahlungen schlagen beim Checkout nicht mehr fehl, wenn ein Gastbenutzer eine Telefonnummer mit Bindestrichen eingibt.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Wenn die Commerce Services-Anmeldedaten ungültig sind, werden Sie von [!DNL Payment Services] jetzt benachrichtigt, indem ein Berechtigungsfehler auf der [!DNL Payment Services] -Startseite im Admin angezeigt wird.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] ist mit `commerce-data-export` v101.20 und höher inkompatibel, wodurch es mit der [[!DNL Channel manager] Erweiterung](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html) inkompatibel wird.

## v1.1.0

_31. März 2022_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeines Verfügbarkeitsrelease—[!DNL Payment Services] wird jetzt [ von den Versionen  [!DNL Adobe Commerce] und [!DNL Magento Open Source] 2.4.0 bis 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility) unterstützt.

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services] -Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist jetzt für kanadische Händler verfügbar. Händler können die Zahlungskonfiguration entweder in [Französisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) oder in [Englisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies) anzeigen.

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Kanadische Dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) für Kreditkarten- und PayPal-Transaktionen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants können die Erweiterung [Onboard [!DNL Payment Services]](onboard.md) in englischer oder französischer Sprache verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können jetzt Finanzberichte in kanadischem Dollar (CAD) anzeigen, sowohl den [Bestellzahlungsstatus](order-payment-status.md) als auch den [Payouts-Bericht](payouts.md).

![Korrektur des Problems](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] ist jetzt mit [PHP 8.1](https://www.php.net/releases/8.1/en.php) kompatibel.

![Korrektur des Fehlers](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbesserter Warnhinweis im Sandbox-Modus zur Anzeige ordnungsgemäßer Warnhinweise mit mehreren Stores.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> Sie können jetzt verfügbare Zahlungsmethoden, wie Venmo, auf der Store-Ansichtsebene aktivieren und deaktivieren. Bisher konnten Sie nur Zahlungsmethoden pro Website konfigurieren.

![Korrektur des Problems](../assets/fix.svg)<!-- Issue PAY-2277 --> Sie können jetzt einzelne PayPal-Zahlungsschaltflächen [ selektiv aktivieren oder deaktivieren](settings.md#payment-buttons).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der Seite _Bestellung überprüfen_ angezeigt.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> Testen von Kreditkartentransaktionen [ kann bei PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) fehlschlagen, wenn Zahlungen in einer Sandbox-Umgebung verarbeitet werden.

## v1.0.0

_29. November 2021_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Allgemeines Verfügbarkeitsrelease—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) wird jetzt von den [!DNL Adobe Commerce] und den [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1 unterstützt.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] -Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für [[!DNL Adobe Commerce]  in der Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder für [On-premise](install.md#on-premises) -Instanzen installiert werden. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt ein [Sandbox-Konto](sandbox.md) , mit dem Händler die Erweiterung im Testmodus bewerten können.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können die Erweiterung der Zahlungsdienste [3} mit grundlegenden Zahlungsverhaltensweisen konfigurieren, z. B. indem sie [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) zwischen Sandbox- oder Produktionsumgebungen wechseln.](settings.md)

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Ihre Käufer können mit [!DNL Payment Services] oder über die 3}manuelle Bestellerstellung](create-order.md) auschecken.[

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> Umfassende Berichterstellung über den [Bestellzahlstatus](order-payment-status.md) und den [Zahlungsbericht](payouts.md) sind für [!DNL Payment Services] verfügbar, um Ihnen einen klaren Überblick über die Bestellungen und damit zusammenhängenden Zahlungen Ihres Geschäfts zu geben.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt flexible gestaffelte Preise, die auf dem gesamten Verarbeitungsvolumen basieren und an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Sie können [einfach das Erscheinungsbild](payments-options.md) der PayPal-Zahlungsschaltflächen und Kreditkartenfelder für die [!DNL Payment Services] -Erweiterung anpassen.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Die Verwendung von [falschen Composer-Schlüsseln](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) während der Installation der Erweiterung verhindert, dass der Benutzer [sich mit dem richtigen `MAGEID` authentifiziert.](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] reports [ darf nicht sofort synchronisiert werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> Ihr [PayPal-Sandbox-Konto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) für [!DNL Payment Services] kann nicht überprüft werden, wenn Sie dieses Konto beim Onboarding erstellen.
