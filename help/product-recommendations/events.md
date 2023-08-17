---
title: Daten erfassen
description: Erfahren Sie, wie Ereignisse Daten für Produktempfehlungen erfassen.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Daten erfassen

Wenn Sie SaaS-basierte Adobe Commerce-Funktionen wie [Produkt-Recommendations](install-configure.md) oder [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), stellen die Module die Verhaltens-Datenerfassung in Ihrem Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Ihren Kunden und ermöglicht Produktempfehlungen. Beispiel: die `view` -Ereignis zur Berechnung der `Viewed this, viewed that` Empfehlungstyp und die `place-order` -Ereignis zur Berechnung der `Bought this, bought that` Empfehlungstyp.

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von Produktempfehlungen umfasst keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html).

Die folgenden Ereignisse sind nicht spezifisch für Product Recommendations, müssen jedoch Ergebnisse zurückgeben:

- `view`
- `add-to-cart`
- `place-order`

Die [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) listet alle Ereignisse auf, die in Ihrer Storefront bereitgestellt wurden. In dieser Liste finden Sie jedoch eine Untergruppe von Ereignissen, die spezifisch für Product Recommendations sind. Diese Ereignisse erfassen Daten, wenn Kunden mit Empfehlungseinheiten im Storefront interagieren, und nutzen die Metriken, die Ihnen bei der Analyse der Performance Ihrer Empfehlungen helfen.

| Ereignis | Beschreibung | [Wird für Metriken verwendet?](workspace.md) |
| --- | --- | --- |
| `impression-render` | Die Empfehlungseinheit wird auf der Seite dargestellt. | Ja |
| `rec-add-to-cart-click` | Der Kunde klickt auf **Zum Warenkorb hinzufügen** -Schaltfläche für einen Artikel in der Empfehlungseinheit. | Ja, wenn ein **Zum Warenkorb hinzufügen** in der Recommendations-Vorlage vorhanden ist. |
| `rec-click` | Der Kunde klickt auf ein Produkt in der Empfehlungseinheit. | Ja |
| `view` | Die Empfehlungseinheit wird auf der Seite sichtbar, z. B. durch Scrollen in die Ansicht. | Ja |

Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie den Abschnitt [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie im Benutzerhandbuch , wie Sie Product Recommendations in eine [Headless](headless.md) Umgebung.

## Einschränkungen

Anzeigensperren und Datenschutzeinstellungen können die `magento/product-recommendations` -Modul aus der Erfassung von Ereignissen verwenden und möglicherweise zu Interaktion und Umsatz führen [Metriken](workspace.md) zu unterschätzen.

Eventing erfasst nicht alle Transaktionen, die auf der Website des Händlers stattfinden. Eventing soll dem Händler eine allgemeine Vorstellung von Ereignissen auf der Site vermitteln.

Headless-Implementierungen müssen Eventing implementieren, um das Produkt-Recommendations-Dashboard zu aktivieren.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
