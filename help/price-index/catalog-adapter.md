---
title: Katalogadaptererweiterung
description: Verwenden des Katalogadapters zum Rendern von Preisen über Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Katalogadapter

Die `Catalog Adapter` -Erweiterung deaktiviert den standardmäßigen Adobe Commerce Product Price-Indexer und verwendet stattdessen die Preise, die über das [Catalog Service](../catalog-service/overview.md).
Der Adobe Commerce Product Price-Indexer ist deaktiviert und kann nicht aktiviert werden, wenn diese Erweiterungsmodule installiert sind. Nur durch das Entfernen oder Deaktivieren dieser Erweiterung kann der standardmäßige Produktpreisindex erneut aktiviert werden.

## Voraussetzungen

* Adobe Commerce 2.4.4+
* Installieren Sie beide der folgenden Commerce-Dienste:

   * [Catalog Service](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)

## Installation

So verwenden Sie die `catalog-adapter` -Modul, [!DNL Live Search] und [!DNL Catalog Service] muss zuerst installiert und konfiguriert werden. Befolgen Sie die [Installieren [!DNL Live Search]](../live-search/install.md) und [Installation des Katalogdienstes](../catalog-service/installation.md) Anweisungen vor dem Fortfahren.

Führen Sie nach der Installation dieser Dienste den folgenden Befehl aus:

```bash
composer require adobe-commerce/catalog-adapter
```

## Aktivieren Sie den Adobe Commerce Product Price-Indexer erneut.

Wenn Sie Anwendungen von Drittanbietern verwenden, die auf den standardmäßigen Adobe Commerce Product Price-Indexer angewiesen sind, können Sie ihn mit den folgenden Befehlen erneut aktivieren:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Deaktivieren des Produktpreisindexers für das Headless-Storefront-Szenario

Wenn Sie über eine Headless-Commerce-Instanz verfügen, müssen Sie möglicherweise den Adobe Commerce-Produktpreisindex deaktivieren, um die Auslastung Ihrer Adobe Commerce-Instanz zu reduzieren.
Dies geschieht durch Installation der `magento/module-price-indexer-disabler` -Modul:

```bash
composer require magento/module-price-indexer-disabler
```

## Nutzungsszenarien

Im Folgenden finden Sie einige häufige `Catalog Adapter` Szenarien.

### Keine Abhängigkeiten von Adobe Commerce Product Price Index

* Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, auf dem ein erforderlicher Dienst installiert ist (Live Search, Product Recommendations, Catalog Service).
* Keine Drittanbietererweiterungen, die auf den Adobe Commerce Product Price Indexer angewiesen sind

1. Installieren Sie den Katalogadapter.

### Abhängigkeiten vom Adobe Commerce Product Price-Indexer

* Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, auf dem ein unterstützter Dienst installiert ist (Live Search, Product Recommendations, Catalog Service).
* Sie verwenden eine Drittanbietererweiterung, die auf dem Adobe Commerce Product Price-Indexer basiert

1. Installieren Sie den Katalogadapter.
1. Aktivieren Sie den standardmäßigen Adobe Commerce Product Price-Indexer erneut.

### Headless-Commerce-Instanzen

* Ein Händler mit einer Headless-Commerce-Instanz mit installierten erforderlichen Diensten (Live Search, Product Recommendations, Catalog Service)
* Keine Abhängigkeit vom standardmäßigen Adobe Commerce Product Price-Indexer

1. Installieren Sie die `magento/module-price-indexer-disabler` -Modul aus dem Katalog-Adapterpaket.
