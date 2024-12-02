---
title: Inventory management Source Transfer
description: Konfigurieren von Lagern für die  [!DNL Store Fulfillment solution]  mit Adobe Commerce Inventory management. Richten Sie ein neues Lager ein und übertragen Sie das Inventar aus dem Standardbestand, damit Sie es Quellen zuweisen können, die so konfiguriert sind, dass die für die Store Fulfillment-Lösung erforderlichen Speicherabnahmefunktionen aktiviert werden.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Source Transfer

Die [!DNL Store Fulfillment] -Lösung verwendet den nativen Adobe Commerce Inventory management. Standardmäßig weist die Konfiguration &quot;[!DNL Commerce]&quot; das gesamte Webinventar dem Standardbestand zu, dem keine zusätzlichen Quellen zugewiesen werden können. Da einer Website nur ein einzelnes Lager zugewiesen werden kann, muss ein Händler ein neues Lager konfigurieren und optional seinen Standardquellbestand an eine Quelle übertragen, die dem entsprechenden Umfang zugeordnet ist. Anschließend kann die Quelle dem neuen Lager zugewiesen werden.

>[!IMPORTANT]
>
>Händler müssen die Standardquelle für alle Produkte beibehalten, die in Gruppen- und Bundle-Produktarten enthalten sind. Diese Produkte benötigen eine Lagerbestandsmenge, die den Mindestmengenschwellenwert für die Lagerpositionen erfüllt und den Lagerstatus von [!UICONTROL In Stock] aufweist.

Mit diesen Konfigurationsänderungen können Sie drei Dinge erreichen:

1. [Übertragen des Bestands an die Quelle](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/inventory-transfer) , um den Bestand aus dem Standardbestand/der Standardquelle in den neuen Bestand/die neue Quelle zu verschieben.

1. [Zuweisen von Massenquellen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/bulk-assignment) zum Hinzufügen der neuen Quellen für alle Produkte.

1. [Umfassende Massenaktualisierungen für Produktattribute](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update) , um die Attribute `Allow Store Pickup` und `Allow Home Delivery` zu vorhandenen Produkten hinzuzufügen. Wenn die Lösung installiert ist, verfügen die Attribute über die optimalen Werte für *Standard*. Diese Attribute werden jedoch erst auf vorhandene Produkte angewendet, wenn Sie den Bulk-Prozess &quot;updaContes&quot;abgeschlossen haben.

Der Bestand wird von der ausgewählten Quelle abgezogen (Einzelhandelsspeicherort oder E-Commerce-Warehouse). Als E-Commerce-Lager verwendete Quellen müssen demselben Lager wie der Speicherort für die Ladung zugeordnet und vor den Einzelhandelsstandorten priorisiert werden. Weitere Informationen finden Sie unter [Priorisieren von Quellen für einen Stock](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources).

Weitere Informationen zum Verwalten von Beständen, Lagern und Quellen finden Sie in der Adobe Commerce-Benutzerdokumentation:

- [Verwalten des Bestands](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)

- [Verwalten der Lagerbestandsmengen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/quantities-manage)

- [Verwalten von Lagern](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)

- [Verwalten von Quellen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage)

- [Priorisieren von Quellen für einen Bestand](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources)

- [Massenaktualisierungen für Produktattribute](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update)


>[!IMPORTANT]
>
>Eine Änderung der Konfiguration für Inventar- und Lagerquellen kann sich auch nachgelagert auf integrierte Systeme auswirken. Stellen Sie sicher, dass Sie verstehen, wie sich die Änderungen an der Lagerbestandskonfiguration auf diese Systeme auswirken.
