---
title: Aktivieren [!DNL Payment Services] für die Produktion
description: Schließen Sie den Onboarding-Prozess ab, indem Sie [!DNL Payment Services] für die Produktion.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# Aktivieren [!DNL Payment Services] für die Produktion

Sie können den Dienst in die Produktionsumgebung übernehmen und die [Onboarding-Prozess](onboard.md)gemäß den Schritten in diesem Thema, nachdem Sie:

* [Installieren](install.md) die Zahlungsdiensterweiterung
* [Konfigurieren und Verbinden](connect.md) Ihre Instanz
* [Einrichten](sandbox.md) und [test](test-validate.md) Ihre Sandbox

## Satz [!DNL Payment Services] als Zahlungsmethode

Nach [Commerce-Dienste konfigurieren](connect.md#configure-commerce-services) und aktivieren Sie entweder [Sandbox-Tests](sandbox.md#enable-sandbox-testing) oder [Live-Zahlungen](#enable-live-payments)festlegen, müssen Sie [!DNL Payment Services] als Zahlungsmethode.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicks **[!UICONTROL Enable Payment Services]**.

   Diese Option wird angezeigt, wenn Sie noch keine Konfiguration vorgenommen haben [!DNL Payment Services] als Zahlungsmethode für eine oder mehrere Ihrer Websites.

   Sie werden zum Einstellungsbereich in der Startansicht geleitet, wobei die entsprechenden Optionen erweitert sind (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), wo Sie die [!DNL Payment Services] Optionen als [Zahlungsmethode](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. In _[!UICONTROL General Configuration]_, set **[!UICONTROL Enable]**nach `Yes`.
1. Satz **[!UICONTROL Payment Action]** für beide _[!UICONTROL Credit Card Fields]_und_[!UICONTROL PayPal payment buttons]_, zu einem der folgenden Elemente:

   | Einstellung | Beschreibung |
   |---|---|
   | `Authorize` | Genehmigt den Kauf und legt die Mittel fest. Der Betrag wird erst dann zurückgezogen, wenn er vom Händler &quot;erfasst&quot;wurde. |
   | `Authorize and Capture` | Genehmigt den Kauf und der Händler &quot;erfasst&quot; die Mittel. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] unterstützt partielle Aufnahmen. Ein Händler kann Teile einer Bestellung teilweise erfassen (Rechnung). Sie können beispielsweise jedes Element einzeln erfassen oder ein Element jetzt und den Rest später.

1. Klicks **[!UICONTROL Save]**.
1. Klicks **[!UICONTROL Go to Payment Services]** zurück an die [!DNL Payment Services] Home.
1. [Cache löschen](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   Das Löschen sollte nach jeder Konfigurationsänderung erfolgen.

Siehe [Zahlungsdienste konfigurieren](settings.md) für weitere Informationen zur Konfiguration von Kreditkartenfeldern und PayPal-Zahlungsschaltflächen.

## Vollständige Onboarding des Händlers

Der nächste Schritt bei der Live-Schaltung Ihrer Geschäfte mit Zahlungsdiensten besteht darin, das Live-Onboarding abzuschließen.

Zahlungsdienste [**Erweitert** (vollständig unterstützt) und **Standard** Zahlungsoptionen (Express-Checkout)](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) und Onboarding-Flüge, abhängig vom Land, in dem Sie tätig sind, und Ihrer bevorzugten Zahlungserfahrung.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicks **[!UICONTROL Live onboarding]**.

   Diese Option wird angezeigt, wenn Sie das Live-Onboarding für [!DNL Payment Services].

1. Im _Land auswählen_ -Modal auswählen, wählen Sie das Land aus, aus dem Sie arbeiten.

   Zahlungsdienste bieten vollständige Unterstützung für alle Zahlungsoptionen in [fünf Länder](../payment-services/overview.md#availability) derzeit. Zahlungsdienste bieten Express-Checkout-Funktionen (eine Teilmenge an Zahlungsoptionen) für alle anderen Länder, die in der Länderliste aufgeführt sind.

   Das Land, das Sie aus der Liste auswählen, bestimmt die Zahlungsoptionen und den Onboarding-Fluss —[Erweitert](#advanced-onboarding) (vollständig unterstützt) oder [Standard](#standard-onboarding) (Express Checkout) - verfügbar für Sie.

>[!TIP]
>
> Sobald Sie eine Onboarding-Option (Standard oder Erweitert) ausgewählt haben und mit dieser fortfahren, müssen Sie das Onboarding erneut abschließen, um von Ihrer ersten Auswahl aus ein Upgrade oder ein Downgrade durchzuführen.

### Erweitertes Onboarding

Dieser Onboarding-Ablauf steht Händlern in [vollständig unterstützte Länder](../payment-services/overview.md#availability).

Nach der Auswahl des Landes:

1. Wählen Sie im angezeigten Modal die Option **Erweitert**.

   Für **Standard** -Option, fahren Sie mit dem [Standardmäßiger Onboarding-Fluss](#standard-onboarding).

1. Klicks **Weiter**.
1. Fahren Sie mit dem PayPal-Fluss fort, um das vollständig unterstützte erweiterte Onboarding unter Verwendung Ihrer PayPal-Kontoanmeldeinformationen (nicht Ihrer Sandbox-Kontoanmeldeinformationen) durchzuführen. _oder_ Melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>**Erweitertes Onboarding** erfordert, dass Händler [Zahlungsanspruch](#request-payments-entitlement-from-adobe) , um das Live-Onboarding zu aktivieren.

### Standard-Onboarding

Dieser standardmäßige Onboarding-Ablauf ist für Händler in verfügbaren Ländern verfügbar, für die [Nur Express-Checkout-Support](../payment-services/overview.md#availability) bereitgestellt wird.

Nach der Auswahl des Landes:

1. Im _Vertrag über Zahlungsdienste_ modal, das angezeigt wird, klicken Sie auf das **Vertrag über Zahlungsdienste** -Link, um die Zahlungsdienstvereinbarung von Adobe Commerce anzuzeigen.
1. Im _Vertrag über Zahlungsdienste_ modal, klicken Sie **Ich akzeptiere**.
1. Fahren Sie mit dem PayPal-Fluss für das Express-Checkout-Onboarding fort, verwenden Sie Ihre PayPal-Kontoanmeldeinformationen (nicht Ihre Sandbox-Kontoanmeldeinformationen) oder melden Sie sich für ein neues PayPal-Konto an.

>[!IMPORTANT]
>
>[Apple-Zahlungs- und Kreditkartenfelder](../payment-services/payments-options.md) sind nicht verfügbar für **Standard-Onboarding**.

## E-Mail-Adresse bestätigen

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

Um Ihre Geschäfte live zu schalten, fordern Sie die Zahlungsansprüche von Adobe an (für [Nur erweitertes Onboarding](#advanced-onboarding)):

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicks **[!UICONTROL Get Live Payments]** in [!DNL Payment Services] Home.

   ![Anforderungsberechtigungen](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Füllen Sie das Formular aus.
1. Ein Mitglied des Vertriebsteams wird sich mit Ihnen in Verbindung setzen.

Alternativ können Sie die Zahlungsanforderung über Adobe unter anfordern. [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Live-Onboarding** ist erst nach Genehmigung des Zahlungsanspruchs zugänglich.

## Preisstufe konfigurieren

Holen Sie sich Ihre [!DNL Payment Services] _Merchant-ID_:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie in der Startansicht auf **[!UICONTROL Settings]**. Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Wählen Sie die erforderlichen _Merchant-ID_ und senden Sie es an Ihren Vertriebsmitarbeiter, der die richtige Preisebene konfiguriert.

## Live-Zahlungen aktivieren

A _Produktions-Merchant-ID_ automatisch generiert und in der [Konfiguration](configure-admin.md). Ändern oder ändern Sie diese ID nicht.

Live-Zahlungen aktivieren:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicken Sie auf der Startseite auf **[!UICONTROL Settings]** oben rechts auf der Seite. Siehe [Startseite](payments-home.md) für weitere Informationen.
1. Im _[!UICONTROL General Configuration]_Abschnittsset **[!UICONTROL Payment mode]**nach `Production`.
1. Klicks **[!UICONTROL Save]**.
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
