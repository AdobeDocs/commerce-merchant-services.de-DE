---
title: Lebensdauer der Benutzersitzung
description: Der Administrator bietet die Möglichkeit, die Cookie-Lebensdauer Ihres Adobe Commerce-Benutzers für die [!DNL Quick Checkout] -Erweiterung.
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Lebensdauer der Benutzersitzung

Die Lebensdauer einer Kundensitzung wird durch verschiedene Faktoren bestimmt, die in Ihrem Adobe Commerce-Administrator konfiguriert werden können. Siehe [Cookie-Lebensdauer konfigurieren](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} für weitere Informationen.

Die konfigurierte Lebensdauer von Cookies kann sich auf Ihre [!DNL Quick Checkout] if:

1. Aufgrund der Inaktivität wird der Käufer von Adobe Commerce abgemeldet.
1. Die [!DNL Bolt] -Sitzung abläuft.

Wenn ein Käufer eine Bestellung aufgibt, [!DNL Bolt] -Sitzung abläuft, wird die Bestellung erfolgreich aufgegeben, der Benutzer wird jedoch von beiden Netzwerken abgemeldet.

Wenn der Benutzer nach einem erfolgreichen Checkout noch aktiv ist, wird er nicht sowohl von Adobe Commerce als auch von [!DNL Bolt].
