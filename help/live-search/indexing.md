---
title: "[!DNL Live Search] Indizierung"
description: "Erfahren Sie wie [!DNL Live Search] indiziert Eigenschaften von Produktattributen."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Indizierung

Die Produktattributeigenschaften (Metadaten) bestimmen:

* Verwendung eines Attributs im Katalog
* Aussehen und Verhalten des Stores
* Die Daten, die in Datenübertragungsvorgängen enthalten sind

Der Umfang der Attributmetadaten lautet `website/store/store view`.

Die [!DNL Live Search] Mit der API kann ein Client nach jedem Produktattribut sortieren, das über die [storefront property](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` auf `Yes` in der Adobe Commerce-Admin. Wenn aktiviert, `Search Weight` und `Visible in Advanced Search` kann für das -Attribut festgelegt werden.

[!DNL Live Search] werden gelöschte Produkte oder die auf `Not Visible Individually`.

>[!NOTE]
>
> Commerce-Kunden mit [!DNL Live Search] kann von schnelleren Preisänderungen und Synchronisierungszeiten auf ihren Websites mit dem [SaaS-Preisindexer](../price-index/index.md).

## Indizierungs-Pipeline

Der Client ruft den Suchdienst aus der Storefront auf, um (filterbare, sortierbare) Indexmetadaten abzurufen. Nur durchsuchbare Produktattribute mit *Verwendung in mehrschichtiger Navigation* Eigenschaft auf `Filterable (with results)` und *Verwendung für die Sortierung in der Produktliste* auf `Yes` kann vom Suchdienst aufgerufen werden.
Um eine dynamische Abfrage zu erstellen, muss der Suchdienst wissen, welche Attribute durchsuchbar sind und wie groß sie sind. [!DNL Live Search] berücksichtigt die Adobe Commerce-Suchgewichtung (1-10, wobei 10 die höchste Priorität hat). Die Liste der Daten, die mit dem Katalogdienst synchronisiert und freigegeben werden, finden Sie im Schema, das definiert ist in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] Indizierungs-Client-Suchdiagramm](assets/indexing-pipeline.svg)

1. Prüfung des Händlers auf [!DNL Live Search] Berechtigung.
1. Abrufen von Store-Ansichten mit Änderungen an Attributmetadaten.
1. Store-Indizierungsattribute
1. Neuindizieren des Suchindex.

### Vollständiger Index

Wann [!DNL Live Search] beim Onboarding konfiguriert und synchronisiert wird, kann es bis zu acht Stunden dauern, bis der anfängliche Index erstellt wird. Der Prozess beginnt nach `cron` sendet den Feed und endet mit der Ausführung.

Mit den folgenden Ereignissen wird ein vollständiger Synchronisations- und Indexaufbau Trigger:

* Onboarding [Katalogdatensynchronisierung](install.md#synchronize-catalog-data)
* Änderungen an Attributmetadaten

Ändern Sie beispielsweise die `Use in Search` -Eigenschaft der `color` Attribut aus `No` nach `Yes` ändert die Attributmetadaten in `searchable=true`und Trigger eine vollständige Synchronisierung und Neuindizierung durchführen. Der folgende Attribut-Metadaten-Trigger enthält eine vollständige Synchronisierung und Neuindizierung, wenn er geändert wurde:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Streaming-Produktaktualisierungen

Nach der Erstellung des anfänglichen Index während [Onboarding](install.md#synchronize-catalog-data)werden die folgenden inkrementellen Produktupdates kontinuierlich synchronisiert und neu indiziert:

* Neue Produkte zum Katalog hinzugefügt
* Änderungen an Produktattributwerten

Fügen Sie beispielsweise einen neuen Musterwert zum `color` -Attribut wird als Streaming-Produktaktualisierung behandelt.
Workflow für Streaming-Update:

1. Aktualisierte Produkte werden von der Adobe Commerce-Instanz mit dem Katalogdienst synchronisiert.
1. Der Indizierungsdienst sucht kontinuierlich nach Produktaktualisierungen aus dem Katalogdienst. Aktualisierte Produkte werden indiziert, sobald sie im Katalogdienst ankommen.
1. Es kann bis zu 15 Minuten dauern, bis eine Produktaktualisierung in [!DNL Live Search].

## Clientsuche

Die [!DNL Live Search] Mit der API kann ein Client nach jedem beliebigen Produktattribut sortieren, indem er die [storefront property](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Wird zum Sortieren in Produktlisten verwendet* nach `Yes`. Abhängig vom Design bewirkt diese Einstellung, dass das -Attribut als Option in die [Sortieren nach](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) Paginierungssteuerung auf Katalogseiten. Bis zu 300 Produktattribute können durch [!DNL Live Search], mit [Storefront-Eigenschaften](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) die durchsuchbar und filterbar sind.
Die Indexmetadaten werden in der Indizierungs-Pipeline gespeichert und sind für den Suchdienst verfügbar.

![[!DNL Live Search] Index-Metadaten-API-Diagramm](assets/index-metadata-api.svg)

### Workflow für sortierbare Attribute

1. Client ruft Suchdienst auf.
1. Suchdienst ruft Suchadministratordienst auf.
1. Suchdienst-Aufrufe Indizierung der Pipeline.

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
