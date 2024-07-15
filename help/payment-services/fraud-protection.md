---
title: Deutlicher Betrugsschutz
description: Aktivieren Sie den automatisierten Betrugsschutz für [!DNL Payment Services] mit Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Schutz vor schweren Betrugsfällen

Mit der Erweiterung [Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html) können Sie den automatisierten Betrugsschutz für [!DNL Payment Services] aktivieren.

Adobe Commerce unterstützt Signifyd-Versionen 5.4.0 und höher. [!DNL Payment Services] unterstützt Signifikanz-Flüsse vor und nach der Authentifizierung.

Die Signifyd/[!DNL Payment Services] -Integration bietet eine Abdeckung für Kreditkarten, Debitkarten, geweckte Karten, Checkout über die Zahlungsmethoden Admin, PayPal und Apple PayPal. Während einige Details der Transaktionen nicht zwischen Zahlungsdiensten und Signifyd geteilt werden, bietet Signifyd eine umfassende Risikoabdeckung für alle Zahlungsmethoden und gewährleistet so den größtmöglichen Schutz.

Weitere Informationen zum Installieren und Konfigurieren der Erweiterung finden Sie in der [Signifyd-Dokumentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) .

## Onboarding

Sie müssen direkt mit Signifyd kommunizieren, um die Erweiterung für die Verwendung mit [!DNL Payment Services] zu integrieren - es ist keine [!DNL Payment Services] -Konfiguration erforderlich. Sie können die Signifyd-Erweiterung im Admin nach der Installation konfigurieren. Jede Unterstützung im Zusammenhang mit dieser Erweiterung wird von Signifyd verwaltet.

Beim Onboarding mit Signifyd müssen Sie:

1. Wenden Sie sich an Signifyd , um ein neues Konto einzurichten.
1. Standardmäßig ist Signifyd [auf die Zulassungsliste gesetzt](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md), um sicherzustellen, dass Signifyd bei anderen Zahlungsoptionen, die derzeit nicht unterstützt werden, nicht Trigger. Wenn Sie eine bestimmte Zahlungsmethode verbieten möchten, müssen Sie Änderungen vornehmen.
1. Bestätigen Sie mit Signifyd, dass PayPal keine Aufträge über die Betrugsschutzeinstellung des Händlers in Paypal zurückweist, die von Signifyd genehmigt werden könnten.
1. Aktivieren Sie die Signifyd-Erweiterung, um mit [!DNL Payment Services] kompatibel zu sein:
   * Bei Verwendung von [!DNL Payment Services] im _Live_ -Modus muss Signifyd im Produktionsmodus sein.
   * Bei Verwendung von [!DNL Payment Services] im Modus _Sandbox_ muss Signifyd im Testmodus sein.

## Konfiguration

Da Signifyd bei Ihren Bestellungen einige Maßnahmen durchführt, muss die Erweiterung so konfiguriert werden, dass sie sich entsprechend der Zahlungsaktion, die Sie für [!DNL Payment Services] festgelegt haben, verhält.

Diese Konfigurationsoptionen sind nicht mit Zahlungsdiensten und der Signifyd-Integration kompatibel:

* Wenn [!DNL Payment Services] mit der `Authorize` Zahlungsaktion _und_ konfiguriert ist, befindet sich Signifyd im `PostAuth` -Modus, wobei die Option _[!UICONTROL Decline Guarantees]_auf **Kreditmemo erstellen**eingestellt ist.

  Grund: [!DNL Payment Services] erstellt eine Autorisierungstransaktion, die Signify und dann versucht, die Rückerstattung vorzunehmen.


* [!DNL Payment Services] wird mit der `Authorize and Capture` Zahlungsaktion _und_ Signifyd befindet sich im `PostAuth` Modus, wobei die Option _[!UICONTROL Decline Guarantees]_auf **Reihenfolge abbrechen**eingestellt ist.

  Grund: [!DNL Payment Services] erstellt eine Aufnahmetransaktion, die Signifyd dann auslöst.


Informationen zum Konfigurieren der Erweiterung ](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension) finden Sie in der Signifikanten Dokumentation .[

Weitere Informationen zu den Bestell-Workflows finden Sie in der umfangreichen Dokumentation zu [ .](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works)
