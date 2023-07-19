---
title: '''[!DNL Product Recommendations] Versionshinweise'
description: Die neuesten Versionsinformationen für [!DNL Product Recommendations] aus Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '1120'
ht-degree: 0%

---

# [!DNL Product Recommendations] Versionshinweise

Die Versionshinweise enthalten Aktualisierungen für Folgendes [!DNL Product Recommendations] -Module:

* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Unterstützung von Page Builder in [!DNL Product Recommendations] (optional) Modul: `magento/module-page-builder-product-recommendations`
* Unterstützung des Typs visueller Ähnlichkeitsempfehlungen für [!DNL Product Recommendations] (optional) Modul: `magento/module-visual-product-recommendations`

Unterstützung wird für die aktuelle, als Hauptversion veröffentlichte Version bereitgestellt. Versionshinweise für ältere Versionen werden als Referenz bereitgestellt.
Die Versionshinweise umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Fehlerbehebung](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Fehler](../assets/bug.svg) Bekannte Probleme

Siehe die Entwicklerdokumentation zu [Informationen zur Produktkompatibilität](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Aktuelle Hauptversion

_18. Juli 2023_

![Neu](../assets/new.svg) Produkt Recommendations verfügt jetzt über eine GraphQL [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) Abfrage.

_25. April 2023_

![Neu](../assets/new.svg) Recommendations-Kunden können jetzt die Vorteile von [SaaS-Preisindizierung](../price-index/index.md).

### 5.0.0 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Produkt-Recommendations wurde aktualisiert, um Adobe Commerce 2.4.6 zu unterstützen.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) der Stamm `composer.json` -Datei für Ihr Projekt.

#### Bekannte Einschränkungen

* Die `websiteCode` -Wert falsch zurückgegeben, wenn er einen Unterstrich (_) enthält.

### Frühere Versionen

+ + + 4.0.1 und früher

### 4.0.1 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Zuvor wurde in der Produkt-Recommendations ein Fehler angezeigt, wenn die Anzeigewährung auf eine nicht standardmäßige Währung umgestellt wurde. Das Wechseln von Währungen funktioniert jetzt ordnungsgemäß.

### 4.0.0 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Hinzugefügt [Bereitschaftsindikatoren](create.md) um Ihnen zu helfen, den Trainings-Fortschritt der einzelnen Empfehlungstypen zu visualisieren.
![Neu](../assets/new.svg) Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) der Stamm `composer.json` -Datei für Ihr Projekt. Für diese Version müssen Sie außerdem bei der Installation und Konfiguration von Product Recommendations zwei API-Schlüssel angeben: [einen Produktionsschlüssel und einen Sandbox-Schlüssel](../landing/saas.md).

#### Bekannte Einschränkungen

* Die `websiteCode` -Wert falsch zurückgegeben, wenn er einen Unterstrich (_) enthält.

### 3.3.7 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Unterstützung für PHP 8.1 hinzugefügt
![Neu](../assets/new.svg) Verbesserte Bildgröße, sodass die Bildgröße in der Referenzanzeigevorlage konsistenter gehandhabt wird

### 3.3.6 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Optimiert [!DNL Product Recommendations] metapackage durch explizite Auflistung der Abhängigkeiten

### 3.3.5 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Hinzugefügt [B2B-Unterstützung](onboarding.md#b2bsupport) in Product Recommendations
![Neu](../assets/new.svg) Neue Feeds zu [Katalogdaten synchronisieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) zu Commerce-Services über die Befehlszeile

### 3.3.3 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Neu hinzugefügt [Empfehlungstypen](type.md): Konversion (Ansicht zum Warenkorb), Konversion (Ansicht zum Kauf) und Kürzlich angezeigt. Diese neuen Empfehlungstypen sind im Abschnitt `magento/product-recommendations` Modul 3.2.2 und höher.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem die Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Produkte, die der nicht standardmäßigen Store-Ansicht zugewiesen waren, nicht im _Recommendations-Produktvorschau_ Bedienfeld beim Erstellen einer Empfehlung für diese bestimmte Store-Ansicht
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem bestimmte Empfehlungseinheiten im Seitenaufbau verhindert haben, dass die Empfehlungseinheit auf der Storefront angezeigt wurde.

### 3.3.2 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Fehlende Abhängigkeit für B2B-Unterstützung behoben

### 3.3.1 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Unterstützung für B2B-Kundengruppenpreise hinzugefügt. Wenn Sie [Preisfilter](filters.md) für eine Empfehlungseinheit sehen B2B-Kunden, die angemeldet sind, den Preissatz der Kundengruppe für die angezeigten Produkte.

### 3.3.0 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Adobe Client Data Layer wird nun unterstützt, um die verhaltensbasierte Datenerfassung über Adobe Commerce-Funktionen und -Dienste hinweg zu standardisieren. Siehe [Readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) , um mehr zu erfahren.

### 3.2.6 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Ein modaler JavaScript-Fehler wurde behoben
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem die Fastly&#39;s Web Application Firewall (WAF) fälschlicherweise ein Cookie blockierte.

### 3.2.5 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Umbenannte Magento Services in [Commerce-Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) und verbesserte Benutzerfreundlichkeit in der Admin-Konsole

### 3.2.4 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Der Fehler &quot;Konfigurierbare Produktoptionen können nicht abgerufen werden&quot;bei der Indizierung von Produktattributen wurde behoben.

### 3.2.3 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Der Fehler &quot;Konfigurierbare Produktoptionen-Daten können nicht abgerufen werden&quot;bei der Katalogsynchronisierung wurde behoben
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem der Store-Code nicht richtig festgelegt wurde, wenn Sie die Konfiguration &quot;Store-Code zur URL hinzufügen&quot;aktiviert haben
![Fehlerbehebung](../assets/fix.svg) Die Erkennung von Konfigurationsänderungen im Admin Panel wurde verbessert, um sicherzustellen, dass diese Änderungen in den Daten der Katalogsynchronisierung berücksichtigt werden.

### 3.2.2 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Die Möglichkeit wurde hinzugefügt, [Vorschau der Empfehlungsergebnisse](create.md) zum Zeitpunkt der Erstellung. Dies erfordert möglicherweise, dass Sie Ihr Modul auf die neueste Version aktualisieren.
![Neu](../assets/new.svg) Die Möglichkeit wurde hinzugefügt, [überwachen und verwalten](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) den Vorgang zur Katalogsynchronisierung vom Administrator.
![Neu](../assets/new.svg) Hinzugefügt [Filter](filters.md) um zu steuern, welche Produkte in Empfehlungen angezeigt werden.
![Neu](../assets/new.svg) Der [Visuelle Ähnlichkeit](type.md#visualsim) Empfehlungstyp.

### 1.2.1 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Unterstützung für die Version 3.2.0+ der `magento/product-recommendations` Modul

### 3.1.0 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Die Möglichkeit wurde hinzugefügt, [resync](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) Ihr Katalog zu SaaS-Diensten über die Befehlszeile.
![Neu](../assets/new.svg) Unterstützung für Datenbanktabellenpräfixe hinzugefügt
![Fehlerbehebung](../assets/fix.svg) PHP 7.1-Unterstützung wurde entfernt

### 3.0.8 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem Ereignisse zur Datenerfassung gesendet wurden, bevor das Modul konfiguriert wurde, wodurch ungültiger Traffic verursacht wurde.

### 3.0.6 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) **(Beta)** Unterstützt neue [Visuelle Ähnlichkeit](type.md#visualsim) Empfehlungstyp.

### 1.0.0 von Magento/module-visual-product-recommendations

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) **(Beta)** [Visuelle Ähnlichkeit](type.md#visualsim). Mit dem _Visuelle Ähnlichkeit_ Empfehlungstyp können Sie eine Empfehlungseinheit für Ihre Produktdetailseite bereitstellen, die Produkte anzeigt, die dem angezeigten Produkt visuell ähnlich sind.

### 3.0.5 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Der Fehler &quot;Produktoptionen können nicht abgerufen werden&quot;wurde behoben, der beim Katalogexport auftreten konnte.
![Fehlerbehebung](../assets/fix.svg) Das Währungssymbol im _Umsatz_ in der Spalte _Produkt-Recommendations_ Das Dashboard spiegelt nun die konfigurierte Basiswährung korrekt wider.

### 3.0.4 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Unterstützung für Adobe Commerce 2.4.0 hinzugefügt

### 3.0.3 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Fehlerbehebung](../assets/fix.svg) Verbesserte Symbolimplementierung in der Storefront-Vorlage

### 1.0.4 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Produktempfehlungsname bei der Bearbeitung des Inhaltstyps von Page Builder hinzugefügt

### 3.0.2 Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Es wurde eine Statusspalte zum Raster hinzugefügt, wenn Empfehlungseinheiten im Seitenaufbau ausgewählt wurden.
![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem mit falschen HTTP/HTTPS-Protokollen in Produkt- und Bild-URLs behoben

### 3.0.1 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

Dies ist eine Hauptversion. [Bearbeiten](install-configure.md#update) die Datei &quot;root composer.json&quot;Ihres Projekts.

![Neu](../assets/new.svg) Abrufen [!DNL Product Recommendations] aus alternativen SaaS-Datenräumen. Auf diese Weise können Sie Produktempfehlungen verwenden, die in Ihrer Produktumgebung in anderen, nicht produktionsbezogenen Umgebungen berechnet wurden. [Wechseln von SaaS-Datenräumen](settings.md) beschreibt diese Funktion weiter.

![Fehlerbehebung](../assets/fix.svg) Es wurde ein Problem behoben, bei dem das Auschecken für Käufer mit Block Origin verhindert wurde.
![Fehlerbehebung](../assets/fix.svg) Fehlerkorrektur - Es wurde ein Problem behoben, durch das irrelevante Ereignisse zum Warenkorb gesendet wurden

### 1.0.3 von magento/module-page-builder-product-recommendations für Page Builder

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Unterstützung von Page Builder. Mit der Integration von Page Builder können Sie Empfehlungseinheiten an einem beliebigen Ort in von Page Builder erstellten Inhalten genau und präzise platzieren. Sie können die Überschriften und Empfehlungseinheiten auch selbst gestalten. Navigieren Sie zu [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) für weitere Informationen.

### 2.0.0 von Magento/Produktempfehlungen

[!BADGE Kompatibilität]{type=Informative tooltip="Kompatibilität"}

![Neu](../assets/new.svg) Allgemeines Release zur Verfügbarkeit!

+++

## Dokumentation

Weitere Informationen finden Sie unter [!DNL Product Recommendations] und [!DNL Product Recommendations] Entwicklung:

* [Benutzerhandbuch](overview.md)
* [Entwicklerdokumentation](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
