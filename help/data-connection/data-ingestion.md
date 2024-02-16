---
title: Typen von Commerce-Daten
description: Erfahren Sie, welche Datentypen Sie erfassen und an die Experience Platform senden können.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Typen von Commerce-Daten

Die [Data Connection-Erweiterung](overview.md) verbindet Ihre Commerce-Daten mit der Experience Platform. Daten, die für die Verwendung in der Experience Platform bestimmt sind, sind in zwei Verhaltenstypen unterteilt: Zeitreihendaten, die zum **Erlebnisereignis** -Klasse und Datensatzdaten, die zur **Individuelles Profil** -Klasse.

Weitere Informationen [Datenverhalten](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) und [classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) in Experience Platform.

## Zeitreihendaten

Zeitreihendaten liefern eine Momentaufnahme des Systems zu dem Zeitpunkt, zu dem eine Aktion entweder direkt oder indirekt von einem Datensatzsubjekt durchgeführt wurde. Wenn beispielsweise ein Käufer ein Produkt auf Ihrer Site durchsucht, zum Warenkorb hinzufügt, eine Bestellung aufgibt usw. Zeitreihendaten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf **Erlebnisereignis**.

### Erfasste Zeitreihendaten

Siehe [Verhaltensereignisse](events.md) und [Backoffice-Ereignisse](events-backoffice.md) , um zu erfahren, welche Daten beim Generieren eines Zeitreihenereignisses erfasst werden.

### Für die Erfassung von Zeitreihenereignisdaten benötigtes Schema

Erfahren Sie, wie [Schema erstellen](update-xdm.md) , mit dem Ereignisdaten aus Verhaltens- und Back-Office-Zeitreihen erfasst werden können.

## Daten aufzeichnen

>[!NOTE]
>
>Diese Funktion befindet sich in der Beta-Phase. Wenn Sie dem Betaprogramm beitreten möchten, senden Sie eine Anfrage an [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Datensatzdaten enthalten Informationen über die Attribute eines Subjekts. Ein Subjekt könnte eine Organisation oder eine Einzelperson sein. Beispielsweise erstellt ein Käufer auf Ihrer Site ein Konto und generiert Datensatzdaten. Diese Daten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf **Individuelles Profil**. Sie können diese Datensatzdaten an den Adobe-Profilverwaltungs- und Segmentierungsdienst senden: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### Erfassen von Profildatensätzen

Siehe [Kundenprofildatensätze](events-profilerecord.md) , um zu erfahren, welche Daten erfasst werden, wenn ein Profildatensatz generiert wird.

### Zum Erfassen von Profildatensatzdaten benötigtes Schema

Erfahren Sie, wie [Schema erstellen](profile-data.md) , das Profildatensatzdaten erfassen kann.
