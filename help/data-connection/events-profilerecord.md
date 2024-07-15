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

Im Folgenden werden die Commerce-Profildatensatzdaten beschrieben, die bei der Installation der Erweiterung [!DNL Data Connection] verfügbar sind. Die Daten in Profildatensätzen werden an die Adobe Experience Platform gesendet.

## Profildatensatz

Aktualisierungen der Profildatensätze sind auf der Experience Platform verfügbar, wenn ein neues Profil erstellt, aktualisiert oder gelöscht wird.

### Aus dem Profildatensatz erfasste Daten

Im Folgenden werden die Daten beschrieben, die für einen Profildatensatz erfasst werden.

| Feld | Beschreibung |
|---|---|
| `channel` | Enthält Informationen zur Datenquelle. Sowohl `_id` als auch `_type` enthalten [Namespace-Werte](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/namespaces). |
| `channel._id` | Die eindeutige Kennung des Kanals, z. B. `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifiziert die Quelle der Kanaldaten, z. B. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Enthält Informationen zum Kunden. |
| `person.name` | Enthält Informationen zum Namen des Kunden. |
| `person.name.firstName` | Enthält den Vornamen des Kunden. |
| `person.name.lastName` | Enthält den Nachnamen des Kunden. |
| `person.birthDate` | Geburtsdatum des Käufers |
| `personalEmail` | Eine persönliche E-Mail-Adresse. |
| `personalEmail.address` | Die technische Adresse, z. B. `name@domain.com`, wie sie üblicherweise in RFC2822 und nachfolgenden Standards definiert ist. |
| `billingAddress` | Die Postadresse der Rechnungsstellung. |
| `billingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `billingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `billingAddress.city` | Der Name der Stadt. |
| `billingAddress.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `billingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Mit Ausnahme von `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `billingAddress.primary` | Gibt an, ob dies die primäre Rechnungsadresse ist. Der Wert ist immer `False`. |
| `billingAddressPhone` | Die mit der Rechnungsadresse verknüpfte Telefonnummer. |
| `billingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern `()`, Bindestriche `-` oder Zeichen enthalten kann, um IDs für Unterwählungen wie Erweiterungen `x` (z. B. `1-353(0)18391111` oder `+613 9403600x1234`) anzugeben. |
| `billingAddressPhone.primary` | Gibt an, ob dies die primäre Telefonnummer für die Abrechnungsadresse ist. Der Wert ist immer `False`. |
| `shippingAddress` | Die Postanschrift des Versands. |
| `shippingAddress.street1` | Primäre Straßeninformationen, Wohnungsnummer, Straßennummer und Straßenname. |
| `shippingAddress.street2` | Optionale Straßeninformationen, zweite Zeile. |
| `shippingAddress.city` | Der Name der Stadt. |
| `shippingAddress.state` | Der Name des Status. Dies ist ein Freiformfeld. |
| `shippingAddress.country` | Der Name des von der Regierung verwalteten Gebiets. Mit Ausnahme von `xdm:countryCode` ist dies ein Freiformfeld, das den Ländernamen in jeder Sprache enthalten kann. |
| `shippingAddress.primary` | Gibt an, ob dies die primäre Versandadresse ist. Der Wert ist immer `False`. |
| `shippingAddressPhone` | Die mit der Lieferadresse verknüpfte Telefonnummer. |
| `shippingAddressPhone.number` | Die Telefonnummer. Beachten Sie, dass die Telefonnummer eine Zeichenfolge ist und aussagekräftige Zeichen wie Klammern `()`, Bindestriche `-` oder Zeichen enthalten kann, um IDs für Unterwählungen wie Erweiterungen `x` (z. B. `1-353(0)18391111` oder `+613 9403600x1234`) anzugeben. |
| `shippingAddressPhone.primary` | Gibt an, ob dies die primäre Telefonnummer für die Versandadresse ist. Der Wert ist immer `False`. |
| `userAccount` | Gibt Details zu Treueprogramm, Voreinstellungen, Anmeldeprozesse und andere Kontovoreinstellungen an. |
| `userAccount.startDate` | Das Datum der ersten Erstellung des Profils. |

>[!NOTE]
>
>Jeder Profildatensatz enthält auch das Feld [`identityMap`](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/identitymap) , das die vom System generierte Commerce-Kunden-ID als primäre Kennung für das Profil und eine E-Mail-ID enthält, die als sekundäre Kennung verwendet wird.

Erfahren Sie, wie Sie [ein profildatensatzspezifisches Schema ](profile-data.md) erstellen, das die Daten aus Ihren Profildatensätzen aufnehmen kann.
