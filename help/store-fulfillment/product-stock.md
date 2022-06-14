---
title: ProduktStock-Management
description: Konfigurieren Sie die für Kunden verfügbaren Merchant Stock Messaging und Funktionen.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Lagerverwaltung

Als Händler können Sie Adobe Commerce verwenden [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) Lager- und Quelloptionen. Darüber hinaus können Sie mit der Lösung Store Fulfillment andere Lagerverfügbarkeitsoptionen für Ihre Handelsgeschäfte steuern.

- Option für den Home-Versand in den Merchant Stores

- Zulassen/Verfügbar für Store-Abruf

- UPC/SKU/Andere eindeutige Produkt-IDs

- Nicht vorrätiger Schwellenwert

- Dekrementieren des Bestands von bestimmten Positionen nach Bestellung

Konfigurieren Sie die Optionen für den Produktbestand über den Administrator: **[!UICONTROL Catalog > Products > Select Product]**

## **Optionen für Produktspeicher**

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Verfügbar für den Home-Versand** | Legt die Verfügbarkeit der Home Delivery (Ship-from-Store) für das Produkt fest. Wenn diese Option aktiviert ist, gelten alle zugewiesenen Händlerstätten mit verfügbarem Inventar für das Produkt als für die Option &quot;Home Delivery&quot;geeignet. Wenn diese Option deaktiviert ist, kann das Produkt nicht für den Heimversand infrage kommen, selbst wenn ein Händler über einen Bestand verfügt.</br></br>In den meisten Fällen ist es ausreichend, diese Option auf der Ebene des Händlers festzulegen. Es kann jedoch individuelle Fälle für bestimmte Produkte geben, z. B. für Produkte, die unter Bundesversandbeschränkungen fallen und die nicht für den Heimversand infrage kommen. | Webseite | Nein |
| **[!UICONTROL Available for Store Pickup]** | Legen Sie die Verfügbarkeit der Store-Abholung für das Produkt fest. Wenn diese Option aktiviert ist, gelten alle zugewiesenen Händler-Store-Standorte mit verfügbarem Inventar für das Produkt als für die Option &quot;Store Pickup&quot;geeignet. Wenn diese Option deaktiviert ist, kann das Produkt nicht für die Store-Abholung verwendet werden, selbst wenn ein Händler über einen Bestand verfügt.</br></br>Diese Option kann für Fälle nützlich sein, in denen Sie den Händlerbestand im System verfolgen, aber nicht über Ihren E-Commerce-Kanal verkaufen möchten. | Webseite | Nein |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Dieses Attribut sollte bereits als Produktattribut vorhanden sein und sich auf die **[!UICONTROL Barcode Source / Barcode Type]** -Einstellung. Dieses Attribut wird verwendet, um einen scannbaren Barcode für Ihre Produkte zu verfolgen. Dieser Wert wird möglicherweise gesendet, wenn eine Bestellung zur Auswahl an Ihre Händler gesendet wird. Speicherverknüpfungen können den Wert mit der Auswahlliste verwenden, um Produkte auf der Ablage mit einem Barcode-Scanner abzugleichen. | Store-Ansicht | Nein |

{style=&quot;table-layout:auto&quot;}

## Quellen für Inventare auf Produktebene

| **Feld** | **Beschreibung** | **Anwendungsbereich** | **Erforderlich** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Legen Sie den Schwellenwert für das Lager für das Element in jeder Quelle fest. Fällt der Bestand unter den Schwellenwert, wird er an der Quelle als nicht vorrätig betrachtet.</br></br>Um die Einstellung für die globale Speicherkonfiguration zu verwenden, überprüfen Sie die **[!UICONTROL Use Default]** -Option. | Global | Nein |
| **[!UICONTROL Allow Store Pickup]** | Legen Sie explizit fest, ob das Element für die Store-Erfassung verfügbar ist, unabhängig von der Konfiguration des Lagerbestands oder des Händlers.</br></br> Um die Einstellung auf Produktebene zu verwenden, deaktivieren Sie die [!UICONTROL Use Default] und wählen Sie aus. Andernfalls wird diese Einstellung basierend auf der Konfiguration für **[!UICONTROL Allow In-Store Pickup]** , der auf die Lagerquelle festgelegt ist. | Global | Nein |

{style=&quot;table-layout:auto&quot;}

