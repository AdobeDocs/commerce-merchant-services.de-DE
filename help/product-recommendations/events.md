---
title: Daten erfassen
description: Erfahren Sie, wie Ereignisse Daten für Produktempfehlungen erfassen.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 7ed9321a2f4e58a7476aa91e74611fe896e1a7b1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Daten erfassen

Wenn Sie SaaS-basierte Adobe Commerce-Funktionen wie [Produkt Recommendations](install-configure.md) oder [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) installieren und konfigurieren, stellen die Module die verhaltensbasierte Datenerfassung auf Ihrem Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Ihren Kunden und ermöglicht Produktempfehlungen. Beispielsweise wird der Empfehlungstyp `Viewed this, viewed that` mit dem Ereignis `view` und der Empfehlungstyp `place-order` berechnet, mit dem der Empfehlungstyp `Bought this, bought that` berechnet wird.

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von Produktempfehlungen umfasst keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Lernen Sie [mehr](https://www.adobe.com/privacy/experience-cloud.html).

Die folgenden Ereignisse sind nicht spezifisch für Product Recommendations, müssen jedoch Ergebnisse zurückgeben:

- `view`
- `add-to-cart`
- `place-order`

Der [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) listet alle Ereignisse auf, die in Ihrer Storefront bereitgestellt wurden. In dieser Liste finden Sie jedoch eine Untergruppe von Ereignissen, die spezifisch für Product Recommendations sind. Diese Ereignisse erfassen Daten, wenn Kunden mit Empfehlungseinheiten im Storefront interagieren, und nutzen die Metriken, die Ihnen bei der Analyse der Performance Ihrer Empfehlungen helfen.

| Ereignis | Beschreibung | Wird für Metriken verwendet? |
| --- | --- | --- |
| `impression-render` | Die Empfehlungseinheit wird auf der Seite dargestellt. | Ja |
| `rec-add-to-cart-click` | Der Kunde klickt für einen Artikel in der Empfehlungseinheit auf die Schaltfläche **Zum Warenkorb hinzufügen** . | Ja, wenn in der Empfehlungsvorlage eine Schaltfläche **Zum Warenkorb hinzufügen** vorhanden ist. |
| `rec-click` | Der Kunde klickt auf ein Produkt in der Empfehlungseinheit. | Ja |
| `view` | Die Empfehlungseinheit wird auf der Seite sichtbar, z. B. durch Scrollen in die Ansicht. | Ja |

Die folgenden Ereignisse sind erforderlich, um das Dashboard ordnungsgemäß zu füllen.
| Dashboard-Spalte | Veranstaltungen    | Feld &quot;Join&quot;  |
| — | — | — |
| Impressionen      |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId  |
| Ansichten            |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId  |
| Klicks           |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | unitId  |
| Umsatz          |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| LT Umsatz       |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| CTR              |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | unitId, sku |
| vCTR             |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie die [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie im Benutzerhandbuch, wie Sie die [Produkt-Recommendations in eine Headless](headless.md)-Umgebung integrieren.

## Einschränkungen

Anzeigensperren und Datenschutzeinstellungen können verhindern, dass das Modul `magento/product-recommendations` Ereignisse erfasst, und können dazu führen, dass die Interaktionen und Umsätze [metriken](workspace.md) unterbewertet werden.

Eventing erfasst nicht alle Transaktionen, die auf der Website des Händlers stattfinden. Eventing soll dem Händler eine allgemeine Vorstellung von Ereignissen auf der Site vermitteln.

Headless-Implementierungen müssen Eventing implementieren, um das Produkt-Recommendations-Dashboard zu aktivieren.

>[!NOTE]
>
>Wenn der [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce erst Verhaltensdaten, wenn der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
