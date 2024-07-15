---
title: Einrichten der Test-Sandbox
description: Verwenden Sie ein PayPal-Sandbox-Konto, um [!DNL Payment Services] im Testmodus zu verwenden.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install
source-git-commit: bfb49e3602cc80f97817a8fd8d7c4684a3a3bcd2
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Einrichten der Test-Sandbox

Bevor Sie mit dem Onboarding einer Sandbox beginnen, müssen Sie sich für ein kostenloses PayPal-Entwicklerkonto registrieren und sowohl Handelskonten (für das Onboarding) als auch Kaufkonten (für das Testen Ihres Checkouts) erstellen. Sie können bei Bedarf mehrere Entwicklerkonten erstellen.

Mit einem PayPal-Sandbox-Konto können Sie [!DNL Payment Services] im Testmodus verwenden. PayPal erfordert die Verwendung eines von PayPal Developer Portal generierten Business Sandbox-Testkontos, einer E-Mail-Adresse und eines Kennworts für das Onboarding einer Sandbox. *Erstellen Sie während des Sandbox-Onboarding-Prozesses kein weiteres Konto.*

## Sandbox-Onboarding

So schließen Sie das Onboarding einer Sandbox ab:

1. Navigieren Sie zur Seite [PayPal-Entwicklerkonto](https://developer.paypal.com/developer/accounts/).
1. Klicken Sie auf &quot;**[!UICONTROL Log in to Dashboard]**&quot;und melden Sie sich mit Ihrem vorhandenen PayPal Developer Portal-generierten Business-Sandbox-Testkonto an oder klicken Sie auf &quot;**Registrieren**&quot;, um ein Konto zu erstellen.
1. Erstellen Sie ein PayPal-Sandbox-Konto:
   1. Gehen Sie zu _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. Klicken Sie auf **[!UICONTROL Create account]**.

      Wenn Sie während des PayPal-Onboarding-Prozesses der Sandbox ein PayPal-Sandbox-Konto erstellt haben, müssen Sie [Ihre Onboarding-Sandbox zurücksetzen](#reset-your-sandbox-account), da Sie Ihre E-Mail nicht verifizieren können.

   1. Wählen Sie **[!UICONTROL Business]** als Kontotyp aus und klicken Sie auf **[!UICONTROL Create]**.
   1. Klicken Sie im Abschnitt _[!UICONTROL Sandbox Accounts]_auf die drei Punkte in der Spalte_[!UICONTROL Manage accounts]_ für das von Ihnen erstellte Sandbox-Konto.
   1. Klicken Sie auf **[!UICONTROL View/edit account]**.

      ![PayPal - Sandbox-Konto anzeigen/bearbeiten](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Kopieren Sie die E-Mail-ID und das systemgenerierte Kennwort und speichern Sie sie für die zukünftige Verwendung.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Sandbox onboarding]**.

   Diese Option ist sichtbar, wenn Sie das Einstieg in die Sandbox für [!DNL Payment Services] noch nicht abgeschlossen haben.

   Eine Sandbox-Händler-ID wird automatisch generiert und in [Einstellungen](settings.md) eingetragen. Ändern oder ändern Sie diese ID nicht.

   Sie erhalten ein PayPal-Fenster, in dem Sie ein PayPal-Konto anschließen können, um mit der Annahme von Zahlungen zu beginnen.

1. Geben Sie die E-Mail-Adresse und das Kennwort des PayPal-Sandbox-Kontos ein, das Sie in Schritt 3 generiert haben (nicht die Informationen zu Ihrem PayPal-Geschäftskonto), und geben Sie Ihr Land oder Ihre Region an.
1. Klicken Sie auf **[!UICONTROL Next]**.

   ![PayPal - Connect PayPal-Konto für Zahlungen](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Folgen Sie weiterhin dem Fluss PayPal und verwenden Sie Ihre zuvor gespeicherten Sandbox-Kontoanmeldeinformationen.
1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   Die Schaltfläche **[!UICONTROL Sandbox onboarding]** ist nicht mehr sichtbar und Sie sehen den Text &quot;Sandbox-Zahlungen ausstehend&quot;.

Wenn Ihr PayPal-Sandbox-Onboarding genehmigt wird, sollte Ihnen eine Benachrichtigung angezeigt werden, dass Ihr Zahlungssystem sich derzeit im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

>[!IMPORTANT]
>
>Wenn Sie die Einwilligung zu [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] für die Verarbeitung Ihrer Zahlungen (in Ihren PayPal-Kontoeinstellungen) widerrufen, können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] verarbeitet werden. Auf Ihrer Zahlungsdienst-Homepage wird ein Warnhinweis über die widerrufene Zustimmung angezeigt. Um den Warnhinweis zu schließen, klicken Sie auf **[!UICONTROL Do not show again]**.

### Sandbox-Konto zurücksetzen

Wenn Sie während des PayPal-Onboarding-Prozesses der Sandbox PayPal ein PayPal-Sandbox-Konto erstellt haben, müssen Sie Ihre Onboarding-Sandbox zurücksetzen, da Sie Ihre E-Mail nicht verifizieren können.

So setzen Sie Ihr Sandbox-Konto zurück:

1. Klicken Sie auf **[!UICONTROL Reset sandbox]**. [Erstellen Sie ein PayPal-Business-Sandbox-Konto](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Klicken Sie auf **[!UICONTROL Sandbox onboarding]** und führen Sie die nächsten Schritte aus.

## Kontakttelefonnummer aktivieren

Mit der Telefonnummer Kontakt können Sie die von PayPal gesammelten Telefonnummern von Ihren Kunden abrufen. PayPal sammelt immer Telefonnummern von PayPal-Kontoinhabern, um ihre Identitäten zu bestätigen und sie zu kontaktieren, um Probleme auf ihren Konten zu beheben oder ihre Erfüllung abzuschließen. PayPal rät jedoch von der Verwendung von Kontakttelefonnummern direkt vom Händler ab, da dies den Verkauf beeinträchtigen kann. Weitere Informationen finden Sie in der Dokumentation zum [PayPal Abrufen von Telefonnummern für Kontakte](https://www.sandbox.paypal.com/businessmanage/preferences/website) .

Diese Funktion ist standardmäßig auf `off` eingestellt. Wenn Sie diese Option aktivieren, können Store-Administratoren Telefonnummern anzeigen, wenn ein Kunde einen Branded Checkout-Fluss außerhalb der Checkout-Seite durchführt.

>[!IMPORTANT]
>
>Diese Einstellung gilt nicht für andere Checkout-Flüsse.

## Test in Sandbox-Umgebung

Weitere Informationen finden Sie unter [Testen und Validieren](test-validate.md) .
