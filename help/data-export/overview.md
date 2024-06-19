---
title: "[!DNL SaaS Data Export Guide]"
description: "Erfahren Sie mehr über die Verwendung der [!DNL data export] Erweiterung für Adobe Commerce SaaS-Dienste, die Daten zwischen Adobe Commerce und verbundenen Commerce-Diensten synchronisieren."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Handbuch zu [!DNL SaaS Data Export]

[!DNL SaaS data export] verbessert die Frontend-Leistung durch die Optimierung der Datensynchronisation zwischen einer Adobe Commerce-Instanz und verbundenen Commerce-Diensten. Wenn Sie einer Adobe Commerce-Installation Live Search, Product Recommendations oder den Catalog Service hinzufügen, wird die [!DNL Data export] wird automatisch installiert.

Der SAAS-Datenexport erfasst und exportiert verschiedene Datentypen, die als _Feeds_, die bestimmte Arten von Informationen aggregieren. Je nachdem, welche Commerce-Dienste installiert sind, umfassen die SaaS-Datenexport-Feeds Folgendes:

- **Katalogentitäts-Feeds** aggregierte Produktdaten. Die Daten umfassen Produkte, Produktattribute, Produktpreise, Produktvarianten, Kategorien, Kategorieberechtigungen und Produktberechtigungen.
- Die **Scopes-Feed** aggregiert Daten für Kundengruppen, Websites, Stores und Store-Ansichten.
- Die **Feed für Verkaufsaufträge** aggregiert Daten zu Bestellungen, einschließlich der mit ihnen verbundenen Einheiten wie Rechnungen, Sendungen, Kreditkarten usw.
- Die **Inventar-Feed aus mehreren Quellen** aggregiert Daten zu Bestandstatuselementen.

Die Datenexport-Erweiterung unterstützt mehrere Methoden zum Initiieren und Verwalten des Datensynchronisierungsprozesses.

- **Manuelle Synchronisierung über den Administrator oder die Befehlszeile**

   - Die [Data Management-Dashboard](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) im Commerce Admin bietet eine grafische Ansicht des Synchronisierungsstatus. Sie können das Dashboard verwenden, um eine vollständige Resynchronisation durchzuführen (_Vollständige Synchronisierung_) aller Feeds. Adobe empfiehlt jedoch, nur eine vollständige Synchronisierung durchzuführen, wenn Sie Adobe Commerce zum ersten Mal mit einem Commerce-Dienst verbinden. Siehe [Synchronisierungsprozess](data-synchronization.md).

   - Die [Adobe Commerce-Befehlszeilen-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) bietet Befehle zum Synchronisieren bestimmter Feeds und umfasst zusätzliche Optionen zum Anpassen der Feed-Verarbeitung.

- **Automatisierte Synchronisierung mit Cron-Aufträgen**

   - [Partielle Datensynchronisation](data-synchronization.md#partial-synchronization-with-cron-jobs)—Cron-Aufträge Trigger eine teilweise Datensynchronisation, wenn ein Commerce-Administrator eine Entität aktualisiert. Der Datenexportprozess sendet nur diese Aktualisierungen an verbundene Commerce-Dienste. Der teilweise Synchronisierungsprozess basiert auf dem MView-Mechanismus und erfordert keine Aktionen des Admin-Benutzers oder Systemintegrators.

   - [Automatische Wiederholung von Synchronisierungsfehlern](data-synchronization.md#failed-items-sync-for-error-recovery)—Cron Jobs Trigger wiederholt den Synchronisierungsprozess automatisch erneut, wenn während der Datensynchronisation Fehler auftreten.

- **Exportplanung und -leistung**

   - Entwickler und Systemintegratoren können die für den SAAS-Datenexport erforderliche Zeit schätzen, um Daten zwischen Adobe Commerce und verbundenen Diensten zu synchronisieren. Diese Schätzung kann bei der Planung der Datenexportverarbeitung helfen, um eine Site-Unterbrechung zu verhindern. Siehe [Geschätztes Datenvolumen und Übertragungszeit](estimate-data-volume-sync-time.md).

   - In Fällen, in denen die Synchronisierung schneller erfolgen muss, bietet der SAAS-Datenexport Anpassungsoptionen zur Verbesserung der Exportverarbeitungsleistung. Siehe [Verbessern der Datenexportleistung](customize-export-processing.md).

- **Tracking und Fehlerbehebung von Datenexport-Aktivitäten**—Verwenden Sie Datenexport- und SAAS-Export-Protokolle, um den Synchronisierungsstatus und die Feed-Payloads während des Synchronisations- und Indexierungsprozesses zu überprüfen. Siehe [Protokollierung und Fehlerbehebung](troubleshooting-logging.md).



