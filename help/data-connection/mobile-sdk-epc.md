---
title: Integrieren des Adobe Experience Platform Mobile SDK mit Commerce
description: Erfahren Sie, wie Sie das Adobe Experience Platform Mobile SDK mit Ihrer Headless- oder benutzerdefinierten Commerce-Storefront verwenden.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 593e92ebf890bd7d9bfef1cd13be727ca6be172b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Integrieren des Adobe Experience Platform Mobile SDK mit Commerce

>[!IMPORTANT]
>
>Das Adobe Experience Platform Mobile SDK für iOS unterstützt iOS 11 oder höher.

Durch die Integration von [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) in die mobile Commerce-App können Händler Commerce [Ereignisdaten](events.md) an die Experience Platform senden.

Wenn Commerce-Ereignisdaten am Edge verfügbar sind, können sie von anderen Adobe Experience Cloud-Anwendungen aufgerufen werden. Beispielsweise können Sie die Daten zum Erstellen von Zielgruppen in Real-Time CDP verwenden und [diese Zielgruppen](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) zur Personalisierung Ihrer mobilen Commerce-App verwenden.

## Konfiguration

Um mit der Verwendung des Adobe Experience Platform Mobile SDK mit Commerce zu beginnen, installieren und konfigurieren Sie das SDK im Experience Platform. Schließen Sie dann die Konfiguration in Commerce ab.

### Experience Platform

1. Informieren Sie sich über die Funktionen mobiler Apps, indem Sie sich das Tutorial [Adobe Experience Cloud in mobilen Apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html) ansehen.

1. [Installieren und konfigurieren Sie](https://developer.adobe.com/client-sdks/documentation/getting-started/) das SDK im Experience Platform.

   >[!NOTE]
   >
   >Das Schema, das Sie auf der Experience Platform erstellen und konfigurieren, ist dasselbe Schema, das Sie im Anwendungscode Ihrer mobilen Commerce-App verwenden.

### Commerce

Nachdem Sie die SDK-Konfiguration für die Experience Platform abgeschlossen haben, fügen Sie die SDK-Konfiguration zu Commerce hinzu.

1. Um Commerce-Ereignisdaten über das SDK an die Experience Platform zu senden, müssen Sie ein XDM-Schema im Anwendungscode angeben. Dieses Schema muss mit dem Schema [configured](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) für das SDK in der Experience Platform übereinstimmen.

   Das folgende Beispiel zeigt, wie das `web.webpagedetails.pageViews` -Ereignis verfolgt und das `identityMap` mithilfe des E-Mail-Felds festgelegt wird.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Stellen Sie eine Verbindung zur Commerce Cloud-Umgebung her.

   Fügen Sie in den Build-Einstellungen Ihres Projekts die URL zum Commerce GraphQL-Endpunkt hinzu. Beispiel:

   - Debug: http://_debug_.commerceSite.cloud/graphql/
   - Release: http://_release_.commerceSite.cloud/graphql/

1. Um Daten aus den Commerce GraphQL-Endpunkten abzurufen, generieren Sie zunächst die erforderlichen Dateien und Ordner in Ihrem Projekt mithilfe des [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. Installieren Sie im Projektverzeichnis [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.

   1. [Initialisieren](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) Sie die Apollo-Codegen-CLI.

      Dadurch wird eine `apollo-codegen-configuration.json` -Datei erstellt.

   1. Generieren Sie die erforderlichen GraphQL-Dateien und -Ordner in Ihrem Projekt, indem Sie den Inhalt der Datei &quot;`apollo-codegen-configuration.json`&quot;durch Folgendes ersetzen:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Rufen Sie ](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) das Commerce GraphQL-Schema ab.

      Stellen Sie sicher, dass der Pfad zur Datei &quot;`./apollo-codegen-config.json`&quot; ist, die den Verweis auf das Commerce GraphQL-Schema enthält.

   1. [Generieren Sie](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) den Quellcode.

      Stellen Sie sicher, dass der Pfad zur Datei &quot;`./apollo-codegen-config.json`&quot; ist, die die Konfigurationsinformationen enthält, um die erforderlichen Dateien und Ordner zu generieren.

   1. Fügen Sie im neu erstellten Ordner **GraphQLGenerated** GraphQL-Typen hinzu oder bearbeiten Sie sie. Sie können beispielsweise den Typ `DynamicBlocks.graphql` mit folgendem Inhalt hinzufügen:

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Sie haben jetzt das Adobe Experience Platform Mobile SDK in Ihre Commerce Mobile App integriert. Ereignisdaten fließen von Ihrer App an die Experience Platform Edge.

## So unterscheiden Sie Commerce-Ereignisse, die aus Apps generiert wurden

Alle [Ereignisse](events.md) enthalten ein Feld namens `channel`. Das Feld `channel` enthält `channel._id` und `channel._type`, die für eine Luma-Storefront Namespace-Werte von `"https://ns.adobe.com/xdm/channels/web"` bzw. `"https://ns.adobe.com/xdm/channel-types/web"` aufweisen. Bei einer mobilen Storefront sind die Namespace-Werte jedoch `"https://ns.adobe.com/xdm/channels/mobile-app"` bzw. `"https://ns.adobe.com/xdm/channel-types/mobile"`.

## Nächste Schritte

Informationen zum Abrufen von Real-Time CDP-Zielgruppen aus Ihrer mobilen Commerce-App, um Warenkorbpreisregeln, dynamische Bausteine und zugehörige Produktregeln zu informieren, finden Sie unter [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
