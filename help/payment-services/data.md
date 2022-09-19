---
title: Verfügbare Daten
description: Verwenden Sie Reporting-Daten zur Abstimmung von Berichten mit Nicht-Commerce-Systemen.
role: User
level: Intermediate
source-git-commit: ed471f363546f1d337e85568dc5079cae4507840
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Verfügbare Daten

Einige Daten zu Bestellungen und Auszahlungen stehen Ihnen zur Verfügung, damit Sie die Adobe Commerce-Finanzberichterstattung über externe Systeme hinweg koordinieren können.

## Mit ERP-System abstimmen

Sie können Adobe Commerce-Finanzberichte mit Ihrem Enterprise Resource Planning (ERP)-System abstimmen, das keine Adobe ist, indem Sie die Inkrement-ID verwenden, die einer bestimmten Bestellung zugeordnet ist.

Wenn Zahlungsdienste die Commerce-Bestellung an PayPal sendet, wird die Inkrement-ID als `custom_id` _und_ im `invoice_id` (die auch eine zufällige Zeichenfolge nach der `increment_id`).

Auf die IDs kann sowohl in den Details der Handelsaktivität für eine Auszahlung als auch im PayPal-Webhook zugegriffen werden.

Die `invoice_id` und `custom_id` werden unten in den Details der Händleraktivität für eine Auszahlung angezeigt:

![`custom_id` im Detail der Handelsaktivität](assets/merchant-activity-ids.png)

`custom_id` und `invoice_id` im Webhook von PayPal:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Weitere Informationen finden Sie in der Dokumentation zu den REST-APIs von PayPal:

* [`purchase_unit`, bei denen `custom_id` und `invoice_id` aufbewahren](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
* [Bestelldetails anzeigen](https://developer.paypal.com/docs/api/orders/v2/#orders_get)