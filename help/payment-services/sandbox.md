---
title: Einrichten der Test-Sandbox
description: Verwenden eines PayPal-Sandbox-Kontos zur Verwendung [!DNL Payment Services] im Testmodus.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Einrichten der Test-Sandbox

Bevor Sie mit dem Onboarding einer Sandbox beginnen, müssen Sie sich für ein kostenloses PayPal-Entwicklerkonto registrieren und sowohl Handelskonten (für das Onboarding) als auch Kaufkonten (für das Testen Ihres Checkouts) erstellen. Sie können bei Bedarf mehrere Entwicklerkonten erstellen.

Mit einem PayPal-Sandbox-Konto können Sie [!DNL Payment Services] im Testmodus. PayPal erfordert die Verwendung eines von PayPal Developer Portal generierten Business Sandbox-Testkontos, einer E-Mail und eines Kennworts für das Onboarding von Sandboxes. Erstellen Sie während des Sandbox-Onboarding-Prozesses kein anderes Konto.

Wenn Sie während des PayPal-Onboarding-Prozesses der Sandbox ein Konto erstellt haben, müssen Sie Ihre Onboarding-Sandbox zurücksetzen, da Sie Ihre E-Mail nicht verifizieren können.

So setzen Sie Ihr Sandbox-Konto zurück:

1. Klicken **[!UICONTROL Reset sandbox]**. Siehe [PayPal erstellen Sie ein Business-Sandbox-Konto](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) Dokumentation finden Sie weitere Informationen.
1. Klicken **[!UICONTROL Sandbox onboarding]** und führen Sie die nächsten Schritte aus.

So schließen Sie das Onboarding einer Sandbox ab:

1. Navigieren Sie zum [Seite &quot;PayPal-Entwicklerkonto&quot;](https://developer.paypal.com/developer/accounts/).
1. Klicken **[!UICONTROL Log in to Home]** und melden Sie sich mit Ihren vorhandenen Anmeldedaten beim PayPal Developers-Konto an oder klicken Sie auf **Anmelden** , um ein Konto zu erstellen.
1. Erstellen Sie ein PayPal-Sandbox-Konto:
   1. Navigieren Sie zu _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**.
   1. Klicken **[!UICONTROL Create account]**.
   1. Auswählen **[!UICONTROL Business]** als Kontotyp und klicken Sie auf **[!UICONTROL Create]**.
   1. Im _[!UICONTROL Sandbox Accounts]_klicken Sie auf die drei Punkte im_[!UICONTROL Manage accounts]_ -Spalte für das von Ihnen erstellte Sandbox-Konto.
   1. Klicken **[!UICONTROL View/edit account]**.

      ![PayPal - Sandbox-Konto anzeigen/bearbeiten](assets/onboarding-viewedit-sandbox.png)

   1. Kopieren Sie die E-Mail-ID und das systemgenerierte Kennwort und speichern Sie sie für die zukünftige Verwendung.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Sandbox onboarding]**.

   Diese Option ist sichtbar, wenn Sie das Onboarding von Sandboxes für [!DNL Payment Services].

   Eine Sandbox-Merchant-ID wird automatisch generiert und in die [settings](settings.md). Ändern oder ändern Sie diese ID nicht.

   Sie erhalten ein PayPal-Fenster, in dem Sie ein PayPal-Konto anschließen können, um Zahlungen zu akzeptieren.

1. Geben Sie die E-Mail-Adresse Ihres Geschäftskontos sowie Ihr Land oder Ihre Region ein und klicken Sie auf **[!UICONTROL Next]**.

   ![PayPal - PayPal-Konto für Zahlungen verbinden](assets/paypal-connectacct.png)

1. Folgen Sie weiterhin dem Fluss PayPal und verwenden Sie Ihre zuvor gespeicherten Sandbox-Kontoanmeldeinformationen.
1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   Die **[!UICONTROL Sandbox onboarding]** -Schaltfläche nicht mehr sichtbar ist und der Text &quot;Sandbox-Zahlungen ausstehend&quot;angezeigt wird.

Wenn Ihr PayPal-Sandbox-Onboarding genehmigt wird, sollte Ihnen eine Benachrichtigung angezeigt werden, dass Ihr Zahlungssystem sich derzeit im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

>[!IMPORTANT]
>
>Wenn Sie die Zustimmung zum [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] für die Verarbeitung Ihrer Zahlungen (in den Einstellungen Ihres PayPal-Kontos) können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services].

## Kontakttelefonnummer aktivieren

Mit der Telefonnummer Kontakt können Sie die von PayPal gesammelten Telefonnummern von Ihren Kunden abrufen. PayPal sammelt immer Telefonnummern von PayPal-Kontoinhabern, um ihre Identitäten zu bestätigen und sie zu kontaktieren, um Probleme auf ihren Konten zu beheben oder ihre Erfüllung abzuschließen. PayPal rät jedoch von der Verwendung von Kontakttelefonnummern direkt vom Händler ab, da dies den Verkauf beeinträchtigen kann. Siehe [PayPal erhalten Telefonnummern](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) Dokumentation finden Sie weitere Informationen.

Diese Funktion ist `off` Standardmäßig. Wenn Sie diese Option aktivieren, können Store-Administratoren Telefonnummern anzeigen, wenn ein Kunde einen Branded Checkout-Fluss außerhalb der Checkout-Seite durchführt.

>[!IMPORTANT]
>
>Diese Einstellung gilt nicht für andere Checkout-Flüsse.

## Test in Sandbox-Umgebung

Siehe [Testen und Validieren](test-validate.md) für weitere Informationen.
