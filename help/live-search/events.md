---
title: '[!DNL Live Search] events'
description: Erfahren Sie, wie Ereignisse Daten für [!DNL Live Search] erfassen.
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] Ereignisse

[!DNL Live Search] verwendet Ereignisse, um Suchalgorithmen wie &quot;Am häufigsten angezeigt&quot;und &quot;Dies angezeigt, Anzeige auch&quot; zu unterstützen. Während LUMA-Benutzer Ereignisse vorkonfiguriert finden, müssen Headless- und andere benutzerdefinierte Implementierungen Eventing für ihre eigenen Anforderungen implementieren.

Da [!DNL Live Search] und [!DNL Product Recommendations] denselben Backend-Algorithmus verwenden, werden einige Ereignisse von beiden Diensten gemeinsam genutzt. Zum Ausfüllen des Recommendations-Dashboards sind einige Recommendations-Ereignisse erforderlich.

In dieser Tabelle werden die von [!DNL Live Search] -Strategien verwendeten Ereignisse beschrieben.

| Strategie | Produkte | Veranstaltungen | Seite |
| --- | --- | --- | ---|
| Am häufigsten angezeigt | Live Search<br>Produktrecs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Am häufigsten gekauft | Live Search<br>Produktrecs | Seitenansicht<br> Checkout | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | Live Search<br>Produktrecs | Seitenansicht<br>zum Warenkorb hinzufügen | Produktdetailseite<br>Seite mit Produktliste<br>Warenkorb<br>Wunschliste |
| Anzeige, Anzeige, | Live Search<br>Produktrecs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Trends | Live Search<br>Produktrecs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Anzeige: , gekauft als | Produkt-Recs | Seitenansicht<br>Produktansicht | Produktdetailseite<br>Warenkorb/Checkout |
| kaufte das, kaufte es | Produkt-Recs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Konversion: Zu erwerbende Ansicht | Produkt-Recs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Konversion: Zu erwerbende Ansicht | Produkt-Recs | Seitenansicht<br> Checkout | Warenkorb/Checkout |
| Konversion: In den Warenkorb | Produkt-Recs | Seitenansicht<br>Produktansicht | Produktdetailseite |
| Konversion: In den Warenkorb | Produkt-Recs | Seitenansicht<br>zum Warenkorb hinzufügen | Seite mit Produktdetails<br>Seite mit Produktliste<br>Warenkorb<br>Wunschliste |

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von [!DNL Live Search] umfasst keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html).

## Erforderliche Dashboard-Ereignisse

Zum Ausfüllen des Dashboards [Live-Suche](performance.md) sind einige Ereignisse erforderlich

| Dashboard-Bereich | Veranstaltungen | Feld &quot;Join&quot; |
| ------------------- | ------------- | ---------- |
| Einzelsuche | `page-view`, `search-request-sent` | searchRequestId |
| Suchvorgänge mit null Ergebnissen | `page-view`, `search-request-sent` | searchRequestId |
| Null-Ergebnisrate | `page-view`, `search-request-sent` | searchRequestId |
| Häufige Suchvorgänge | `page-view`, `search-request-sent` | searchRequestId |
| Durchschn. Klickposition | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| Clickthrough-Rate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| Konversionsrate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### Erforderliche Kontexte

Für alle Ereignisse sind die Kontexte `Page` und `Storefront` erforderlich. Dies sollte auf Seitenebene/storefront-Anwendungsebene statt beim Generieren einzelner Ereignisse geschehen (z. B. in einer PHP-Storefront ist der PHP-Anwendungscontainer dafür verantwortlich, diese zur Laufzeit festzulegen).

## Nutzung

Hier finden Sie eine Beispielimplementierung des `search-request-sent` -Ereignisses:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Einschränkungen

Anzeigensperren und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und die Umsatzmetriken [Metriken](workspace.md) nicht ausreichend gemeldet werden.

Eventing erfasst nicht alle Transaktionen, die auf der Website des Händlers stattfinden. Eventing soll dem Händler eine allgemeine Vorstellung von Ereignissen auf der Site vermitteln.

Headless-Implementierungen müssen Eventing implementieren, um das [Produkt-Recommendations-Dashboard](../product-recommendations/events.md) zu aktivieren.

>[!NOTE]
>
>Wenn der [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce erst Verhaltensdaten, wenn der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
