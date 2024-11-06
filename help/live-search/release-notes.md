---
title: "[!DNL Live Search] Versionshinweise"
description: "Die neuesten Versionsinformationen für [!DNL Live Search] aus Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 7f536c93ab1c87bf88bc892b2a485067fa8f8110
workflow-type: tm+mt
source-wordcount: '2042'
ht-degree: 0%

---

# [!DNL Live Search] Versionshinweise

In diesen Versionshinweisen werden die neuesten Versionen von [!DNL Live Search] beschrieben.
Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Zu den Aktualisierungen gehören:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

## Aktualisierungen gehosteter Dienste

Diese Hinweise beschreiben Aktualisierungen, die außerhalb einer versionierten Version veröffentlicht wurden, oder Verbesserungen am gehosteten Dienst.

_19. September 2024_

![Neu](../assets/new.svg) Eine Betaversion veröffentlicht, die drei neue Suchfunktionen unterstützt: &quot;Ebenen&quot;, &quot;Beginn mit&quot;und &quot;enthält&quot;. [Weitere Infos](install.md#install-the-live-search-beta).

_4. September 2024_

![Korrektur](../assets/fix.svg) Die maximale Anzahl von Buckets, die [innerhalb einer Facette](boundaries-limits.md#facets) zurückgegeben werden können, wurde auf 100 erhöht.

_7. August 2024_

![Korrektur](../assets/fix.svg) Der maximale Intervallwert oder Preisbereich für [Preisfaceting](settings.md#price-faceting) wurde von 10.000 auf 40.000.000 erhöht.

_13. Februar 2024_

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt das Festlegen einer Standardregel für [Merchandising durchsuchen](rules.md).

_12. Oktober 2023_

![Neu](../assets/new.svg) Commerce-Administratoren können jetzt die Indexsprache für [!DNL Live Search] angeben. Siehe [Einstellungen](settings.md).
![Korrektur](../assets/fix.svg) Die Registerkarte &quot;Suchregeln&quot;wurde in &quot;Merchandising suchen&quot;umbenannt.

_13. Juni 2023_

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem einige Zeichen wie Anführungszeichen oder Apostrophe Probleme mit der Rangfolge verursachten. Durch die Neuindizierung werden diese Probleme gelöst.

_25. April 2023_

![Neu](../assets/new.svg) [!DNL Live Search] -Kunden können jetzt den neuen [SaaS-Preisindex](../price-index/price-indexing.md) nutzen.

### PLP-Widget

_31. Mai 2024_

![Neu](../assets/new.svg) Version 2.0.0 des PLP-Widgets veröffentlicht, die Unterstützung für die folgenden Funktionen hinzufügt:

- Zum Warenkorb hinzufügen - Nur für einfache Produkte verfügbar.
- Mehrere Bilder pro Produkt - Das Bild kann sich ändern, wenn für ein konfigurierbares Produkt eine andere Farbe ausgewählt wird.

_27. Oktober 2023_

![Neu](../assets/new.svg) Das [!DNL Live Search] PLP-Widget unterstützt jetzt Farbmuster.

## [!DNL Live Search] 4.2.1 {#421}

_31. Juli 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem bestimmte Skripte nicht auf der Checkout-Seite geladen wurden.
![Korrektur](../assets/fix.svg) Korrektur einer Abhängigkeitsversion in der Datei `composer.json`.

## [!DNL Live Search] 4.2.0 {#420}

_31. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Aktualisierung der Live Search-Erweiterung zur Verwendung von PLP-Widgets der Version 2.0.0.

## [!DNL Live Search] 4.1.2 {#412}

_16. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Updates

![Korrektur](../assets/fix.svg) Korrektur der [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) GraphQL-Abfrage, um die Filterung für Kategorien anhand der `categoryPath` und der `categoryList` korrekt durchzuführen.

## [!DNL Live Search] 4.1.1 {#411}

_19. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Sprachunterstützung für Polnisch hinzugefügt.
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.3 für Installationen mit Adobe Commerce 2.4.4.

## [!DNL Live Search] 4.1.0 {#410}

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Der [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) ist jetzt verfügbar. Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service].

### Updates

![Korrektur](../assets/fix.svg) Korrektur eines Fehlers, der zu einem Fehler führte, wenn Gastbenutzer Produkte in nicht standardmäßigen Store-Ansichten zum Warenkorb hinzugefügt haben.
![Korrektur](../assets/fix.svg) Korrektur eines Fehlers, der dazu führte, dass das Suchmenü immer das Währungssymbol vor dem Preiswert anzeigte, unabhängig von den Gebietsschemaeinstellungen.
![Korrektur](../assets/fix.svg) Es wurden unnötige Typdefinitionen für deaktivierte Core-Plug-ins entfernt, um Kompatibilitätsprobleme bei der Installation zu beheben.

## [!DNL Live Search] 4.0.0 {#400}

_13. November 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Farbmuster im PLP-Widget.
![Neu](../assets/new.svg) [!DNL Live Search] zeigt jetzt den Kategorienamen anstelle der Kategorie-ID an.
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt Durchschnittspreise im PLP-Widget.
![Neu](../assets/new.svg) Die Schaltfläche &quot;Filter ausblenden&quot;wurde eingeführt, um den Filterbereich auszublenden.


### Updates

![Korrektur](../assets/fix.svg) Das PLP-Widget [!DNL Live Search] ist jetzt standardmäßig für neue Installationen aktiviert.
![Korrektur](../assets/fix.svg) CSS-Stile wurden neu konfiguriert, um Widget-Klassen besser zu isolieren.
![Fehlerbehebung](../assets/fix.svg) Kleinere Fehlerbehebungen

Aktivieren Sie nach der Installation von Version 3.1.1 oder höher die neuen Indexer:

- Produktpreis-Feed
- Umfang des Website-Daten-Feeds
- Umfang des Daten-Feeds von Kundengruppen

Testen Sie nach dem Upgrade die aktualisierte Konfiguration in QA oder Staging, bevor Sie die Änderungen in die Produktion übernehmen.

## Frühere Versionen

+ + + 3.1.1 und früher

## [!DNL Live Search] 3.1.1 {#311}

_15. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Registerkarte &quot;Neues Kategorie-Merchandising&quot;wurde hinzugefügt. Benutzer können jetzt intelligente Ranglisten und manuelle Ranglisten (Pin, Verstärken, Begraben, Verbergen) pro Kategorie hinzufügen
![Neu](../assets/new.svg) Benutzer können eine einzelne Kategorieregel mit intelligentem oder manuellem Rang hinzufügen
![Neu](../assets/new.svg) Benutzer können jetzt intelligente Ranking-Regeln zu Unterkategorien hinzufügen
![Neu](../assets/new.svg) Beim Löschen von Unterkategorien mit intelligentem Rang werden detaillierte Informationen bereitgestellt
![Neu](../assets/new.svg) Die Möglichkeit zum Löschen von Regeln für geerbte Ranking-Strategien wurde hinzugefügt.
![Neu](../assets/new.svg) Die Möglichkeit zum Löschen von Regeln für eine einzelne Kategorie wurde hinzugefügt.
![Neu](../assets/new.svg) Benutzer können beim Hinzufügen einer Regel jetzt nach Kategorienamen suchen
![Neu](../assets/new.svg) Mit der Ansicht &quot;Kategoriestruktur&quot;können Benutzer jetzt sehen, für welche Kategorie Regeln angewendet werden.
![Neu](../assets/new.svg) Die Kategorievorschau zeigt nur die ausgewählte Kategorie an.
![Neu](../assets/new.svg) AEM [Popover-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/319)- und [PLP-Widget](https://github.com/adobe/aem-cif-guides-venia/pull/320)-Komponenten ermöglichen es AEM Sites, [!DNL Live Search] zu nutzen.

### Updates

![Korrektur](../assets/fix.svg) Die Tabellengröße der Produkt- und Preis-Feeds wurde stark reduziert. Für die Tabellen `catalog_data_exporter_products` und `catalog_data_exporter_product_prices` sollte eine erhebliche Reduzierung der Größe vorgenommen werden.
![Korrektur](../assets/fix.svg) Die Registerkarte &quot;Regeln&quot;wird in &quot;Suchregeln&quot;umbenannt.
![Korrektur](../assets/fix.svg) Bei der Rangfolge nach &quot;Trends&quot;können Sie jetzt zwischen folgenden Optionen wählen:
- 3 Tage (Standard)
- 14 Tage
- 30 Tage
![Korrektur](../assets/fix.svg) &#39;Ereignisse&#39; (Verstärken/Verbergen/Ausblenden) wurde in &#39;Manuelles Ranking&#39; umbenannt.
![Korrektur](../assets/fix.svg) &#39;Ranking Type&#39; wurde in &#39;Intelligent ranking&#39; umbenannt.
![Fehlerbehebung](../assets/fix.svg) Kleinere Fehlerbehebungen

## [!DNL Live Search] 3.1.0 {#310}

_1. September 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Updates

![Korrektur](../assets/fix.svg) Das Widget &quot;Produktauflistung&quot;wurde aktualisiert und verwendet nun die [Catalog Service-API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7. August 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Dem Objekt `storeDetails` wurden die folgenden Werte hinzugefügt:

- &quot;Alle Produkte pro Seite zulassen&quot;
- Währungskurs
- &quot;Products per Page on Grid Allowed Values&quot;
- &quot;Products per Page on Grid Default Value&quot;
- Store language

### Updates

![Korrektur](../assets/fix.svg) Dem Metapaket wurden Catalog Service-Module hinzugefügt, um den erweiterten Datenabruf zu unterstützen.
![Korrektur](../assets/fix.svg) Die Seitennavigation **Mein Konto** verschwindet nicht mehr bei Verwendung des Widgets &quot;Seite mit Produktauflistung&quot;.

Händler müssen die [!DNL Live Search] -Erweiterungsversion >= 3.0.2 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### Einschränkungen

Die Verwendung des Widgets &quot;Live Search Product Listing Page&quot;führt dazu, dass der Google Tag Manager fehlschlägt. Verwenden Sie den standardmäßigen Suchadapter, wenn der Google Tag Manager erforderlich ist.

## [!DNL Live Search] 3.0.1 {#301}

_14. März 2023_

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

### Neue Funktionen

![Neu](../assets/new.svg) Produktelementkarte in der Regelvorschau
![Neu](../assets/new.svg) [Seitenwidget &quot;Produktliste&quot;](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![Neu](../assets/new.svg) [Filteroptionen für Kategorien](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Neu](../assets/new.svg) Es wurde die Möglichkeit hinzugefügt, Pin-Ereignisse per Drag-and-Drop zu erstellen
![Neu](../assets/new.svg) Neue Pin-Aktionen:
- An Ort und Stelle befestigen - Schaltfläche &quot;Pin&quot;zum Erstellen eines Pin-Ereignisses mit einem Klick
- Nach oben pinnen - Setzt das Produkt an die erste Position
- An den unteren Rand anheften - Platziert das Produkt am Ende der Ergebnisse
- Aufheben der Bindung eines Ereignisses mit einem Klick
![Neu](../assets/new.svg) [Intelligente Rangliste für Regeln](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt alle Funktionen von [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) in Commerce (ehemals Multi-Source Inventory oder MSI). Um die vollständige Unterstützung zu aktivieren, müssen Sie [das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+ aktualisieren.](install.md#update)

### Updates

![Korrektur](../assets/fix.svg) Regeln konfigurieren sortiert jetzt automatisch Positionen eindeutig
![Korrektur](../assets/fix.svg) Beim Löschen eines vorhandenen Ereignisses wird jetzt die Vorschau aktualisiert.
![Korrektur](../assets/fix.svg) Regeln ohne Ereignisse können gespeichert werden
![Korrektur](../assets/fix.svg) Facettenauswahl &quot;Typ auswählen&quot;entfernen
![Korrektur](../assets/fix.svg) Neuer Status &quot;Bearbeiten&quot;für nicht gespeicherte Regeln hinzugefügt

### Fehlerbehebungen

![Beheben](../assets/fix.svg) Korrektur eines Serverfehlers, wenn beim Speichern ein nicht abgeschlossenes Ereignis auftritt
![Korrektur](../assets/fix.svg) Korrektur des korrekten Löschens eines bestimmten Ereignisses bei mehreren Ereignissen
![Korrektur](../assets/fix.svg) Korrektur des vorhandenen Regelereignisses, das nicht aktualisiert wurde, wenn ein neues Ereignis hinzugefügt wurde
![Korrektur](../assets/fix.svg) Korrektur beim zweiten &quot;Bearbeiten&quot;-Klick aus Details, [!DNL Live Search] Seite, die neu geladen werden muss
![Fehlerbehebung](../assets/fix.svg) Synonyme: Es wurde ein Problem behoben, bei dem ein Benutzer, der aus der Eingabe heraus klickte, den Fokus nicht auf das Feld zurückgeben konnte.
![Fehlerbehebung](../assets/fix.svg) Weitere kleinere Fehlerbehebungen und Leistungsaktualisierungen


![Fehler](../assets/bug.svg) - Die Rangfolge nach &quot;Empfohlen für Sie&quot;wird nur in den Live-Suche-Widgets unterstützt. Sie wird von der standardmäßigen Luma- und PWA-Suchfunktion nicht unterstützt.
![Fehler](../assets/bug.svg) - Benutzerdefinierte Preisattribut-Facetten werden in Luma nicht korrekt dargestellt, aber die API filtert sie ordnungsgemäß.

Händler müssen die [!DNL Live Search] -Erweiterungsversion >= 3.0.1 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) - Die Live-Suche würde einen Fehler auslösen, wenn SDK-Ressourcen aufgrund von Netzwerkproblemen nicht verfügbar waren. Dieser Fehler wurde behoben.

Händler müssen die Live Search-Erweiterung Version >= 2.0.5 aktualisieren, um auf diese Funktionen zugreifen zu können.

Es wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor Sie die Produktionsumgebung aktivieren. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Live-Suche unterstützt jetzt das Filtern nach der Einstellung &quot;Nicht vorrätige Produkte anzeigen&quot;im Admin. Wenn &quot;Nicht vorrätige Produkte anzeigen&quot;auf &quot;false&quot;gesetzt ist, wird dem Filter `inStock = true` hinzugefügt.
![Korrektur](../assets/fix.svg) Zur Leistungsverbesserung wurde der Block &quot;Vorschläge&quot;aus dem Popup für die Live-Suche entfernt. Die Daten werden weiterhin über GraphQL übergeben, falls Sie die Funktion ersetzen möchten.
![Korrektur](../assets/fix.svg) `categories` und `categoryPath` haben `categoryIds` für die Kategoriefilterung ersetzt. Weitere Informationen finden Sie im Thema [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) .
![Korrektur](../assets/fix.svg) Zuvor erhielt ein Benutzer, der an ein B2B-Unternehmen gebunden war, bei der Suche einen falschen Kundengruppen-Code. Die Live-Suche gibt jetzt den richtigen Wert zurück.
![Korrektur](../assets/fix.svg) Zuvor gab die Live-Suche bei der Suche nach einem nicht vorhandenen Begriff einen Fehler zurück. Dieser Fehler wurde nun behoben.

Händler müssen die [!DNL Live Search] -Erweiterungsversion >= 2.0.4 aktualisieren, um auf diese Funktionen zugreifen zu können.

Benutzern wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Live-Suche unterstützt jetzt B2B-Funktionen durch Berücksichtigung von Kategorieberechtigungen, freigegebenen Katalogen und kundengruppenspezifischen Preisen.

Händler müssen die [!DNL Live Search] -Erweiterungsversion >= 2.0.3 aktualisieren, um auf diese Funktionen zugreifen zu können.

Benutzern wird empfohlen, ein Upgrade durchzuführen und zu testen, bevor sie zur Produktion wechseln. Erwägen Sie, die Produktionsumgebung außerhalb der Spitzenzeiten zu aktualisieren, nachdem Sie die Ergebnisse der Testumgebung überprüft haben.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

Bestehende [!DNL Live Search] -Installationen müssen auf [!DNL Live Search] 2.0.0 aktualisiert werden, um die folgenden neuen Funktionen, Fehlerbehebungen und Verbesserungen nutzen zu können:

![Neu](../assets/new.svg) [!DNL Live Search] unterstützt jetzt PHP 8.1 für Installationen mit Adobe Commerce 2.4.4.
![Neu](../assets/new.svg) Das Modul `Magento_ElasticsearchCatalogPermissionsGraphQl` wird der Liste der Module hinzugefügt, die während der Installation deaktiviert werden.
![Neu](../assets/new.svg) Die Anzahl der verfügbaren Zeilen im [[!DNL storefront popover]](overview.md) kann über den *Administrator* konfiguriert werden.
![Neu](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) wird für [!DNL Live Search] unterstützt.
![Neu](../assets/new.svg) Der [!DNL Live Search] -Installationsprozess wird mit erweiterten Prozessänderungen aktualisiert.
Der Link ![Korrektur](../assets/fix.svg) [Erweiterte Suche](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) wurde aus der Fußzeile der Storefront entfernt.
![Fehler](../assets/bug.svg) Die folgenden Produktattribute werden von der [Commerce GraphQL API](https://developer.adobe.com/commerce/services/graphql/live-search/) nicht unterstützt, wenn sie im Zusammenhang mit der Betaversion von PWA verwendet werden: `description`, `name`, `short_description`
![Fehler](../assets/bug.svg) Die Beta-Version von PWA für [!DNL Live Search] unterstützt nicht die [Ereignisverarbeitung](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) [Benutzerdefiniertes Preisattribut](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) gibt keinen Fehler mehr zurück, wenn es als [facet](facets-add.md) konfiguriert wurde.
![Korrektur](../assets/fix.svg) Korrektur eines Fehlers, der dazu führte, dass ein Fehler auftrat, wenn kein [Währungssymbol](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration#step-5-customize-currency-symbols-optional) (`data-currency-symbol`) verfügbar war.
![Korrektur](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) zeigt jetzt den [Sonderpreis](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) (den letzten Mindestpreis) an, sofern verfügbar.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) [Leistung](performance.md) -Berichterstellungs-Dashboard bietet Einblicke in Suchbegriffe, die von Käufern verwendet werden.
![Neu](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) bietet Zugriff auf eine gemeinsame Datenschicht mit Ereignisveröffentlichungs- und Abonnementdiensten sowie Metriken.
![Korrektur](../assets/fix.svg) Die [[!DNL Storefront popover]](storefront-popover.md) hat eine neue `active`-Klasse für den `.search-autocomplete`-Container, der die Sichtbarkeit steuert.
![Korrektur](../assets/fix.svg) In der Storefront wird der Fußzeilenlink [Suchbegriffe ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) entfernt und sein Cache für [!DNL Live Search] -Installationen deaktiviert.
![Fehler](../assets/bug.svg) Patch für Suchadapter behandelt doppelte Produkte.
![Bug](../assets/bug.svg) [!DNL Live Search] unterstützt [einzelne Quellen](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) (physische) Inventarstandorte mit mehreren (virtuellen) [Lagern](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). Mehrere Inventarquellen werden jetzt nicht mehr unterstützt.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Neu](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) zeigt vorgeschlagene Produkte und Miniaturansichten der wichtigsten Suchergebnisse an, wenn Käufer Abfragen in das Suchfeld eingeben.
![Neu](../assets/new.svg) Commerce *Admin*-Sitzung bleibt während längerer Zeiträume der Tastaturinaktivität geöffnet
![Neu](../assets/new.svg) [!DNL Live Search] wird nach dem Onboarding automatisch aktiviert
![Korrektur](../assets/fix.svg) Die anfängliche Indizierungszeit beträgt weniger als eine Stunde
![Korrektur](../assets/fix.svg) Inkrementelle Produktaktualisierungen nahezu in Echtzeit (nach Installation und Einrichtung)
![Korrektur](../assets/fix.svg) Sortierbare Spalten im Synonym-Editor
![Korrektur](../assets/fix.svg) [!DNL Live Search] löst keinen Fehler mehr aus, wenn Suchkriterien einen leeren Sortierreihenfolgenwert enthalten
![Korrektur](../assets/fix.svg) Die Bereichsfilterung schlägt nicht mehr fehl, wenn Attributcodes die Zeichenfolgen &quot;to&quot;oder &quot;from&quot;enthalten

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Unterstützt]{type="Informativ" tooltip="Unterstützt"}

![Fehler](../assets/bug.svg) Der [!DNL Live Search]-Dienst unterstützt nur die [Basiswährung](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) der Adobe Commerce-Installation.
![Fehler](../assets/bug.svg) Beim Hinzufügen einer Facette wird der Produktattribut-Feed nicht korrekt aktualisiert, wenn er auf `Update on Save` gesetzt ist. Um dieses Problem zu vermeiden, navigieren Sie zu [Indexverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) und setzen Sie den Produktattribut-Feed auf `Update by Schedule`.
![Fehler](../assets/bug.svg) [!DNL Live Search] Synonyme werden pro Store-Ansicht definiert, werden jedoch derzeit pro Website gespeichert und mit einer Kombination aus `environmentId` und `storeViewCode` identifiziert. Daher verwenden alle Websites und Speicheransichten innerhalb der Adobe Commerce-Installation Synonyme. Der zuletzt erstellte Satz von Synonymen für die Store-Ansicht hat Vorrang.
![Fehler](../assets/bug.svg) Wenn ein Synonym mehrere Wörter enthält, wird jedes Wort als separates Synonym behandelt. Wenn Sie beispielsweise &quot;Zeitelement&quot;als Synonym für &quot;Uhr&quot;definieren, werden sowohl &quot;Zeit&quot;als auch &quot;Stück&quot;als Uhrensynonyme behandelt.

+++

## Dokumentation

Weitere Informationen:

- [Adobe Commerce-Entwicklerdokumentation](https://developer.adobe.com/commerce/docs)
- [Adobe Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search] auf Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
