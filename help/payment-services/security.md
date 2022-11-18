---
title: Sicherheit und Einhaltung
description: Überprüfen Sie die Sicherheits- und Compliance-Anforderungen für Ihre Site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Sicherheit und Einhaltung

Sicherheit ist von größter Bedeutung [!DNL Payment Services] und keine von der privaten oder der Zahlungskartenindustrie (PCI) regulierten Informationen über Ihre [!DNL Payment Services].

## Commerce-Sicherheit

[!DNL Adobe Commerce] und [!DNL Magento Open Source] Unterstützung für verschiedene Sicherheitsfunktionen.

Siehe [Sicherheit](https://docs.magento.com/user-guide/stores/security.html){target=&quot;_blank&quot;} im Benutzerhandbuch zu Sicherheitsvorkehrungen. Hier erfahren Sie, wie Sie Admin-Sitzungen und -Anmeldedaten verwalten, CAPTCHA implementieren und Website-Beschränkungen verwalten.

## PCI-Compliance

Die Payment Card Industry (PCI) hat eine Reihe von Anforderungen für Unternehmen festgelegt, die Zahlungen per Kreditkarte über das Internet akzeptieren. Neben einer sicheren Umgebung sind Händler, die mit Kreditkarteninformationen von Kunden umgehen, für die Einhaltung einiger Standardrichtlinien verantwortlich.

Siehe [PCI Compliance Guidelines](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;} für weitere Informationen.

Merchandising kann eine [Selbstbewertungsfragebogen (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}, ein Tool zur Selbstvalidierung zur Bewertung der Sicherheit von Karteninhaberdaten.

### Kreditkartenfelder

Mit Kreditkartenfeldern werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

### Kartengewölbe

Wenn ein Kunde [Vault- oder &quot;Save&quot;- ihre Kreditkarteninformationen](vaulting.md) für zukünftige Käufe in Ihren Geschäften werden nur minimale Kreditkarteninformationen für den Käufer freigegeben (letzte vierstellige Zahl, Ablaufdatum der Karte und Marke der Karte). Kreditkarteninformationen werden beim Zahlungsdienstleister gespeichert. Wenn eine Karte abläuft oder sie die Informationen nicht mehr speichern müssen, können sie dieses Token löschen, damit die Informationen nicht mehr vom Zahlungsdienstleister gespeichert werden.

### PayPal Smart-Schaltflächen

Mit PayPal Smart Buttons werden keine PCI-regulierten Daten über Ihre Dienste weitergegeben. Diese Daten müssen nicht gespeichert oder gepflegt werden, was die PCI-Compliance-Probleme erheblich verringert.

Aus Sicherheitsgründen gibt PayPal die Rechnungsadresse beim Checkout nicht weiter - Land, E-Mail und Name sind die einzigen verwendeten Rechnungsinformationen. Sie können optional den PayPal-Checkout Ihrer Site aktivieren, um die vollständige Rechnungsadresse zurückzugeben, indem Sie PayPal kontaktieren und einen Prüfvorgang abschließen.

PayPal verfügt auch über einen integrierten Betrugsschutz, der das maschinelle Lernen nutzt, um Betrug zu bekämpfen. Siehe PayPal&#39;s [Dokumentation zum Schutz von Verkäufern](https://www.paypal.com/us/webapps/mpp/security/seller-protection) für weitere Informationen.
