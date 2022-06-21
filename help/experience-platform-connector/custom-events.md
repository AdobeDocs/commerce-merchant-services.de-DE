---
title: Erstellen benutzerdefinierter Ereignisse
description: Erfahren Sie, wie Sie benutzerdefinierte Ereignisse erstellen, um Ihre Adobe Commerce-Daten mit anderen Adobe DX-Produkten zu verbinden.
source-git-commit: 1dd8f94e632bb98666ad252badf8420a014260fb
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Erstellen benutzerdefinierter Ereignisse

Sie können die [Eventplattform](events.md) durch Erstellung eigener Storefront-Ereignisse, um branchenspezifische Daten zu erfassen. Wenn Sie ein benutzerspezifisches Ereignis erstellen und konfigurieren, wird es an die [Magento Storefront Event Collector](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Umgang mit benutzerdefinierten Ereignissen

Benutzerdefinierte Ereignisse werden nur für Adobe Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Adobe Commerce-Dashboards und -Metriken-Tracker weitergeleitet.

Für alle `custom` -Ereignis, fügt der Kollektor eine `personId` (`ecid`) zu `customContext` und ein `xdm` -Objekt um es herum vor der Weiterleitung an die Edge.

Beispiel:

Benutzerspezifisches Ereignis, das über das MSE-SDK veröffentlicht wird:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> Die Verwendung benutzerdefinierter Ereignisse kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.

## Verarbeiten von Ereignisüberschreibungen (benutzerdefinierte Attribute)

Attributüberschreibungen für Standardereignisse werden nur für die Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Commerce-Dashboards und -Metriken-Tracker weitergeleitet.

Für alle Ereignisse mit einem Satz `customContext`, überschreibt der Kollektor `personId` und Adobe Analytics-Zähler und leitet alle anderen Attribute weiter, die in `customContext`.

Beispiele:

Produktansicht mit über das MSE SDK veröffentlichten Überschreibungen:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

Die Produktansicht mit Adobe Commerce überschreibt über das MSE-SDK veröffentlichte Informationen:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

In Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Das Überschreiben von Ereignissen mit benutzerdefinierten Attributen kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.
