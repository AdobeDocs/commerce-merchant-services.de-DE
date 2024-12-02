---
title: Indizierung
description: Erfahren Sie, wie [!DNL Live Search] die Eigenschaften von Produktattributen indiziert.
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 2833b723845312fe657b29024b9d715ee07d5a1e
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Indizierung

Der Indizierungsprozess von [!DNL Live Search] liest durch den Katalog nach Produktattributen und erstellt einen Index, damit Produkte schnell durchsucht, gefiltert und präsentiert werden können.

Die Produktattributeigenschaften (Metadaten) bestimmen:

* Verwendung eines Attributs im Katalog
* Aussehen und Verhalten des Stores
* Die Daten, die in Datenübertragungsvorgängen enthalten sind

Der Umfang der Attributmetadaten ist `website/store/store view`.

Mit der API [!DNL Live Search] kann ein Client nach jedem Produktattribut sortieren, für das die Eigenschaft [storeFront](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) `Use in Search` im Adobe Commerce Admin auf `Yes` festgelegt ist. Wenn diese Option aktiviert ist, kann `Search Weight` für das Attribut festgelegt werden.

[!DNL Live Search] indiziert keine gelöschten Produkte oder Produkte, die auf `Not Visible Individually` festgelegt sind.

>[!NOTE]
>
> Commerce-Kunden mit [!DNL Live Search] können von schnelleren Preisänderungen und Synchronisierungszeiten auf ihren Websites mit dem [SaaS-Preisindex](../price-index/price-indexing.md) profitieren.

## Indizierungs-Pipeline

Der Client ruft den Suchdienst aus der Storefront auf, um (filterbare, sortierbare) Indexmetadaten abzurufen. Nur durchsuchbare Produktattribute, bei denen die Eigenschaft *Use in Layered Navigation* auf `Filterable (with results)` und die Eigenschaft *Use for Sorting in Product Listing* auf `Yes` festgelegt ist, können vom Suchdienst aufgerufen werden.

Um eine dynamische Abfrage zu erstellen, muss der Suchdienst wissen, welche Attribute durchsuchbar sind und welche [Gewichtung](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-results) sie haben. [!DNL Live Search] berücksichtigt die Adobe Commerce-Suchgewichtung (1-10, wobei 10 die höchste Priorität hat). Die Liste der Daten, die mit dem Katalogdienst synchronisiert und freigegeben werden, finden Sie im Schema, das definiert ist in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] Indizierung des Client-Suchdiagramms](assets/indexing-pipeline.svg)

1. Überprüfen Sie den Händler auf die Berechtigung [!DNL Live Search] .
1. Abrufen von Store-Ansichten mit Änderungen an Attributmetadaten.
1. Store-Indizierungsattribute
1. Indizieren Sie den Suchindex neu.

### Vollständiger Index

Wenn [!DNL Live Search] beim Onboarding konfiguriert und synchronisiert wird, kann es bis zu 60 Minuten dauern, bis der anfängliche Index erstellt wird. Die Indizierung großer Kataloge kann länger dauern. Der Prozess beginnt, nachdem `cron` den Feed gesendet hat, und endet mit der Ausführung.

Mit den folgenden Ereignissen wird ein vollständiger Synchronisations- und Indexaufbau Trigger:

* Onboarding der [Katalogdatensynchronisierung](install.md#synchronize-catalog-data)
* Änderungen an Attributmetadaten

Wenn Sie beispielsweise die Eigenschaft `Use in Search` des Attributs `color` von `No` in `Yes` ändern, werden die Attributmetadaten in `searchable=true` geändert, und es wird eine vollständige Synchronisierung und Neuindizierung Trigger. Der folgende Attribut-Metadaten-Trigger enthält eine vollständige Synchronisierung und Neuindizierung, wenn er geändert wurde:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Streaming-Produktaktualisierungen

Nachdem der anfängliche Index während des [Onboarding](install.md#synchronize-catalog-data) erstellt wurde, werden die folgenden inkrementellen Produktaktualisierungen kontinuierlich synchronisiert und neu indiziert:

* Neue Produkte zum Katalog hinzugefügt
* Änderungen an Produktattributwerten

Beispielsweise wird das Hinzufügen eines neuen Musterwerts zum Attribut `color` als Streaming-Produktaktualisierung behandelt.

Workflow für Streaming-Update:

1. Aktualisierte Produkte werden von der Adobe Commerce-Instanz mit dem Katalogdienst synchronisiert.
1. Der Indizierungsdienst sucht kontinuierlich nach Produktaktualisierungen aus dem Katalogdienst. Aktualisierte Produkte werden indiziert, sobald sie im Katalogdienst ankommen.
1. Es kann bis zu 15 Minuten dauern, bis eine Produktaktualisierung in [!DNL Live Search] verfügbar ist.

#### Aktualisierungen, die sich auf die Produktsichtbarkeit auswirken

Wenn Sie Aktualisierungen an den [!DNL Live Search] Admin-Konfigurationseinstellungen, den Adobe Commerce Admin-Konfigurationseinstellungen oder Aktualisierungen an Katalogdaten vornehmen, kann eine Verzögerung erwartet werden, bevor diese Änderungen im Storefront angezeigt werden.

In der folgenden Tabelle werden verschiedene Änderungen und die ungefähre Wartezeit beschrieben, bevor sie auf der Storefront angezeigt werden.

| Updates | Auf Storefront sichtbare Verzögerung |
|---|---|
| [!DNL Live Search] Admin ändert sich in Facetten, Preiseinstellungen, Suchregeln oder KategorieMerchandising-Regeln. | 15-20 Minuten. |
| [!DNL Live Search] Administratoränderungen, die eine Neuindizierung erfordern: Spracheinstellungen oder Synonyme. | Bis zu 15 Minuten nach Abschluss der Neuindizierung. |
| Adobe Commerce Admin-Änderungen, die eine vollständige Neuindizierung erfordern: durchsuchbare, sortierbare oder filterbare Attributmetadaten | Bis zu 15 Minuten nach Abschluss der Neuindizierung. |
| Inkrementelle Änderungen an Katalogdaten, die nicht neu indiziert werden müssen: Produktbestand, Preis, Name usw. | Bis zu 15 Minuten nach der Aktualisierung des Index der Elastic Search mit den neuesten Daten. |

## Client-Suche

Die [!DNL Live Search] -API ermöglicht es einem Client, nach jedem beliebigen sortierbaren Produktattribut zu sortieren, indem die [storefront-Eigenschaft](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes), *für die Sortierung in Produktlisten verwendet* auf `Yes` gesetzt wird. Abhängig vom Design bewirkt diese Einstellung, dass das Attribut als Option in das Paginierungssteuerelement [Sortieren nach ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation) auf Katalogseiten aufgenommen wird. Bis zu 200 Produktattribute können mit [!DNL Live Search] indiziert werden, wobei [Storefront-Eigenschaften](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) durchsuchbar und filterbar sind.

Die Indexmetadaten werden in der Indizierungs-Pipeline gespeichert und sind für den Suchdienst verfügbar.

![[!DNL Live Search] Index-Metadaten-API-Diagramm](assets/index-metadata-api.svg)

### Workflow für sortierbare Attribute

1. Der Client ruft den Suchdienst auf.
1. Der Suchdienst ruft den Suchadministratordienst auf.
1. Der Suchdienst ruft die Indizierungs-Pipeline auf.

## Indexiert für alle Produkte

Die Reihenfolge der Felder in dieser Liste spiegelt die typische Reihenfolge der Spalten in den exportierten Produktdaten wider.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

Das folgende Feld wird für alle konfigurierbaren Produkte indexiert:

* `childrenSkus`
