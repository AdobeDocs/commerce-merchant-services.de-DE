---
title: Onboard the [!DNL Express Checkout] für die Adobe Commerce-Erweiterung
description: Erfahren Sie, wie Sie [!DNL Express Checkout] kann von Ihrer Adobe Commerce-Instanz profitieren und zeigen, wie Sie die Erweiterung erfolgreich integrieren und einrichten können.
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# [!DNL Express Checkout] Onboarding

>[!IMPORTANT]
>
> Diese Funktion ist nur für Benutzer des Early Adopter Program (EAP) gedacht und steht noch nicht allen Kunden zur Verfügung. Derzeit auf US-Kunden beschränkt. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

Erste Schritte mit der Verwendung von [!DNL Express Checkout] Für die Adobe Commerce-Erweiterung müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit unserer Checkout-Funktion zu verbinden.

1. [Erweiterung abrufen](#get-extension).
1. [Erstellen eines Produktions- oder Sandbox-Händlerkontos mit Bolt](#create-account-with-bolt). Geben Sie alle erforderlichen Informationen zur Überprüfung Ihrer Identität an.
1. [Stellen Sie den eindeutigen API-Schlüssel und den in Bolt generierten Schlüssel für die Veröffentlichung bereit.](#obtain-api-credentials).
1. [Einen Zahlungsdienstleister im Bolt-Konto einrichten](#configure-payment-providers).
1. [Setzen Sie das Dropdown-Menü &quot;Aktivieren&quot;auf &quot;Ja&quot;](#enable-extension) , um die Erweiterung zu aktivieren.
1. [Diensteinstellungen definieren](#complete-admin-configuration) , um die [!DNL Express Checkout] -Erweiterung.
1. [Klicken Sie auf die Schaltfläche Konfiguration speichern .](#enable-live-express-checkout) , um die Erweiterung zu aktivieren.

>[!NOTE]
>
> Wenn Sie Ihre Bolt-Konten nicht konfigurieren (Schritt 2 oben), können Sie Ihre Sandbox- oder Produktionsumgebungen nicht einrichten.

## Voraussetzungen

Um die [!DNL Express Checkout]müssen Sie Folgendes für Bolt verfügbar haben:

- Unterstützte Zahlungsdienstleister
- Handels- und Produktionskonto in Bolt
- API- und Veröffentlichungsschlüssel, der in Bolt generiert wurde

Siehe Abschnitt [Voraussetzungen](../express-checkout/prerequisites.md) für weitere Informationen.

Siehe [API-Anmeldeinformationen](#obtain-api-credentials) , um zu erfahren, wie Sie API-Schlüssel für Ihre Instanz erstellen oder darauf zugreifen können.

## Erweiterung abrufen

Siehe [install](../express-checkout/install.md) Thema für detaillierte Informationen zum Abrufen der Erweiterung.

## Konto mit Bolt erstellen

Vor der Konfiguration [!DNL Express Checkout] In Ihrem Adobe Commerce-Administrator muss eine [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} und [Sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} Handelskonto in Bolt. Geben Sie alle erforderlichen Details an, um ein Konto in Bolt zu erstellen.

Siehe Abschnitt [Testen und Validieren](../express-checkout/testing.md) für weitere Informationen.

## API-Anmeldeinformationen abrufen

So verwenden Sie die [!DNL Express Checkout] benötigen Sie eindeutige Bolt-Schlüssel. Rufen Sie die folgenden API-Schlüssel ab, indem Sie zu **Entwickler** > **API** > **Schlüssel** im **Bolt Merchant Dashboard**.

- API-Schlüssel: Ein privater Schlüssel, der von Ihrem Backend zur Interaktion mit Bolt-APIs verwendet wird.
- Veröffentlichungsschlüssel: Ein Schlüssel, der von Ihrem Frontend zur Interaktion mit Bolt-APIs verwendet wird.

Siehe [Details zur Bolzen-Umgebung](https://help.bolt.com/developers/references/environment-details/#about-keys)Seite {target=&quot;_blank&quot;} mit Informationen zu API- und Veröffentlichungsschlüsseln für die [!DNL Express Checkout] -Erweiterung.

>[!CAUTION]
>
> Sie müssen API-Schlüssel für Sandbox- und Produktionsumgebungen erstellen.

## Zahlungsdienstleister konfigurieren

Gehen Sie wie im Abschnitt [Prozessoreinrichtung](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} Entwickler-Bolt-Seite.

## Erweiterung aktivieren

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > **Konfiguration** > **Checkout** , um auf die Seite Checkout-Admin-Konfiguration zuzugreifen.

![Express Checkout](../assets/admin-view.png)

1. Im [!DNL Express Checkout] Ansicht, festlegen **Aktivieren** nach `Yes`.
1. Wählen Sie die zu verwendende Methode (Produktion oder Sandbox) aus.
1. Überprüfen Sie die Anmeldeinformationen, nachdem Sie Ihre eindeutigen API- und veröffentlichungsfähigen Schlüssel bereitgestellt haben.

>[!CAUTION]
>
> Sie müssen eindeutige API- und veröffentlichbare Schlüssel bereitstellen, bevor Sie die Erweiterung aktivieren. Andernfalls wird den Kunden ein Zahlungsformular angezeigt und sie können keine Bestellung aufgeben.

## Vollständige Admin-Konfiguration

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Stores** > **Konfiguration** > **Checkout** , um auf die allgemeine Checkout Admin-Konfigurationsseite zuzugreifen.
1. Im _Diensteinstellungen_ Geben Sie alle Details an, die zum Aktivieren der Erweiterung erforderlich sind.
1. Satz _Zahlungsaktion_ as:

   - Autorisieren: Erfassen Sie Transaktionen nicht automatisch bei der Autorisierung.
   - Autorisieren und Erfassen: Erfassen Sie die Transaktion automatisch nach Genehmigung.

Weitere Informationen zu den standardmäßigen Adobe Commerce-Checkout-Optionen finden Sie im Abschnitt [Kasse](https://docs.magento.com/user-guide/configuration/sales/checkout.html) Thema.

## Aktivieren des Live-Express-Checkouts

So aktivieren Sie die [!DNL Express Checkout] für die Adobe Commerce-Erweiterung:

1. Klicken **Konfiguration speichern**.

## Hilfe erhalten

Der Onboarding-Prozess soll Sie durch die erforderlichen Schritte zur Einrichtung und Aktivierung aller [!DNL Express Checkout] Funktionalität. Wenden Sie sich für Unterstützung und Fragen an den Adobe Commerce-Support.

Siehe Abschnitt [Testen und Validieren](../express-checkout/testing.md) für weitere Informationen.
