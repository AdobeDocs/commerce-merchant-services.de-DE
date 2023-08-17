---
title: Headless
description: Informationen zur Integration [!DNL Product Recommendations] in einer Headless-Storefront.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Headless

Sie können [!DNL Product Recommendations] in einer Headless-Storefront mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) oder einer benutzerdefinierten Frontend-Technologie, z. B. React oder Vue JS.

Benutzerdefinierte und Headless-Integratoren sollten als vorgeschlagene Implementierung auf diese Luma- und PWA-Anweisungen verweisen. Es gibt viele Möglichkeiten, Produkt Recommendations in Headless-Lösungen zu implementieren. Diese Dokumentation deckt nicht alle Szenarien ab. Integratoren müssen Veranstaltungen, Designs und Tests für ihre Implementierungen abdecken.

[!DNL Product Recommendations] erfordern [Verhaltens- und Katalogdaten](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) zum Betrieb. Der Vorgang zur Datensynchronisierung im Katalog bleibt in einer Headless-Implementierung unverändert, aber für die Erfassung von Verhaltensdaten sind Änderungen erforderlich.

>[!NOTE]
>
>Headless-Instanzen müssen Eventing implementieren, um das Produkt-Recommendations-Dashboard zu aktivieren.

Zur Integration [!DNL Product Recommendations] In einer Headless-Storefront müssen Sie:

1. Senden Sie Verhaltensdaten an Adobe Sensei, um Produktempfehlungsergebnisse zu analysieren und zu berechnen. Sie können auch zusätzliche Daten senden, um Produktempfehlungen zu ermöglichen [Metrikberichte](workspace.md).

1. Rufen Sie Produktempfehlungsergebnisse ab und rendern Sie diese Ergebnisse auf der Seite.

Sie können diese beiden Aktionen mit den verfügbaren SDKs ausführen, wie im folgenden Workflow beschrieben.

1. [Installieren](install-configure.md) die [!DNL Product Recommendations] -Modul.

1. Installieren und verwenden Sie die [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) , um die [Verhaltensereignisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   Die erforderlichen Mindestereignisse, die zurückgegeben werden [!DNL Product Recommendations] Ergebnisse:

   | Ereignis | Kategorie |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | Kasse |

   Aktivieren [Metrikberichte](workspace.md)müssen die folgenden zusätzlichen Ereignisse ausgeführt werden:

   | Ereignis | Kategorie |
   |--- | ---|
   | `impression-render` | recommendations-unit |
   | `view` | recommendations-unit |
   | `rec-click` | recommendations-unit |
   | `rec-add-to-cart-click` | Empfehlungseinheiten (wenn die Schaltfläche &quot;Zum Warenkorb hinzufügen&quot;in der Empfehlungsvorlage vorhanden ist) |

1. Wenn die Ereignisse ausgelöst werden, verwenden Sie die [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) um die Ereignisse zu verarbeiten und an Adobe Sensei zu senden.

1. Nachdem die Verhaltensdaten erfasst wurden, können Sie [erstellen](create.md) [!DNL Product Recommendations] im Admin.

1. Verwenden Sie die [RECOMMENDATIONS SDK](https://developer.adobe.com/commerce/services/product-recommendations/) , um die Empfehlungseinheiten in die Storefront zu laden. Das SDK gibt die erforderlichen Produktdaten zum Rendern von Empfehlungseinheiten auf einer Seite zurück.
