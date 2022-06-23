---
title: Anforderungen an die Store-Erfüllung
description: Anforderungen an die Bereitstellung und das Onboarding der [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 2%

---

# Anforderungen an die Store-Erfüllung für Adobe Commerce

Sie müssen die folgenden technischen und geschäftlichen Anforderungen erfüllen, um die Store Fulfillment-Lösung für Adobe Commerce zu installieren und zu aktivieren.

## Anforderungen an die Plattform- und Softwareversion

Die [!DNL Store Fulfillment] -Lösung ist für Adobe Commerce-Kunden auf den folgenden Plattformen verfügbar.

- Adobe Commerce über Cloud-Infrastruktur (ECE)
- Adobe Commerce vor Ort (EE)

Die Store Fulfillment-Lösung ist mit den folgenden Softwareversionen kompatibel.

**Softwarekompatibilität**

| **Software** | **Mindestversion** | **Maximale Version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2,4,0 | 2,4,4 |
| Verfasser | 1.x | 2.x |
| MariaDB | Artikel 10 Absatz 2 | Artikel 10 Absatz 4 |
| MySQL | 5,7 | 8,0 |
| PHP | 7,4 | 8,1 |

Detaillierte Anforderungen finden Sie unter Adobe Commerce . [Systemanforderungen](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) in der Entwicklerdokumentation.

## Anforderungen an Store Assist-Apps

Der End-to-End-Prozess zur Verwaltung von Store-Abruf-Bestellungen wird über die Store-Hilfe-App verwaltet, die auf Mobilgeräten installiert ist. Diese Geräte, die vom Einzelhändler oder von den Verkaufsmitarbeitern mit ihren persönlichen Smartphones bereitgestellt werden, müssen die folgenden Anforderungen erfüllen:

**Mindestanforderungen an das Betriebssystem**

- Android 6
- iOS 12

**Mindestanforderungen an die Hardware**

- 1 GB RAM
- 600 MB freier Speicherplatz

## Geschäftsanforderungen

Ihr Unternehmen muss die folgenden Mindestkriterien erfüllen, um die Store Fulfillment-Lösung zu implementieren.

- Nur in den USA ansässige Unternehmen

- B2C-Einzelhändler, CPG-Hersteller, die D2C verkaufen, oder Vertriebsgesellschaften, die D2C oder kleine Unternehmen verkaufen

- Mindestens ein physisches Lager oder Lager

- Verwalten des Produktbestands mit Inventory management für Adobe Commerce (auch MSI genannt)

- Möglichkeit zur Konsortimentierung des Händlerinventars

- Die WLAN-Verfügbarkeit wird an allen Standorten gespeichert, die die Store Fulfillment-Lösung unterstützen: Internet-Geschwindigkeit von 3 MBit/s

- Store- und Warehouse-Mitarbeiter haben während ihres Verlags Zugriff auf Mobilgeräte mit iOS oder Android, die entweder persönlich oder vom Händler bereitgestellt werden

- Produkte, die mit der Store Fulfillment-Lösung verwaltet werden, müssen über Produktattribute verfügen, die entweder einen SKU- oder einen UPC-Produktcode enthalten
