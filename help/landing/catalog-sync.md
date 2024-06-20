---
title: Katalogsynchronisierung
description: Erfahren Sie, wie Sie Produktdaten aus der [!DNL Commerce] Server zu [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Katalogsynchronisierung

>[!NOTE]
>
> Das Dashboard für die Katalogsynchronisierung ist jetzt das Dashboard für die Datenverwaltung. Dieses überarbeitete Dashboard unterstützt jetzt [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md), und [[!DNL Catalog Service]](../catalog-service/overview.md). Kunden können das Data Management Dashboard abrufen, indem sie auf die neueste Version eines dieser Dienste aktualisieren. Mehr darüber erfahren Sie im Abschnitt [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) Dokumentation. Dieses aktuelle Thema richtet sich nach den Benutzern, die noch kein Upgrade durchführen müssen und noch über das Dashboard Katalogsynchronisierung verfügen.

Adobe Commerce verwendet Indexer, um Katalogdaten in Tabellen zu kompilieren. Der Prozess wird automatisch von [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) wie eine Änderung des Produktpreises oder des Lagerbestands.

Der Catalog Sync-Dienst verschiebt Produktdaten von einem [!DNL Adobe Commerce] -Instanz auf [!DNL Commerce Services] -Plattform auf dem neuesten Stand zu halten. Beispiel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) erfordert aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit exakt zurückzugeben. Verwenden Sie die _Katalogsynchronisierung_ Dashboard zur Beobachtung und Verwaltung des Synchronisierungsprozesses oder der Befehlszeilenschnittstelle zum Trigger einer Katalogsynchronisierung und zur Neuindizierung von Produktdaten zur Verwendung durch [!DNL Commerce Services]. Siehe [Befehlszeilenschnittstelle - Referenz](../data-export/data-export-cli-commands.md) im _SaaS-Datenexport_ Handbuch.

## Zugriff auf das Dashboard &quot;Katalogsynchronisierung&quot;

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

Siehe [Protokolle und Fehlerbehebung](../data-export/troubleshooting-logging.md#troubleshooting) im _SaaS-Datenexportanleitung_.
