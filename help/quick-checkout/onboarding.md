---
title: "Onboard the [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"
description: "Erfahren Sie, wie die [!DNL Quick Checkout] kann von Ihrer Adobe Commerce-Instanz profitieren und zeigen, wie Sie die Erweiterung erfolgreich integrieren und einrichten können."
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 1f2305df7566cd77a6be161cc9d1265c0291171c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] Onboarding

Erste Schritte mit der Verwendung von [!DNL Quick Checkout] Für die Adobe Commerce-Erweiterung müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit unserer Checkout-Funktion zu verbinden.

![Quick Checkout](assets/overview-admin-panel.png)

1. [Erweiterung abrufen](#get-extension).
1. [Erstellen Sie ein Produktions- oder Sandbox-Handelskonto mit [!DNL Bolt]](#create-account-with-bolt). Geben Sie alle erforderlichen Informationen zur Überprüfung Ihrer Identität an.
1. [Stellen Sie die eindeutige [!DNL API Key] und [!DNL Publishable Key]](#obtain-api-credentials) generiert in [!DNL Bolt].
1. [Richten Sie einen Zahlungsdienstleister im [!DNL Bolt] account](#configure-payment-providers).
1. [Setzen Sie das Dropdown-Menü &quot;Aktivieren&quot;auf &quot;Ja&quot;](#enable-extension) , um die Erweiterung zu aktivieren.
1. [Diensteinstellungen definieren](#complete-admin-configuration) , um die [!DNL Quick Checkout] -Erweiterung.
1. [Klicken Sie auf Konfiguration speichern .](#enable-live-quick-checkout) -Schaltfläche, um die Erweiterung zu aktivieren.
1. Scope auf **Hauptwebsite** und [Klicken Sie auf Callback-URL konfigurieren .](#check-shopper-valid-account) Schaltfläche.

Wenn Gainsight aktiviert ist, wird die **Tour** -Schaltfläche in [!DNL Quick Checkout] Admin Panel Info [!DNL Quick Checkout] für Adobe Commerce:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > Erweitert:

   ![Quick Checkout](assets/gainsight-admin.png)

Wenn Gainsight nicht aktiviert ist, fahren Sie mit den Onboarding-Schritten fort.

Siehe [[!DNL Quick Checkout] Admin-Bereich](../quick-checkout/admin-panel.md) für weitere Informationen.

>[!NOTE]
>
> Wenn Sie Ihre [!DNL Bolt] -Konten können Sie Ihre Sandbox- oder Produktionsumgebungen nicht einrichten.

## Voraussetzungen

Um die [!DNL Quick Checkout]müssen Sie über Folgendes verfügen für [!DNL Bolt]:

- Unterstützte Zahlungsdienstleister
- Handels- und Produktionskonto in [!DNL Bolt]
- API und [!DNL Publishable key] generiert in [!DNL Bolt]

Siehe Abschnitt [Voraussetzungen](../quick-checkout/prerequisites.md) für weitere Informationen.

Siehe [API-Anmeldeinformationen](#obtain-api-credentials) Hier erfahren Sie, wie Sie Ihre [!DNL API keys] für Ihre Instanz.

## Erweiterung abrufen

Siehe [install](../quick-checkout/install.md) Thema für detaillierte Informationen zum Abrufen der Erweiterung.

## Konto erstellen mit [!DNL Bolt]

Vor der Konfiguration [!DNL Quick Checkout] In Ihrem Adobe Commerce-Administrator muss eine [Sandbox](https://merchant-sandbox.bolt.com/register?platform=magento2){target=&quot;_blank&quot;} und [production](https://merchant.bolt.com/register?platform=magento2){target=&quot;_blank&quot;} Handelskonten in [!DNL Bolt]. Geben Sie alle erforderlichen Details an, um ein Konto in [!DNL Bolt].

Siehe Abschnitt [Testen und Validieren](../quick-checkout/testing.md) für weitere Informationen.

## API-Anmeldeinformationen abrufen

So verwenden Sie die [!DNL Quick Checkout] benötigen [!DNL Bolt] eindeutige Schlüssel und [!DNL signing secret]. Folgendes abrufen [!DNL API keys] durch Navigation zu **Entwickler** > **API** > **Schlüssel** im **Bolt Merchant Dashboard**.

- [!DNL API key]: Ein privater Schlüssel, der von Ihrem Backend für die Interaktion mit [!DNL Bolt] APIs.
- [!DNL Publishable key]: Ein Schlüssel, mit dem Ihr Frontend interagiert [!DNL Bolt] APIs.
- [!DNL Signing secret]: Dient zur Signaturüberprüfung von Anforderungen, die von empfangen wurden [!DNL Bolt].

   ![Quick Checkout](assets/account-credentials.png)

Siehe [[!DNL Bolt] Umgebungsdetails](https://help.bolt.com/developers/references/environment-details/#about-keys)Seite &quot;{target=&quot;_blank&quot;}&quot;, auf der Sie Informationen zu Schlüsseln und zum Signieren von Geheimnissen erhalten. [!DNL Bolt] für [!DNL Quick Checkout] -Erweiterung.

>[!CAUTION]
>
> Sie müssen [!DNL API keys] für Sandbox- und Produktionsumgebungen.

## Zahlungsdienstleister konfigurieren

Gehen Sie wie im Abschnitt [Prozessoreinrichtung](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;} developer [!DNL Bolt] Seite.

## Erweiterung aktivieren

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > _Einstellungen_ > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Vertrieb** und wählen Sie **Checkout**.
1. Im [!DNL Quick Checkout] Ansicht, festlegen **Aktivieren** nach `Yes`.

![Quick Checkout](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> Die Felder für den SchnellCheckout sind nur sichtbar, wenn **Aktivieren** auf `Yes`.

1. Wählen Sie die zu verwendende Methode (Sandbox oder Produktion) aus.

   - Sandbox zu Test- und Entwicklungszwecken
   - Herstellung zur Verarbeitung von Transaktionen mit dem Live-Zahlungsverarbeiter

1. Validieren Sie die Anmeldeinformationen, nachdem Sie Ihre eindeutige API bereitgestellt haben und [!DNL Publishable keys].

![Quick Checkout](assets/quick-checkout-main-view-react.png)

Siehe Abschnitt [Einstellungen](../quick-checkout/settings-quick-checkout.md) Thema für weitere Informationen zu den Konfigurationsoptionen für die [!DNL Quick Checkout] für die Adobe Commerce-Erweiterung.

>[!CAUTION]
>
> Sie müssen eine eindeutige API bereitstellen und [!DNL Publishable] -Schlüssel vor Aktivierung der Erweiterung angezeigt, da sonst Kunden ein Zahlungsformular sehen und keine Bestellung tätigen können.

## Vollständige Admin-Konfiguration

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > **Konfiguration** > **Checkout** , um auf die allgemeine Checkout Admin-Konfigurationsseite zuzugreifen.
1. Im _Diensteinstellungen_ Geben Sie alle Details an, die zum Aktivieren der Erweiterung erforderlich sind.
1. Satz _Zahlungsaktion_ zu einer der beiden Optionen:

   - `Authorize`: Erfassen Sie Transaktionen nicht automatisch bei der Autorisierung.
   - `Authorize and Capture`: Erfassen Sie die Transaktion automatisch nach Genehmigung.

Weitere Informationen zu den standardmäßigen Adobe Commerce-Checkout-Optionen finden Sie im Abschnitt [Kasse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) Thema.

## Aktivieren der Live-Schnellüberprüfung

So aktivieren Sie die [!DNL Quick Checkout] für die Adobe Commerce-Erweiterung:

1. Stellen Sie sicher, dass die [!UICONTROL Enable] Dropdown-Liste auf **Ja** , um die Erweiterung zu aktivieren.
1. Klicken **Konfiguration speichern**.

## Prüfen des gültigen Kontos des Käufers

So prüfen Sie, ob der Käufer über eine [!DNL Bolt] Konto:

1. Ändern Sie den Umfang in **Hauptwebsite**.
1. Klicken Sie auf **Callback-URL konfigurieren** Schaltfläche. Dies ermöglicht [!DNL Bolt] um festzustellen, ob der Käufer über ein Konto verfügt. Ist dies der Fall, wird das OTP-Popup angezeigt.

   >[!CAUTION]
   >
   > Wechsel des Umfangs zum **Hauptwebsite** stellt sicher, dass die richtige URL festgelegt ist. Jede Website kann über mehrere Domänen verfügen.

Siehe [Site-, Store- und Ansichtsbereich](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)Thema {target=&quot;_blank&quot;} für weitere Informationen zu Bereichen in Adobe Commerce.

## Diensteinstellungen konfigurieren

![Quick Checkout](assets/service-settings.png)

1. Satz **Checkout-Tracking aktivieren** nach `Yes`.

   >[!CAUTION]
   >
   > Die Deaktivierung dieser Option wirkt sich auf die Berichterstellung aus, da Adobe Commerce Kasse-Tracking-Informationen nicht mit Bolt teilen darf.

1. Wählen Sie die **Nächste Phase nach der Anmeldung** Option, um den Navigationsfluss zu ändern, nachdem sich der Kunde angemeldet hat. Standardmäßig ist der Wert auf **Zahlungen** Seite.

## Hilfe erhalten

Der Onboarding-Prozess soll Sie durch die erforderlichen Schritte zur Einrichtung und Aktivierung der [!DNL Express Checkout] Funktionalität.

Kontaktieren Sie den Adobe Commerce-Support über [Adobe Commerce Help Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en) für jede Unterstützung.

Siehe [Testen und Validieren](../quick-checkout/testing.md) für weitere Informationen.
