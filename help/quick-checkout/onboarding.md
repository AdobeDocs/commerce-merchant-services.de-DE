---
title: '"Onboard the [!DNL Quick Checkout] für Adobe Commerce-Erweiterung"'
description: '"Erfahren Sie, wie die [!DNL Quick Checkout] kann von Ihrer Adobe Commerce-Instanz profitieren und zeigen, wie Sie die Erweiterung erfolgreich integrieren und einrichten können."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: ac55bf6354c8f5569ad83dc0ac2671b34c98d303
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# [!DNL Quick Checkout] Onboarding

Erste Schritte mit der Verwendung von [!DNL Quick Checkout] Für die Adobe Commerce-Erweiterung müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit unserer Checkout-Funktion zu verbinden.

1. [Erweiterung abrufen](#get-extension).
1. [Erstellen Sie ein Produktions- oder Sandbox-Handelskonto mit [!DNL Bolt]](#create-account-with-bolt). Geben Sie alle erforderlichen Informationen zur Überprüfung Ihrer Identität an.
1. [Stellen Sie die eindeutige [!DNL API Key] und [!DNL Publishable Key] generiert in [!DNL Bolt]](#obtain-api-credentials).
1. [Richten Sie einen Zahlungsdienstleister im [!DNL Bolt] account](#configure-payment-providers).
1. [Setzen Sie das Dropdown-Menü &quot;Aktivieren&quot;auf &quot;Ja&quot;](#enable-extension) , um die Erweiterung zu aktivieren.
1. [Diensteinstellungen definieren](#complete-admin-configuration) , um die [!DNL Quick Checkout] -Erweiterung.
1. [Klicken Sie auf die Schaltfläche Konfiguration speichern .](#enable-live-quick-checkout) , um die Erweiterung zu aktivieren.

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

Vor der Konfiguration [!DNL Quick Checkout] In Ihrem Adobe Commerce-Administrator muss eine [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} und [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} Handelskonten in [!DNL Bolt]. Geben Sie alle erforderlichen Details an, um ein Konto in [!DNL Bolt].

Siehe Abschnitt [Testen und Validieren](../quick-checkout/testing.md) für weitere Informationen.

## API-Anmeldeinformationen abrufen

So verwenden Sie die [!DNL Quick Checkout] benötigen [!DNL Bolt] eindeutige Schlüssel. Folgendes abrufen [!DNL API keys] durch Navigation zu **Entwickler** > **API** > **Schlüssel** im **Bolt Merchant Dashboard**.

- [!DNL API key]: Ein privater Schlüssel, der von Ihrem Backend für die Interaktion mit [!DNL Bolt] APIs.
- [!DNL Publishable key]: Ein Schlüssel, mit dem Ihr Frontend interagiert [!DNL Bolt] APIs.

Siehe [[!DNL Bolt] Umgebungsdetails](https://help.bolt.com/developers/references/environment-details/#about-keys)Seite {target=&quot;_blank&quot;} mit Informationen zu API und [!DNL Publishable keys] für [!DNL Quick Checkout] -Erweiterung.

>[!CAUTION]
>
> Sie müssen [!DNL API keys] für Sandbox- und Produktionsumgebungen.

## Zahlungsdienstleister konfigurieren

Gehen Sie wie im Abschnitt [Prozessoreinrichtung](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;} developer [!DNL Bolt] Seite.

## Erweiterung aktivieren

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > _Einstellungen_ > **Konfiguration**.
1. Erweitern Sie im linken Bereich **Vertrieb** und wählen Sie **Checkout**.

   ![Quick Checkout](assets/admin-view.png)

1. Im [!DNL Quick Checkout] Ansicht, festlegen **Aktivieren** nach `Yes`.
1. Wählen Sie die zu verwendende Methode (Sandbox oder Produktion) aus.

   - Sandbox zu Test- und Entwicklungszwecken
   - Herstellung zur Verarbeitung von Transaktionen mit dem Live-Zahlungsverarbeiter

1. Validieren Sie die Anmeldeinformationen, nachdem Sie Ihre eindeutige API bereitgestellt haben und [!DNL Publishable keys].

>[!CAUTION]
>
> Sie müssen eine eindeutige API bereitstellen und [!DNL Publishable keys] bevor Sie die Erweiterung aktivieren, sehen die Kunden ein Zahlungsformular und können keine Bestellung aufgeben.

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

## Hilfe erhalten

Der Onboarding-Prozess soll Sie durch die erforderlichen Schritte zur Einrichtung und Aktivierung der [!DNL Express Checkout] Funktionalität. Wenden Sie sich über Ihren zugewiesenen Slack an das Adobe Commerce-Technikerteam. [Adobe Beta-Programmkanal](http://adobe-beta-programs.slack.com/) Hilfskanal.

Siehe [Testen und Validieren](../quick-checkout/testing.md) für weitere Informationen.
