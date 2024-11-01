---
title: Test in der Staging-Umgebung
description: Erfahren Sie, wie Sie [!DNL Product Recommendations] aus Ihrer Produktionsumgebung für Testzwecke in Ihrer Staging-Umgebung verwenden können.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Test in der Staging-Umgebung

Bevor Sie Empfehlungen in Ihrer Produktionsumgebung bereitstellen, testen Sie den Dienst in einer Nicht-Produktionsumgebung, um sicherzustellen, dass alles wie erwartet funktioniert.

[!DNL Product Recommendations] gibt Produkte basierend auf [Verhaltensdaten von Käufern](events.md) zurück, die aus Ihrer Storefront erfasst wurden. In einer Nicht-Produktionsumgebung verfügen Sie jedoch wahrscheinlich nicht über Verhaltensdaten von Käufern. Der einzige Empfehlungstyp, den Sie ohne Verhaltensdaten testen können, ist `More like this`. Für diesen Empfehlungstyp sind keine Eingabedaten erforderlich, da er eine Übereinstimmung mit der direkten Ähnlichkeit von Inhalten verwendet.

Die folgenden Empfehlungstypen erfordern Verhaltensdaten:

- Am häufigsten angezeigt
- Anzeige, Anzeige,
- kaufte das, kaufte es

Wie können Sie Ihre Empfehlungen in einer Nicht-Produktionsumgebung mit Verhaltensdaten testen? Es gibt mehrere Möglichkeiten.

## Abrufen von Empfehlungen aus der Produktionsumgebung (empfohlen)

Mit Adobe Commerce können Sie Empfehlungen aus Ihrer Produktionsumgebung abrufen und in Ihrer Nicht-Produktionsumgebung eine Vorschau davon anzeigen, indem Sie den SaaS-Datenraum [umschalten](settings.md).

Um Empfehlungen aus Ihrer Produktionsumgebung abzurufen, müssen Sie Folgendes sicherstellen:

- Die Storefront-Datenerfassung ist in der Produktionsumgebung [konfiguriert und aktiviert](install-configure.md).
- Der Katalog in Ihrer Nicht-Produktionsumgebung entspricht weitgehend dem in der Produktionsumgebung. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die in den Empfehlungseinheiten zurückgegebenen Produkte denen in der Produktionsumgebung sehr ähnlich sind.

## Generieren von Verhaltensdaten in Nicht-Produktionsumgebungen

1. Stellen Sie das Modul `magento/product-recommendations` in einer Nicht-Produktionsumgebung bereit, in der die Katalogdaten Ihrem Produktionskatalog ähnlich sind.

1. Verwenden Sie eine der Nicht-Produktions-Datenraum-IDs für die [Konfiguration](../landing/saas.md#saas-configuration) im Admin.

1. Generieren Sie die Daten selbst, indem Sie auf Ihre Storefront klicken, um das Verhalten der tatsächlichen Käufer zu imitieren (oder erstellen Sie ein Automatisierungsskript). Durch Ihre Tests generieren Sie Verhaltensereignisse in Ihrer Nicht-Produktionsumgebung. Diese Ereignisse werden verwendet, um die Produktaffinitäten zu erstellen, die Empfehlungen unterstützen. Zum Testen deutet [!DNL Commerce] darauf hin, dass Sie mit den folgenden Empfehlungstypen interagieren:

   - Am häufigsten angezeigt - Erfordert minimale Eingabedaten. Benutzer müssen Produkte anzeigen.
   - Anzeige, Anzeige: Erfordert mehrere Benutzer, mehrere Produkte anzuzeigen.
   - Hat dies gekauft und gekauft - Erfordert, dass mehrere Benutzer mehrere Produkte kaufen.

### Einschränkungen

- Die Verhaltens- und Katalogdaten aus dem nicht produktionsbezogenen [SaaS-Datenraum](../landing/saas.md#saas-configuration) identifizieren eine isolierte Umgebung, in der die resultierenden Produktempfehlungen vollständig auf den Verhaltensdaten basieren, die auf der zugehörigen Storefront generiert wurden.

- Da Sie nicht über große Mengen von Verhaltensdaten verfügen, sind Eingabedaten für die Berechnung von Produktverknüpfungen selten. Diese Daten werden jedoch weiterhin an Sensei gesendet, um die maschinellen Lernmodelle zu berechnen und Empfehlungen basierend auf den in dieser Umgebung generierten Daten bereitzustellen.
