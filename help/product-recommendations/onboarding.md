---
title: Onboarding
description: Erfahren Sie mehr über die Anforderungen und unterstützten Plattformen in [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Onboarding

Onboarding-Prozess für [!DNL Product Recommendations] erfordert Zugriff auf die Befehlszeile des Servers und besteht aus den folgenden Schritten. Wenn Sie nicht mit der Arbeit über die Befehlszeile vertraut sind, bitten Sie einen Entwickler oder Systemintegrator um Hilfe.

- [Implementierungsarbeitsablauf](implementation-workflow.md)
- [Installieren und Konfigurieren](install-configure.md)
- [Einstellungen](settings.md)
- [Überprüfen](verify.md)
- [Staging-Umgebung](staging-environment.md)

## Voraussetzungen

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Verfasser 2

### Unterstützte Plattformen

- Adobe Commerce On-Premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpunkt

[!DNL Product Recommendations] kommuniziert über den Endpunkt unter `https://catalog-service.adobe.io/graphql`.

### Unterstützung von Page Builder

[!DNL Product Recommendations] kann einer Seite als Inhaltstyp des Seitenaufbaus hinzugefügt werden. Informationen zum Hinzufügen von Page Builder-Unterstützung zu Product Recommendations finden Sie unter [Installieren und Konfigurieren](install-configure.md).

Siehe [[!DNL Page Builder] Integration](page-builder.md) Anweisungen zum Hinzufügen von [!DNL Product Recommendations] in [!DNL Page Builder] Inhalt.

### SaaS-Preisindizierung

Kunden mit Produktempfehlungen können [SaaS-Preisindizierung](../price-index/price-indexing.md), was schnellere Preisänderungen und Synchronisierungszeiten ermöglicht.

### B2B-Unterstützung {#b2bsupport}

B2B-Storefronts erfordern häufig eine komplexe Logik, die die Produktsichtbarkeit und die Preise für jeden Käufer oder jede Kundengruppe vorschreibt. [!DNL Product Recommendations] now [Support](release-notes.md) diese Funktionalität durch [Kategorienberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [freigegebene Kataloge](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), und [kundengruppenspezifische Preise](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Wenn Sie beispielsweise bestimmte Kategorien aus Ihrem Einzelhandelskundensegment ausgeblendet haben, wird einem Käufer in diesem Segment keine Empfehlung für Produkte in diesen Kategorien angezeigt. Wenn Sie einen freigegebenen Katalog für bestimmte Kundengruppen und Unternehmen definieren, sehen diese Käufer nur Empfehlungen für Produkte, auf die sie zugreifen können. Alle empfohlenen Produkte spiegeln den korrekten gruppenspezifischen Preis der einzelnen Kunden basierend auf ihrer Kundengruppe wider.

>[!NOTE]
>
>Merchants können Widgets oder Storefront-Elemente mithilfe der [Catalog Service](../catalog-service/overview.md) Storefront-API, aber jede Anpassung ist für das Adobe Support-Team nicht möglich.
