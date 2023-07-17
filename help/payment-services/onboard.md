---
title: Onboard [!DNL Payment Services]
description: Verbinden Sie Ihre Instanz mit [!DNL Payment Services] durch Ausführung einiger Onboarding-Schritte.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Onboard [!DNL Payment Services]

Erste Schritte mit [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source]müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit der Zahlungsfunktion zu verbinden.

## Onboarding-Fluss

![Onboarding-Fluss](assets/onboarding-diagram.svg)

Dieses Diagramm zeigt den allgemeinen Prozess für das Onboarding. [!DNL Payment Services].

Nachdem Sie das Onboarding für Sandbox- oder Live-Zahlungen abgeschlossen haben, können Sie über [!DNL Payment Services] im Admin.

Wenn sowohl Sandbox- als auch Live-Zahlungen integriert und aktiviert sind, können Sie einfach zwischen diesen Modi über die [!DNL Payment Services] Home.

## Voraussetzungen

Zur Verwendung [!DNL Payment Services]muss für Ihre Instanz Folgendes verfügbar sein:

* Dienste-Connector-Modul
* Dienst-ID-Modul
* API-Schlüssel

Die Dienste-Connector- und -Dienst-ID-Module werden während der [Installation [!DNL Payment Services]](install.md). Nach Abschluss der Installation wird in den Konfigurationseinstellungen ein neuer Abschnitt angezeigt (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) beim Erweitern **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Informationen zum Erstellen oder Zugreifen auf API-Schlüssel finden Sie unter [API-Anmeldeinformationen](#obtain-api-credentials).

## Onboarding-Schritte

1. [Installieren Sie die [!DNL Payment Services] Erweiterung](install.md#get-payment-services).
1. [API-Anmeldeinformationen abrufen](connect.md#obtain-api-credentials).
1. [Instanz verbinden](connect.md#configure-commerce-services) auf Commerce-Dienste. Diese Verbindung darf nur einmal pro Commerce-Instanz abgeschlossen werden.
1. [Einrichten des Sandbox-Dienstes](sandbox.md#enable-sandbox-testing) (oder alternativ [Live-Zahlungen ermöglichen](sandbox.md#enable-live-payments) , wenn Sie Funktionalität in einer anderen Umgebung getestet haben) mit einem PayPal Zahlungskonto zu testen.
1. [Satz [!DNL Payment Services] als Zahlungsmethode](production.md#set-payment-services-as-payment-method), um die Verarbeitung der Testzahlungen im Sandbox-Modus zu starten.
1. [Zahlungsanspruch anfordern](production.md#request-payments-entitlement-from-adobe) , um das Live-Onboarding zu aktivieren.
1. [Vollständige Onboarding des Händlers](production.md#complete-merchant-onboarding) um Live-Zahlungen für Ihre Commerce-Websites zu ermöglichen.
1. [Holen Sie sich [!DNL Payment Services] Merchant-ID](production.md#configure-pricing-tier) und übergeben Sie es an Sales , um die richtige Preisebene zu konfigurieren.
1. [Aktivieren [!DNL Payment Services] im Livemodus](production.md#enable-live-payments) um mit der Verarbeitung von Live-Zahlungen zu beginnen.
1. Testzahlungen, in beiden [Sandbox](sandbox.md#test-in-sandbox-environment) und [production](production.md#test-in-production) Umgebungen.

>[!NOTE]
>
>Wenn Sie Ihre Commerce-Services nicht in Admin (Schritt 3) konfigurieren, können Sie keine Sandbox- oder Live-Zahlungen einrichten.

## Fehlerbehebung

* [Fehlerbehebung [!DNL Payment Services] Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal-Sandbox-Konto nicht verifiziert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Verzögert [!DNL Payment Services] Berichtsdaten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Testen der Kreditkarte schlägt bei PayPal bei der Verarbeitung von Zahlungen in einer Sandbox-Umgebung fehl](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
