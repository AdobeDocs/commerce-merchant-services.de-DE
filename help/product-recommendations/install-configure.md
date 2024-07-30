---
title: Installieren und Konfigurieren
description: Erfahren Sie, wie Sie [!DNL Product Recommendations] installieren, aktualisieren und deinstallieren.
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Installieren und Konfigurieren

Wenn Sie [!DNL Product Recommendations] in Ihrer Storefront und in Ihrem Admin bereitstellen, müssen Sie das Modul installieren und den [Commerce Services Connector](../landing/saas.md) konfigurieren. Sobald Updates veröffentlicht sind, können Sie die Installation einfach mit der neuesten Version aktualisieren.

- [Installieren](#install)
- [Konfigurieren](#configure)
- [Aktualisieren](#update)
- [Deinstallieren](#uninstall)

## Installieren Sie [!DNL Product Recommendations] {#install}

Da das [!DNL Product Recommendations] -Modul ein eigenständiges Metapaket ist, werden Aktualisierungen häufiger veröffentlicht als Adobe Commerce. Um sicherzustellen, dass Sie über die neuesten Fehlerbehebungen und Funktionen verfügen, lesen Sie die [Versionshinweise](release-notes.md).

Installieren Sie das Modul `magento/product-recommendations` mit Composer:

```bash
composer require magento/product-recommendations
```

### Unterstützung von Page Builder hinzufügen {#pbsupport}

[!DNL Product Recommendations] für Page Builder ist ein optionales Modul und separat installiert. Um [!DNL Product Recommendations] mit Page Builder zu verwenden, installieren Sie das Modul, indem Sie den folgenden Befehl ausführen:

```bash
composer require magento/module-page-builder-product-recommendations
```

Durch Aktivierung von &quot;[!DNL Product Recommendations]&quot;im Seitenaufbau können Sie allen Inhalten, die im Seitenaufbau erstellt wurden, eine vorhandene aktive [Empfehlungseinheit](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) hinzufügen, z. B. Seiten, Bausteine und dynamische Bausteine.

Weitere Anweisungen finden Sie unter [Verwenden von [!DNL Product Recommendations] mit Seitenaufbau-Inhalt](page-builder.md) .

### Hinzufügen des Empfehlungstyps für visuelle Ähnlichkeit {#vissimsupport}

Mit dem Empfehlungstyp _Visuelle Ähnlichkeit_ können Sie eine Empfehlungseinheit für Ihre Produktdetailseite bereitstellen, die Produkte anzeigt, die [visuell ähnlich](type.md#visualsim) wie das angezeigte Produkt sind. Dieser Empfehlungstyp ist am nützlichsten, wenn Bilder und visuelle Aspekte der Produkte wichtige Teile des Einkaufserlebnisses sind. Installieren Sie den Empfehlungstyp _Visuelle Ähnlichkeit_ , indem Sie den folgenden Befehl ausführen:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurieren von [!DNL Product Recommendations] {#configure}

1. Konfigurieren Sie nach der Installation des Moduls `magento/product-recommendations` den Connector für Commerce-Dienste ](../landing/saas.md), indem Sie API-Schlüssel angeben und einen SaaS-Datenspeicher auswählen.[

   Die Konfiguration dieser Verbindung ermöglicht die Datensynchronisation und Kommunikation zwischen der Commerce-Instanz, dem Catalog Service und anderen unterstützenden Diensten. Die Datensynchronisation wird von der [SAAS-Datenexport-Erweiterung](../data-export/overview.md) durchgeführt.

1. Um sicherzustellen, dass der Katalogexport ordnungsgemäß ausgeführt werden kann, stellen Sie sicher, dass die [cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)-Aufträge und die [Indexer](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) ausgeführt werden und der `Product Feed`-Indexer auf `Update by Schedule` eingestellt ist.

Nachdem Sie die Commerce-Anwendung erfolgreich mit Commerce Services verknüpft und den [SaaS-Datenspeicher](../landing/saas.md#saas-configuration) angegeben haben, beginnt die Katalogsynchronisierung. Anschließend können Sie [verifizieren](verify.md), dass Verhaltensdaten an Ihre Storefront gesendet werden.

## Überwachung und Fehlerbehebung bei der Datensynchronisation

Über den Commerce-Administrator können Sie den Synchronisierungsprozess mithilfe des [Daten-Management-Dashboards](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) überwachen. Verwenden Sie die [Commerce-CLI](../data-export/data-export-cli-commands.md#troubleshooting) und Protokolle, um den Prozess zu verwalten und Fehler zu beheben.

Anschließend können Sie [verifizieren](verify.md), dass Verhaltensdaten an Ihre Storefront gesendet werden.

## Aktualisieren der [!DNL Product Recommendations]-Installation {#update}

Wie alle Adobe Commerce verwendet [!DNL Product Recommendations] den Composer für die Installation und Aktualisierung. Um das Modul `magento/product-recommendations` zu aktualisieren, führen Sie Folgendes aus:

```bash
composer update magento/product-recommendations --with-dependencies
```

Um auf eine Hauptversion zu aktualisieren, z. B. von 3.0 auf 4.0, müssen Sie die Stammdatei `composer.json` für Ihr Projekt bearbeiten. (Informationen zur neuesten Version finden Sie in den [Versionshinweisen](release-notes.md) .) Öffnen wir beispielsweise die Hauptdatei `composer.json` und suchen Sie nach dem Modul `magento/product-recommendations`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Bringen wir die Hauptversion von `3.0` in `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Speichern Sie die Datei &quot;`composer.json`&quot; und führen Sie Folgendes aus:

```bash
composer update magento/product-recommendations --with-dependencies
```

Oder wenn Sie die Module `magento/module-visual-product-recommendations` und `magento/module-page-builder-product-recommendations` installiert haben:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> In den Versionen 3.x.x von Product Recommendations benötigen Sie nur einen einzigen API-Schlüssel. In den Versionen 4.x.x und höher müssen Sie öffentliche und private API-Schlüssel für die Sandbox- und Produktionsumgebungen bereitstellen. Wenn Sie nicht beide API-Schlüsselpaare bereitstellen, können Sie nicht in Admin auf die Funktion &quot;Product Recommendations&quot;zugreifen. Die Datenerfassung wird jedoch in Ihrer Storefront fortgesetzt und vorhandene Empfehlungen werden Ihren Kunden weiterhin angezeigt.

## Firewalls

Um Product Recommendations über eine Firewall zulassen, fügen Sie der Zulassungsliste `commerce.adobe.io` hinzu.

## Deinstallieren von [!DNL Product Recommendations] {#uninstall}

Bei Bedarf können Sie das Modul &quot;Produktempfehlungen&quot;[deinstallieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).
