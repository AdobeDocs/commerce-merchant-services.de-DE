---
title: Bestellstatusbericht
description: Verwenden Sie den Bestellstatusbericht, um mehr über den Zahlungsstatus Ihrer Bestellungen zu erfahren und potenzielle Probleme zu identifizieren.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Bestellstatusbericht

[!DNL Payment Services] für [!DNL Adobe Commerce] und [!DNL Magento Open Source] bietet Ihnen umfassende Berichte, sodass Sie einen klaren Überblick über die [Transaktionen](transactions.md), Bestellungen und Zahlungen.

Es gibt zwei verfügbare Ansichten zum Bestellstatus, mit denen Sie schnell den Zahlungsstatus Ihrer Bestellungen anzeigen können:

* **[Visualisierung des Bestellstatus](#order-payment-status-data-visualization-view)**—Auf der Zahlungsdienst-Startseite verfügbares Diagramm, das eine visuelle Darstellung des aggregierten Zahlungsstatus pro Tag in der Ansicht des Bestellstatus-Berichts darstellt
* **[Berichtansicht zum Bestellstatus](#order-payment-status-report-view)**—Bericht verfügbar im Bestellstatus, der detaillierte Zahlungs-, Fakturierungs-, Versand-, Erstattungs- und Streitstatusangaben für alle Transaktionen anzeigt

Mit den Statusansichten für die Bestellzahlung können Sie leicht erkennen, wo sich eine bestimmte Bestellung innerhalb des Bestellablaufs befindet. Diese Berichte ermöglichen es Ihnen, Bestellungen schnell anzuzeigen - basierend auf ihrem Zahlungsstatus und Zahlungsdatum - und potenzielle Probleme zu identifizieren.

Sie können [Zahlungsstatus herunterladen](#download-order-payment-statuses) im .csv-Dateiformat zur Verwendung in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware.

>[!NOTE]
>
>Wenn Sie keine [integrierte und aktivierte Livemodus](production.md#enable-live-payments) für [!DNL Payment Services].

## Datenvisualisierung zum Bestellstatus

Die Visualisierung der Daten zum Bestellstatus ist auf der Zahlungsdienst-Startseite verfügbar. Es handelt sich um eine visuelle Darstellung des aggregierten tägliche Zahlungsstatus aus der detaillierten Tabelle. [Berichtansicht zum Bestellstatus](#order-payment-status-report-view).

Im _Admin_ Seitenleiste, navigieren Sie zu **Vertrieb** > **Zahlungsdienste** > _Bestellungen_ um die Datenvisualisierung anzuzeigen [Grafik des Zahlungsstatus](#statuses-information).

![Payout-Datenvisualisierung in Admin](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Klicks **[!UICONTROL View Report]** zur detaillierten Tabelle navigieren [Berichtansicht zum Bestellstatus](#order-payment-status-report-view).

### Zeitrahmen für Status anpassen

Standardmäßig werden 30 Tage Zahlungsstatus angezeigt.

In der Visualisierung des Bestellstatus können Sie den Zeitrahmen für die Zahlungsstatus, die Sie anzeigen möchten, anpassen, indem Sie einen Datumsbereich auswählen:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Die Datenvisualisierung zum Bestellstatus ist in der Ansicht _Bestellungen_ Abschnitt.
1. Klicken Sie auf **[!UICONTROL Range]** Auswahlfilter.
1. Wählen Sie den entsprechenden Datumsbereich aus: 30 Tage, 15 Tage oder 7 Tage.
1. Zeigen Sie die Statusinformationen für die angegebenen Daten an.

### Statusinformationen

Die Zahlungsstatus für einen ausgewählten Datumsbereich werden links in der Datenvisualisierung Bestellstatus-Daten angezeigt. Die Datumsangaben für den ausgewählten Datumsbereich werden unten in der Ansicht angezeigt. Wenn an einem bestimmten Datum keine Bestellungen eingegangen sind, wird dieses Datum nicht angezeigt.

Die Datenvisualisierung zum Bestellstatus enthält die folgenden Informationen.

| Daten | Beschreibung |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Datumsbereich für Bestellungen im angegebenen Zeitrahmen; Daten auf der Y-Achse (links) |
| Datumsbereich | Datumsbereich für den angegebenen Zeitraum; Daten auf der X-Achse (unten) |
| Autorisiert | Auftrag genehmigt |
| Beantragte Aufnahme | Beantragte Aufnahme |
| Erfassung bestätigt | Auftragserfassung abgeschlossen |
| Partielle Erfassung | Teilweise erfasste Reihenfolge |
| Aufnahme fehlgeschlagen | Auftragserfassung fehlgeschlagen |
| Voided | Reihenfolge aufgehoben |

## Berichtansicht zum Bestellstatus

Die Ansicht des Bestellstatus-Berichts ist in der Ansicht Home der Zahlungsdienste verfügbar. Sie enthält detaillierte Status für alle Transaktionen - Zahlung, Fakturierung, Versand, Rückerstattung, Streitigkeit und mehr.

Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**um die detaillierte Tabellenansicht des Bestellstatus-Berichts anzuzeigen.

![Bestellstatusvorgänge im Admin](assets/orders-report-data.png){width="800" zoomable="yes"}

Sie können diese Ansicht entsprechend den Abschnitten in diesem Thema konfigurieren, um die gewünschten Daten am besten darzustellen.

Sie können [Download-Auszahlungstransaktionen](#download-order-payment-statuses) im .csv-Dateiformat zur Verwendung in bestehenden Buchhaltungs- oder Auftragsverwaltungssoftware.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `TRANS DATE`. Die `TRANS DATE` ist das Datum und die Uhrzeit, zu der die Transaktion eingeleitet wurde.

### Aktualisierungen des Zahlungsstatus

Bestimmte Zahlungsmethoden erfordern einen Zeitraum, um die Zahlung zu erfassen. [!DNL Payment Services] erkennt nun die ausstehenden Status eines Zahlungsvorgangs in einer Bestellung durch:

* Synchrone Erkennung `pending capture` Transaktionen
* Asynchrone Überwachung `pending capture` Transaktionen

>[!NOTE]
>
>Die Erkennung des ausstehenden Status von Zahlungsvorgängen in einer Bestellung verhindert versehentlich Versandaufträge, wenn die Zahlung noch nicht eingegangen ist. Dies kann bei E-Check- und PayPal-Transaktionen auftreten.

#### Synchrone Erkennung von Transaktionen mit ausstehender Erfassung

Automatische Erkennung von Transaktionen in einer `Pending` Status zu ändern und die Eingabe von Bestellungen zu verhindern, `Processing` Status, wenn eine solche Transaktion erkannt wird.

Während des Auscheckens eines Kunden oder wenn ein Administrator eine Rechnung für eine zuvor autorisierte Zahlung erstellt, [!DNL Payment Services] erkennt automatisch Transaktionen in einer `Pending` Status und Verlagerungen der entsprechenden Bestellungen in `Payment Review` -Status.

#### Asynchrone Überwachung von Transaktionen mit ausstehenden Datensätzen

Erkennen, wenn eine ausstehende Capture-Transaktion eine `Completed` -Status, damit Händler die Verarbeitung der betroffenen Bestellung fortsetzen können.

Um sicherzustellen, dass dieser Prozess erwartungsgemäß funktioniert, müssen Händler einen neuen Cron-Auftrag konfigurieren. Sobald der Auftrag für die automatische Ausführung konfiguriert wurde, werden vom Händler keine weiteren Eingriffe erwartet.

Siehe [Konfigurieren von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html). Nach der Konfiguration wird der neue Auftrag alle 30 Minuten ausgeführt, um Aktualisierungen für Bestellungen abzurufen, die sich in einer `Payment Review` -Status.

Händler können den aktualisierten Zahlungsstatus über die Berichtansicht Bestellzahlstatus überprüfen.

### Im Bericht verwendete Daten

[!DNL Payment Services] verwendet Bestelldaten und kombiniert sie mit aggregierten Zahlungsdaten aus anderen Quellen (einschließlich PayPal), um aussagekräftige und sehr nützliche Berichte bereitzustellen.

Die Bestelldaten werden exportiert und im Zahlungsdienst beibehalten. Wenn Sie [Bestellstatus ändern oder hinzufügen](https://docs.magento.com/user-guide/sales/order-status-custom.html) oder [Bearbeiten einer Store-Ansicht](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html), [store](https://docs.magento.com/user-guide/stores/store-information.html), oder Website-Name, dass die Daten mit den Zahlungsdaten kombiniert werden und der Bericht Bestellzahlstatus mit den kombinierten Informationen ausgefüllt wird.

Dieser Prozess umfasst zwei Schritte:

1. Der Index wird entweder `ON SAVE` (jedes Mal, wenn Bestellinformationen oder Store-Informationen geändert werden) oder `BY SCHEDULE` (auf einen vorkonfigurierten Cron-Zeitplan), je nachdem, wie er in konfiguriert ist [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html) im Admin.

   Standardmäßig erfolgt die Datenindizierung `ON SAVE`, was bedeutet, dass bei jeder Änderung der Reihenfolge, des Bestellstatus, der Store-Ansicht, des Stores oder der Website der Neudexationsprozess sofort stattfindet.

1. Die indexierten Daten werden an den Zahlungsdienst gesendet, der dann in den Bestellstatusbericht eingetragen wird.

Die einzigen Daten, die zu Berichtszwecken exportiert und erfasst werden, sind Daten, die vom Bestellstatusbericht verwendet werden.

>[!NOTE]
>
>Die in dieser Tabelle angezeigten Daten werden in absteigender Reihenfolge sortiert (`DESC`) standardmäßig mithilfe der `ORDER DATE`. Die `ORDER DATE` ist der Datum-Zeitstempel, an dem die Bestellung erstellt wurde.

#### Datenexport konfigurieren

Auch wenn die Neuindizierung standardmäßig in `ON SAVE` -Modus wird empfohlen, die Indizierung in `BY SCHEDULE` -Modus. Die `BY SCHEDULE` Der Index wird auf einem Cron-Zeitplan von einer Minute ausgeführt und alle geänderten Daten werden innerhalb von zwei Minuten nach jeder Datenänderung im Bestellstatusbericht angezeigt. Diese geplante Neuindizierung hilft Ihnen, den Aufwand für Ihren Store zu reduzieren, insbesondere wenn Sie eine große Menge eingehender Bestellungen haben, da dies planmäßig erfolgt (nicht bei jeder Bestellung).

Sie können den Indexmodus ändern.`ON SAVE` oder `BY SCHEDULE`—[im Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

Informationen zum Konfigurieren des Datenexports finden Sie unter [Befehlszeilenkonfiguration](configure-cli.md#configure-data-export).

### Datenquelle auswählen

In der Berichtansicht Bestellzahlstatus können Sie die Datenquelle auswählen.**[!UICONTROL Live]** _ oder **[!UICONTROL Sandbox]**- für die Sie Berichtsergebnisse anzeigen möchten.

![Auswahl von Datenquellen](assets/datasource.png){width="300" zoomable="yes"}

Wenn _[!UICONTROL Live]_die ausgewählte Datenquelle ist, können Sie Berichtinformationen für Ihre Stores anzeigen, die [!DNL Payment Services] im Produktionsmodus. Wenn_[!UICONTROL Sandbox]_ die ausgewählte Datenquelle ist, können Sie Berichtinformationen für den Sandbox-Modus anzeigen.

Datenquellenauswahlen funktionieren wie folgt:

* Wenn Sie keine Stores haben, die [!DNL Payment Services] Im Livemodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Sandbox]_.
* Wenn Sie über Stores (einen oder mehrere) verfügen, die [!DNL Payment Services] Im Livemodus wird bei der Auswahl der Datenquelle standardmäßig _[!UICONTROL Live]_.
* Beim Exportieren von Berichten wird immer die Auswahl der Datenquelle berücksichtigt.

So wählen Sie die Datenquelle für Ihre [!UICONTROL Order Payment Status] Bericht:

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Klicken Sie auf _[!UICONTROL Data source]_Auswahlfilter und Auswahl **[!UICONTROL Live]**oder **[!UICONTROL Sandbox]**.

   Die Berichtsergebnisse werden basierend auf der ausgewählten Datenquelle neu generiert.

### Zeitrahmen für Bestelldaten anpassen

In der Berichtansicht Bestellzahlungsstatus können Sie den Zeitrahmen der Statusergebnisse, die Sie anzeigen möchten, anpassen, indem Sie bestimmte Daten auswählen. Standardmäßig werden 30 Tage Bestellzahlstatus im Raster angezeigt.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf _[!UICONTROL Order dates]_Kalenderauswahl .
1. Wählen Sie den entsprechenden Datumsbereich aus.
1. Zeigen Sie die Bestellzahlstatus für Ihre angegebenen Daten im Raster an.

### Berichtinformationen filtern

In der Berichtansicht Bestellzahlungsstatus können Sie die anzuzeigenden Statusergebnisse filtern, indem Sie Filterkriterien auswählen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf **[!UICONTROL Filter]** auswählen.
1. Umschalten zwischen _Zahlungsstatus_ Optionen, um die Berichtsergebnisse nur für ausgewählte Bestellzahlstatus anzuzeigen.
1. Zeigen Sie die Berichtsergebnisse innerhalb eines Bestellwertbereichs an, indem Sie eine _[!UICONTROL Min Order Amount]_oder _[!UICONTROL Max Order Amount_].
1. Klicks **[!UICONTROL Hide filters]** um den Filter auszublenden.

### Spalten ein- und ausblenden

Der Bericht Bestellzahlstatus zeigt standardmäßig alle verfügbaren Informationsspalten an. Sie können jedoch anpassen, welche Spalten in Ihrem Bericht angezeigt werden.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf _Spalteneinstellungen_ Symbol (![Symbol für Spalteneinstellungen](assets/column-settings.png){width="20" zoomable="yes"}).
1. Um anzupassen, welche Spalten im Bericht angezeigt werden, aktivieren oder deaktivieren Sie die Spalten in der Liste.

   Im Bericht Bestellzahlstatus werden alle Änderungen, die Sie im Menü Spalteneinstellungen vorgenommen haben, sofort angezeigt. Die Spaltenvoreinstellungen werden gespeichert und bleiben in Kraft, wenn Sie von der Berichtsansicht weg navigieren.

### Status anzeigen

Die Ansicht des Bestellstatus-Berichts zeigt umfassende Informationen zum Zahlungsstatus für jede Bestellung.

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

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicken Sie auf _Aktualisieren_ Symbol (![Aktualisierungssymbol](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Die Daten des Berichts über den Bestellstatus werden aktualisiert, und *[!UICONTROL Update complete]* -Bestätigung angezeigt und die neuesten Informationen im Raster vorhanden sind.

### Streitigkeiten anzeigen

Sie können alle Streitigkeiten bezüglich der Bestellungen Ihres Ladens einsehen und zum PayPal-Abwicklungszentrum navigieren, um über den Bestellstatusbericht darauf zu reagieren.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Navigieren Sie zum **[!UICONTROL Disputes column]**.
1. Anzeigen von Streitigkeiten für eine bestimmte Bestellung, siehe [den Streitstatus](#order-payment-status-information).
1. Überprüfung der Streitdetails von [PayPal Resolution Center](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) durch Klicken auf den Link zur Kennung des Streits, der mit _PP-D-_.
1. Ergreifen Sie bei Bedarf geeignete Maßnahmen für den Streit.

   Klicken Sie auf die Schaltfläche [!UICONTROL Disputes] Spaltenüberschrift.

### Zahlungsstatus der Bestellung herunterladen

Sie können eine CSV-Datei mit allen Status herunterladen, die im Raster der Bestellzahlungsansicht angezeigt werden, unabhängig davon, ob Sie den standardmäßigen Status von 30 Tagen oder einen benutzerdefinierten Zeitrahmen anzeigen.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Wenn Sie Status für einen anderen Zeitraum als die letzten 30 Tage anzeigen möchten, [Datumsbereich-Zeitrahmen für Ihre Status anpassen](#customize-dates-timeframe).
1. Klicken Sie auf _Herunterladen_ (![Download-Symbol](assets/icon-download.png){width="20" zoomable="yes"}).

Ihr Bestellzahlstatus wird im .csv -Format heruntergeladen.

### Spaltenbeschreibungen

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
| [!UICONTROL Store] | Store, in dem die Bestellung aufgegeben wurde |
| [!UICONTROL Store View] | Store-Ansicht, aus der die Bestellung aufgegeben wurde |
