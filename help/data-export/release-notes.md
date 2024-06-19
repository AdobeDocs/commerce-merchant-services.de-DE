---
title: "[!DNL SaaS Data Export Extension] Versionshinweise"
description: Die neuesten Versionshinweise für [!DNL Data Export Extension] für Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Versionshinweise zur Erweiterung

In diesen Versionshinweisen werden die neuesten Versionen der [!DNL SaaS data export] -Erweiterung. Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.

Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme


>[!NOTE]
>
>Die SaaS-Datenexport-Erweiterung ist eine Sammlung von Modulen, die automatisch mit Live Search, Product Recommendations und dem Catalog Service installiert werden. Sie können die auf Ihrem System installierte Version mithilfe von Composer überprüfen. In einigen Fällen möchten Sie möglicherweise die Datenexport-Erweiterung auf Ihrem System aktualisieren, um Korrekturen oder neue Funktionen aufzunehmen, ohne die Version des Commerce-Dienstes zu aktualisieren.

## Aktuelle Hauptversion

## Version 103.3.5

![Fehlerbehebung](../assets/fix.svg) Legen Sie die Abhängigkeit für die neueste kompatible Datenexportversion für das allgemeine SaaS-Modul fest.

![Fehlerbehebung](../assets/fix.svg) Ersetzt `ScopeConfig` Instanz mit `ServiceConfigInterface` , um verschiedene Dienstkonfigurationen zu unterstützen.

## Version 103.3.4

![Fehlerbehebung](../assets/fix.svg) Verbessern Sie die Protokollierung des Commerce SaaS-Datenexports, indem Sie weitere Details zum Neuindizierungsprozess hinzufügen.

## Version 103.3.3

![Neu](../assets/new.svg) Der SAAS-Datenexport speichert jetzt Entitäts-Attribut-Wert (EAV)-Attribute für die Attributmetadatenabfrage zwischen.

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem die Variable `InventoryStockStatus` Der Feed wurde beim erneuten Versuch nicht gespeichert, wenn das Produkt gelöscht wurde.

## Version 103.3.2

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem die Variable `modifiedAt` -Feld fehlte in entfernten Entitäts-Feeds.

## Version 103.3.1

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, das eine `Invalid Template File` Meldung, die bei der Neuindizierung des Produkt-Feeds angezeigt wird, wenn der Seitenaufbau installiert ist.

## Version 103.3.0

![Neu](../assets/new.svg) Migrieren von sofortigen Export-Feed-Tabellen in die einheitliche Struktur:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Neu](../assets/new.svg) Katalog- und Inventar-Feeds zur sofortigen Exportlösung migriert.

![Neu](../assets/new.svg) Umbenennung sofortiger Export-Feed-Cron-Aufträge in `*_feed_resend_failed_items`.

![Neu](../assets/new.svg) Umbenennung des sofortigen Export-Feeds und Änderung der Protokolltabellen.

![Fehlerbehebung](../assets/fix.svg) Satz `modified_at` -Feld in den Feed-Daten nur für Feeds, für die dies erforderlich ist.

![Fehlerbehebung](../assets/fix.svg) Ändern Sie die `productAttributes` Abfrage zum Abrufen nur von Produktattributen.

## Version 103.2.6

![Fehlerbehebung](../assets/fix.svg) Fehlerkorrektur - Feeds können jetzt neu indiziert werden, wenn Tabellen über ein Präfix verfügen.

## Version 103.2.5

![Fehlerbehebung](../assets/fix.svg) Die Preisabfrage wurde optimiert.

## Version 103.2.4

![Fehlerbehebung](../assets/fix.svg) Es wurde ein falscher Lagerstatus behoben, der für ein Produkt angezeigt wurde, wenn Commerce Inventory management aktiviert war.

## Version 103.2.3

![Fehlerbehebung](../assets/fix.svg) Die Sonderpreise auf Website-Ebene wurden korrigiert.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein mutex für alle Feeds hinzugefügt, die verarbeitet werden.


## Version 103.2.2

![Fehlerbehebung](../assets/fix.svg) Verbesserte Batch-Strategie für Feeds für große Kataloge. Die Stapeltabelle ist jetzt mit einer begrenzten Anzahl von IDs gefüllt, um die Speicherbelegung zu reduzieren.

![Fehlerbehebung](../assets/fix.svg) Die feste Abhängigkeit von CommerceInventoryDataExporter von MSI-Modulen wurde beseitigt.

![Fehlerbehebung](../assets/fix.svg) Verbessert `commerce-data-exporter` Protokolle, um weitere Informationen zu sammeln und nach verschiedenen Exportphasen zu organisieren.

## Version 103.2.1

- Aktualisierte Version veröffentlicht.

## Version 103.2.0

- Die Datensynchronisierung mit mehreren Threads für Produkte und Preise wurde hinzugefügt.

