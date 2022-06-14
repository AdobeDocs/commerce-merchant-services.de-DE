---
title: Inventory management Source Transfer
description: Konfigurieren Sie Lager für die Store-Erfüllung, indem Sie ein neues Lager einrichten und das Inventar aus dem Standardbestand übertragen.
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Inventory management Source Transfer

Die [!DNL Store Fulfillment] -Lösung verwendet die native Adobe Commerce Inventory management. Standardmäßig wird die [!DNL Commerce] -Konfiguration weist das gesamte Webinventar dem Standardbestand zu, dem keine zusätzlichen Quellen zugewiesen werden können. Da einer Website nur ein einzelnes Lager zugewiesen werden kann, muss ein Händler ein neues Lager konfigurieren und optional seinen Standardquellbestand an eine Quelle übertragen, die dem entsprechenden Umfang zugeordnet ist. Anschließend kann die Quelle dem neuen Lager zugewiesen werden.

Mit diesen Konfigurationsänderungen können Sie drei Dinge erreichen:

1. [Inventar an Quelle übertragen](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) , um den Bestand aus dem Standardbestand/der Standardquelle in den neuen Bestand/die neue Quelle zu verschieben.

2. [Massenzuweisungen von Quellen](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) , um die neuen Quellen für alle Ihre Produkte hinzuzufügen.

3. [Vollständige Massenaktualisierungen für Produktattribute](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) , um `Allow Store Pickup` und `Allow Home Delivery` -Attributen vorhandenen Produkten zuordnen. Wenn die Lösung installiert ist, haben die Attribute die optimale *default* -Werte. Diese Attribute werden jedoch erst dann auf vorhandene Produkte angewendet, wenn Sie die Massenaktualisierungen abgeschlossen haben.

Der Bestand wird von der ausgewählten Quelle abgezogen (Einzelhandelsspeicherort oder E-Commerce-Warehouse). Als E-Commerce-Lager verwendete Quellen müssen demselben Lager wie der Speicherort für die Ladung zugeordnet und vor den Einzelhandelsstandorten priorisiert werden. Weitere Informationen finden Sie unter [Priorisieren von Quellen für einen Bestand](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).


Weitere Informationen zum Verwalten von Beständen, Lagern und Quellen finden Sie in der Adobe Commerce-Benutzerdokumentation:

- [Verwalten des Bestands](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Verwalten von Lagerbestandsmengen](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Verwalten von Lagern](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Verwalten von Quellen](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorisieren von Quellen für einen Bestand](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Massenaktualisierungen für Produktattribute](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Eine Änderung der Konfiguration für Inventar- und Lagerquellen kann sich auch nachgelagert auf integrierte Systeme auswirken. Stellen Sie sicher, dass Sie verstehen, wie sich die Änderungen an der Lagerbestandskonfiguration auf diese Systeme auswirken.
