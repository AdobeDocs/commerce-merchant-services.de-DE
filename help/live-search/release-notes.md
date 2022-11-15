---
title: "[!DNL Live Search] Versionshinweise"
description: "Die neuesten Versionsinformationen für [!DNL Live Search] von Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 87b60e28e45466bf4271953c6704a53e6d43d73a
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 1%

---

# [!DNL Live Search] Versionshinweise

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Live Search] und umfassen:

* ![Neu](../assets/new.svg) - Neue Funktionen
* ![Fehlerbehebung](../assets/fix.svg) - Fehlerbehebungen und Verbesserungen
* ![Fehler](../assets/bug.svg) - Bekannte Probleme

## [!DNL Live Search] 2,0,5

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Fehlerbehebung](../assets/fix.svg) - Die Live-Suche würde einen Fehler auslösen, wenn SDK-Ressourcen aufgrund von Netzwerkproblemen nicht verfügbar waren. Dieser Fehler wurde nun behoben.

Händler müssen die Live Search-Erweiterung Version >= 2.0.5 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

## [!DNL Live Search] 2,0,4

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Neu](../assets/new.svg) - Die Live-Suche unterstützt jetzt das Filtern nach der Einstellung &quot;Nicht vorrätige Produkte anzeigen&quot;im Admin. Wenn &quot;Nicht vorrätige Produkte anzeigen&quot;auf &quot;false&quot;gesetzt ist, `inStock = true` wird zum Filter hinzugefügt.
* ![Fehlerbehebung](../assets/fix.svg) - Zur Leistungsverbesserung wurde der Block &quot;Vorschläge&quot;aus dem Popup-Fenster &quot;Live-Suche&quot;entfernt. Die Daten werden weiterhin über GraphQL weitergeleitet, falls Sie die Funktion ersetzen möchten.
* ![Fehlerbehebung](../assets/fix.svg) - `categories` und `categoryPath` ersetzt `categoryIds` für die Kategoriefilterung. Mehr dazu im [productSearch](https://devdocs.magento.com/live-search/product-search.html#filter) Thema.
* ![Fehlerbehebung](../assets/fix.svg) - Zuvor erhielt ein Benutzer, der mit einem B2B-Unternehmen verbunden war, bei der Suche einen falschen Kundengruppen-Code. Die Live-Suche gibt jetzt den richtigen Wert zurück.
* ![Fehlerbehebung](../assets/fix.svg) - Bisher gab die Live-Suche bei der Suche nach einem nicht vorhandenen Begriff einen Fehler zurück. Dieser Fehler wurde nun behoben.

Händler müssen die Live Search-Erweiterung Version >= 2.0.4 aktualisieren, um auf diese Funktionen zugreifen zu können.

## [!DNL Live Search] 2,0,3

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Neu](../assets/new.svg) - Live Search unterstützt jetzt B2B-Funktionen durch Berücksichtigung von Kategorieberechtigungen, freigegebenen Katalogen und kundengruppenspezifischen Preisen.

Händler müssen die Live Search-Erweiterung Version >= 2.0.3 aktualisieren, um auf diese Funktionen zugreifen zu können.

Wir empfehlen Benutzern, ein Upgrade durchzuführen und zu testen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

>[!NOTE]
>
>B2B-Unterstützung wird schrittweise ab dem 9. August in den Backend-Services hinzugefügt, wobei die Migration voraussichtlich Ende August abgeschlossen sein wird. Wenn die Live Search-Erweiterung nicht aktualisiert wird, funktioniert Ihre Storefront weiterhin normal, jedoch ohne B2B-Funktionen.

### Bekannte Einschränkungen/Fehler:

* ![Fehler](../assets/bug.svg) - Vorschläge stammen aus Produkten, die der Kundengruppe nicht angezeigt werden können.
* ![Fehler](../assets/bug.svg) - Produkte werden nicht angezeigt, wenn sie nicht zum &quot;freigegebenen Standardkatalog&quot;hinzugefügt wurden.
* ![Fehler](../assets/bug.svg) - Der Suchadapter rendert den Behälter &quot;Nein&quot;für boolesche Produktattribute nicht, obwohl Produkte mit dem -Attribut konfiguriert sind und der Behälter &quot;Nein&quot;in der Antwort zurückgegeben wird.
* Während einige Produkte und Abfragen nicht-englische Ergebnisse zurückgeben können, werden mehrsprachige Abfragen derzeit nicht unterstützt.
* B2B mit Live Search for PWA Studio ist erst verfügbar, wenn PWA Studio Unterstützung dafür hinzufügt.
* Produktüberschreibungen und Produktattribut-Feeds können Synchronisierungsprobleme aufweisen, die die Ausführung von Administratoren erfordern `bin/magento indexer:reset` und `bin/magento indexer:reindex` , um die Synchronisierung korrekt zu wiederholen.
* Wenn Sie die Catalog Permissions/Shared Catalog/B2B-Funktionen aktivieren oder deaktivieren, wird die `catalog_data_exporter_product_overrides` Indexer wird nicht aktualisiert und fälschlicherweise als `valid`. Verwendung `bin/magento saas:resync --feed=productOverrides` , um das Problem zu beheben.

## [!DNL Live Search] 2,0

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

Bestehend [!DNL Live Search] -Installationen müssen aktualisiert werden auf [!DNL Live Search] 2.0.0 nutzen, um die folgenden neuen Funktionen, Fehlerbehebungen und Verbesserungen zu nutzen:

* ![Neu](../assets/new.svg) - [!DNL Live Search] unterstützt jetzt PHP 8.1 für Installationen mit Adobe Commerce 2.4.4.
* ![Neu](../assets/new.svg) - die `Magento_ElasticsearchCatalogPermissionsGraphQl` -Modul wird zur Liste der Module hinzugefügt, die während der Installation deaktiviert werden.
* ![Neu](../assets/new.svg) - Die Anzahl der verfügbaren Zeilen im [[!DNL storefront popover]](quick-tour.md) kann über die *Admin*.
* ![Neu](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) Kompatibilität für [!DNL Live Search].
* ![Neu](../assets/new.svg) - die [!DNL Live Search] Der Installationsprozess wird mit erweiterten Prozessänderungen aktualisiert.
* ![Fehlerbehebung](../assets/fix.svg) - [Erweiterte Suche](https://docs.magento.com/user-guide/catalog/search-advanced.html) -Link aus der Fußzeile der Storefront entfernt.
* ![Fehler](../assets/bug.svg) - Die folgenden Produktattribute werden von [Magento GraphQL-API](https://devdocs.magento.com/guides/v2.4/graphql) bei Verwendung im Zusammenhang mit der Betaversion von PWA: `description`, `name`, `short_description`
* ![Fehler](../assets/bug.svg) - Die Beta-Version von PWA für [!DNL Live Search] unterstützt nicht [Ereignisverarbeitung](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Fehlerbehebung](../assets/fix.svg) - [Benutzerdefiniertes Preisattribut](https://docs.magento.com/user-guide/stores/attributes-input-types.html) gibt keinen Fehler mehr zurück, wenn die Konfiguration als [facet]({% link live-search/facets-add.md %}).
* ![Fehlerbehebung](../assets/fix.svg) - Korrektur eines Fehlers, der dazu führte, dass ein Fehler auftrat, wenn [Währungssymbol](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) verfügbar ist.
* ![Fehlerbehebung](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) zeigt nun die [Sonderpreis](https://docs.magento.com/user-guide/catalog/product-price-special.html) (Endpreis), sofern verfügbar.

## [!DNL Live Search] 1,3,0

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Neu](../assets/new.svg) - [Leistung](performance.md) Das Berichterstellungs-Dashboard bietet Einblicke in Suchbegriffe, die von Käufern verwendet werden.
* ![Neu](../assets/new.svg) - [!DNL Live Search] [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) bietet Zugriff auf eine gemeinsame Datenschicht mit Ereignisveröffentlichungs- und Abonnementdiensten sowie Metriken.
* ![Fehlerbehebung](../assets/fix.svg) - die [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) hat eine neue `active` -Klasse für `.search-autocomplete` Container, der die Sichtbarkeit steuert.
* ![Fehlerbehebung](../assets/fix.svg) - In der Storefront wird die [Suchbegriffe](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) Fußzeilenlink entfernt und sein Cache für [!DNL Live Search] Installationen.
* ![Fehler](../assets/bug.svg) - Patch for Search Adapter handhabt doppelte Produkte.
* ![Fehler](../assets/bug.svg) - [!DNL Live Search] unterstützt [einzelne Quelle](https://docs.magento.com/user-guide/catalog/inventory-sources.html) (physische) Inventarstandorte mit mehreren (virtuellen) [Bestände](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Mehrere Inventarquellen werden derzeit nicht unterstützt.

## [!DNL Live Search] 1,2,0

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Neu](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) zeigt empfohlene Produkte und Miniaturansichten der wichtigsten Suchergebnisse an, wenn Käufer Abfragen in das Suchfeld eingeben.
* ![Neu](../assets/new.svg) - Handel *Admin* -Sitzung bleibt während längerer Zeiträume der Tastaturinaktivität geöffnet
* ![Neu](../assets/new.svg) - [!DNL Live Search] wird nach dem Onboarding automatisch aktiviert
* ![Fehlerbehebung](../assets/fix.svg) - Die anfängliche Indizierungszeit beträgt weniger als eine Stunde
* ![Fehlerbehebung](../assets/fix.svg) - Inkrementelle Produktupdates nahezu in Echtzeit (nach Installation und Einrichtung)
* ![Fehlerbehebung](../assets/fix.svg) - Sortierbare Spalten im Synonym-Editor
* ![Fehlerbehebung](../assets/fix.svg) - [!DNL Live Search] kein Fehler mehr auslöst, wenn Suchkriterien einen leeren Sortierreihenfolgenwert enthalten
* ![Fehlerbehebung](../assets/fix.svg) - Die Bereichsfilterung wird nicht mehr umgebrochen, wenn Attributcodes die Zeichenfolgen &quot;to&quot;oder &quot;from&quot;enthalten.

## [!DNL Live Search] 1.1.0

* Kompatibel mit Adobe Commerce (EE): 2.4.x
* Kompatibel mit Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilität: Stabil

* ![Fehler](../assets/bug.svg) - die [!DNL Live Search] -Dienst unterstützt nur die [Basiswährung](https://docs.magento.com/user-guide/stores/currency-configuration.html) der Adobe Commerce-Installation.
* ![Fehler](../assets/bug.svg) - Beim Hinzufügen einer Facette wird der Produktattribut-Feed nicht ordnungsgemäß aktualisiert, wenn auf `Update on Save`. Um dieses Problem zu vermeiden, gehen Sie zu [Indexverwaltung](https://docs.magento.com/user-guide/system/index-management.html) und legen Sie den Produktattribut-Feed auf `Update by Schedule`.
* ![Fehler](../assets/bug.svg) - [!DNL Live Search] Synonyme werden pro Store-Ansicht definiert, derzeit jedoch pro Website gespeichert und mit einer Kombination aus `environmentId` + `storeViewCode`. Daher verwenden alle Websites und Speicheransichten innerhalb der Adobe Commerce-Installation denselben Satz von Synonymen. Der zuletzt erstellte Satz von Synonymen für die Store-Ansicht hat Vorrang.
* ![Fehler](../assets/bug.svg) - Wenn ein Synonym mehrere Wörter enthält, wird jedes Wort als separates Synonym behandelt. Wenn Sie beispielsweise &quot;Zeitelement&quot;als Synonym für &quot;Uhr&quot;definieren, werden sowohl &quot;Zeit&quot;als auch &quot;Stück&quot;als Uhrensynonyme behandelt.

## Dokumentation

Weitere Informationen:

* [Adobe Commerce-Entwicklerdokumentation](https://devdocs.magento.com/)
* [Adobe Commerce-Benutzerhandbuch](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] auf Marketplace](https://marketplace.magento.com/magento-live-search.html)
