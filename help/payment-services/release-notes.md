---
title: "[!DNL Payment Services] Versionshinweise"
description: Informationen zu allen [!DNL Payment Services] veröffentlicht.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: e9209d7361d0dd6b6f502df9a898a5a35c53ec1a
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 0%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Payment Services] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Informationen zu Funktionsänderungen und Fehlerbehebungen, die außerhalb der regulären Version der Funktionen veröffentlicht wurden, finden Sie in den Abschnitten gehostete Dienstaktualisierungen .

Siehe [Bevorstehende Versionen](https://devdocs.magento.com/release/) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://devdocs.magento.com/release/availability.html) in der Entwicklerdokumentation , um mehr über die Produktkompatibilität zu erfahren.

## Aktualisierungen gehosteter Dienste

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Versionen der gehosteten Funktionen für den gehosteten Dienst veröffentlicht wurden.

+++Hosting-Dienstaktualisierungen

_9. Juni 2023_

![Neu](../assets/new.svg)<!-- Issue PAY-4288 --> Jetzt können Händler [konfigurieren _only_ PayPal-Zahlungsschaltflächen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—und _not_ Verwenden Sie die PayPal Kreditkartenzahlungsoption, um eine Vielzahl von Zahlungsoptionen bereitzustellen, ohne die Genehmigung der PayPal-Kreditkarte zu beantragen.

![Neu](../assets/new.svg)<!-- Issue PAY-4050 --> Eine [Datenvisualisierungsansicht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), der auf der Zahlungsdienst-Startseite für den Bericht Bestellzahlstatus angezeigt wird.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4486--> Zuvor wurde die Schaltfläche PayPal PayLater nicht beim Checkout für Händler in Großbritannien angezeigt. Dieses Problem ist gelöst.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4485--> Visualisierungsansichten für Berichtsdaten werden jetzt auf der Zahlungsdienst-Startseite angezeigt, wenn Zahlungsdienste deaktiviert sind.

_25. Januar 2023_

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-4102 --> Neue Installationen von Zahlungsdiensten können Commerce-Services nicht konfigurieren, sodass Zahlungsdienste nicht mehr funktionsfähig sind. Um dieses Problem zu beheben, aktualisieren Sie Ihre Zahlungsdiensterweiterung auf Version 1.5.3.

_12. September 2022_

![Neu](../assets/new.svg)<!-- Issue PAY-3705 --> Die `increment_id` ist jetzt für die Abstimmung von Auszahlungen in externen ERP-Systemen verfügbar. Sie wird an die [`custom_id` _und_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), die sowohl im PayPal-Webhook als auch in den Details zur Handelsaktivität für eine Auszahlung angezeigt wird.

_31. August 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3629 --> Wenn ein neuer Händler zum ersten Mal auf die Zahlungsdienst-Startseite zugreift, wird die Seite jetzt sofort geladen, um den Inhalt anzuzeigen, anstatt dass eine Seitenaktualisierung erforderlich ist.

_9. August 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay ist jetzt als PayPal Smart Button verfügbar. Diese [Zahlungsoption](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) ermöglicht es Kunden, die Touch-ID-Funktion auf ihrem iOS- oder macOS-Gerät zu verwenden, um Apple Pay auszuwählen. Apple Pay verarbeitet die Zahlung mit den auf dem Gerät gespeicherten Zahlungsberechtigungen für Kredit- und Debitkarten.

_28. Juni 2021_

![Neu](../assets/new.svg)<!-- Issue PAY-1720 --> Streitigkeiten über Store-Bestellungen sind jetzt verfügbar unter [den Bericht über den Auftragszahlungsstatus](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Sie können bei Streitigkeiten direkt zum PayPal-Abwicklungszentrum navigieren von [!DNL Payment Services].

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Verbesserungen des Benutzererlebnisses aus [!DNL Payment Services] Zu den Startseiten gehören die Möglichkeit, eine Konfiguration auf der aktuellen Vererbungsebene zu ändern, sowie Verbesserungen bei der Anzeige der Kopfzeile und der Navigation.

![Neu](../assets/new.svg)<!-- Issue PAY-2854 --> Jetzt werden Warnungen angezeigt, wenn Sie vom Sandbox-Modus zum Produktionsmodus wechseln und versuchen, von einer Ansicht mit nicht gespeicherten Aktualisierungen weg zu navigieren.

![Neu](../assets/new.svg)<!-- Issue PAY-2761 --> Sie können jetzt die Daten anpassen, die im [Bestellstatusbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) und [Zahlungsbericht](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) durch Einblenden oder Ausblenden von Spalten mithilfe des Steuerelements Spalteneinstellungen.

+++

## v2.1.0

_9. Juni 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue xxx --> Unterstützung für Adobe Commerce 2.4.7-beta1 hinzugefügt.

![Neu](../assets/new.svg)<!-- Issue xxx --> Hinzugefügt [Verfügbarkeit in den folgenden Ländern und assoziierten Währungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australien, Frankreich, Vereinigtes Königreich.

![Neu](../assets/new.svg)<!-- Issue PAY-4296 --> Hinzugefügt [Erweiterte Ressourcen für Admin-Rollen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) um sicherzustellen, dass Admin-Benutzer Bestellungen für Kunden erstellen und verwalten können und Zahlungsdienste im Menü &quot;Verkauf&quot;angezeigt werden.

![Neu](../assets/new.svg)<!-- Issue PAY-4236 --> Hinzugefügt [automatische Aufhebung von Bestellungen, die beim Checkout Fehler verursachen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Neu](../assets/new.svg)<!-- Issue PAY-4183 --> Erstellte Funktionalität zu [Schaltfläche für die Zahlungsoption von Kredit-/Debitkarten anzeigen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) auf der Checkout-Seite.

## v2.0.0

_10. März 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-4152 --> Unterstützung für PHP 8.2 und Adobe Commerce 2.4.6 hinzugefügt. Nicht kompatibel mit PHP 7.x.

## v1.6.1

_10. März 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg)<!-- Issue PAY-4226 --> Es wurde ein Problem behoben, das verhinderte, dass neue Zahlungsdienst-Händler den Checkout im Admin verwenden konnten. Die Zahlungsdienste verwendeten zuvor die Commerce-Kunden-ID, die für neue Kunden nicht vorhanden ist.

![Fehlerbehebung](../assets/fix.svg)<!-- Issue PAY-4205 --> Es wurde ein Fehler behoben, der dazu führte, dass der angegebene Versandadressenstatus beim Checkout mit dem Status in den Standardsteuereinstellungen durch den Status ersetzt wurde. [PayPal-Option](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Jetzt können Kunden ihre Bestellungen in einen anderen Staat verschicken lassen als den, der in den Steuereinstellungen des Händlers als Standard konfiguriert wurde.

![Fehlerbehebung](../assets/fix.svg)<!-- Issue PAY-4202 --> Es wurde ein Problem behoben, das Kunden daran hinderte, einen Kartengewinn zu verwenden, um einen Kauf abzuschließen oder eine ungültige Zahlungsmethode für einen Store zu löschen [mithilfe der `Authorize and Capture` Zahlungsaktion](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Zuvor trat der Fehler &quot;Provider Vault ID not found&quot;auf, wenn der Kunde versuchte, seine ausgefüllten Kreditkarten zu verwenden oder zu ändern.

## v1.6.0

_17. Februar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-3540 --> Hinzugefügt [PCI-3DS-Compliance-Funktion für Händler, die in der Europäischen Union (EU) und Großbritannien tätig sind](security.md#3ds). Diese zusätzliche Sicherheitsebene, die die Authentifizierung von Käufern bei ihrem Kreditkartenaussteller erfordert, trägt zur Verhinderung von Online-Betrug bei und ist als Teil der EU-Vorschriften zur Einhaltung der Vorschriften erforderlich.

![Neu](../assets/new.svg)<!-- Issue PAY-3609 --> Die Möglichkeit wurde hinzugefügt, [Aktivieren der Kartenüberprüfung in der Admin-Konsole](vaulting.md#use-vaulting-in-the-admin). Auf diese Weise können Händler mit ihren bewährten Zahlungsmethoden eine Bestellung für Kunden in der Admin erstellen.

## v1.5.4

_29. Januar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4110 --> Fehlerkorrektur - Käufer können jetzt eine Bestellung mit intelligenten Schaltflächen auf der Produktseite, im Mini-Warenkorb und im Warenkorb platzieren. Käufer können Bestellungen nun erfolgreich abschließen.

## v1.5.3

_25. Januar 2023_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-4102 --> Es wurde ein Problem behoben, das ein rückwärtsinkompatibles bekanntes Problem verursachte. In dieser Version wird die Version der Dienst-ID-Erweiterung auf die neueste stabile Version festgelegt, die es neuen Zahlungsdienst-Installationen ermöglicht, Commerce Services zu konfigurieren.

## v1.5.2

_22. Dezember 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3992 --> Verbesserte Rechnungsstellung bei Zahlungsdiensten, wenn eine Zahlungsmethode abgelehnt wird.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3999 --> Zahlungsdienste zeigen Händlern jetzt die PayPal-Smart-Schaltflächen korrekt an, indem sie [Auslösen eines Checkouts](https://marketplace.magento.com/swissup-firecheckout.html){target=_blank} benutzerdefinierte Vorlage für die Checkout-Seite. Zuvor wurden die Schaltflächen im Minicart gelegentlich angezeigt.

## v1.5.1

_23. November 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-3923 --> Zahlungsdienste enthalten jetzt die Versionsnummer in der Kopfzeile des Benutzeragenten, damit Anfragen nicht verwendete Endpunkte verfolgen, filtern oder veralteten können.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3968 --> Die Zahlungsdienste zeigen jetzt korrekt Bestelldaten an, wenn eine Bestellung über Smart-Schaltflächen von der Produktseite aus platziert wird.

## v1.5.0

_18. November 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-3880 --> Ein Käufer kann jetzt [Vault-Kreditkarteninformationen beim Checkout speichern](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) , um in einem späteren Kauf für denselben oder einen anderen Store innerhalb desselben Händlers zu verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3950 --> Händler können jetzt die [Funktion &quot;Sofortiger Kauf - Commerce&quot;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) für ihre Geschäfte, damit die Käufer [ungültige Kreditkarteninformationen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)), um den Checkout zu beschleunigen.

## v1.4.1

_14. Oktober 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg)<!-- Issue PAY-3766 --> Wenn die Zahlungsmethode eines Kunden abgelehnt wird, ist die sichtbare Fehlermeldung beschreibender. Es empfiehlt dem Kunden, die Zahlungsinformationen erneut einzugeben und es erneut zu versuchen, eine andere Zahlungsmethode auszuprobieren oder seine Bank über die Ablehnung der Transaktion zu kontaktieren.

## v1.4.0

_30. September 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-784 --> Zahlungsdienste bieten jetzt die Möglichkeit, ein Händlerkonto einzurichten, um [mehrere PayPal-Geschäftskonten verwenden](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Dadurch kann der Händler Ihre Geschäfte in mehreren Ländern mit unterschiedlichen Währungen betreiben oder Adobe Commerce für einen Teil Ihres Unternehmens verwenden.

![Neu](../assets/new.svg)<!-- Issue PAY-3231 --> Händler können [hinzufügen [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) auf Websites oder in der Konfiguration einzelner Store-Ansichten, die in Kundentransaktionsbankausweisen angezeigt werden, um Marken, Geschäfte oder Produktlinien zu unterscheiden.

![Neu](../assets/new.svg)<!-- Issue PAY-3707 --> [Aktivieren oder Deaktivieren von Kreditkartenfeldern und PayPal-Smart-Schaltflächen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) für den Checkout in den Zahlungsdiensteinstellungen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3546 --> Klickt ein Kunde **[!UICONTROL Edit cart]**, leitet die Seite zur Warenkorbseite um und zeigt die aktualisierten Elemente an, anstatt einen leeren Warenkorb anzuzeigen.

## v1.3.1

_6. September 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3663 --> Wenn der Store eines Händlers eine Bestellung erfasst, die mit einer nicht globalen Währung autorisiert ist, wird der Erfassungsvorgang abgeschlossen und es wird kein Fehler angezeigt.

## v1.3.0

_9. August 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-XX --> Version der allgemeinen Verfügbarkeit -[!DNL Payment Services] ist jetzt [kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ist jetzt mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop kompatibel.

## v1.2.0

_29. Juni 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay ist nicht mit dem Safari-Browser Version 15.5 auf dem Mobilgerät und Desktop kompatibel. Bei Verwendung von Safari Version 15.5 können Sie den Checkout nicht mit Apple Pay abschließen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3264 --> Bisher ist der Checkout fehlgeschlagen, wenn ein angemeldeter Benutzer eine andere Abrechnungs-/Lieferadresse als die Standardadresse für sein Konto ausgewählt hat. Dieses Problem wurde behoben. Jetzt wird die ausgewählte Abrechnungs-/Lieferadresse gesendet (anstelle der gespeicherten Standardadresse) und der Checkout erfolgreich abgeschlossen.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3314 --> Wenn Sie die PayPal Smart-Schaltflächen zum Auschecken deaktivieren, werden keine Fehler angezeigt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3330 --> Zahlungen schlagen beim Checkout nicht mehr fehl, wenn ein Gastbenutzer eine Telefonnummer mit Bindestrichen eingibt.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Wenn die Anmeldedaten für Commerce Services ungültig sind, wird die [!DNL Payment Services] Die Startseite wird jetzt in der Admin-Konsole angezeigt. Es wird ein Berechtigungsfehler angezeigt, der Sie darauf hinweist, dass Ihre Anmeldedaten ungültig sind.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] ist derzeit inkompatibel mit `commerce-data-export` v101.20 und höher, wodurch sie mit dem [[!DNL Channel manager] Erweiterung](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31. März 2022_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[!DNL Payment Services] ist jetzt [kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Neu](../assets/new.svg)<!-- Issue PAY-2682 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] ist jetzt für kanadische Händler verfügbar. Merchandising kann die Zahlungskonfiguration in einer der beiden [französisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) oder [englisch](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Neu](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] unterstützt [Kanadische Dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) für Kreditkarten und PayPal-Transaktionen.

![Neu](../assets/new.svg)<!-- Issue PAY-2680 --> Händler können [Onboard [!DNL Payment Services]](onboard.md) Erweiterung in englischer oder französischer Sprache.

![Neu](../assets/new.svg)<!-- Issue PAY-2678 --> Händler können nun Finanzberichte anzeigen, sowohl die [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), in kanadischen Dollar (CAD).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ist jetzt kompatibel mit [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbesserter Warnhinweis im Sandbox-Modus zur Anzeige ordnungsgemäßer Warnhinweise mit mehreren Stores.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2742 --> Sie können jetzt verfügbare Zahlungsmethoden wie Venmo auf der Store-Ansichtsebene aktivieren und deaktivieren. Bisher konnten Sie nur Zahlungsmethoden pro Website konfigurieren.

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2277 --> Sie können jetzt selektiv [Aktivieren oder Deaktivieren einzelner PayPal-Smart-Schaltflächen](settings.md#payment-buttons).

![Problem behoben](../assets/fix.svg)<!-- Issue PAY-2561 --> Zuvor entfernte Produkte werden nicht im Warenkorb auf der _Überprüfungsreihenfolge_ Seite.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2842 --> Testen von Kreditkartentransaktionen [kann bei PayPal fehlschlagen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung.

## v1.0.0

_29. November 2021_

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg)<!-- Issue PAY-2127 --> Version der allgemeinen Verfügbarkeit -[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ist jetzt kompatibel mit [!DNL Adobe Commerce] und [!DNL Magento Open Source] Versionen 2.4.0 bis 2.4.3-p1.

![Neu](../assets/new.svg)<!-- Issue PAY-124 --> Die [!DNL Payment Services] Erweiterung für [!DNL Adobe Commerce] und [!DNL Magento Open Source] kann entweder für [[!DNL Adobe Commerce] zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [Vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] unterstützt [Sandbox-Konto](sandbox.md) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue PAY-666 --> Händler können [Zahlungsdienste konfigurieren](settings.md) Erweiterung mit grundlegendem Zahlungsverhalten, z. B. unter Verwendung von [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) Wechsel zwischen Sandbox- oder Produktionsumgebungen.

![Neu](../assets/new.svg)<!-- Issue PAY-780 --> Ihre Kunden können mit [!DNL Payment Services] oder über [manuelle Auftragserstellung](create-order.md).

![Neu](../assets/new.svg)<!-- Issue PAY-1856 --> Umfassende Berichterstellung über [Bestellstatus](order-payment-status.md) und [Payload-Berichte](payouts.md), sind verfügbar für [!DNL Payment Services] um Ihnen einen klaren Überblick über die Bestellungen und die damit verbundenen Zahlungen Ihres Ladens zu geben.

![Neu](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] unterstützt flexible gestaffelte Preise, die auf dem gesamten Verarbeitungsvolumen basieren und an jeden Händler angepasst sind.

![Neu](../assets/new.svg)<!-- Issue PAY-1443 --> Sie können [Erscheinungsbild und Verhalten anpassen](payments-options.md) von PayPal-Smart-Schaltflächen und Kreditkartenfeldern für die [!DNL Payment Services] -Erweiterung.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2473 --> Verwenden [falsche Composer-Schlüssel](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) während der Installation der Erweiterung verhindert, dass der Benutzer [authentifizieren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) mit der richtigen `MAGEID`.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] Berichte [kann nicht sofort synchronisiert werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Bekanntes Problem](../assets/bug.svg)<!-- Issue PAY-2475 --> Ihre [PayPal-Sandbox-Konto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) für [!DNL Payment Services] kann nicht überprüft werden, wenn Sie dieses Konto beim Onboarding erstellen.
