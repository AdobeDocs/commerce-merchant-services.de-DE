---
title: Erstellen benutzerdefinierter Ereignisse
description: Erfahren Sie, wie Sie benutzerspezifische Ereignisse erstellen, um Ihre Adobe Commerce-Daten mit anderen Adobe DX-Produkten zu verbinden.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Erstellen benutzerdefinierter Ereignisse

Sie können die [Eventing-Plattform](events.md) erweitern, indem Sie eigene Storefront-Ereignisse erstellen, um branchenspezifische Daten zu erfassen. Wenn Sie ein benutzerspezifisches Ereignis erstellen und konfigurieren, wird es an den [Adobe Commerce-Ereigniskollektor](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector) gesendet.

## Umgang mit benutzerdefinierten Ereignissen

Benutzerdefinierte Ereignisse werden nur für Adobe Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Adobe Commerce-Dashboards und -Metriken-Tracker weitergeleitet.

Für jedes `custom` -Ereignis führt der Kollektor Folgendes aus:

- Fügt `identityMap` mit `ECID` als primäre Identität hinzu
- Umfasst `email` in `identityMap` als sekundäre Identität _wenn_ `personalEmail.address` im Ereignis festgelegt ist
- Schließt das vollständige Ereignis in ein `xdm` -Objekt ein, bevor es an die Edge weitergeleitet wird

Beispiel:

Benutzerspezifisches Ereignis, das über das Adobe Commerce Events SDK veröffentlicht wird:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> Die Verwendung benutzerdefinierter Ereignisse kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.

## Ereignisüberschreibungen verarbeiten (benutzerdefinierte Attribute)

Attributüberschreibungen für Standardereignisse werden nur für die Experience Platform unterstützt. Benutzerdefinierte Daten werden nicht an Commerce-Dashboards und -Metriken-Tracker weitergeleitet.

Bei jedem Ereignis mit `customContext` überschreibt der Kollektor die in den relevanten Kontexten festgelegten Felder mit den Feldern in `customContext`. Der Anwendungsfall für Außerkraftsetzungen besteht darin, dass ein Entwickler Kontexte wiederverwenden und erweitern möchte, die von anderen Teilen der Seite in bereits unterstützten Ereignissen festgelegt wurden.

>[!NOTE]
>
>Beim Überschreiben benutzerspezifischer Ereignisse sollte die Ereignisweiterleitung an Experience Platform für diesen Ereignistyp deaktiviert werden, um eine doppelte Zählung zu vermeiden.

Beispiele:

Produktansicht mit Überschreibungen, die über das Adobe Commerce Events SDK veröffentlicht werden:

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Das Überschreiben von Ereignissen mit benutzerdefinierten Attributen kann sich auf standardmäßige Adobe Analytics-Berichte auswirken.
