---
title: Onboard [!DNL Payment Services]
description: Verbinden Sie Ihre Instanz mit der [!DNL Payment Services] Funktionalität, indem Sie einige Onboarding-Schritte ausführen.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 5481b19f95908b441e12c4700c51649921dabb08
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Onboard [!DNL Payment Services]

Um mit der Verwendung von [!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] zu beginnen, müssen Sie einige Onboarding-Schritte ausführen, um Ihre Instanz mit der Zahlungsfunktion zu verbinden.

## Onboarding-Fluss

Dieses Flussdiagramm zeigt den allgemeinen Prozess für das Onboarding von [!DNL Payment Services].

![Onboarding-Fluss](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

>[!NOTE]
>
> Bei Adobe Commerce-Versionen 2.4.7 oder höher können Sie den Schritt der Marketplace-Erweiterung überspringen, da [!DNL Payment Services] standardmäßig verfügbar ist.

Nachdem Sie das Onboarding für Sandbox- oder Live-Zahlungen abgeschlossen haben, können Sie über &quot;[!DNL Payment Services]&quot;in der Admin-Konsole auf Finanzberichte zugreifen.

Wenn sowohl Sandbox- als auch Live-Zahlungen integriert und aktiviert sind, können Sie über die Startseite von [!DNL Payment Services] einfach zwischen diesen Modi wechseln.

## Voraussetzungen

Um [!DNL Payment Services] verwenden zu können, müssen alle abhängigen Module aktiviert sein und die folgenden für Ihre Instanz verfügbar sein:

* Dienste-Connector-Modul
* Dienst-ID-Modul
* API-Schlüssel

Die Dienste-Connector- und -Dienst-ID-Module werden während der [Installation von [!DNL Payment Services]](install.md) automatisch installiert.

Nach Abschluss der Installation wird in den Konfigurationseinstellungen (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) ein neuer Abschnitt angezeigt, wenn Sie **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**erweitern.

Informationen zum Erstellen oder Zugreifen auf API-Schlüssel finden Sie unter [API-Anmeldeinformationen](#obtain-api-credentials).

## Onboarding-Schritte

1. [Installieren Sie die  [!DNL Payment Services] Erweiterung](install.md#get-payment-services).
1. [API-Anmeldeinformationen abrufen](connect.md#obtain-api-credentials).
1. [Verbinden Sie Ihre Instanz](connect.md#configure-commerce-services) mit Commerce Services. Diese Verbindung darf nur einmal pro Commerce-Instanz hergestellt werden.
1. [Richten Sie den Sandbox-Dienst](sandbox.md#enable-sandbox-testing) ein (oder fahren Sie alternativ mit [Aktivieren von Live-Zahlungen](sandbox.md#enable-live-payments) fort, wenn Sie die Funktionalität in einer anderen Umgebung getestet haben), indem Sie ein PayPal-Zahlungskonto testen.
1. [Legen Sie  [!DNL Payment Services]  als Zahlungsmethode fest](production.md#set-payment-services-as-payment-method), um im Sandbox-Modus mit der Verarbeitung der Testzahlungen zu beginnen.
1. [Fordern Sie den Zahlungsanspruch an](production.md#request-payments-entitlement-from-adobe), um das Live-Onboarding zu aktivieren.
1. [Vervollständigen Sie das Onboarding des Händlers](production.md#complete-merchant-onboarding) , um Live-Zahlungen für Ihre Commerce-Websites zu ermöglichen.
1. [Besorgen Sie sich Ihre  [!DNL Payment Services] Merchant-ID](production.md#configure-pricing-tier) und geben Sie sie an Sales weiter, um die richtige Preisebene zu konfigurieren.
1. [Aktivieren Sie [!DNL Payment Services] im Live-Modus](production.md#enable-live-payments) , um mit der Verarbeitung von Live-Zahlungen zu beginnen.
1. Testen von Zahlungen in den Umgebungen [sandbox](sandbox.md#test-in-sandbox-environment) und [production](production.md#test-in-production) .

>[!NOTE]
>
>Wenn Sie Ihre Commerce-Dienste nicht in Admin (Schritt 3) konfigurieren, können Sie keine Sandbox- oder Live-Zahlungen einrichten.

## Fehlerbehebung

* [Fehlerbehebung bei der [!DNL Payment Services] Installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal-Sandbox-Konto nicht verifiziert](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Verzögerte [!DNL Payment Services] Berichtsdaten](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Testen der Kreditkarte schlägt mit PayPal fehl, wenn Zahlungen in einer Sandbox-Umgebung verarbeitet werden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
