---
title: Lebensdauer der Benutzersitzung
description: Der Administrator bietet die Möglichkeit, die Cookie-Lebensdauer Ihres Adobe Commerce-Benutzers für die [!DNL Quick Checkout] -Erweiterung.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: 2f14cd437be6d48e24e56b3b31a1c640357b27e3
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Lebensdauer der Benutzersitzung

Die Lebensdauer einer Kundensitzung wird durch verschiedene Faktoren bestimmt, die in Ihrem Adobe Commerce-Administrator konfiguriert werden können. Siehe [Cookie-Lebensdauer konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} für weitere Informationen.

Die konfigurierte Lebensdauer von Cookies kann sich auf Ihre [!DNL Quick Checkout] if:

1. Aufgrund der Inaktivität wird der Käufer von Adobe Commerce abgemeldet.
1. Die [!DNL Bolt] -Sitzung abläuft.

Wenn ein Käufer eine Bestellung aufgibt, [!DNL Bolt] -Sitzung abläuft, wird die Bestellung erfolgreich aufgegeben, der Benutzer wird jedoch von beiden Netzwerken abgemeldet.

Wenn der Benutzer nach einem erfolgreichen Checkout noch aktiv ist, wird er nicht sowohl von Adobe Commerce als auch von [!DNL Bolt].
