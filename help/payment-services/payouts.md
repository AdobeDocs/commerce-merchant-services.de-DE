---
title: Payouts-Bericht
description: Verwenden Sie den Bericht "Auszahlungen", um vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung zu erhalten.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 0%

---

# Payouts-Bericht

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen umfassende Berichte, sodass Sie einen klaren Überblick über die Transaktionen, Bestellungen und Zahlungen Ihres Geschäfts erhalten.

Es gibt zwei verfügbare Ansichten zur Payouts-Berichterstellung, mit denen Sie detaillierte Informationen zu all Ihren Auszahlungen anzeigen können:

* **[Ansicht der Payouts-Daten-Visualisierung](#payouts-data-visualization-view)**—Auf der Zahlungsdienst-Startseite verfügbares Diagramm, das eine visuelle Darstellung der aggregierten Beträge pro Tag in der Ansicht des Payouts-Berichts darstellt.
* **[Ansicht des Berichts &quot;Payouts&quot;](#payouts-report-view)** - In Payouts verfügbarer Bericht mit detaillierten Payout-Informationen für alle Transaktionen

Die Payouts-Ansichten zeigen umfassende Auszahlungsinformationen auf einen Blick, sodass Sie vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung erhalten.

Sie können [Zahlungsvorgänge herunterladen](#download-transactions) und diese im .csv-Dateiformat in der bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware verwenden.

>[!NOTE]
>
>Payouts-Berichte zeigen nur Bestellungen an, die erfasst werden (Zahlungsaktion ist auf [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method) festgelegt) - oder [ als `Invoiced`](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) markiert sind.

## Ansicht der Payouts-Daten

Die Ansicht Payouts-Daten-Visualisierung ist auf der Zahlungsdienst-Startseite verfügbar. Es handelt sich um eine visuelle Darstellung der aggregierten Beträge pro Tag aus der detaillierten Tabelle [Ansicht des Berichts &quot;Payouts&quot;](#payouts-report-view).

Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** , um das Datenvisualisierungsdiagramm der Gutschriften und Lastschriften sowie die sich bewegenden Durchschnittswerte im Zeitverlauf anzuzeigen.

![Payout-Datenvisualisierung in Admin](assets/payouts-report.png){width="800" zoomable="yes"}

Klicken Sie auf **[!UICONTROL View Report]** , um zur detaillierten Tabelle [Ansicht des Berichts &quot;Payouts&quot;zu navigieren.](#payouts-report-view)

### Zeitrahmen für Transaktionen anpassen

Standardmäßig werden Transaktionen mit einer Dauer von 30 Tagen angezeigt.

In der Ansicht Payouts-Datenvisualisierung können Sie den Zeitrahmen für die Payout-Transaktionen, die Sie anzeigen möchten, anpassen, indem Sie einen Datumsbereich auswählen:

1. Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Ansicht für die Payouts-Datenvisualisierung ist im Abschnitt Payouts sichtbar.
1. Klicken Sie auf den Auswahlfilter **[!UICONTROL Range]** .
1. Wählen Sie den entsprechenden Datumsbereich aus: 30 Tage, 15 Tage oder 7 Tage.
1. Zeigen Sie die Transaktionsinformationen für Ihre angegebenen Daten an.

### Transaktionsinformationen

Die Transaktionsbeträge für einen ausgewählten Datumsbereich werden links in der Ansicht Payouts-Datenvisualisierung angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn an einem bestimmten Datum keine Auszahlungen erfolgte, wird dieses Datum nicht angezeigt.

Die Ansicht Payouts-Datenvisualisierung enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Datumsbereich für Transaktionen im angegebenen Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitraum; Daten auf der X-Achse (unten) |
| Kredit | Zahlungen für den angegebenen Zeitraum |
| Schulden | Forderungen (Erstattungen) für den festgelegten Zeitraum |
| anpassbarer Durchschnittswert | Darstellung der durchschnittlichen Auszahlung für jedes Datum im angegebenen Zeitrahmen |
| Netto für Bereich | Nettoauszahlungsbetrag für den angegebenen Zeitraum (Bereich) |

## Ansicht des Payload-Berichts

Die Ansicht des Berichts &quot;Payouts&quot;ist in der Ansicht &quot;Payouts&quot;der Zahlungsdienste verfügbar. Sie enthält alle verfügbaren Informationen über die Auszahlungen für Ihre Geschäfte.

Wechseln Sie in der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**, um die detaillierte Ansicht des Berichts &quot;Payouts&quot;anzuzeigen.

![Zahlungsvorgänge im Admin](assets/payouts-report-new.png){width="800" zoomable="yes"}

Sie können diese Ansicht entsprechend den Abschnitten in diesem Thema konfigurieren, um die gewünschten Daten am besten darzustellen.

Siehe verknüpfte Commerce-Bestell- und Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr, die alle in diesem Bericht enthalten sind.

Sie können [Zahlungsvorgänge herunterladen](#download-transactions) und diese im .csv-Dateiformat in der bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware verwenden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden standardmäßig mit dem Wert `TRANS DATE` in absteigender Reihenfolge (`DESC`) sortiert. Der `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion initiiert wurde.

### Datenquelle auswählen

In der Ansicht des Payouts-Berichts können Sie die Datenquelle **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]** auswählen, für die Sie die Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Stores im Produktionsmodus anzeigen. Wenn_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie die Berichtinformationen im Sandbox-Modus anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn keine Stores im Livemodus vorhanden sind, wird standardmäßig die Datenquelle &quot;_[!UICONTROL Sandbox]_&quot; ausgewählt.
* Wenn Sie im Livemodus über Stores (einen oder mehrere) verfügen, wird standardmäßig _[!UICONTROL Live]_als Datenquelle ausgewählt.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihren Bestellzahlstatus-Bericht aus:

1. Wechseln Sie auf der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Data source]** und wählen Sie **[!UICONTROL Live]** oder **[!UICONTROL Sandbox]** aus.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Transaktionen anzeigen

Standardmäßig werden Transaktionen mit einer Dauer von 30 Tagen angezeigt.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder in den standardmäßigen 30-Tage-Transaktionen angezeigt werden, wird über dem Raster der Payouts-Ansicht neben dem Filter für die Kalenderauswahl für Transaktionsinformationen angezeigt.

Scrollen Sie nach links und rechts, um im täglichen Bericht [Informationen zu den einzelnen Auszahlungstransaktionen](#column-descriptions) anzuzeigen, einschließlich Transaktionsdatum, Referenz-ID, Rechnungsnummer und Zahlungsmethodendetails.

#### Zeitrahmen für Transaktionen anpassen

In der Ansicht des Payouts-Berichts können Sie den Zeitrahmen für die Payout-Transaktionen anpassen, die Sie anzeigen möchten, indem Sie bestimmte Daten eingeben oder einen Datumsbereich in der Datumsauswahl auswählen:

1. Wechseln Sie auf der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf den Kalender-Auswahlfilter _[!UICONTROL Transaction dates]_.
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Payouts-Status im Raster für Ihre angegebenen Daten an.

### Spalten ein- und ausblenden

Die Ansicht des Payouts-Berichts zeigt standardmäßig die meisten verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten im Bericht angezeigt werden.

1. Wechseln Sie auf der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf das Symbol _Spalteneinstellungen_ (![Spalteneinstellungssymbol](assets/column-settings.png){width="20" zoomable="yes"}).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   In der Ansicht des Berichts &quot;Payouts&quot;werden alle Änderungen, die Sie im Menü &quot;Spalteneinstellungen&quot;vorgenommen haben, sofort angezeigt. Die Spaltenvoreinstellungen werden gespeichert und bleiben in Kraft, wenn Sie von der Berichtsansicht weg navigieren.

### Herunterladen von Transaktionen

Sie können eine CSV-Datei herunterladen, die alle im Raster Ansicht der Payouts sichtbaren Transaktionen enthält.

1. Wechseln Sie auf der Seitenleiste _Admin_ zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. [Passen Sie den Zeitrahmen des Datumsbereichs für Ihre Transaktionen an](#customize-transactions-timeframe).
1. Klicken Sie auf das Symbol _Download_ (![](assets/icon-download.png){width="20" zoomable="yes"}).

Ihre Zahlungsvorgänge werden im .csv-Format heruntergeladen.

### Spaltenbeschreibungen

Payout-Berichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Zahlungsdienstleister |
| [!UICONTROL Provider trans] | Transaktions-ID |
| [!UICONTROL Trans date] | Datum und Uhrzeit der Initiierung der Transaktion |
| [!UICONTROL Type] | Transaktionstyp -*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Weitere Informationen finden Sie unter [Transaktionstypen](#transaction-types) . |
| [!UICONTROL Status] | Aktueller Status der Transaktion—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaktionscode, der entweder Guthaben (*CR*) oder Schulden (*DR*) angibt |
| [!UICONTROL Reference ID] | Ursprüngliche Transaktions-ID, mit der dieses Ereignis verknüpft ist |
| [!UICONTROL Invoice] | Rechnungskennung (eine pro Bestellung) der Transaktion |
| [!UICONTROL Commerce order] | Commerce-Bestell-ID <br> <br>Um verwandte [Bestellinformationen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders) anzuzeigen, klicken Sie auf die ID. |
| [!UICONTROL Commerce trans] | Commerce-Transaktions-ID |
| [!UICONTROL Pay method] | Kreditkartentyp -*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* - und der zugehörige Kartenanbieter (z. B. *Visa* oder *MasterCard*) |
| [!UICONTROL TRANS AMT] | Transaktionsbetrag |
| [!UICONTROL CUR] | Währungseinheit für Transaktionsbetrag |
| [!UICONTROL PENDING] | Noch auszuzahlender Betrag |
| [!UICONTROL CUR] | Währungseinheit für den ausstehenden Betrag |
| [!UICONTROL SELLER AMT] | Betrag der an einen Kunden oder von ihm übertragenen Mittel <br> <br>Für aus dem Verkäuferkonto ausgehende Fonds wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL CUR] | Währungseinheit für den Verkäuferbetrag |
| [!UICONTROL PARTNER FEE] | Mit der Transaktion verbundene Partnergebühren <br> <br>Für Fonds, die aus dem Partnergebührenkonto aussteigen, wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL CUR] | Währungseinheit für die Partnergebühr |
| [!UICONTROL PROV FEES] | Gebühren für die Transaktion <br> <br>Für Fonds, die aus dem Gebührenkonto des Providers aussteigen, wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL CUR] | Währungseinheit für die Provider-Gebühr |
| [!UICONTROL FEE %] | Prozentsatz des Transaktionsbetrags, der als Gebühr in Rechnung gestellt wird |
| [!UICONTROL FIXED FEE] | Feste Anbietergebühr |
| [!UICONTROL CHBK FEE] | Chargeback-Gebühr für die Transaktion <br> <br>Ein Dash-Präfix (-) zeigt an, dass die Chargeback-Gebühr umgekehrt wurde. |
| [!UICONTROL CUR] | Währungseinheit für die Chargeback-Gebühr |
| [!UICONTROL HOLD AMT] | Betrag, der ausgesetzt oder aus dem Laderaum freigelassen wurde <br> <br>Ein Bindestrich (-)-Präfix gibt an, dass auf Eignungsniveau befindliche Mittel freigegeben werden. |
| [!UICONTROL CUR] | Währungseinheit für den Halten-Betrag |
| [!UICONTROL RECOUP AMT] | Aus dem Konto eingezogener Betrag <br> <br>Für aus dem Konto ausgehende Fonds wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL CUR] | Währungseinheit für den Rückforderungsbetrag |

### Transaktionsarten

Diese Transaktionstypen können in den Auszahlungstransaktionen vermerkt werden.

| Bericht | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Geld wechselt zwischen einem Käufer und einem Verkäufer für eine Bestellung |
| [!UICONTROL AUTH] | Nichterfüllung der Zulassung und Genehmigung |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Chargeback-Gebühr und Chargeback-Gebühr-Umrechnungstransaktionen |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Partnergebühren, Zahlungsgebühren und umkehrende Gebühren |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Einzüge aus Bank- oder Verlustkonten |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
