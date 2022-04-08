---
title: Onboarding-Übersicht
description: Onboarding-Fluss der Live-Suche, Systemanforderungen, Grenzen und Einschränkungen
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 67e0287d38eb81e17c1ae317c54d60a5c4816eab
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Onboarding-Übersicht

Um mit der Live-Suche für Adobe Commerce zu beginnen, müssen Sie einige Onboarding-Schritte ausführen, um die Erweiterung zu installieren, Ihre API-Schlüssel zu konfigurieren und Ihren Katalog zu synchronisieren.

## Onboarding-Fluss

![Onboarding-Diagramm für die Live-Suche](assets/onboarding-flow.svg)

## Voraussetzungen {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Unterstützte Plattformen

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Grenzen und Schwellenwerte

Derzeit hat die Live Search/Kategorie-API die folgenden unterstützten Einschränkungen und statischen Begrenzungen:

### Indizierung

* Indexiert bis zu 300 Produktattribute pro Store-Ansicht
* Indexiert nur Produkte aus der Adobe Commerce-Datenbank
* Indexiert keine CMS-Seiten

### Abfragebeschränkungen

* Die Live-Suche hat keinen Zugriff auf die vollständige Taxonomie des Kategoriebaums, wodurch einige Navigationsszenarien mit Ebenen über ihre Reichweite hinausgehen.
* Die Live-Suche verwendet einen eindeutigen GraphQL-Endpunkt für Abfragen, um Funktionen wie intelligente Facettierung und Suche nach dem eigenen Typ zu unterstützen. Obwohl ähnlich der [Magento GraphQL-API](https://devdocs.magento.com/guides/v2.4/graphql), gibt es einige Unterschiede und einige Felder sind derzeit möglicherweise nicht vollständig kompatibel.

### PWA Beta-Version

* Die Beta-Version von PWA für Live Search unterstützt nicht [Ereignisverarbeitung](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Die folgenden Produktattribute werden von GraphQL nicht unterstützt, wenn sie im Zusammenhang mit der Betaversion von [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Derzeit nicht unterstützt

* Die [Erweiterte Suche](https://docs.magento.com/user-guide/catalog/search-advanced.html) -Modul deaktiviert ist, wenn die Live-Suche installiert ist, und der Link Erweiterte Suche in der Fußzeile der Storefront entfernt wird.
* [Kundengruppen](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Benutzerspezifische Preisgruppen](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Mehrere Lagerorte, die von [MCOM](https://docs.magento.com/user-guide/mcom.html) oder anderen OMS-Erweiterungen
* [Integrierte B2B-Funktionen](https://business.adobe.com/products/magento/b2b-ecommerce.html)
