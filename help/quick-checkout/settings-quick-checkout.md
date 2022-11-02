---
title: "Konfigurieren Sie die [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"
description: "Erfahren Sie mehr über die Konfigurationsoptionen für die [!DNL Quick Checkout] und wie Sie die Erweiterung erfolgreich integrieren und einrichten können."
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# [!DNL Quick Checkout] settings

[!DNL Quick Checkout] für Adobe Commerce und Magento Open Source bietet eine Konfigurationsansicht mit allen Informationen, die zum Einrichten der Erweiterung erforderlich sind.

So greifen Sie auf diese Konfigurationseinstellungen zu:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > _Einstellungen_ > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Vertrieb** und wählen Sie **Checkout**.

   ![Quick Checkout](assets/quick-checkout-main-view-react.png)

Siehe Abschnitt [Onboarding](../quick-checkout/onboarding.md) Thema für weitere Informationen zur Konfiguration der [!DNL Quick Checkout] für Adobe Commerce.

## Erweiterung aktivieren

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Enable] | website | Aktivieren oder Deaktivieren [!DNL Quick Checkout] für Ihre Website. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | website | Legen Sie die -Methode oder -Umgebung für Ihre [!DNL Quick Checkout]. Optionen: [!UICONTROL Sandbox] / [!UICONTROL Production] |

## Kontoanmeldeinformationen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL API key] | website | Ein privater Schlüssel, der von Ihrem Backend für die Interaktion mit [!DNL Bolt] APIs. |
| [!UICONTROL Publishable key] | website | Ein Schlüssel, mit dem Ihr Frontend interagiert [!DNL Bolt] APIs. |
| [!UICONTROL Signing secret] | website | Dient zur Signaturüberprüfung von Anforderungen, die von empfangen wurden [!DNL Bolt]. |

## Diensteinstellungen

| Feld | Anwendungsbereich | Beschreibung |
|---|---|---|
| [!UICONTROL Title] | Store-Ansicht | Fügen Sie den Text für die Anzeige als Titel für diese Zahlungsoption in der Ansicht Zahlungsmethode während des Checkouts hinzu. Optionen: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | Die [Zahlungsaktion](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} für die angegebene Zahlungsmethode. Optionen: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | website | Aktivieren oder deaktivieren Sie den Debug-Modus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | website | Definieren Sie, ob Adobe Commerce die Freigabe von Checkout-Tracking-Informationen für Bolt zulässt. Standardmäßig aktiviert. Wenn diese Option deaktiviert ist, wirkt sich dies auf die Berichterstellung aus. Optionen: [!UICONTROL Yes] / [!UICONTROL No] |
