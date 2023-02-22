---
title: Aktivieren [!DNL Payment Services] für die Produktion
description: Schließen Sie den Onboarding-Prozess ab, indem Sie [!DNL Payment Services] für die Produktion.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Aktivieren [!DNL Payment Services] für die Produktion

Sie können den Dienst in die Produktion einbauen und die [Onboarding-Prozess](onboard.md)gemäß den Schritten in diesem Thema, nachdem Sie:

* [Installieren](install.md) die Zahlungsdiensterweiterung
* [Konfigurieren und Verbinden](connect.md) Ihre Instanz
* [Einrichten](sandbox.md) und [test](test-validate.md) Ihre Sandbox

## Satz [!DNL Payment Services] als Zahlungsmethode

Nach [Commerce-Dienste konfigurieren](connect.md#configure-commerce-services) und aktivieren Sie entweder [Sandbox-Tests](sandbox.md#enable-sandbox-testing) oder [Live-Zahlungen](#enable-live-payments)festlegen, müssen Sie [!DNL Payment Services] als Zahlungsmethode.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Enable Payment Services]**.

   Diese Option wird angezeigt, wenn Sie noch keine Konfiguration vorgenommen haben [!DNL Payment Services] als Zahlungsmethode für eine oder mehrere Ihrer Websites.

   Sie werden zum Einstellungsbereich in der Startansicht geleitet, wobei die entsprechenden Optionen erweitert sind (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), wo Sie die [!DNL Payment Services] Optionen als [Zahlungsmethode](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. In _[!UICONTROL General Configuration]_, set **[!UICONTROL Enable]**nach `Yes`.
1. Satz **[!UICONTROL Payment Action]** für beide _[!UICONTROL Credit Card Fields]_und_[!UICONTROL PayPal Smart Buttons]_, zu einem der folgenden Elemente:

   | Einstellung | Beschreibung |
   |---|---|
   | `Authorize` | Genehmigt den Kauf und legt die Mittel fest. Der Betrag wird erst dann zurückgezogen, wenn er vom Händler &quot;erfasst&quot;wurde. |
   | `Authorize and Capture` | Genehmigt den Kauf und der Händler &quot;erfasst&quot; die Mittel. |

1. Klicken **[!UICONTROL Save]**.
1. Klicken **[!UICONTROL Go to Payment Services]** zurück an die [!DNL Payment Services] Home.
1. [Cache löschen](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   Das Löschen sollte nach jeder Konfigurationsänderung erfolgen.

Siehe [Zahlungsdienste konfigurieren](settings.md) Weitere Informationen zur Konfiguration von Kreditkartenfeldern und PayPal-Smart-Schaltflächen.

## Vollständige Onboarding des Händlers

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Live onboarding]**.

   Diese Option wird angezeigt, wenn Sie das Live-Onboarding für [!DNL Payment Services].

   Sie erhalten ein PayPal-Fenster.

1. Fahren Sie mit dem Fluss PayPal fort, verwenden Sie Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) oder melden Sie sich für ein neues PayPal-Konto an.
1. Navigieren Sie in der Admin-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   Die _[!UICONTROL Live onboarding]_-Schaltfläche nicht mehr sichtbar ist und ein &quot;[!UICONTROL Live payments pending]&quot;.

   In diesem Textfeld werden Sie möglicherweise aufgefordert, Ihre E-Mail-Adresse mit PayPal zu bestätigen, um das Onboarding abzuschließen.

1. Wenn Sie aufgefordert werden, Ihre E-Mail-Adresse zu bestätigen, überprüfen Sie Ihre E-Mail auf die von PayPal gesendete Bestätigungsnachricht und klicken Sie auf , um Ihre E-Mail-Adresse zu bestätigen.
1. Navigieren Sie in der Admin-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Aktualisieren Sie das Browser-Fenster.

   Wenn Ihr PayPal-Händler das Onboarding genehmigt, sollte Ihnen eine Benachrichtigung angezeigt werden, dass Ihr Zahlungssystem sich im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

   >[!IMPORTANT]
   >
   >Wenn Sie die Zustimmung zum [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] für die Verarbeitung Ihrer Zahlungen (in den Einstellungen Ihres PayPal-Kontos) können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services]. Auf Ihrer Zahlungsdienst-Startseite wird ein Warnhinweis über die widerrufene Zustimmung angezeigt.

## Zahlungsanspruch von Adobe anfordern

Um das Live-Onboarding zu aktivieren, müssen Sie einen Zahlungsanspruch von Adobe anfordern:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken **[!UICONTROL Get Live Payments]** in [!DNL Payment Services] Home.

   ![Anforderungsberechtigungen](assets/request-entitlements.png)

1. Füllen Sie das Formular aus.
1. Ein Mitglied des Vertriebsteams wird sich mit Ihnen in Verbindung setzen.

Alternativ können Sie Zahlungsansprüche von Adobe anfordern unter [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Live-Onboarding** ist erst nach Genehmigung des Zahlungsanspruchs zugänglich.

## Preisstufe konfigurieren

Um [!DNL Payment Services] _Merchant-ID_:


1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie in der Startansicht auf **[!UICONTROL Settings]**. Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Wählen Sie die erforderlichen _Merchant-ID_ und senden Sie es an Ihren Vertriebsmitarbeiter, der die richtige Preisebene konfiguriert.

## Live-Zahlungen aktivieren

A _Produktions-Merchant-ID_ automatisch generiert und in der [Konfiguration](configure-admin.md). Ändern oder ändern Sie diese ID nicht.

So aktivieren Sie Live-Zahlungen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf der Startseite auf **[!UICONTROL Settings]** oben rechts auf der Seite. Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Im _[!UICONTROL General Configuration]_Abschnittsset **[!UICONTROL Payment mode]**nach `Production`.
1. Klicken **[!UICONTROL Save]**.
1. [Cache löschen](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >Wenn Sie Ihren Cache nicht löschen, können Kunden beim Checkout keine PayPal-Zahlungsoptionen sehen.

Wenn Sie zurück zu [!DNL Payment Services] Home: Die Sandbox-Zahlungsmodusmeldung wird nicht mehr angezeigt, da Sie jetzt Live-Zahlungen verarbeiten.

Siehe [In Admin konfigurieren](configure-admin.md) für ältere Konfigurationsoptionen.

>[!IMPORTANT]
>
>Wenn Sie die Zustimmung zum [!DNL Payment Services] für die Verarbeitung Ihrer Zahlungen (in den Einstellungen Ihres PayPal-Kontos) können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services]. Wenn Sie die Zahlungsverarbeitung erneut aktivieren möchten, müssen Sie das Onboarding erneut abschließen. Auf Ihrer Zahlungsdienst-Startseite wird ein Warnhinweis über die widerrufene Zustimmung angezeigt.

## Produktionstest

Es wird dringend empfohlen, dass Sie Zahlungen in der Produktion mit echten Kreditkarten und Banken testen, bevor Sie diese Funktion den Käufern zur Verfügung stellen.

Siehe [Testen und Validieren](test-validate.md) für weitere Informationen.
