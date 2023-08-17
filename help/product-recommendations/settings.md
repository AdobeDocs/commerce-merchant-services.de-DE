---
title: Einstellungen
description: Erfahren Sie, wie Sie die Quelle Ihrer [!DNL Product Recommendations] Daten und wie visuelle Empfehlungen aktiviert werden.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 48e350167611a2737d79bf5decccd7f6f24c714c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Einstellungen

Wenn Sie [Konfigurieren eines SaaS-Datenraums](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) für Recommendations erfasst der SaaS-Datenraum Katalogdaten und Storefront-Verhaltensdaten. [Adobe Sensei](https://www.adobe.com/sensei.html) analysiert diese Daten und berechnet Produktzuordnungen, die zur Bereitstellung von Product Recommendations verwendet werden.

Nicht-Produktionsumgebungen für Tests oder Staging verfügen in der Regel nicht über die Menge oder Qualität der Storefront-Verhaltensdaten, um realistische Produktempfehlungen zu erhalten. Das tatsächliche Kaufverhalten in großem Maßstab kann nur in einer Produktionsumgebung erfasst werden. Um dieses Problem zu beheben, können Sie mit Adobe Commerce Produktempfehlungen aus Ihrer Produktionsumgebung mit anderen SaaS-Datenräumen ohne Produktionsumgebung verwenden. Durch die Verwendung der tatsächlichen Storefront-Daten in einer Nicht-Produktionsumgebung können Sie die Empfehlungen, die Ihre Kunden sehen, in der Vorschau anzeigen und mit verschiedenen Empfehlungstypen und Platzierungsorten experimentieren. Recommendations aus einem anderen SaaS-Datenraum kann von Käufern in der Vorschau angezeigt, aber nicht angeklickt werden.

>[!NOTE]
>
>Bei der Verwendung von Product Recommendations über REST wird die `alternateEnvironmentId` kann verwendet werden, um andere Datenbereiche anzugeben. Bei Verwendung von Product Recommendations über GraphQL ist dieser Parameter nicht verfügbar.

## Empfehlungsquelle auswählen

Um die Quelle Ihrer Produktempfehlungsdaten zu ändern, wählen Sie den SaaS-Datenraum mit den gewünschten Verhaltensdaten aus. Bevor Sie beginnen, stellen Sie Folgendes sicher:

- Die Storefront-Datenerfassung muss [konfiguriert und aktiviert](install-configure.md) für Ihre Produktionsumgebung und [verifiziert](verify.md) dass Verhaltensdaten an Adobe Commerce gesendet werden.
- Ihr Nicht-Produktions-Umgebungs-Katalog sollte im Wesentlichen mit Ihrem Produktionskatalog übereinstimmen. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die zurückgegebenen Produktempfehlungseinheiten die in der Produktion ähneln.

1. Melden Sie sich beim Administrator Ihrer Nicht-Produktions-Adobe Commerce-Umgebung an.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **Marketing** > _Promotions_ > **Produkt-Recommendations**.

1. Klicks **Einstellungen**.

   ![Produktempfehlungseinstellungen](assets/settings.png)
   _Einstellungen_

1. Im _Recommendations-Quelle_ aktivieren Sie die **Abrufen von Empfehlungen aus einem anderen SaaS-Datenraum** -Option. Die _Recommendations-Quelle_ wird nur in einer Nicht-Produktionsumgebung angezeigt.

   Eine Liste von _Verfügbare SaaS-Datenräume_ angezeigt.

   ![Produktempfehlungseinstellungen](assets/settings-select-saas.png)
   _Einstellungen_

1. Wählen Sie den SaaS-Datenraum aus, der über die zu verwendenden Kundendaten verfügt.

1. Klicks **Änderungen speichern**.

   Adobe Commerce ruft jetzt Empfehlungen aus dem ausgewählten Datenraum ab.

   >[!NOTE]
   >
   > Sie können zwar Empfehlungen anzeigen, die aus einem anderen SaaS-Datenraum außerhalb des Produktions-Storefront abgerufen wurden, aber Sie können nicht auf die Empfehlungen klicken.

### Neuen SaaS-Datenraum konfigurieren

1. Klicken Sie im Recommendations-Quellabschnitt auf **Konfiguration bearbeiten**.

1. Befolgen Sie die Anweisungen zum Konfigurieren eines neuen [[!DNL Commerce] service](/help/landing/saas.md).

## Visuelle Empfehlungen aktivieren

Wenn die Variable [Visual Product Recommendations](install-configure.md) installiert ist, müssen Sie Visual Recommendations aktivieren, um die [Visuelle Ähnlichkeit](type.md#visualsim) Empfehlungstyp.

Im _Visual Recommendations_ Abschnitt, festlegen **Aktivieren von Visual Recommendations** an die aktive Position.
