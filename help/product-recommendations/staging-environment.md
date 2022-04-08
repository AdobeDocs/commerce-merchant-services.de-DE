---
title: Test in der Staging-Umgebung
description: Learn how to use [!DNL Product Recommendations] from your production environment in your staging environment for testing purposes.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Test in der Staging-Umgebung

Bevor Sie Empfehlungen in Ihrer Produktionsumgebung bereitstellen, sollten Sie sie in einer Nicht-Produktionsumgebung testen, um sicherzustellen, dass alles wie erwartet funktioniert.

[!DNL Product Recommendations] Rückkehrprodukte auf der Grundlage [Verhaltensdaten von Käufern](behavioral-data.md) von Ihrer Storefront erfasst. In einer Nicht-Produktionsumgebung verfügen Sie jedoch wahrscheinlich nicht über Verhaltensdaten von Käufern. The only recommendation type that you can test without behavioral data is `More like this`. This recommendation type does not require any input data, as it uses a direct content similarity match.

Die folgenden Empfehlungstypen erfordern Verhaltensdaten:

- Am häufigsten angezeigt
- Anzeige, Anzeige,
- Bought this, bought that

Wie können Sie Ihre Empfehlungen in einer Nicht-Produktionsumgebung mit Verhaltensdaten testen? There are a couple of options.

## Abrufen von Empfehlungen aus der Produktionsumgebung (empfohlen)

Adobe Commerce allows you to fetch recommendations from your production environment and preview them in your non-production environment by [switching](settings.md) the SaaS data space.

Um Empfehlungen aus Ihrer Produktionsumgebung abzurufen, müssen Sie Folgendes sicherstellen:

- Storefront data collection is [configured and enabled](install-configure.md) on production.
- Ihr Nicht-Produktions-Umgebungs-Katalog ist größtenteils mit dem in der Produktion vorhandenen Katalog identisch. Using similar catalogs ensures that the products returned in the recommendation units closely mimic those on production.

## Generieren von Verhaltensdaten in Nicht-Produktionsumgebungen

1. Stellen Sie die `magento/product-recommendations` -Modul in eine Nicht-Produktionsumgebung übertragen, in der die Katalogdaten Ihrem Produktionskatalog ähneln.

1. Verwenden Sie eine der nicht produktionsbezogenen Datenspeicherungs-IDs für [Konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html) im Admin.

1. Generate the data yourself by clicking around your storefront to mimic the behavior of actual shoppers (or create an automation script). Durch Ihre Tests generieren Sie Verhaltensereignisse in Ihrer Nicht-Produktionsumgebung. Diese Ereignisse werden verwendet, um die Produktaffinitäten zu erstellen, die Empfehlungen unterstützen. für Tests, [!DNL Commerce] empfiehlt, dass Sie mit den folgenden Empfehlungstypen interagieren:

   - Am häufigsten angezeigt - Erfordert minimale Eingabedaten. Benutzer müssen Produkte anzeigen.
   - Anzeige, Anzeige: Erfordert mehrere Benutzer, mehrere Produkte anzuzeigen.
   - Bought this, bought that - Requires multiple users to purchase multiple products.

### Einschränkungen

- Die Verhaltens- und Katalogdaten aus dem SaaS-Datenraum ohne Produktionscharakter identifizieren eine isolierte Umgebung, in der die resultierenden Produktempfehlungen vollständig auf den Verhaltensdaten basieren, die auf der zugehörigen Storefront generiert wurden.

- Da Sie nicht über große Mengen von Verhaltensdaten verfügen, sind Eingabedaten für die Berechnung von Produktverknüpfungen selten. Diese Daten werden jedoch weiterhin an Sensei gesendet, um die maschinellen Lernmodelle zu berechnen und Empfehlungen basierend auf den in dieser Umgebung generierten Daten bereitzustellen.
