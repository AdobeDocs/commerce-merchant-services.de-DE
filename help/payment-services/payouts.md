---
title: Zahlungsbericht
description: Verwenden Sie den Bericht "Auszahlungen", um vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung zu erhalten.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: aff1a43fedab473b84d02068a7d3fbd33b4fe093
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# Zahlungsbericht

[!DNL Payment Services] für Adobe Commerce und Magento Open Source bietet Ihnen umfassende Berichte, sodass Sie einen klaren Überblick über die Bestellungen und Zahlungen Ihres Geschäfts erhalten.

![Übersicht über die Finanzberichte](assets/reports-view.png)

Der Bericht zu den Auszahlungen zeigt umfassende Auszahlungsinformationen auf einen Blick, sodass Sie vollständige Transparenz in Bezug auf den Zahlungsbetrag, das verarbeitete Volumen und detaillierte Berichte über die Transaktionsstufe zur finanziellen Abstimmung erhalten.

Sie müssen nicht mehrere Dashboards oder Ansichten öffnen, um Bestellungen und Zahlungen zu vergleichen oder Konten abzustimmen. [!DNL Payment Services] für Adobe Commerce und Magento Open Source können Sie all diese Aktionen von einem Ort aus - dem Payouts-Bericht - ausführen, damit Sie Ihre Payouts effizient anzeigen und verwalten können.

Weitere Informationen finden Sie unter verknüpfte Commerce-Bestell- und Transaktions-IDs, Transaktionsbeträge, Zahlungsmethoden pro Transaktion und mehr im Payouts-Bericht in der Admin-Rubrik.

Sie können Zahlungsvorgänge im .csv-Dateiformat herunterladen, um sie in der bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `TRANS DATE`. Die `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion eingeleitet wurde.

## Verfügbarkeit

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![Zahlungsvorgänge im Admin](assets/payouts-report.png)

## Datenquelle auswählen

In der Ansicht des Payouts-Berichts können Sie die Datenquelle auswählen._[!UICONTROL Live]_oder [!UICONTROL Sandbox]_—für die Sie Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png)

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Live Stores anzeigen. Wenn [!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Sandbox-Umgebung anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn keine Stores im Livemodus vorhanden sind, wird bei der Auswahl der Datenquelle standardmäßig [!UICONTROL Sandbox]_.
* Wenn Sie im Livemodus über Speicher (einen oder mehrere) verfügen, wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Live]_.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihren Bestellzahlstatus-Bericht aus:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicken **[!UICONTROL Data source]** und wählen Sie _[!UICONTROL Live]_oder [!UICONTROL Sandbox]_.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

## Transaktionen anzeigen

Standardmäßig werden 30 Tage Transaktionen im Raster angezeigt.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder in den standardmäßigen 30-Tage-Transaktionen angezeigt werden, wird über dem Raster der Payouts-Ansicht neben dem Filter für die Kalenderauswahl für Transaktionsinformationen angezeigt.

Scrollen Sie nach links und rechts, um [Informationen zu den einzelnen Auszahlungstransaktionen](#column-descriptions) im täglichen Bericht, einschließlich Transaktionsdatum, Referenz-ID, Rechnungsnummer und Zahlungsmethodendetails.

### Zeitrahmen für Transaktionen anpassen

In der Ansicht &quot;Payouts&quot;können Sie den Zeitrahmen für die Payout-Transaktionen anpassen, die Sie anzeigen möchten, indem Sie bestimmte Daten eingeben oder einen Datumsbereich in der Datumsauswahl auswählen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicken Sie auf den Filter Kalenderauswahl für Transaktionsdaten .
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Payouts-Status im Raster für Ihre angegebenen Daten an.

## Herunterladen von Transaktionen

Sie können eine CSV-Datei herunterladen, die alle im Raster Ansicht der Payouts sichtbaren Transaktionen enthält.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Zeitrahmen für den Datumsbereich Ihrer Transaktionen anpassen](#customize-transactions-timeframe).
1. Klicken Sie auf _Download_ (![](assets/icon-download.png)).

Ihre Zahlungsvorgänge werden im .csv-Format heruntergeladen.

## Transaktionsinformationen

Die Payouts-Ansicht zeigt umfassende Informationen für jede Transaktion an, die im Raster angezeigt wird.

### Spaltenbeschreibungen

Payout-Berichte enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Zahlungsdienstleister |
| [!UICONTROL Provider trans] | Transaktions-ID |
| [!UICONTROL Trans date] | Datum und Uhrzeit der Initiierung der Transaktion |
| [!UICONTROL Type] | Transaktionstyp—*[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Siehe [Transaktionstypen](#transaction-types) für weitere Informationen. |
| [!UICONTROL Status] | Aktueller Status der Transaktion—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaktionscode, der entweder einen Kredit (*CR*) oder Schulden (*DR*) |
| [!UICONTROL Reference ID] | Ursprüngliche Transaktions-ID, mit der dieses Ereignis verknüpft ist |
| [!UICONTROL Invoice] | Rechnungskennung (eine pro Bestellung) der Transaktion |
| [!UICONTROL Commerce order] | Commerce-Bestell-ID <br> <br>So sehen Sie verwandte [Bestellinformationen](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, klicken Sie auf die ID. |
| [!UICONTROL Commerce trans] | Transaktions-ID <br> <br>So sehen Sie verwandte [Transaktionsinfo](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, klicken Sie auf die ID. |
| [!UICONTROL Pay method] | Kreditkartenart—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*- und dem zugehörigen Kartenanbieter (z. B. *Visagebühren* oder *MasterCard*) |
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
