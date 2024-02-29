---
title: Profildatensätze
description: Erfahren Sie, welche Daten ein Profildatensatz erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# [!DNL Data Connection] Profildatensätze

Im Folgenden werden die Commerce-Profildatensätze beschrieben, die bei der Installation der [!DNL Data Connection] -Erweiterung. Die Daten in Profildatensätzen werden an die Adobe Experience Platform gesendet.

## Profildatensatz

Aktualisierungen der Profildatensätze sind auf der Experience Platform verfügbar, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird.

### Aus dem Profildatensatz erfasste Daten

Im Folgenden werden die Daten beschrieben, die für einen Profildatensatz erfasst werden.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Beide `_id` und `_type` contain [Namensraum-Werte](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `person.birthDate` | Geburtsdatum des Käufers |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.startDate` | Das Datum der ersten Erstellung des Profils. |

>[!NOTE]
>
>Jeder Profildatensatz enthält auch [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -Feld, das die E-Mail-Adresse des Käufers, sofern verfügbar, sowie die ECID enthält.

Erfahren Sie, wie [Erstellen eines profildatensatzspezifischen Schemas](profile-data.md) die die Daten aus Ihren Profildatensätzen aufnehmen können.
