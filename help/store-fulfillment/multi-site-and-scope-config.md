---
title: Mehrere Konfigurationen von Website und Umfang
description: Konfigurieren Sie Lager und Bereitstellungsmethoden für mehrere Websites und Storebereiche.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Mehrere Konfigurationen von Website und Umfang

Sie können die [Anwendungsbereich](https://docs.magento.com/user-guide/configuration/scope.html) für einige Elemente, um mehrere Websites, Stores und Store-Ansichten aufzunehmen:

- [Verwalten von Lagern](https://docs.magento.com/user-guide/catalog/inventory-stock.html) pro Perimeter

- Verwalten [!DNL Delivery Methods] pro Perimeter

Sie können einem Website- oder Store-Bereich ein Lager zuweisen. Aktualisieren Sie dann die Store-Quellen, um verfügbare Bereitstellungsmethoden festzulegen (Startseite, Store-Abruf).

Nach erfolgreicher Aktualisierung der Konfiguration können die Speicherbereinigungsoptionen auf der Produktdetailseite (PDP) in der Adobe Commerce-Storefront nur für Produkte ausgewählt werden, die von einer Lagerquelle verfügbar sind, die die Speicherbereinigung ermöglicht.

## Einstellungen zur In-Store-Abholung verwalten

Aktivieren oder deaktivieren Sie die [!UICONTROL In-Store Pickup] Optionen für jede Website oder den Speicherbereich aus der [Konfigurationen für Bereitstellungsmethoden](enable-general.md#delivery-methods) im Admin.

1. Navigieren Sie zu **[!UICONTROL Stores > Configuration]**.

1. Wählen Sie den zu konfigurierenden Perimeter (Website zu Store) aus.

1. Navigieren Sie mit ausgewähltem Bereich zu **[!UICONTROL Sales > Delivery Methods]**.

1. Deaktivieren oder aktivieren Sie die **[!UICONTROL In-Store Pickup]** Versandmethode.

In diesem Abschnitt können Sie auch verwalten, ob die Cursor- oder In-Store-Abholung global verfügbar ist.

Verwalten Sie die [!UICONTROL In-Store Pickup] und [!UICONTROL Delivery Method] Einstellungen pro Lagerbestand. Es gibt zahlreiche weitere Konfigurationen, um die volle Flexibilität Ihrer Implementierung zu gewährleisten.