---
title: Erstattungen
description: Erstellen von Erstattungen für [!DNL Payment Services] Bestellungen im Admin als Teil des Credit Memo-Prozesses.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Erstattungen

Erstattungen [!DNL Payment Services] Bestellungen werden im Admin als Teil des Credit Memo-Prozesses erstellt. Ein Kreditmemo ist ein Dokument, das den Betrag angibt, der dem Kunden für eine vollständige oder teilweise Rückerstattung zusteht, die auf einen Kauf angewendet oder dem Kunden direkt zurückerstattet werden kann. Kreditkarten können nur für Bestellungen ausgestellt werden, die [fakturiert](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}.

Siehe [Credit Memos](https://docs.magento.com/user-guide/sales/credit-memos.html){target=&quot;_blank&quot;} in unserem Core-Benutzerhandbuch finden Sie weitere Informationen und erfahren, wie Sie Kreditkarten ausgeben und drucken können.

Für Bestellungen, die mit PayPal oder einer Kreditkarte verarbeitet werden, können Sie:

* Den Gesamtbetrag der Bestellung zurückerstatten
* Erstattung eines Teilbetrags einer Bestellung (oder mehrerer Teilbeträge)
* Erstattung eines Betrags, der unter dem Wert eines bestimmten Bestellartikels liegt

Siehe [Erstellen eines KreditMemos](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target=&quot;_blank&quot;} in unserem Benutzerhandbuch für weitere Informationen.

>[!NOTE]
>
>Bei Bestellungen, die von PayPal oder Kreditkarten verarbeitet werden, tritt ein Fehler auf, wenn Sie versuchen, eine Bestellung teilweise zurückzuerstatten, wenn sie mehr als den verbleibenden Bestellbetrag übersteigt (Originalbetrag abzüglich der Gesamtsumme der bestehenden Rückerstattungen) oder wenn Sie eine Rückerstattung für einen Betrag vornehmen, der über dem vollen Bestellbetrag liegt.

Die [!UICONTROL Payment Action] -Einstellung in [!UICONTROL Payment Settings] configuration - Entweder `Authorize` oder `Authorize and Capture`—bestimmt die [Grundlegender Erstattungs-Workflow](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target=&quot;_blank&quot;} für Bestellungen.

Siehe [Bereich für die Zahlungsaktion](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;} von _Erstellen eines KreditMemos_ für weitere Informationen.
