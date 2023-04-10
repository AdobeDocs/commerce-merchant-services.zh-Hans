---
title: 事件
description: 了解每个事件捕获的数据。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 8e5fb65363b2fa39f44da86d7ba0cc5459b18768
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Experience Platform连接器事件

下面列出了安装Commerce Connector扩展时可用的Experience Platform事件。 这些事件收集的数据会发送到Adobe Experience Platform Edge。 您还可以创建 [自定义事件](custom-events.md) 来收集开箱即用未提供的其他数据。

除了以下事件收集的数据之外，您还会 [其他数据](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

## 店面事件

店面事件在购物者浏览您的网站时从他们那里收集匿名化行为数据。 这些事件收集的数据可用于创建针对特定购物者集的促销活动和促销活动。

>[!NOTE]
>
>所有店面事件都包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，其中包括购物者的电子邮件地址（如果可用）和ECID。 通过在每个事件中包含此用户档案数据，您无需从Adobe Commerce中单独导入用户帐户。

### addToCart

| 描述 | XDM事件名称 |
|---|---|
| 当产品添加到购物车或购物车中产品的数量增加时触发。 | `commerce.productListAdds` |

#### 从addToCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListAdds` | 指示产品是否已添加到购物车。 值 `1` 表示已添加产品。 |
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 添加到购物车的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

### openCart

| 描述 | XDM事件名称 |
|---|---|
| 创建新购物车时触发，即将产品添加到空购物车时。 | `commerce.productListOpens` |

#### 从openCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListOpens` | 指示是否已创建购物车。 值 `1` 表示购物车已创建。 |
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 添加到购物车的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

### removeFromCart

| 描述 | XDM事件名称 |
|---|---|
| 每次删除产品时或每次购物车中产品的数量减少时触发。 | `commerce.productListRemovals` |

#### 从removeFromCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListRemovals` | 指示产品是否已从购物车中删除。 值 `1` 表示产品已从购物车中删除。 |
| `productListItems` | 从购物车中删除的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 从购物车中删除的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

### shoppingCartView

| 描述 | XDM事件名称 |
|---|---|
| 加载任何购物车页面时触发。 | `commerce.productListViews` |

#### 从shoppingCartView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListViews` | 指示是否查看了产品列表 |
| `productListItems` | 购物车中的一系列产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 购物车中的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

### pageView

| 描述 | XDM事件名称 |
|---|---|
| 加载任何页面时触发。 | `web.webpagedetails.pageViews` |

#### 从pageView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `pageViews` | 指示是否已加载页面。 A `value` of `1` 表示页面已加载。 |

### productPageView

| 描述 | XDM事件名称 |
|---|---|
| 加载任何产品页面时触发。 | `commerce.productViews` |

#### 从productPageView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productViews` | 指示产品是否已查看 |
| `productListItems` | 购物车中的一系列产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

### startCheckout

| 描述 | XDM事件名称 |
|---|---|
| 购物者单击结帐按钮时触发。 | `commerce.checkouts` |

#### 从startCheckout收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `checkouts` | 指示在结帐过程中是否发生操作 |
| `productListItems` | 购物车中的一系列产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 购物车中的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

### completeCheckout

| 描述 | XDM事件名称 |
|---|---|
| 购物者下订单时触发。 | `commerce.order` |

#### 从completeCheckout收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `purchases` | 指示是否接受了订单 |
| `order` | 包含有关一个或多个产品的已下单的信息 |
| `purchaseID` | 卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `orderType` | 指示已下单的类型，如“结帐”或“即时购买” |
| `payments` | 此订单的付款列表 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码。 例如， `USD` 或 `EUR`. |
| `paymentAmount` | 付款的价值 |
| `paymentType` | 此订单的付款方式。 选项包括： `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | 此付款项的唯一交易记录标识符 |
| `shipping` | 一个或多个产品的装运详细信息。 |
| `shippingMethod` | 客户选择的运输方法，如标准交货、快速交货、商店取货等 |
| `shippingAmount` | 购物车中商品的总装运成本 |
| `promotionID` | 促销活动的唯一标识符（如果有） |
| `personalEmail` | 指定个人电子邮件地址 |
| `address` | 例如，技术地址 `name@domain.com` RFC2822及后续标准中通常定义的 |
| `productListItems` | 购物车中的一系列产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 产品行项目的总价格 |
| `quantity` | 购物车中的产品件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于订单合计的货币代码。 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

## 用户档案事件

用户档案事件包括帐户信息，例如 `signIn`, `signOut`, `createAccount`和 `editAccount`. 此数据用于帮助填充更好地定义区段或执行营销活动所需的关键客户详细信息，例如，您希望定位居住在纽约的购物者。

### signIn

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试登录时触发。 | `userAccount.login` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

#### 从signIn收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `eventType` | 此时间系列记录的主事件类型，例如： `userAccount.login` |
| `person` | 个人行为者、联系人或所有者 |
| `accountID` | 捕获用户帐户ID |
| `personalEmailID` | 指定个人电子邮件的唯一标识符 |
| `address` | 例如，技术地址 `name@domain.com` RFC2822及后续标准中通常定义的 |
| `userAccount` | 指示任何忠诚度详细信息、首选项、登录流程和其他帐户首选项 |
| `login` | 指示访客是否尝试登录 |

### signOut

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试注销时触发。 | `userAccount.logout` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

#### 从signOut收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `eventType` | 此时间系列记录的主事件类型，例如： `userAccount.logout` |
| `userAccount` | 指示任何忠诚度详细信息、首选项、登录流程和其他帐户首选项 |
| `logout` | 指示访客是否尝试注销 |

### createAccount

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试创建帐户时触发。 | `userAccount.createProfile` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

#### 从createAccount收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `eventType` | 此时间系列记录的主事件类型，例如： `account.createProfile` |
| `person` | 个人行为者、联系人或所有者 |
| `accountID` | 捕获用户帐户ID |
| `accountType` | 捕获用户帐户类型，例如 `Personal` 或 `Company`（如果适用） |
| `personalEmailID` | 指定个人电子邮件的唯一标识符 |
| `address` | 例如，技术地址 `name@domain.com` RFC2822及后续标准中通常定义的 |
| `userAccount` | 指示任何忠诚度详细信息、首选项、登录流程和其他帐户首选项 |
| `createProfile` | 指示用户是否已创建帐户配置文件 |

### editAccount

| 描述 | XDM事件名称 |
|---|---|
| 当购物者尝试编辑帐户时触发。 | `userAccount.updateProfile` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

#### 从editAccount收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `eventType` | 此时间系列记录的主事件类型，例如： `account.updateProfile` |
| `person` | 个人行为者、联系人或所有者 |
| `accountID` | 捕获用户帐户ID |
| `accountType` | 捕获用户帐户类型，例如 `Personal` 或 `Company`（如果适用） |
| `personalEmailID` | 指定个人电子邮件的唯一标识符 |
| `personalEmail` | 指定个人电子邮件地址 |
| `address` | 例如，技术地址 `name@domain.com` RFC2822及后续标准中通常定义的 |
| `userAccount` | 指示任何忠诚度详细信息、首选项、登录流程和其他帐户首选项 |
| `updateProfile` | 指示用户是否已更新其帐户配置文件 |

## 搜索事件

搜索事件提供与购物者意图相关的数据。 对购物者意图的洞察有助于商家了解购物者如何搜索商品、他们点击的内容，以及最终购买或放弃的内容。 例如，如果您要定位那些在您的热门产品中搜索但从不购买该产品的现有购物者，则可以如何使用此数据。

使用 `uniqueIdentifier` 字段 `searchRequestSent` 和 `searchResponseReceived` 事件以交叉引用搜索请求到相应的搜索响应。

### searchRequestSent

| 描述 | XDM事件名称 |
|---|---|
| 在“键入时搜索”弹出窗口中，由以下事件触发：<br><br>按Enter键，单击 _查看全部_<br><br>&#x200B;由搜索结果页面上的以下事件触发：<br><br>选择过滤器，更改排序顺序(_排序依据_)、更改排序方向（升序或降序）、更改每页结果数(_每页显示数_)、导航到下一页、导航到上一页、导航到其他页面 | `searchRequest` |

>[!NOTE]
>
>安装了B2B模块的Adobe Commerce Enterprise Edition不支持搜索事件。

#### 从searchRequestSent收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchRequest` | 指示是否发送了搜索请求 |
| `id` | 此特定搜索请求的唯一ID |
| `filter` | 指示是否应用了任何过滤器来限制搜索结果 |
| `attribute` （过滤器） | 用于确定是否将项目包含在搜索结果中的项目 |
| `value` | 用于确定搜索结果中包含哪些项目的属性值 |
| `isRange` | 如果为true，则值表示可接受值范围的端点 |
| `sort` | 指示应如何对搜索结果排序 |
| `attribute` （排序） | 用于对搜索结果中的项目进行排序的属性 |
| `order` | 返回搜索结果的顺序 |
| `query` | 搜索的词 |

### searchResponseReceived

| 描述 | XDM事件名称 |
|---|---|
| 在实时搜索返回“键入时搜索”弹出窗口或搜索结果页面的结果时触发。 | `searchResponse` |

>[!NOTE]
>
>安装了B2B模块的Adobe Commerce Enterprise Edition不支持搜索事件。

#### 从searchResponseReceived收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchResponse` | 指示是否收到搜索响应 |
| `id` | 此特定搜索响应的唯一ID |
| `suggestions` | 字符串数组，其中包含目录中存在的与搜索查询类似的产品和类别的名称 |
| `numberOfResults` | 返回的产品数 |
| `productListItems` | 购物车中的一系列产品。 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `productImageUrl` | 产品的主图像URL |

## B2B事件

![B2B for Adobe Commerce](../assets/b2b.svg) 对于B2B商户，您必须 [安装](install.md#install-the-b2b-extension) the `experience-platform-connector-b2b` 扩展来启用这些事件。

B2B事件包含 [申请列表](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 信息，例如是否创建、添加或删除了申请列表。 通过跟踪特定于申请列表的事件，您可以查看客户经常购买的产品，并根据这些数据创建促销活动。

### createRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 购物者创建新申请列表时触发。 | `commerce.requisitionListOpens` |

#### 从createRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `requisitionList` | 客户创建的申请列表的属性 |
| `ID` | 申请列表的唯一标识符 |
| `name` | 客户指定的申请列表名称 |
| `description` | 客户指定的申请列表描述 |

### addToRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 当购物者将产品添加到现有请求列表或在创建新列表时触发。 | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` 类别视图页面或可配置产品不支持此功能。 产品查看页面和简单产品均支持此功能。

#### 从addToRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `requisitionList` | 客户创建的申请列表的属性 |
| `ID` | 申请列表的唯一标识符 |
| `name` | 客户指定的申请列表名称 |
| `description` | 客户指定的申请列表描述 |
| `productListItems` | 已添加到申请列表的产品数组 |
| `name` | 产品的显示名称或人类可读的名称 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `quantity` | 添加的产品件数 |
| `priceTotal` | 产品行项目的总价格 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码 |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

### removeFromRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 当购物者从申请列表中删除产品时触发。 | `commerce.requisitionListRemovals` |

#### 从removeFromRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `requisitionList` | 客户创建的申请列表的属性 |
| `ID` | 申请列表的唯一标识符 |
| `name` | 客户指定的申请列表名称 |
| `description` | 客户指定的申请列表描述 |
| `productListItems` | 已添加到申请列表的产品数组 |
| `name` | 产品的显示名称或人类可读的名称 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `quantity` | 添加的产品件数 |
| `priceTotal` | 产品行项目的总价格 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码 |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

## 后台活动

后台事件包含有关订单状态的信息，例如，订单是否被下达、取消、退还、发运或完成。 这些服务器端事件收集的数据显示购物者订单的360视图。 此视图可帮助商家在开发营销活动时更好地定位或分析整个订单状态。 例如，您可以发现某些产品类别中在一年中不同时间表现良好的趋势。 例如，在寒冷月份卖得更好的冬装，或者一些购物者多年来感兴趣的特定产品颜色。 此外，订单状态数据还可帮助您通过了解购物者基于先前订单进行转化的倾向来计算客户生命周期值。

>[!NOTE]
>
>所有后台活动都包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，提供购物者的电子邮件地址。 通过在每个事件中包含此用户档案数据，您无需从Adobe Commerce中单独导入用户帐户。

### orderPlaced

| 描述 | XDM事件名称 |
|---|---|
| 购物者下订单时触发。 | `commerce.backofficeOrderPlaced` |

#### 从orderPlaced收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `address` | 例如，技术地址 `name@domain.com` RFC2822及后续标准中通常定义的 |
| `eventType` | `commerce.backofficeOrderPlaced` |
| `productListItems` | 订单中的产品数组 |
| `name` | 产品的显示名称或人类可读的名称 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `quantity` | 购物车中的产品件数 |
| `priceTotal` | 产品行项目的总价格 |
| `discountAmount` | 指示应用的折扣金额 |
| `order` | 包含有关订单的信息 |
| `purchaseID` | 卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的 |
| `purchaseOrderNumber` | 购买者为此购买或合同分配的唯一标识符 |
| `payments` | 此订单的付款列表 |
| `paymentType` | 此订单的付款方式。 枚举后，允许自定义值。 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码 |
| `paymentAmount` | 付款的价值 |
| `taxAmount` | 买方作为最终付款的一部分支付的税额 |
| `createdDate` | 在商务系统中创建新订单的时间和日期。 例如， `2022-10-15T20:20:39+00:00` |
| `shipping` | 一个或多个产品的装运详细信息 |
| `shippingMethod` | 客户选择的运输方法，如标准交货、快速交货、商店取货等 |
| `shippingAddress` | 实物送货地址 |
| `street1` | 主要街道级别信息、公寓号、街道号和街道名称 |
| `shippingAmount` | 客户为装运所需支付的金额。 |
| `billingAddress` | 帐单邮政地址 |
| `street1` | 主要街道级别信息、公寓号、街道号和街道名称 |
| `street2` | 街道级别信息的其他字段 |
| `city` | 城市名称 |
| `state` | 州的名称。 这是自由格式字段。 |
| `postalCode` | 位置的邮政编码。 邮政编码并非适用于所有国家/地区。 在某些国家/地区，此代码将仅包含部分邮政编码。 |
| `country` | 政府管理领土的名称。 除 `xdm:countryCode`，这是一个自由格式字段，可使用任何语言提供国家/地区名称。 |

### orderItemsShipped

| 描述 | XDM事件名称 |
|---|---|
| 订单发运时触发。 | `commerce.backofficeOrderItemsShipped` |

#### 从orderItemsShipped收集的数据

下表描述了为此事件收集的数据。
|字段|描述| |—|—| |`address`|例如技术地址， `name@domain.com` RFC2822及后续标准中通常定义的| |`eventType`|`commerce.backofficeOrderItemsShipped`| |`productListItems`|订单中的产品数组| |`name`|产品的显示名称或人类可读名称| |`SKU`|库存单位。 产品的唯一标识符。| |`quantity`|购物车中的产品件数| |`priceTotal`|产品行项目的总价| |`discountAmount`|指示应用的折扣金额| |`order`|包含有关订单的信息| |`purchaseID`|卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的| |`purchaseOrderNumber`|购买者为此购买或合同分配的唯一标识符| |`payments`|此订单的付款清单| |`paymentType`|此订单的付款方式。 枚举后，允许自定义值。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码| |`paymentAmount`|付款的价值| |`trackingNumber`|装运承运人为订单物料发运提供的跟踪编号| |`trackingURL`|用于跟踪订单物料发运状态的URL| |`lastUpdatedDate`|在商务系统中上次更新特定订单记录的时间| |`shipping`|一个或多个产品的装运详细信息| |`shippingMethod`|客户选择的装运方法，如标准交货、快速交货、在店取货等| |`shippingAddress`|实际送货地址| |`street1`|主要街道级别信息、公寓号、街道号和街道名称| |`shippingAmount`|客户为装运所需支付的金额。| |`billingAddress`|帐单邮政地址| |`street1`|主要街道级别信息、公寓号、街道号和街道名称| |`street2`|街道级别信息的其他字段| |`city`|城市名称| |`state`|状态的名称。 这是自由格式字段。| |`postalCode`|位置的邮政编码。 邮政编码并非适用于所有国家/地区。 在某些国家/地区，此代码将仅包含部分邮政编码。| |`country`|政府管理领土的名称。 除 `xdm:countryCode`，这是一个自由格式字段，可使用任何语言提供国家/地区名称。|

### orderCancelled

| 描述 | XDM事件名称 |
|---|---|
| 购物者取消订单时触发。 | `commerce.backofficeOrderCancelled` |

#### 从orderCancelled收集的数据

下表描述了为此事件收集的数据。
|字段|描述| |—|—| |`address`|例如技术地址， `name@domain.com` RFC2822及后续标准中通常定义的| |`eventType`|`commerce.backofficeOrderCancelled`| |`productListItems`|订单中的产品数组| |`name`|产品的显示名称或人类可读名称| |`SKU`|库存单位。 产品的唯一标识符。| |`quantity`|购物车中的产品件数| |`priceTotal`|产品行项目的总价| |`discountAmount`|指示应用的折扣金额| |`order`|包含有关订单的信息| |`purchaseID`|卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的| |`purchaseOrderNumber`|购买者为此购买或合同分配的唯一标识符| |`cancelDate`|购物者取消订单的日期和时间| |`lastUpdatedDate`|在商务系统中上次更新特定订单记录的时间|

### creditMemoIssued

| 描述 | XDM事件名称 |
|---|---|
| 当购物者按顺序返回项目时触发。 | `commerce.backofficeCreditMemoIssued` |

#### 从creditMemoIssuled收集的数据

下表描述了为此事件收集的数据。
|字段|描述| |—|—| |`address`|例如技术地址， `name@domain.com` RFC2822及后续标准中通常定义的| |`eventType`|`commerce.backofficeCreditMemoIssued`| |`productListItems`|订单中的产品数组| |`order`|包含有关订单的信息| |`purchaseID`|卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的| |`purchaseOrderNumber`|购买者为此购买或合同分配的唯一标识符| |`lastUpdatedDate`|在商务系统中上次更新特定订单记录的时间|

### orderShipmentCompleted

| 描述 | XDM事件名称 |
|---|---|
| 当购物者按顺序返回项目时触发。 | `commerce.backofficeOrderShipmentCompleted` |

#### 从orderShimpentCompleted收集的数据

下表描述了为此事件收集的数据。
|字段|描述| |—|—| |`address`|例如技术地址， `name@domain.com` RFC2822及后续标准中通常定义的| |`eventType`|`commerce.backofficeOrderShipmentCompleted`| |`productListItems`|订单中的产品数组| |`name`|产品的显示名称或人类可读名称| |`SKU`|库存单位。 产品的唯一标识符。| |`quantity`|购物车中的产品件数| |`priceTotal`|产品行项目的总价| |`discountAmount`|指示应用的折扣金额| |`order`|包含有关订单的信息| |`purchaseID`|卖方为此采购或合同分配的唯一标识符。 无法保证ID是唯一的| |`purchaseOrderNumber`|购买者为此购买或合同分配的唯一标识符| |`taxAmount`|买方作为最终付款的一部分支付的税额。| |`createdDate`|在商务系统中创建新订单的时间和日期。 例如， `2022-10-15T20:20:39+00:00`| |`payments`|此订单的付款清单| |`paymentType`|此订单的付款方式。 枚举后，允许自定义值。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于此付款项的货币代码| |`paymentAmount`|付款的价值| |`shipping`|一个或多个产品的装运详细信息| |`shippingMethod`|客户选择的装运方法，如标准交货、快速交货、在店取货等| |`shippingAddress`|实际送货地址| |`street1`|主要街道级别信息、公寓号、街道号和街道名称| |`shippingAmount`|客户为装运所需支付的金额。| |`personalEmail`|指定个人电子邮件地址| |`address`|例如技术地址， `name@domain.com` RFC2822及后续标准中通常定义的| |`billingAddress`|帐单邮政地址| |`street1`|主要街道级别信息、公寓号、街道号和街道名称| |`street2`|街道级别信息的其他字段| |`city`|城市名称| |`state`|状态的名称。 这是自由格式字段。| |`postalCode`|位置的邮政编码。 邮政编码并非适用于所有国家/地区。 在某些国家/地区，此数据仅包含部分邮政编码。| |`country`|政府管理领土的名称。 除 `xdm:countryCode`，这是一个自由格式字段，可使用任何语言提供国家/地区名称。|
