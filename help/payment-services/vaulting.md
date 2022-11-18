---
title: Kreditkartenausnahme
description: Käufer können ihre Kreditkartendetails für zukünftige Käufe einbehalten (speichern).
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# Kreditkartenausnahme

Konvertieren von einmaligen Kunden in treue Kunden mit Kreditkartenausfall. Käufer können ihre Kreditkartenanmeldeinformationen während des Checkout speichern - oder &quot;Vault&quot;- um sie bei einem späteren Kauf für denselben oder einen anderen, innerhalb desselben Händlerkontos zu verwenden.

![Beziehen der Kreditkarte zur späteren Verwendung](assets/save-card-for-later.png)

Käufer verwenden das gespeicherte Token, um einen zukünftigen Checkout mit ihren gespeicherten Kreditkarteninformationen abzuschließen.

![Verwenden gespeicherter Anmeldedaten für zukünftige Käufe](assets/use-stored-card.png)

Sie können ihre Kreditkarten auch einfach aus [Gespeicherte Zahlungsmethoden](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) in ihrem Konto.

![Gespeicherte Zahlungsmethoden in meinem Konto](assets/stored-payment-methods.png)

## Validierung aktivieren

In den Zahlungsdiensten können Sie Kreditkartenkosten für Ihre Geschäfte aktivieren [Einstellungen](settings.md#card-vaulting).

## Sicherheit

Minimale Kreditkarteninformationen werden für den Käufer freigegeben. Sie sehen nur die letzten vier Ziffern, das Ablaufdatum und die Marke ihrer ausgefüllten Kreditkarte. Die Kreditkarteninformationen werden bei dem Zahlungsdienstleister gespeichert, um [PCI](security.md#PCI-compliance) Compliance-Standards.
