---
title: Lebensdauer der Benutzersitzung
description: Der Administrator bietet die Möglichkeit, die Cookie-Lebensdauer Ihres Adobe Commerce-Benutzers für die [!DNL Quick Checkout] -Erweiterung.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Lebensdauer der Benutzersitzung

Die Lebensdauer einer Kundensitzung wird durch verschiedene Faktoren bestimmt, die in Ihrem Adobe Commerce-Administrator konfiguriert werden können. Siehe [Cookie-Lebensdauer konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} für weitere Informationen.

Die konfigurierte Lebensdauer von Cookies kann sich auf Ihre [!DNL Quick Checkout] if:

1. Aufgrund der Inaktivität wird der Käufer von Adobe Commerce abgemeldet.
1. Die [!DNL Bolt] -Sitzung abläuft.

Wenn ein Käufer eine Bestellung aufgibt, [!DNL Bolt] -Sitzung abläuft, wird die Bestellung erfolgreich aufgegeben, der Benutzer wird jedoch von beiden Netzwerken abgemeldet.

Wenn der Benutzer nach einem erfolgreichen Checkout noch aktiv ist, wird er nicht sowohl von Adobe Commerce als auch von [!DNL Bolt].
