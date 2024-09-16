---
title: '[!DNL SaaS Data Export Guide]'
description: Erfahren Sie mehr über die Verwendung der [!DNL data export] Erweiterung für Adobe Commerce SaaS-Dienste, die Daten zwischen Adobe Commerce und verbundenen Commerce-Diensten synchronisieren.
role: Admin, Developer
exl-id: c5711fa6-09e2-42b0-a7af-4d7b866c871d
source-git-commit: 2eeb11bf5ead38131d42b330162ea3d9c531c465
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Handbuch zu [!DNL SaaS Data Export]

[!DNL SaaS data export] synchronisiert Daten zwischen einer Adobe Commerce-Instanz und verbundenen Commerce Services. Wenn Sie einer Adobe Commerce-Installation Live Search, Product Recommendations oder den Catalog Service hinzufügen, wird die Erweiterung [!DNL Data export] automatisch installiert.

Der SAAS-Datenexport erfasst und exportiert verschiedene Datentypen, die als _Feeds_ bezeichnet werden und bestimmte Arten von Informationen aggregieren. Je nachdem, welche Commerce-Dienste installiert sind, umfassen die SaaS-Datenexport-Feeds Folgendes:

- **Katalogentitäts-Feeds** aggregierte Produktdaten. Die Daten umfassen Produkte, Produktattribute, Produktpreise, Produktvarianten, Kategorien, Kategorieberechtigungen und Produktberechtigungen.
- Der **Scopes-Feed** aggregiert Daten für Kundengruppen, Websites, Stores und Store-Ansichten.
- Der **Feed &quot;Verkaufsaufträge&quot;** aggregiert Auftragsdaten einschließlich der zugehörigen Entitäten wie Rechnungen, Sendungen, Kreditkarten usw.
- Der **Multi-Source Inventar-Feed** aggregiert Daten zu Lagerbestandsstatuselementen.

Der SaaS-Datenexport wird als PHP-Erweiterung geliefert. Es unterstützt mehrere Methoden zum Initiieren und Verwalten des Datensynchronisierungsprozesses.

- **Manuelle Synchronisation über den Administrator oder die Befehlszeile**

   - Das Dashboard [Datenverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) in Commerce Admin bietet eine grafische Ansicht des Synchronisierungsstatus. Sie können das Dashboard verwenden, um eine vollständige Neusynchronisierung (_vollständige Synchronisierung_) aller Feeds durchzuführen. Adobe empfiehlt jedoch, nur eine vollständige Synchronisierung durchzuführen, wenn Sie Adobe Commerce zum ersten Mal mit einem Commerce-Dienst verbinden. Siehe [Synchronisierungsprozess](data-synchronization.md).

   - Das Befehlszeilen-Tool [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) bietet Befehle zum Synchronisieren bestimmter Feeds und umfasst zusätzliche Optionen zum Anpassen der Feed-Verarbeitung.

- **Automatisierte Synchronisierung mit Cron-Aufträgen**

   - [TeilDatensynchronisation](data-synchronization.md#partial-synchronization-with-cron-jobs) - Cron-Aufträge führen zu einer teilweisen Datensynchronisation, wenn ein Commerce-Administrator eine Entität aktualisiert. Der Datenexportprozess sendet nur diese Aktualisierungen an verbundene Commerce-Dienste. Der teilweise Synchronisierungsprozess basiert auf dem MView-Mechanismus und erfordert keine Aktionen des Admin-Benutzers oder Systemintegrators.

   - [Automatischer Neuversuch auf Synchronisierungsfehler](data-synchronization.md#failed-items-sync-for-error-recovery) - Der Cron-Auftrags-Trigger versucht den Synchronisierungsprozess automatisch erneut, wenn während des Datensynchronisierungsprozesses Fehler auftreten.

- **Exportplanung und -leistung**

   - Entwickler und Systemintegratoren können die für den SAAS-Datenexport erforderliche Zeit schätzen, um Daten zwischen Adobe Commerce und verbundenen Diensten zu synchronisieren. Diese Schätzung kann bei der Planung der Datenexportverarbeitung helfen, um eine Site-Unterbrechung zu verhindern. Siehe [Schätzen des Datenvolumens und der Übertragungszeit ](estimate-data-volume-sync-time.md).

   - In Fällen, in denen die Synchronisierung schneller erfolgen muss, bietet der SAAS-Datenexport Anpassungsoptionen zur Verbesserung der Exportverarbeitungsleistung. Siehe [Verbessern der Datenexportleistung](customize-export-processing.md).

- **Tracking und Fehlerbehebung bei Datenexportaktivitäten** - Verwenden Sie Datenexport- und SAAS-Export-Protokolle, um den Synchronisierungsstatus und die Feed-Payloads während des Synchronisations- und Indexierungsprozesses zu überprüfen. Siehe [Protokollierung und Fehlerbehebung](troubleshooting-logging.md).
