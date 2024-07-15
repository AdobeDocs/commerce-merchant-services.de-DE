---
title: Verfügbare Daten
description: Verwenden Sie Reporting-Daten zur Abstimmung von Berichten mit Nicht-Commerce-Systemen.
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
feature: Payments, Checkout, Data Import/Export
source-git-commit: 9a933d41bffc2af453eed00caeb941eb18b23852
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verfügbare Daten

Einige Daten zu Bestellungen und Auszahlungen stehen Ihnen zur Verfügung, damit Sie die Adobe Commerce-Finanzberichterstattung über externe Systeme hinweg koordinieren können.

## Mit ERP-System abstimmen

Sie können Adobe Commerce-Finanzberichte mit Ihrem ERP-System (Enterprise Resource Planning) abstimmen, das keine Adobe ist, indem Sie die Inkrement-ID verwenden, die einer bestimmten Bestellung zugeordnet ist.

Wenn Zahlungsdienste die Commerce-Bestellung an PayPal senden, wird die Inkrement-ID als `custom_id` _und_ in den `invoice_id` (die ebenfalls eine zufällige Zeichenfolge nach dem `increment_id` enthält) einbezogen.

Auf die IDs kann sowohl in den Details der Handelsaktivität für eine Auszahlung als auch im PayPal-Webhook zugegriffen werden.

Die `invoice_id` und `custom_id` werden für eine Auszahlung unten in den Details der Handelsaktivität angezeigt:

![`custom_id` im Detail der Handelsaktivität](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` und `invoice_id` in den Details im Webhook von PayPal:

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

* [`purchase_unit`, in dem sich `custom_id` und `invoice_id` befinden](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit)
* [Bestelldetails anzeigen](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
