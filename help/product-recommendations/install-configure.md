---
title: Installieren und Konfigurieren
description: Erfahren Sie, wie Sie installieren, aktualisieren und deinstallieren [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: 09609fd0b5bd3da9e884115de001bc33832ad792
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# Installieren und Konfigurieren

Bereitstellen [!DNL Product Recommendations] müssen Sie das -Modul installieren und die [Commerce Services Connector](../landing/saas.md). Sobald Updates veröffentlicht sind, können Sie Ihre Installation einfach mit der neuesten Version aktualisieren.

- [Installieren](#install)
- [Konfigurieren](#configure)
- [Aktualisieren](#update)
- [Deinstallieren](#uninstall)

## Installieren [!DNL Product Recommendations] {#install}

Da die [!DNL Product Recommendations] -Modul ist ein eigenständiges Metapaket. Aktualisierungen werden häufiger veröffentlicht als Adobe Commerce. Um sicherzustellen, dass Sie über die neuesten Fehlerbehebungen und Funktionen verfügen, lesen Sie den Abschnitt [Versionshinweise](release-notes.md).

Installieren Sie die `magento/product-recommendations` -Modul mit Composer:

```bash
composer require magento/product-recommendations
```

### Unterstützung von Page Builder hinzufügen {#pbsupport}

[!DNL Product Recommendations] für Page Builder sind ein optionales Modul und wird separat installiert. Verwendung [!DNL Product Recommendations] Installieren Sie das -Modul mit Page Builder, indem Sie den folgenden Befehl ausführen:

```bash
composer require magento/module-page-builder-product-recommendations
```

Durch Aktivierung von [!DNL Product Recommendations] Im Seitenaufbau können Sie eine vorhandene, aktive [Empfehlungseinheit](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) zu allen Inhalten, die in Page Builder erstellt wurden, wie z. B. Seiten, Blöcken und dynamischen Bausteinen.

>[!NOTE]
>
>[!DNL Page Builder] Empfehlungseinheiten können nur für die standardmäßige Store-Ansicht erstellt werden.

### Hinzufügen des Empfehlungstyps für visuelle Ähnlichkeit {#vissimsupport}

Die _Visuelle Ähnlichkeit_ Mit dem Empfehlungstyp können Sie eine Empfehlungseinheit für Ihre Produktdetailseite bereitstellen, die Produkte anzeigt, die [visuell ähnlich](type.md#visualsim) zum angezeigten Produkt hinzu. Dieser Empfehlungstyp ist am nützlichsten, wenn Bilder und visuelle Aspekte der Produkte wichtige Teile des Einkaufserlebnisses sind. Installieren Sie die _Visuelle Ähnlichkeit_ Empfehlungstyp durch Ausführen des folgenden Befehls:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurieren [!DNL Product Recommendations] {#configure}

Nach der Installation `magento/product-recommendations` -Modul, müssen Sie die [Commerce Services Connector](https://docs.magento.com/user-guide/configuration/services/saas.html) durch Angabe von API-Schlüsseln und Auswahl eines SaaS-Datenspeichers.

Um sicherzustellen, dass der Katalogexport ordnungsgemäß ausgeführt wird, überprüfen Sie, ob die Variable [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) und [Indexer](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) ausgeführt werden und die `Product Feed` Indexer ist auf `Update by Schedule`.

Wenn Sie über API-Schlüssel erfolgreich eine Verknüpfung zu Commerce Services herstellen und den SaaS-Datenraum angeben, beginnt die Katalogsynchronisierung. Sie können dann [verify](verify.md) dass Verhaltensdaten an Ihre Storefront gesendet werden.

## Aktualisieren Sie Ihre [!DNL Product Recommendations] Installation {#update}

Wie alle Adobe Commerce [!DNL Product Recommendations] verwendet Composer für Installation und Aktualisierung. So aktualisieren Sie die `magento/product-recommendations` -Modul ausführen, führen Sie Folgendes aus:

```bash
composer update magento/product-recommendations --with-dependencies
```

Um auf eine Hauptversion zu aktualisieren, z. B. von 3.0 auf 4.0, müssen Sie den Stamm bearbeiten `composer.json` -Datei für Ihr Projekt. (Siehe [Versionshinweise](release-notes.md) für Informationen zur neuesten Version.) Lassen Sie uns beispielsweise den `composer.json` Datei und suchen Sie nach `magento/product-recommendations` -Modul:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Überspringen wir die Hauptversion von `3.0` nach `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Speichern Sie die `composer.json` Datei und führen Sie Folgendes aus:

```bash
composer update magento/product-recommendations --with-dependencies
```

>[!NOTE]
>
> In den Versionen 3.x.x von Product Recommendations benötigen Sie nur einen einzigen API-Schlüssel. In den Versionen 4.x.x und höher müssen Sie öffentliche und private API-Schlüssel für die Produktion sowie öffentliche und private Sandbox-API-Schlüssel bereitstellen. Wenn Sie nicht beide API-Schlüsselpaare bereitstellen, können Sie nicht in der Admin-Konsole auf die Funktion &quot;Product Recommendations&quot;zugreifen. Die Datenerfassung wird jedoch in Ihrer Storefront fortgesetzt und vorhandene Empfehlungen werden Ihren Käufern weiterhin angezeigt.

## Deinstallieren [!DNL Product Recommendations] {#uninstall}

Bei Bedarf können Sie [uninstall](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) das Modul &quot;Produktempfehlungen&quot;.
