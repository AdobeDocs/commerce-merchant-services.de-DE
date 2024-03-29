---
title: Konfigurieren Sie die [!DNL Quick Checkout] für die Adobe Commerce-Erweiterung
description: Erfahren Sie mehr über die Konfigurationsoptionen für die [!DNL Quick Checkout] und wie Sie die Erweiterung erfolgreich integrieren und einrichten können.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Quick Checkout] Einstellungen

[!DNL Quick Checkout] für Adobe Commerce und Magento Open Source bietet eine Konfigurationsansicht mit allen Informationen, die zum Einrichten der Erweiterung erforderlich sind.

So greifen Sie auf diese Konfigurationseinstellungen zu:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > _Einstellungen_ > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Vertrieb** und wählen **Checkout**.

   ![Quick Checkout](assets/config-new-logo-view.png){width="800" zoomable="yes"}

Siehe Abschnitt [Onboarding](../quick-checkout/onboarding.md) Thema für weitere Informationen zur Konfiguration der [!DNL Quick Checkout] für Adobe Commerce.

## Erweiterung aktivieren

![Quick Checkout](assets/enable-method.png){width="500" zoomable="yes"}

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Quick Checkout] für Ihre Website. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | website | Legen Sie die Methode oder Umgebung für Ihre [!DNL Quick Checkout]. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## Kontoanmeldeinformationen

![Quick Checkout](assets/account-creds.png){width="500" zoomable="yes"}

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL API key] | website | Ein privater Schlüssel, der von Ihrem Backend für die Interaktion mit [!DNL Bolt] APIs. |
| [!UICONTROL Publishable key] | website | Ein Schlüssel, mit dem Ihr Frontend interagiert [!DNL Bolt] APIs. |
| [!UICONTROL Signing secret] | website | Dient zur Signaturüberprüfung von Anforderungen, die von empfangen wurden [!DNL Bolt]. |

{style="table-layout:auto"}

## Diensteinstellungen

![Quick Checkout](assets/service-settings.png){width="500" zoomable="yes"}

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | website | Definieren Sie, ob Adobe Commerce die Freigabe von Checkout-Tracking-Informationen für Bolt ermöglicht. Standardmäßig aktiviert. Wenn diese Option deaktiviert ist, wirkt sich dies auf die Berichterstellung aus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | website | Ändern Sie den Navigationsfluss, nachdem der Kunde angemeldet ist. Optionen: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | website | Definieren Sie, ob [!DNL Quick Checkout] ermöglicht die automatische Anmeldung beim Checkout. Standardmäßig aktiviert. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | website | Wählen Sie das Netzwerk aus, in dem sich der Kunde automatisch anmeldet. Standardmäßig &quot;Bolt&quot;aktiviert. Optionen: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
