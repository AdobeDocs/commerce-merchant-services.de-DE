---
title: Deutlicher Betrugsschutz
description: Automatisierten Schutz gegen Betrug aktivieren für [!DNL Payment Services] mit Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: 400d1f8a384fceebcd13e9496f8e218e694d2752
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Schutz vor schweren Betrugsfällen

Sie können den automatisierten Schutz von Betrug für [!DNL Payment Services] mit dem [Signifyd-Erweiterung](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce unterstützt Signifyd-Versionen 5.4.0 und höher. [!DNL Payment Services] unterstützt Signifyd-Flüsse vor und nach der Authentifizierung.

Siehe [Signifikante Dokumentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) , um mehr über die Installation und Konfiguration der Erweiterung zu erfahren.

## Integrationsbeschränkungen

Derzeit gelten die folgenden Einschränkungen für die Integration zwischen Signifyd und [!DNL Payment Services]:

* Signifyd/[!DNL Payment Services] nur unterstützt [Kreditkartenfelder](../payment-services/payments-options.md#credit-card-fields) (nicht PayPal Zahlungsschaltflächen oder Apple Pay). [!DNL Payment Services] sendet Bestelldaten, die über PayPal-Zahlungsschaltflächen und Apple PayPal an Signifyd empfangen wurden. Die Integration stellt jedoch nur Details zu Bestellungen bereit, die über Kreditkartenfelder bestellt wurden.
* Signifyd unterstützt keine Bestellungen, die von einem Händler für einen Kunden in der Admin-Konsole aufgegeben werden.
* Signifikante Bestellungen werden nicht unterstützt bei [ausgefüllte Kreditkarten](../payment-services/vaulting.md).

## Onboarding

Sie müssen direkt mit Signifyd kommunizieren, um die Erweiterung für die Verwendung mit [!DNL Payment Services]—es gibt keine [!DNL Payment Services] Konfiguration erforderlich. Sie können die Signifyd-Erweiterung im Admin nach der Installation konfigurieren. Jede Unterstützung im Zusammenhang mit dieser Erweiterung wird von Signifyd verwaltet.

Beim Onboarding mit Signifyd müssen Sie:

1. Wenden Sie sich an Signifyd , um ein neues Konto einzurichten.
1. Standardmäßig ist Signifyd [auf die Zulassungsliste gesetzt](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) um sicherzustellen, dass Signifyd nicht für andere Zahlungsoptionen Trigger macht, die es derzeit nicht unterstützt. Wenn Sie eine bestimmte Zahlungsmethode verbieten möchten, müssen Sie Änderungen vornehmen.
1. Bestätigen Sie mit Signifyd, dass PayPal keine Aufträge über die Betrugsschutzeinstellung des Händlers in Paypal zurückweist, die von Signifyd genehmigt werden könnten.
1. Aktivieren Sie die Signifyd-Erweiterung, damit sie kompatibel ist mit [!DNL Payment Services]:
   * Bei Verwendung von [!DNL Payment Services] in _Live_ -Modus, muss Signifyd im Produktionsmodus sein.
   * Bei Verwendung von [!DNL Payment Services] in _Sandbox_ -Modus, muss Signifyd sich im Testmodus befinden.

## Konfiguration

Da Signifyd Ihre Bestellungen verarbeitet, muss die Erweiterung so konfiguriert werden, dass sie sich entsprechend der Zahlungsaktion, für die Sie festgelegt haben, verhält [!DNL Payment Services].

Diese Konfigurationsoptionen sind nicht mit Zahlungsdiensten und der Signifyd-Integration kompatibel:

* Wann [!DNL Payment Services] wird mit der `Authorize` Zahlungsaktion _und_ Signifikanz ist in der `PostAuth` -Modus mit der _[!UICONTROL Decline Guarantees]_Option auf **Erstellen eines Credit Memos**.

  Grund: [!DNL Payment Services] erstellt ein Genehmigungsverfahren, das Signify und anschließend versucht, die Rückerstattung vorzunehmen.


* [!DNL Payment Services] wird mit der `Authorize and Capture` Zahlungsaktion _und_ Signifikanz ist in der `PostAuth` -Modus mit der _[!UICONTROL Decline Guarantees]_Option auf **Bestellung abbrechen**.

  Grund: [!DNL Payment Services] erstellt eine Capture-Transaktion, die Signifyd dann zu annullieren versucht.


Informationen zu [Konfigurieren der Erweiterung](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Siehe Signifikante Dokumentation zu [Erfahren Sie mehr über die Auftrags-Workflows.](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
