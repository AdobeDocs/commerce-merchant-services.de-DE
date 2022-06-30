---
title: Headless
description: Informationen zur Integration [!DNL Product Recommendations] in einer Headless-Storefront.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Headless

Sie können [!DNL Product Recommendations] in einer Headless-Storefront mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) oder einer benutzerdefinierten Frontend-Technologie, z. B. React oder Vue JS.

[!DNL Product Recommendations] erfordern [Verhaltensdaten und Katalogdaten](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) zum Betrieb. Der Vorgang zur Datensynchronisierung im Katalog bleibt in einer Headless-Implementierung unverändert, aber für die Erfassung von Verhaltensdaten sind Änderungen erforderlich.

Integration [!DNL Product Recommendations] In einer Headless-Storefront müssen Sie:

1. Senden Sie Verhaltensdaten an Adobe Sensei, um Produktempfehlungsergebnisse zu analysieren und zu berechnen. Sie können auch zusätzliche Daten senden, um Produktempfehlungen zu ermöglichen [Metrikberichte](workspace.md).

1. Rufen Sie Produktempfehlungsergebnisse ab und rendern Sie diese Ergebnisse auf der Seite.

Sie können diese beiden Aktionen mit den verfügbaren SDKs ausführen, wie im folgenden Workflow beschrieben.

1. [Installieren](install-configure.md) die [!DNL Product Recommendations] -Modul.

1. Installieren und verwenden Sie die [Adobe Commerce Storefront Event SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) , um [Verhaltensereignisse](https://devdocs.magento.com/recommendations/events.html).

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
   | `rec-add-to-cart-click` | Empfehlungseinheit (wenn eine Schaltfläche zum Warenkorb in der Empfehlungsvorlage vorhanden ist) |

1. Wenn die Ereignisse ausgelöst werden, verwenden Sie die [Adobe Commerce Storefront Event Collector](https://devdocs.magento.com/shared-services/storefront-event-collector.html) um die Ereignisse zu verarbeiten und an Adobe Sensei zu senden.

1. Nachdem die Verhaltensdaten erfasst wurden, können Sie [erstellen](create.md) [!DNL Product Recommendations] im Admin.

1. Verwenden Sie die [Recommendations SDK](https://devdocs.magento.com/recommendations/recs-api.html) , um die Empfehlungseinheiten in die Storefront zu laden. Das SDK gibt die erforderlichen Produktdaten zum Rendern von Empfehlungseinheiten auf einer Seite zurück.
