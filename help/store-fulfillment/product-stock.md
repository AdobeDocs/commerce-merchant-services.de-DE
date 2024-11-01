---
title: Verwaltung von Produktbeständen
description: Konfigurieren Sie die für Kunden verfügbaren Merchant Stock Messaging und Funktionen.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Verwaltung von Produktbeständen

Als Händler können Sie die Lager- und Quelloptionen von Adobe Commerce [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) verwenden. Sie können auch die Lösung Store Fulfillment verwenden, um andere Lagerverfügbarkeitsoptionen im Zusammenhang mit Ihren Händlerstapeln zu steuern.

- Option für den Home-Versand in den Merchant Stores

- Zulassen/Verfügbar für Store-Abruf

- UPC/SKU/Andere eindeutige Produkt-IDs

- Nicht vorrätiger Schwellenwert

- Dekrementieren des Bestands von bestimmten Positionen nach Bestellung

Konfigurieren Sie die Optionen für den Produktbestand über den Administrator: **[!UICONTROL Catalog > Products > Select Product]**

## **Optionen für Produktspeicher**

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Verfügbar für die Home-Bereitstellung** | <p>Legt die Verfügbarkeit der Home Delivery (Ship-from-Store) für das Produkt fest. Wenn diese Option aktiviert ist, gelten alle zugewiesenen Händlerstätten mit verfügbarem Inventar für das Produkt als für die Option &quot;Home Delivery&quot;geeignet. Wenn diese Option deaktiviert ist, ist das Produkt nie für den Heimversand qualifiziert.</p>Normalerweise reicht es aus, diese Option auf der Ebene des Händlers festzulegen. Es kann jedoch individuelle Fälle für bestimmte Produkte geben, z. B. für Produkte, die unter Bundesversandbeschränkungen fallen und die nicht für den Heimversand infrage kommen.</p> | Webseite | Nein |
| **[!UICONTROL Available for Store Pickup]** | <p>Legen Sie die Verfügbarkeit der Store-Abholung für das Produkt fest. Wenn diese Option aktiviert ist, gelten alle zugewiesenen Händler-Store-Standorte mit verfügbarem Inventar für das Produkt als für die Option &quot;Store Pickup&quot;geeignet. Wenn diese Option deaktiviert ist, ist das Produkt nie für die Store-Abholung qualifiziert.</p><p>Diese Option kann nützlich sein, um Handelsbestand im System zu verfolgen, den Sie nicht über Ihren E-Commerce-Kanal verkaufen möchten.</p> | Webseite | Nein |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Dieses Attribut sollte als Produktattribut vorhanden sein und sich auf die Einstellung **[!UICONTROL Barcode Source / Barcode Type]** beziehen. Dieses Attribut wird verwendet, um einen scannbaren Barcode für Ihre Produkte zu verfolgen. Dieser Wert wird möglicherweise gesendet, wenn eine Bestellung zur Auswahl an Ihre Händler gesendet wird. Speicherverknüpfungen können den Wert mit der Auswahlliste verwenden, um Produkte auf der Ablage mit einem Barcode-Scanner abzugleichen. | Store-Ansicht | Nein |

{style="table-layout:auto"}

## Quellen für Inventare auf Produktebene

| **Feld** | **Beschreibung** | **Umfang** | **Erforderlich** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | <p>Legen Sie den Schwellenwert für das Lager für das Element in jeder Quelle fest. Fällt der Bestand unter den Schwellenwert, wird er an der Quelle als nicht vorrätig betrachtet.</p><p>Um die globale Speicherkonfigurationseinstellung zu verwenden, aktivieren Sie die Option **[!UICONTROL Use Default]** .</p> | Global | Nein |
| **[!UICONTROL Allow Store Pickup]** | <p>Legen Sie explizit fest, ob das Element für die Store-Erfassung verfügbar ist, unabhängig von der Konfiguration des Lagerbestands oder des Händlers.</p><p>Um die Einstellung auf Produktebene zu verwenden, deaktivieren Sie die Option [!UICONTROL Use Default] und treffen Sie Ihre Auswahl. Andernfalls wird diese Einstellung basierend auf der Konfiguration für **[!UICONTROL Allow In-Store Pickup]** ausgewählt, die in der Stock-Quelle festgelegt ist.</p> | Global | Nein |

{style="table-layout:auto"}

