---
title: Typen von Commerce-Daten
description: Erfahren Sie, welche Datentypen Sie erfassen und an die Experience Platform senden können.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 1cdf3fcb-fb16-47ef-be5c-0ebbf1feaff4
source-git-commit: d5d5741442973d86a2d403edc940d18333defd67
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Typen von Commerce-Daten

Die [Datenverbindungs-Erweiterung](overview.md) verbindet Ihre Commerce-Daten mit der Experience Platform. Daten, die für die Verwendung in der Experience Platform vorgesehen sind, sind in zwei Verhaltenstypen unterteilt: Zeitreihendaten, die zur Klasse **Erlebnisereignis** gehören, und Datensatzdaten, die zur Klasse **Individuelles Profil** gehören.

Erfahren Sie mehr über das [Datenverhalten](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) und die [Klassen](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) im Experience Platform.

## Zeitreihendaten

Zeitreihendaten liefern eine Momentaufnahme des Systems zu dem Zeitpunkt, zu dem eine Aktion entweder direkt oder indirekt von einem Datensatzsubjekt durchgeführt wurde. Wenn beispielsweise ein Käufer ein Produkt auf Ihrer Site durchsucht, zum Warenkorb hinzufügt, eine Bestellung aufgibt usw. Zeitreihendaten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf **Erlebnisereignis** festgelegt ist.

### Erfasste Zeitreihendaten

Unter [Verhaltensereignisse](events.md) und [Backoffice-Ereignisse](events-backoffice.md) erfahren Sie, welche Daten beim Generieren eines Zeitreihenereignisses erfasst werden.

### Für die Erfassung von Zeitreihenereignisdaten benötigtes Schema

Erfahren Sie, wie Sie [ein Schema ](update-xdm.md) erstellen, das verhaltensbezogene und Back-Office-Zeitreihenereignisdaten erfassen kann.

## Daten aufzeichnen

Datensatzdaten enthalten Informationen über die Attribute eines Subjekts. Ein Subjekt könnte eine Organisation oder eine Einzelperson sein. Beispielsweise erstellt ein Käufer auf Ihrer Site ein Konto und generiert Datensatzdaten. Diese Daten werden mithilfe eines Schemas in die Experience Platform aufgenommen, bei dem die Klasse auf **Individuelles Profil** gesetzt ist. Sie können diese Datensatzdaten an den Adobe-Profilverwaltungs- und Segmentierungsdienst senden: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=de).

### Erfassen von Profildatensätzen

Unter [Kundenprofil-Datensatzdaten](events-profilerecord.md) erfahren Sie, welche Daten erfasst werden, wenn ein Profildatensatz generiert wird.

### Zum Erfassen von Profildatensatzdaten benötigtes Schema

Erfahren Sie, wie Sie [ein Schema ](profile-data.md) erstellen, das Profildatensatzdaten erfassen kann.
