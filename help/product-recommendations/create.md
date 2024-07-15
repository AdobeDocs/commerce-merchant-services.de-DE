---
title: Neue Empfehlung erstellen
description: Erfahren Sie, wie Sie eine Produktempfehlungseinheit erstellen.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# Neue Empfehlung erstellen

Wenn Sie eine Empfehlung erstellen, erstellen Sie eine _Empfehlungseinheit_, die die empfohlenen Artikel _Artikel_ enthält.

![Empfehlungseinheit](assets/unit.png)
_Empfehlungseinheit_

Wenn Sie die Empfehlungseinheit aktivieren, beginnt Adobe Commerce mit [Datenerfassung](workspace.md), um Impressionen, Ansichten, Klicks usw. zu messen. Die Tabelle [!DNL Product Recommendations] enthält die Metriken für jede Empfehlungseinheit, damit Sie fundierte Geschäftsentscheidungen treffen können.

1. Wechseln Sie in der Seitenleiste _Admin_ zu **Marketing** > _Promotions_ > **Produkt-Recommendations** , um den Arbeitsbereich _Produkt-Recommendations_ anzuzeigen.

1. Geben Sie die [Store-Ansicht](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) an, in der die Empfehlungen angezeigt werden sollen.

   >[!NOTE]
   >
   > Die Empfehlungseinheiten für den Seitenaufbau müssen in der standardmäßigen Store-Ansicht erstellt werden, können dann jedoch überall verwendet werden. Weitere Informationen zum Erstellen von Produktempfehlungen mit Page Builder finden Sie unter [Content hinzufügen - Product Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Klicken Sie auf **Empfehlung erstellen**.

1. Geben Sie im Abschnitt _Ihre Empfehlung benennen_ einen beschreibenden Namen für die interne Referenz ein, z. B. `Home page most popular`.

1. Wählen Sie im Abschnitt _Seitentyp auswählen_ die Seite aus, auf der die Empfehlung aus den folgenden Optionen angezeigt werden soll:

   >[!NOTE]
   >
   > Produkt-Recommendations wird auf der Warenkorbseite nicht unterstützt, wenn Ihr Store so konfiguriert ist, dass [die Warenkorbseite unmittelbar nach dem Hinzufügen eines Produkts zum Warenkorb angezeigt wird](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html#redirect-to-cart).

   * Startseite
   * Kategorie
   * Produktdetails
   * Warenkorb
   * Bestätigung
   * [Seitenaufbau](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Sie können bis zu fünf aktive Empfehlungseinheiten für jeden Seitentyp und bis zu 25 für Page Builder erstellen. Der Seitentyp ist grau ausgeblendet, wenn die Grenze erreicht ist.

   ![Empfehlungsname und Seite](assets/create-recommendation.png)
   _Empfehlungsname und Seitenplatzierung_

1. Geben Sie im Abschnitt _Empfehlungstyp auswählen_ den [Empfehlungstyp](type.md) an, der auf der ausgewählten Seite angezeigt werden soll. Bei einigen Seiten ist die [Platzierung](placement.md) von Empfehlungen auf bestimmte Typen beschränkt.

1. Geben Sie im Abschnitt _Schaufenster-Anzeigetitel_ den für Ihre Kunden sichtbaren [Titel](placement.md#recommendation-labels) ein, z. B. &quot;Topverkäufe&quot;.

1. Verwenden Sie im Abschnitt _Anzahl der Produkte auswählen_ den Schieberegler, um festzulegen, wie viele Produkte in der Empfehlungseinheit angezeigt werden sollen.

   Der Standardwert ist `5`, mit einem Maximalwert von `20`.

1. Geben Sie im Abschnitt _Platzierung auswählen_ an, wo die Empfehlungseinheit auf der Seite angezeigt werden soll.

   * Am unteren Rand des Hauptinhalts
   * Oben im Hauptinhalt

1. (Optional) Um die Reihenfolge der Empfehlungen zu ändern, wählen Sie die Zeilen in der Tabelle _Position auswählen_ aus und verschieben Sie sie.

   Im Abschnitt _Position auswählen_ werden alle Empfehlungen (falls vorhanden) angezeigt, die für den ausgewählten Seitentyp erstellt wurden.

   ![Empfehlungsreihenfolge](assets/create-recommendation-select-placement.png)
   _Empfehlungsreihenfolge auf Seite_

1. (Optional) Wenden Sie im Abschnitt _Filter_ die Filter [an](filters.md), um zu steuern, welche Produkte in der Empfehlungseinheit angezeigt werden.

   ![Empfehlungsfilter](assets/create-recommendation-filter-products.png)
   _Empfehlungs-Produktfilter_

1. Klicken Sie nach Abschluss des Vorgangs auf eine der folgenden Optionen:

   * **Als Entwurf speichern**, um die Empfehlungseinheit später zu bearbeiten. Sie können den Seitentyp oder den Empfehlungstyp für eine Empfehlungseinheit nicht in einem Entwurfsstatus ändern.

   * **Aktivieren Sie** , um die Empfehlungseinheit in Ihrer Storefront zu aktivieren.

## Bereitschaftsindikatoren

Einige Empfehlungstypen verwenden Verhaltensdaten von Ihren Kunden zum [Trainieren von maschinellen Lernmodellen](behavioral-data.md), um personalisierte Empfehlungen zu erstellen.

Erfordert nur Katalogdaten. Hierfür sind keine Verhaltensdaten erforderlich:

* _Am meisten gefällt dies_
* _Kürzlich angezeigt_
* _Visuelle Ähnlichkeit_

Basierend auf den letzten sechs Monaten von Storefront-Verhaltensdaten:

* _Betrachtet dies, hat diesen_ angesehen
* _Betrachtet dies, kaufte diesen_
* _kaufte dies, kaufte diesen_
* _Für Sie empfohlen_

Popularitätsbasierte Empfehlungstypen verwenden die letzten sieben Tage von Storefront-Verhaltensdaten:

* Am häufigsten angezeigt
* Am häufigsten gekauft
* Zum Warenkorb hinzugefügt
* Trends

Die Werte der Bereitschaftsindikatoren werden aufgrund von Faktoren wie der Gesamtgröße des Katalogs, dem Volumen der Interaktionsereignisse (Ansichten, Hinzufügung zum Warenkorb, Käufe) und dem Prozentsatz der Skus, die diese Ereignisse innerhalb eines bestimmten Zeitfensters registrieren, voraussichtlich schwanken. Beispielsweise können die Bereitschaftsindikatoren während des Traffics in der Hochsaison höhere Werte aufweisen als in Zeiten normalen Volumens.

Um Ihnen bei der Visualisierung des Trainings-Fortschritts für jeden Empfehlungstyp zu helfen, zeigt der Abschnitt _Empfehlungstyp auswählen_ ein Maß an Bereitschaft für jeden Typ an. Diese Indikatoren werden anhand von zwei Faktoren berechnet:

* Ausreichende Ergebnissatzgröße: Gibt es in den meisten Szenarien genügend Ergebnisse, um die Verwendung von [Reserveempfehlungen](behavioral-data.md#backuprecs) zu vermeiden?

* Ausreichende Ergebnismenge: Stellen die zurückgegebenen Produkte eine Vielzahl von Produkten aus Ihrem Katalog dar? Mit diesem Faktor soll verhindert werden, dass eine Minderheit von Produkten die einzigen Artikel ist, die auf der gesamten Site empfohlen werden.

Basierend auf den oben genannten Faktoren wird ein Bereitschaftswert berechnet und angezeigt. Ein Empfehlungstyp gilt als bereitstellbar, wenn sein Bereitschaftswert 75 % oder höher beträgt. Ein Empfehlungstyp wird als teilweise fertig angesehen, wenn seine Bereitschaft mindestens 50 % beträgt. Ein Empfehlungstyp gilt als nicht bereit zur Bereitstellung, wenn sein Bereitschaftswert unter 50 % liegt. Dies sind allgemeine Richtlinien, aber jeder Einzelfall kann je nach Art der erfassten Daten unterschiedlich sein, wie oben beschrieben.

![Empfehlungstyp](assets/create-recommendation-select-type.png)
_Empfehlungstyp_

>[!NOTE]
>
>Die Indikatoren dürfen niemals 100 % erreichen.

## Recommendations-Vorschau {#preview}

Das Bedienfeld &quot;_Empfohlene Produktvorschau_&quot;ist immer mit einer Beispielauswahl von Produkten verfügbar, die in der Empfehlungseinheit angezeigt werden, wenn sie auf der Storefront bereitgestellt wird.

Um eine Empfehlung bei der Arbeit in einer Nicht-Produktionsumgebung zu testen, können Sie Empfehlungsdaten aus einer [anderen Quelle](settings.md) abrufen. Auf diese Weise können Händler mit Regeln experimentieren und die Empfehlungen in der Vorschau anzeigen, bevor sie in der Produktion bereitgestellt werden.

| Feld | Beschreibung |
|---|---|
| Name | Der Name des Produkts. |
| SKU | Lagereinheit, die dem Produkt zugewiesen ist |
| Preis | Der Preis des Produkts. |
| Ergebnistyp | Primär - gibt an, dass ausreichend Schulungsdaten gesammelt wurden, um eine Empfehlung anzuzeigen.<br />Backup - gibt an, dass nicht genügend Schulungsdaten erfasst wurden, sodass eine Reserveempfehlung zum Ausfüllen des Slots verwendet wird. Navigieren Sie zu [Verhaltensdaten](behavioral-data.md) , um mehr über Modelle für maschinelles Lernen und Reserveempfehlungen zu erfahren. |

Experimentieren Sie beim Erstellen Ihrer Empfehlungseinheit mit dem Seitentyp, Empfehlungstyp und Filtern, um sofort Echtzeit-Feedback zu den einzuschließenden Produkten zu erhalten. Sobald Sie wissen, welche Produkte angezeigt werden, können Sie die Empfehlungseinheit entsprechend Ihren Geschäftsanforderungen konfigurieren.

Adobe Commerce [filtert ](filters.md) -Empfehlungen, um zu verhindern, dass doppelte Produkte angezeigt werden, wenn mehrere Empfehlungseinheiten auf einer Seite bereitgestellt werden. Daher unterscheiden sich die im Vorschaufenster angezeigten Produkte möglicherweise von denen, die in der Storefront angezeigt werden.

>[!NOTE]
>
> Sie können keine Vorschau des Empfehlungstyps `Recently viewed` anzeigen, da die Daten nicht im Admin verfügbar sind.
