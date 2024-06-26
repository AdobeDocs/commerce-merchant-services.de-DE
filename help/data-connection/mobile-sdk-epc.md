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

Integrieren der [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) mit der mobilen Commerce-App können Händler Commerce senden  [Ereignisdaten](events.md) zum Experience Platform-Edge hinzu.

Wenn Commerce-Ereignisdaten am Rande verfügbar sind, können sie von anderen Adobe Experience Cloud-Anwendungen aufgerufen werden. Beispielsweise können Sie die Daten zum Erstellen von Zielgruppen in Real-Time CDP verwenden und [Verwenden dieser Zielgruppen](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) , um Ihre mobile Commerce-App zu personalisieren.

## Konfiguration

Um mit der Verwendung des Adobe Experience Platform Mobile SDK mit Commerce zu beginnen, installieren und konfigurieren Sie das SDK in der Experience Platform. Schließen Sie dann die Konfiguration in Commerce ab.

### Experience Platform

1. Informationen zu den Funktionen mobiler Apps erhalten Sie unter [Tutorial zu Adobe Experience Cloud in Apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Installieren und Konfigurieren](https://developer.adobe.com/client-sdks/documentation/getting-started/) das SDK in Experience Platform.

   >[!NOTE]
   >
   >Das Schema, das Sie auf der Experience Platform erstellen und konfigurieren, ist dasselbe Schema, das Sie im Anwendungscode in Ihrer Commerce-Mobile-App verwenden.

### Handel

Nachdem Sie die SDK-Konfiguration für die Experience Platform abgeschlossen haben, fügen Sie die SDK-Konfiguration zu Commerce hinzu.

1. Um Commerce-Ereignisdaten über das SDK an die Experience Platform zu senden, müssen Sie ein XDM-Schema im Anwendungscode angeben. Dieses Schema muss dem Schema entsprechen [konfiguriert](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) für das SDK in der Experience Platform.

   Das folgende Beispiel zeigt, wie Sie die `web.webpagedetails.pageViews` -Ereignis und legen Sie `identityMap` unter Verwendung des E-Mail-Felds.

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
   - Release: http://_Version_.commerceSite.cloud/graphql/

1. Um Daten aus den Commerce GraphQL-Endpunkten abzurufen, generieren Sie zunächst die erforderlichen Dateien und Ordner in Ihrem Projekt mithilfe der [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. In Ihrem Projektverzeichnis: [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.

   1. [Initialisieren](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) Apollo Codegen CLI.

      Dadurch wird eine `apollo-codegen-configuration.json` -Datei.

   1. Generieren Sie die erforderlichen GraphQL-Dateien und -Ordner in Ihrem Projekt, indem Sie den Inhalt der `apollo-codegen-configuration.json` -Datei mit der folgenden Zeichenfolge:

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

   1. [Abrufen](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) das Schema Commerce GraphQL .

      Stellen Sie sicher, dass der Pfad zum `./apollo-codegen-config.json` -Datei, die den Verweis auf das Schema Commerce GraphQL enthält.

   1. [Erzeugen](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) den Quellcode.

      Stellen Sie sicher, dass der Pfad zum `./apollo-codegen-config.json` -Datei, die die Konfigurationsinformationen zum Generieren der erforderlichen Dateien und Verzeichnisse enthält.

   1. Innerhalb des neu erstellten **GraphQLGenerated** Ordner, fügen Sie GraphQL-Typen hinzu oder bearbeiten Sie sie. Sie können beispielsweise eine `DynamicBlocks.graphql` Geben Sie folgenden Inhalt ein:

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

## Unterscheidung von Commerce-Ereignissen, die aus Mobile Apps generiert wurden

Alle [events](events.md) enthält ein Feld namens `channel`. Die `channel` -Feld enthält `channel._id` und `channel._type` , die für eine Luma-Storefront Namespace-Werte von `"https://ns.adobe.com/xdm/channels/web"` und `"https://ns.adobe.com/xdm/channel-types/web"` bzw. Bei einer mobilen Storefront sind die Namespace-Werte jedoch `"https://ns.adobe.com/xdm/channels/mobile-app"` und `"https://ns.adobe.com/xdm/channel-types/mobile"` bzw.

## Nächste Schritte

Informationen zum Abrufen von Real-Time CDP-Zielgruppen aus Ihrer mobilen Commerce-App, um Warenkorbpreisregeln, dynamische Bausteine und zugehörige Produktregeln zu informieren, finden Sie unter [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
