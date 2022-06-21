---
title: Neue Empfehlung erstellen
description: Erfahren Sie, wie Sie eine Produktempfehlungseinheit erstellen.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 1d2b4b8d85e5ccea1c4258869fbfd191a2e7987b
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Neue Empfehlung erstellen

Wenn Sie eine Empfehlung erstellen, erstellen Sie eine _Empfehlungseinheit_ , das das empfohlene Produkt enthält _items_.

![Empfehlungseinheit](assets/unit.png)
_Empfehlungseinheit_

Wenn Sie die Empfehlungseinheit aktivieren, beginnt Adobe Commerce [Daten erfassen](workspace.md) , um Impressionen, Ansichten, Klicks usw. zu messen. Die [!DNL Product Recommendations] zeigt die Metriken für jede Empfehlungseinheit an, damit Sie fundierte Geschäftsentscheidungen treffen können.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Marketing** > _Promotions_ > **Produkt-Recommendations** , um _Produkt-Recommendations_ Arbeitsbereich.

1. Geben Sie die [Store-Ansicht](https://docs.magento.com/user-guide/configuration/scope.html) wo die Empfehlungen angezeigt werden sollen.

   >[!NOTE]
   >
   > Die Empfehlungseinheiten für den Seitenaufbau können nur für die standardmäßige Store-Ansicht erstellt werden. Weitere Informationen zum Erstellen von Produktempfehlungen mit Page Builder finden Sie unter [Hinzufügen von Inhalten - Produkt-Recommendations](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html).

1. Klicken **Empfehlung erstellen**.

1. Im _Benennen Sie Ihre Empfehlung._ eingeben, einen beschreibenden Namen für die interne Referenz eingeben, z. B. `Home page most popular`.

1. Im _Seitentyp auswählen_ wählen Sie aus den folgenden Optionen die Seite aus, auf der die Empfehlung angezeigt werden soll:

   - Startseite
   - Kategorie
   - Produktdetails
   - Warenkorb
   - Bestätigung
   - [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html)

   Sie können bis zu fünf aktive Empfehlungseinheiten für jeden Seitentyp und bis zu 25 für Page Builder erstellen. Der Seitentyp ist grau ausgeblendet, wenn die Grenze erreicht ist.

   ![Empfehlungsname](assets/create-recommendation.png)
   _Empfehlungsname und -platzierung_

1. Im _Empfehlungstyp auswählen_ -Abschnitt, geben Sie die [Empfehlungstyp](type.md) Sie möchten auf der ausgewählten Seite angezeigt werden. Bei einigen Seiten wird die Variable [placement](placement.md) Empfehlungen sind auf bestimmte Typen beschränkt.

   Einige Empfehlungstypen verwenden Verhaltensdaten von Ihren Kunden zu [Trainingsmodelle für maschinelles Lernen](behavioral-data.md) , um personalisierte Empfehlungen zu erstellen. Um Ihnen bei der Visualisierung des Trainings-Fortschritts für jeden Empfehlungstyp zu helfen, zeigt dieser Abschnitt die Bereitschaft für jeden Typ an. Diese Indikatoren werden anhand von zwei Faktoren berechnet:

   - Ausreichende Ergebnissatzgröße: Gibt es in den meisten Szenarien genügend Ergebnisse, um die Verwendung von [Ersatzempfehlungen](behavioral-data.md#backuprecs)?

   - Ausreichende Ergebnissatzvielfalt: Stellen die zurückgegebenen Produkte eine Vielzahl von Produkten aus Ihrem Katalog dar? Mit diesem Faktor soll verhindert werden, dass eine Minderheit von Produkten die einzigen Artikel ist, die auf der gesamten Site empfohlen werden.

   Basierend auf den oben genannten Faktoren wird ein Bereitschaftswert berechnet und angezeigt. Ein Empfehlungstyp gilt als bereitstellbar, wenn sein Bereitschaftswert 75 % oder höher beträgt. Ein Empfehlungstyp wird als teilweise fertig angesehen, wenn seine Bereitschaft mindestens 50 % beträgt. Schließlich gilt ein Empfehlungstyp als nicht bereit zur Bereitstellung, wenn sein Bereitschaftswert unter 50 % liegt.

1. Im _Anzeigebezeichnung Storefront_ eingeben. [label](placement.md#recommendation-labels) die für Ihre Kunden sichtbar ist, z. B. &quot;Topverkäufe&quot;.

   ![Empfehlungsname](assets/create-recommendation-select-type.png)
   _Empfehlungstyp_

1. Im _Anzahl der Produkte auswählen_ können Sie mit dem Schieberegler festlegen, wie viele Produkte in der Empfehlungseinheit angezeigt werden sollen.

   Der Standardwert ist `5`, mit einem Maximalwert von `20`.

1. Im _Platzierung auswählen_ geben Sie den Speicherort an, an dem die Empfehlungseinheit auf der Seite angezeigt werden soll.

   - Am unteren Rand des Hauptinhalts
   - Oben im Hauptinhalt

1. (Optional) Um die Reihenfolge der Empfehlungen zu ändern, wählen Sie die Zeilen aus und verschieben Sie sie in die _Position auswählen_ Tabelle.

   Die _Position auswählen_ zeigt alle Empfehlungen (falls vorhanden) an, die für den ausgewählten Seitentyp erstellt wurden.

   ![Empfehlungsname](assets/create-recommendation-select-placement.png)
   _Empfehlungstyp_

1. (Optional) Im _Filter_ Abschnitt [Filter anwenden](filters.md) , um zu steuern, welche Produkte in der Empfehlungseinheit angezeigt werden.

   ![Empfehlungsname](assets/create-recommendation-select-placement.png)
   _Empfehlungs-Produktfilter_

1. Klicken Sie nach Abschluss des Vorgangs auf eine der folgenden Optionen:

   - **Als Entwurf speichern** um die Empfehlungseinheit später zu bearbeiten. Sie können den Seitentyp oder den Empfehlungstyp für eine Empfehlungseinheit nicht in einem Entwurfsstatus ändern.

   - **Aktivieren** , um die Empfehlungseinheit in Ihrer Storefront zu aktivieren.

## Recommendations-Vorschau {#preview}

Die _Vorschau empfohlener Produkte_ ist immer mit einer Beispielauswahl von Produkten verfügbar, die in der Empfehlungseinheit angezeigt werden, wenn sie in der Storefront bereitgestellt wird.

Um eine Empfehlung zu testen, wenn Sie in einer Nicht-Produktionsumgebung arbeiten, können Sie Empfehlungsdaten aus einer [andere Quelle](settings.md). Auf diese Weise können Händler mit Regeln experimentieren und die Empfehlungen in der Vorschau anzeigen, bevor sie in der Produktion bereitgestellt werden.

| Feld | Beschreibung |
|---|---|
| Name | Der Name des Produkts. |
| SKU | Lagereinheit, die dem Produkt zugewiesen ist |
| Preis | Der Preis des Produkts. |
| Ergebnistyp | Primär - gibt an, dass ausreichend Schulungsdaten gesammelt wurden, um eine Empfehlung anzuzeigen.<br />Backup - zeigt an, dass nicht genügend Schulungsdaten erfasst wurden, sodass eine Reserveempfehlung zum Ausfüllen des Slots verwendet wird. Navigieren Sie zu [Verhaltensdaten](behavioral-data.md) , um mehr über Modelle für maschinelles Lernen und Ersatzempfehlungen zu erfahren. |

Experimentieren Sie beim Erstellen Ihrer Empfehlungseinheit mit dem Seitentyp, Empfehlungstyp und Filtern, um sofort Echtzeit-Feedback zu den einzuschließenden Produkten zu erhalten. Sobald Sie wissen, welche Produkte angezeigt werden, können Sie die Empfehlungseinheit entsprechend Ihren Geschäftsanforderungen konfigurieren.

Adobe Commerce [Filter](filters.md) Empfehlungen, um zu vermeiden, dass doppelte Produkte angezeigt werden, wenn mehrere Empfehlungseinheiten auf einer einzelnen Seite bereitgestellt werden. Daher unterscheiden sich die im Vorschaufenster angezeigten Produkte möglicherweise von denen, die in der Storefront angezeigt werden.

>[!NOTE]
>
> Die Vorschau der `Recently viewed` Empfehlungstyp, da die Daten nicht in Admin verfügbar sind.
