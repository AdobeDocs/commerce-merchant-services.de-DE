---
title: Einstellungen
description: Erfahren Sie, wie Sie die Quelle Ihrer  [!DNL Product Recommendations]  ändern und visuelle Empfehlungen aktivieren.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Einstellungen

Wenn Sie [SaaS-Datenbereich konfigurieren](../landing/saas.md#saas-configuration) für Recommendations erfasst der SaaS-Datenbereich Katalogdaten und Verhaltensdaten für die Storefront. [Adobe Sensei](https://www.adobe.com/sensei.html) analysiert diese Daten und berechnet Produktverknüpfungen, die zur Bereitstellung von Produkt-Recommendations verwendet werden.

Nicht-Produktionsumgebungen für Tests oder Staging verfügen normalerweise nicht über die Menge oder Qualität der Verhaltensdaten der Storefront, um realistische Produktempfehlungen zu liefern. Das tatsächliche Einkaufsverhalten in großem Umfang kann nur in einer Produktionsumgebung erfasst werden. Um dieses Problem zu lösen, können Sie mit Adobe Commerce Produktempfehlungen aus Ihrer Produktionsumgebung mit anderen, produktionsfremden SaaS-Datenbereichen verwenden. Durch die Verwendung tatsächlicher Storefront-Daten in einer Nicht-Produktionsumgebung können Sie eine Vorschau der Empfehlungen anzeigen, die Ihre Kunden sehen, und mit verschiedenen Empfehlungstypen und Platzierungsorten experimentieren. Recommendations aus einem anderen SaaS-Datenbereich kann von Käufern in der Vorschau angezeigt, aber nicht angeklickt werden.

Staging-Aufträge werden mithilfe der Staging-`environmentId` aufgezeichnet. Die Produktionsdaten sind davon nicht betroffen. Die Produktionsdaten werden über die `alternateEnvironmentId` abgerufen.

>[!NOTE]
>
>Bei Verwendung von Produkt-Recommendations über REST kann der `alternateEnvironmentId`-Parameter verwendet werden, um andere Datenräume anzugeben. Bei Verwendung von Produkt-Recommendations über GraphQL ist dieser Parameter nicht verfügbar.

## Quelle der Empfehlungen auswählen

Um die Quelle der Produktempfehlungsdaten zu ändern, wählen Sie den SaaS-Datenbereich mit den Verhaltensdaten aus, die Sie verwenden möchten. Bevor Sie beginnen, stellen Sie Folgendes sicher:

- Die Datenerfassung in der Storefront muss [konfiguriert und aktiviert](install-configure.md) für Ihre Produktionsumgebung konfiguriert und [überprüft](verify.md), dass Verhaltensdaten an Adobe Commerce gesendet werden.
- Ihr Katalog für die Nicht-Produktionsumgebung sollte im Wesentlichen mit Ihrem Produktionskatalog identisch sein. Durch die Verwendung ähnlicher Kataloge wird sichergestellt, dass die zurückgegebenen Produktempfehlungseinheiten die in der Produktion verwendeten Kataloge genau nachahmen.

1. Melden Sie sich beim Administrator Ihrer produktionsfremden Adobe Commerce-Umgebung an.

1. Navigieren Sie in der _Admin_-Seitenleiste zu **Marketing** > _Promotions_ > **Product Recommendations**.

1. Klicken Sie **Einstellungen**.

   ![Produktempfehlungseinstellungen](assets/settings.png)
   _Einstellungen_

1. Aktivieren Sie im Abschnitt _Recommendations_ die Option **Abrufen von Empfehlungen aus einem anderen SaaS-**. Der Abschnitt _Recommendations-Quelle_ wird nur in einer Nicht-Produktionsumgebung angezeigt.

   Eine Liste _Verfügbare SaaS-Datenräume_ wird angezeigt.

   ![Produktempfehlungseinstellungen](assets/settings-select-saas.png)
   _Einstellungen_

1. Wählen Sie den SaaS-Datenbereich aus, der über Kundendaten verfügt, die Sie verwenden möchten.

1. Klicken Sie **Änderungen speichern**.

   Adobe Commerce ruft jetzt Empfehlungen aus dem ausgewählten Datenbereich ab.

   >[!NOTE]
   >
   > Sie können zwar Empfehlungen anzeigen, die aus einem anderen SaaS-Datenbereich in der Nicht-Produktions-Storefront abgerufen wurden, Sie können jedoch nicht auf die Empfehlungen klicken.

### Konfigurieren eines neuen SaaS-Datenspeichers

1. Klicken Sie im Abschnitt Recommendations-Quelle auf **Konfiguration bearbeiten**.

1. Befolgen Sie die Anweisungen zum Konfigurieren eines neuen [[!DNL Commerce] Service](/help/landing/saas.md).

## Visuelle Empfehlungen aktivieren

Wenn das [Visual Product Recommendations](install-configure.md)-Modul installiert ist, müssen Sie Visual Recommendations aktivieren, um den Empfehlungstyp [Visuelle Ähnlichkeit](type.md#visualsim) zu verwenden.

Legen Sie im _Visual Recommendations_-Abschnitt **Visual Recommendations aktivieren** auf die aktive Position fest.
