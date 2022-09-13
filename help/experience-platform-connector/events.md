---
title: 事件
description: 了解每个事件捕获并查看完整架构定义的哪些数据。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 589d22f488572411b6632ac37d7bc5b752f72e2d
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---

# Experience Platform连接器事件

下面列出了安装Commerce Connector扩展时可用的Experience Platform事件。 这些事件收集的数据会发送到Adobe Experience Platform Edge。 您还可以创建 [自定义事件](custom-events.md) 来收集开箱即用未提供的其他数据。

除了以下事件收集的数据之外，您还会 [附加数据](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

>[!NOTE]
>
>所有事件都包括 `personID` 字段中，该字段是人员的唯一标识符。

## addToCart

当产品添加到购物车或购物车中产品的数量增加时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts).

### 类型

店面

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListAdds` | 指示产品是否已添加到购物车。 值 `1` 表示已添加产品。 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 在应用所有折扣和税后，此订单的合计 |
| `quantity` | 客户表示他们需要产品的件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

## shoppingCartView

加载任何购物车页面时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts).

### 类型

店面

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productListViews` | 指示是否查看了产品列表 |
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 在应用所有折扣和税后，此订单的合计 |
| `quantity` | 客户表示他们需要产品的件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

## pageView

加载任何页面时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts).

### 类型

店面

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `pageViews` | 指示是否已加载页面。 A `value` of `1` 表示页面已加载。 |

## productPageView

加载任何产品页面时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts).

### 类型

店面

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `productViews` | 指示产品是否已查看 |
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 在应用所有折扣和税后，此订单的合计 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

## startCheckout

购物者单击结帐按钮时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts).

### 类型

店面

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `checkouts` | 指示在结帐过程中是否发生操作 |
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 在应用所有折扣和税后，此订单的合计 |
| `quantity` | 客户表示他们需要产品的件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 产品的货币 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |
| `cartID` | 标识客户购物车的唯一ID |

## completeCheckout

购物者下订单时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts).

### 类型

店面

### 收集的数据

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
| `productListItems` | 添加到购物车的一组产品 |
| `SKU` | 库存单位。 产品的唯一标识符。 |
| `name` | 产品的显示名称或人类可读的名称 |
| `priceTotal` | 在应用所有折扣和税后，此订单的合计 |
| `quantity` | 客户表示他们需要产品的件数 |
| `discountAmount` | 指示应用的折扣金额 |
| `currencyCode` | 的 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 用于订单合计的货币代码。 |
| `productImageUrl` | 产品的主图像URL |
| `selectedOptions` | 用于可配置产品的字段。 `attribute` 标识可配置产品的属性，例如 `size` 或 `color` 和 `value` 标识属性的值，例如 `small` 或 `black`. |

## signIn

购物者尝试登录时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts).

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

### 类型

用户档案

### 收集的数据

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

## signOut

购物者尝试注销时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts).

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

### 类型

用户档案

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `eventType` | 此时间系列记录的主事件类型，例如： `userAccount.logout` |
| `userAccount` | 指示任何忠诚度详细信息、首选项、登录流程和其他帐户首选项 |
| `logout` | 指示访客是否尝试注销 |

## createAccount

购物者尝试创建帐户时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts).

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

### 类型

用户档案

### 收集的数据

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

## editAccount

当购物者尝试编辑帐户时触发。 [完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts).

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它不表示操作成功。

### 类型

用户档案

### 收集的数据

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

## searchRequestSent

在“键入时搜索”弹出窗口中，由以下事件触发：

- 按Enter
- 单击 _查看全部_

由搜索结果页面上的以下事件触发：

- 选择过滤器
- 更改排序顺序(_排序依据_)
- 更改排序方向（升序或降序）
- 更改每页的结果数(_每页显示数_)
- 导航到下一页
- 导航到上一页
- 导航到其他页面

[完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts).

>[!NOTE]
>
>安装了B2B模块的Adobe Commerce Enterprise Edition不支持搜索事件。

### 类型

搜索

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchRequest` | 指示是否发送了搜索请求 |
| `filter` | 指示是否应用了任何过滤器来限制搜索结果 |
| `attribute` （过滤器） | 用于确定是否将项目包含在搜索结果中的项目 |
| `value` | 用于确定搜索结果中包含哪些项目的属性值 |
| `isRange` | 如果为true，则值表示可接受值范围的端点 |
| `sort` | 指示应如何对搜索结果排序 |
| `attribute` （排序） | 用于对搜索结果中的项目进行排序的属性 |
| `order` | 返回搜索结果的顺序 |
| `query` | 搜索的词 |

## searchResponseReceived

在实时搜索返回“键入时搜索”弹出窗口或搜索结果页面的结果时触发。

[完整模式](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)

>[!NOTE]
>
>安装了B2B模块的Adobe Commerce Enterprise Edition不支持搜索事件。

### 类型

搜索

### 收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchResponse` | 指示是否收到搜索响应 |
| `suggestions` | 字符串数组，其中包含目录中存在的与搜索查询类似的产品和类别的名称 |
| `numberOfResults` | 返回的产品数 |
| `productListItems` | 添加到购物车的一组产品。 包括 `SKU`（库存单位）及 `name` （显示名称或人类可读名称） |
