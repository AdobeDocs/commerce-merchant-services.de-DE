---
title: Transaktionsbericht
description: Verwenden Sie den Transaktionsbericht, um Einblicke in die Rate der Transaktionsautorisierungen und die Transaktionstrends zu erhalten.
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 91acc6e1dfd142caca77c0dc9ba55da34f75dd60
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---

# Transaktionsbericht

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen umfassende Berichte, sodass Sie einen klaren Überblick über die Transaktionen, Bestellungen und Zahlungen Ihres Geschäfts erhalten.

![Transaktionsbericht](assets/transactions-report.png){width="700" zoomable="yes"}

Der Transaktionsbericht bietet Einblicke in die Rate der Transaktionsautorisierungen und negative Transaktionstrends, sodass Sie den Zustand Ihres Geschäfts effektiv überwachen und alle Transaktionsprobleme vorbeugend identifizieren und beheben können.

Siehe Individuelle Transaktionen für Bestellungen, die in der Storefront platziert werden, ihre Zahlungsmethoden, Ergebnisse, Zahlungsantwort-Codes und mehr.

Die im Transaktionsbericht enthaltenen Informationen sind nur für den Händlereinsatz bestimmt. Teilen Sie diese Informationen nicht mit Kunden oder anderen potenziellen Betrügern. Transaktionsinformationen können verwendet werden, um Sicherheitsprüfungen zu umgehen oder Bestellungen zu platzieren, die zu Chargebacks führen.

Sie können den Transaktionsbericht im .csv-Dateiformat herunterladen, um ihn in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware verwenden zu können.

>[!NOTE]
>
>Wenn Sie keine [integrierte und aktivierte Livemodus](production.md#enable-live-payments) für [!DNL Payment Services].

## Ansicht des Transaktionsberichts

Die Ansicht des Transaktionsberichts ist in der Ansicht &quot;Transaktionen&quot;von Zahlungsdiensten verfügbar. Sie enthält alle verfügbaren Informationen über Transaktionen für Ihre Geschäfte.

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**um die detaillierte Ansicht des Berichts Transaktionen in der Tabelle anzuzeigen.

![Ansicht des Transaktionsberichts](assets/transactions-report-detail.png){width="600" zoomable="yes"}

Sie können diese Ansicht entsprechend den Abschnitten in diesem Thema konfigurieren, um die gewünschten Daten am besten darzustellen.

Siehe verknüpfte Commerce-Bestell- und Provider-Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr, alles in diesem Bericht.

Nicht alle Zahlungsmethoden bieten die gleiche Granularität von Informationen. Kreditkartentransaktionen bieten beispielsweise Antwort-, AVS- und CSV-Codes sowie die letzten vier Ziffern der Karte im Transaktionsbericht. PayPal Smart-Schaltflächen nicht.

Sie können [Download-Transaktionen](#download-transactions) im .csv-Dateiformat zur Verwendung in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware.

### Datenquelle auswählen

In der Ansicht des Transaktionsberichts können Sie die Datenquelle auswählen.**[!UICONTROL Live]** oder **[!UICONTROL Sandbox]**- für die Sie Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Stores anzeigen, die [!DNL Payment Services] im Produktionsmodus. Wenn_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihren Sandbox-Modus anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn Sie keine Stores haben, die [!DNL Payment Services] Im Produktionsmodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Sandbox]_.
* Wenn Sie über Stores (einen oder mehrere) verfügen, die [!DNL Payment Services] Im Produktionsmodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Live]_.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihre [!UICONTROL Transactions] Bericht:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicks **[!UICONTROL Data source]** und wählen **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]**.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Datum und Zeitrahmen anpassen

In der Ansicht des Transaktionsberichts können Sie den Zeitrahmen der Transaktionen, die Sie anzeigen möchten, anpassen, indem Sie bestimmte Daten auswählen. Standardmäßig werden 30 Tage Transaktionen im Raster angezeigt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Transaction dates]** Kalenderauswahl .
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Transaktionen für die angegebenen Daten im Raster an.

### Berichtinformationen filtern

In der Ansicht des Transaktionsberichts können Sie die anzuzeigenden Statusergebnisse filtern, indem Sie Filterkriterien auswählen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Filter]** auswählen.
1. Umschalten zwischen _[!UICONTROL Transaction Result]_Optionen, um die Berichtsergebnisse nur für ausgewählte Bestellvorgänge anzuzeigen.
1. Wählen Sie die _[!UICONTROL Card Type]_, um die Berichtsergebnisse für den ausgewählten Kartentyp anzuzeigen. Eine QuickInfo mit weiteren Informationen wird angezeigt, wenn der Zahlungsverarbeiter den Kartentyp nicht identifizieren kann.
1. Wählen Sie die _[!UICONTROL Card Brand]_, um die Berichtsergebnisse für die ausgewählte Kartenmarke anzuzeigen. Eine QuickInfo mit weiteren Informationen wird angezeigt, wenn der Zahlungsverarbeiter die Kartenmarke nicht identifizieren kann.
1. Umschalten zwischen _[!UICONTROL Payment Method]_Optionen, um die Berichtsergebnisse nur für ausgewählte Zahlungsmethoden anzuzeigen.
1. Geben Sie einen _Min. Bestellbetrag_ oder _Max. Bestellbetrag_ , um die Berichtsergebnisse innerhalb dieses Bestellwertbereichs anzuzeigen.
1. Geben Sie eine _[!UICONTROL Order ID]_, um nach einer bestimmten Transaktion zu suchen.
1. Geben Sie die _[!UICONTROL Card Last Four Digits]_um nach einer bestimmten Kredit- oder Debitkarte zu suchen.
1. Klicks **[!UICONTROL Hide filters]** um den Filter auszublenden.

### Spalten ein- und ausblenden

Der Transaktionsbericht zeigt standardmäßig alle verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten in Ihrem Bericht angezeigt werden.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Column settings]** icon ![Symbol für Spalteneinstellungen](assets/column-settings.png){width="20" zoomable="yes"}.
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Der Transaktionsbericht zeigt sofort alle Änderungen an, die Sie im Menü Spalteneinstellungen vorgenommen haben. Die Spaltenvoreinstellungen werden gespeichert und bleiben in Kraft, wenn Sie von der Berichtsansicht weg navigieren.

### Berichtdaten aktualisieren

Die Ansicht des Transaktionsberichts zeigt eine _[!UICONTROL Last updated]_Zeitstempel, der das letzte Mal angibt, dass die Berichtinformationen aktualisiert wurden. Standardmäßig werden die Daten des Transaktionsberichts alle drei Stunden automatisch aktualisiert.

Sie können auch manuell eine Aktualisierung der Berichtsdaten erzwingen, um die aktuellsten Berichtinformationen anzuzeigen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf _Aktualisieren_ Symbol (![Aktualisierungssymbol](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Die Daten des Transaktionsberichts werden aktualisiert. *[!UICONTROL Update complete]* -Bestätigung angezeigt und die neuesten Informationen im Raster vorhanden sind.

### Herunterladen von Transaktionen

Sie können eine .csv -Datei mit allen Transaktionen herunterladen, die im Raster der Ansicht der Transaktionen sichtbar sind, unabhängig davon, ob Sie die standardmäßigen 30-Tage-Transaktionen oder einen benutzerdefinierten Zeitrahmen anzeigen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Wenn Sie Transaktionen für einen anderen Zeitraum als die letzten 30 Tage anzeigen möchten, [Datumsbereich-Zeitrahmen für Ihre Status anpassen](#customize-dates-timeframe).
1. Klicken Sie auf _Herunterladen_ ![Download-Symbol](assets/icon-download.png){width="20" zoomable="yes"} Symbol.

Ihre Transaktionen werden im .csv-Format heruntergeladen.

### Spaltenbeschreibungen

Transaktionsberichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce-Bestell-ID (enthält nur Werte für erfolgreiche Transaktionen und ist bei abgelehnten Transaktionen leer)<br> <br>So sehen Sie verwandte [Bestellinformationen](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}klicken Sie auf die ID. |
| [!UICONTROL Provider Transaction ID] | Vom Zahlungsdienstleister bereitgestellte Transaktions-ID, die nur Werte für erfolgreiche Transaktionen enthält und einen Bindestrich für zurückgewiesene Transaktionen enthält. |
| [!UICONTROL Transaction Date] | Transaktionsdatumszeitstempel |
| [!UICONTROL Payment Method] | Zahlungsmethode der Transaktion mit detaillierten Informationen über Marke und Kartentyp. Siehe [Kartentypen](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) für weitere Informationen, verfügbar für Zahlungsdienste-Versionen 1.6.0 und höher |
| [!UICONTROL Card Last Four Digits] | Letzte vier Stellen der Kredit- oder Debitkarten, die für die Transaktion verwendet werden |
| [!UICONTROL Result] | Das Ergebnis der Transaktion —*[!UICONTROL OK]* (erfolgreiche Transaktion), *[!UICONTROL Rejected by Payment Provider]* (abgelehnt von PayPal), *[!UICONTROL Rejected by Bank]* (von einer Bank abgelehnt, die die Karte ausgestellt hat) |
| [!UICONTROL Response Code] | Fehlercode, der den Grund für die Zurückweisung von Zahlungsdienstleistern oder Banken angibt; siehe Liste möglicher Antwortcodes und Beschreibungen für [`Rejected by Bank` status](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) und [`Rejected by Payment Provider` status](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | Adresse Verification Service-Code; die Antwortinformationen des Verarbeiters für Zahlungsanfragen. Siehe [Liste möglicher Codes und Beschreibungen](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) für weitere Informationen. |
| [!UICONTROL CVV Code] | Kartenprüfungswertcode für Kredit- und Debitkarten, siehe [Liste möglicher Codes und Beschreibungen](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) für weitere Informationen. |
| [!UICONTROL Amount] | Bestellmenge |
| [!UICONTROL Currency] | Währung, die für die Bestellung in der Transaktion verwendet wird |
| [!UICONTROL Type] | [Zahlungsaktion](../payment-services/production.md#set-payment-services-as-payment-method) für Transaktionen—`Authorize` oder `Authorize and Capture` |

### Fehler-Antwortcodes

Die _Antwortcode_ zeigt einen spezifischen Fehler- oder Erfolgscode im Zusammenhang mit der Transaktion an. Zu den gebräuchlichen Fehlercodes, die möglicherweise angezeigt werden, gehören:

* `PAYMENT_DENIED`—Transaktion wurde von PayPal abgelehnt, weil sie als Betrug vermutet wurde.
* `INTERNAL_SERVER_ERROR`—Die Transaktion wurde von PayPal abgelehnt und ein PayPal-Server-Fehler aufgetreten. Die Transaktion kann wiederholt werden.
* `INSTRUMENT_DECLINED`—Der Kunde wurde per PayPal pro ausgewählter Zahlungsmethode abgelehnt. Transaktionen können mit einer anderen Zahlungsmethode wiederholt werden.
* `9500`—Die Transaktion wurde von der verbundenen Bank abgelehnt, weil sie verdächtigt wurde, betrügerisch zu sein.
* `5120`—Die Transaktion wurde von der verbundenen Bank abgelehnt, da der Kunde nicht über ausreichende Mittel für die Zahlung verfügte.
* `5650`—Die Transaktion wurde von der verbundenen Bank abgelehnt, da die Bank eine starke Kundenauthentifizierung erfordert ([3DS](security.md#3ds)).

Detaillierte Fehlerantwort-Codes für fehlgeschlagene Transaktionen sind für Transaktionen verfügbar, die jünger als am 1. Juni 2023 sind. Teilberichtdaten werden für Transaktionen angezeigt, die vor dem 1. Juni 2023 stattgefunden haben.
