---
title: '[!DNL Product Recommendations] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Product Recommendations] aus Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 0e0f67c01c49c8d8c0ac4967eda0bde8685b2980
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 0%

---

# [!DNL Product Recommendations] Versionshinweise

Die Versionshinweise enthalten Aktualisierungen der folgenden [!DNL Product Recommendations] -Module:

* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Unterstützung von Page Builder im Modul [!DNL Product Recommendations] (optional): `magento/module-page-builder-product-recommendations`
* Unterstützung des Typs visueller Ähnlichkeitsempfehlungen für das Modul [!DNL Product Recommendations] (optional): `magento/module-visual-product-recommendations`

Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Die Versionshinweise beinhalten:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

Weitere Informationen zum Produktsupport finden Sie in der Entwicklerdokumentation zu [finden Sie in der .](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)

## Aktualisierungen gehosteter Dienste

Diese Hinweise beschreiben Aktualisierungen oder bekannte Probleme, die außerhalb einer versionierten Version veröffentlicht oder entdeckt wurden, oder Verbesserungen am gehosteten Dienst.

_28. Juni 2024_

![Fehler](../assets/bug.svg) Produkte, die einer [!DNL Product Recommendations] -Einheit auf der Warenkorbseite zum Warenkorb hinzugefügt wurden, werden nicht aus der Liste der empfohlenen Produkte entfernt, wenn die Warenkorbseite erneut geladen wird.
![Fehler](../assets/bug.svg) Aus dem Warenkorb entfernte Produkte bleiben im Array `cartSkus` erhalten, bis die Warenkorbseite neu geladen wird.

_18. Juli 2023_

![Neu](../assets/new.svg) [!DNL Product Recommendations] hat jetzt eine GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) -Abfrage.

_25. April 2023_

![Neu](../assets/new.svg) [!DNL Product Recommendations] -Kunden können jetzt die [SaaS-Preisindizierung](../price-index/price-indexing.md) nutzen.

## Aktuelle Hauptversion

### 6.0.3 von Magento/Produktempfehlungen

_6. November 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der [Kategoriefilter](filters.md#category) Kategorien enthielt, die nicht zum aktuellen Storebericht gehörten.
![Korrektur](../assets/fix.svg) Korrektur eines Abhängigkeitsproblems im `magento/product-recommendations` -Metapaket.

### 6.0.2 von Magento/Produktempfehlungen

_9. Mai 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur des Fehlers, der dazu führte, dass der Käufer beim Klicken auf die Schaltfläche **[!DNL Add to Cart]** in einem einfachen Produkt innerhalb einer Product Recommendations-Einheit zur Homepage weitergeleitet wurde, anstatt auf der aktuellen Seite zu bleiben.
![Fehler](../assets/bug.svg) Es gibt einen Validierungsfehler, der durch das Element `referenceBlock` in der XML-Datei `ProductRecommendations Layout` verursacht wird.

### Frühere Versionen

### 6.0.1 von Magento/Produktempfehlungen

_19. März 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) PHP 8.3-Unterstützung wurde hinzugefügt.

### 6.0.0 von Magento/Produktempfehlungen

_22. Februar 2024_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der [!DNL Catalog Sync Dashboard] ist jetzt der [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Dieses überarbeitete Dashboard bietet Einblicke in Datenströme für [!DNL Product Recommendations], [!DNL Live Search] und [!DNL Catalog Service].
![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, das Checkout-Fehler für [!DNL Product Recommendations] verursachte.

++ 5.0.0 und früher

### 5.0.1 von Magento/Produktempfehlungen

_15. September 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Es wurden neue Module zur Unterstützung des [Saas-Preis-Indexers](../price-index/price-indexing.md) hinzugefügt.
![Neu](../assets/new.svg) Es wurden neue Datenexportmodule hinzugefügt, die den Export weiterer Produktarten unterstützen, einschließlich gebündelter Produkte und Geschenkkarten.
![Korrektur](../assets/fix.svg) Die Tabellengröße der Produkt- und Preis-Feeds wurde stark reduziert. Für die Tabellen `catalog_data_exporter_products` und `catalog_data_exporter_product_prices` sollte eine erhebliche Reduzierung der Größe vorgenommen werden.

#### Bekannte Einschränkungen

* Der Wert `websiteCode` wird falsch zurückgegeben, wenn er einen Unterstrich (_) enthält.

### 5.0.0 von Magento/Produktempfehlungen

_20. März 2023_

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) [!DNL Product Recommendations] wurde aktualisiert, um Adobe Commerce 2.4.6 zu unterstützen.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten Sie](install-configure.md#update) die Stamm-Datei `composer.json` für Ihr Projekt.
![Neu](../assets/new.svg) [!DNL Product Recommendations] unterstützt jetzt alle Funktionen von [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) in Commerce (ehemals &quot;Multi-Source Inventory&quot;oder &quot;MSI&quot;). Um die vollständige Unterstützung zu aktivieren, müssen Sie [das Abhängigkeitsmodul `commerce-data-export` auf Version 102.2.0+ aktualisieren.](install-configure.md#update)

### 4.0.1 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Zuvor zeigte [!DNL Product Recommendations] einen Fehler an, wenn die Anzeigewährung auf eine nicht standardmäßige Währung umgestellt wurde. Das Wechseln von Währungen funktioniert jetzt ordnungsgemäß.

### 4.0.0 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) [Bereitschaftsindikatoren](create.md) wurden hinzugefügt, damit Sie den Trainings-Fortschritt der einzelnen Empfehlungstypen visualisieren können.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten Sie](install-configure.md#update) die Stamm-Datei `composer.json` für Ihr Projekt. Für diese Version müssen Sie außerdem bei der Installation und Konfiguration von [!DNL Product Recommendations] zwei API-Schlüssel angeben: [einen Produktionsschlüssel und einen Sandbox-Schlüssel](../landing/saas.md).

#### Bekannte Einschränkungen

* Der Wert `websiteCode` wird falsch zurückgegeben, wenn er einen Unterstrich (_) enthält.

### 3.3.7 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung für PHP 8.1 hinzugefügt
![Neu](../assets/new.svg) Die Bildgröße wurde verbessert, sodass die Bildgröße in der Referenzanzeigevorlage konsistenter gehandhabt wird

### 3.3.6 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Optimiertes [!DNL Product Recommendations] -Metapaket durch explizites Auflisten der Abhängigkeiten

### 3.3.5 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) [B2B-Unterstützung](onboarding.md#b2bsupport) in [!DNL Product Recommendations] hinzugefügt
![Neu](../assets/new.svg) Neue Feeds zu [Synchronisieren von Katalogdaten](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) mit Commerce-Diensten über die Befehlszeile hinzugefügt

### 3.3.3 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Es wurden neue [Empfehlungstypen](type.md) hinzugefügt: Konversion (Ansicht in Warenkorb), Konversion (Ansicht in Kauf) und Zuletzt angezeigt. Diese neuen Empfehlungstypen sind im `magento/product-recommendations` Modul 3.2.2 und höher verfügbar.
![Korrektur](../assets/fix.svg) Korrektur eines Problems, bei dem die Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte
![Korrektur](../assets/fix.svg) Das Problem, dass Produkte, die der nicht standardmäßigen Store-Ansicht zugewiesen sind, beim Erstellen einer Empfehlung für diese bestimmte Store-Ansicht nicht im Bereich _Recommendations-Produktvorschau_ angezeigt wurden, wurde behoben.
![Korrektur](../assets/fix.svg) Korrektur des Problems, bei dem bestimmte Empfehlungseinheiten im Seitenaufbau verhindert haben, dass die Empfehlungseinheit auf der Storefront angezeigt wurde

### 3.3.2 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Fehlende Abhängigkeit für B2B-Unterstützung korrigiert

### 3.3.1 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung für B2B-Kundengruppenpreise hinzugefügt. Wenn Sie einen [Preisfilter](filters.md) für eine Empfehlungseinheit festlegen, sehen B2B-Kunden, die angemeldet sind, den Preissatz der Kundengruppe für die angezeigten Produkte.

### 3.3.0 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung für die Adobe Client-Datenschicht zur Standardisierung der verhaltensbezogenen Datenerfassung über Adobe Commerce-Funktionen und -Dienste hinweg hinzugefügt. Weitere Informationen finden Sie unter [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) .

### 3.2.6 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur eines modalen JavaScript-Fehlers
![Korrektur](../assets/fix.svg) Korrektur eines Problems, bei dem die Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte

### 3.2.5 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Umbenannte Magento-Services in [Commerce-Dienste](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) und verbesserte Benutzerfreundlichkeit in Admin

### 3.2.4 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur des Fehlers &quot;Konfigurierbare Produktoptionen können nicht abgerufen werden&quot;bei der Indizierung von Produktattributen

### 3.2.3 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur des Fehlers &quot;Konfigurierbare Produktoptionen können nicht abgerufen werden&quot;bei der Katalogsynchronisierung
![Korrektur](../assets/fix.svg) Korrektur eines Problems, bei dem der Store-Code nicht richtig festgelegt wurde, wenn Sie die Konfiguration &quot;Store-Code zur URL hinzufügen&quot;aktiviert haben
![Korrektur](../assets/fix.svg) Verbesserte Erkennung von Konfigurationsänderungen im Admin Panel, um sicherzustellen, dass diese Änderungen in den Katalogsynchronisierungsdaten übernommen werden

### 3.2.2 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Möglichkeit zur [Vorschau der Empfehlungsergebnisse](create.md) wurde zum Erstellungszeitpunkt hinzugefügt. Dies erfordert möglicherweise, dass Sie Ihr Modul auf die neueste Version aktualisieren.
![Neu](../assets/new.svg) Die Möglichkeit, [den Katalogsynchronisierungsprozess vom Administrator zu überwachen und zu verwalten](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync), wurde hinzugefügt.
![Neu](../assets/new.svg) [Filter](filters.md) wurde hinzugefügt, um zu steuern, welche Produkte in Empfehlungen angezeigt werden.
![Neu](../assets/new.svg) Der Empfehlungstyp [Visuelle Ähnlichkeit](type.md#visualsim) wurde hinzugefügt.

### 1.2.1 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Unterstützung für Version 3.2.0+ des `magento/product-recommendations`-Moduls hinzugefügt

### 3.1.0 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Die Möglichkeit, Ihren Katalog über die Befehlszeile erneut mit den SaaS-Diensten zu synchronisieren, wurde hinzugefügt.
[](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync)
![Neu](../assets/new.svg) Unterstützung für Datenbanktabellenpräfixe hinzugefügt
![Korrektur](../assets/fix.svg) PHP 7.1-Unterstützung wurde entfernt

### 3.0.8 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur des Fehlers, der dazu führte, dass Ereignisse zur Datenerfassung gesendet wurden, bevor das Modul konfiguriert wurde, wodurch ungültiger Traffic verursacht wurde

### 3.0.6 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) **(Beta)** Enthält Unterstützung für neuen Empfehlungstyp [Visuelle Ähnlichkeit](type.md#visualsim) .

### 1.0.0 von Magento/module-visual-product-recommendations

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) **(Beta)** [Visuelle Ähnlichkeit](type.md#visualsim). Mit dem Empfehlungstyp _Visuelle Ähnlichkeit_ können Sie eine Empfehlungseinheit für Ihre Produktdetailseite bereitstellen, die Produkte anzeigt, die dem angezeigten Produkt visuell ähnlich sind.

### 3.0.5 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Korrektur des Fehlers &quot;Produktoptionendaten können nicht abgerufen werden&quot;, der beim Katalogexport auftreten konnte.
![Korrektur](../assets/fix.svg) Das Währungssymbol in der Spalte _Umsatz_ im Dashboard _[!DNL Product Recommendations]_gibt jetzt die konfigurierte Basiswährung korrekt wieder.

### 3.0.4 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Unterstützung für Adobe Commerce 2.4.0 hinzugefügt

### 3.0.3 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Korrektur](../assets/fix.svg) Verbesserte Symbolimplementierung in der Storefront-Vorlage

### 1.0.4 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Der Name der Produktempfehlung wurde hinzugefügt, wenn der Inhaltstyp des Seitenaufbaus bearbeitet wird.

### 3.0.2 Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Eine Statusspalte im Raster bei der Auswahl von Empfehlungseinheiten im Seitenaufbau wurde hinzugefügt
![Korrektur](../assets/fix.svg) Korrektur eines Problems mit falschen HTTP/HTTPS-Protokollen in Produkt- und Bild-URLs

### 3.0.1 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

Dies ist eine Hauptversion. [Bearbeiten Sie](install-configure.md#update) die Datei &quot;root composer.json&quot;Ihres Projekts.

![Neu](../assets/new.svg) Rufen Sie [!DNL Product Recommendations] aus alternativen SaaS-Datenräumen ab. Auf diese Weise können Sie [!DNL Product Recommendations] verwenden, das in Ihrer Produktumgebung in anderen, nicht produktionsbezogenen Umgebungen berechnet wurde. [Wechseln von SaaS-Datenräumen](settings.md) beschreibt diese Funktion weiter.

![Korrektur](../assets/fix.svg) Es wurde ein Problem behoben, bei dem das Auschecken für Käufer mit Blockursprung verhindert wurde.
![Behebung](../assets/fix.svg) Es wurde ein Problem behoben, durch das irrelevante Add-to-Warenkorb-Ereignisse gesendet wurden

### 1.0.3 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Seitenaufbau unterstützt. Mit der Integration von Page Builder können Sie Empfehlungseinheiten an einem beliebigen Ort in von Page Builder erstellten Inhalten genau und präzise platzieren. Sie können die Überschriften und Empfehlungseinheiten auch selbst gestalten. Weitere Informationen finden Sie unter [Seitenaufbau](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) .

### 2.0.0 von Magento/Produktempfehlungen

[!BADGE Unterstützt]{type=Informative tooltip="Unterstützt"}

![Neu](../assets/new.svg) Allgemeine Verfügbarkeitsversion!

+++

## Dokumentation

Weitere Informationen zur Entwicklung von [!DNL Product Recommendations] und [!DNL Product Recommendations]:

* [Benutzerhandbuch](overview.md)
* [Entwicklerdokumentation](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
