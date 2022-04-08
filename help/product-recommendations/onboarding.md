---
title: Onboarding
description: Erfahren Sie mehr über die Anforderungen und unterstützten Plattformen in [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '222'
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

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4
- Verfasser

### Unterstützte Plattformen

- Adobe Commerce on prem (EE) : 2.4.x
- Adobe Commerce on Cloud (ECE) : 2.4.x

### Unterstützung von Page Builder

[!DNL Product Recommendations] kann einer Seite als Inhaltstyp des Seitenaufbaus hinzugefügt werden. Informationen zum Hinzufügen von Page Builder-Unterstützung zu Product Recommendations finden Sie unter [Installieren und Konfigurieren](install-configure.md).

### B2B-Unterstützung {#b2bsupport}

B2B-Storefronts erfordern häufig eine komplexe Logik, die die Produktsichtbarkeit und die Preise für jeden Käufer oder jede Kundengruppe vorschreibt. [!DNL Product Recommendations] now [Support](release-notes.md) diese Funktionalität durch [Kategorienberechtigungen](https://docs.magento.com/user-guide/catalog/category-permissions.html), [freigegebene Kataloge](https://docs.magento.com/user-guide/catalog/catalog-shared.html)und [kundengruppenspezifische Preise](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). Wenn Sie beispielsweise bestimmte Kategorien aus Ihrem Einzelhandelskundensegment ausgeblendet haben, wird einem Käufer in diesem Segment keine Empfehlung für Produkte in diesen Kategorien angezeigt. Wenn Sie einen freigegebenen Katalog für bestimmte Kundengruppen und Unternehmen definieren, sehen diese Käufer nur Empfehlungen für Produkte, auf die sie zugreifen können. Alle empfohlenen Produkte spiegeln den korrekten gruppenspezifischen Preis der einzelnen Kunden basierend auf ihrer Kundengruppe wider.