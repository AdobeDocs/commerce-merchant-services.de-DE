---
title: Erfassen von Commerce-Daten mit Adobe Experience Platform Tags
description: Erfahren Sie, wie Sie Commerce-Daten mithilfe von Adobe Experience Platform-Tags erfassen.
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '2126'
ht-degree: 0%

---

# Erfassen von Commerce-Daten mit Adobe Experience Platform Tags

Sie können zwar den Experience Platform-Connector zum Veröffentlichen und Abonnieren von Storefront-Ereignissen verwenden, aber einige Händler verwenden möglicherweise bereits eine Datenerfassungslösung, z. B. die [Adobe Experience Platform-Tags](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en). Für diese Händler bietet Adobe Commerce im Experience Platform-Connector, der das Adobe Commerce Event SDK verwendet, die Option &quot;Nur Veröffentlichung&quot;.

![Experience Platform Connector-Datenfluss](assets/tags-data-flow.png)
_Experience Platform Connector-Datenfluss mit Tags_

In diesem Thema erfahren Sie, wie Sie die vom Experience Platform-Connector bereitgestellten Storefront-Ereigniswerte der bereits verwendeten Adobe Experience Platform-Tags-Lösung zuordnen.

## Erfassen von Ereignisdaten aus Adobe Commerce

So erfassen Sie Commerce-Ereignisdaten:

- Installieren Sie die [Adobe Commerce Event SDK](https://www.npmjs.com/package/@adobe/magento-storefront-events-sdk). Informationen zu PHP-Storefronts finden Sie im Abschnitt [install](install.md) Thema. PWA Studio-Storefronts: [PWA Studio-Handbuch](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

   >[!NOTE]
   >
   > Do **not** [konfigurieren](connect-data.md) die Organisations-ID und die Datastream-ID.

## Zuordnen von Commerce-Storefront-Daten zu Adobe Experience Platform

Um Commerce-Storefront-Daten Adobe Experience Platform zuzuordnen, konfigurieren und installieren Sie Folgendes innerhalb von Adobe Experience Platform-Tags:

1. [Einrichten einer Tag-Eigenschaft](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) in der Adobe Experience Platform-Datenerfassung.

1. under **Authoring** auswählen **Erweiterungen** und installieren und konfigurieren Sie die folgenden Erweiterungen:

   - [Adobe Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [Veröffentlichungs-Tag](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) in Ihre Entwicklungsumgebung.

1. Befolgen Sie die **Ereigniszuordnung** Gehen Sie wie folgt vor, um Datenelemente und Regeln für bestimmte Ereignisse zu konfigurieren.

### Ereigniszuordnung

Da sich die Datenerfassung mit Tags von der Verwendung des Adobe Commerce Event SDK unterscheidet, müssen die in beiden Frameworks verwendeten äquivalenten Begriffe verstanden werden.

| Adobe Experience Platform-Tags-Begriff | Adobe Commerce Event SDK - Begriff |
|---|---|
| _Datenelemente_ | context |
| _Regeln_ | event |
|  | _Regelbedingungen_ - Ereignis-Listener (aus ACDL)<br><br>_Regelaktionen_ - Ereignishandler (an Adobe Experience Platform senden) |

Wenn Sie die Datenelemente und Regeln in Adobe Experience Platform-Tags mit Adobe Commerce-spezifischen Ereignisdaten aktualisieren, werden Sie einige gängige Schritte ausführen.

Fügen wir beispielsweise die Adobe Commerce hinzu `signOut` -Ereignis auf Adobe Experience Platform-Tags. In den unten beschriebenen Schritten wird beschrieben, wie Sie - mit Ausnahme der festgelegten Werte - [Datenelemente](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) und [Regeln](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule), die für alle Adobe Commerce-Ereignisse gelten, die Sie zu Tags hinzufügen.

1. Erstellen Sie ein Datenelement:

   ![Neues Datenelement erstellen](assets/create-new-data-elements.png)
   _Neues Datenelement erstellen_

1. Satz **Name** nach `Sign out`.

1. Satz **Erweiterung** nach `Adobe Experience Platform Web SDK`.

1. Satz **Datenelementtyp** nach `XDM object`.

1. Wählen Sie die **Sandbox** und **Schema** die Sie aktualisieren möchten.

1. under **userAccount** > **Abmelden**, legen Sie die **value** in **Besucher-Abmeldung** nach `1`.

   ![Abmeldewert aktualisieren](assets/signout-value.png)
   _Abmeldewert aktualisieren_

1. Erstellen einer Regel:

   ![Neue Regel erstellen](assets/create-new-rule.png)
   _Neue Regel erstellen_

1. Satz **Erweiterung** nach `Adobe Client Data Layer`.

1. Satz **Ereignistyp** nach `Data Pushed`.

1. Auswählen **Bestimmtes Ereignis** und legen Sie die **Ereignis/Schlüssel zur Registrierung** nach `sign-out`.

1. Fügen Sie eine Aktion hinzu.

1. Satz **Erweiterung** nach `Adobe Experience Platform Web SDK`.

1. Satz **Aktionstyp** nach `Send Event`.

1. Satz **Instanz** nach `Alloy`.

1. Satz **Typ** nach `userAccount.logout`.

1. Satz **XDM-Daten** nach `%sign out%`.

1. Klicken **Speichern**.

   Sie haben ein Datenelement in Ihrem Schema für die `signOut` -Ereignis aus Adobe Commerce. Außerdem haben Sie eine Regel mit einer bestimmten Aktion erstellt, die auftreten sollte, wenn dieses Ereignis aus der Adobe Commerce-Storefront ausgelöst wird.

Wiederholen Sie die oben genannten Schritte in den Tags für jedes der unten beschriebenen Adobe Commerce-Ereignisse.

### Verfügbare Ereignisse

Ordnen Sie für jedes der folgenden Ereignisse die Adobe Commerce-Ereignisse Ihrem XDM zu, indem Sie die oben genannten Schritte ausführen.

- [`signOut`](#signout)
- [`signIn`](#signin)
- [`createAccount`](#createaccount)
- [`editAccount`](#editaccount)
- [`pageView`](#pageview)
- [&quot;productView&quot;](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [`viewCart`](#viewcart)
- [`removeFromCart`](#removefromcart)
- [`initiativeCheckout`](#initiatecheckout)
- [`placeOrder`](#placeorder)

### signOut {#signout}

#### Datenelemente

Erstellen Sie das folgende Datenelement:

1. Abmelden:

   - **Name**: `Sign out`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `userAccount` > `logout`
   - **Besucher-Abmeldung**: **Wert** = `1`

#### Regeln 

- **Name**: `Sign out`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `sign-out`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.logout`
- **XDM-Daten**: `%sign-out%`

### signIn {#signin}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `Account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountEmail`

1. Kontotyp:

   - **Name**: `Account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `Account ID`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path***: `accountContext.accountId`

1. Anmelden:

   - **Name**: `Sign in`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `userAccount` > `login`
   - **Besucheranmeldung**: **Wert** = `1`

#### Regeln 

- **Name**: `Sign in`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `sign-in`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.login`
- **XDM-Daten**: `%sign-in%`

### createAccount {#createaccount}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `Account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountEmail`

1. Kontotyp:

   - **Name**: `Account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `Account ID`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path***: `accountContext.accountId`

1. Konto erstellen:

   - **Name**: `Create account`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `userAccount` > `createProfile`
   - **Kontoprofil erstellen**: **Wert** = `1`

#### Regeln 

- **Name**: `Create account`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `create-account`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.createProfile`
- **XDM-Daten**: `%create account%`

### editAccount {#editaccount}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Konto-E-Mail:

   - **Name**: `Account email`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountEmail`

1. Kontotyp:

   - **Name**: `Account type`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `accountContext.accountType`

1. Konto-ID:

   - **Name**: `Account ID`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path***: `accountContext.accountId`

1. Konto bearbeiten:

   - **Name**: `Edit account`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `userAccount` > `updateProfile`
   - **Kontoprofil erstellen**: **Wert** = `1`

#### Regeln

- **Name**: `Edit account`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `edit-account`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `userAccount.updateProfile`
- **XDM-Daten**: `%edit account%`

### pageView {#pageview}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Seitenname:

   - **Name**: `Page name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `pageContext.pageName`

#### Regeln 

- **Name**: `Page view`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `Core-Library Loaded`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `web.webPageDetails.pageViews`
- **XDM-Daten**: `%page view%`

### productView {#productview}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `Product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `Product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Währungscode:

   - **Name**: `Currency code`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Sonderpreis:

   - **Name**: `Special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Regelpreis:

   - **Name**: `Regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produktpreis:

   - **Name**: `Product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**: `return _satellite.getVar('product regular price') || _satellite.getVar('product special price')`

1. Produktansicht:

   - **Name**: `Product view`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Auswählen **Bereitstellen einzelner Elemente** und klicken Sie auf **Element hinzufügen** Schaltfläche. Da diese Ansicht für eine Produktdetailseiten gilt, können Sie mit einem einzelnen Element füllen.

#### Regeln 

- **Name**: `Product view`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `product-page-view`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productViews`
- **XDM-Daten**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Sucheingabe

   - **Name**: `Search input`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `searchInputContext.units[0]`

1. Sucheingabesatz

   - **Name**: `Search input phrase`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   `return _satellite.getVar('search input').phrase;`
   ```

1. Suche nach Eingabe

   - **Name**: `Search input sort`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. Sucheingabefelder

   - **Name**: `Search input filters`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. Suchanfrage:

   - **Name**: `Search request`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `siteSearch` > `phrase`
   - **value**: Noch nicht verfügbar
   - **Feldergruppe**: `siteSearch` > `sort`. Auswählen **Gesamtes Objekt bereitstellen**.
   - **Feldergruppe**: `siteSearch` > `filter`. Auswählen **Gesamtes Objekt bereitstellen**.
   - **Feldergruppe**: `searchRequest` > `value`
   - **value**: **Wert** = `1`

#### Regeln 

- **Name**: `Search request sent`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `search-request-sent`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `searchRequest`
- **XDM-Daten**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Suchergebnisse:

   - **Name**: `Search results`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `searchResultsContext.units[0]`

1. Suchergebnisnummer der Produkte:

   - **Name**: `Search result number of products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('search result').productCount;
   ```

1. Suchergebnisprodukte:

   - **Name**: `Search result products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. Suchergebnisvorschläge:

   - **Name**: `Search result products`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. Suchantwort:

   - **Name**: `Search response`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `siteSearch` > `suggestions`. Auswählen **Gesamtes Objekt bereitstellen**.
   - **Feldergruppe**: `siteSearch` > `numberOfResults`
   - **value**: `%search result number of products%`
   - **Feldergruppe**: `productListItems`. Auswählen **Gesamtes Objekt bereitstellen**.
   - **Feldergruppe**: `searchResponse` > `value`
   - **value**: **Wert** = `1`

#### Regeln 

- **Name**: `Search Response Received`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `search-response-received`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `searchResponse`
- **XDM-Daten**: `%search response%`

### addToCart {#addtocart}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `Product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `Product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Währungscode:

   - **Name**: `Currency code`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Sonderpreis für das Produkt:

   - **Name**: `Product special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Produktregulärer Preis:

   - **Name**: `Product regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produktpreis:

   - **Name**: `Product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Warenkorb:

   - **Name**: `Cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `Cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Zum Warenkorb hinzufügen:

   - **Name**: `Add to cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Auswählen **Bereitstellen einzelner Elemente** und klicken Sie auf **Element hinzufügen** Schaltfläche. Da diese Ansicht für eine Produktdetailseiten gilt, können Sie mit einem einzelnen Element füllen.
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListAdds` > `id`
   - **Eindeutige Kennung**: **value** = `1`

#### Regeln 

- **Name**: `Add to cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `add-to-cart`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListAdds`
- **XDM-Daten**: `%add to cart%`

### viewCart {#viewcart}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Storefront:

   - **Name**: `Storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Warenkorb:

   - **Name**: `Cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `Cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Produktlistenelemente:

   - **Name**: `Product list items:`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Warenkorb anzeigen:

   - **Name**: `View cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Für `productListItems`kann es mehrere vorberechnete Elemente geben. Auswählen **productListItems** > **Gesamtes Array ausfüllen**.
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListAdds` > `id`
   - **Eindeutige Kennung**: **value** = `1`

#### Regeln 

- **Name**: `View cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `shopping-cart-view`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListViews`
- **XDM-Daten**: `%view cart%`

### removeFromCart {#removefromcart}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Produktname:

   - **Name**: `Product name`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.name`

1. Produkt-SKU:

   - **Name**: `Product sku`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.sku`

1. Währungscode:

   - **Name**: `Currency code`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.currencyCode`

1. Sonderpreis für das Produkt:

   - **Name**: `Product special price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.specialPrice`

1. Produktregulärer Preis:

   - **Name**: `Product regular price`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `productContext.pricing.regularPrice`

1. Produktpreis:

   - **Name**: `Product price`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Warenkorb:

   - **Name**: `Cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `Cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Aus Warenkorb entfernen:

   - **Name**: `Remove from cart`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Auswählen **Bereitstellen einzelner Elemente** und klicken Sie auf **Element hinzufügen** Schaltfläche. Da diese Ansicht für eine Produktdetailseiten gilt, können Sie mit einem einzelnen Element füllen.
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `productListRemovals`
   - **Eindeutige Kennung**: **value** = `1`

#### Regeln 

- **Name**: `Remove from cart`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `remove-from-cart`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.productListRemovals`
- **XDM-Daten**: `%remove from cart%`

### initiativeCheckout {#initiatecheckout}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Storefront:

   - **Name**: `Storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Warenkorb:

   - **Name**: `Cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `Cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Produktlistenelemente:

   - **Name**: `Product list items`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Checkout starten:

   - **Name**: `Initiate checkout`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Für `productListItems`kann es mehrere vorberechnete Elemente geben. Auswählen **productListItems** > **Gesamtes Array ausfüllen**.
   - **Feldergruppe**: `commerce` > `cart` > `cartID`
   - **Warenkorb-ID**: **Wert** = `%cart id%`
   - **Feldergruppe**: `commerce` > `checkouts`
   - **Eindeutige Kennung**: **value** = `1`

#### Regeln 

- **Name**: `Initiate checkout`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `initiate-checkout`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.checkouts`
- **XDM-Daten**: `%initiate checkout%`

### placeOrder {#placeorder}

#### Datenelemente

Erstellen Sie die folgenden Datenelemente:

1. Storefront:

   - **Name**: `Storefront`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `storefrontInstanceContext`

1. Warenkorb:

   - **Name**: `Cart`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `shoppingCartContext`

1. Warenkorb-ID:

   - **Name**: `Cart id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Reihenfolge:

   - **Name**: `Order`
   - **Erweiterung**: `Adobe Client Data Layer`
   - **Datenelementtyp**: `Data Layer Computed State`
   - **[Optional] path**: `orderContext`

1. Commerce-Bestellung:

   - **Name**: `Commerce order`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. Bestellversand:

   - **Name**: ` Order shipping`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. Promotion-ID:

   - **Name**: `Promotion id`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. Produktlistenelemente:

   - **Name**: `Product list items`
   - **Erweiterung**: `Core`
   - **Datenelementtyp**: `Custom Code`
   - **Editor öffnen**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Platzierungsreihenfolge:

   - **Name**: `Place order`
   - **Erweiterung**: `Adobe Experience Platform Web SDK`
   - **Datenelementtyp**: `XDM object`
   - **Feldergruppe**: `productListItems`. Für `productListItems`kann es mehrere vorberechnete Elemente geben. Auswählen **productListItems** > **Gesamtes Array ausfüllen**.
   - **Feldergruppe**: `commerce` > `order`
   - **Eindeutige Kennung**: **Wert** = `%commerce order%`
   - **Feldergruppe**: `commerce` > `shipping`
   - **Eindeutige Kennung**: **value** = ` %order shipping%`
   - **Feldergruppe**: `commerce` > `promotionID`
   - **Promotion-ID**: **Wert** = `%promotion id%`
   - **Feldergruppe**: `commerce` > `purchases` > `value`
   - **Wert**: **Wert** = `1`

#### Regeln 

- **Name**: `Place order`
- **Erweiterung**: `Adobe Client Data Layer`
- **Ereignistyp**: `Data Pushed`
- **Bestimmtes Ereignis**: `place-order`

##### Aktionen

- **Erweiterung**: `Adobe Experience Platform Web SDK`
- **Aktionstyp**: `Send event`
- **Typ**: `commerce.order`
- **XDM-Daten**: `%place order%`

## Identität festlegen

Experience Platform Connector-Profile werden verbunden und basierend auf dem `personID` und `personalEmail` Identitätsfelder in XDM-Erlebnisereignissen. 

Wenn Sie bereits über ein Setup verfügen, das auf verschiedenen Feldern basiert, können Sie diese weiterhin verwenden. Um die Identitätsfelder des Experience Platform Connector-Profils festzulegen, müssen Sie die folgenden Felder festlegen:

- `personalEmail` - Nur Kontoereignisse - führen Sie die oben beschriebenen Schritte für Kontoereignisse aus.
- `personID` - Alle anderen Ereignisse:

   - Wenn Sie bereits erfasst haben `ECID` in Tags können Sie `personID` in allen Adobe Experience Platform Web SDK-Regeln auf `%ECID%`.
   - Zu erfassen `ECID` in -Tags müssen Sie eine **Benutzerspezifischer Code** -Aktion auf die Regeln für das Senden von Ereignissen folgen, [Dokumentation zu Tags](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html). Siehe Beispiel unten.

### Beispiel

Die folgenden Abbildungen zeigen, wie Sie eine `pageView` -Ereignis mit `personID` in Experience Platform Connector:

1. Konfigurieren Sie das Datenelement mit benutzerdefiniertem Code für ECID:

   ![Datenelement mit benutzerdefiniertem Code konfigurieren](assets/set-custom-code-ecid.png)
   _Datenelement mit benutzerdefiniertem Code konfigurieren_

1. Fügen Sie benutzerdefinierten ECID-Code hinzu:

   ![Code zum Festlegen der ECID im Datenelement](assets/code-to-set-ecid.png)
   _Code zum Festlegen der ECID im Datenelement_

1. Aktualisieren Sie das XDM-Schema mit der personID als ECID:

   ![PersonID als ECID festlegen](assets/set-personid-as-ecid.png)
   _PersonID als ECID festlegen_

1. Definieren Sie Regelaktionen, die ECID abrufen:

   ![ECID abrufen](assets/rule-retrieve-ecid.png)
   _ECID abrufen_

## Einverständniserklärung

Die Datenerfassung für Adobe Commerce und Experience Platform Connector ist standardmäßig aktiviert. Die Opt-out-Funktion wird über das [`mg_dnt` Cookie](https://docs.magento.com/user-guide/stores/cookie-reference.html). Sie können die hier beschriebenen Schritte ausführen, wenn Sie `mg_dnt` um das Einverständnis zu verwalten. Die [Dokumentation zum Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) verfügt über mehrere zusätzliche Optionen zur Verwaltung der Zustimmung.

1. Erstellen Sie eine **Benutzerdefinierter Core-Code** Datenelement (`%do not track cookie%`) für die `mg_dnt` Cookie:

   ![Datenelement erstellen: Datenelement nicht verfolgen](assets/element-dnt-cookie.png)
   _Datenelement erstellen: Datenelement nicht verfolgen_

1. Erstellen Sie eine **Benutzerdefinierter Core-Code** Datenelement (`%consent%`), die `out` wenn Cookie gesetzt ist und `in` ansonsten:

   ![Datenelement &quot;Einwilligung&quot;](assets/element-consent-dnt-cookie.png)
   _Datenelement &quot;Einwilligung&quot;_

1. Konfigurieren der Adobe Experience Platform Web SDK-Erweiterung mit `%consent%` Datenelement:

   ![SDK mit Zustimmung aktualisieren](assets/config-sdk-consent.png)
   _SDK mit Zustimmung aktualisieren_

## Warnungen

- Wenn Sie die Schritte zum Deaktivieren der Erfassung von Experience Platformen nicht ausführen, werden die Ereignisse doppelt gezählt
- Das nicht wie in diesem Thema beschriebene Einrichten von Zuordnungen/Ereignissen kann sich auf Adobe Analytics-Pinnwände auswirken
- Sie können Target nicht über den Experience Platform-Connector einrichten, wenn die Datenerfassung deaktiviert ist