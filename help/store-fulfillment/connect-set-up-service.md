---
title: Schließen Sie die Store Fulfillment-Lösung an.
description: Stellen Sie die Verbindungen zwischen Adobe Commerce und der Store Fulfillment-Lösung her. Erstellen und autorisieren Sie eine Adobe Commerce-Integration und fügen Sie die Anmeldedaten für das Store-Fulfillment-Konto zur Adobe Commerce-Dienstkonfiguration hinzu.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Schließen Sie die Store Fulfillment-Lösung an.

Verbinden Sie Store Fulfillment Services mit Adobe Commerce, indem Sie die erforderlichen Authentifizierungsberechtigungen und Verbindungsdaten zum Adobe Commerce-Administrator hinzufügen.

- **[Konfigurieren [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)**-Erstellen Sie eine Adobe Commerce-Integration für Store Fulfillment-Dienste und generieren Sie die Zugriffstoken, um eingehende Anfragen von den Store Fulfillment-Servern zu authentifizieren.

- **[Kontoanmeldeinformationen für Store Fulfillment Services konfigurieren](#configure-store-fulfillment-account-credentials)**-Fügen Sie Ihre Anmeldedaten hinzu, um Adobe Commerce mit Ihrem Store-Fulfillment-Konto zu verbinden.

>[!NOTE]
>
>Schließen Sie die Verbindungskonfiguration ab und validieren Sie die Verbindung erfolgreich, bevor Sie mit dem Testen beginnen.

## Erstellen einer Adobe Commerce-Integration

Um Adobe Commerce mit Store Fulfillment-Diensten zu integrieren, erstellen Sie eine Commerce-Integration und generieren Sie Zugriffstoken, die zum Authentifizieren von Anforderungen von Store Fulfillment-Servern verwendet werden können. Sie müssen auch die Adobe Commerce aktualisieren [!UICONTROL Consumer Settings] Optionen zum Vermeiden `The consumer isn't authorized to access %resources.` Antwortfehler bei Anfragen von Adobe Commerce an [!DNL Store Fulfillment] Dienste.

1. Erstellen Sie aus dem Admin die Integration für die Store-Erfüllung.

   - Benennen der Erweiterung
   - E-Mail-Adresse eingeben
   - Geben Sie Ihr Admin-Kontokennwort ein

1. Konfigurieren Sie die Zugriffsberechtigungen für die API-Ressource für die Integration mit folgenden Eigenschaften:

   - Vertrieb > BOPIS-Bestellaktualisierung
   - System > Store Fulfillment App-Berechtigungen

1. Generieren Sie die Zugriffstoken für die Authentifizierung, indem Sie die Integration speichern und aktivieren.

1. Kopieren Sie die Zugriffstoken und speichern Sie sie an einem sicheren, verschlüsselten Speicherort.

1. Wenden Sie sich an Ihren Kundenbetreuer, um die Konfiguration auf der Seite Store-Erfüllung abzuschließen und die Integration zu autorisieren.

1. Adobe Commerce aktivieren [!UICONTROL Consumer Settings] -Option [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - Navigieren Sie vom Administrator zu **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Legen Sie die [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] -Option **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> Das Integrations-Token ist umgebungsspezifisch. Wenn Sie die Datenbank für eine Umgebung mit Quelldaten aus einer anderen Umgebung wiederherstellen, z. B. die Wiederherstellung von Produktionsdaten aus einer Staging-Umgebung, schließen Sie die `oauth_token` aus dem Datenbankexport, sodass die Details des Integrationstokens beim Wiederherstellungsvorgang nicht überschrieben werden.


## Konfigurieren der Anmeldedaten für das Store-Fulfillment-Konto

Nachdem Sie das Annahmeformular ausgefüllt haben, wird ein Walmart Store Fulfillment-Konto für Sie erstellt. Sie erhalten die folgenden Anmeldeinformationen, wenn sie verfügbar sind:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (normalerweise identisch mit der oben genannten Konfiguration)

Diese Anmeldeinformationen sind erforderlich, um die Store-Ausführung zu konfigurieren und zu verwenden.

>[!NOTE]
>
>Der Prozess der Kontoerstellung kann einige Zeit in Anspruch nehmen. Während Sie auf Anmeldeinformationen warten, [Überprüfen und konfigurieren Sie andere Einstellungen für die Lösung &quot;Store Fulfillment&quot;](service-config-settings-overview.md).

### Hinzufügen von Anmeldeinformationen zum Herstellen einer Verbindung zur Store-Erfüllung

1. Konfigurieren [Kontoanmeldeinformationen](enable-general.md) für die Produktions- und Sandbox-Umgebungen.

1. Navigieren Sie vom Administrator zu **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Geben Sie die Kontoanmeldeinformationen ein, die für die **[!UICONTROL Production environment]**. Alle Felder sind erforderlich.

1. Auswählen **[!UICONTROL Save Config]**.

1. Testen Sie die Verbindung, indem Sie **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Wenn die Anmeldeinformationen ungültig sind, vergewissern Sie sich, dass Sie die richtigen Werte für jede Umgebung eingegeben haben, und überprüfen Sie erneut. Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie weiterhin Probleme bei der Verbindung haben.
