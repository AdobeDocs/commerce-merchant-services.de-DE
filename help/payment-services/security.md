---
title: Sicherheit und Compliance
description: Überprüfen Sie die Sicherheits- und Compliance-Anforderungen für Ihre Site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# Sicherheit und Compliance

Sicherheit ist von größter Bedeutung [!DNL Payment Services] und keine von der privaten oder der Zahlungskartenindustrie (PCI) regulierten Informationen über Ihre [!DNL Payment Services].

## Commerce-Sicherheit

[!DNL Adobe Commerce] und [!DNL Magento Open Source] Unterstützung für verschiedene Sicherheitsfunktionen.

Siehe [Sicherheit](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} im Benutzerhandbuch zu den wichtigsten Sicherheitsvorkehrungen. Hier erfahren Sie, wie Sie Admin-Sitzungen und -Anmeldedaten verwalten, CAPTCHA implementieren und Website-Einschränkungen verwalten.

## PCI-Compliance

Die Payment Card Industry (PCI) hat eine Reihe von Anforderungen für Unternehmen festgelegt, die Zahlungen per Kreditkarte über das Internet akzeptieren. Neben einer sicheren Umgebung sind Händler, die mit Kreditkarteninformationen von Kunden umgehen, für die Einhaltung einiger Standardrichtlinien verantwortlich.

Siehe [PCI Compliance Guidelines](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} für weitere Informationen.

Merchandising kann eine [Selbstbewertungsfragebogen (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, ein Tool zur Selbstvalidierung zur Bewertung der Sicherheit von Karteninhaberdaten.

### Kreditkartenfelder

Mit Kreditkartenfeldern werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

### 3DS

PCI 3-D Secure (3DS) ermöglicht die Authentifizierung von Käufern mit ihrem Kreditkartenaussteller bei Online-Kreditkartenkäufen. Diese zusätzliche Sicherheitsstufe trägt zur Vermeidung von Online-Betrug bei und ist als Teil der EU-Vorschriften zur Einhaltung der Vorschriften erforderlich.

[!UICONTROL Payment Services] bietet 3DS-Funktionen, die es Händlern ermöglichen, die EU-Vorschriften einzuhalten und Kunden und Händler vor betrügerischen Aktivitäten in ihren Geschäften zu schützen.

Wenn Sie Händler in der EU oder in Großbritannien sind, für die die Einhaltung der 3DS-Vorschriften erforderlich ist, müssen Sie 3DS manuell aktivieren (dies ist `Off` standardmäßig in [Einstellungen](settings.md#credit-card-fields).

>[!NOTE]
>
>Die 3DS-Anforderung gilt für Transaktionen, bei denen sich das Unternehmen und die Bank des Karteninhabers im [Europäischer Wirtschaftsraum](https://www.efta.int/eea) (EWR) und Großbritannien. US-Händler benötigen keine 3DS, können sie jedoch für ihre Transaktionen aktivieren.

Bestellungen, die für den Käufer von Händlern/Ladenbesitzern abgegeben werden, sind nicht mit den 3DS-Compliance-Maßnahmen konfiguriert.

Siehe [3DS in Einstellungen](settings.md#3ds) für weitere Informationen.

### Kartengewölbe

Wenn ein Kunde [Vault- oder &quot;Save&quot;- ihre Kreditkarteninformationen](vaulting.md) für zukünftige Käufe in Ihren Geschäften werden nur minimale Kreditkarteninformationen für den Käufer freigegeben (letzte vierstellige Zahl, Ablaufdatum der Karte und Marke der Karte). Kreditkarteninformationen werden beim Zahlungsdienstleister gespeichert. Wenn eine Karte abläuft oder sie die Informationen nicht mehr speichern müssen, können sie dieses Token löschen, damit die Informationen nicht mehr vom Zahlungsdienstleister gespeichert werden.

Siehe [Kreditkartenausnahme](vaulting.md) für weitere Informationen.

### PayPal Smart-Schaltflächen

Mit PayPal Smart Buttons werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

Aus Sicherheitsgründen gibt PayPal die Rechnungsadresse beim Checkout nicht weiter - Land, E-Mail und Name sind die einzigen verwendeten Rechnungsinformationen. Sie können optional den PayPal-Checkout Ihrer Site aktivieren, um die vollständige Rechnungsadresse zurückzugeben, indem Sie PayPal kontaktieren und einen Prüfvorgang abschließen.

PayPal verfügt auch über einen integrierten Betrugsschutz, der das maschinelle Lernen nutzt, um Betrug zu bekämpfen. Siehe PayPal&#39;s [Dokumentation zum Schutz von Verkäufern](https://www.paypal.com/us/webapps/mpp/security/seller-protection) für weitere Informationen.
