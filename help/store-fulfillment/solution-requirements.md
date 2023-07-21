---
title: Anforderungen an die Store-Erfüllung
description: Anforderungen an die Bereitstellung und das Onboarding der [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Anforderungen an die Store-Erfüllung für Adobe Commerce

In den folgenden Abschnitten werden die technischen und geschäftlichen Anforderungen für die Installation und Aktivierung der Store Fulfillment-Lösung für Adobe Commerce beschrieben.

## Anforderungen an die Plattform- und Softwareversion

Die [!DNL Store Fulfillment] -Lösung ist für Adobe Commerce-Kunden auf den folgenden Plattformen verfügbar.

- Adobe Commerce über Cloud-Infrastruktur (ECE)
- Adobe Commerce vor Ort (EE)

Die Store Fulfillment-Lösung ist mit den Softwareversionen kompatibel, die im Abschnitt *Softwarekompatibilität* Tabelle.

**Softwarekompatibilität**

| **Software** | **Mindestversion** | **Maximale Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Verfasser | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Detaillierte Anforderungen finden Sie unter Adobe Commerce . [Systemanforderungen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) im *Adobe Commerce-Installationsanleitung*.

## Anforderungen an Store Assist-Apps

Der End-to-End-Prozess zur Verwaltung von Store-Abruf-Bestellungen wird über die Store-Hilfe-App verwaltet, die auf Mobilgeräten installiert ist. Diese Geräte, die vom Einzelhändler oder von den Verkaufsmitarbeitern mit ihren persönlichen Smartphones bereitgestellt werden, müssen die folgenden Anforderungen erfüllen:

**Mindestanforderungen an das Betriebssystem**

- Android 6
- iOS 12

**Mindestanforderungen an die Hardware**

- 1 GB RAM
- 600 MB freier Speicherplatz

## Geschäftsanforderungen

Ihr Unternehmen muss die folgenden Mindestkriterien erfüllen, um die Store Fulfillment-Lösung zu implementieren:

- Nur in den USA ansässige Unternehmen

- B2C-Händler (Business to Consumer), Consumer Packaged Goods (CPG) Hersteller, die direkt an Verbraucher verkaufen (D2C), oder Vertriebsgesellschaften, die direkt an Verbraucher oder kleine Unternehmen verkaufen

- Mindestens ein physisches Lager oder Lager

- Verwalten des Produktbestands mit Inventory management für Adobe Commerce (auch MSI genannt)

- Möglichkeit zur Konsortimentierung des Händlerinventars

- Die WLAN-Verfügbarkeit wird an allen Standorten gespeichert, die die Store Fulfillment-Lösung unterstützen: Internet-Geschwindigkeit von 3 MBit/s

- Store- und Warehouse-Mitarbeiter haben während ihres Verlags Zugriff auf Mobilgeräte mit iOS oder Android, die entweder persönlich oder vom Händler bereitgestellt werden

- Produkte, die mit der Store Fulfillment-Lösung verwaltet werden, müssen über Produktattribute verfügen, die entweder einen SKU- oder einen UPC-Produktcode enthalten
