---
title: Sicherheit und Compliance
description: Überprüfen Sie die Sicherheits- und Compliance-Anforderungen für Ihre Site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 17c8d16a2593f7bb6015f5b2968fc4c67be8ed5b
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Sicherheit und Compliance

Die Sicherheit ist in [!DNL Payment Services] von größter Bedeutung und es werden keine privaten oder PCI-basierten Informationen (Payment Card Industry) über Ihre [!DNL Payment Services] weitergegeben.

## Commerce-Sicherheit

[!DNL Adobe Commerce] und [!DNL Magento Open Source] unterstützen mehrere Sicherheitsfunktionen.

Siehe [Sicherheit](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security){target="_blank"} im Benutzerhandbuch zu zentralen Sicherheitsvorkehrungen, um mehr über die Verwaltung von Admin-Sitzungen und -Anmeldedaten zu erfahren, CAPTCHA zu implementieren und Website-Einschränkungen zu verwalten.

## PCI-Compliance

Die Payment Card Industry (PCI) hat eine Reihe von Anforderungen für Unternehmen festgelegt, die Zahlungen per Kreditkarte über das Internet akzeptieren. Neben einer sicheren Umgebung sind Händler, die mit Kreditkarteninformationen von Kunden umgehen, für die Einhaltung einiger Standardrichtlinien verantwortlich.

Weitere Informationen finden Sie unter [PCI Compliance Guidelines](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-pci){target="_blank"} .

Händler können einen [Fragebogen zur Selbstbewertung (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"} ausfüllen, der ein Tool zur Selbstvalidierung zur Bewertung der Sicherheit von Karteninhaberdaten darstellt.

### Kreditkartenfelder

Mit Kreditkartenfeldern werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

### 3DS

PCI 3-D Secure (3DS) ermöglicht die Authentifizierung von Käufern mit ihrem Kreditkartenaussteller bei Online-Kreditkartenkäufen. Diese zusätzliche Sicherheitsstufe trägt zur Vermeidung von Online-Betrug bei und ist als Teil der EU-Vorschriften zur Einhaltung der Vorschriften erforderlich.

[!UICONTROL Payment Services] bietet 3DS-Funktionen, mit denen Händler die EU-Vorschriften einhalten und Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften schützen können.

Wenn Sie Händler in der EU oder in Großbritannien sind, für die die Einhaltung der 3DS-Vorschriften erforderlich ist, müssen Sie 3DS manuell aktivieren (standardmäßig ist dies &quot;`Off`&quot;) in den [Einstellungen](settings.md#credit-card-fields).

>[!IMPORTANT]
>
>Die 3DS-Anforderung gilt für Transaktionen, bei denen sich die Bank des Unternehmens und des Karteninhabers im [Europäischen Wirtschaftsraum](https://www.efta.int/eea) (EWR) und in Großbritannien befindet. US-Händler benötigen keine 3DS, können sie jedoch für ihre Transaktionen aktivieren.

Bestellungen, die für den Käufer von Händlern/Ladenbesitzern abgegeben werden, sind nicht mit den 3DS-Compliance-Maßnahmen konfiguriert.

>[!MORELIKETHIS]
>
> * Weitere Informationen finden Sie unter [3DS in den Einstellungen](settings.md#3ds) .
> * Weitere Informationen zu bestimmten Kreditkarten für 3DS-Tests finden Sie unter [Testkarten](https://developer.paypal.com/docs/checkout/advanced/customize/3d-secure/test/) in der PayPal-Entwicklerdokumentation.

### Kartengewölbe

Wenn ein Kunde [seine Kreditkarteninformationen ](vaulting.md) für zukünftige Käufe in Ihren Geschäften speichert, werden dem Käufer nur minimale Kreditkarteninformationen (letzte vier Stellen, Ablaufdatum der Karte und Marke der Karte) zur Verfügung gestellt. Kreditkarteninformationen werden beim Zahlungsdienstleister gespeichert. Wenn eine Karte abläuft oder sie die Informationen nicht mehr speichern müssen, können sie dieses Token löschen, damit die Informationen nicht mehr vom Zahlungsdienstleister gespeichert werden.

Weitere Informationen finden Sie unter [Kreditkartenausnahme](vaulting.md) .

### PayPal-Zahlungsschaltflächen

Mit PayPal Zahlungsschaltflächen werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

Aus Sicherheitsgründen gibt PayPal die Rechnungsadresse beim Checkout nicht weiter - Land, E-Mail und Name sind die einzigen verwendeten Rechnungsinformationen. Sie können optional den PayPal-Checkout Ihrer Site aktivieren, um die vollständige Rechnungsadresse zurückzugeben, indem Sie PayPal kontaktieren und einen Prüfvorgang abschließen.

PayPal verfügt auch über einen integrierten Betrugsschutz, der das maschinelle Lernen nutzt, um Betrug zu bekämpfen. Weitere Informationen finden Sie in der PayPal-Dokumentation zum [Schutz von Verkäufern](https://www.paypal.com/us/webapps/mpp/security/seller-protection) .

## Betrugsschutz

Sie können den automatisierten Betrugsschutz für Zahlungsdienste mit der Erweiterung [Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html) aktivieren. Weitere Informationen finden Sie unter [Signifikanter Betrugsschutz](fraud-protection.md) .

PayPal bietet in der Entwicklerdokumentation weitere Optionen für den [Betrugsschutz](https://www.paypal.com/us/cshelp/article/what-is-fraud-protection-help1014){target=_blank}:

* Weitere Informationen finden Sie unter [Betrugsschutz erweitert](https://www.paypal.com/us/enterprise/fraud-protection-advanced#fraud-protection-advanced){target=_blank} .
* Weitere Informationen finden Sie unter [Chargeback-Schutz](https://www.paypal.com/us/cshelp/article/what-is-chargeback-protection-help608){target=_blank} .
