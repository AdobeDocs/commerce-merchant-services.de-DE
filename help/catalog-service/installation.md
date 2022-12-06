---
title: Onboarding und Installation
description: Erfahren Sie, wie Sie installieren [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: fd1c6c385efb2f0e632f74959e75b3b7240b7ada
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Onboarding und Installation

## Voraussetzungen

Onboarding-Prozess für [!DNL Catalog Service] erfordert Zugriff auf die Befehlszeile des Servers. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

### Softwareanforderungen

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Verfasser: 2.x, 1.x

### Unterstützte Plattformen

- Adobe Commerce über Cloud-Infrastruktur: 2.4.x
- Adobe Commerce vor Ort: 2.4.x

## Installieren der Erweiterung

Sie können die [!DNL Catalog Service] Erweiterung für Adobe Commerce in Cloud-Infrastruktur und lokalen Instanzen.

Die [!DNL Catalog Service] wird mit Composer-Schlüsseln installiert, die mit dem Commerce-Konto verknüpft sind [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) im Anmeldeprozess bereitgestellt werden. Der Verfasser verwendet diese Schlüssel bei der ersten Installation von [!DNL Adobe Commerce]oder in Situationen, in denen die Composer-Schlüssel zuvor nicht im `auth.json` -Datei.

Siehe [Abrufen der Authentifizierungsschlüssel](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) für weitere Informationen zum Abrufen von Composer-Schlüsseln.

### Adobe Commerce auf Cloud-Infrastruktur

Verwenden Sie diese Methode, um die [!DNL Catalog Service] -Erweiterung für eine Commerce Cloud-Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` Datei in einem Texteditor speichern und aktualisieren `require` wie folgt:

   ```json
   "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1"
    }
   ```

1. Testen Sie die neue Konfiguration lokal und aktualisieren Sie Abhängigkeiten:

   ```bash
   composer update
   ```

   Der Befehl aktualisiert alle Abhängigkeiten.

1. Übernehmen Sie Ihre Änderungen und übertragen Sie sie für `composer.json` und `composer.lock`.

### Vor Ort

Verwenden Sie diese Methode, um die [!DNL Catalog Service] Erweiterung für eine lokale Instanz.

1. Öffnen Sie die `<Commerce_root>/composer.json` Datei in einem Texteditor speichern und aktualisieren `require` wie folgt:

   ```json
   "require": {
    "magento/module-saas-catalog": "^101.4.0",
    "magento/module-saas-product-override": "^101.4.0",
    "magento/module-saas-product-variant": "^101.4.0",
    "magento/module-bundle-product-data-exporter": "^101.3.1",
    "magento/module-catalog-data-exporter": "^101.3.1",
    "magento/module-catalog-inventory-data-exporter": "^101.3.1",
    "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
    "magento/module-configurable-product-data-exporter": "^101.3.1",
    "magento/module-data-exporter": "^101.3.1",
    "magento/module-parent-product-data-exporter": "^101.3.1",
    "magento/module-product-override-data-exporter": "^101.3.1",
    "magento/data-services": "^7.0.11",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
   }
   ```

1. Aktualisieren Sie die Abhängigkeiten und installieren Sie die Erweiterung:

   ```bash
   composer update
   ```

   Der Befehl aktualisiert alle Abhängigkeiten.

1. Upgrade von Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache:

   ```bash
   bin/magento cache:clean
   ```

## Konfigurieren des Katalogexports

Nach der Installation [!DNL Catalog Service], müssen Sie die [Commerce Services Connector](../landing/saas.md) durch Angabe von API-Schlüsseln und Auswahl eines SaaS-Datenspeichers.

So stellen Sie sicher, dass der Katalogexport ordnungsgemäß ausgeführt wird:

- Vergewissern Sie sich, dass [Cron-Aufträge](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) laufen.
- Überprüfen Sie die [Indexer](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) laufen.
- Stellen Sie sicher, dass `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`und `Product Variant Feed` Indexer werden auf `Update by Schedule`.

## Catalog Service und API-Mesh

Die [API-Mesh für Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) ermöglicht es Entwicklern, mithilfe von Adobe IO private oder Drittanbieter-APIs und andere Schnittstellen mit Adobe-Produkten zu integrieren.

Der erste Schritt zur Verwendung des API-Meshs mit dem Catalog Service besteht darin, API-Mesh mit Ihrer Instanz zu verbinden. Detaillierte Anweisungen finden Sie unter [Erstellen eines Gitters](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Um das Setup abzuschließen, benötigen Sie die [Adobe IO CLI-Paket](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installiert.

Nachdem der Mesh auf Adobe I/O konfiguriert wurde, führen Sie den folgenden Befehl aus, der einen `CommerceCatalogServiceGraph` zu Ihrem Gitter.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` ist eine separate Datei, in der häufig verwendete Werte für Adobe IO gespeichert werden.
Beispielsweise kann der API-Schlüssel in der Datei gespeichert werden:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Nach Ausführung dieses Befehls sollte der Catalog Service über das API-Mesh ausgeführt werden. Sie können die `aio api-mesh:get` -Befehl, um die Konfiguration Ihres aktualisierten Netzwerks anzuzeigen.

## [!DNL Catalog Service] Demo

In diesem Video erfahren Sie mehr über [!DNL Catalog Service] Installation und Prüfung:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
