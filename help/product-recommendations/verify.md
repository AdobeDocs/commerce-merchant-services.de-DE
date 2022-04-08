---
title: Ereigniskollektion überprüfen
description: Erfahren Sie, wie Sie überprüfen können, ob Verhaltensdaten an Adobe Commerce gesendet werden.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Ereigniskollektion überprüfen

Nach [Installieren und Konfigurieren](install-configure.md) die `magento/product-recommendations` -Modul können Sie überprüfen, ob die Verhaltensdaten an Adobe Commerce gesendet werden. Sie können die in Chrome verfügbaren Entwicklertools verwenden oder die Chrome-Erweiterung Snowplow installieren. Weitere Informationen finden Sie unter [Fehlerbehebung [!DNL Product Recommendations] Modul](https://support.magento.com/hc/en-us/articles/360042224851) in der Support-Wissensdatenbank.

## Überprüfen mit Entwicklertools in Chrome

So stellen Sie sicher, dass die JS-Datei für den Ereignissammler auf allen Seiten der Website geladen wird:

1. Wählen Sie in Chrome **Anpassen und Steuern von Google Chrome** und wählen Sie **Weitere Tools** > **Entwicklertools**.
1. Wählen Sie die **Netzwerk** und wählen Sie dann die **JS** Typ.
1. Filtern nach `ds.`
1. Laden Sie die Seite neu.
1. Sie sollten `ds.js` oder `ds.min.js` im **Name** Spalte.

So stellen Sie sicher, dass Ereignisse auf Seiten Ihrer Site (Startseite, Produkt, Checkout usw.) ausgelöst werden:

1. Stellen Sie sicher, dass Sie alle Anzeigensperren in Ihrem Browser deaktivieren und Cookies auf der Site akzeptieren.
1. Wählen Sie in Chrome **Anpassen und Steuern von Google Chrome** (die drei vertikalen Punkte in der oberen rechten Ecke des Browsers) und wählen Sie **Weitere Tools** > **Entwicklertools**.
1. Wählen Sie die **Netzwerk** Registerkarte und Filter für `tp2`.
1. Laden Sie die Seite neu.
1. Aufrufe werden unter angezeigt `tp2` im **Name** Spalte.

## Überprüfen mit der Chrome-Erweiterung Snowplow

Installieren Sie die [Erweiterung &quot;Snowplow Analytics Debugger&quot;für Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Diese Erweiterung zeigt die Ereignisse an, die erfasst und an Adobe Commerce gesendet werden.

1. Stellen Sie sicher, dass Sie alle Anzeigensperren in Ihrem Browser deaktivieren und Cookies auf der Site akzeptieren.

1. Wählen Sie in Chrome **Anpassen und Steuern von Google Chrome** (die drei vertikalen Punkte in der oberen rechten Ecke des Browsers) und wählen Sie **Weitere Tools** > **Entwicklertools**.

1. Wählen Sie die **Snowplow Analytics-Debugger** Registerkarte.

1. Unter dem **Ereignis** Spalte auswählen **Strukturiertes Ereignis**.

1. Scrollen Sie nach unten, bis Sie **Kontextdaten _n_**. Suchen Sie nach der Storefront-Instanz in **Schema**.

1. Stellen Sie sicher, dass [SaaS-Datenraum-ID](https://docs.magento.com/user-guide/configuration/services/saas.html) korrekt eingestellt ist.

Wenn bei der Überprüfung, ob die Ereignisse erfasst und an Adobe Commerce gesendet werden, Probleme auftreten, [Support kontaktieren](https://support.magento.com/hc/en-us).

>[!NOTE]
>
> Ein Wert von `Data validity : NOT FOUND` im Debugger zeigt ein internes Schema an. Das Snowplow-Chrome-Plug-in kann die Ereignisse nicht mit einem internen Schema überprüfen. Dies hat keine Auswirkungen auf die tatsächliche Funktionalität.

## Sicherstellen, dass Ereignisse ordnungsgemäß ausgelöst werden

Um sicherzustellen, dass die für Metriken verwendeten Ereignisse ordnungsgemäß ausgelöst werden, suchen Sie nach der `impression-render`, `view`und `rec-click` -Ereignisse im Snowplow Analytics-Debugger. Siehe [vollständige Liste der Ereignisse](https://devdocs.magento.com/recommendations/events.html).

>[!NOTE]
>
> Wenn [Cookie-Einschränkungsmodus](https://docs.magento.com/user-guide/stores/compliance-cookie-restriction-mode.html) aktiviert ist, erfasst Adobe Commerce keine Verhaltensdaten, bis der Käufer zustimmt. Wenn der Cookie-Beschränkungsmodus deaktiviert ist, werden standardmäßig Verhaltensdaten erfasst.
