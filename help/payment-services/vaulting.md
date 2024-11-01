---
title: Kreditkartenausfall
description: Käufer können ihre Kreditkartendetails für zukünftige Käufe einbehalten (speichern).
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Kreditkartenausfall

Konvertieren von einmaligen Kunden in treue Kunden mit Kreditkartenausfall. Käufer können ihre Kreditkartenanmeldeinformationen während des Checkout speichern - oder &quot;Vault&quot;- um sie bei einem späteren Kauf für denselben oder einen anderen, innerhalb desselben Händlerkontos zu verwenden.

![Nimm ihre Kreditkarte für die spätere Verwendung ab](assets/save-card-for-later.png){width="400" zoomable="yes"}

Käufer verwenden das gespeicherte Token, um einen zukünftigen Checkout mit ihren gespeicherten Kreditkarteninformationen abzuschließen.

![Verwenden Sie gespeicherte Anmeldeinformationen für zukünftigen Kauf](assets/use-stored-card.png){width="400" zoomable="yes"}

Außerdem können sie ihre Kreditkarten einfach aus den [gespeicherten Zahlungsmethoden](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/stored-payment-methods) in ihrem Konto löschen.

![In meinem Konto gespeicherte Zahlungsmethoden](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal kann derzeit maximal fünf gewölbte Karten speichern.

## Validierung aktivieren

Sie können die Kreditkartenüberprüfung für Kunden _und_, die Händler in der Admin-Konsole sind, für Ihre Geschäfte in [!DNL Payment Services] [Einstellungen](settings.md#card-vaulting) aktivieren.

## Use vaulting in the Admin

Wenn ein Kunde über eine zuvor gültige Kreditkarte verfügt, kann ein Händler mithilfe seiner gültigen Zahlungsmethoden eine nachfolgende Bestellung für diesen Kunden im Admin erstellen.

Sie können im Admin nur dann gültige Karten verwenden, wenn der Kunde über ein bestehendes Konto und ein gültiges Token verfügt, das im System von einer zuvor abgeschlossenen Zahlung gespeichert ist.

So erstellen Sie im Admin eine Bestellung für einen Kunden mit seiner gültigen Kreditkarte:

1. [Erstellen Sie eine Bestellung und fügen Sie Produkte hinzu](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. Wählen Sie in _[!UICONTROL Payment & Shipping Information]_**[!UICONTROL Stored Cards]**als Zahlungsmethode aus.
1. Wählen Sie die gewünschte Kreditkartenzahlmethode aus.
1. Nachdem Sie alle weiteren erforderlichen Schritte für die Bestellung ausgeführt haben, senden Sie [sie](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Verwenden Sie eine gültige Kreditkarte in Admin für den Kunden](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Sicherheit

Minimale Kreditkarteninformationen werden für den Käufer freigegeben. Er sieht nur die letzten vier Ziffern, das Ablaufdatum und die Marke seiner ausgefüllten Kreditkarte. Kreditkarteninformationen werden beim Zahlungsdienstleister gespeichert, um die [PCI](security.md#PCI-compliance)-Compliance-Standards zu erfüllen.
