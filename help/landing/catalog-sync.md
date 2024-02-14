---
title: Katalogsynchronisierung
description: Erfahren Sie, wie Sie Produktdaten aus der [!DNL Commerce] Server zu [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 748fb32913f9e7f0dea21f87be20386d9cc0ad17
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 0%

---


# Katalogsynchronisierung

Adobe Commerce verwendet Indexer, um Katalogdaten in Tabellen zu kompilieren. Der Prozess wird automatisch von [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) wie eine Änderung des Produktpreises oder des Lagerbestands.

Der Catalog Sync-Dienst verschiebt Produktdaten von einem [!DNL Adobe Commerce] -Instanz auf [!DNL Commerce Services] -Plattform auf dem neuesten Stand zu halten. Beispiel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) erfordert aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit exakt zurückzugeben. Verwenden Sie die _Katalogsynchronisierung_ Dashboard zur Beobachtung und Verwaltung des Synchronisierungsprozesses oder der [Befehlszeilenschnittstelle](#resynccmdline) zum Trigger einer Katalogsynchronisierung und zur Neuindizierung von Produktdaten für den Verbrauch durch [!DNL Commerce Services].

>[!NOTE]
>
> So verwenden Sie die _Katalogsynchronisierung_ -Dashboard oder der Befehlszeilenschnittstelle muss eine [API-Schlüssel und konfigurierter SaaS-Datenraum](saas.md).

## Zugriff auf das Dashboard &quot;Katalogsynchronisierung&quot;

>[!NOTE]
>
> Die _Katalogsynchronisierung_ Dashboard ist nur verfügbar, wenn die _Produkt-Recommendations_ -Module installiert sind und nur Datenprojektionen für diese Funktion widerspiegeln. Unterstützung für andere Commerce-Dienste wie _Live Search_ und _Catalog Service_ sind für die Zukunft geplant.

Um auf das Dashboard &quot;Katalogsynchronisierung&quot;zuzugreifen, wählen Sie **System** > _Datenübertragung_ > **Katalogsynchronisierung**.

Mit dem **Katalogsynchronisierung** Dashboard können Sie:

- Synchronisierungsstatus anzeigen (**In Bearbeitung**, **Erfolg**, **Fehlgeschlagen**)
- Gesamtanzahl der synchronisierten Produkte anzeigen
- Synchronisierte Produkte suchen, um ihren aktuellen Status anzuzeigen
- Suchspeicherkatalog nach Name, SKU usw.
- Anzeigen synchronisierter Produktdetails in JSON, um eine Synchronisierungsdiskrepanz zu diagnostizieren
- Initialisieren des Synchronisierungsprozesses

### Letzte Synchronisierung

Meldet einen Synchronisierungsstatus von:

- **Erfolg** - Zeigt Datum und Uhrzeit der erfolgreichen Synchronisierung und die Anzahl der aktualisierten Produkte an
- **Fehlgeschlagen** - Zeigt Datum und Uhrzeit des Synchronisierungsversuchs an
- **In Bearbeitung** - Zeigt Datum und Uhrzeit der letzten erfolgreichen Synchronisierung an

Der Vorgang zur Katalogsynchronisierung wird automatisch stündlich ausgeführt. Wenn die erwarteten Produkte nicht auf der Storefront angezeigt werden oder die Produkte die kürzlich vorgenommenen Änderungen nicht widerspiegeln, können Sie [Probleme bei der Katalogsynchronisierung](#resolvesync).

### Synchronisierte Produkte

Zeigt die Gesamtzahl der mit Ihrer [!DNL Commerce] Katalog. Nach der ersten Synchronisierung sollten nur geänderte Produkte synchronisiert werden.

## Neu synchronisieren {#resync}

Wenn Sie eine Neusynchronisierung Ihres Katalogs starten müssen, bevor die stündliche geplante Synchronisierung erfolgt, können Sie eine Neusynchronisierung erzwingen.

>[!NOTE]
>
> Erzwingen einer erneuten Synchronisierung von Triggern eine Neusynchronisierung des gesamten Produktkatalogs, was die Belastung der Hardware-Ressourcen erhöhen kann.

1. Aus dem _Katalogsynchronisierung_ Dashboard, auswählen **Einstellungen**.

   Die _Einstellungen zur Katalogsynchronisierung_ angezeigt.

1. Im _Daten neu synchronisieren_ Abschnitt, klicken Sie auf [!UICONTROL Resync].

   [!DNL Commerce] synchronisiert Ihren Katalog während des nächsten geplanten Synchronisierungsfensters. Je nach Größe Ihres Katalogs kann dieser Vorgang sehr lange dauern.

## Synchronisierte Katalogprodukte

Die **Synchronisierte Katalogprodukte** -Tabelle werden die folgenden Informationen angezeigt.

| Feld | Beschreibung |
|---|---|
| ID | Eindeutige Kennung des Produkts |
| Name | Storefront-Name des Produkts |
| Typ | Identifiziert den Produkttyp, z. B. einfach, konfigurierbar oder herunterladbar |
| Zuletzt exportiert | Datum, an dem das Produkt zuletzt erfolgreich aus Ihrem Katalog exportiert wurde |
| Zuletzt geändert | Datum der letzten Änderung des Produkts in Ihrem Katalog |
| SKU | Zeigt die Lagereinheit für das Produkt an |
| Preis | Preis der Ware |
| Sichtbarkeit | Die Sichtbarkeitseinstellung eines Produkts, wie in der Variablen [!DNL Commerce] Katalog |

## Beheben von Problemen bei der Katalogsynchronisierung {#resolvesync}

Wenn Sie eine erneute Synchronisierung von Daten Trigger haben, kann es bis zu eine Stunde dauern, bis die Daten aktualisiert werden und in UI-Komponenten wie Empfehlungseinheiten angezeigt werden. Wenn weiterhin Diskrepanzen zwischen Ihrem Katalog und den Daten in der Storefront auftreten oder die Katalogsynchronisierung fehlgeschlagen ist, lesen Sie Folgendes:

### Datendiskrepanz

1. Zeigen Sie die detaillierte Ansicht des betreffenden Produkts in den Suchergebnissen an.
1. Kopieren Sie die JSON-Ausgabe und stellen Sie sicher, dass der Inhalt mit dem übereinstimmt, den Sie im [!DNL Commerce] Katalog.
1. Wenn der Inhalt nicht übereinstimmt, nehmen Sie eine geringfügige Änderung am Produkt in Ihrem Katalog vor, z. B. das Hinzufügen eines Leerzeichens oder eines Zeitraums.
1. Warten Sie auf eine Neusynchronisierung oder [Trigger einer manuellen Neusynchronisierung](#resync).

### Synchronisierung wird nicht ausgeführt

Wenn die Synchronisierung nicht planmäßig ausgeführt wird oder nichts synchronisiert wird, lesen Sie dies [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) Artikel.

### Synchronisierung fehlgeschlagen

Wenn die Katalogsynchronisierung den Status **Fehlgeschlagen**, senden Sie eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Befehlszeilenschnittstelle {#resynccmdline}

Die `saas:resync` -Befehl ist Teil der `magento/saas-export` und ist standardmäßig mit einem der [!DNL Commerce Services] Produkte, wie [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) oder [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Führen Sie beim erstmaligen Ausführen einer Datensynchronisierung den `productattributes` Feed zuerst, gefolgt von `productoverrides`, bevor Sie die `products` Feed.

Befehlsoptionen:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

Die folgende Tabelle beschreibt die `saas:resync` Parameter und Beschreibungen.

| Parameter | Beschreibung | Erforderlich? |
|---| ---| ---|
| `feed` | Gibt an, welche Entität erneut synchronisiert werden soll, z. B. `products` | Ja |
| `no-reindex` | Sendet die vorhandenen Katalogdaten an [!DNL Commerce Services] ohne Neuindizierung. Wenn dieser Parameter nicht angegeben ist, führt der Befehl vor der Synchronisierung von Daten eine vollständige Neuindizierung durch. | Nein |
| `cleanup-feed` | Bereinigen Sie die Feed-Indexer-Tabelle vor einer Synchronisierung. | Nein |

Der Feed-Name kann einer der folgenden sein:

- `products`- Produkte in Ihrem Katalog
- `productattributes`- Produktattribute wie `activity`, `gender`, `tops`, `bottoms`, usw.
- `variants`— Produktvarianten eines konfigurierbaren Produkts wie Farbe und Größe
- `prices` — Produktpreise
- `scopesCustomerGroup` - Kundengruppen
- `scopesWebsite` — Websites mit Store-Ansichten
- `categories`— Kategorien in Ihrem Katalog
- `categoryPermissions` - Berechtigungen für jede Kategorie
- `productoverrides`— Kundenspezifische Preisbildungs- und Katalogsichtbarkeitsregeln, z. B. auf der Grundlage von Kategorieberechtigungen

Je nach [Commerce-Services](../landing/saas.md) installiert sind, stehen Ihnen möglicherweise verschiedene Feeds zur Verfügung für `saas:resync` Befehl.

Die Ausführung der `saas:resync` regulären Befehls. Möglicherweise müssen Sie den Befehl in zwei Szenarien manuell ausführen:

- Die erste Synchronisierung
- Die [SaaS-Datenraum-ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) geändert wurde

### Erstsynchronisierung

Beim Trigger eines `saas:resync` über die Befehlszeile kann es je nach Größe Ihres Katalogs einige Minuten bis einige Stunden dauern, bis die Daten aktualisiert werden.

Für die anfängliche Synchronisierung wird empfohlen, Befehle in der folgenden Reihenfolge auszuführen:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### Fehlerbehebung

Wenn die erwarteten Daten in [!DNL Commerce Service], überprüfen Sie, ob während der Synchronisierung aus dem [!DNL Adobe Commerce] -Instanz auf [!DNL Commerce Service] Plattform.

Es gibt zwei Protokolldateien im `var/log/` directory:

- `commerce-data-export-errors.log` - wenn während der _sammeln_ Phase
- `saas-export-errors.log` - wenn während der _Sendung_ Phase

#### Überprüfen der Feed-Payload

Es kann nützlich sein, die Feed-Payload anzuzeigen, die an die [!DNL Commerce Service]. Dies kann durch Übergabe der Umgebungsvariablen erfolgen `EXPORTER_EXTENDED_LOG=1`. Die `no-reindex` Markierung bedeutet, dass nur die derzeit erfassten Daten gesendet werden.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

Die Payload ist verfügbar in `var/log/saas-export.log`.

#### Payload in Feed-Indextabelle beibehalten

Staging von `magento/module-data-exporter:103.0.0` Einige Feeds: Produkt-Feed, Preis-Feeds, bewahren Sie nur die erforderlichen Mindestdaten in der Indextabelle auf.

Die Beibehaltung von Payload-Daten in der Indextabelle wird für die Produktion nicht empfohlen, kann aber auf einer Entwicklerinstanz nützlich sein. Dies geschieht durch Übergabe der `PERSIST_EXPORTED_FEED=1` Umgebungsvariable:

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### Profiling

Wenn der Neuindizierungsprozess bestimmter Feeds unangemessen lange dauert, führen Sie den Profiler aus, um zusätzliche Daten zu erfassen, die für das Supportteam nützlich sein könnten. Übergeben Sie dazu die Variable `EXPORTER_PROFILER=1`Umgebungsvariable:

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profildaten werden in gespeichert `var/log/commerce-data-export.log` mit dem Format:

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### Senden einer Support-Anfrage

Wenn Fehler auftreten, die nicht mit der Konfiguration oder Erweiterungen von Drittanbietern in Zusammenhang stehen, senden Sie eine [Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) mit so vielen Informationen wie möglich.
