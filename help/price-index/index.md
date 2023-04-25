---
title: SaaS-Preisindizierung
description: Verwenden der SaaS-Preisindizierung zur Leistungsverbesserung
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 45999b6499f248ea4138f7de4e910c274e747a04
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# SaaS-Preisindizierung

Die SaaS-Preisindizierung beschleunigt die Zeit, die benötigt wird, um Preisänderungen auf der Website eines Kunden nach deren Übermittlung widerzuspiegeln. Dieses optionale Modul ermöglicht Händlern mit großen, komplexen Katalogen oder mit mehreren Websites oder Kundengruppen, Preisänderungen schneller und kontinuierlich zu verarbeiten.

Der größte Engpass der Pipeline: Rechenintensive Prozesse wie Indizierung und Preisberechnung wurden vom PHP-Kern in die Cloud-Infrastruktur der Adobe verschoben. Dadurch können Händler Ressourcen schnell skalieren, um die Indexierungszeiten zu erhöhen, und diese Änderungen an Websites mit viel schnelleren Geschwindigkeiten widerspiegeln.

Alle Händler, die die Anforderungen erfüllen, können von diesen Verbesserungen profitieren, aber diejenigen, die die größten Gewinne erzielen, sind Kunden mit:

* Konstante Preisänderungen: Händler, die wiederholte Preisänderungen erfordern, um strategische Ziele wie häufige Promotions, saisonale Rabatte oder Inventarmarkdowns zu erreichen.
* Mehrere Websites und/oder Kundengruppen: Händler mit freigegebenen Produktkatalogen über mehrere Websites (Domänen/Marken) und/oder Kundengruppen hinweg.
* Große Anzahl einzigartiger Preise für Websites oder Kundengruppen: Händler mit umfangreichen gemeinsamen Produktkatalogen, die individuelle Preise für Websites oder Kundengruppen enthalten, wie B2B-Händler mit vorab ausgehandelten Preisen, Marken mit unterschiedlichen Preisstrategien.

Wenn Sie Anwendungen von Drittanbietern haben, die sich auf den PHP-Core-Preisindex verlassen, lesen Sie die Dokumentation und wenden Sie sich an den Erweiterungsanbieter, bevor Sie Änderungen vornehmen.

Die SaaS-Preisindizierung ist für Kunden, die Adobe Commerce-Dienste nutzen, kostenlos verfügbar.

In diesem Mini-Handbuch wird beschrieben, wie die SaaS-Preisindizierung funktioniert und wie sie aktiviert wird.

## Systemanforderungen

Zur Verwendung der SaaS-Preisindizierung benötigen Sie:

* Adobe Commerce 2.4.4+
* Mindestens einer der folgenden SaaS-Dienste installiert:

   * [Catalog Service](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Produkt-Recommendations](../product-recommendations/guide-overview.md)

## Module

Die SaaS-Preisindizierung nutzt eine Reihe von Modulen, um Funktionen bereitzustellen. Die Liste der erforderlichen Module kann je nach Store-Einrichtung etwas anders aussehen.

Diese Module fügen die neuen Feeds dem Administrator hinzu. Diese Feeds übertragen Daten, die für Preisberechnungen erforderlich sind, an den SaaS-Indexer und ignorieren den PHP Core-Preisindex.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Kunden, die Luma und Adobe Commerce Core GraphQL verwenden, können ein Modul installieren, das die Luma-Kompatibilität bietet und den PHP Core-Preisindex deaktiviert:

```
adobe-commerce/catalog-adapter
```

Die `catalog-adapter` ist nur mit Version 2.4.5 kompatibel. Die Unterstützung für 2.4.4 und 2.4.6 wird demnächst veröffentlicht.
Der PHP Core-Preisindex kann bei Bedarf durch eine Drittanbietererweiterung oder aus anderen Gründen wieder aktiviert werden.

## Einschränkungen

Abhängig von Faktoren wie Produkttypen, Preiskomplexität und Kataloggröße kann die SaaS-Preisindizierung die richtige Lösung für Ihr Geschäft sein. Lesen Sie die folgenden Einschränkungen und stellen Sie fest, ob dies eine gute Lösung für Ihre Site ist.

Derzeit unterstützt die SaaS-Preisindizierung einfache, gruppierte, virtuelle, konfigurierbare und gebündelte dynamische Produktarten.
Die Unterstützung für herunterladbare, vergriffene Karten und behobene Produkttypen von Bundle wird in Kürze angeboten.

Die SaaS-Preisindizierung unterstützt Basispreise:

* Min./Max. regulärer Preis
* Min./Max. Endpreis
* Sonderpreise
* Preise der Kundengruppen
* Katalogregelpreise

Sobald Sie sich für die Verwendung des neuen Preisangebots entschieden haben, können Sie sich an [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) , damit Sie es rückgängig machen können.

Neue Feeds sollten manuell mit der `resync` [CLI, Befehl](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Andernfalls werden die Daten im standardmäßigen Synchronisierungsprozess aktualisiert. Weitere Informationen zu [Katalogsynchronisierung](../landing/catalog-sync.md) Prozess.

## Nutzungsszenarien

### Luma ohne Erweiterungsabhängigkeiten

* Ein Luma- oder Abode Commerce Core GraphQL-Händler, auf dem ein erforderlicher Dienst installiert ist (Live Search, Product Recommendations, Catalog Service)
* Keine Drittanbietererweiterungen, die auf den PHP-Core-Preisindex angewiesen sind
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren.
1. Installieren Sie den Katalogadapter.

### Luma und Abode Commerce Core GraphQl mit PHP Core-Preisindexierabhängigkeiten

* Ein Luma- oder Abode Commerce Core GraphQL-Händler, auf dem ein unterstützter Dienst installiert ist (Live Search, Product Recommendations, Catalog Service)
* Mit einer Drittanbietererweiterung, die auf den PHP-Core-Preisindex angewiesen ist
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren
1. Installieren Sie den Katalogadapter.
1. Aktivieren Sie den PHP Core-Preisindex erneut.
1. Verwenden Sie neue Feeds und den Luma-Kompatibilitätscode im `catalog-adapter` -Modul.

### Headless-Händler

* Ein Headless-Händler, der einen unterstützten Dienst installiert hat (Live Search, Product Recommendations, Catalog Service)
* Keine Abhängigkeit von PHP Core-Preisindex
* Verkaufen einfacher, konfigurierbarer, gruppierter, virtueller und gebündelter dynamischer Produkte

1. Neue Feeds aktivieren
1. Installieren Sie den Katalog-Adapter, der den PHP Core-Preisindex deaktiviert.

### Luma/Core GraphQL/Headless mit nicht unterstützten Produktarten

* Luma/Headless-Händler
* Verkauf von Geschenkkarten, herunterladbaren oder gebündelten festen Produkten

Warten Sie bei derzeit nicht unterstützten Produktarten auf die vollständige Unterstützung des Produkttyps.
