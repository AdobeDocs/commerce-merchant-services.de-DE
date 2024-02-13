---
title: Feed-Erfassungsdienst
description: Erfahren Sie mehr über den Feed-Erfassungsdienst für Adobe Commerce
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
source-git-commit: d3798efa038c35f71bb0bb6874d954a8e66c7467
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Feed-Erfassungsdienst

Mit dem Feed-Erfassungsdienst können Kunden mit großen und/oder komplexen Katalogen Daten direkt an Adobe Commerce-Dienste senden.

Der Feed-Erfassungsdienst verkürzt die Zeit, die für die Verarbeitung von Produktänderungen (Preisaktualisierungen, Hinzufügen neuer Attribute) benötigt wird, indem die Adobe Commerce-Instanz umgangen und Katalogdaten von einer externen Enterprise Resource Planning (ERP) direkt zu Adobe Commerce-Diensten verschoben werden.

Dieser Dienst richtet sich an Kunden, die ihren Produktkatalog in einem außerhalb der Adobe Commerce-Hauptanwendung gelegenen System speichern und verwalten. Sie wird als API bereitgestellt, damit Kunden sie in ihre vorhandenen Systeme integrieren können, wodurch zusätzliche Flexibilität bei der Bereitstellung entsteht.

Kunden mit großen, komplexen Katalogen oder Katalogen, die häufige Updates erhalten, befürchten, dass es länger dauern könnte, bis die neuen Daten im Live Store angezeigt werden. Da der Catalog Service weiß, welche Daten er für die Verarbeitung dieser Aktualisierungen benötigt, müssen die Daten nicht über das Commerce-Hauptprodukt gesendet werden, sondern nur an Catalog Service weitergeleitet werden. Wenn Sie diesen Zwischenschritt entfernen, werden Effizienzsteigerungen festgestellt.

## Feed-Erfassungsflüsse

Je nach Adobe Commerce-Konfiguration können Datenspeicher und Datenflüsse unterschiedliche Pfade annehmen.

* In einer standardmäßigen Adobe Commerce-Instanz wird der Produktkatalog in der Hauptdatenbank gespeichert.
* Bei Verwendung von Adobe Commerce Services werden Katalogdaten aus der Hauptdatenbank in den Dienst kopiert, dort verarbeitet und bereitgestellt.
* Beim Speichern von Katalogdaten in einem Drittanbietersystem (ERP, MDM, PIM) fließen die Daten über die zentrale Commerce-Anwendung und dann an die Commerce-Dienste.
* Mit dem Feed-Erfassungsdienst werden Produktdaten direkt vom Drittanbietersystem zur Commerce-Dienstinfrastruktur geleitet.

![Feed-Erfassungsdienst](assets/feed-ingestion.png)

Durch Umgehung der Commerce-Hauptanwendung und direktes Verschieben von Daten in die Commerce-Dienste werden Produktaktualisierungen schneller im Speicher angezeigt. Kernkatalogdaten wie SKUs werden zur getrennten Verarbeitung an die Commerce-Hauptanwendung gesendet.

## API

Die [Dokumentation zur Feed-Aufnahme-Service-API](https://developer.adobe.com/commerce/services/feed-ingestion) enthält Details zur Implementierung des Dienstes.
