---
title: Typen von Commerce-Daten
description: Erfahren Sie, welche Datentypen Sie erfassen und an den Experience Platform senden können.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 1cdf3fcb-fb16-47ef-be5c-0ebbf1feaff4
source-git-commit: d5d5741442973d86a2d403edc940d18333defd67
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Typen von Commerce-Daten

Die [Datenverbindungserweiterung](overview.md) verbindet Ihre Commerce-Daten mit der Experience Platform. Daten, die auf der Experience Platform verwendet werden können, sind in zwei Verhaltenstypen unterteilt: Zeitreihendaten, die zur Klasse **Erlebnisereignis** gehören, und Datensatzdaten, die zur Klasse **Individuelles Profil** gehören.

Erfahren Sie mehr über [Datenverhalten](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) und [Klassen](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) in Experience Platform.

## Zeitreihendaten

Zeitreihendaten liefern eine Momentaufnahme des Systems zu dem Zeitpunkt, zu dem eine Aktion entweder direkt oder indirekt von einem Datensatzsubjekt durchgeführt wurde. Wenn ein Käufer beispielsweise ein Produkt auf Ihrer Site durchsucht, ein Produkt zum Warenkorb hinzufügt, eine Bestellung aufgibt usw. Zeitreihendaten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf „Erlebnisereignis **festgelegt**.

### Erfasste Zeitreihendaten

Unter [Verhaltensereignisse](events.md) und [Backoffice-Ereignisse](events-backoffice.md) erfahren Sie, welche Daten erfasst werden, wenn ein Zeitreihenereignis generiert wird.

### Zum Aufnehmen von Zeitreihen-Ereignisdaten erforderliches Schema

Erfahren Sie, wie [ein Schema erstellen](update-xdm.md) das Verhaltens- und Backoffice-Zeitreihen-Ereignisdaten aufnehmen kann.

## Datensatzdaten

Datensatzdaten liefern Informationen über die Attribute eines Subjekts. Ein Subjekt kann eine Organisation oder eine Einzelperson sein. Beispiel: Ein Käufer auf Ihrer Site erstellt ein Konto, das Datensatzdaten generiert. Diese Daten werden mit einem Schema in die Experience Platform aufgenommen, bei dem die Klasse auf „Individuelles **&quot; festgelegt**. Sie können diese Datensatzdaten an den Profilverwaltungs- und Segmentierungs-Service von Adobe senden: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=de).

### Erfasste Profildatensatzdaten

Unter [Kundenprofildatensatzdaten](events-profilerecord.md) erfahren Sie, welche Daten erfasst werden, wenn ein Profildatensatz generiert wird.

### Zum Aufnehmen von Profildatensatzdaten erforderliches Schema

Erfahren Sie, wie [ein Schema erstellen](profile-data.md) das Profildatensatzdaten aufnehmen kann.
