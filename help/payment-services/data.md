---
title: Verfügbare Daten
description: Verwenden Sie Reporting-Daten zur Abstimmung von Berichten mit Nicht-Commerce-Systemen.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Verfügbare Daten

Einige Daten zu Bestellungen und Auszahlungen stehen Ihnen zur Verfügung, damit Sie die Adobe Commerce-Finanzberichterstattung über externe Systeme hinweg koordinieren können.

## Mit ERP-System abstimmen

Sie können Adobe Commerce-Finanzberichte mit Ihrem Enterprise Resource Planning (ERP)-System abstimmen, das keine Adobe ist, indem Sie die Inkrement-ID verwenden, die einer bestimmten Bestellung zugeordnet ist.

Wenn Zahlungsdienste die Commerce-Bestellung an PayPal sendet, wird die Inkrement-ID als `custom_id`. Die `custom_id` ist in den Details der Handelsaktivität für eine Auszahlung und im PayPal-Webhook sichtbar.

`custom_id` unten in den Details der Händleraktivität für eine Auszahlung:

![`custom_id` im Detail der Handelsaktivität](assets/merchant-activity.png)

`custom_id` im Webhook von PayPal:

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

Weitere Informationen finden Sie in der Dokumentation zu den REST-APIs von PayPal:

* [`purchase_unit` , `custom_id` resides](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
* [Bestelldetails anzeigen](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
