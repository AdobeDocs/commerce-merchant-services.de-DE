---
title: '[!DNL Manage the Data Export extension]'
description: Erfahren Sie, wie Sie die Erweiterung [!DNL Data Export] aktualisieren und nicht erforderliche Datenexportdienste entfernen oder deaktivieren.
role: Admin, Developer
exl-id: d2326673-0f82-4266-bf56-74d55e32fcab
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Verwalten der SaaS-Datenexport-Erweiterung

Die Erweiterung [!DNL data export] für SaaS-Dienste ist eine Sammlung von Modulen, die die Datenerfassung und Synchronisierung zwischen Adobe Commerce und verbundenen Commerce-Diensten ermöglichen.

In den Metapaketen für Adobe Commerce Services-Erweiterungen sind spezifische Module enthalten, z. B.
als [Live Search](/help/live-search/overview.md), [Product Recommendations](/help/product-recommendations/overview.md) und [Catalog Service](/help/catalog-service/overview.md). Wenn Sie diese Dienste verwenden, ist keine separate Installation erforderlich, um die Datenexport-Erweiterung zu aktivieren.

## Commerce-Datenexportfunktionen entfernen oder deaktivieren

Wenn Sie eines der installierten Commerce-Datenexport-Module nicht benötigen, verwenden Sie den CLI-Befehl `magento:module:disable` , um es zu deaktivieren.

Beispielsweise gibt es eine [Kategorien-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/), die die Feed-Daten für Kategorieberechtigungen intern verwendet. Wenn Sie diese API nicht verwenden, können Sie den Datenexport für den Berechtigungs-Feed der Kategorien deaktivieren.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Aktualisieren eines Moduls auf eine bestimmte Version

Sie können jedes der installierten Commerce-Datenexport-Module mithilfe von Composer aktualisieren. Sie können beispielsweise ein Modul auf eine angegebene Version aktualisieren und auch alle erforderlichen Abhängigkeiten aktualisieren.

1. Melden Sie sich beim Commerce-Anwendungsserver an.

1. Aktualisieren Sie in der Befehlszeile das Modul mit Composer:

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Wenn die Commerce-Instanz in der Cloud-Infrastruktur bereitgestellt wird, aktualisieren Sie die Erweiterung aus Ihrem Cloud-Projektverzeichnis. Siehe [Aktualisieren einer Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) im _Adobe Commerce on Cloud Infrastructure Guide_.
