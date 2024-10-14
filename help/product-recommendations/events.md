---
title: Daten erfassen
description: Erfahren Sie, wie Ereignisse Daten für Produktempfehlungen erfassen.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 87db52e0c851b56c9a8ceba1bf25c222c6d63cda
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---

# Daten erfassen

Wenn Sie SaaS-basierte Adobe Commerce-Funktionen wie [Produkt Recommendations](install-configure.md) oder [Live Search](../live-search/install.md) installieren und konfigurieren, stellen die Module die verhaltensbasierte Datenerfassung auf Ihrem Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Ihren Kunden und ermöglicht Produktempfehlungen sowie die [Live-Suche](../live-search/overview.md) -Ergebnisse. Beispielsweise wird der Empfehlungstyp `Viewed this, viewed that` mit dem Ereignis `view` und der Empfehlungstyp `place-order` berechnet, mit dem der Empfehlungstyp `Bought this, bought that` berechnet wird.

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von Produktempfehlungen umfasst keine personenbezogenen Daten (PII). Alle Benutzer-IDs wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Lernen Sie [mehr](https://www.adobe.com/privacy/experience-cloud.html).

## Datentypen und Ereignisse

In Product Recommendations werden zwei Datentypen verwendet:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, zu einem Warenkorb hinzugefügte Artikel und Käufe.
- **Katalog** - Produktmetadaten wie Name, Preis, Verfügbarkeit usw.

Wenn Sie das `magento/product-recommendations` -Modul installieren, aggregiert Adobe Sensei die Verhaltens- und Katalogdaten und erstellt so für jeden Empfehlungstyp Produkt-Recommendations. Der Product Recommendations-Dienst stellt diese Empfehlungen dann in Form eines Widgets, das das empfohlene Produkt _items_ enthält, auf Ihrer Storefront bereit.

Einige Empfehlungstypen verwenden Verhaltensdaten Ihrer Kunden, um Modelle für maschinelles Lernen zu trainieren und so personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie Produkt Recommendations schnell auf Ihrer Site verwenden möchten, können Sie die folgenden, rein katalogbezogenen Empfehlungstypen verwenden:

- `More like this`
- `Visual similarity`

### Kaltstart

Wann können Sie mit der Verwendung von Empfehlungstypen beginnen, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als das Problem _Cold Start_ bezeichnet.

Das Problem _Cold Start_ bezieht sich auf die Zeit, die es dauert, bis ein Modell trainiert und wirksam wird. Bei Produktempfehlungen bedeutet dies, darauf zu warten, dass Adobe Sensei genügend Daten erfasst, um seine maschinellen Lernmodelle zu trainieren, bevor Empfehlungseinheiten auf Ihrer Site bereitgestellt werden. Je mehr Daten die Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Da die Datenerfassung auf einer Live-Site erfolgt, ist es am besten, diesen Prozess frühzeitig zu starten, indem das `magento/production-recommendations` -Modul installiert und eingerichtet wird.

Die folgende Tabelle enthält einige allgemeine Anleitungen für die Zeit, die benötigt wird, um genügend Daten für jeden Empfehlungstyp zu sammeln:

| Empfehlungstyp | Schulungszeit | Hinweise |
|---|---|---|
| Popularitätsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Varianten | Hängt vom Ereignisvolumen ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu, werden Käufe |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Die Produktansichten sind relativ umfangreich |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meisten Schulungen | Kaufereignisse sind die seltensten Ereignisse auf einer Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Beliebtheitsgrundlinie zu erstellen | Die Trends sind ein Messwert für die aktuelle Beliebtheit eines Produkts im Vergleich zu seiner Beliebtheitsgrundlinie. Der Trendwert eines Produkts wird mithilfe eines Vordergrundsatzes (aktuelle Beliebtheit über 24 Stunden) und eines Hintergrundsatzes (Beliebtheitsgrundlinie über 72 Stunden) berechnet. Wenn die Beliebtheit eines Elements innerhalb eines Zeitraums von 24 Stunden im Vergleich zur Grundbeliebtheit signifikant zunimmt, erhält es einen hohen Trendwert. Jedes Produkt hat diese Punktzahl, und die Artikel mit der höchsten Punktzahl bilden jederzeit die Gruppe der Top-Trendprodukte. |

Andere Variablen, die sich auf die zum Trainieren benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- Adobe Commerce berechnet Verhaltensdaten alle vier Stunden neu. Je länger sie auf Ihrer Site verwendet werden, desto genauer wird Recommendations.

Um Ihnen bei der Visualisierung des Trainings-Fortschritts der einzelnen Empfehlungstypen zu helfen, zeigt die Seite [Empfehlung erstellen](create.md#readiness-indicators) Bereitschaftsindikatoren an.

Während Daten auf Ihrer Live-Site erfasst werden und die Modelle für maschinelles Lernen trainiert werden, können Sie andere Test- und Konfigurationsaufgaben abschließen, die zum Einrichten von Empfehlungen erforderlich sind. Wenn Sie mit dieser Arbeit fertig sind, verfügen die Modelle über genügend Daten, um nützliche Empfehlungen zu erstellen, sodass Sie sie in Ihrer Storefront bereitstellen können.

Wenn Ihre Site für die meisten Produkt-SKUs nicht genügend Traffic (Ansichten, Käufe, Trends) erhält, sind möglicherweise nicht genügend Daten vorhanden, um den Lernprozess abzuschließen. Dies kann dazu führen, dass der Bereitschaftsindikator im Admin feststeckt. Die Bereitschaftsindikatoren sollen Händlern einen weiteren Datenpunkt bei der Auswahl des Empfehlungstyps bieten, der für ihren Store besser ist. Die Zahlen sind ein Leitfaden und werden möglicherweise nie 100 % erreichen. [Erfahren Sie mehr](create.md#readiness-indicators) über Bereitschaftsindikatoren.

### Reserveempfehlungen {#backuprecs}

Wenn die Eingabedaten nicht ausreichen, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet Adobe Commerce Ersatzempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise den Empfehlungstyp &quot;`Recommended for you`&quot;auf Ihrer Homepage bereitstellen, hat ein Erstkäufer Ihrer Site nicht genügend Verhaltensdaten generiert, um genau empfohlene personalisierte Produkte zu erzielen. In diesem Fall überdeckt Adobe Commerce Artikel basierend auf dem Empfehlungstyp `Most viewed` für diesen Käufer.

Bei unzureichender Eingabe-Datenerfassung greifen die folgenden Empfehlungstypen auf den Empfehlungstyp `Most viewed` zurück:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### Veranstaltungen

Der [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) listet alle Ereignisse auf, die in Ihrer Storefront bereitgestellt wurden. In dieser Liste finden Sie jedoch eine Untergruppe von Ereignissen, die spezifisch für Product Recommendations sind. Diese Ereignisse erfassen Daten, wenn Kunden mit Empfehlungseinheiten im Storefront interagieren, und nutzen die Metriken, die Ihnen bei der Analyse der Performance Ihrer Empfehlungen helfen.

| Ereignis | Beschreibung |
| --- | --- | --- |
| `impression-render` | Wird gesendet, wenn die Empfehlungseinheit auf der Seite gerendert wird. Wenn eine Seite zwei Empfehlungseinheiten enthält (gekauft, Ansicht), werden zwei `impression-render` -Ereignisse gesendet. Dieses Ereignis wird verwendet, um die Metrik für Impressionen zu verfolgen. |
| `rec-add-to-cart-click` | Der Käufer klickt für einen Artikel in der Empfehlungseinheit auf die Schaltfläche **Zum Warenkorb hinzufügen** . |
| `rec-click` | Der Käufer klickt auf ein Produkt in der Empfehlungseinheit. |
| `view` | Wird gesendet, wenn die Empfehlungseinheit mindestens 50 Prozent sichtbar wird, z. B. durch Scrollen der Seite nach unten. Wenn beispielsweise eine Empfehlungseinheit zwei Zeilen hat, wird ein `view` -Ereignis gesendet, wenn eine Zeile plus ein Pixel der zweiten Zeile für den Käufer sichtbar wird. Wenn der Käufer die Seite mehrmals nach oben und unten scrollt, wird das `view` -Ereignis so oft gesendet, wie der Käufer die gesamte Empfehlungseinheit erneut auf der Seite sieht. |

>[!NOTE]
>
>Die Metriken zur Produktempfehlung sind für Luma-Storefronts optimiert. Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie die [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie, wie Sie [Product Recommendations in eine Headless](headless.md)-Umgebung integrieren.

#### Erforderliche Dashboard-Ereignisse

Die folgenden Ereignisse sind erforderlich, um das [[!DNL Product Recommendations] Dashboard](workspace.md) zu füllen

| Dashboard-Spalte | Veranstaltungen | Feld &quot;Join&quot; |
| ---------------- | --------- | ----------- |
| Impressionen | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId` |
| Ansichten | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId` |
| Klicks | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | `unitId` |
| Umsatz | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| LT Umsatz | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

Die folgenden Ereignisse beziehen sich nicht auf Product Recommendations, sind jedoch erforderlich, damit Adobe Sensei die Kundendaten korrekt interpretieren kann:

- `view`
- `add-to-cart`
- `place-order`

#### Empfehlungstyp

In dieser Tabelle werden die von den einzelnen Empfehlungstypen verwendeten Ereignisse beschrieben.

| Empfehlungstyp | Veranstaltungen | Seite |
| --- | --- | --- | ---|
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`complete-checkout` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Seite mit Produktliste<br>Warenkorb<br>Wunschliste |
| Anzeige, Anzeige, | `page-view`<br>`product-view` | Produktdetailseite |
| Anzeige: , gekauft als | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite<br>Warenkorb/Checkout |
| kaufte das, kaufte es | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Trends | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zu erwerbende Ansicht | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zu erwerbende Ansicht | Produkt-Recs | `page-view`<br>`complete-checkout` | Warenkorb/Checkout |
| Konversion: In den Warenkorb | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: In den Warenkorb | Produkt-Recs | `page-view`<br>`add-to-cart` | Seite mit Produktdetails<br>Seite mit Produktliste<br>Warenkorb<br>Wunschliste |

#### Einschränkungen

- Anzeigensperren und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und die Umsatzmetriken [Metriken](workspace.md#column-descriptions) nicht ausreichend gemeldet werden. Außerdem werden einige Ereignisse möglicherweise nicht gesendet, weil Käufer die Seite verlassen oder Netzwerkprobleme haben.
- [Headless-Implementierungen](headless.md) müssen Eventing implementieren, um das Produkt-Recommendations-Dashboard zu erweitern.
- Für konfigurierbare Produkte verwendet Product Recommendations das Bild des übergeordneten Produkts in der Empfehlungseinheit. Wenn für das konfigurierbare Produkt kein Bild angegeben ist, ist die Empfehlungseinheit für dieses bestimmte Produkt leer.

>[!NOTE]
>
>Wenn der [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce erst Verhaltensdaten, wenn der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
