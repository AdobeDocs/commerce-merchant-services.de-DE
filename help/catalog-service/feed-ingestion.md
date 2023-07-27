---
title: Feed-Erfassungsdienst
description: Erfahren Sie mehr über den Feed-Erfassungsdienst für Adobe Commerce
source-git-commit: 12b1e89924a2eb89494bcb884fc3bc14e87b2b1c
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Feed-Erfassungsdienst

>[!NOTE]
>
>Der Feed-Erfassungsdienst befindet sich derzeit in der privaten Beta-Phase. Es ist noch nicht für die allgemeine Anwendung verfügbar.

Der Feed-Erfassungsdienst verkürzt die Zeit für die Verarbeitung von Produktänderungen (Preisaktualisierungen, Hinzufügen neuer Attribute), indem die Adobe Commerce-Instanz umgangen und Katalogdaten von einer externen Enterprise Resource Planning (ERP) direkt zu Adobe Commerce-Diensten verschoben werden.

Dieser Dienst richtet sich an Kunden, die ihren Produktkatalog in einem außerhalb der Adobe Commerce-Hauptanwendung gelegenen System speichern und verwalten.

Kunden mit großen, komplexen Katalogen oder Katalogen, die häufige Updates erhalten, befürchten, dass es länger dauern könnte, bis die neuen Daten im Live Store angezeigt werden. Da der Catalog Service weiß, welche Daten er für die Verarbeitung dieser Aktualisierungen benötigt, müssen die Daten nicht über das Commerce-Hauptprodukt gesendet werden, sondern nur an Catalog Service weitergeleitet werden. Wenn Sie diesen Zwischenschritt entfernen, werden Effizienzsteigerungen festgestellt.

## Feed-Erfassungsflüsse

Je nach Adobe Commerce-Konfiguration können Datenspeicher und Datenflüsse unterschiedliche Pfade annehmen.

* In einer standardmäßigen Adobe Commerce-Instanz wird der Produktkatalog in der Hauptdatenbank gespeichert.
* Bei Verwendung von Adobe Commerce Services werden Katalogdaten aus der Hauptdatenbank in den Dienst kopiert, dort verarbeitet und bereitgestellt.
* Beim Speichern von Katalogdaten in einem Drittanbietersystem (ERP, MDM, PIM) fließen die Daten über die zentrale Commerce-Anwendung und dann an die Commerce-Dienste.
* Mit dem Feed-Erfassungsdienst werden Produktdaten direkt vom Drittanbietersystem zur Commerce-Dienstinfrastruktur geleitet.

![Feed-Erfassungsdienst](assets/feed-ingestion.png)

Durch Umgehung der Commerce-Hauptanwendung und direktes Verschieben von Daten in die Commerce-Dienste werden Produktaktualisierungen schneller im Speicher angezeigt. Kernkatalogdaten wie SKUs werden zur getrennten Verarbeitung an die Commerce-Hauptanwendung gesendet.

## Betaversion

Der Feed-Erfassungsdienst wurde für Folgendes entwickelt:

* Unternehmensmäßige Kunden mit Headless-Implementierungen
* Kunden mit großen, komplexen Katalogen
* Kunden, die zum Verwalten von Katalogdaten nicht den Adobe Commerce Admin verwenden, sondern ein ERP- oder Drittanbietersystem zur Verwaltung von Katalogdaten verwenden

Wenn Sie Interesse haben, am Betaprogramm teilzunehmen, wenden Sie sich bitte unter sagonzal@adobe.com an das Team.
