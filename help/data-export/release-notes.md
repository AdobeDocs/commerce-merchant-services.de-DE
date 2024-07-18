---
title: '[!DNL SaaS Data Export Extension] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Data Export Extension] für Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 7757cc382e306a6c074a815d5148a4dcd8fff284
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Versionshinweise zur Erweiterung

In diesen Versionshinweisen werden die neuesten Versionen der [!DNL SaaS data export] -Erweiterung beschrieben. Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.

Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme


>[!NOTE]
>
>Die SaaS-Datenexport-Erweiterung ist eine Sammlung von Modulen, die automatisch mit Live Search, Product Recommendations und dem Catalog Service installiert werden. Sie können die auf Ihrem System installierte Version mithilfe von Composer überprüfen. In einigen Fällen möchten Sie möglicherweise die Datenexport-Erweiterung auf Ihrem System aktualisieren, um Korrekturen oder neue Funktionen aufzunehmen, ohne die Version des Commerce-Dienstes zu aktualisieren.

## Aktuelle Hauptversion

## Version 103.3.8

![Korrektur](../assets/fix.svg) Deaktivierte Konfigurationsoptionen werden nicht mehr als aktive Optionen exportiert.<!--MDEE-812-->
![Korrektur](../assets/fix.svg) Optionen und Werte werden jetzt für ein konfigurierbares Produkt aktualisiert, wenn Änderungen an einem untergeordneten Produkt vorgenommen werden. <!--MDEE-835-->
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, zusätzliche Systemattributdaten in den Feed &quot;Produktattribute&quot;einzuschließen.

## Version 103.3.7

![Korrektur](../assets/fix.svg) unnötige Abhängigkeiten aus dem Modul &quot;InventoryDataExporter&quot;entfernt.
![Korrektur](../assets/fix.svg) Die erforderlichen Versionen für die im CatalogInventoryDataExporter-Modul enthaltenen Inventarmodule wurden geändert, um die Adobe Commerce-Version 2.4.4 zu unterstützen.

## Version 103.3.6

![Korrektur](../assets/fix.svg) Deadlocks behoben, die während der Neuindizierung von Feeds im Multi-Thread-Modus aufgetreten sind. Die Abfragen sind nun in die Vorgänge &quot;Einfügen&quot;und &quot;Aktualisieren&quot;unterteilt.
![Korrektur](../assets/fix.svg) Die Preisabfrage für große Kataloge mit vielen Websites wurde optimiert.
![Neu](../assets/new.svg) Eine Wiederholungslogik wurde hinzugefügt, um fehlgeschlagene Transaktionen bei Deadlocks erneut auszuführen.

## Version 103.3.5

![Korrektur](../assets/fix.svg) Stellen Sie die Abhängigkeit für die neueste kompatible Datenexportversion für das allgemeine SaaS-Modul ein.

![Korrektur](../assets/fix.svg) Die `ScopeConfig` -Instanz wurde durch `ServiceConfigInterface` ersetzt, um verschiedene Dienstkonfigurationen zu unterstützen.

## Version 103.3.4

![Korrektur](../assets/fix.svg) Verbessern Sie die Protokollierung des Commerce SaaS-Datenexports, indem Sie weitere Details zum Neuindizierungsprozess hinzufügen.

## Version 103.3.3

![Neu](../assets/new.svg) Der SAAS-Datenexport speichert jetzt Entitäts-Attribut-Wert (EAV)-Attribute für die Attributmetadatenabfrage zwischen.

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der `InventoryStockStatus` -Feed beim erneuten Versuch nicht gespeichert wurde, wenn das Produkt gelöscht wurde.

## Version 103.3.2

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem das Feld `modifiedAt` in entfernten Entitäts-Feeds fehlte.

## Version 103.3.1

![Korrektur](../assets/fix.svg) Korrektur eines Fehlers, der dazu führte, dass während der Neuindizierung des Produkt-Feeds bei der Installation von Page Builder eine `Invalid Template File` -Meldung angezeigt wurde.

## Version 103.3.0

![Neu](../assets/new.svg) Migrieren von sofort exportierten Feed-Tabellen in die einheitliche Struktur:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Neu](../assets/new.svg) Katalog- und Inventar-Feeds wurden zur sofortigen Exportlösung migriert.

![Neu](../assets/new.svg): Umbenannte Cron-Aufträge für den sofortigen Export-Feed in `*_feed_resend_failed_items`.

![Neu](../assets/new.svg) Umbenannte sofortige Export-Feeds und Änderung von Protokolltabellen.

![Korrektur](../assets/fix.svg) Setzen Sie das Feld `modified_at` nur für Feeds, für die dies erforderlich ist, in den Feed-Daten.

![Korrektur](../assets/fix.svg) Ändern Sie die `productAttributes` -Abfrage, um nur Produktattribute abzurufen.

## Version 103.2.6

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, das die Neuindizierung von Feeds verhinderte, wenn Tabellen über ein Präfix verfügten.

## Version 103.2.5

![Korrektur](../assets/fix.svg) Die Preisabfrage wurde optimiert.

## Version 103.2.4

![Korrektur](../assets/fix.svg) Korrektur des falschen Lagerstatus, der für ein Produkt angezeigt wurde, wenn Commerce Inventory management aktiviert war.

## Version 103.2.3

![Korrektur](../assets/fix.svg) Korrektur der Sonderpreise auf Website-Ebene.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Mutex für alle verarbeiteten Feeds hinzugefügt.


## Version 103.2.2

![Korrektur](../assets/fix.svg) Verbesserte Batch-Strategie für Feeds für große Kataloge. Die Stapeltabelle ist jetzt mit einer begrenzten Anzahl von IDs gefüllt, um die Speicherbelegung zu reduzieren.

![Korrektur](../assets/fix.svg) Die harte Abhängigkeit von CommerceInventoryDataExporter von MSI-Modulen wurde beseitigt.

![Korrektur](../assets/fix.svg) Verbesserte `commerce-data-exporter` Protokolle, um mehr Informationen zu sammeln und nach verschiedenen Exportphasen zu organisieren.

## Version 103.2.1

- Aktualisierte Version veröffentlicht.

## Version 103.2.0

- Die Datensynchronisierung mit mehreren Threads für Produkte und Preise wurde hinzugefügt.
