---
title: "Anzeigen von besteuerten Preisen mit dem API-Mesh"
description: "Verwenden [!DNL API Mesh] für Adobe Commerce und Catalog Service zur Anzeige der Preise einschließlich Steuern."
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: d235f28c7f438fe89eb20ea7ef8bda7ae39733c0
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Anzeigen von besteuerten Preisen mit API-Mesh für Adobe Developer App Builder

[API-Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe I/O Runtime private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

In diesem Thema wird API-Mesh verwendet, um Produktpreise auf einer Produktdetailseite mit konfigurierten Steuern anzuzeigen.

## Festlegen von Steuersätzen

Sie müssen Steuern für die Anzeige auf der Produktdetailseite konfiguriert haben.

1. [Festlegen von Steuersätzen](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/tax-rules.html).
1. Steuern aktivieren [im Katalog angezeigt](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/display-settings.html#step-1%3A-configure-catalog-prices-display-settings)und legen Sie sie auf `Including and Excluding Tax` oder `Including Tax`.

Stellen Sie sicher, dass der Catalog Service funktioniert, indem Sie eine Produktdetailseite überprüfen.

![Auf der Produktdetailseite angezeigte Steuern](assets/display-tax.png)

## API-Gitter konfigurieren

Verbinden Sie, falls noch nicht geschehen, den API-Mesh mit Catalog Service mit Ihrer Instanz. Detaillierte Anweisungen finden Sie unter [Erste Schritte](https://developer.adobe.com/graphql-mesh-gateway/gateway/getting-started/) Thema im API-Mesh-Entwicklerhandbuch.

Im `mesh.json` ersetzen Sie die `name `, `endpoint`, und `x-api-key` -Werte.

```json
{
    "meshConfig": {
      "sources": [
        {
          "name": "<NAME OF MESH>",
          "handler": {
            "graphql": {
              "endpoint": "<COMMERCE INSTANCE GQL ENDPOINT URL>"
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
              "endpoint": "https://catalog-service-sandbox.adobe.io/graphql/",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "API_KEY",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend type ComplexProductView {\n  priceWithTaxes: Core_PriceRange\n}\n extend type SimpleProductView {\n  priceWithTaxes: Core_PriceRange\n}\n",
      "additionalResolvers": [
            {  
              "targetTypeName": "ComplexProductView",
              "targetFieldName": "priceWithTaxes",
              "sourceName": "MagentoQACore",
              "sourceTypeName": "Query",
              "sourceFieldName": "Core_products",
              "requiredSelectionSet": "{\n items {\n sku, \n price_range {\n minimum_price {\n final_price {\n value\n currency\n }\n }\n }\n }\n }",
                "sourceArgs": {
                    "filter.sku.eq": "{root.sku}"
                },
                "result": "items[0].price_range"
            },
            {  
              "targetTypeName": "SimpleProductView",
              "targetFieldName": "priceWithTaxes",
              "sourceName": "MagentoQACore",
              "sourceTypeName": "Query",
              "sourceFieldName": "Core_products",
              "requiredSelectionSet": "{\n items {\n sku, \n price_range {\n minimum_price {\n final_price {\n value\n currency\n }\n }\n }\n }\n }",
                "sourceArgs": {
                    "filter.sku.eq": "{root.sku}"
                },
                "result": "items[0].price_range"
            }
        ]
     }
  }
```

Diese `mesh.json` Konfigurationsdatei:

* Wandelt die Commerce-Core-Anwendung so um, dass &quot;Core_&quot;erforderlich ist, das Abfragen oder Typen vorangestellt wird. Dadurch werden mögliche Namenskonflikte mit dem Catalog Service verhindert.
* Erweitert die `ComplexProductView` und `SimpleProductView` Typen mit einem neuen Feld namens `priceWithTaxes`.
* Fügt einen benutzerdefinierten Resolver für das neue Feld hinzu.

Erstellen Sie das Gitter mit dem [create, Befehl](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/#create-a-mesh-1) mit dem `mesh.json` -Datei.

### GraphQL-Abfrage

Sie können die neue `priceWithTaxes` Daten mit GraphQL.

Abfragebeispiel:

```graphql
query {
    products(skus:[MH07]) {
        __typename
        id
        sku
        name
        description
        shortDescription
        addToCartAllowed
        url
        ... on ComplexProductView {
            priceWithTaxes {
              minimum_price {
                final_price {
                  value
                }
              }
              maximum_price {
                final_price {
                  value
                }
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
                    roles
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
                    roles
                }
            }
        }
    }
}
```

Abfrageantwort:

```json
{
  "data": {
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVnd053AFpHVm1ZWFZzZEEAWkRWa09Ua3hNVFl0WTJJd015MDBaRGMwTFRnME16a3RNak01TVRVNE9ESTBOemd4AGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSE1EQTFPRFEyTVRjeA",
        "sku": "MH07",
        "name": "Hero Hoodie13",
        "description": "<p>Gray and black color blocking sets you apart as the Hero Hoodie keeps you warm on the bus, campus or cold mean streets. Slanted outsize front pockets keep your style real . . . convenient.</p>\r\n<p>* Full-zip gray and black hoodie.<br />* Ribbed hem.<br />* Standard fit.<br />* Drawcord hood cinch.<br />* Water-resistant coating.</p>",
        "shortDescription": "",
        "addToCartAllowed": true,
        "url": "http://commerce_url/hero-hoodie.html",
        "priceWithTaxes": {
          "minimum_price": {
            "final_price": {
              "value": 8.330001
            }
          },
          "maximum_price": {
            "final_price": {
              "value": 13355.524701
            }
          }
        },
        "priceRange": {
          "maximum": {
            "final": {
              "amount": {
                "value": 39.02,
                "currency": "USD"
              }
            },
            "regular": {
              "amount": {
                "value": 54,
                "currency": "USD"
              }
            },
            "roles": [
              "visible"
            ]
          },
          "minimum": {
            "final": {
              "amount": {
                "value": 39.02,
                "currency": "USD"
              }
            },
            "regular": {
              "amount": {
                "value": 54,
                "currency": "USD"
              }
            },
            "roles": [
              "visible"
            ]
          }
        }
      }
    ]
  },
  "extensions": {}
}
```
