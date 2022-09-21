---
title: Produktabfrage
description: '"Ein Referenzhandbuch für die GraphQL-Abfrage "products"für den Adobe Commerce Catalog Service."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# Produktabfrage

Der Katalogdienst für Adobe Commerce `products` -Abfrage gibt Details zu den als Eingabe angegebenen SKUs zurück. Obwohl diese Abfrage denselben Namen hat wie die [`products` Abfrage](https://devdocs.magento.com//guides/v2.4/graphql/queries/products.html) , die mit Adobe Commerce und Magento Open Source bereitgestellt wird, gibt es einige Unterschiede.

Die Katalogdienst-Abfrage erfordert einen oder mehrere SKU-Werte als Eingabe. Die Abfrage dient hauptsächlich dem Abrufen von Informationen zum Rendern der folgenden Inhaltstypen:

* Produktdetailseiten - Sie können vollständige Details zum Produkt angeben, das durch die angegebene SKU identifiziert wurde.

* Produktvergleichsseiten - Sie können ausgewählte Informationen über mehrere Produkte abrufen, z. B. Name, Preis und Bild.

Die `ProductView` Das Ausgabeobjekt unterscheidet sich deutlich vom Kern `products` Abfrage `Products` Output-Objekt. Zu den wichtigsten Unterschieden gehören:

* Produkte sind entweder einfach oder komplex. Einfache, virtuelle, herunterladbare und Geschenkkartenprodukte werden der `SimpleProductView`. Alle anderen Produktarten werden `ComplexProductView`. Einfache Produkte haben Preise definiert. Komplexe Produkte haben Preisspannen. Da komplexe Produkte aus mehreren einfachen Produkten bestehen, haben sie Zugriff auf einfache Produktpreise.

* Merchant-definierte Attribute werden in einem Container der obersten Ebene angezeigt und geben die Storefront-Rollen an. Rollen beinhalten &quot;Auf PDP anzeigen&quot;, &quot;Auf PLP anzeigen&quot;und &quot;In Suchergebnissen anzeigen&quot;.

* Bilder sind auch als Container der obersten Ebene verfügbar und können anhand ihrer Rolle gefiltert werden. Ein Bild kann eine Basis-, kleine oder Miniaturansicht-Rolle haben.

## Syntax

```graphql
products (skus [String]) [ProductView]
```

## Erforderliche Kopfzeilen

Sie müssen die folgenden HTTP-Header angeben, um diese Abfrage auszuführen.

| Kopfzeile | Beschreibung |
| --- | --- |
| `Magento-Customer-Group` | Für Storefront-Clients ist dieser Wert in der Storefront im `dataservices_customer_group` Cookie. |
| `Magento-Environment-Id` | Dieser Wert wird angezeigt unter **System** > **Commerce Services Connector** > **SaaS-Kennung** > **Datenspeicherkennung** oder durch Ausführen der `bin/magento config:show services_connector/services_id/environment_id` Befehl. |
| `Magento-Store-Code` | Der dem Store zugewiesene Code, der mit der aktiven Store-Ansicht verknüpft ist. Beispiel, `main_website_store`. |
| `Magento-Store-View-Code` | Der der aktiven Store-Ansicht zugewiesene Code. Beispiel, `default`. |
| `Magento-Website-Code` | Der der Website zugewiesene Code, der mit der aktiven Store-Ansicht verknüpft ist. Beispiel, `base`. |
| `X-Api-Key` | Ein eindeutiger Schlüssel, der während des Onboarding-Prozesses generiert wird. |

## Beispielverwendung

### Details zu einem einfachen Produkt zurückgeben

Die folgende Abfrage gibt Details zu einem einfachen Produkt zurück.

**Anfrage:**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**Antwort:**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### Details zu einem komplexen Produkt zurückgeben {#complex-product-example}

Die folgende Abfrage gibt Details zu einem konfigurierbaren Produkt zurück.

**Anfrage:**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## Ausgabefelder

Die `ProductView` return -Objekt ist eine Schnittstelle, die die folgenden Felder enthalten kann. Sie wird von der [`SimpleProductView`](#SimpleProductView-type) und [`ComplexProductView`](#ComplexProductView-type) Typen.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Eine Liste der von Händlern definierten Attribute, die für die Storefront bestimmt sind. |
| `description` | Zeichenfolge | Die detaillierte Beschreibung des Produkts. |
| `id` | ID! | Die Produkt-ID, die als zusammengesetzter Schlüssel generiert und pro Gebietsschema eindeutig ist. |
| `images(roles: [String])` | [ProductViewImage] | Eine Liste der für das Produkt definierten Bilder. |
| `metaDescription` | Zeichenfolge | Eine kurze Übersicht über das Produkt für Suchergebnislisten. |
| `metaKeyword` | Zeichenfolge | Eine kommagetrennte Liste von Suchbegriffen, die nur für Suchmaschinen sichtbar sind. |
| `metaTitle` | Zeichenfolge | Eine Zeichenfolge, die in der Titelleiste und Registerkarte des Browsers sowie in den Suchergebnislisten angezeigt wird. |
| `name` | Zeichenfolge | Produktname. |
| `shortDescription` | Zeichenfolge | Eine Zusammenfassung des Produkts. |
| `sku` | Zeichenfolge | Produkt-SKU. |
| `url` | Zeichenfolge | Kanonische URL des Produkts. |

### ComplexProductView-Typ {#ComplexProductView-type}

Die `ComplexProductView` type steht für Paket-, Konfigurierungs- und Gruppenprodukte. Komplexe Produktpreise werden als Preisbereich zurückgegeben, da die Preiswerte je nach ausgewählten Optionen variieren können. Der Typ implementiert `ProductView`.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Eine Liste der von Händlern definierten Attribute, die für die Storefront bestimmt sind. |
| `description` | Zeichenfolge | Die detaillierte Beschreibung des Produkts. |
| `id` | ID! | Die Produkt-ID, die als zusammengesetzter Schlüssel generiert und pro Gebietsschema eindeutig ist. |
| `images(roles: [String])` | [ProductViewImage] | Eine Liste der für das Produkt definierten Bilder. |
| `metaDescription` | Zeichenfolge | Eine kurze Übersicht über das Produkt für Suchergebnislisten. |
| `metaKeyword` | Zeichenfolge | Eine kommagetrennte Liste von Suchbegriffen, die nur für Suchmaschinen sichtbar sind. |
| `metaTitle` | Zeichenfolge | Eine Zeichenfolge, die in der Titelleiste und Registerkarte des Browsers sowie in den Suchergebnislisten angezeigt wird. |
| `name` | Zeichenfolge | Produktname. |
| `options` | [ProductViewOption] | Eine Liste der auswählbaren Optionen. |
| `priceRange` | ProductViewPriceRange | Eine Reihe möglicher Preise für ein komplexes Produkt. |
| `shortDescription` | Zeichenfolge | Eine Zusammenfassung des Produkts. |

### Preistyp

Die `Price type` definiert den Preis eines einfachen Produkts oder eines Teils einer Preisspanne für ein komplexes Produkt. Sie kann eine Liste der Preisanpassungen enthalten.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `amount` | ProductViewMoney | Enthält den Geldwert und den Währungscode eines Produkts. |

### PriceAdjustment-Typ

Die `PriceAdjustment` type gibt den Betrag und die Art einer Preisanpassung an. Ein Beispielcode-Wert ist `weee`.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `amount` | Float | Höhe der Preisanpassung. |
| `code` | Zeichenfolge | Gibt die Art der Preisanpassung an. |

### ProductViewAttribute-Typ

Die `ProductViewAttribute` type ist ein Container für kundendefinierte Attribute, die in der Storefront angezeigt werden.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `label` | Zeichenfolge | Titel des Attributs. |
| `name` | String! | Name eines Attributcodes. |
| `roles` | [Zeichenfolge] | Rollen, die für ein Attribut auf der Storefront bestimmt sind, z. B. &quot;Auf PLP anzeigen&quot;, &quot;In PDP anzeigen&quot;oder &quot;In Suche anzeigen&quot;. |
| `value` | JSON | Attributwert, beliebig vom Typ. |

### ProductViewImage-Typ

Die `ProductViewImage` type enthält Details zu einem Produktbild.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `label` | Zeichenfolge | Die Anzeigebezeichnung des Produktbilds. |
| `roles` | [Zeichenfolge] | Eine Liste, die beschreibt, wie das Bild verwendet wird. Kann `image`, `small_image`oder `thumbnail`. |
| `url` | String! | Die URL zum Produktbild. |

### ProductViewMoney-Typ

Die `ProductViewMoney` Typ definiert einen Geldwert, einschließlich eines numerischen Werts und eines Währungscodes.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `currency` | ProductViewCurrency | Ein aus drei Buchstaben bestehender Währungscode, z. B. USD oder EUR. |
| `value` | Float | Eine Zahl, die einen Geldwert angibt. |

### ProductViewOption-Typ

Produktoptionen bieten eine Möglichkeit, Produkte zu konfigurieren, indem Sie eine Auswahl bestimmter Optionswerte treffen. Wenn Sie eine oder mehrere Optionen auswählen, wird auf ein bestimmtes einfaches Produkt verwiesen.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `id` | ID | Die ID der Option. |
| `multi` | Boolesch | Gibt an, ob die Option mehrere Optionen zulässt. |
| `required` | Boolesch | Gibt an, ob die Option ausgewählt werden muss. |
| `title` | Zeichenfolge | Der Anzeigename der Option. |
| `values` | [ProductViewOptionValue!] | Liste der verfügbaren Optionswerte. |

### ProductViewOptionValue-Schnittstelle

Die `ProductViewOptionValue` Die Benutzeroberfläche definiert die für die `ProductViewOptionValueProduct` und `ProductViewOptionValueConfiguration` Typen.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `id` | ID | Die ID eines Optionswerts. |
| `title` | Zeichenfolge | Der Anzeigename des Optionswerts. |

### ProductViewOptionValueConfiguration type

Die `ProductViewOptionValueConfiguration` type ist eine Implementierung von `ProductViewOptionValue` für Konfigurationswerte.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `id` | ID | Die ID eines Optionswerts. |
| `title` | Zeichenfolge | Der Anzeigename des Optionswerts. |

### ProductViewOptionValueProduct type

Die `ProductViewOptionValueProduct` type ist eine Implementierung von `ProductViewOptionValue` fügt Details zu einem einfachen Produkt hinzu.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `id` | ID | Die ID eines Optionswerts. |
| `title` | Zeichenfolge | Der Anzeigename des Optionswerts. |
| `product` | SimpleProductView | Details zu einem einfachen Produkt. |

### ProductViewPrice-Typ

Die `ProductViewPrice` type bietet die Basisproduktpreisansicht, die für einfache Produkte inhärent ist.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `final` | Preis | Preiswert nach Rabatten, ohne personalisierte Promotions. |
| `regular` | Preis | Vom Händler angegebener Basisproduktpreis. |
| `roles` | [Zeichenfolge] | Bestimmt, ob der Preis sichtbar oder ausgeblendet sein soll. |

### ProductViewPriceRange-Typ

Die `ProductViewPriceRange` type listet den Mindest- und Höchstpreis eines komplexen Produkts auf.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `maximum` | ProductViewPrice | Höchstpreis. |
| `minimum` | ProductViewPrice | Mindestpreis. |

### SimpleProductView-Typ {#SimpleProductView-type}

Die `SimpleProductView` type steht für alle Produkttypen außer Bundle, konfigurierbar und Gruppe. Einfache Produktpreise enthalten keine Preisspannen. `SimpleProductView` implementiert `ProductView`.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Eine Liste der von Händlern definierten Attribute, die für die Storefront bestimmt sind. |
| `description` | Zeichenfolge | Die detaillierte Beschreibung des Produkts. |
| `id` | ID! | Die Produkt-ID, die als zusammengesetzter Schlüssel generiert und pro Gebietsschema eindeutig ist. |
| `images(roles: [String])` | [ProductViewImage] | Eine Liste der für das Produkt definierten Bilder. |
| `metaDescription` | Zeichenfolge | Eine kurze Übersicht über das Produkt für Suchergebnislisten. |
| `metaKeyword` | Zeichenfolge | Eine kommagetrennte Liste von Suchbegriffen, die nur für Suchmaschinen sichtbar sind. |
| `metaTitle` | Zeichenfolge | Eine Zeichenfolge, die in der Titelleiste und Registerkarte des Browsers sowie in den Suchergebnislisten angezeigt wird. |
| `name` | Zeichenfolge | Produktname. |
| `price` | ProductViewPrice | Basisproduktpreisansicht. |
| `shortDescription` | Zeichenfolge | Eine Zusammenfassung des Produkts. |
| `sku` | Zeichenfolge | Produkt-SKU. |
| `url` | Zeichenfolge | Kanonische URL des Produkts. |
