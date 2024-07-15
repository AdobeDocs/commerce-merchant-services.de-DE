---
title: Headless
description: Erfahren Sie, wie Sie [!DNL Product Recommendations] in eine Headless-Storefront integrieren.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Headless

Sie können [!DNL Product Recommendations] entweder mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) oder einer benutzerdefinierten Frontend-Technologie wie React oder Vue JS in eine Headless-Storefront integrieren.

Benutzerdefinierte und Headless-Integratoren sollten als vorgeschlagene Implementierung auf diese Luma- und PWA-Anweisungen verweisen. Es gibt viele Möglichkeiten, Produkt Recommendations in Headless-Lösungen zu implementieren. Diese Dokumentation deckt nicht alle Szenarien ab. Integratoren müssen Veranstaltungen, Designs und Tests für ihre Implementierungen abdecken.

[!DNL Product Recommendations] erfordert den Betrieb von [Verhaltens- und Katalogdaten](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html). Der Vorgang zur Datensynchronisierung im Katalog bleibt in einer Headless-Implementierung unverändert, aber für die Erfassung von Verhaltensdaten sind Änderungen erforderlich.

>[!NOTE]
>
>Headless-Instanzen müssen Eventing implementieren, um das Produkt-Recommendations-Dashboard zu aktivieren.

Um [!DNL Product Recommendations] in eine Headless-Storefront zu integrieren, müssen Sie:

1. Senden Sie Verhaltensdaten an Adobe Sensei, um Produktempfehlungsergebnisse zu analysieren und zu berechnen. Sie können auch zusätzliche Daten senden, um die Berichterstellung für Produktempfehlungen [Metriken](workspace.md) zu ermöglichen.

1. Rufen Sie Produktempfehlungsergebnisse ab und rendern Sie diese Ergebnisse auf der Seite.

Sie können diese beiden Aktionen mit den verfügbaren SDKs ausführen, wie im folgenden Workflow beschrieben.

1. [Installieren Sie](install-configure.md) das Modul [!DNL Product Recommendations].

1. Installieren Sie das [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) und verwenden Sie es, um die [Verhaltensereignisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html) auszulösen.

   Die erforderlichen Minimalereignisse, die [!DNL Product Recommendations] -Ergebnisse zurückgeben:

   | Ereignis | Kategorie |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | Kasse |

   Um die Berichterstellung für [Metriken](workspace.md) zu aktivieren, sind die folgenden zusätzlichen Ereignisse erforderlich:

   | Ereignis | Kategorie |
   |--- | ---|
   | `impression-render` | recommendations-unit |
   | `view` | recommendations-unit |
   | `rec-click` | recommendations-unit |
   | `rec-add-to-cart-click` | Empfehlungseinheiten (wenn die Schaltfläche &quot;Zum Warenkorb hinzufügen&quot;in der Empfehlungsvorlage vorhanden ist) |

1. Wenn die Ereignisse ausgelöst werden, verwenden Sie den [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) , um die Ereignisse zu verarbeiten und an Adobe Sensei zu senden.

1. Nachdem die Verhaltensdaten erfasst wurden, können Sie im Admin [ ](create.md) [!DNL Product Recommendations] erstellen.

1. Verwenden Sie das [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/) , um die Empfehlungseinheiten in die Storefront zu laden. Das SDK gibt die erforderlichen Produktdaten zum Rendern von Empfehlungseinheiten auf einer Seite zurück.
