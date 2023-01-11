---
title: "Onboarding-Übersicht"
description: "[!DNL Live Search] Onboarding-Fluss, Systemanforderungen, Grenzen und Einschränkungen"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Onboarding-Übersicht

Erste Schritte mit [!DNL Live Search] Führen Sie für Adobe Commerce den Onboarding-Prozess aus, um die Erweiterung zu installieren, Ihre API-Schlüssel zu konfigurieren und Ihren Katalog zu synchronisieren.

## Onboarding-Fluss

![[!DNL Live Search] Onboarding-Diagramm](assets/onboarding-flow.svg)

## Voraussetzungen {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Unterstützte Plattformen

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Grenzen und Schwellenwerte

Zu diesem Zeitpunkt wird die [!DNL Live Search] Die Such-/Kategorie-API weist die folgenden unterstützten Einschränkungen und statischen Begrenzungen auf:

### Indizierung

* Indexiert bis zu 300 Produktattribute pro Store-Ansicht.
* Indiziert nur Produkte aus der Adobe Commerce-Datenbank.
* CMS-Seiten werden nicht indiziert.

### Abfrage

* [!DNL Live Search] hat keinen Zugriff auf die vollständige Taxonomie des Kategoriebaums, wodurch einige Navigationsszenarien mit Ebenen über die Reichweite hinausgehen.
* [!DNL Live Search] verwendet einen eindeutigen GraphQL-Endpunkt für Abfragen, um Funktionen wie intelligente Facettierung und Suche nach dem eigenen Typ zu unterstützen. Obwohl ähnlich der [Magento GraphQL-API](https://developer.adobe.com/commerce/webapi/graphql/), gibt es einige Unterschiede und einige Felder sind derzeit möglicherweise nicht vollständig kompatibel.

### Regeln

* Maximale Regelanzahl pro Store-Ansicht ist 50.
* Maximale Anzahl an Bedingungen pro Regel ist 10.
* Maximale Anzahl an Ereignissen pro Regel ist 25.

### Synonyme

* [!DNL Live Search] kann bis zu 200 Synonyme pro Store-Ansicht verwalten.

### PWA Beta-Version

* Die aktuelle Beta-PWA-Implementierung der Live-Suche erfordert mehr Verarbeitungszeit, um Suchergebnisse zurückzugeben, als die Live-Suche mit der nativen Commerce-Storefront.
* Die Beta-Version von PWA für [!DNL Live Search] unterstützt nicht [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Die folgenden Produktattribute werden von GraphQL nicht unterstützt, wenn sie im Zusammenhang mit der Beta-Version von [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Derzeit nicht unterstützt

* Die [Erweiterte Suche](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) -Modul deaktiviert ist, wenn [!DNL Live Search] installiert ist und der Link Erweiterte Suche in der Fußzeile der Storefront entfernt wird.
* [Benutzerspezifische Preisgruppen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Mehrere Lagerorte, die von [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) oder anderen OMS-Erweiterungen
* Die Produktpreise beinhalten nicht [Mehrwertsteuer](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (MwSt).
