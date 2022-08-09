---
title: 使用Adobe Experience Platform标记收集商务数据
description: 了解如何使用Adobe Experience Platform标记收集商务数据。
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '2126'
ht-degree: 0%

---

# 使用Adobe Experience Platform标记收集商务数据

虽然您可以使用Experience Platform连接器发布和订阅店面事件，但某些商户可能已经使用数据收集解决方案，例如 [Adobe Experience Platform标记](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en). 对于这些商户，Adobe Commerce在使用Adobe Commerce事件SDK的Experience Platform连接器中提供了仅发布选项。

![Experience Platform连接器数据流](assets/tags-data-flow.png)
_Experience Platform连接器数据流与标记_

在本主题中，您将了解如何将Experience Platform连接器提供的店面事件值映射到您已在使用的Adobe Experience Platform标记解决方案。

## 从Adobe Commerce收集事件数据

要收集商务事件数据，请执行以下操作：

- 安装 [Adobe Commerce Event SDK](https://www.npmjs.com/package/@adobe/magento-storefront-events-sdk). 有关PHP店面，请参阅 [安装](install.md) 主题。 有关PWA Studio店面，请参阅 [PWA Studio指南](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

   >[!NOTE]
   >
   > 做 **not** [配置](connect-data.md) 组织ID和数据流ID。

## 将商务店面数据映射到Adobe Experience Platform

要将Commerce Storefront数据映射到Adobe Experience Platform，请在Adobe Experience Platform标记中配置并安装以下内容：

1. [设置标记属性](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) 在Adobe Experience Platform数据收集中。

1. 在 **创作**，选择 **扩展** ，然后安装和配置以下扩展：

   - [Adobe客户端数据层](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [发布标记](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) 到您的开发环境。

1. 关注 **事件映射** 以下步骤为特定事件配置数据元素和规则。

### 事件映射

由于使用标记的数据收集与使用Adobe Commerce Event SDK的数据收集不同，因此了解这两个框架中使用的对等术语非常重要。

| Adobe Experience Platform标记术语 | Adobe Commerce事件SDK术语 |
|---|---|
| _数据元素_ | 上下文 |
| _规则_ | 事件 |
|  | _规则条件_  — 事件侦听器（来自ACDL）<br><br>_规则操作_  — 事件处理程序(发送到Adobe Experience Platform) |

使用特定于Adobe Commerce的事件数据更新Adobe Experience Platform标记中的数据元素和规则时，将执行一些常见步骤。

例如，让我们将Adobe Commerce `signOut` 事件到Adobe Experience Platform标记。 除您设置的特定值外，下面列出的步骤将介绍如何添加 [数据元素](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) 和 [规则](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule)，适用于您添加到标记的所有Adobe Commerce事件。

1. 创建数据元素：

   ![创建新数据元素](assets/create-new-data-elements.png)
   _创建新数据元素_

1. 已设置 **名称** to `Sign out`.

1. 已设置 **扩展** to `Adobe Experience Platform Web SDK`.

1. 已设置 **数据元素类型** to `XDM object`.

1. 选择 **沙盒** 和 **架构** 要更新的。

1. 在 **userAccount** > **注销**，请设置 **值** in **访客注销** to `1`.

   ![更新注销值](assets/signout-value.png)
   _更新注销值_

1. 创建规则：

   ![创建新规则](assets/create-new-rule.png)
   _创建新规则_

1. 已设置 **扩展** to `Adobe Client Data Layer`.

1. 已设置 **事件类型** to `Data Pushed`.

1. 选择 **特定事件** 并设置 **要注册的事件/密钥** to `sign-out`.

1. 添加操作。

1. 已设置 **扩展** to `Adobe Experience Platform Web SDK`.

1. 已设置 **操作类型** to `Send Event`.

1. 已设置 **实例** to `Alloy`.

1. 已设置 **类型** to `userAccount.logout`.

1. 已设置 **XDM数据** to `%sign out%`.

1. 单击 **保存**.

   您在架构中为 `signOut` 事件。Adobe Commerce 此外，您还创建了一个规则，该规则包含从Adobe Commerce店面触发该事件时应发生的特定操作。

对于下面描述的每个Adobe Commerce事件，在标记中重复上述步骤。

### 可用事件

对于以下每个事件，请按照上述步骤将Adobe Commerce事件映射到您的XDM。

- [“signOut”](#signout)
- [“signIn”](#signin)
- [&#39;createAccount&#39;](#createaccount)
- [&#39;editAccount&#39;](#editaccount)
- [“pageView”](#pageview)
- [“productView”](#productview)
- [&#39;searchRequestSent&#39;](#searchrequestsent)
- [&#39;searchResponseReceived&#39;](#searchresponsereceived)
- [“addToCart”](#addtocart)
- [“viewCart”](#viewcart)
- [“removeFromCart”](#removefromcart)
- [&#39;initiateCheckout&#39;](#initiatecheckout)
- [“placeOrder”](#placeorder)

### signOut {#signout}

#### 数据元素

创建以下数据元素：

1. 注销：

   - **名称**: `Sign out`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `userAccount` > `logout`
   - **访客注销**: **值** = `1`

#### 规则 

- **名称**: `Sign out`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `sign-out`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `userAccount.logout`
- **XDM数据**: `%sign-out%`

### signIn {#signin}

#### 数据元素

创建以下数据元素：

1. 帐户电子邮件：

   - **名称**: `Account email`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountEmail`

1. 帐户类型：

   - **名称**: `Account type`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountType`

1. 帐户ID:

   - **名称**: `Account ID`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径***: `accountContext.accountId`

1. 登录：

   - **名称**: `Sign in`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `userAccount` > `login`
   - **访客登录**: **值** = `1`

#### 规则 

- **名称**: `Sign in`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `sign-in`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `userAccount.login`
- **XDM数据**: `%sign-in%`

### createAccount {#createaccount}

#### 数据元素

创建以下数据元素：

1. 帐户电子邮件：

   - **名称**: `Account email`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountEmail`

1. 帐户类型：

   - **名称**: `Account type`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountType`

1. 帐户ID:

   - **名称**: `Account ID`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径***: `accountContext.accountId`

1. 创建帐户：

   - **名称**: `Create account`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `userAccount` > `createProfile`
   - **帐户配置文件创建**: **值** = `1`

#### 规则 

- **名称**: `Create account`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `create-account`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `userAccount.createProfile`
- **XDM数据**: `%create account%`

### editAccount {#editaccount}

#### 数据元素

创建以下数据元素：

1. 帐户电子邮件：

   - **名称**: `Account email`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountEmail`

1. 帐户类型：

   - **名称**: `Account type`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `accountContext.accountType`

1. 帐户ID:

   - **名称**: `Account ID`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径***: `accountContext.accountId`

1. 编辑帐户：

   - **名称**: `Edit account`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `userAccount` > `updateProfile`
   - **帐户配置文件创建**: **值** = `1`

#### 规则

- **名称**: `Edit account`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `edit-account`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `userAccount.updateProfile`
- **XDM数据**: `%edit account%`

### pageView {#pageview}

#### 数据元素

创建以下数据元素：

1. 页面名称：

   - **名称**: `Page name`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `pageContext.pageName`

#### 规则 

- **名称**: `Page view`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `Core-Library Loaded`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `web.webPageDetails.pageViews`
- **XDM数据**: `%page view%`

### productView {#productview}

#### 数据元素

创建以下数据元素：

1. 产品名称：

   - **名称**: `Product name`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.name`

1. 产品SKU:

   - **名称**: `Product sku`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.sku`

1. 货币代码：

   - **名称**: `Currency code`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.currencyCode`

1. 特价：

   - **名称**: `Special price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.specialPrice`

1. 固定价格：

   - **名称**: `Regular price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.regularPrice`

1. 产品价格：

   - **名称**: `Product price`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**: `return _satellite.getVar('product regular price') || _satellite.getVar('product special price')`

1. 产品视图：

   - **名称**: `Product view`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 选择 **提供单个项目** ，然后单击 **添加项目** 按钮。 由于此视图是用于PDP，因此可以使用单个项目填充。

#### 规则 

- **名称**: `Product view`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `product-page-view`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.productViews`
- **XDM数据**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### 数据元素

创建以下数据元素：

1. 搜索输入

   - **名称**: `Search input`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `searchInputContext.units[0]`

1. 搜索输入短语

   - **名称**: `Search input phrase`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   `return _satellite.getVar('search input').phrase;`
   ```

1. 搜索输入排序

   - **名称**: `Search input sort`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 搜索输入过滤器

   - **名称**: `Search input filters`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 搜索请求：

   - **名称**: `Search request`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `siteSearch` > `phrase`
   - **值**:尚未可用
   - **字段组**: `siteSearch` > `sort`. 选择 **提供整个对象**.
   - **字段组**: `siteSearch` > `filter`. 选择 **提供整个对象**.
   - **字段组**: `searchRequest` > `value`
   - **值**: **值** = `1`

#### 规则 

- **名称**: `Search request sent`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `search-request-sent`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `searchRequest`
- **XDM数据**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### 数据元素

创建以下数据元素：

1. 搜索结果：

   - **名称**: `Search results`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `searchResultsContext.units[0]`

1. 产品的搜索结果编号：

   - **名称**: `Search result number of products`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('search result').productCount;
   ```

1. 搜索结果产品：

   - **名称**: `Search result products`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 搜索结果建议：

   - **名称**: `Search result products`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. 搜索响应：

   - **名称**: `Search response`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `siteSearch` > `suggestions`. 选择 **提供整个对象**.
   - **字段组**: `siteSearch` > `numberOfResults`
   - **值**: `%search result number of products%`
   - **字段组**: `productListItems`. 选择 **提供整个对象**.
   - **字段组**: `searchResponse` > `value`
   - **值**: **值** = `1`

#### 规则 

- **名称**: `Search Response Received`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `search-response-received`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `searchResponse`
- **XDM数据**: `%search response%`

### addToCart {#addtocart}

#### 数据元素

创建以下数据元素：

1. 产品名称：

   - **名称**: `Product name`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.name`

1. 产品SKU:

   - **名称**: `Product sku`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.sku`

1. 货币代码：

   - **名称**: `Currency code`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.currencyCode`

1. 产品特价：

   - **名称**: `Product special price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.specialPrice`

1. 产品正常价格：

   - **名称**: `Product regular price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.regularPrice`

1. 产品价格：

   - **名称**: `Product price`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 购物车：

   - **名称**: `Cart`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `shoppingCartContext`

1. 购物车ID:

   - **名称**: `Cart id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 添加到购物车：

   - **名称**: `Add to cart`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 选择 **提供单个项目** ，然后单击 **添加项目** 按钮。 由于此视图是用于PDP，因此可以使用单个项目填充。
   - **字段组**: `commerce` > `cart` > `cartID`
   - **购物车ID**: **值** = `%cart id%`
   - **字段组**: `commerce` > `productListAdds` > `id`
   - **唯一标识符**: **值** = `1`

#### 规则 

- **名称**: `Add to cart`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `add-to-cart`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.productListAdds`
- **XDM数据**: `%add to cart%`

### viewCart {#viewcart}

#### 数据元素

创建以下数据元素：

1. 店面：

   - **名称**: `Storefront`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `storefrontInstanceContext`

1. 购物车：

   - **名称**: `Cart`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `shoppingCartContext`

1. 购物车ID:

   - **名称**: `Cart id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 产品列表项：

   - **名称**: `Product list items:`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 查看购物车：

   - **名称**: `View cart`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 对于 `productListItems`，则可能有多个项目需要预先计算。 选择 **productListItems** > **填充整个数组**.
   - **字段组**: `commerce` > `cart` > `cartID`
   - **购物车ID**: **值** = `%cart id%`
   - **字段组**: `commerce` > `productListAdds` > `id`
   - **唯一标识符**: **值** = `1`

#### 规则 

- **名称**: `View cart`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `shopping-cart-view`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.productListViews`
- **XDM数据**: `%view cart%`

### removeFromCart {#removefromcart}

#### 数据元素

创建以下数据元素：

1. 产品名称：

   - **名称**: `Product name`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.name`

1. 产品SKU:

   - **名称**: `Product sku`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.sku`

1. 货币代码：

   - **名称**: `Currency code`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.currencyCode`

1. 产品特价：

   - **名称**: `Product special price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.specialPrice`

1. 产品正常价格：

   - **名称**: `Product regular price`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `productContext.pricing.regularPrice`

1. 产品价格：

   - **名称**: `Product price`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 购物车：

   - **名称**: `Cart`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `shoppingCartContext`

1. 购物车ID:

   - **名称**: `Cart id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 从购物车中删除：

   - **名称**: `Remove from cart`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 选择 **提供单个项目** ，然后单击 **添加项目** 按钮。 由于此视图是用于PDP，因此可以使用单个项目填充。
   - **字段组**: `commerce` > `cart` > `cartID`
   - **购物车ID**: **值** = `%cart id%`
   - **字段组**: `commerce` > `productListRemovals`
   - **唯一标识符**: **值** = `1`

#### 规则 

- **名称**: `Remove from cart`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `remove-from-cart`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.productListRemovals`
- **XDM数据**: `%remove from cart%`

### initiateCheckout {#initiatecheckout}

#### 数据元素

创建以下数据元素：

1. 店面：

   - **名称**: `Storefront`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `storefrontInstanceContext`

1. 购物车：

   - **名称**: `Cart`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `shoppingCartContext`

1. 购物车ID:

   - **名称**: `Cart id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 产品列表项：

   - **名称**: `Product list items`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 启动结帐：

   - **名称**: `Initiate checkout`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 对于 `productListItems`，则可能有多个项目需要预先计算。 选择 **productListItems** > **填充整个数组**.
   - **字段组**: `commerce` > `cart` > `cartID`
   - **购物车ID**: **值** = `%cart id%`
   - **字段组**: `commerce` > `checkouts`
   - **唯一标识符**: **值** = `1`

#### 规则 

- **名称**: `Initiate checkout`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `initiate-checkout`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.checkouts`
- **XDM数据**: `%initiate checkout%`

### placeOrder {#placeorder}

#### 数据元素

创建以下数据元素：

1. 店面：

   - **名称**: `Storefront`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `storefrontInstanceContext`

1. 购物车：

   - **名称**: `Cart`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `shoppingCartContext`

1. 购物车ID:

   - **名称**: `Cart id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 顺序：

   - **名称**: `Order`
   - **扩展**: `Adobe Client Data Layer`
   - **数据元素类型**: `Data Layer Computed State`
   - **[可选] 路径**: `orderContext`

1. 商务订单：

   - **名称**: `Commerce order`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 订单发运：

   - **名称**: ` Order shipping`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. 促销活动ID:

   - **名称**: `Promotion id`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. 产品列表项：

   - **名称**: `Product list items`
   - **扩展**: `Core`
   - **数据元素类型**: `Custom Code`
   - **Open Editor**:

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

1. 下单：

   - **名称**: `Place order`
   - **扩展**: `Adobe Experience Platform Web SDK`
   - **数据元素类型**: `XDM object`
   - **字段组**: `productListItems`. 对于 `productListItems`，则可能有多个项目需要预先计算。 选择 **productListItems** > **填充整个数组**.
   - **字段组**: `commerce` > `order`
   - **唯一标识符**: **值** = `%commerce order%`
   - **字段组**: `commerce` > `shipping`
   - **唯一标识符**: **值** = ` %order shipping%`
   - **字段组**: `commerce` > `promotionID`
   - **促销ID**: **值** = `%promotion id%`
   - **字段组**: `commerce` > `purchases` > `value`
   - **值**: **值** = `1`

#### 规则 

- **名称**: `Place order`
- **扩展**: `Adobe Client Data Layer`
- **事件类型**: `Data Pushed`
- **特定事件**: `place-order`

##### 操作

- **扩展**: `Adobe Experience Platform Web SDK`
- **操作类型**: `Send event`
- **类型**: `commerce.order`
- **XDM数据**: `%place order%`

## 设置标识

Experience Platform连接器配置文件根据 `personID` 和 `personalEmail` XDM体验事件中的身份字段。 

如果您之前的设置依赖于不同的字段，则可以继续使用这些字段。 要设置Experience Platform连接器配置文件标识字段，必须设置以下字段：

- `personalEmail`  — 仅限帐户事件 — 对帐户事件执行上述步骤
- `personID`  — 所有其他事件：

   - 如果您已在捕获 `ECID` 在标记中，您可以 `personID` 在所有Adobe Experience Platform Web SDK规则中 `%ECID%`.
   - 要捕获 `ECID` 在标记中，必须 **自定义代码** 按照以下规则对发送事件规则执行操作 [标记文档](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html). 请参阅以下示例。

### 示例

下图显示了如何配置 `pageView` 事件 `personID` 在Experience Platform连接器中：

1. 使用ECID的自定义代码配置数据元素：

   ![使用自定义代码配置数据元素](assets/set-custom-code-ecid.png)
   _使用自定义代码配置数据元素_

1. 添加ECID自定义代码：

   ![在数据元素中设置ECID的代码](assets/code-to-set-ecid.png)
   _在数据元素中设置ECID的代码_

1. 将personID设置为ECID时，更新XDM架构：

   ![将personID设置为ECID](assets/set-personid-as-ecid.png)
   _将personID设置为ECID_

1. 定义检索ECID的规则操作：

   ![检索ECID](assets/rule-retrieve-ecid.png)
   _检索ECID_

## 设置同意

Adobe Commerce和Experience Platform连接器数据收集同意默认启用。 选择退出通过 [`mg_dnt` cookie](https://docs.magento.com/user-guide/stores/cookie-reference.html). 如果您选择使用 `mg_dnt` 来管理同意。 的 [Adobe Experience Platform Web SDK文档](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) 还有几个用于管理同意的其他选项。

1. 创建 **核心自定义代码** 数据元素(`%do not track cookie%`) `mg_dnt` cookie:

   ![创建不跟踪数据元素](assets/element-dnt-cookie.png)
   _创建不跟踪数据元素_

1. 创建 **核心自定义代码** 数据元素(`%consent%`) `out` 如果已设置cookie和 `in` 否则：

   ![创建同意数据元素](assets/element-consent-dnt-cookie.png)
   _创建同意数据元素_

1. 使用配置Adobe Experience Platform Web SDK扩展 `%consent%` 数据元素：

   ![在同意下更新SDK](assets/config-sdk-consent.png)
   _在同意下更新SDK_

## 警告

- 未执行关闭Experience Platform收集的步骤，会导致事件被重复计数
- 如果不按本主题所述设置映射/事件，则可能会影响Adobe Analytics展示板
- 如果禁用数据收集，则无法通过Experience Platform连接器设置Target