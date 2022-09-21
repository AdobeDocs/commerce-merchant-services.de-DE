---
title: productSearch-Abfrage
description: '"Ein Referenzhandbuch für die GraphQL-Abfrage "productSearch"für den Adobe Commerce-Katalogdienst."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 2%

---


# productSearch-Abfrage

Der Katalogdienst für Adobe Commerce `productSearch` -Abfrage kann LiveSearch verwenden, um Details zu den als Eingabe angegebenen SKUs zurückzugeben. Diese Abfrage entspricht zwar der [`productSearch` Abfrage](https://devdocs.magento.com//live-search/product-search.html), gibt LiveSearch eine `productView` -Objekt. Siehe [`productSearch` Abfrage](https://devdocs.magento.com//live-search/product-search.html) Thema für Referenzinformationen.

## Syntax

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## Erforderliche Kopfzeilen

Sie müssen die folgenden HTTP-Header angeben, um diese Abfrage auszuführen.

| Kopfzeile | Beschreibung |
|--- | ---|
| `Magento-Customer-Group` | Für Storefront-Clients ist dieser Wert in der Storefront im `dataservices_customer_group` Cookie. |
| `Magento-Environment-Id` | Dieser Wert wird angezeigt unter **System** > **Commerce Services Connector** > **SaaS-Kennung** > **Datenspeicherkennung** oder durch Ausführen der `bin/magento config:show services_connector/services_id/environment_id` Befehl. |
| `Magento-Store-Code` | Der dem Store zugewiesene Code, der mit der aktiven Store-Ansicht verknüpft ist. Beispiel, `main_website_store`. |
| `Magento-Store-View-Code` | Der der aktiven Store-Ansicht zugewiesene Code. Beispiel, `default`. |
| `Magento-Website-Code` | Der der Website zugewiesene Code, der mit der aktiven Store-Ansicht verknüpft ist. Beispiel, `base`. |
| `X-Api-Key` | Ein eindeutiger Schlüssel, der während des Onboarding-Prozesses generiert wird. |

## Beispielverwendung

Im folgenden Beispiel gibt die Abfrage Informationen zu denselben Produkten wie im vorherigen Beispiel zurück. Es wurde jedoch so konstruiert, dass Artikelinformationen innerhalb des Katalogdienstes zurückgegeben werden `productView` Objekt anstelle des Kerns `product` -Objekt. Beachten Sie, dass sich die Preisinformationen je nach Produkttyp unterscheiden. Aus Gründen der Kürze werden keine Facetteninformationen angezeigt.

**Anfrage:**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**Antwort:**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
