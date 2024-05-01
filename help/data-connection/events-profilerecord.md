---
title: Profildatensätze
description: Erfahren Sie, welche Daten ein Profildatensatz erfasst.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: c02496fb3f88f4781b79c5e477d5508c3e3d5224
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# [!DNL Data Connection] Profildatensätze (Beta)

Im Folgenden werden die Commerce-Profildatensatzdaten beschrieben, die bei der Installation der [!DNL Data Connection] -Erweiterung. Die Daten in Profildatensätzen werden an die Adobe Experience Platform gesendet.

## Profildatensatz

Aktualisierungen der Profildatensätze sind auf der Experience Platform verfügbar, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird.

### Aus dem Profildatensatz erfasste Daten

Im Folgenden werden die Daten beschrieben, die für einen Profildatensatz erfasst werden.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Beide `_id` und `_type` contain [Namensraum-Werte](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/namespaces). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `person.birthDate` | Geburtsdatum des Käufers |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, beispielsweise `name@domain.com` wie allgemein in RFC2822 und nachfolgenden Standards definiert. |
| `billingAddress` | Die Postadresse der Rechnungsstellung. |
| `billingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `billingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `billingAddress.city` | Der Name der Stadt. |
| `billingAddress.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `billingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `billingAddress.primary` | Gibt an, ob dies die primäre Rechnungsadresse ist. Wert ist immer `False`. |
| `billingAddressPhone` | Die mit der Rechnungsadresse verknüpfte Telefonnummer. |
| `billingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern enthalten kann. `()`, Bindestriche `-`, oder Zeichen, um IDs für Unterwählungen wie Erweiterungen anzugeben `x` Beispiel:  `1-353(0)18391111` oder `+613 9403600x1234`. |
| `billingAddressPhone.primary` | Gibt an, ob dies die primäre Telefonnummer für die Abrechnungsadresse ist. Wert ist immer `False`. |
| `shippingAddress` | Die Postanschrift des Versands. |
| `shippingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `shippingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `shippingAddress.city` | Der Name der Stadt. |
| `shippingAddress.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `shippingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Andere als `xdm:countryCode`, ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `shippingAddress.primary` | Gibt an, ob dies die primäre Versandadresse ist. Wert ist immer `False`. |
| `shippingAddressPhone` | Die mit der Lieferadresse verknüpfte Telefonnummer. |
| `shippingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern enthalten kann. `()`, Bindestriche `-`, oder Zeichen, um IDs für Unterwählungen wie Erweiterungen anzugeben `x` Beispiel:  `1-353(0)18391111` oder `+613 9403600x1234`. |
| `shippingAddressPhone.primary` | Gibt an, ob dies die primäre Telefonnummer für die Versandadresse ist. Wert ist immer `False`. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.startDate` | Das Datum der ersten Erstellung des Profils. |

>[!NOTE]
>
>Jeder Profildatensatz enthält auch [`identityMap`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/identitymap) -Feld, das die systemgenerierte Commerce-Kunden-ID als primäre Kennung für das Profil und eine E-Mail-ID als sekundäre Kennung enthält.

Erfahren Sie, wie [Erstellen eines profildatensatzspezifischen Schemas](profile-data.md) die die Daten aus Ihren Profildatensätzen aufnehmen können.
