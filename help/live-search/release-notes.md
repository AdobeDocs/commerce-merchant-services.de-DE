---
title: "[!DNL Live Search] Versionshinweise"
description: "Die neuesten Versionsinformationen für [!DNL Live Search] von Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 20b4fc2dc0f6cba325e4bc79778ce4852eb189c2
workflow-type: tm+mt
source-wordcount: '1925'
ht-degree: 0%

---

# [!DNL Live Search] Versionshinweise

Diese Versionshinweise beschreiben die neuesten Versionen von [!DNL Live Search].
Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

## Aktualisierungen gehosteter Dienste

Diese Hinweise beschreiben Aktualisierungen, die außerhalb einer versionierten Version veröffentlicht wurden, oder Verbesserungen am gehosteten Dienst.

_13. Februar 2024_

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt das Festlegen einer Standardregel für [Merchandising durchsuchen](rules.md).

_27. Oktober 2023_

![Neu](../assets/new.svg) Die [!DNL Live Search] Das PLP-Widget unterstützt jetzt Farbmuster.

_12. Oktober 2023_

![Neu](../assets/new.svg) Commerce-Administratoren können jetzt die Indexsprache für [!DNL Live Search]. Siehe [Einstellungen](settings.md).
![Fehlerbehebung](../assets/fix.svg) Die Registerkarte &quot;Suchregeln&quot;wurde in &quot;Merchandising durchsuchen&quot;umbenannt.

_13. Juni 2023_

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem einige Zeichen wie Anführungszeichen oder Apostrophe Ranking-Probleme verursachten. Durch die Neuindizierung werden diese Probleme gelöst.

_25. April 2023_

![Neu](../assets/new.svg) [!DNL Live Search] Kunden können jetzt die neue [SaaS-Preisindexer](../price-index/price-indexing.md).

## [!DNL Live Search] 4.1.1 {#411}

_19.03.2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Sprachunterstützung für [polnisch](technical-overview.md#language-support).
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.3 für Installationen mit Adobe Commerce 2.4.7.

## [!DNL Live Search] 4.1.0 {#410}

_22.02.2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Die [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search], und [!DNL Catalog Service].
![Neu](../assets/new.svg) Mehrere neue Funktionen wurden zum [PLP-Widget](plp-styling.md):

* Umschalten zwischen Listen-/Rasteransicht
* Schaltflächen &quot;Zum Warenkorb hinzufügen&quot;
* Musterunterstützung
* Mehrere Bilder pro Produkt
* Preisregler
* Sprachunterstützung

Merchandising muss die [!DNL Live Search] Erweiterung auf Version >= 4.1.0 , um auf diese Funktionen zuzugreifen.

### Updates

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Fehler behoben, der zu einem Fehler führte, wenn Gastbenutzer Produkte in nicht standardmäßigen Store-Ansichten zum Warenkorb hinzugefügt haben.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Fehler behoben, der dazu führte, dass im Suchmenü unabhängig von den Gebietsschemaeinstellungen immer das Währungssymbol vor dem Preiswert angezeigt wurde.
![Fehlerbehebung](../assets/fix.svg) Es wurden unnötige Typdefinitionen für deaktivierte Core-Plug-ins entfernt, um Kompatibilitätsprobleme bei der Installation zu beheben.

## [!DNL Live Search] 4,0,0 {#400}

_13. November 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Farbmuster im PLP-Widget.
![Neu](../assets/new.svg) [!DNL Live Search] zeigt nun den Kategorienamen anstelle der Kategorie-ID an.
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Durchstreichen-Preise im PLP-Widget.
![Neu](../assets/new.svg) Die Schaltfläche &quot;Filter ausblenden&quot;wurde eingeführt, um den Filterbereich auszublenden.


### Updates

![Fehlerbehebung](../assets/fix.svg) Die [!DNL Live Search] PLP-Widget ist jetzt standardmäßig für neue Installationen aktiviert.
![Fehlerbehebung](../assets/fix.svg) CSS-Stile wurden neu konfiguriert, um Widget-Klassen besser zu isolieren.
![Fehlerbehebung](../assets/fix.svg) Geringfügige Fehlerbehebungen

Aktivieren Sie nach der Installation von Version 3.1.1 oder höher die neuen Indexer:

* Produktpreis-Feed
* Umfang des Website-Daten-Feeds
* Umfang des Daten-Feeds von Kundengruppen

Testen Sie nach dem Upgrade die aktualisierte Konfiguration in QA oder Staging, bevor Sie die Änderungen in die Produktion übernehmen.

## Frühere Versionen

+ + + 3.1.1 und früher

## [!DNL Live Search] 3.1.1 {#311}

_15. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die neue Registerkarte Kategorie-Merchandising wurde hinzugefügt. Benutzer können jetzt intelligente Ranglisten und manuelle Ranglisten (Pin, Verstärken, Begraben, Verbergen) pro Kategorie hinzufügen
![Neu](../assets/new.svg) Benutzer können eine einzelne Kategorieregel mit intelligentem oder manuellem Rang hinzufügen
![Neu](../assets/new.svg) Benutzer können nun intelligente Ranking-Regeln zu Unterkategorien hinzufügen
![Neu](../assets/new.svg) Beim Löschen von Unterkategorien mit intelligentem Rang werden detaillierte Informationen bereitgestellt.
![Neu](../assets/new.svg) Die Möglichkeit zum Löschen von Regeln für geerbte Ranking-Strategien wurde hinzugefügt.
![Neu](../assets/new.svg) Die Möglichkeit zum Löschen von Regeln für eine Kategorie wurde hinzugefügt.
![Neu](../assets/new.svg) Benutzer können jetzt beim Hinzufügen einer Regel nach Kategoriename suchen
![Neu](../assets/new.svg) Mit der Ansicht &quot;Kategoriestruktur&quot;können Benutzer jetzt anzeigen, auf welche Kategorie Regeln angewendet wurden.
![Neu](../assets/new.svg) Die Kategorievorschau zeigt nur die ausgewählte Kategorie an.
![Neu](../assets/new.svg) AEM CIF [Popover-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/319) und [PLP-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) Komponenten ermöglichen es AEM Sites, von [!DNL Live Search].

### Updates

![Fehlerbehebung](../assets/fix.svg) Die Tabellengröße der Produkt- und Preis-Feeds wurde stark reduziert. Tabellen `catalog_data_exporter_products` und `catalog_data_exporter_product_prices` eine erhebliche Reduzierung der Größe vorsehen.
![Fehlerbehebung](../assets/fix.svg) Die Registerkarte &quot;Regeln&quot;wird in &quot;Suchregeln&quot;umbenannt.
![Fehlerbehebung](../assets/fix.svg) Bei der Rangfolge nach &quot;Trend&quot;können Sie jetzt zwischen: * 3 Tage (Standard) * 14 Tage * 30 Tage auswählen
![Fehlerbehebung](../assets/fix.svg) &quot;Ereignisse&quot;(Verstärken/Einfügen/Verbergen/Ausblenden) wurde in &quot;Manuelles Ranking&quot;umbenannt.
![Fehlerbehebung](../assets/fix.svg) &quot;Ranking Type&quot;wurde in &quot;Intelligent ranking&quot;umbenannt.
![Fehlerbehebung](../assets/fix.svg) Geringfügige Fehlerbehebungen

## [!DNL Live Search] 3.1.0 {#310}

_1. September 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Updates

![Fehlerbehebung](../assets/fix.svg) Das Widget &quot;Produktliste&quot;wurde aktualisiert und verwendet nun die [Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3,0,2 {#302}

_7. August 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Die folgenden Werte wurden zum `storeDetails` -Objekt:

* &quot;Alle Produkte pro Seite zulassen&quot;
* Währungskurs
* &quot;Products per Page on Grid Allowed Values&quot;
* &quot;Products per Page on Grid Default Value&quot;
* Store language

### Updates

![Fehlerbehebung](../assets/fix.svg) Dem Metapaket wurden Catalog Service-Module hinzugefügt, um den erweiterten Datenabruf zu unterstützen.
![Fehlerbehebung](../assets/fix.svg) Die **Mein Konto** Die Seitennavigation verschwindet nicht mehr bei Verwendung des Widgets &quot;Produktauflistungsseite&quot;.

Merchandising muss die [!DNL Live Search] -Erweiterungsversion >= 3.0.2 verwenden, um auf diese Funktionen zuzugreifen.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### Einschränkungen

Die Verwendung des Widgets &quot;Live Search Product Listing Page&quot;führt dazu, dass der Google Tag Manager fehlschlägt. Verwenden Sie den standardmäßigen Suchadapter, wenn der Google Tag Manager erforderlich ist.

## [!DNL Live Search] 3,0,1 {#301}

_14. März 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Produktelementkarte in der Vorschau für Regeln
![Neu](../assets/new.svg) [Widget &quot;Seite für Produktauflistung&quot;](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![Neu](../assets/new.svg) [Filteroptionen für Kategorien](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Neu](../assets/new.svg) Die Möglichkeit, Pin-Ereignisse per Drag &amp; Drop zu erstellen, wurde hinzugefügt
![Neu](../assets/new.svg) Neue Pin-Aktionen: * An Position fixieren - Schaltfläche &quot;Pin&quot;, um ein Pin-Ereignis mit einem Klick zu erstellen * Pin to top - Setzt das Produkt an die erste Position * Pin to bottom - Platziert das Produkt am unteren Ende der Ergebnisse * Passen Sie ein Ereignis mit einem Klick auf
![Neu](../assets/new.svg) [Intelligente Rangordnung für Regeln](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt vollständig [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Funktionen in Commerce (ehemals &quot;Multi-Source Inventory&quot;oder &quot;MSI&quot;). Um den vollständigen Support zu ermöglichen, müssen Sie [update](install.md#update) das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+.

### Updates

![Fehlerbehebung](../assets/fix.svg) Regeln jetzt automatisch konfigurieren Sortiert Positionen einmalig
![Fehlerbehebung](../assets/fix.svg) Beim Löschen eines vorhandenen Ereignisses wird jetzt die Vorschau aktualisiert.
![Fehlerbehebung](../assets/fix.svg) Regeln ohne Ereignisse können gespeichert werden
![Fehlerbehebung](../assets/fix.svg) Facettenauswahl &quot;Typ auswählen&quot;entfernen
![Fehlerbehebung](../assets/fix.svg) Neuer Status &quot;Bearbeiten&quot;für nicht gespeicherte Regeln hinzugefügt

### Fehlerbehebungen

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Serverfehler behoben, der auftrat, wenn beim Speichern ein nicht abgeschlossenes Ereignis auftrat
![Fehlerbehebung](../assets/fix.svg) Korrektur des korrekten Löschens eines bestimmten Ereignisses bei mehreren Ereignissen
![Fehlerbehebung](../assets/fix.svg) Fehlerkorrektur - Das vorhandene Regelereignis wird jetzt aktualisiert, wenn ein neues Ereignis hinzugefügt wird
![Fehlerbehebung](../assets/fix.svg) Beim zweiten &quot;Bearbeiten&quot;-Klick aus Details behoben, [!DNL Live Search] Seite muss neu geladen werden
![Fehlerbehebung](../assets/fix.svg) Synonyme: Es wurde ein Problem behoben, bei dem ein Benutzer, der auf die Eingabe klickte, den Fokus nicht auf das Feld zurücksetzen konnte.
![Fehlerbehebung](../assets/fix.svg) Andere kleinere Fehlerbehebungen und Leistungsaktualisierungen


![Fehler](../assets/bug.svg) - Die Rangordnung nach &quot;Empfohlen für Sie&quot;wird nur in den Live-Suche-Widgets unterstützt. Sie wird von der standardmäßigen Luma- und PWA-Suchfunktion nicht unterstützt.
![Fehler](../assets/bug.svg) - Benutzerdefinierte Preisattribut-Facetten werden in Luma nicht korrekt dargestellt, aber die API filtert sie ordnungsgemäß.

Merchandising muss die [!DNL Live Search] -Erweiterungsversion >= 3.0.1 verwenden, um auf diese Funktionen zuzugreifen.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

## [!DNL Live Search] 2,0,5 {#205}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Fehlerbehebung](../assets/fix.svg) - Die Live-Suche würde einen Fehler auslösen, wenn SDK-Ressourcen aufgrund von Netzwerkproblemen nicht verfügbar waren. Dieser Fehler wurde behoben.

Händler müssen die Live Search-Erweiterung Version >= 2.0.5 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2,0,4 {#204}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Live-Suche unterstützt jetzt das Filtern nach der Einstellung &quot;Nicht vorrätige Produkte anzeigen&quot;im Admin. Wenn &quot;Nicht vorrätige Produkte anzeigen&quot;auf &quot;false&quot;gesetzt ist, `inStock = true` wird zum Filter hinzugefügt.
![Fehlerbehebung](../assets/fix.svg) Um die Leistung zu verbessern, wurde der Block &quot;Vorschläge&quot;aus dem Popup-Fenster &quot;Live-Suche&quot;entfernt. Die Daten werden weiterhin über GraphQL übergeben, falls Sie die Funktion ersetzen möchten.
![Fehlerbehebung](../assets/fix.svg) `categories` und `categoryPath` ersetzt `categoryIds` für die Kategoriefilterung. Weitere Informationen finden Sie unter [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) Thema.
![Fehlerbehebung](../assets/fix.svg) Zuvor erhielt ein Benutzer, der an ein B2B-Unternehmen gebunden war, bei der Suche einen falschen Kundengruppen-Code. Die Live-Suche gibt jetzt den richtigen Wert zurück.
![Fehlerbehebung](../assets/fix.svg) Bisher gab die Live-Suche bei der Suche nach einem nicht vorhandenen Begriff einen Fehler zurück. Dieser Fehler wurde nun behoben.

Merchandising muss die [!DNL Live Search] -Erweiterungsversion >= 2.0.4 verwenden, um auf diese Funktionen zuzugreifen.

Benutzern wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2,0,3 {#203}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) Live Search unterstützt jetzt B2B-Funktionen durch Berücksichtigung von Kategorieberechtigungen, freigegebenen Katalogen und kundengruppenspezifischen Preisen.

Merchandising muss die [!DNL Live Search] Erweiterungsversion >= 2.0.3 verwenden, um auf diese Funktionen zuzugreifen.

Benutzern wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2,0 {#20}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

Bestehend [!DNL Live Search] -Installationen müssen aktualisiert werden auf [!DNL Live Search] 2.0.0 nutzen, um die folgenden neuen Funktionen, Fehlerbehebungen und Verbesserungen zu nutzen:

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.1 für Installationen mit Adobe Commerce 2.4.4.
![Neu](../assets/new.svg) Die `Magento_ElasticsearchCatalogPermissionsGraphQl` -Modul wird zur Liste der Module hinzugefügt, die während der Installation deaktiviert werden.
![Neu](../assets/new.svg) Die Anzahl der verfügbaren Zeilen im [[!DNL storefront popover]](quick-tour.md) kann über die *Admin*.
![Neu](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) unterstützt für [!DNL Live Search].
![Neu](../assets/new.svg) Die [!DNL Live Search] Der Installationsprozess wird mit erweiterten Prozessänderungen aktualisiert.
![Fehlerbehebung](../assets/fix.svg) [Erweiterte Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) -Link aus der Fußzeile der Storefront entfernt.
![Fehler](../assets/bug.svg) Die folgenden Produktattribute werden nicht von [Commerce GraphQL-API](https://developer.adobe.com/commerce/services/graphql/live-search/) bei Verwendung im Zusammenhang mit der Betaversion von PWA: `description`, `name`, `short_description`
![Fehler](../assets/bug.svg) Die Beta-Version von PWA für [!DNL Live Search] unterstützt nicht [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Fehlerbehebung](../assets/fix.svg) [Benutzerdefiniertes Preisattribut](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) gibt keinen Fehler mehr zurück, wenn die Konfiguration als [facet]({% link live-search/facets-add.md %}).
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Fehler behoben, der dazu führte, dass ein Fehler auftrat, wenn [Währungssymbol](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration(optional)) (`data-currency-symbol`) verfügbar ist.
![Fehlerbehebung](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) zeigt nun die [Sonderpreis](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) (Endpreis), sofern verfügbar.

### [!DNL Live Search] 1,3,0 {#130}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) [Leistung](performance.md) Das Berichterstellungs-Dashboard bietet Einblicke in Suchbegriffe, die von Käufern verwendet werden.
![Neu](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) bietet Zugriff auf eine gemeinsame Datenschicht mit Ereignisveröffentlichungs- und Abonnementdiensten sowie Metriken.
![Fehlerbehebung](../assets/fix.svg) Die [[!DNL Storefront popover]](storefront-popover.md) hat eine neue `active` -Klasse für `.search-autocomplete` Container, der die Sichtbarkeit steuert.
![Fehlerbehebung](../assets/fix.svg) In der Storefront wird die [Suchbegriffe](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) Fußzeilenlink entfernt und sein Cache für [!DNL Live Search] Installationen.
![Fehler](../assets/bug.svg) Patch for Search Adapter handhabt doppelte Produkte.
![Fehler](../assets/bug.svg) [!DNL Live Search] unterstützt [einzelne Quelle](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) (physische) Inventarstandorte mit mehreren (virtuellen) [Bestände](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). Mehrere Inventarquellen werden jetzt nicht mehr unterstützt.

### [!DNL Live Search] 1,2,0 {#120}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) zeigt empfohlene Produkte und Miniaturansichten der wichtigsten Suchergebnisse an, wenn Käufer Abfragen in das Suchfeld eingeben.
![Neu](../assets/new.svg) Commerce *Admin* -Sitzung bleibt während längerer Zeiträume der Tastaturinaktivität geöffnet
![Neu](../assets/new.svg) [!DNL Live Search] wird nach dem Onboarding automatisch aktiviert
![Fehlerbehebung](../assets/fix.svg) Die anfängliche Indizierungszeit beträgt weniger als eine Stunde
![Fehlerbehebung](../assets/fix.svg) Inkrementelle Produktupdates nahezu in Echtzeit (nach Installation und Einrichtung)
![Fehlerbehebung](../assets/fix.svg) Sortierbare Spalten im Synonym-Editor
![Fehlerbehebung](../assets/fix.svg) [!DNL Live Search] kein Fehler mehr auslöst, wenn Suchkriterien einen leeren Sortierreihenfolgenwert enthalten
![Fehlerbehebung](../assets/fix.svg) Die Bereichsfilterung wird nicht mehr umgebrochen, wenn Attributcodes die Zeichenfolgen &quot;to&quot;oder &quot;from&quot;enthalten

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Fehler](../assets/bug.svg) Die [!DNL Live Search] -Dienst unterstützt nur die [Basiswährung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) der Adobe Commerce-Installation.
![Fehler](../assets/bug.svg) Beim Hinzufügen einer Facette wird der Produktattribut-Feed nicht ordnungsgemäß aktualisiert, wenn auf `Update on Save`. Um dieses Problem zu vermeiden, gehen Sie zu [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) und legen Sie den Produktattribut-Feed auf `Update by Schedule`.
![Fehler](../assets/bug.svg) [!DNL Live Search] Synonyme werden pro Store-Ansicht definiert, derzeit jedoch pro Website gespeichert und mit einer Kombination aus `environmentId` und `storeViewCode`. Daher verwenden alle Websites und Speicheransichten innerhalb der Adobe Commerce-Installation Synonyme. Der zuletzt erstellte Satz von Synonymen für die Store-Ansicht hat Vorrang.
![Fehler](../assets/bug.svg) Wenn ein Synonym mehrere Wörter enthält, wird jedes Wort als separates Synonym behandelt. Wenn Sie beispielsweise &quot;Zeitelement&quot;als Synonym für &quot;Uhr&quot;definieren, werden sowohl &quot;Zeit&quot;als auch &quot;Stück&quot;als Uhrensynonyme behandelt.

+++

## Dokumentation

Weitere Informationen:

* [Dokumentation für Adobe Commerce-Entwickler](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/commerce)
* [[!DNL Live Search] auf Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
