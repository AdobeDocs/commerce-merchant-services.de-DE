---
title: Katalogsynchronisierung
description: Erfahren Sie, wie Sie Produktdaten aus der [!DNL Commerce] Server zu [!DNL Commerce Services] laufend, um die Dienstleistungen auf dem neuesten Stand zu halten.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: 6d0c7c749fe90c7c204afe47446f3483d8668b53
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Katalogsynchronisierung

Adobe Commerce und Magento Open Source verwenden Indexer, um Katalogdaten in Tabellen zu kompilieren. Der Prozess wird automatisch von [events](https://docs.magento.com/user-guide/system/index-management-events.html) wie eine Änderung des Produktpreises oder des Lagerbestands.

Der Katalogsynchronisierungsprozess wird stündlich ausgeführt, um [!DNL Commerce] Dienste zur Verwendung von Katalogdaten. Die Katalogsynchronisierung exportiert Produktdaten aus der [!DNL Commerce] Server zu [!DNL Commerce] Dienstleistungen, um die Dienstleistungen auf dem neuesten Stand zu halten. Beispiel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) benötigt aktuelle Kataloginformationen, um Empfehlungen mit korrekten Namen, Preisen und Verfügbarkeit exakt zurückzugeben. Sie können die _Katalogsynchronisierung_ Dashboard zur Beobachtung und Verwaltung des Synchronisierungsprozesses oder der [Befehlszeilenschnittstelle](#resynccmdline) zum Trigger der Katalogsynchronisierung und der Neuindizierung von Produktdaten für die Verwendung durch [!DNL Commerce] Dienste.

>[!NOTE]
>
> So verwenden Sie die _Katalogsynchronisierung_ -Dashboard oder der Befehlszeilenschnittstelle muss eine [API-Schlüssel und konfigurierter SaaS-Datenraum](saas.md).

## Zugriff auf das Dashboard &quot;Katalogsynchronisierung&quot;

Um auf das Dashboard Katalogsynchronisierung zuzugreifen, wählen Sie **System** > _Datenübertragung_ > **Katalogsynchronisierung**.

Mit dem **Katalogsynchronisierung** Dashboard:

- Synchronisierungsstatus anzeigen (**In Bearbeitung**, **Erfolg**, **Fehlgeschlagen**)
- Anzeigen der Gesamtzahl der synchronisierten Produkte bei Erfolg
- Suchen Sie synchronisierte Produkte, um ihren aktuellen Status anzuzeigen.
- Suchspeicherkatalog nach Name, SKU usw.
- Anzeigen synchronisierter Produktdetails in JSON, um eine Synchronisierungsdiskrepanz zu diagnostizieren
- Initialisieren des Synchronisierungsprozesses

### Letzte Synchronisierung

Meldet einen Synchronisierungsstatus von:

- **Erfolg** - Zeigt das Datum und die Uhrzeit der erfolgreichen Synchronisierung und die Anzahl der aktualisierten Produkte an
- **Fehlgeschlagen** - Zeigt das Datum und die Uhrzeit des Synchronisierungsversuchs an
- **In Bearbeitung** - Zeigt Datum und Uhrzeit der letzten erfolgreichen Synchronisierung an

>[!NOTE]
>
> Der Vorgang zur Katalogsynchronisierung wird automatisch stündlich ausgeführt. Wenn Sie jedoch keine Produkte in Ihrer Storefront sehen oder die Produkte nicht die kürzlich vorgenommenen Änderungen widerspiegeln, können Sie [Probleme bei der Katalogsynchronisierung](#resolvesync).

### Synchronisierte Produkte

Zeigt die Gesamtzahl der mit Ihrer [!DNL Commerce] Katalog. Nach der ersten Synchronisierung sollten Sie erwarten, dass nur geänderte Produkte synchronisiert werden.

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
| Typ | Identifiziert den Produkttyp, z. B. einfach, konfigurierbar, herunterladbar usw. |
| Zuletzt exportiert | Datum, an dem das Produkt zuletzt erfolgreich aus Ihrem Katalog exportiert wurde |
| Zuletzt geändert | Datum der letzten Änderung des Produkts in Ihrem Katalog |
| SKU | Zeigt die Lagereinheit für das Produkt an |
| Preis | Preis der Ware |
| Sichtbarkeit | Die Sichtbarkeitseinstellung eines Produkts, wie in der Variablen [!DNL Commerce] Katalog |

## Beheben von Problemen bei der Katalogsynchronisierung {#resolvesync}

Wenn Sie eine Datenresynchronisierung Trigger haben, kann es bis zu eine Stunde dauern, bis die Daten aktualisiert und in UI-Komponenten wie Empfehlungseinheiten angezeigt werden. Wenn Sie jedoch nach einer stündlichen Wartezeit immer noch Abweichungen zwischen Ihrem Katalog und dem, was auf Ihrer Storefront angezeigt wird, feststellen oder wenn die Katalogsynchronisierung fehlgeschlagen ist, sehen Sie sich Folgendes an:

### Datendiskrepanz

1. Zeigen Sie die detaillierte Ansicht des betreffenden Produkts in den Suchergebnissen an.
1. Kopieren Sie die JSON-Ausgabe und stellen Sie sicher, dass der Inhalt mit dem übereinstimmt, den Sie im [!DNL Commerce] Katalog.
1. Wenn der Inhalt nicht übereinstimmt, nehmen Sie eine geringfügige Änderung am Produkt in Ihrem Katalog vor, z. B. das Hinzufügen eines Leerzeichens oder eines Zeitraums.
1. Warten Sie auf eine Neusynchronisierung oder [Trigger einer manuellen Neusynchronisierung](#resync).

### Synchronisierung wird nicht ausgeführt

Wenn die Synchronisierung nicht planmäßig ausgeführt wird oder nichts synchronisiert wird, lesen Sie den Abschnitt [KnowledgeBase](https://support.magento.com/hc/en-us/articles/360042224851).

### Synchronisierung fehlgeschlagen

Wenn die Katalogsynchronisierung den Status **Fehlgeschlagen**, senden Sie eine [Support-Ticket](https://support.magento.com/hc/en-us/articles/360019088251).

## Befehlszeilenschnittstelle {#resynccmdline}

Die `saas:resync` -Befehl ist Teil der `magento/saas-export` Paket. Sie können dieses Paket mit einem der [!DNL Commerce Services] Produkte wie [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) oder [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Wenn Sie eine erneute Synchronisierung von Daten über die Befehlszeile Trigger haben, kann es bis zu einer Stunde dauern, bis die Daten aktualisiert werden.

Befehlsoptionen:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

Die folgende Tabelle beschreibt die `saas:resync` Parameter und Beschreibungen.

| Parameter | Beschreibung | Erforderlich? |
|---| ---| ---|
| `feed` | Gibt an, welche Entität erneut synchronisiert werden soll, z. B. `products` | Ja |
| `no-reindex` | Sendet die vorhandenen Katalogdaten an [!DNL Commerce Services] ohne Neuindizierung. Wenn dieser Parameter nicht angegeben ist, führt der Befehl vor der Synchronisierung von Daten eine vollständige Neuindizierung durch. | Nein |

Der Feed-Name kann einer der folgenden sein:

- `products`- Produkte in Ihrem Katalog
- `categories`— Kategorien in Ihrem Katalog
- `variants`— Produktvarianten eines konfigurierbaren Produkts wie Farbe und Größe
- `productattributes`- Produktattribute wie `activity`, `gender`, `tops`, `bottoms`, usw.
- `productoverrides`— Kundenspezifische Preisbildungs- und Katalogsichtbarkeitsregeln, z. B. auf der Grundlage von Kategorieberechtigungen

### Beispiele

Im folgenden Beispiel werden die Produktdaten aus der [!DNL Commerce] Kataloge erstellen und sie erneut mit Commerce-Diensten synchronisieren:

```bash
bin/magento saas:resync --feed products
```

Wenn Sie keine vollständige Neuindizierung der Produkte ausführen möchten, können Sie stattdessen die bereits generierten Produktdaten synchronisieren:

```bash
bin/magento saas:resync --feed products --no-reindex
```
