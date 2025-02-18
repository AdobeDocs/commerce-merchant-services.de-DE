---
title: GraphQL
description: Mit dem  [!DNL Live Search] GraphQL-Arbeitsbereich können Sie Abfragen mit Ihren Live-Daten erstellen.
exl-id: f7b17c5a-a97b-4724-a50e-83e28a4c4c38
source-git-commit: cf94623fd4a87c13d15c81ac62243a508cb1d14d
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

Der Arbeitsbereich *GraphQL* ermöglicht es Admins, GraphQL-Abfragen mit ihren eigenen Daten zu erstellen und zu testen.

Dieser Arbeitsbereich unterstützt die [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) und [`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/) Abfragen.

![GraphQL Workspace](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
      }
    }
    facets {
      title
    }
  }
}
```

Variablen:

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```

