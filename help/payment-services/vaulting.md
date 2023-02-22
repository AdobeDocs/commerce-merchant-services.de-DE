---
title: Kreditkartenausfall
description: Käufer können ihre Kreditkartendetails für zukünftige Käufe einbehalten (speichern).
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Kreditkartenausfall

Konvertieren von einmaligen Kunden in treue Kunden mit Kreditkartenausfall. Käufer können ihre Kreditkartenanmeldeinformationen während des Checkout speichern - oder &quot;Vault&quot;- um sie bei einem späteren Kauf für denselben oder einen anderen, innerhalb desselben Händlerkontos zu verwenden.

![Beziehen der Kreditkarte zur späteren Verwendung](assets/save-card-for-later.png)

Käufer verwenden das gespeicherte Token, um einen zukünftigen Checkout mit ihren gespeicherten Kreditkarteninformationen abzuschließen.

![Verwenden gespeicherter Anmeldedaten für zukünftige Käufe](assets/use-stored-card.png)

Sie können ihre Kreditkarten auch einfach aus [Gespeicherte Zahlungsmethoden](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) in ihrem Konto.

![Gespeicherte Zahlungsmethoden in meinem Konto](assets/stored-payment-methods.png)

## Validierung aktivieren

Sie können die Kreditkartenüberprüfung für Kunden aktivieren _und_ Händler in der Admin - für Ihre Geschäfte in [!DNL Payment Services] [Einstellungen](settings.md#card-vaulting).

## Use vaulting in the Admin

Wenn ein Kunde über eine zuvor gültige Kreditkarte verfügt, kann ein Händler mithilfe seiner gültigen Zahlungsmethoden eine nachfolgende Bestellung für diesen Kunden im Admin erstellen.

Sie können im Admin nur dann gültige Karten verwenden, wenn der Kunde über ein bestehendes Konto und ein gültiges Token verfügt, das im System von einer zuvor abgeschlossenen Zahlung gespeichert ist.

So erstellen Sie im Admin eine Bestellung für einen Kunden mit seiner gültigen Kreditkarte:

1. [Erstellen einer Bestellung und Hinzufügen von Produkten](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. In _[!UICONTROL Payment & Shipping Information]_auswählen **[!UICONTROL Stored Cards]**als Zahlungsmethode.
1. Wählen Sie die gewünschte Kreditkartenzahlmethode aus.
1. Nachdem Sie alle weiteren erforderlichen Schritte für die Bestellung ausgeführt haben, [submit it](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Verwenden Sie eine ausgewertete Kreditkarte in Admin für Kunden](assets/admin-vaultedcard.png)

## Sicherheit

Minimale Kreditkarteninformationen werden für den Käufer freigegeben. Sie sehen nur die letzten vier Ziffern, das Ablaufdatum und die Marke ihrer ausgefüllten Kreditkarte. Die Kreditkarteninformationen werden bei dem Zahlungsdienstleister gespeichert, um [PCI](security.md#PCI-compliance) Compliance-Standards.
