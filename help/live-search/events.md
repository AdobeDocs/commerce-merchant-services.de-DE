---
title: '[!DNL Live Search] Ereignisse'
description: Erfahren Sie, wie Ereignisse Daten für [!DNL Live Search] erfassen.
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: e1bf54b9fde42746a8c2f75253cbb3730821fb8c
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# [!DNL Live Search] Ereignisse

[!DNL Live Search] verwendet Ereignisse, um Suchalgorithmen wie &quot;Am häufigsten angezeigt&quot;und &quot;Dies angezeigt, Anzeige auch&quot; zu unterstützen. Während das Beispiel-Luma-Design ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/design/themes/themes#the-default-theme) für [Commerce vorkonfiguriert ist, müssen Headless- und andere benutzerdefinierte Implementierungen Eventing für ihre eigenen Anforderungen implementieren.

In dieser Tabelle werden die Ereignisse beschrieben, die von [!DNL Live Search] [Rangstrategien](rules-add.md#intelligent-ranking) verwendet werden.

| Ranking Strategy | Veranstaltungen | Seite |
| --- | --- | --- |
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`complete-checkout` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Seite mit Produktliste<br>Warenkorb<br>Wunschliste |
| Anzeige, Anzeige, | `page-view`<br>`product-view` | Produktdetailseite |

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von [!DNL Live Search] umfasst keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. [Weitere Infos](https://www.adobe.com/privacy/experience-cloud.html).

## Erforderliche Dashboard-Ereignisse

Zum Ausfüllen des Dashboards [Live-Suche](performance.md) sind einige Ereignisse erforderlich

| Dashboard-Bereich | Veranstaltungen | Feld &quot;Join&quot; |
| ------------------- | ------------- | ---------- |
| Einzelsuche | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Suchvorgänge mit null Ergebnissen | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Null-Ergebnisrate | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Häufige Suchvorgänge | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Durchschn. Klickposition | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId` |
| Clickthrough-Rate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId`, `sku`, `parentSku` |
| Konversionsrate | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | `searchRequestId`, `sku`, `parentSku` |

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

- Anzeigensperren und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und die Umsatzmetriken [Metriken](performance.md) nicht ausreichend gemeldet werden. Außerdem werden einige Ereignisse möglicherweise nicht gesendet, weil Käufer die Seite verlassen oder Netzwerkprobleme haben.
- Headless-Implementierungen müssen Eventing implementieren, um intelligentes Merchandising zu ermöglichen.

>[!NOTE]
>
>Wenn der [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce erst Verhaltensdaten, wenn der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
