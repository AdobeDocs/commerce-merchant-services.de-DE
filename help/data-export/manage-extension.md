---
title: "[!DNL Manage the Data Export extension]"
description: "Erfahren Sie, wie Sie die [!DNL Data Export] und um nicht erforderliche Datenexportdienste zu entfernen oder zu deaktivieren."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Verwalten der SaaS-Datenexport-Erweiterung

Die [!DNL data export] Erweiterung für SaaS-Dienste ist eine Sammlung von Modulen, die die Datenerfassung und Synchronisation zwischen Adobe Commerce und verbundenen Commerce-Diensten ermöglichen.

In den Metapaketen für Adobe Commerce Services-Erweiterungen sind spezifische Module enthalten, z. B. [Live Search](/help/live-search/overview.md), [Produkt-Recommendations](/help/product-recommendations/overview.md), und [Catalog Service](/help/catalog-service/overview.md). Wenn Sie diese Dienste verwenden, ist keine separate Installation erforderlich, um die Datenexport-Erweiterung zu aktivieren.

## Commerce-Datenexportfunktionen entfernen oder deaktivieren

Wenn Sie keines der installierten Commerce-Datenexport-Module benötigen, verwenden Sie die `magento:module:disable` CLI-Befehl zum Deaktivieren.

Beispielsweise gibt es eine [Kategorien-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) , das die Feed-Daten der Kategorieberechtigungen intern verwendet. Wenn Sie diese API nicht verwenden, können Sie den Datenexport für den Berechtigungs-Feed der Kategorien deaktivieren.

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

Wenn die Commerce-Instanz in der Cloud-Infrastruktur bereitgestellt wird, aktualisieren Sie die Erweiterung aus Ihrem Cloud-Projektverzeichnis. Siehe [Aktualisierung einer Erweiterung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) im _Handbuch zu Adobe Commerce on Cloud Infrastructure_.




