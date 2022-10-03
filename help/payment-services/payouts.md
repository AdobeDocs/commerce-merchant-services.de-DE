---
title: Zahlungsbericht
description: Verwenden Sie den Bericht "Auszahlungen", um vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung zu erhalten.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 39c0140961fa9de5075087bbc3fbec0e14560860
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 0%

---

# Zahlungsbericht

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen eine umfassende Berichterstellung, damit Sie einen klaren Überblick über die Bestellungen und Zahlungen Ihres Geschäfts erhalten.

![Übersicht über die Finanzberichte](assets/report-view.png)

Es gibt zwei verfügbare Ansichten zur Payouts-Berichterstellung, mit denen Sie detaillierte Informationen zu all Ihren Auszahlungen anzeigen können:

* **[Ansicht der Payouts-Daten](#payouts-data-visualization-view)**—Auf der Zahlungsdienst-Startseite verfügbares Diagramm, das eine visuelle Darstellung der aggregierten Beträge pro Tag in der Ansicht des Payouts-Berichts darstellt
* **[Ansicht des Payload-Berichts](#payouts-report-view)**—Bericht verfügbar unter &quot;Auszahlungen&quot;, der detaillierte Payout-Informationen für alle Transaktionen anzeigt

Die Payouts-Ansichten zeigen umfassende Auszahlungsinformationen auf einen Blick, sodass Sie vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung erhalten.

>[!NOTE]
>
>Payouts-Berichte zeigen nur erfasste Bestellungen an (Zahlungsaktion ist auf [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method)) - oder [markiert als `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## Ansicht der Payouts-Daten

Die Ansicht Payouts-Daten-Visualisierung ist auf der Zahlungsdienst-Startseite verfügbar. Es handelt sich um eine visuelle Darstellung der aggregierten Beträge pro Tag aus der detaillierten Tabelle [Ansicht des Payload-Berichts](#payouts-report-view).

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** um das Datenvisualisierungs-Diagramm von Gutschriften im Vergleich zu Lastschriften und die sich bewegenden Durchschnittswerte im Zeitverlauf anzuzeigen.

![Payout-Datenvisualisierung in Admin](assets/payouts-report.png)

Klicken **[!UICONTROL View Report]** zur detaillierten Tabelle navigieren [Ansicht des Payload-Berichts](#payouts-report-view).

### Zeitrahmen für Transaktionen anpassen

Standardmäßig werden Transaktionen mit einer Dauer von 30 Tagen angezeigt.

In der Ansicht Payouts-Datenvisualisierung können Sie den Zeitrahmen für die Payout-Transaktionen, die Sie anzeigen möchten, anpassen, indem Sie einen Datumsbereich auswählen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Ansicht für die Payouts-Datenvisualisierung ist im Abschnitt Payouts sichtbar.
1. Klicken Sie auf **[!UICONTROL Range]** Auswahlfilter.
1. Wählen Sie den entsprechenden Datumsbereich aus: 30 Tage, 15 Tage oder 7 Tage.
1. Zeigen Sie die Transaktionsinformationen für Ihre angegebenen Daten an.

### Transaktionsinformationen

Die Transaktionsbeträge für einen ausgewählten Datumsbereich werden links in der Ansicht Payouts-Datenvisualisierung angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn an einem bestimmten Datum keine Auszahlungen erfolgte, wird dieses Datum nicht angezeigt.

Die Ansicht Payouts-Datenvisualisierung enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Betrag für Transaktionen im festgelegten Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitraum; Daten auf der X-Achse (unten) |
| Kredit | Zahlungen für den angegebenen Zeitraum |
| Schulden | Forderungen (Erstattungen) für den festgelegten Zeitraum |
| anpassbarer Durchschnittswert | Darstellung der durchschnittlichen Auszahlung für jedes Datum im angegebenen Zeitrahmen |
| Netto für Bereich | Nettoauszahlungsbetrag für den angegebenen Zeitraum (Bereich) |

## Ansicht des Payload-Berichts

Die Ansicht des Berichts &quot;Payouts&quot;ist in der Ansicht &quot;Payouts&quot;der Zahlungsdienste verfügbar. Sie enthält alle verfügbaren Informationen über die Auszahlungen für Ihre Geschäfte. Die [Ansicht der Payouts-Daten](#payouts-data-visualization-view) in der Zahlungsdienst-Startseite ist eine visuelle Darstellung der aggregierten Beträge pro Tag in dieser detaillierteren Berichtsansicht.

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** um die detaillierte Tabellenansicht des Berichts &quot;Payouts&quot;anzuzeigen.

![Zahlungsvorgänge im Admin](assets/payouts-report-new.png)

Sie können diese Ansicht entsprechend den Abschnitten in diesem Thema konfigurieren, um die gewünschten Daten am besten darzustellen.

Weitere Informationen finden Sie unter verknüpfte Commerce-Bestell- und Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr im Payouts-Bericht in der Admin-Rubrik.

Sie können Zahlungsvorgänge im .csv-Dateiformat herunterladen, um sie in der bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `TRANS DATE`. Die `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion eingeleitet wurde.

### Datenquelle auswählen

In der Ansicht des Payouts-Berichts können Sie die Datenquelle auswählen._[!UICONTROL Live]_oder_[!UICONTROL Sandbox]_- für die Sie Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png)

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Live Stores anzeigen. Wenn [!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Sandbox-Umgebung anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn keine Stores im Livemodus vorhanden sind, wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Sandbox]_.
* Wenn Sie im Livemodus über Speicher (einen oder mehrere) verfügen, wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Live]_.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihren Bestellzahlstatus-Bericht aus:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicken **[!UICONTROL Data source]** und wählen Sie _[!UICONTROL Live]_oder_[!UICONTROL Sandbox]_.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Transaktionen anzeigen

Standardmäßig werden Transaktionen mit einer Dauer von 30 Tagen angezeigt.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder in den standardmäßigen 30-Tage-Transaktionen angezeigt werden, wird über dem Raster der Payouts-Ansicht neben dem Filter für die Kalenderauswahl für Transaktionsinformationen angezeigt.

Scrollen Sie nach links und rechts, um [Informationen zu den einzelnen Auszahlungstransaktionen](#column-descriptions) im täglichen Bericht, einschließlich Transaktionsdatum, Referenz-ID, Rechnungsnummer und Zahlungsmethodendetails.

#### Zeitrahmen für Transaktionen anpassen

In der Ansicht des Payouts-Berichts können Sie den Zeitrahmen für die Payout-Transaktionen anpassen, die Sie anzeigen möchten, indem Sie bestimmte Daten eingeben oder einen Datumsbereich in der Datumsauswahl auswählen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicken Sie auf den Filter Kalenderauswahl für Transaktionsdaten .
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Payouts-Status im Raster für Ihre angegebenen Daten an.

### Spalten ein- und ausblenden

Die Ansicht des Payouts-Berichts zeigt standardmäßig die meisten verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten im Bericht angezeigt werden.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Klicken Sie auf _Spalteneinstellungen_ Symbol (![Symbol für Spalteneinstellungen](assets/column-settings.png)).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   In der Ansicht des Berichts &quot;Payouts&quot;werden alle Änderungen, die Sie im Menü &quot;Spalteneinstellungen&quot;vorgenommen haben, sofort angezeigt. Die Spaltenvoreinstellungen werden gespeichert und bleiben in Kraft, wenn Sie von der Berichtsansicht weg navigieren.

### Herunterladen von Transaktionen

Sie können eine CSV-Datei herunterladen, die alle im Raster Ansicht der Payouts sichtbaren Transaktionen enthält.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Zeitrahmen für den Datumsbereich Ihrer Transaktionen anpassen](#customize-transactions-timeframe).
1. Klicken Sie auf _Download_ (![](assets/icon-download.png)).

Ihre Zahlungsvorgänge werden im .csv-Format heruntergeladen.

### Spaltenbeschreibungen

Payout-Berichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Zahlungsdienstleister |
| [!UICONTROL Provider trans] | Transaktions-ID |
| [!UICONTROL Trans date] | Datum und Uhrzeit der Initiierung der Transaktion |
| [!UICONTROL Type] | Transaktionstyp—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Siehe [Transaktionstypen](#transaction-types) für weitere Informationen. |
| [!UICONTROL Status] | Aktueller Status der Transaktion—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaktionscode, der entweder einen Kredit (*CR*) oder Schulden (*DR*) |
| [!UICONTROL Reference ID] | Ursprüngliche Transaktions-ID, mit der dieses Ereignis verknüpft ist |
| [!UICONTROL Invoice] | Rechnungskennung (eine pro Bestellung) der Transaktion |
| [!UICONTROL Commerce order] | Commerce-Bestell-ID <br> <br>So sehen Sie verwandte [Bestellinformationen](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, klicken Sie auf die ID. |
| [!UICONTROL Commerce trans] | Transaktions-ID <br> <br>So sehen Sie verwandte [Transaktionsinfo](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, klicken Sie auf die ID. |
| [!UICONTROL Pay method] | Kreditkartenart—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL APPLE_PAY]*, *[!UICONTROL CREDIT_CARD]*- und dem zugehörigen Kartenanbieter (z. B. *Visagebühren* oder *MasterCard*) |
| [!UICONTROL Trans amt] | Transaktionsbetrag |
| [!UICONTROL Cur] | Währungseinheit für Transaktionsbetrag |
| [!UICONTROL Pending] | Noch auszuzahlender Betrag |
| [!UICONTROL Cur] | Währungseinheit für den ausstehenden Betrag |
| [!UICONTROL Seller amt] | Geldbetrag, der an einen Kunden oder von einem Kunden übertragen wird <br> <br>Fonds, die aus dem Verkaufskonto aussteigen, weisen ein Bindestrich (-)-Präfix auf. |
| [!UICONTROL Cur] | Währungseinheit für den Verkäuferbetrag |
| [!UICONTROL Partner fee] | Mit der Transaktion verbundene Partnergebühren <br> <br>Für Fonds, die aus dem Partnergebührenkonto aussteigen, wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL Cur] | Währungseinheit für die Partnergebühr |
| [!UICONTROL Prov fees] | Mit der Transaktion verbundene Gebühren <br> <br>Für Fonds, die aus dem Gebührenkonto des Providers aussteigen, wird ein Bindestrich (-)-Präfix angezeigt. |
| [!UICONTROL Cur] | Währungseinheit für die Provider-Gebühr |
| [!UICONTROL Fee %] | Prozentsatz des als Gebühr in Rechnung gestellten Transaktionsbetrags |
| [!UICONTROL Fixed fee] | Feste Anbietergebühr |
| [!UICONTROL Chbk fee] | Chargeback-Gebühr im Zusammenhang mit der Transaktion <br> <br>Ein Bindestrich (-)-Präfix zeigt an, dass die Chargeback-Gebühr umgekehrt wurde. |
| [!UICONTROL Cur] | Währungseinheit für die Chargeback-Gebühr |
| [!UICONTROL Hold amt] | Auf Lager gehaltene oder aus dem Wartezustand freigegebene Menge <br> <br>Ein Bindestrich (-)-Präfix gibt an, dass auf Eis gelegene Mittel freigegeben werden. |
| [!UICONTROL Cur] | Währungseinheit für den Halten-Betrag |
| [!UICONTROL Recoup amt] | Aus dem Konto eingezogener Betrag <br> <br>Bei aus dem Konto ausgehenden Fonds wird ein Bindestrich (-) vorangestellt. |
| [!UICONTROL Cur] | Währungseinheit für den Rückforderungsbetrag |

### Transaktionstypen

Diese Transaktionstypen können in den Auszahlungstransaktionen angegeben werden.

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
