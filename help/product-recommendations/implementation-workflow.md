---
title: Implementierungsarbeitsablauf
description: Erfahren Sie mehr über die Schritte zur erfolgreichen Implementierung [!DNL Product Recommendations] auf Ihrer Schaufensterfront.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Implementierungsarbeitsablauf

[!DNL Product Recommendations] verwendet sowohl Verhaltens- als auch Katalogdaten:

- Verhalten - Daten zur Interaktion eines Käufers auf Ihrer Site, z. B. Produktansichten, zu einem Warenkorb hinzugefügte Artikel und Käufe. Adobe Commerce und Adobe Sensei erheben keine personenbezogenen Daten.

- Katalog - Produktmetadaten wie Name, Preis und Verfügbarkeit.

Wenn Sie die `magento/product-recommendations module`, aggregiert Adobe Sensei die Verhaltens- und Katalogdaten und erstellt [!DNL Product Recommendations] für jeden Empfehlungstyp. Die [!DNL Product Recommendations] -Dienst stellt diese Empfehlungen dann in Ihrer Storefront bereit. Verwenden Sie den folgenden Workflow, um Produktempfehlungen in Ihre Storefront zu implementieren:

>[!NOTE]
>
> Wenn Ihre Storefront mit PWA Studio implementiert ist, lesen Sie den Abschnitt [PWA-Dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Wenn Sie eine benutzerdefinierte Frontend-Technologie wie React oder Vue JS verwenden, erfahren Sie, wie Sie [integrieren](headless.md) [!DNL Product Recommendations] in Ihre Headless-Storefront.

## Workflow

1. **Bereitstellen der Datenerfassung für die Produktion**

   Bereitstellen [!DNL Product Recommendations] erfordert zwei Hauptschritte [Datenquellen](type.md): Katalog und Verhaltensweisen. Da die Produktion die einzige Umgebung ist, in der die Aktionen Ihrer Kunden erfasst und analysiert werden, ist es in Ihrem Interesse, so früh wie möglich mit der Datenerfassung in der Produktion zu beginnen. [Lernen](behavioral-data.md) wie Adobe Sensei maschinelle Lernmodelle trainiert, die zu Empfehlungen mit höherer Qualität führen. Wenn Sie mit der Erfassung von Verhaltensdaten über die Produktion beginnen, können Sie [Empfehlungen abrufen](verify.md) auf diesen Produktionsdaten basieren, während sie in Nicht-Produktionsumgebungen ausgeführt werden. Anschließend können Sie verschiedene Empfehlungen testen und mit ihnen experimentieren, die anhand von in der Produktion erfassten echten Käuferdaten berechnet werden.

   Um die Datenerfassung für die Produktion bereitzustellen, müssen Sie [Installieren und Konfigurieren](install-configure.md) die [!DNL Product Recommendations] -Modul durch Bereitstellung einer [API-Schlüssel](https://docs.magento.com/user-guide/system/saas.html#apikey).

   >[!TIP]
   >
   > Die Bereitstellung der Datenerfassung ändert weder das Erscheinungsbild Ihrer Storefront noch das Kundenerlebnis. Das Kundenerlebnis in Ihrer Storefront wird nur durch die Erstellung und Bereitstellung von Empfehlungseinheiten verändert. Testen Sie vor der Bereitstellung in der Produktionsumgebung unbedingt die Nicht-Produktionsumgebung. Erstellen Sie außerdem keine Empfehlungseinheiten, bis Sie Ihre Vorlage anpassen. Siehe nächsten Schritt.

1. **Passen Sie die Vorlage an Ihren Stil an**

   Ihre Storefront repräsentiert Ihre Marke. Stellen Sie daher sicher, dass Sie die Vorlage für Produktempfehlungen entsprechend Ihrem Site-Design ändern.

   >[!TIP]
   >
   > Durch Anpassung der Vorlage können Sie Ihr Stylesheet festlegen, überschreiben, wo eine Empfehlungseinheit auf einer Seite angezeigt wird, usw.

   Siehe [Anpassen](https://devdocs.magento.com/recommendations/customize.html) in der Entwicklerdokumentation , um zu erfahren, wie Sie diesen Schritt abschließen.

1. **Testen von Empfehlungen in Ihrer Nicht-Produktionsumgebung**

   Es empfiehlt sich immer, eine neue Technologie in Ihrer Nicht-Produktionsumgebung zu testen, bevor Sie sie für die Produktion bereitstellen. Durch das Testen von Empfehlungen in Ihrer Nicht-Produktionsumgebung können Sie mit verschiedenen Arten von Empfehlungseinheiten, Positionierungen und Seiten spielen. Sie können Empfehlungen basierend auf Verhaltensdaten abrufen, die bereits während des Testens in Ihrer Nicht-Produktionsumgebung in der Produktion erfasst wurden, sodass die Empfehlungsergebnisse auf dem Kaufverhalten der tatsächlichen Kunden basieren.

   >[!TIP]
   >
   > Stellen Sie sicher, dass Ihr Nicht-Produktions-Umgebungs-Katalog weitgehend mit dem in der Produktion vorhandenen Katalog übereinstimmt. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die in den Empfehlungseinheiten zurückgegebenen Produkte die Produkte in der Produktion sehr gut nachahmen.

   Siehe [Abrufen](staging-environment.md) Verhaltensdaten aus Ihrer Produktionsumgebung, um zu erfahren, wie Sie diesen Schritt durchführen.

1. **Erstellen und Bereitstellen von Empfehlungen für Ihr Produktions-Storefront**

   Nachdem Sie nun die verhaltensbasierte Datenerfassung in der Produktion bereitgestellt, die Vorlage für Produktempfehlungen geändert und Empfehlungen anhand des tatsächlichen Kaufverhaltens getestet haben, sind Sie bereit, sämtlichen Code für die Produktion weiterzuleiten und [erstellen](create.md) Live-Produktempfehlungen.
