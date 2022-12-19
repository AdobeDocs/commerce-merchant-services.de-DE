---
title: '[!DNL Quick Checkout] Versionshinweise'
description: Informationen zu allen [!DNL Quick Checkout] veröffentlicht.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 8b915cd0a8f25934675a2ae00ee2694b7facc1bd
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# Versionshinweise

Diese Versionshinweise beschreiben die erste Version von [!DNL Quick Checkout] und umfassen:

![Neu](../assets/new.svg) Neue Funktionen
![Problem behoben](../assets/fix.svg) Fehlerbehebungen und Verbesserungen
![Bekanntes Problem](../assets/bug.svg) Bekannte Probleme

Siehe [Bevorstehende Versionen](https://devdocs.magento.com/release/) , um mehr über die Veröffentlichungszeitpläne und die Unterstützung zu erfahren.

Siehe [Verfügbarkeit](https://devdocs.magento.com/release/availability.html) in der Entwicklerdokumentation , um mehr über die Produktkompatibilität zu erfahren.

## Aktualisierungen des Admin-Bereichs

In diesen Versionshinweisen werden Funktionsänderungen und -korrekturen beschrieben, die außerhalb der regulären Versionen der versionierten Funktionen für das Admin-Bedienfeld veröffentlicht wurden.

+++Admin-Bedienfeldaktualisierungen

_14. Dezember 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-524 --> Die [!DNL Quick Checkout] Im Admin-Bereich werden nun die richtigen Gesamtbestellungen und aktualisierten Berichtsinformationen angezeigt.

_30. November 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-502 --> Nun, die [Berichterstellung](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) enthält eine neue Vorgabe vom Typ &quot;Letztes Jahr&quot;.

![Neu](../assets/new.svg)<!-- Issue BOLT-471 --> Verbesserungen der Benutzererfahrung in [!DNL Quick Checkout] Admin-Bereich zeigt weitere Informationen in [QuickInfos](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-514 --> Verbesserungen der Benutzererfahrung in [!DNL Quick Checkout] Im Admin-Bedienfeld werden die korrekten Gesamtbestellzahlen, die Farbkonsistenz und die korrekten Legenden für alle Diagramme angezeigt.

_2. November 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-293 --> Nun, die [Berichterstellung](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) im [!DNL Quick Checkout] Das Admin-Bedienfeld zeigt Diagramme und Berichtsinformationen der Checkout-Erlebnisstatistiken Ihres Stores an.

![Neu](../assets/new.svg)<!-- Issue BOLT-422 --> Die [_Übersicht_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) im Abschnitt zum Thema Berichte werden detaillierte Informationen zur Leistung des Checkout in Ihrem Geschäft angezeigt, einschließlich der durchschnittlichen Checkout-Zeit, neuer Konten, die beim Checkout erstellt wurden, und des Checkout.

![Neu](../assets/new.svg)<!-- Issue BOLT-423 --> Die [_Trends_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) im Tab Berichte zeigt Ihre Kassengang-Erlebnis-Trends gefiltert nach Kontotyp und neuen Konten, die beim Checkout erstellt wurden.

![Neu](../assets/new.svg)<!-- Issue BOLT-439 --> Die **Berichte** Registerkarten anzeigen [Standardfiltervorgaben](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) , mit dem bestimmte Datenbereiche angezeigt werden können.

![Neu](../assets/new.svg)<!-- Issue BOLT-433 --> Sie können jetzt eine _Keine Daten verfügbar_ Warnhinweis für ein Diagramm, wenn eine Anforderung keine Daten zurückgibt.

![Neu](../assets/new.svg)<!-- Issue BOLT-473 --> Verbesserungen des Benutzererlebnisses aus [!DNL Quick Checkout] Admin-Bereich bietet die Möglichkeit, eine [Checkout-Tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) -Einstellung, die es Adobe Commerce ermöglicht, Berichtsinformationen mit Bolt zu teilen.

_5. Oktober 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-379 --> Wenn nun ein neuer Händler auf die [!DNL Quick Checkout] Admin-Bereich zum ersten Mal [Funktionstour auf Basis von Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) angezeigt.

![Neu](../assets/new.svg)<!-- Issue BOLT-377 --> Die **Berichte** im [!DNL Quick Checkout] Admin-Bereich zeigt Diagramme und Berichtsanalysen an.

![Neu](../assets/new.svg)<!-- Issue BOLT-377 --> Die **Berichte** im [!DNL Quick Checkout] Das Admin-Bedienfeld zeigt den Datumsbereich und die Filtervorgaben für Diagramme und Berichtsanalysen an.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-369 --> Nun, die [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) zeigt die App-Version in der Fußzeile an.

+++

## v1.4.0

_30. November 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-513 --> Wenn jetzt ein Adobe Commerce-Kunde während des Checkout-Prozesses beim Store angemeldet ist und über ein Bolt-Konto verfügt, wird eine Option angezeigt, sich beim Bolt-Konto des Käufers anzumelden.

![Neu](../assets/new.svg)<!-- Issue BOLT-512 --> Eine neue Konfiguration erkennt automatisch, ob angemeldete Käufer auch in Bolt angemeldet werden können.

![Neu](../assets/new.svg)<!-- Issue BOLT-480 --> Eine neue Konfiguration im [!DNL Quick Checkout] Mit dem Admin Panel können Sie den standardmäßigen Navigationsfluss in **Versand** Seite, sobald sich ein Bolt-Kunde anmeldet. Standardmäßig ist sie für die **Zahlungen** Seite.

## v1.3.0

_2. November 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-293 --> Jetzt [!DNL Quick Checkout] umfasst die Möglichkeit, eine [Checkout-Tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) -Einstellung, die es Adobe Commerce ermöglicht, Berichtsinformationen mit Bolt zu teilen.

![Neu](../assets/new.svg)<!-- Issue BOLT-461 --> Sie können jetzt eine Warnmeldung in Ihrem [!DNL Quick Checkout] Admin-Bereich, wenn [Checkout-Tracking](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) -Konfiguration deaktiviert ist.

## v1.2.0

_8. September 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-341 --> Version der allgemeinen Verfügbarkeit -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) ist jetzt mit Adobe Commerce-Versionen 2.4.5 kompatibel.

![Neu](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] für Adobe Commerce und Magento Open Source bietet eine [Ansicht des Admin-Bedienfelds](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) mit allen erforderlichen Informationen zum Einrichten und Verwenden der Erweiterung.

![Neu](../assets/new.svg)<!-- Issue BOLT-364 --> Administratorbenutzer [kann Benutzerrollen und Berechtigungen einrichten](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) , damit andere Benutzer die [!DNL Quick Checkout] Admin-Bereich.

![Neu](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] Das Admin-Bedienfeld enthält jetzt einen Seitenkopf, der bestimmte Abschnitte enthält, z. B. **Übersicht**, **Berichte** und **Einstellungen**.

![Neu](../assets/new.svg)<!-- Issue BOLT-379 --> Wenn ein neuer Händler auf die [!DNL Quick Checkout] Das Admin-Bedienfeld zeigt zum ersten Mal ein Begrüßungs-Widget an, das eine Übersicht über Funktionen bietet.

![Neu](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Ansicht des Admin-Bedienfelds](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) enthält eine **Konfiguration** -Schritt, der angezeigt wird, wenn die API- und veröffentlichungsfähigen Schlüssel nicht im [Einstellungen](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) anzeigen.

![Neu](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Ansicht des Admin-Bedienfelds](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) enthält eine **Ressourcen** -Abschnitt, der sich je nach der Onboarding-Phase ändert.

![Neu](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Ansicht des Admin-Bedienfelds](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) enthält **Hilfe und Support** Abschnitt.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-369 --> Die [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) zeigt nun die Erweiterungsversion in der Fußzeile an.

## v1.1.0

_12. August 2022_

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-375 --> Verbesserungen der Benutzererfahrung in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) enthalten jetzt nur die Parameter, die sichtbar und validiert sind, wenn die Erweiterung aktiviert ist.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-349 --> Kompatibilitätsverbesserungen für bestehende Versandadressen mit der Bolt-Brieftasche.

## v1.0.0

_9. August 2022_

![Neu](../assets/new.svg)<!-- Issue BOLT-341 --> Version der allgemeinen Verfügbarkeit -[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) ist jetzt mit den Adobe Commerce-Versionen 2.4.1 bis 2.4.4 kompatibel.

![Neu](../assets/new.svg)<!-- Issue BOLT-340 --> Die [!DNL Quick Checkout] für Adobe Commerce kann entweder für Adobe Commerce installiert werden [zur Cloud-Infrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) oder [vor Ort](install.md#on-premises) Instanzen. Diese Methoden erfordern die Verwendung einer Befehlszeilenschnittstelle.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce bietet eine optimierte Storefront, die eine [Kasse mit einem Klick](overview.md) ohne für den Verbraucher erforderliche Füllfelder.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce erkennt jeden Käufer im Netzwerk automatisch für [Käufe mit einem Klick](checkout-flow.md) direkt auf Ihrer Site.

![Neu](../assets/new.svg)<!-- Issue BOLT-1 --> Die [!DNL Quick Checkout] für Adobe Commerce ermöglicht es einem Kunden, gleichzeitig [bei Adobe Commerce und Bolt angemeldet sein](checkout-flow.md/#quick-checkout-use-cases) bessere `one-click checkout` Erlebnis.

![Neu](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] für Adobe Commerce unterstützt eine [Sandbox-Konto](testing.md#testing-in-sandbox) die es Händlern ermöglicht, die Erweiterung im Testmodus zu bewerten.

![Neu](../assets/new.svg)<!-- Issue BOLT-780 --> Ihre Kunden können über die [[!DNL Quick Checkout]](checkout-page.md) oder über eine [manuelle Auftragserstellung](create-order-admin.md).

![Neu](../assets/new.svg)<!-- Issue BOLT-666 --> Merchants können die [!DNL Quick Checkout] mit grundlegenden Zahlungsaktionen wie [`Authorize and Capture` oder `Authorize` ](onboarding.md#complete-admin-configuration)oder zwischen Sandbox- und Produktionsumgebungen wechseln.

![Neu](../assets/new.svg)<!-- Issue BOLT-288 --> Benutzerdefiniert [Lebensdauer der Benutzersitzung](user-session-lifetime.md) für [!DNL Quick Checkout] für Adobe Commerce.

![Problem behoben](../assets/fix.svg)<!-- Issue BOLT-375 --> Verbesserungen der Benutzererfahrung in [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) ermöglicht Ihnen, Ihre Konfiguration zu speichern, wenn alle erforderlichen Parameter angegeben sind.

![Bekanntes Problem](../assets/bug.svg)<!-- Issue BOLT-342 --> Häufig [Fehlerbehebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Probleme während der Installation [!DNL Quick Checkout].
