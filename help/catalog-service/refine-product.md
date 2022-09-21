---
title: refineProduct query
description: '"Ein Referenzhandbuch für die GraphQL-Abfrage "refineProduct"für den Adobe Commerce-Katalogdienst."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# refineProduct query

Die `refineProduct` Abfrage schränkt die Ergebnisse eines `products` Abfrage, die mit einem komplexen Produkt ausgeführt wurde. Vor dem Ausführen der `refineProduct` -Abfrage ausführen, müssen Sie die `products` abfragen und die Antwort so erstellen, dass sie eine Liste von `options` innerhalb einer `ComplexProductView` Inline-Fragment. Wenn ein Käufer eine Produktoption (z. B. Größe oder Farbe) auf der Storefront auswählt, führen Sie die `refineProduct` Abfrage, wobei die SKU und die IDs der ausgewählten Optionswerte als Eingabe angegeben werden. Abhängig von der Anzahl der Produktoptionen, die das komplexe Produkt bietet, müssen Sie möglicherweise die `refineProduct` mehrmals abfragen, bis der Käufer eine bestimmte Variante ausgewählt hat.

Sie sollten die Antwort Ihrer Abfrage so erstellen, dass sie beide `ComplexProductView` und `SimpleProductView` Inline-Fragmente. Wenn der Käufer nicht alle erforderlichen Optionen ausgewählt hat, gibt die Abfrage die IDs der nicht ausgewählten Optionen sowie den Mindest- und Höchstpreis des Produkts zurück, basierend auf den ausgewählten Optionen und möglichen verbleibenden Optionen. Wenn der Käufer alle erforderlichen Optionen ausgewählt hat, gibt die Abfrage Details zu einem einfachen Produkt zurück, das einen festgelegten Preis enthält.

## Syntax

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
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

### Details zu einem teilweise ausgewählten komplexen Produkt zurückgeben

Die folgende Abfrage gibt Details zu den verfügbaren Farboptionen für eine mittlere Produktvariante zurück `MH12`. Der Wert der `optionIDs` Eingabeparameter wird aus dem `products` Abfrage [Details zu einem komplexen Produkt zurückgeben](products.md#complex-product-example) Beispiel.

**Anfrage:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Details zu einem vollständig ausgewählten komplexen Produkt zurückgeben

In der folgenden Abfrage hat der Käufer Optionen für Größe und Farbe ausgewählt. Die Antwort enthält Details zum entsprechenden einfachen Produkt.

**Anfrage:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Eingabefelder

Sie müssen einen SKU-Wert und mindestens eine Option-ID als Eingabe angeben.

| Feld | Datentyp | Beschreibung |
|--- | --- | ---|
| `optionIds` | [String!]! | Eine Liste der IDs, die den vom Käufer ausgewählten Produktoptionen zugewiesen sind, z. B. Farben und Größen. |
| `sku` | String! | Die SKU eines komplexen Produkts. |

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
