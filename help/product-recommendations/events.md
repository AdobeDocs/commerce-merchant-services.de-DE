---
title: Erfassen von Daten
description: Erfahren Sie, wie Ereignisse Daten für Produktempfehlungen erfassen.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: cd1ce643d7c1ffeec8e9853cfc6ffc5519ce8f7a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---

# Erfassen von Daten

Wenn Sie SaaS-basierte Adobe Commerce-Funktionen wie [Produkt-Recommendations](install-configure.md) oder [Live-Suche](../live-search/install.md) installieren und konfigurieren, stellen die Module die Erfassung von Verhaltensdaten für Ihre Storefront bereit. Dieser Mechanismus erfasst anonymisierte Verhaltensdaten von Käufern und ermöglicht Produktempfehlungen und [Live Search](../live-search/overview.md)Ergebnisse. Beispielsweise wird das `view` Ereignis verwendet, um den `Viewed this, viewed that` Empfehlungstyp zu berechnen, und das `place-order` Ereignis wird verwendet, um den `Bought this, bought that` Empfehlungstyp zu berechnen.

>[!NOTE]
>
>Die Datenerfassung für die Zwecke von Produktempfehlungen umfasst keine personenbezogenen Daten (PII). Alle Benutzerkennungen wie Cookie-IDs und IP-Adressen werden streng anonymisiert. Weitere [ (](https://www.adobe.com/privacy/experience-cloud.html).

## Datentypen und Ereignisse

Es gibt zwei Arten von Daten, die in der Produkt-Recommendations verwendet werden:

- **Verhalten** - Daten aus der Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, Artikel, die zum Warenkorb hinzugefügt werden, und Käufe.
- **Katalog** - Produktmetadaten, z. B. Name, Preis, Verfügbarkeit usw.

Bei der Installation des `magento/product-recommendations` aggregiert Adobe Sensei die Verhaltens- und Katalogdaten und erstellt für jeden Empfehlungstyp Produkt-Recommendations. Der Produkt-Recommendations-Service stellt diese Empfehlungen dann in Form eines Widgets, das das empfohlene Produkt (_) enthält, in Ihrer Storefront_.

Einige Empfehlungstypen verwenden Verhaltensdaten von Kundinnen und Kunden, um Modelle für maschinelles Lernen zu trainieren, um personalisierte Empfehlungen zu erstellen. Andere Empfehlungstypen verwenden nur Katalogdaten und verwenden keine Verhaltensdaten. Wenn Sie Produkt-Recommendations schnell auf Ihrer Site verwenden möchten, können Sie die folgenden, nur für den Katalog geeigneten Empfehlungstypen verwenden:

- `More like this`
- `Visual similarity`

### Kaltstart

Ab wann können Empfehlungstypen verwendet werden, die Verhaltensdaten verwenden? Es kommt darauf an. Dies wird als &quot;_&quot;-_ bezeichnet.

Das _Kaltstart_-Problem bezieht sich auf die Zeit, die ein Modell benötigt, um trainiert und effektiv zu werden. Für Produktempfehlungen bedeutet dies, dass Sie warten müssen, bis Adobe Sensei genügend Daten gesammelt hat, um seine Modelle für maschinelles Lernen zu trainieren, bevor Sie Empfehlungseinheiten auf Ihrer Site bereitstellen. Je mehr Daten die Modelle haben, desto genauer und nützlicher sind die Empfehlungen. Da die Datenerfassung auf einer Live-Site erfolgt, ist es am besten, diesen Prozess frühzeitig durch die Installation und Einrichtung des `magento/production-recommendations`-Moduls zu starten.

Die folgende Tabelle enthält einige allgemeine Hinweise dazu, wie lange es dauert, bis für jeden Empfehlungstyp genügend Daten erfasst sind:

| Empfehlungstyp | Trainingszeit | Notizen |
|---|---|---|
| Beliebtheitsbasiert (`Most viewed`, `Most purchased`, `Most added to cart`) | Variiert | Hängt von der Menge der Ereignisse ab - Ansichten sind am häufigsten und lernen daher schneller; fügt dann zum Warenkorb hinzu und kauft |
| `Viewed this, viewed that` | Erfordert mehr Schulung | Das Volumen der Produktansichten ist annehmbar hoch |
| `Viewed this, bought that`, `Bought this, bought that` | Erfordert die meiste Schulung | Kaufereignisse sind die seltensten Ereignisse auf einer Commerce-Site, insbesondere im Vergleich zu Produktansichten |
| `Trending` | Erfordert drei Tage Daten, um eine Popularitätsbasislinie zu erstellen | Der Trend ist ein Maß für die jüngste Dynamik in der Popularität eines Produkts verglichen mit seiner eigenen Popularitätsbasislinie. Der Trend-Score eines Produkts wird anhand eines Vordergrundsatzes (aktuelle Popularität über 24 Stunden) und eines Hintergrundsatzes (Popularitätsbasislinie über 72 Stunden) berechnet. Wenn die Popularität eines Elements innerhalb eines Zeitraums von 24 Stunden im Vergleich zu seiner Grundbeliebtheit signifikant zunimmt, erhält es einen hohen Trend-Score. Jedes Produkt hat diese Bewertung, und die Artikel mit der höchsten Bewertung zu jeder Zeit umfassen die Gruppe der Top-Trend-Produkte. |

Andere Variablen, die sich auf die für das Training benötigte Zeit auswirken können:

- Höheres Traffic-Volumen trägt zu schnellerem Lernen bei
- Einige Empfehlungstypen trainieren schneller als andere
- Adobe Commerce berechnet die Verhaltensdaten alle vier Stunden neu. Recommendations wird umso genauer, je länger sie auf Ihrer Site verwendet werden.

Auf der Seite „Empfehlung erstellen[ werden Bereitschaftsindikatoren angezeigt, damit Sie den Trainings-Fortschritt ](create.md#readiness-indicators) jeden Empfehlungstyp visualisieren können.

Während Daten auf Ihrer Live-Site erfasst werden und die Modelle für maschinelles Lernen trainiert werden, können Sie andere Test- und Konfigurationsaufgaben abschließen, die zum Einrichten von Empfehlungen erforderlich sind. Wenn Sie mit dieser Arbeit fertig sind, verfügen die Modelle über genügend Daten, um nützliche Empfehlungen zu erstellen, sodass Sie sie in Ihrer Storefront bereitstellen können.

Wenn auf Ihrer Site nicht genügend Traffic (Ansichten, Käufe, Trends) für die meisten Produkt-SKUs vorhanden ist, sind möglicherweise nicht genügend Daten vorhanden, um den Lernprozess abzuschließen. Dadurch kann der Bereitschaftsindikator im Admin-Bereich hängen bleiben. Die Bereitschaftsindikatoren sollen Händlern einen weiteren Datenpunkt bei der Auswahl des Recommendations-Typs bieten, der für ihren Store besser ist. Die Zahlen sind Richtwerte und erreichen möglicherweise nie 100 %. [Weitere ](create.md#readiness-indicators) zu Bereitschaftsindikatoren.

### Empfehlungen für Backups {#backuprecs}

Wenn die Eingabedaten nicht ausreichen, um alle angeforderten Empfehlungselemente in einer Einheit bereitzustellen, bietet Adobe Commerce Sicherungsempfehlungen zum Ausfüllen von Empfehlungseinheiten. Wenn Sie beispielsweise den `Recommended for you` Empfehlungstyp auf Ihrer Homepage bereitstellen, hat ein Erstkäufer auf Ihrer Site nicht genügend Verhaltensdaten generiert, um personalisierte Produkte korrekt zu empfehlen. In diesem Fall zeigt Adobe Commerce Elemente basierend auf dem `Most viewed` Empfehlungstyp an diesen Käufer an.

Bei unzureichender Erfassung von Eingabedaten greifen die folgenden Empfehlungstypen auf `Most viewed` Empfehlungstyp zurück:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### -Events

Der Ereignissammler für die [Adobe Commerce-Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) listet alle Ereignisse auf, die in Ihrer Storefront bereitgestellt wurden. Aus dieser Liste gibt es jedoch eine Teilmenge von Ereignissen, die für Produkt-Recommendations spezifisch sind. Diese Ereignisse erfassen Daten, wenn Käufer mit Empfehlungseinheiten in der Storefront interagieren, und liefern die Grundlage für die Metriken, mit denen Sie die Leistung Ihrer Empfehlungen analysieren können.

| Ereignis | Beschreibung |
| --- | --- |
| `impression-render` | Wird gesendet, wenn die Empfehlungseinheit auf der Seite dargestellt wird. Wenn eine Seite zwei Empfehlungseinheiten hat (gekauft, Ansicht), werden zwei `impression-render` gesendet. Dieses Ereignis wird verwendet, um die Metrik für Impressionen zu verfolgen. |
| `rec-add-to-cart-click` | Der Käufer klickt auf die Schaltfläche **Zum Warenkorb hinzufügen** für einen Artikel in der Empfehlungseinheit. |
| `rec-click` | Der Käufer klickt in der Empfehlungseinheit auf ein Produkt. |
| `view` | Wird gesendet, wenn die Empfehlungseinheit zu mindestens 50 % sichtbar wird, z. B. durch Scrollen auf der Seite nach unten. Wenn beispielsweise eine Empfehlungseinheit über zwei Zeilen verfügt, wird ein `view` gesendet, sobald eine Zeile plus ein Pixel der zweiten Zeile für den Erstkäufer sichtbar wird. Wenn der Erstkäufer die Seite mehrmals nach oben und unten scrollt, wird das `view` so oft gesendet, wie der Erstkäufer die gesamte Empfehlungseinheit erneut auf der Seite sieht. |

>[!NOTE]
>
>Metriken für Produktempfehlungen sind für Luma-Storefronts optimiert. Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie die Dokumentation zu [PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie, wie Sie [Product Recommendations in einer Headless-](headless.md) integrieren.

#### Erforderliche Dashboard-Ereignisse

Die folgenden Ereignisse sind erforderlich, um das (Dashboard[[!DNL Product Recommendations]  auszufüllen](workspace.md)

| Dashboard-Spalte | -Events | Feld verbinden |
| ---------------- | --------- | ----------- |
| Impressionen | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId` |
| Ansichten | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId` |
| Klicks | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | `unitId` |
| Einnahmen | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| LT-Umsatz | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

Die folgenden Ereignisse sind nicht spezifisch für Produkt-Recommendations, sind jedoch erforderlich, damit Adobe Sensei Kundendaten korrekt interpretiert:

- `view`
- `add-to-cart`
- `place-order`

#### Empfehlungstyp

In dieser Tabelle werden die von den einzelnen Empfehlungstypen verwendeten Ereignisse beschrieben.

| Empfehlungstyp | -Events | Seite |
| --- | --- | --- |
| Am häufigsten angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Am häufigsten gekauft | `page-view`<br>`complete-checkout` | Warenkorb/Checkout |
| Am häufigsten zum Warenkorb hinzugefügt | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite<br>Warenkorb<br>Wunschliste |
| hat dieses angezeigt, hat Folgendes angezeigt | `page-view`<br>`product-view` | Produktdetailseite |
| Das hier angesehen, das gekauft | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite/<br>/Checkout |
| Das kaufte ich, das kaufte ich | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Trend | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zum Kauf anzeigen | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: Zum Kauf anzeigen | Produkt-Recs | `page-view`<br>`complete-checkout` | Warenkorb/Checkout |
| Konversion: In Warenkorb anzeigen | Produkt-Recs | `page-view`<br>`product-view` | Produktdetailseite |
| Konversion: In Warenkorb anzeigen | Produkt-Recs | `page-view`<br>`add-to-cart` | Produktdetailseite<br>Produktlistenseite.<br>.<br> |

#### Einschränkungen

- Anzeigenblocker und Datenschutzeinstellungen können verhindern, dass Ereignisse erfasst werden, und können dazu führen, dass die Interaktion und der Umsatz [Metriken](workspace.md#column-descriptions) nicht erfasst werden. Darüber hinaus werden einige Ereignisse möglicherweise nicht gesendet, weil der Käufer die Seite oder das Netzwerk verlassen hat.
- [Headless-Implementierungen](headless.md) müssen das Eventing implementieren, um das Produkt-Recommendations-Dashboard zu unterstützen.
- Bei konfigurierbaren Produkten verwendet Product Recommendations das Image des übergeordneten Produkts in der Empfehlungseinheit. Wenn für das konfigurierbare Produkt kein Bild angegeben ist, ist die Empfehlungseinheit für dieses spezifische Produkt leer.

>[!NOTE]
>
>Wenn [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer der Verwendung von Cookies zustimmt. Wenn der Cookie-Einschränkungsmodus deaktiviert ist, erfasst Adobe Commerce standardmäßig Verhaltensdaten.
