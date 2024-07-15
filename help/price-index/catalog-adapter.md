---
title: Katalogadaptererweiterung
description: Verwenden des Katalogadapters zum Rendern von Preisen über Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Katalogadapter

Die Erweiterung `[!DNL Catalog Adapter]` deaktiviert den standardmäßigen Produktpreisindex, der in der Commerce-Anwendung enthalten ist, und verwendet stattdessen die vom [Katalogdienst](../catalog-service/overview.md) bereitgestellten Preise.

Der Adapter wurde für die Verwendung mit dem [SAAS-Datenexport](../data-export/overview.md) und dem Adobe Commerce-Dienst entwickelt. Der SAAS-Datenexport ist für die Übermittlung der Preise verantwortlich, und der [!DNL Catalog Adapter] ruft alle Preise vom Adobe Commerce-Dienst ab.

Wenn Sie den [!DNL Catalog Adapter] aktivieren, wirken sich die Preisindizierung und Vorgänge wie folgt aus:

- Der in der Adobe Commerce-Anwendung enthaltene Preisindex ist deaktiviert.
- Preise werden mithilfe des SaaS-Datenexports und des [SaaS-Preisindexers](price-indexing.md) verwaltet.
- Wenn ein Kunde ein Produkt, eine Kategorie oder eine andere Seite öffnet, die die Produktpreise anzeigt, werden die Preise vom Adobe Commerce-Dienst abgerufen.
- Die Preise werden an den Adobe Commerce-Dienst gesendet, indem Daten aus dem [SAAS-Datenexport](../data-export/overview.md) synchronisiert werden.
- Beim Checkout werden die Preise dynamisch neu berechnet.

Sie können die Preisindizierung in der Commerce-Anwendung erneut aktivieren, indem Sie die Erweiterung des Katalogadapters entfernen oder deaktivieren.

## Voraussetzungen

- Adobe Commerce 2.4.4+
- Installieren Sie einen der folgenden Commerce-Dienste:

   - [Live Search](../live-search/install.md)
   - [Produkt-Recommendations](../product-recommendations/install-configure.md)
   - [Catalog Service](../catalog-service/installation.md)

## Installation

Die Catalog Adapter-Erweiterung ist ein Composer-Metapaket, das die folgenden Module installiert:

- **Price Indexer Disabler** - Dieses Modul deaktiviert den Preisindex in der Commerce-Anwendung, sodass Preise über die SaaS-Preisindizierung bereitgestellt werden. Der Produktpreisindex in der Commerce-Anwendung kann nicht aktiviert werden, wenn die SaaS-Preisindizierungserweiterung installiert ist.
- **Preisanbieter** - Dieses Modul bietet Preise für Produkte aus dem Adobe Commerce-Dienst. Es bildet die Suchabfrage und erhält die Preise für die Produkte auf der Vorderseite.
- **Catalog Service Search Adapter** - Dieses Modul überträgt Preise von der Adobe Commerce-Anwendung an einen Adobe Commerce-Dienst, wenn eine Produktsuchanforderung eingeht.

## Installationsschritte

>[!BEGINTABS]

>[!TAB Cloud-Infrastruktur]

Verwenden Sie diese Methode, um die [!DNL Catalog Adapter] für eine Commerce Cloud-Instanz zu installieren.

1. Wechseln Sie auf Ihrer lokalen Workstation zum Projektverzeichnis für Ihr Adobe Commerce-Projekt in der Cloud-Infrastruktur-Projekt.

   >[!NOTE]
   >
   >Informationen zum lokalen Verwalten von Commerce-Projektumgebungen finden Sie unter [Verwalten von Verzweigungen mit der CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) im _Benutzerhandbuch zu Adobe Commerce on Cloud Infrastructure_.

1. Sehen Sie sich die Umgebungsverzweigung an, die mit der Adobe Commerce Cloud-CLI aktualisiert werden soll.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Fügen Sie das Catalog Adapter-Modul hinzu.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Aktualisieren Sie Package-Abhängigkeiten.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Übernehmen und pushen Sie Code-Änderungen für die Dateien `composer.json` und `composer.lock`.

1. Fügen Sie die Codeänderungen für die Dateien `composer.json` und `composer.lock` hinzu, übertragen Sie sie und übertragen Sie sie in die Cloud-Umgebung.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   Durch das Übermitteln der Aktualisierungen an die Cloud-Umgebung wird der [Commerce-Cloud-Bereitstellungsprozess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) initiiert, um die Änderungen anzuwenden. Überprüfen Sie den Bereitstellungsstatus im [Bereitstellungsprotokoll](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-premise]

Verwenden Sie diese Methode, um die [!DNL Catalog Adapter] für eine lokale Instanz zu installieren.

1. Fügen Sie Ihrem Projekt mithilfe von Composer den Katalogadapter hinzu:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In einigen Fällen, insbesondere bei der Bereitstellung in der Produktionsumgebung, sollten Sie das Löschen von kompiliertem Code vermeiden, da dies einige Zeit in Anspruch nehmen kann. Stellen Sie sicher, dass Sie Ihr System sichern, bevor Sie Änderungen vornehmen.

>[!ENDTABS]


## Aktivieren Sie den Adobe Commerce-Produktpreisindex erneut.

Wenn Sie Anwendungen von Drittanbietern verwenden, die auf den standardmäßigen Adobe Commerce-Produktpreisindex angewiesen sind, können Sie ihn mit den folgenden Befehlen erneut aktivieren:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Deaktivieren des Produktpreisindexers für das Headless-Storefront-Szenario

Wenn Sie über eine Headless-Commerce-Instanz verfügen, müssen Sie möglicherweise den Adobe Commerce-Produktpreisindex deaktivieren, um die Auslastung Ihrer Adobe Commerce-Instanz zu reduzieren. Sie können diese Aufgabe abschließen, indem Sie das Modul `magento/module-price-indexer-disabler` installieren:

```bash
composer require magento/module-price-indexer-disabler
```

## Nutzungsszenarien

Im Folgenden finden Sie einige gängige `[!DNL Catalog Adapter]`-Szenarien.

### Keine Abhängigkeiten vom Adobe Commerce-Produktpreisindex

- Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, auf dem ein erforderlicher Dienst installiert ist (Live Search, Product Recommendations, Catalog Service).
- Keine Integrationen mit Drittanbietererweiterungen, die auf dem Adobe Commerce-Produktpreisindex basieren

1. Installieren Sie die [!DNL Catalog Adapter].

### Abhängigkeiten vom Adobe Commerce-Produktpreisindex

- Sie sind ein Händler von Luma oder Adobe Commerce Core GraphQL, auf dem ein unterstützter Dienst installiert ist (Live Search, Product Recommendations, Catalog Service).
- Sie verwenden eine Drittanbietererweiterung, die auf dem Adobe Commerce-Produktpreisindex basiert

1. Installieren Sie die [!DNL Catalog Adapter].
1. Aktivieren Sie den standardmäßigen Adobe Commerce-Produktpreisindex erneut.

### Headless-Commerce-Instanzen

- Ein Händler mit einer Headless-Commerce-Instanz mit installierten erforderlichen Diensten (Live Search, Product Recommendations, Catalog Service)
- Keine Abhängigkeit vom standardmäßigen Adobe Commerce-Produktpreisindex

1. Installieren Sie das Modul `magento/module-price-indexer-disabler` aus dem Paket [!DNL Catalog Adapter] .

