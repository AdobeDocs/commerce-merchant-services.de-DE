---
title: Katalogsynchronisierung
description: Erfahren Sie, wie Sie Produktdaten vom  [!DNL Commerce] Server nach [!DNL Commerce Services] exportieren.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 0b0bc88c13d8c90a6209d9156f6fd6a7ce040f72
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Katalogsynchronisierung

>[!NOTE]
>
> Das Dashboard für die Katalogsynchronisierung ist jetzt das Dashboard für die Datenverwaltung. Dieses überarbeitete Dashboard unterstützt jetzt [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md) v6.0.0+, [[!DNL Live Search]](../live-search/overview.md) v4.1.0+ und [[!DNL Catalog Service]](../catalog-service/overview.md) v1.17+. Kunden können das Data Management Dashboard abrufen, indem sie auf die neueste Version eines dieser Dienste aktualisieren. Weitere Informationen dazu finden Sie in der Dokumentation zum [Data Management Dashboard](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) . Dieses aktuelle Thema richtet sich nach den Benutzern, die noch kein Upgrade durchführen müssen und noch über das Dashboard Katalogsynchronisierung verfügen.

Adobe Commerce verwendet Indexer, um Katalogdaten in Tabellen zu kompilieren. Der Prozess wird automatisch durch [Ereignisse](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) ausgelöst, z. B. eine Änderung an einem Produktpreis oder Lagerbestand.

Der Dienst zur Katalogsynchronisierung verschiebt Produktdaten laufend von einer [!DNL Adobe Commerce] -Instanz auf die [!DNL Commerce Services] -Plattform, um die Daten auf dem neuesten Stand zu halten. Beispielsweise erfordert [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) die aktuellen Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit genau zurückzugeben. Verwenden Sie das Dashboard _Katalogsynchronisierung_ , um den Synchronisierungsprozess oder die Befehlszeilenschnittstelle zu beobachten und zu verwalten, um eine Katalogsynchronisierung Trigger und Produktdaten für die Verwendung durch [!DNL Commerce Services] neu zu indizieren. Siehe [Befehlszeilenschnittstelle-Referenz](../data-export/data-export-cli-commands.md) im Handbuch _SAAS-Datenexport_ .

## Zugriff auf das Dashboard &quot;Katalogsynchronisierung&quot;

Um auf das Dashboard &quot;Katalogsynchronisierung&quot;zuzugreifen, wählen Sie **System** > _Datenübertragung_ > **Katalogsynchronisierung** aus.

Im Dashboard **Katalogsynchronisierung** haben Sie folgende Möglichkeiten:

- Synchronisierungsstatus anzeigen (**Wird ausgeführt**, **Erfolg**, **Fehlgeschlagen**)
- Gesamtanzahl der synchronisierten Produkte anzeigen
- Synchronisierte Produkte suchen, um ihren aktuellen Status anzuzeigen
- Suchspeicherkatalog nach Name, SKU usw.
- Anzeigen synchronisierter Produktdetails in JSON, um eine Synchronisierungsdiskrepanz zu diagnostizieren
- Initialisieren des Synchronisierungsprozesses

### Letzte Synchronisierung

Meldet einen Synchronisierungsstatus von:

- **Erfolg** - Zeigt das Datum und die Uhrzeit an, zu der die Synchronisierung erfolgreich war und die Anzahl der aktualisierten Produkte.
- **Fehlgeschlagen** - Zeigt das Datum und die Uhrzeit des Synchronisierungsversuchs an
- **Wird ausgeführt** - Zeigt das Datum und die Uhrzeit der letzten erfolgreichen Synchronisierung an

Der Vorgang zur Katalogsynchronisierung wird automatisch stündlich ausgeführt. Wenn die erwarteten Produkte nicht auf der Storefront angezeigt werden oder die Produkte die kürzlich vorgenommenen Änderungen nicht widerspiegeln, können Sie [Probleme bei der Katalogsynchronisierung](#resolvesync) beheben.

### Synchronisierte Produkte

Zeigt die Gesamtzahl der Produkte an, die aus Ihrem [!DNL Commerce]-Katalog synchronisiert wurden. Nach der ersten Synchronisierung sollten nur geänderte Produkte synchronisiert werden.

## Neu synchronisieren {#resync}

Wenn Sie eine Neusynchronisierung Ihres Katalogs starten müssen, bevor die stündliche geplante Synchronisierung erfolgt, können Sie eine Neusynchronisierung erzwingen.

>[!NOTE]
>
> Erzwingen einer erneuten Synchronisierung von Triggern eine Neusynchronisierung des gesamten Produktkatalogs, was die Belastung der Hardware-Ressourcen erhöhen kann.

1. Wählen Sie im Dashboard _Katalogsynchronisierung_ die Option **Einstellungen** aus.

   Die Seite _Einstellungen für die Katalogsynchronisierung_ wird angezeigt.

1. Klicken Sie im Abschnitt _Daten neu synchronisieren_ auf [!UICONTROL Resync].

   [!DNL Commerce] synchronisiert Ihren Katalog im nächsten geplanten Synchronisierungsfenster. Je nach Größe Ihres Katalogs kann dieser Vorgang sehr lange dauern.

## Synchronisierte Katalogprodukte

Die Tabelle **Synchronisierte Katalogprodukte** enthält die folgenden Informationen.

| Feld | Beschreibung |
|---|---|
| ID | Eindeutige Kennung des Produkts |
| Name | Storefront-Name des Produkts |
| Typ | Identifiziert den Produkttyp, z. B. einfach, konfigurierbar oder herunterladbar |
| Zuletzt exportiert | Datum, an dem das Produkt zuletzt erfolgreich aus Ihrem Katalog exportiert wurde |
| Zuletzt geändert | Datum der letzten Änderung des Produkts in Ihrem Katalog |
| SKU | Zeigt die Lagereinheit für das Produkt an |
| Preis | Preis der Ware |
| Sichtbarkeit | Sichtbarkeitseinstellung eines Produkts, wie im [!DNL Commerce]-Katalog definiert |

## Beheben von Problemen bei der Katalogsynchronisierung {#resolvesync}

Siehe [Protokolle und Fehlerbehebung](../data-export/troubleshooting-logging.md#troubleshooting) im _SAAS-Datenexport-Handbuch_.
