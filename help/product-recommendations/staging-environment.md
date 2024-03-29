---
title: Test in der Staging-Umgebung
description: Verwendung von [!DNL Product Recommendations] aus Ihrer Produktionsumgebung in Ihrer Staging-Umgebung zu Testzwecken.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Test in der Staging-Umgebung

Bevor Sie Empfehlungen in Ihrer Produktionsumgebung bereitstellen, sollten Sie sie in einer Nicht-Produktionsumgebung testen, um sicherzustellen, dass alles wie erwartet funktioniert.

[!DNL Product Recommendations] Rückkehrprodukte auf der Grundlage [Verhaltensdaten von Käufern](behavioral-data.md) von Ihrer Storefront erfasst. In einer Nicht-Produktionsumgebung verfügen Sie jedoch wahrscheinlich nicht über Verhaltensdaten von Käufern. Der einzige Empfehlungstyp, den Sie ohne Verhaltensdaten testen können, ist `More like this`. Für diesen Empfehlungstyp sind keine Eingabedaten erforderlich, da er eine Übereinstimmung mit der direkten Ähnlichkeit von Inhalten verwendet.

Die folgenden Empfehlungstypen erfordern Verhaltensdaten:

- Am häufigsten angezeigt
- Anzeige, Anzeige,
- kaufte das, kaufte es

Wie können Sie Ihre Empfehlungen in einer Nicht-Produktionsumgebung mit Verhaltensdaten testen? Es gibt mehrere Möglichkeiten.

## Abrufen von Empfehlungen aus der Produktionsumgebung (empfohlen)

Adobe Commerce ermöglicht es Ihnen, Empfehlungen aus Ihrer Produktionsumgebung abzurufen und sie in Ihrer Nicht-Produktionsumgebung in der Vorschau anzuzeigen, indem Sie [Switching](settings.md) den SaaS-Datenraum.

Um Empfehlungen aus Ihrer Produktionsumgebung abzurufen, müssen Sie Folgendes sicherstellen:

- Storefront-Datenerfassung: [konfiguriert und aktiviert](install-configure.md) auf die Produktion.
- Ihr Nicht-Produktions-Umgebungs-Katalog ist größtenteils mit dem in der Produktion vorhandenen Katalog identisch. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die in den Empfehlungseinheiten zurückgegebenen Produkte denen in der Produktion sehr ähnlich sind.

## Generieren von Verhaltensdaten in Nicht-Produktionsumgebungen

1. Stellen Sie die `magento/product-recommendations` -Modul in eine Nicht-Produktionsumgebung übertragen, in der die Katalogdaten Ihrem Produktionskatalog ähneln.

1. Verwenden Sie eine der nicht produktionsbezogenen Datenspeicherungs-IDs für [Konfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) im Admin.

1. Generieren Sie die Daten selbst, indem Sie auf Ihre Storefront klicken, um das Verhalten der tatsächlichen Käufer zu imitieren (oder erstellen Sie ein Automatisierungsskript). Durch Ihre Tests generieren Sie Verhaltensereignisse in Ihrer Nicht-Produktionsumgebung. Diese Ereignisse werden verwendet, um die Produktaffinitäten zu erstellen, die Empfehlungen unterstützen. für Tests, [!DNL Commerce] empfiehlt, dass Sie mit den folgenden Empfehlungstypen interagieren:

   - Am häufigsten angezeigt - Erfordert minimale Eingabedaten. Benutzer müssen Produkte anzeigen.
   - Anzeige, Anzeige: Erfordert mehrere Benutzer, mehrere Produkte anzuzeigen.
   - Hat dies gekauft und gekauft - Erfordert, dass mehrere Benutzer mehrere Produkte kaufen.

### Einschränkungen

- Die Verhaltens- und Katalogdaten aus dem SaaS-Datenraum ohne Produktionscharakter identifizieren eine isolierte Umgebung, in der die resultierenden Produktempfehlungen vollständig auf den Verhaltensdaten basieren, die auf der zugehörigen Storefront generiert wurden.

- Da Sie nicht über große Mengen von Verhaltensdaten verfügen, sind Eingabedaten für die Berechnung von Produktverknüpfungen selten. Diese Daten werden jedoch weiterhin an Sensei gesendet, um die maschinellen Lernmodelle zu berechnen und Empfehlungen basierend auf den in dieser Umgebung generierten Daten bereitzustellen.
