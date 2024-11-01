---
title: Erstattungen
description: Erstellen Sie Erstattungen für [!DNL Payment Services] Bestellungen im Admin als Teil des Kreditmemoprozesses.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Erstattungen

Rückerstattungen für [!DNL Payment Services] Bestellungen werden im Admin als Teil des Credit Memo-Prozesses erstellt. Ein Kreditmemo ist ein Dokument, das den Betrag angibt, der dem Kunden für eine vollständige oder teilweise Rückerstattung zusteht, die auf einen Kauf angewendet oder dem Kunden direkt zurückerstattet werden kann. Kreditkarten können nur für Bestellungen ausgegeben werden, die [in Rechnung gestellt](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} sind.

Weitere Informationen und Informationen zum Ausgeben und Drucken von Kreditkarten finden Sie unter [Kreditkarten](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos){target="_blank"} in unserem Core-Benutzerhandbuch.

Für Bestellungen, die mit PayPal oder einer Kreditkarte verarbeitet werden, können Sie:

* Den Gesamtbetrag der Bestellung zurückerstatten
* Erstattung eines Teilbetrags einer Bestellung (oder mehrerer Teilbeträge)
* Erstattung eines Betrags, der unter dem Wert eines bestimmten Bestellartikels liegt

Weitere Informationen finden Sie unter [Ausgeben eines Credit Memo](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create){target="_blank"} in unserem Core-Benutzerhandbuch.

>[!NOTE]
>
>Bei Bestellungen, die von PayPal oder Kreditkarten verarbeitet werden, tritt ein Fehler auf, wenn Sie versuchen, eine Bestellung teilweise zurückzuerstatten, wenn sie mehr als den verbleibenden Bestellbetrag übersteigt (Originalbetrag abzüglich der Gesamtsumme der bestehenden Rückerstattungen) oder wenn Sie eine Rückerstattung für einen Betrag vornehmen, der über dem vollen Bestellbetrag liegt.

Die Einstellung [!UICONTROL Payment Action] in Ihrer [!UICONTROL Payment Settings] -Konfiguration - entweder `Authorize` oder `Authorize and Capture` - bestimmt den [grundlegenden Rückerstattungs-Workflow](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos#refund-workflow){target="_blank"} für Bestellungen.

Weitere Informationen finden Sie im Abschnitt [Einstellung der Zahlungsaktion](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create#payment-action-setting){target="_blank"} von _Ausgeben eines Credit Memo_ .
