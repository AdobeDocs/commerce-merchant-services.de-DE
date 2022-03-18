---
title: Instanz verbinden
description: Verbinden Sie Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben Sie den Datenraum in der Konfiguration an.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Instanz verbinden

[!DNL Payment Services] wird von Commerce Services unterstützt und als SaaS (Software as a Service) bereitgestellt. Sie verbinden Ihre Commerce-Instanz mit einem API-Schlüssel und einem privaten Schlüssel und geben den Datenraum in der Konfiguration an. Sie richten diese Verbindung nur einmal ein.

Siehe [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} im Benutzerhandbuch zu diesem Dienst.

## API-Anmeldeinformationen abrufen

Um einen Commerce SaaS-Dienst zu nutzen, müssen Sie die API-Schlüssel Ihrer Instanz verwenden, die in Ihren [Mein Konto-Dashboard](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. Für ein Commerce-Konto können zwei verschiedene API-Schlüsselpaare erstellt werden - eines für Sandbox und eines für Produktion (Live-Zahlungen). Es kann jedoch immer nur ein Paar aktiv verwendet werden.

>[!NOTE]
>
>Benötigen Sie Hilfe beim Zugriff auf Ihre [!UICONTROL My Account] Dashboard? Siehe [Erstellen eines Commerce-Kontos](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;} im Benutzerhandbuch zur Kernbenutzeroberfläche.

Ein bestimmtes API-Schlüsselpaar ist für alle Commerce-Services in einer Umgebung gültig. Wenn Sie also Commerce Services bereits für Ihre Commerce-Instanz konfiguriert haben, ist Ihr API-Schlüsselpaar bereits im Admin vorhanden. Wenn Ihr privater API-Schlüssel verloren geht, muss ein neues API-Schlüsselpaar generiert und auf die Commerce Services-Konfiguration in Admin angewendet werden.

Informationen zum Generieren eines API-Schlüssels für Sandbox- oder Produktionsumgebungen finden Sie unter [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} im Benutzerhandbuch zur Kernbenutzeroberfläche.

>[!IMPORTANT]
>
>Wenn Sie ein API-Schlüsselpaar neu generieren und die SaaS-Kennung ändern, stellen alle von dieser Instanz verwendeten Commerce-Dienste eine Verbindung zu einem anderen Datenspeicher her und Ihr Zugriff (einschließlich zuvor gespeicherter Daten) geht verloren. Es wird empfohlen, kein API-Schlüsselpaar neu zu generieren und die SaaS-Kennung in einer aktiven Produktionsinstanz zu ändern.

### Commerce-API-Schlüssel und privater Schlüssel

Einige Adobe Commerce- und Magento Open Source-Funktionen werden als SaaS (Software as a Service), auch Commerce Services genannt, bereitgestellt. Um diese Dienste zu verwenden, müssen Sie Ihre Commerce-Instanz mithilfe eines API-Schlüssels und eines privaten Schlüssels mit diesen Diensten verbinden und den gewünschten Datenraum im [Konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

Wenn Sie ein Commerce-Konto erstellen, das durch eine MageID identifiziert wird, können Sie einen Commerce-API-Schlüssel und einen privaten Schlüssel generieren. So verwenden Sie Commerce-Dienste wie [!DNL Payment Services], [!DNL Product Recommendations]oder [!DNL Live Search]muss der Lizenzinhaber diese Schlüssel generieren, um die Berechtigungsprüfung zu bestehen. Diese Schlüssel können dann an den Systemintegrator oder das Entwicklungsteam übergeben werden, der die Projekte und Umgebungen im Auftrag des Lizenzinhabers verwaltet. Wenn Sie Lösungsintegrator sind, sind Sie auch berechtigt, diese Dienste für Ihre eigenen Anforderungen zu nutzen. In diesem Fall sollte der Unterzeichner des Commerce-Partnervertrags die Schlüssel generieren.

### API-Schlüssel und privaten Schlüssel generieren

1. Melden Sie sich bei Ihrem Commerce-Konto an unter [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. Unter dem **[!UICONTROL Magento]** Registerkarte, wählen Sie **[!UICONTROL API Portal]** auf der Seitenleiste.
1. Aus dem _[!UICONTROL Environment]_Menü auswählen **[!UICONTROL Sandbox]**, dann **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >API-Schlüssel sind für beide Umgebungen erforderlich.

1. Geben Sie im Feld _[!UICONTROL API Keys]_und klicken Sie auf **[!UICONTROL Add New]**.

   Diese Aktion öffnet ein Dialogfeld zum Herunterladen des neuen Schlüssels.

   >[!IMPORTANT]
   >
   >Dieser Dialog ist die einzige Möglichkeit, dass Sie Ihren Schlüssel kopieren oder herunterladen können.

1. Klicken **[!UICONTROL Download]** Klicken Sie dann auf **[!UICONTROL Cancel]**.

   Die _[!UICONTROL API Keys]_-Abschnitt zeigt nun Ihren API-Schlüssel an.

1. Kopieren Sie sowohl den API-Schlüssel als auch den privaten Schlüssel, wenn Sie ein SaaS-Projekt auswählen oder erstellen.

   Siehe [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} im Benutzerhandbuch zu den wichtigsten Informationen.

Derselbe API-Schlüssel kann für alle Instanzen verwendet werden, aber jede Instanz muss über einen eigenen SaaS-Datenraum verfügen.

Wenn Sie ein SaaS-Projekt erstellen, generiert Commerce je nach Ihrer Commerce-Lizenz einen oder mehrere SaaS-Datenräume:

* Adobe Commerce - Ein Produktionsdatenraum; zwei Testdatenbereiche
* Magento Open Source - Ein Produktionsdatenraum; keine Testdatenräume

### Konfigurieren des SaaS-Projekts

>[!NOTE]
>
>Wenn die Variable _[!UICONTROL Commerce Services Connector]_in der Commerce-Konfiguration müssen Sie die Commerce-Module für Ihren gewünschten Commerce-Dienst installieren, z. B. [[!DNL Payment Services]](install.md).

Um ein SaaS-Projekt auszuwählen oder zu erstellen, fordern Sie den Commerce-API-Schlüssel vom Commerce-Lizenzinhaber für Ihren Store an.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Services]** und wählen Sie **[!UICONTROL Commerce Services Connector]**.
1. Im _[!UICONTROL API Keys]_-Abschnitt, fügen Sie Ihre Schlüsselwerte ein.

   >[!IMPORTANT]
   >
   >Fügen Sie Schlüsselwerte für beide hinzu **[!UICONTROL sandbox]** und **[!UICONTROL production]** Umgebungen.

1. Klicken **[!UICONTROL Save Config]**.

   Wenn beim Speichern SaaS-Projekte mit Ihrem API-Schlüssel verknüpft sind, werden diese Projekte im _[!UICONTROL SaaS Project]_im Feld_[!UICONTROL SaaS Identifier]_ Abschnitt.

1. Wenn keine SaaS-Projekte vorhanden sind, klicken Sie auf **[!UICONTROL Create Project]**. Geben Sie dann einen Namen für Ihr SaaS-Projekt im **[!UICONTROL Project Name]** -Feld.
1. Um für die aktuelle Konfiguration Ihres Commerce-Stores zu verwenden, wählen Sie die **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>Wenn Sie Ihre Schlüssel im Abschnitt &quot;Mein Konto&quot;im API-Portal neu generieren, aktualisieren Sie sofort die API-Schlüssel in der Admin-Konfiguration. Wenn Sie neue Schlüssel generieren und diese nicht im Admin aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Sie können die Namen ändern, indem Sie auf die **[!UICONTROL Rename this Project]** oder **[!UICONTROL Rename Data Space]** -Schaltflächen.

## Commerce Services konfigurieren

Der erste Schritt beim Onboarding [!DNL Payment Services] ist die Konfiguration Ihrer Commerce-Services in der Admin-Konsole.

1. Im _Admin_ Seitenleiste, navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicken **[!UICONTROL Configure Commerce Services]**.

   Diese Option ist sichtbar, wenn Sie Commerce Services noch nicht für Ihr Konto konfiguriert haben.

   Sie werden zum Konfigurationsbereich in der Admin-Konsole geleitet. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, um Ihren Commerce Services Connector zu konfigurieren.

1. Gehen Sie wie in beschrieben vor, um Ihre Commerce-Services zu konfigurieren. [Commerce-Services](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
