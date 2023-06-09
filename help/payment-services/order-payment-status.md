---
title: Bestellstatusbericht
description: Verwenden Sie den Bestellstatusbericht, um mehr über den Zahlungsstatus Ihrer Bestellungen zu erfahren und potenzielle Probleme zu identifizieren.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 8295b7c4ea407f0528d6be69655a8b12f7defe15
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 0%

---

# Bestellstatusbericht

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen eine umfassende Berichterstellung, damit Sie einen klaren Überblick über die Bestellungen und Zahlungen Ihres Geschäfts erhalten.

Es gibt zwei verfügbare Ansichten zum Bestellstatus, mit denen Sie schnell den Zahlungsstatus Ihrer Bestellungen anzeigen können:

* **[Visualisierung des Bestellstatus](#order-payment-status-data-visualization-view)**—Auf der Zahlungsdienst-Startseite verfügbares Diagramm, das eine visuelle Darstellung des aggregierten Zahlungsstatus pro Tag in der Ansicht des Bestellstatus-Berichts darstellt
* **[Berichtansicht zum Bestellstatus](#order-payment-status-report-view)**—Bericht verfügbar im Bestellstatus, der detaillierte Zahlungs-, Fakturierungs-, Versand-, Erstattungs- und Streitstatusangaben für alle Transaktionen anzeigt

Mit den Statusansichten für die Bestellzahlung können Sie leicht erkennen, wo sich eine bestimmte Bestellung innerhalb des Bestellablaufs befindet. Diese Berichte ermöglichen es Ihnen, Bestellungen schnell anzuzeigen - basierend auf ihrem Zahlungsstatus und Zahlungsdatum - und potenzielle Probleme zu identifizieren.

Sie können Bestellungsstatustransaktionen im .csv-Dateiformat herunterladen, um sie in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware zu verwenden.

>[!NOTE]
>
>Sie können keine Finanzberichte anzeigen, wenn Sie [integrierte und aktivierte Livemodus](production.md#enable-live-payments) für [!DNL Payment Services].

## Datenvisualisierung zum Bestellstatus

Die Visualisierung der Daten zum Bestellstatus ist auf der Zahlungsdienst-Startseite verfügbar. Es handelt sich um eine visuelle Darstellung des aggregierten tägliche Zahlungsstatus aus der detaillierten Tabelle [Berichtansicht zum Bestellstatus](#order-payment-status-report-view).

Im _Admin_ Seitenleiste, navigieren Sie zu **Vertrieb** > **Zahlungsdienste** um die Datenvisualisierung anzuzeigen [Grafik des Zahlungsstatus](#statuses-information).

![Payout-Datenvisualisierung in Admin](assets/orderpayment-dataviz.png){zoomable=yes}

Klicken **Bericht anzeigen** zur detaillierten Tabelle navigieren [Berichtansicht zum Bestellstatus](#order-payment-status-report-view).

### Zeitrahmen für Status anpassen

Standardmäßig werden 30 Tage Zahlungsstatus angezeigt.

In der Visualisierung des Bestellstatus können Sie den Zeitrahmen für die Zahlungsstatus, die Sie anzeigen möchten, anpassen, indem Sie einen Datumsbereich auswählen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Visualisierung der Daten zum Bestellzahlungsstatus wird im Abschnitt Bestellzahlstatus angezeigt.
1. Klicken Sie auf **[!UICONTROL Range]** Auswahlfilter.
1. Wählen Sie den entsprechenden Datumsbereich aus: 30 Tage, 15 Tage oder 7 Tage.
1. Zeigen Sie die Statusinformationen für die angegebenen Daten an.

### Statusinformationen

Die Zahlungsstatus für einen ausgewählten Datumsbereich werden links in der Datenvisualisierung Bestellstatus-Daten angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn an einem bestimmten Datum keine Bestellungen eingegangen sind, wird dieses Datum nicht angezeigt.

Die Datenvisualisierung zum Bestellstatus enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Umfang der Bestellungen im angegebenen Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitraum; Daten auf der X-Achse (unten) |
| Autorisiert | Auftrag |
| Beantragte Aufnahme | Beantragte Aufnahme zur Bestellung |
| Erfassung bestätigt | Auftragserfassung abgeschlossen |
| Partielle Erfassung | Teilweise erfasste Reihenfolge |
| Aufnahme fehlgeschlagen | Auftragserfassung fehlgeschlagen |
| Voided | Reihenfolge aufgehoben |

## Berichtansicht zum Bestellstatus

Die Übersicht über den Bestellstatus-Bericht finden Sie in der Statusansicht der Zahlungsdienste. Sie enthält detaillierte Status für alle Transaktionen - Zahlung, Fakturierung, Versand, Rückerstattung, Streitigkeit und mehr. Die [Datenvisualisierung zum Bestellstatus](#order-payment-status-data-visualization-view) in der Zahlungsdienst-Startseite ist eine visuelle Darstellung des aggregierten Zahlungsstatus pro Tag aus der Berichtansicht des Bestellstatus.

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** um die detaillierte Tabellenansicht des Bestellstatus-Berichts anzuzeigen.

![Bestellstatustransaktionen in der Admin-Konsole](assets/orders-report-data.png)

Sie können diese Ansicht entsprechend den Abschnitten in diesem Thema konfigurieren, um die gewünschten Daten am besten darzustellen.

Sie können [Download-Payload-Transaktionen](#download-order-payment-statuses) im .csv-Dateiformat zur Verwendung in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `TRANS DATE`. Die `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion eingeleitet wurde.

### Im Bericht verwendete Daten

Die [!DNL Payment Services] -Modul verwendet Bestelldaten und kombiniert sie mit aggregierten Zahlungsdaten aus anderen Quellen (einschließlich PayPal), um aussagekräftige und sehr nützliche Berichte bereitzustellen.

Die Bestelldaten werden exportiert und im Zahlungsdienst beibehalten. Wenn Sie [Bestellstatus ändern oder hinzufügen](https://docs.magento.com/user-guide/sales/order-status-custom.html){target="_blank"} or [edit a store view](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target="_blank"}, [store](https://docs.magento.com/user-guide/stores/store-information.html){target="_blank"}, oder Website-Name, dass die Daten mit den Zahlungsdaten kombiniert werden und der Bericht Bestellzahlstatus mit den kombinierten Informationen ausgefüllt wird.

Dieser Prozess umfasst zwei Schritte:

1. Der Index wird entweder `ON SAVE` (jedes Mal, wenn Bestellinformationen oder Store-Informationen geändert werden) oder `BY SCHEDULE` (auf einen vorkonfigurierten Cron-Zeitplan), je nachdem, wie er in konfiguriert ist [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html){target="_blank"} im Admin.

   Standardmäßig erfolgt die Datenindizierung `ON SAVE`, was bedeutet, dass bei jeder Änderung der Reihenfolge, des Bestellstatus, der Store-Ansicht, des Stores oder der Website der Neudexationsprozess sofort stattfindet.

1. Die indexierten Daten werden an den Zahlungsdienst gesendet, der dann in den Bestellstatusbericht eingetragen wird.

Die einzigen Daten, die zu Berichtszwecken exportiert und erfasst werden, sind Daten, die vom Bestellstatusbericht verwendet werden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `ORDER DATE`. Die `ORDER DATE` ist der Datum-Zeitstempel, an dem die Bestellung erstellt wurde.

#### Datenexport konfigurieren

Auch wenn die Neuindizierung standardmäßig in `ON SAVE` -Modus wird empfohlen, die Indizierung in `BY SCHEDULE` -Modus. Die `BY SCHEDULE` Der Index wird auf einem Cron-Zeitplan von einer Minute ausgeführt und alle geänderten Daten werden innerhalb von zwei Minuten nach jeder Datenänderung im Bestellstatusbericht angezeigt. Diese geplante Neuindizierung hilft Ihnen, den Aufwand für Ihren Store zu reduzieren, insbesondere wenn Sie eine große Menge eingehender Bestellungen haben, da dies planmäßig erfolgt (nicht bei jeder Bestellung).

Sie können den Indexmodus ändern.`ON SAVE` oder `BY SCHEDULE`—[im Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"}.

Informationen zum Konfigurieren des Datenexports finden Sie unter [Befehlszeilenkonfiguration](configure-cli.md#configure-data-export).

### Datenquelle auswählen

In der Berichtansicht Bestellzahlstatus können Sie die Datenquelle auswählen._[!UICONTROL Live]_oder_[!UICONTROL Sandbox]_- für die Sie Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png){width=400px}

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Stores anzeigen, die [!DNL Payment Services] im Produktionsmodus. Wenn_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtinformationen für den Sandbox-Modus anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn Sie keine Stores haben, die [!DNL Payment Services] Im Livemodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Sandbox]_.
* Wenn Sie über Stores (einen oder mehrere) verfügen, die [!DNL Payment Services] Im Livemodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Live]_.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihre [!UICONTROL Order Payment Status] Bericht:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicken **[!UICONTROL Data source]** und wählen Sie _[!UICONTROL Live]_oder_[!UICONTROL Sandbox]_.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Datum und Zeitrahmen anpassen

In der Berichtansicht Bestellzahlungsstatus können Sie den Zeitrahmen der Status, die Sie anzeigen möchten, anpassen, indem Sie bestimmte Daten auswählen. Standardmäßig werden 30 Tage Bestellzahlstatus im Raster angezeigt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicken Sie auf **[!UICONTROL Order dates]** Kalenderauswahl .
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Bestellzahlstatus für Ihre angegebenen Daten im Raster an.

### Spalten ein- und ausblenden

Der Bericht Bestellzahlstatus zeigt standardmäßig alle verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten in Ihrem Bericht angezeigt werden.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicken Sie auf _Spalteneinstellungen_ Symbol (![Symbol für Spalteneinstellungen](assets/column-settings.png)).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Im Bericht Bestellzahlstatus werden alle Änderungen angezeigt, die Sie im Menü Spalteneinstellungen vorgenommen haben. Die Spaltenvoreinstellungen werden gespeichert und bleiben in Kraft, wenn Sie von der Berichtsansicht weg navigieren.

### Status anzeigen

Die Ansicht des Bestellstatus-Berichts zeigt für jede Bestellung von Zahlungsdiensten umfassende Informationen zum Transaktionsstatus und Zahlstatus an.

#### Transaktionsstatus

Standardmäßig werden 30 Tage Bestellzahlstatus im Raster angezeigt.

Scrollen Sie nach links und rechts, um [Bestellstatusangaben](#column-descriptions), einschließlich Bestelldatum, autorisiertes Datum, fakturiert, versandt, Zahlungsstatus und mehr.

Die Anzahl der Zeilen, die bei einer Suche zurückgegeben oder in den standardmäßigen 30 Tagen des Bestellzahlstatus angezeigt werden, wird über dem Raster der Statusanzeige für Bestellungen neben dem Auswahlfilter für Bestelldaten-Kalender angezeigt.

#### Zahlungsstatus

In der Spalte Zahlungsstatus wird der aktuelle Status einer Zahlung angezeigt. A `Capture failed` Die Zahlung zeigt einen roten Warnstatus und eine `Voided` Die Zahlung zeigt einen grauen Warnstatus an.

#### Erstattungsstatus

In der Spalte Rückerstattungsstatus wird der aktuelle Status einer Rückerstattung angezeigt. A `Capture failed` Die Zahlung zeigt einen roten Warnstatus und eine `Voided` Die Zahlung zeigt einen grauen Warnstatus an.

### Berichtdaten aktualisieren

Die Ansicht des Bestellstatus-Berichts zeigt eine _[!UICONTROL Last updated]_Zeitstempel, der das letzte Mal angibt, dass die Berichtinformationen aktualisiert wurden. Standardmäßig werden die Daten des Berichts zum Bestellstatus alle drei Stunden automatisch aktualisiert.

Sie können auch manuell eine Aktualisierung der Berichtdaten zum Bestellzahlungsstatus erzwingen, um die aktuellsten Berichtinformationen anzuzeigen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicken Sie auf _Aktualisieren_ Symbol (![Aktualisierungssymbol](assets/refresh-button-med.png)).

   Die Daten des Berichts zum Bestellstatus werden aktualisiert, und *[!UICONTROL Update complete]* -Bestätigung angezeigt und die neuesten Informationen im Raster vorhanden sind.

### Streitigkeiten anzeigen

Sie können alle Streitigkeiten bezüglich der Bestellungen Ihres Ladens einsehen und zum PayPal-Abwicklungszentrum navigieren, um über den Bestellstatusbericht darauf zu reagieren.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Navigieren Sie zum **[!UICONTROL Disputes column]**.
1. Anzeigen von Streitigkeiten für eine bestimmte Bestellung, siehe [den Streitstatus](#order-payment-status-information).
1. Klicken Sie auf den Link zur Kennung des Streits (beginnend mit _PP-D-_), um zur [PayPal Resolution Center](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. Ergreifen Sie bei Bedarf geeignete Maßnahmen für den Streit.

   Klicken Sie auf die Spaltenüberschrift &quot;Streitigkeiten&quot;, um die Streitigkeiten nach Status zu sortieren.

### Zahlungsstatus der Bestellung herunterladen

Sie können eine CSV-Datei mit allen Status herunterladen, die im Raster der Bestellzahlungsansicht angezeigt werden, unabhängig davon, ob Sie den standardmäßigen Status von 30 Tagen oder einen benutzerdefinierten Zeitrahmen anzeigen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Wenn Sie Status für einen anderen Zeitraum als die letzten 30 Tage anzeigen möchten, [Datumsbereich-Zeitrahmen für Ihre Status anpassen](#customize-dates-timeframe).
1. Klicken Sie auf _Download_ (![Download-Symbol](assets/icon-download.png)).

Ihr Bestellzahlstatus wird im .csv -Format heruntergeladen.

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

#### Statusinformationen

Berichte zum Bestellstatus enthalten die folgenden Informationen.

| Spalte | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce-Bestell-ID<br> <br>So sehen Sie verwandte [Bestellinformationen](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}klicken Sie auf die ID. |
| [!UICONTROL Order Date] | Zeitstempel der Bestellung |
| [!UICONTROL Authorized Date] | Datum des Zeitstempels der Zahlungsgenehmigung |
| [!UICONTROL Order Status] | Aktueller Commerce [Bestellstatus](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | Rechnungsstatus —*[!UICONTROL No]*, *[!UICONTROL Partial]* oder *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Versandstatus —*[!UICONTROL No]*, *[!UICONTROL Partial]* oder *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Gesamtbetrag der Bestellung |
| [!UICONTROL Cur] | Währungstyp der Bestellung |
| [!UICONTROL Pay Status] | Zahlungsstatus für eine bestimmte Bestellung |
| [!UICONTROL Paid Amt] | Auf Bestellung entrichteter Betrag |
| [!UICONTROL Cur] | Währungstyp des für eine Bestellung gezahlten Betrags |
| [!UICONTROL Refund Status] | Status einer Rückerstattung bei einer Bestellung (z. B. Informationen aus Rückgaben, RMAs und Kreditkarten)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* oder *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Erstatteter Gesamtbetrag für eine Bestellung |
| [!UICONTROL Cur] | Währungstyp des für eine Bestellung rückerstatteten Betrags |
| [!UICONTROL Disputes] | Stand der Streitigkeiten über einen Beschluss (Informationen aus Streitigkeiten und Chargebacks)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* oder *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Zahlungsmethode, die bei einer Bestellung im Commerce-Geschäft verwendet wird |
| [!UICONTROL Website] | Website, von der aus die Bestellung aufgegeben wurde |
| [!UICONTROL Store] | Store, aus dem die Bestellung aufgegeben wurde |
| [!UICONTROL Store View] | Store-Ansicht, aus der die Bestellung aufgegeben wurde |
