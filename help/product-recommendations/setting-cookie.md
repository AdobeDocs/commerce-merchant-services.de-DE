---
title: Umgang mit Cookie-Einschränkungen
description: Erfahren Sie, wie Produktempfehlungen Cookie-Einschränkungen verarbeiten.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Umgang mit Cookie-Einschränkungen

Sowohl Adobe Commerce als auch Magento Open Source ersuchen um Zustimmung, bevor Daten in Browser-Cookies gespeichert werden. Weitere Informationen finden Sie unter [Cookie-Einschränkungsmodus](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

Wenn Sie die `magento/product-recommendations` -Modul in die Produktion integriert ist, beginnt es, Interaktionsereignisse von Käufern auf Ihrer Storefront zu erfassen. Da Daten für diese Ereignisse in Browser-Cookies oder im lokalen Speicher gespeichert werden können, unterstützt die Funktion den Cookie-Einschränkungsmodus, indem sie Ereignisse erst erfasst, nachdem der Käufer seine Cookie-Zustimmung erteilt hat.

Dies funktioniert möglicherweise nicht mit Lösungen für die Zustimmung zu Drittanbieter-Cookies. Es liegt in der Verantwortung jedes Händlers sicherzustellen, dass die Datenerfassung nicht erfolgt, bevor die Cookie-Zustimmung erteilt wurde, wie dies häufig gesetzlich vorgeschrieben ist. Wenn Sie die Cookie-Zustimmung mit benutzerdefiniertem Code verwalten, können Sie ein Nicht-Tracking-Cookie namens `mg_dnt` , um die Datenerfassung zu beschränken.

- Name des Cookies:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- Setzen Sie das Cookie do-not-track , um die Datenerfassung zu deaktivieren:

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- So löschen Sie das Cookie, wenn der Benutzer Cookies akzeptiert hat:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
