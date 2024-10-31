---
title: Geschätztes Datenvolumen und Übertragungszeit
description: Erfahren Sie, wie Sie das Datenvolumen und die Übertragungszeit schätzen können, die für das [!DNL data export] Tool zur Synchronisierung von Feed-Daten zwischen Adobe Commerce und verbundenen Diensten erforderlich sind.
role: Admin, Developer
exl-id: 51ea98fd-cf90-44bd-a639-992bfc7f3eca
source-git-commit: 7e33b1d5dfc825f8a4d252bcfcbd4f591e337aed
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Schätzen des Datenvolumens und der Übertragungszeit für die Datensynchronisierung

Adobe empfiehlt die Schätzung des Datenvolumens und der Synchronisierungszeit vor Beginn der Daten-Feed-Synchronisation, um eine reibungslose Planung zu gewährleisten und Unterbrechungen bei Site-Vorgängen zu vermeiden. Diese Schätzung ist bei der Planung von anfänglichen Synchronisierungen oder umfangreichen Katalogaktualisierungen, wie z. B. Massenpreisänderungen, wichtig.

Standardmäßig verarbeitet das Datenexport-Tool Daten im Einzelthread-Modus mit einer standardmäßigen Batch-Größe. Mit der Standardkonfiguration gibt es keine Parallelisierung des Feed-Sendeprozesses. Darüber hinaus akzeptiert diese Komponente Anforderungen pro Sekunde (RPS), was Folgendes bedeutet:

- Bis zu 10.000 Produkte pro Minute, bei denen ein Produkt eine SKU mit Attributen in einem bestimmten Store ist
- Bis zu 50.000 Preise pro Minute

Die folgenden Faktoren beeinflussen die Datenübertragungszeit während der Synchronisierung.

- Die Thread-Anzahl ist auf 1 gesetzt (standardmäßig)
- Die Stapelgröße wird für alle Feeds mit Ausnahme des `prices` -Feeds auf _100_ festgelegt, wobei sie auf _500_ festgelegt ist.
- Die Akzeptanzrate des Feeds beträgt 2 Anfragen pro Sekunden.
- Alle Produkte werden allen vorhandenen Websites zugewiesen.
- Für die Preisberechnungsszenarien werden allen Produkten spezielle und gruppierte Preise zugewiesen.


## Datenübertragung pro Feed berechnen

Verwenden Sie die Werte und Formeln in der folgenden Tabelle, um das Datenvolumen und die Synchronisierungszeit für jeden Daten-Feed zu berechnen.

>[!NOTE]
>
>Diese Berechnungen basieren auf einer Übertragungsrate von 2 Anforderungen pro Sekunde. Die Geschwindigkeit basiert auf der für die Datenerfassung und Datenübermittlung erforderlichen Zeit. Die tatsächliche Übertragungsgeschwindigkeit variiert je nach Größe der Anfrage-Payload und der aktuellen Auslastung des Commerce-Anwendungsservers.

| Feed | Datenbeispiel | Formel zur Berechnung von Datensätzen | Prognostizierte Anforderungsanzahl | Vorhergesagte Synchronisierungszeit |
| --- | --- | --- | --- | --- |
| Produkte | Produkte (P): 10000, Store Views (SV): 4 | P * SV = 40000 | 40000 / Stapelgröße (100) = 400 Anforderungen | (400 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 3,3 Minuten |
| Kategorien | Kategorien (C): 500, Store-Ansichten (SV): 4 | C * SV = 2000 | 2000 / Stapelgröße (100) = 20 Anforderungen | (20 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 0,1 Minuten (4 Sekunden) |
| Preise | Produkte (P): 10000, Kundengruppen (CG): 6 (z. B. eindeutiger Preis im freigegebenen Katalog), Websites (WS): 2 | P \* WS * CG = 120000 | 120000 / Stapelgröße (500) = 240 Anfragen | (240 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 2 Minuten |
| Produktüberschreibungen | Produkte mit Berechtigungen oder im freigegebenen Katalog (P): 10000, Betroffene Kundengruppen (CG): 5, Zugewiesene Websites WS: 2 | P \* WS * CG = 100000 | 100000 / Stapelgröße (100) = 1000 Anfragen | (1000 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 8,3 Minuten |
| Produktvarianten | Varianten (untergeordnete Produkte), die konfigurierbaren Produkten (PV) zugeordnet sind: 100000 | PV = 100000 | 100000 / Stapelgröße (100) = 1000 Anfragen | (1000 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 8,3 Minuten |
| Kategorieberechtigungen | Zählung aller Kategorieberechtigungen + 4 Fallback-Datensätze (CP): 10000 | KP = 10000 | 10000 / Stapelgröße (100) = 100 Anforderungen | (100 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 0,8 Minuten (50 Sekunden) |
| Lagerbestandsstatus | Produkte (P): 10000, Lagerprodukte für (S): 5 (vorausgesetzt, jedes Produkt ist jedem Lager zugeordnet) | P * S = 50000 | 50000 / Stapelgröße (100) = 500 Anforderungen | (500 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 4,2 Minuten |
| Verkaufsaufträge | Alle Auftragsunterlagen (einschließlich Rechnungen, Sendungen usw.) (SO): 10000 | SO = 10000 | 10000 / Stapelgröße (100) = 100 Anforderungen | (100 Anforderungen * 0,5 Sekunden pro Anforderung) / 60 = 0,8 Minuten (50 Sekunden) |
