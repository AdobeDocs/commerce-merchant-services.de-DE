---
title: Inventory management Source Transfer
description: "Konfigurieren von Lagern für die  [!DNL Store Fulfillment solution]  mit Adobe Commerce Inventory management. Richten Sie ein neues Lager ein und übertragen Sie das Inventar aus dem Standardbestand, damit Sie es Quellen zuweisen können, die so konfiguriert sind, dass die für die Store-Fulfillment-Lösung erforderlichen Speicherabnahmefunktionen aktiviert werden."
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
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

1. [Übertragen des Bestands an die Quelle](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) , um den Bestand aus dem Standardbestand/der Standardquelle in den neuen Bestand/die neue Quelle zu verschieben.

1. [Zuweisen von Massenquellen](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) zum Hinzufügen der neuen Quellen für alle Produkte.

1. [Umfassende Massenaktualisierungen für Produktattribute](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) , um die Attribute `Allow Store Pickup` und `Allow Home Delivery` zu vorhandenen Produkten hinzuzufügen. Wenn die Lösung installiert ist, verfügen die Attribute über die optimalen Werte für *Standard*. Diese Attribute werden jedoch erst auf vorhandene Produkte angewendet, wenn Sie den Bulk-Prozess &quot;updaContes&quot;abgeschlossen haben.

Der Bestand wird von der ausgewählten Quelle abgezogen (Einzelhandelsspeicherort oder E-Commerce-Warehouse). Als E-Commerce-Lager verwendete Quellen müssen demselben Lager wie der Speicherort für die Ladung zugeordnet und vor den Einzelhandelsstandorten priorisiert werden. Weitere Informationen finden Sie unter [Priorisieren von Quellen für einen Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Weitere Informationen zum Verwalten von Beständen, Lagern und Quellen finden Sie in der Adobe Commerce-Benutzerdokumentation:

- [Verwalten des Bestands](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Verwalten der Lagerbestandsmengen](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Verwalten von Lagern](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Verwalten von Quellen](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorisieren von Quellen für einen Bestand](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Massenaktualisierungen für Produktattribute](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Eine Änderung der Konfiguration für Inventar- und Lagerquellen kann sich auch nachgelagert auf integrierte Systeme auswirken. Stellen Sie sicher, dass Sie verstehen, wie sich die Änderungen an der Lagerbestandskonfiguration auf diese Systeme auswirken.
