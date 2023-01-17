---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] für Adobe Commerce bietet eine Möglichkeit, mehrere Datenquellen über einen gemeinsamen GraphQL-Endpunkt zu integrieren."'
source-git-commit: 7b95be48c21e17cb6ba88d326fd061f7de2f8fb5
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

Die [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe IO private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

Der erste Schritt zur Verwendung des API-Meshs mit dem Catalog Service besteht darin, API-Mesh mit Ihrer Instanz zu verbinden. Detaillierte Anweisungen finden Sie unter [Erstellen eines Gitters](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Um das Setup abzuschließen, benötigen Sie die [Adobe IO CLI-Paket](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installiert.

Nachdem der Mesh auf Adobe I/O konfiguriert wurde, führen Sie den folgenden Befehl aus, der einen `CommerceCatalogServiceGraph` zu Ihrem Gitter.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` ist eine separate Datei, in der häufig verwendete Werte für Adobe IO gespeichert werden.
Beispielsweise kann der API-Schlüssel in der Datei gespeichert werden:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Nach Ausführung dieses Befehls sollte der Catalog Service über das API-Mesh ausgeführt werden. Sie können die `aio api-mesh:get` -Befehl, um die Konfiguration Ihres aktualisierten Netzwerks anzuzeigen.

## API-Mesh verwenden

Mit dem API-Mesh können Benutzer externe Datenquellen nutzen, um Ihre Adobe Commerce-Instanz zu verbessern. Sie kann auch verwendet werden, um vorhandene Commerce-Daten zu konfigurieren und neue Funktionen zu aktivieren.

In diesem Beispiel wird der API-Mesh verwendet, um die Ebenenpreise in Adobe Commerce zu aktivieren.
Ersetzen Sie die `name `, `endpoint` und `x-api-key` -Werte.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Abfragen Sie nach der Konfiguration das Mesh nach gestaffelten Preisen:

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
