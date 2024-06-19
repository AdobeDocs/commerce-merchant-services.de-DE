---
title: SaaS-Preisindizierung
description: Verwenden der SaaS-Preisindizierung zur Leistungsverbesserung
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# SaaS-Preisindizierung

Die Preisindizierung von SaaS verbessert die Site-Leistung, indem schwere Rechenvorgänge wie Indexierung und Preisberechnung von der Commerce-Anwendung in die Adobe Cloud-Infrastruktur verschoben werden. Dieser Ansatz ermöglicht es Händlern, Ressourcen schnell zu skalieren, um die Indexierungszeiten für Preise zu verkürzen, um Preisänderungen schneller widerzuspiegeln, wenn Daten an die Storefront und verbundene Commerce-Dienste gesendet werden.

Das folgende Diagramm zeigt den indizierenden Datenfluss zu SaaS-Diensten, wenn Commerce die Variable [Preisindizierung](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) -Prozess, der in der Commerce-Anwendung enthalten ist:

![Standarddatenfluss](assets/old_way.png)

Wenn die SaaS-Preisindizierung aktiviert ist, ändert sich der Datenfluss. Die Preisindizierung erfolgt mithilfe von [Commerce SaaS-Datenexport](../data-export/data-synchronization.md).

![Datenfluss der SaaS-Preisindizierung](assets/new_way.png)

Alle Händler können von der Nutzung der SaaS-Preisindizierung profitieren, aber Händler mit Projekten mit den folgenden Eigenschaften können die größten Gewinne erzielen:

* **Konstante Preisänderungen**-Händler, die wiederholte Preisänderungen erfordern, um strategische Ziele wie häufige Promotions, saisonale Rabatte oder Inventarmarkdowns zu erreichen.
* **Mehrere Websites und/oder Kundengruppen**-Händler mit freigegebenen Produktkatalogen über mehrere Websites (Domänen/Marken) und/oder Kundengruppen hinweg.
* **Viele einzigartige Preise auf Websites oder Kundengruppen**-Händler mit umfangreichen freigegebenen Produktkatalogen, die einzigartige Preise für Websites oder Kundengruppen enthalten. Beispiele sind B2B-Händler mit vorverhandelten Preisen oder Marken mit unterschiedlichen Preisstrategien.

## SaaS-Preisindizierung verwenden

Die SaaS-Preisindizierung wird bei der Installation von Adobe Commerce Services automatisch aktiviert. Es unterstützt die Preisberechnung für alle integrierten Adobe Commerce-Produktarten.

### Voraussetzungen

* Adobe Commerce 2.4.4+

### Voraussetzungen

* Einer der folgenden Commerce-Dienste muss mit der neuesten Version der Commerce-Erweiterung installiert sein:

   * [Catalog Service](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)
   * [Produkt-Recommendations](../product-recommendations/guide-overview.md)


>[!NOTE]
>
>Bei Bedarf kann der standardmäßige Preisindexer in der Commerce-Anwendung mithilfe der Variablen [Katalogadapter](catalog-adapter.md).

## Preise mit SaaS-Preisindizierung synchronisieren

Nachdem Sie die SaaS-Preisindizierung für Adobe Commerce aktiviert haben, aktualisieren Sie die Preise auf der Storefront und in Commerce Services, indem Sie die neuen Feeds synchronisieren:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Preise für benutzerdefinierte Produktarten

Preisberechnungen werden für benutzerdefinierte Produktarten wie Basispreis, Sonderpreis, Gruppenpreis, Katalogregelpreis usw. unterstützt.

Wenn Sie über einen benutzerdefinierten Produkttyp verfügen, der eine bestimmte Formel zur Berechnung des Endpreises verwendet, können Sie das Verhalten des Produktpreis-Feeds erweitern.

1. Erstellen Sie ein Plug-in im `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` -Klasse.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
       </type>
   </config>
   ```

1. Erstellen Sie eine Methode mit der benutzerdefinierten Formel:

   ```php
   class UpdatePriceFromFeed
   {
       /**
       * @param ProductPrice $subject
       * @param array $result
       * @param array $values
       *
       * @return array
       */
       public function afterGet(ProductPrice $subject, array $result, array $values) : array
       {
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```

