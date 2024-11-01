---
title: Aktivieren von [!DNL Payment Services] für die Produktion
description: Schließen Sie den Onboarding-Prozess ab, indem Sie [!DNL Payment Services] für die Produktion aktivieren.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# [!DNL Payment Services] für Produktion aktivieren

Sie können den Dienst gemäß den Schritten in diesem Thema in die Produktionsumgebung übernehmen und den [Onboarding-Prozess](onboard.md) abschließen, nachdem Sie:

* [Installieren](install.md) der Zahlungsdienst-Erweiterung
* [Konfigurieren und Verbinden](connect.md) Ihrer Instanz
* [ Richten Sie ](sandbox.md) und [test](test-validate.md) Ihre Sandbox ein.

## [!DNL Payment Services] als Zahlungsmethode festlegen

Nachdem Sie [Ihre Commerce-Dienste](connect.md#configure-commerce-services) konfiguriert und entweder [Sandbox-Tests](sandbox.md#enable-sandbox-testing) oder [Live-Zahlungen](#enable-live-payments) aktiviert haben, müssen Sie [!DNL Payment Services] als Zahlungsmethode festlegen.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Enable Payment Services]**.

   Diese Option ist sichtbar, wenn Sie [!DNL Payment Services] noch nicht als Zahlungsmethode für eine oder mehrere Ihrer Websites konfiguriert haben.

   Sie werden zum Einstellungsbereich in der Startansicht weitergeleitet, wobei die entsprechenden Optionen erweitert sind (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), wo Sie die [!DNL Payment Services]-Optionen als Ihre [Zahlungsmethode](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods){target="_blank"} aktivieren können.

1. Setzen Sie in _[!UICONTROL General Configuration]_**[!UICONTROL Enable]**auf `Yes`.
1. Setzen Sie **[!UICONTROL Payment Action]** sowohl für _[!UICONTROL Credit Card Fields]_als auch für_[!UICONTROL PayPal payment buttons]_ auf einen der folgenden Werte:

   | Einstellung | Beschreibung |
   |---|---|
   | `Authorize` | Genehmigt den Kauf und legt die Mittel fest. Der Betrag wird erst dann zurückgezogen, wenn er vom Händler &quot;erfasst&quot;wurde. |
   | `Authorize and Capture` | Genehmigt den Kauf und der Händler &quot;erfasst&quot; die Mittel. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] unterstützt partielle Aufnahmen. Ein Händler kann Teile einer Bestellung teilweise erfassen (Rechnung). Sie können beispielsweise jedes Element einzeln erfassen oder ein Element jetzt und den Rest später.

1. Klicken Sie auf **[!UICONTROL Save]**.
1. Klicken Sie auf **[!UICONTROL Go to Payment Services]** , um zur Startseite von [!DNL Payment Services] zurückzukehren.
1. [Löschen Sie Ihren Cache](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   Das Löschen sollte nach jeder Konfigurationsänderung erfolgen.

Weitere Informationen zum Konfigurieren von Kreditkartenfeldern und PayPal-Zahlungsschaltflächen finden Sie unter [Zahlungsdienste konfigurieren](settings.md) .

## Vollständige Onboarding des Händlers

Der nächste Schritt bei der Live-Schaltung Ihrer Geschäfte mit Zahlungsdiensten besteht darin, das Live-Onboarding abzuschließen.

Die Zahlungsdienste bieten je nach dem Land, in dem Sie tätig sind, und Ihrer bevorzugten Zahlungserfahrung die Zahlungsoptionen [**Erweitert** (vollständig unterstützt) und **Standard** (Express-Checkout)](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) sowie Onboarding-Datenflüsse.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Live onboarding]**.

   Diese Option ist sichtbar, wenn Sie das Live-Onboarding für [!DNL Payment Services] noch nicht abgeschlossen haben.

1. Wählen Sie im Modal _Land auswählen_ das Land aus, aus dem Sie arbeiten.

   Zahlungsdienste bieten derzeit volle Unterstützung für alle Zahlungsoptionen in [fünf Ländern](../payment-services/overview.md#availability). Zahlungsdienste bieten Express-Checkout-Funktionen (eine Teilmenge an Zahlungsoptionen) für alle anderen Länder, die in der Länderliste aufgeführt sind.

   Das Land, das Sie aus der Liste auswählen, bestimmt die Zahlungsoptionen und den für Sie verfügbaren Onboarding-Fluss:[Erweitert](#advanced-onboarding) (vollständig unterstützt) oder [Standard](#standard-onboarding) (Express Checkout).

>[!TIP]
>
> Sobald Sie eine Onboarding-Option (Standard oder Erweitert) ausgewählt haben und mit dieser fortfahren, müssen Sie das Onboarding erneut abschließen, um von Ihrer ersten Auswahl aus ein Upgrade oder ein Downgrade durchzuführen.

### Erweitertes Onboarding

Dieser Onboarding-Fluss steht Händlern in [vollständig unterstützten Ländern](../payment-services/overview.md#availability) zur Verfügung.

Nach der Auswahl des Landes:

1. Wählen Sie im angezeigten Modal **Erweitert** aus.

   Fahren Sie bei der Option **Standard** mit dem standardmäßigen Onboarding-Fluss [3} fort.](#standard-onboarding)

1. Klicken Sie auf **Weiter**.
1. Fahren Sie mit dem PayPal-Fluss fort, um das vollständig unterstützte erweiterte Onboarding durchzuführen. Verwenden Sie dazu Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) _oder_, und melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>**Erweitertes Onboarding** erfordert, dass Händler die Berechtigung für Zahlungen anfordern](#request-payments-entitlement-from-adobe), um das Live-Onboarding zu aktivieren.[

### Standard-Onboarding

Dieser standardmäßige Onboarding-Fluss ist für Händler in verfügbaren Ländern verfügbar, für die [nur Express-Checkout-Unterstützung](../payment-services/overview.md#availability) bereitgestellt wird.

Nach der Auswahl des Landes:

1. Klicken Sie im angezeigten Modal _Zahlungsdienstvereinbarung_ auf den Link **Zahlungsdienstvereinbarung** , um die Zahlungsdienstvereinbarung von Adobe Commerce anzuzeigen.
1. Klicken Sie im Modal _Zahlungsdienstvereinbarung_ auf **Ich akzeptiere**.
1. Fahren Sie mit dem PayPal-Fluss für das Express-Checkout-Onboarding fort, verwenden Sie Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) oder melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>[Apple Pay and Credit card fields](../payment-services/payments-options.md) sind nicht für **Standard Onboarding** verfügbar.

## E-Mail-Adresse bestätigen

1. Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   Die Schaltfläche &quot;_[!UICONTROL Live onboarding]_&quot; ist nicht mehr sichtbar, und das Textfeld &quot;[!UICONTROL Live payments pending]&quot; wird angezeigt.

   In diesem Textfeld werden Sie möglicherweise aufgefordert, Ihre E-Mail-Adresse mit PayPal zu bestätigen, um das Onboarding abzuschließen.

1. Wenn Sie aufgefordert werden, Ihre E-Mail-Adresse zu bestätigen, überprüfen Sie Ihre E-Mail auf die von PayPal gesendete Bestätigungsnachricht und klicken Sie auf , um Ihre E-Mail-Adresse zu bestätigen.
1. Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Aktualisieren Sie das Browser-Fenster.

   Wenn Ihr PayPal-Händler das Onboarding genehmigt, sollte Ihnen eine Benachrichtigung angezeigt werden, dass Ihr Zahlungssystem sich im Sandbox-Modus befindet und keine Live-Zahlungen verarbeitet.

   >[!IMPORTANT]
   >
   >Wenn Sie die Einwilligung zu [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] für die Verarbeitung Ihrer Zahlungen (in Ihren PayPal-Kontoeinstellungen) widerrufen, können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] verarbeitet werden. Auf Ihrer Zahlungsdienst-Startseite wird ein Warnhinweis über die widerrufene Zustimmung angezeigt.

## Zahlungsanspruch von Adobe anfordern

Damit Ihre Stores live geschaltet werden können, fordern Sie die Zahlungsansprüche von Adobe an (nur für [Erweitertes Onboarding](#advanced-onboarding)):

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf **[!UICONTROL Get Live Payments]** auf Ihrer [!DNL Payment Services] Startseite.

   ![Anforderungsberechtigungen](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Füllen Sie das Formular aus.
1. Ein Mitglied des Vertriebsteams wird sich mit Ihnen in Verbindung setzen.

Alternativ können Sie unter [business.adobe.com](https://business.adobe.com/resources/payment-services.html) eine Zahlungsanforderung von Adobe anfordern.

>[!IMPORTANT]
>
>**Live-Onboarding** ist erst verfügbar, nachdem der Zahlungsanspruch genehmigt wurde.

## Preisstufe konfigurieren

[!DNL Payment Services] _Händler-ID_ abrufen:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie in der Startansicht auf **[!UICONTROL Settings]**. Weitere Informationen finden Sie unter [Startseite](payments-home.md) .
1. Wählen Sie die erforderliche _Merchant-ID_ aus und senden Sie sie an Ihren Vertriebsmitarbeiter, der die richtige Preisebene konfiguriert.

Weitere Informationen zu Zahlungsvorgängen finden Sie unter [Verarbeitung auf Stufe 2 und Stufe 3](levels-card-payment-transactions.md) .

## Live-Zahlungen aktivieren

Eine _Produktions-Merchant-ID_ wird automatisch generiert und in die [Konfiguration](configure-admin.md) eingefügt. Ändern oder ändern Sie diese ID nicht.

Live-Zahlungen aktivieren:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf der Startseite oben rechts auf der Seite auf **[!UICONTROL Settings]** . Weitere Informationen finden Sie unter [Startseite](payments-home.md) .
1. Setzen Sie im Abschnitt _[!UICONTROL General Configuration]_**[!UICONTROL Payment mode]**auf `Production`.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. [Löschen Sie Ihren Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management){target="_blank"}.

   >[!IMPORTANT]
   >
   >Wenn Sie Ihren Cache nicht löschen, können Kunden beim Checkout keine PayPal-Zahlungsoptionen sehen.

Wenn Sie zurück zur Startseite von [!DNL Payment Services] navigieren, wird die Sandbox-Zahlungsmodusmeldung nicht mehr angezeigt, da Sie jetzt Live-Zahlungen verarbeiten.

Weitere Informationen zu den alten Konfigurationsoptionen finden Sie unter [Konfigurieren in Admin](configure-admin.md) .

>[!IMPORTANT]
>
>Wenn Sie die Einwilligung zu [!DNL Payment Services] für die Verarbeitung Ihrer Zahlungen (in Ihren PayPal-Kontoeinstellungen) widerrufen, können Bestellungen in Ihrem Geschäft nicht von [!DNL Payment Services] verarbeitet werden. Wenn Sie die Zahlungsverarbeitung erneut aktivieren möchten, müssen Sie das Onboarding erneut abschließen. Auf Ihrer Zahlungsdienst-Startseite wird ein Warnhinweis über die widerrufene Zustimmung angezeigt.

## Produktionstest

Es wird dringend empfohlen, dass Sie Zahlungen in der Produktion mit echten Kreditkarten und Banken testen, bevor Sie diese Funktion den Käufern zur Verfügung stellen.

Weitere Informationen finden Sie unter [Testen und Validieren](test-validate.md) .
