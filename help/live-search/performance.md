---
title: "Leistung"
description: '"Der Arbeitsbereich "Leistung"bietet Einblicke in die Suchbegriffe, die von Käufern verwendet werden." [!DNL Live Search] '
exl-id: ee2053fc-98c5-4d2c-9345-4d1f9a3180fb
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Leistung

Der Arbeitsbereich *Leistung* bietet Einblicke in die Suchbegriffe, die von Käufern verwendet werden. Die Informationen können verwendet werden, um Trends zu identifizieren, die Clickthrough-Rate zu erhöhen und die Konversionsrate zu verbessern. Der Arbeitsbereich &quot;Leistung&quot;bietet eine Momentaufnahme der Suchmetriken für einen bestimmten Datumsbereich und enthält die folgenden Berichte:

* Einzelsuche
* Null Ergebnisse
* Häufige Ergebnisse

![Leistung](assets/performance-unique-searches.png)

Weitere Informationen zur Datensynchronisation finden Sie auch im [Dashboard zur Datenverwaltung](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) .

## Bericht anzeigen

1. Um den **Datumsbereich** einzugeben, klicken Sie auf den Kalender (![Kalender](assets/btn-calendar.png)) und führen Sie einen der folgenden Schritte aus:

   * Um ein einzelnes Datum anzugeben, doppelklicken Sie auf das Datum im Kalender.
   * Um einen Datumsbereich festzulegen, klicken Sie auf das erste und letzte Datum im Kalender.

>[!NOTE]
>
>Der Arbeitsbereich für die Leistung wird alle 12 Stunden aktualisiert.

## Feldbeschreibungen

| Momentaufnahmen-Daten | Beschreibung |
|--- |--- |
| Einzelsuche | Die Gesamtzahl der eindeutigen Suchvorgänge für den angegebenen Datumsbereich. Mehrere Suchen desselben Käufers werden als eindeutig betrachtet, selbst wenn sie für dieselbe Abfrage im Abstand von mehr als einer Stunde gesendet werden. |
| Clickthrough-Rate | Der Prozentsatz der Suchvorgänge, die mit dem Klick auf ein Produkt abgeschlossen werden. Die Clickthrough-Rate beträgt beispielsweise 50 %, wenn der Käufer nach &quot;Hosen&quot;und &quot;Hemd&quot;sucht und dann in der &quot;Shirt&quot;-Suche auf ein Ergebnis klickt. |
| Konversionsrate | Der Prozentsatz der Produkte, die der Käufer kauft, im Vergleich zur Anzahl der Produkte, auf die der Käufer im angegebenen Datumsbereich klickt. Beispielsweise beträgt die Konversionsrate der Interaktion 100 %, wenn der Käufer sechs Produkte im Popover anzeigt, auf eins klickt und einen Kauf tätigt. <br /><br />Die Konversionsrate wird durch die Anzahl der Ansichten eines bestimmten Produkts nicht beeinflusst. Beispielsweise bleibt die Konversionsrate gleich, wenn der Käufer die Suche verwendet, aber auf keine Produkte klickt. |
| Null-Ergebnisrate | Der Prozentsatz der eindeutigen Suchen, die für den angegebenen Datumsbereich keine Ergebnisse zurückgeben. Beispielsweise beträgt die Null-Ergebnisrate 66,67 %, wenn der Käufer zweimal nach &quot;fjjajfjfjf&quot; (ohne Ergebnisse) und einmal nach &quot;pants&quot; (mit Ergebnissen) sucht. |
| Durchschn. Klickposition | Die relative Position der durchschnittlichen Clickthrough-Rate basierend auf eindeutigen Suchen für den angegebenen Datumsbereich. |

| Berichte | Beschreibung |
|--- |--- |
| Einzelsuche | Listet die eindeutigen Suchabfragen auf, die im angegebenen Datumsbereich verwendet wurden. Die Berichtsdaten werden auf die gleiche Weise wie die Daten der einzelnen Suchanzeigen berechnet. Wenn ein Käufer dieselbe Suchanfrage zweimal, aber im Abstand von mehr als einer Stunde eingibt, gilt die Suche als zwei eindeutige Suchen. Berichtslimit: Die 500 wichtigsten Begriffe |
| Null Ergebnisse | Listet die Suchabfragen auf, die keine Ergebnisse zurückgeben, sowie die Anzahl der Male, die im angegebenen Datumsbereich verwendet wurden. Berichtslimit: Die 500 wichtigsten Begriffe |
| Häufige Ergebnisse | Listet die Namen der Produkte auf, die im angegebenen Datumsbereich die meisten Ansichten erhalten haben. Die beliebten Ergebnisse werden nur anhand von Impressionen berechnet und sind nicht von der Anzahl der Klicks oder des erzielten Umsatzes betroffen. Berichtslimit: Die 500 wichtigsten Begriffe |
