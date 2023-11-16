---
title: 活动
description: 了解每个事件捕获的数据。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f90ef4d2732a0b0676e0899712f94b41a1c2d85a
workflow-type: tm+mt
source-wordcount: '6894'
ht-degree: 0%

---

# [!DNL Data Connection] 活动

以下列出了安装时可用的Commerce事件 [!DNL Data Connection] 扩展。 这些事件收集的数据将发送到Adobe Experience Platform Edge。 您还可以创建 [自定义事件](custom-events.md) 收集未开箱即用的其他数据。

除了以下事件收集的数据之外，您还会获得 [其他数据](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) 由Adobe Experience Platform Web SDK提供。

## 店面活动

店面活动在购物者浏览您的网站时收集来自他们的匿名行为数据。 您可以使用这些事件收集的数据创建针对特定购物者集的促销和促销活动。 店面事件数据仅包括简单且可配置的产品。

>[!NOTE]
>
>所有店面活动包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，其中包括购物者的电子邮件地址（如果可用）和ECID。 通过在每个事件中包含此配置文件数据，您无需从Adobe Commerce中导入单独的用户帐户。

### addToCart

| 描述 | XDM事件名称 |
|---|---|
| 将产品添加到购物车时或购物车中的产品数量增加时触发。 | `commerce.productListAdds` |

#### 从addToCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.productListAdds` | 指示是否将产品添加到购物车。 值 `1` 表示已添加产品。 |
| `commerce.cart.cartID` | 标识客户购物车的唯一ID。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### openCart

| 描述 | XDM事件名称 |
|---|---|
| 在创建新购物车时触发，即在将产品添加到空购物车时。 | `commerce.productListOpens` |

#### 从openCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.productListOpens` | 指示是否已创建购物车。 值 `1` 表示已创建购物车。 |
| `commerce.cart.cartID` | 标识客户购物车的唯一ID。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### removeFromCart

| 描述 | XDM事件名称 |
|---|---|
| 每次删除产品或购物车中的产品数量减少时触发。 | `commerce.productListRemovals` |

#### 从removeFromCart收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.productListRemovals` | 指示产品是否已从购物车中删除。 值 `1` 表示产品已从购物车中删除。 |
| `commerce.cart.cartID` | 标识客户购物车的唯一ID。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### shoppingcartView

| 描述 | XDM事件名称 |
|---|---|
| 任何购物车页面加载时触发。 | `commerce.productListViews` |

#### 从shoppingCartView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.productListViews` | 指示是否已查看产品列表。 |
| `commerce.cart.cartID` | 标识客户购物车的唯一ID。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### pageView

| 描述 | XDM事件名称 |
|---|---|
| 任何页面加载时触发。 | `web.webpagedetails.pageViews` |

#### 从pageView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `web.webPageDetails.pageViews` | 指示是否已加载页面。 A `value` 之 `1` 指示页面已加载。 |
| `web.webPageDetails.URL` | 网页的规范或常用URL。 这可以是用于访问页面的实际URL，将使用进行记录 `Web Link`. |
| `web.webPageDetails.name` | 网页的规范名称。 此名称不一定是页面标题或直接与页面内容关联，但用于整理网站页面以进行分类。 |
| `web.webReferrer.URL` | 购物者在单击指向您的网站的链接之前访问过的网页的URL。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### productPageView

| 描述 | XDM事件名称 |
|---|---|
| 任何产品页面加载时触发。 | `commerce.productViews` |

#### 从productPageView收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.productViews` | 指示是否查看了产品。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### startCheckout

| 描述 | XDM事件名称 |
|---|---|
| 购物者单击结帐按钮时触发。 | `commerce.checkouts` |

#### 从startCheckout收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.checkouts` | 指示在结账过程中是否执行了某个操作。 |
| `commerce.cart.cartID` | 标识客户购物车的唯一ID。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### completeCheckout

| 描述 | XDM事件名称 |
|---|---|
| 购物者下订单时触发。 | `commerce.order` |

#### 从completeCheckout收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.purchases` | 指示是否已接受订单。 |
| `commerce.order` | 包含有关一个或多个产品所下订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.payments` | 此订单的付款清单。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易记录的唯一标识符。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此订单的付款方式。 选项包括： `cash`， `credit_card`， `debit_card`， `gift_card`， `check`， `paypal`， `wire_transfer`， `credit_card_reference`， `other`. |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 买方作为最终付款的一部分所支付的税额。 |
| `commerce.order.discountAmount` | 指示应用于整个订单的折扣金额。 |
| `commerce.order.createdDate` | 在商业系统中创建新订单的时间和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.shippingMethod` | 客户选择的配送方式，如标准配送、加急配送、店内提货等。 |
| `commerce.shipping.shippingAmount` | 客户必须支付的运费。 |  | `shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

## 配置文件事件

配置文件事件包括帐户信息，例如 `signIn`， `signOut`， `createAccount`、和 `editAccount`. 此数据用于帮助填充更好地定义区段或执行营销活动所需的关键客户详细信息，例如，如果您希望定位居住在纽约的购物者。

### 登录

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试登录时触发。 | `userAccount.login` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它并不表示操作成功。

#### 从登录收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `person` | 单独的操作者、联系人或所有者。 |
| `person.accountID` | 捕获用户帐户ID。 |
| `person.accountType` | 捕获用户帐户类型，如 `Personal` 或 `Company`，如果适用。 |
| `person.personalEmailID` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `personalEmail` | 捕获联系人详细信息 — 电子邮件和相关信息。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.login` | 指示访客是否尝试登录。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### 注销

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试注销时触发。 | `userAccount.logout` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它并不表示操作成功。

#### 从注销收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.logout` | 指示访客是否尝试注销。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### createAccount

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试创建帐户时触发。 | `userAccount.createProfile` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它并不表示操作成功。

#### 从createAccount收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `person` | 单独的操作者、联系人或所有者。 |
| `person.accountID` | 捕获用户帐户ID。 |
| `person.accountType` | 捕获用户帐户类型，如 `Personal` 或 `Company`，如果适用。 |
| `person.personalEmailID` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `personalEmail` | 捕获联系人详细信息 — 电子邮件和相关信息。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.updateProfile` | 指示用户是否已更新其帐户配置文件。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### editAccount

| 描述 | XDM事件名称 |
|---|---|
| 购物者尝试编辑帐户时触发。 | `userAccount.updateProfile` |

>[!NOTE]
>
> 此事件在尝试特定操作时触发。 它并不表示操作成功。

#### 从editAccount收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `person` | 单独的操作者、联系人或所有者。 |
| `person.accountID` | 捕获用户帐户ID。 |
| `person.accountType` | 捕获用户帐户类型，如 `Personal` 或 `Company`，如果适用。 |
| `person.personalEmailID` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `personalEmail` | 捕获联系人详细信息 — 电子邮件和相关信息。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.updateProfile` | 指示用户是否已更新其帐户配置文件。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

## 搜索事件

搜索事件会提供与购物者意图相关的数据。 洞察购物者的意图有助于商家了解购物者如何搜索商品、点击内容，最终购买或放弃。 例如，如果您希望定位现有购物者，这些购物者搜索您的热门产品，但从未购买该产品，您可能会如何使用此数据。

使用 `searchRequest.id` 和 `searchResponse.id` 在以下两个字段中都找到： `searchRequestSent` 和 `searchResponseReceived` 用于交叉引用搜索请求以响应相应搜索的事件。

### searchRequestSent

| 描述 | XDM事件名称 |
|---|---|
| 在“键入时搜索”弹出框中由以下事件触发：<br><br>按Enter键，单击 _查看全部_<br><br>&#x200B;由搜索结果页面上的以下事件触发：<br><br>选择一个过滤器，更改排序顺序(_排序方式_)，更改排序方向（升序或降序），更改每页的结果数(_每页显示数量_)，导航到下一页，导航到上一页，导航到其他页面 | `searchRequest` |

>[!NOTE]
>
>安装了B2B扩展的Adobe Commerce Enterprise Edition不支持搜索事件。

#### 从searchRequestSent收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchRequest` | 指示是否发送了搜索请求。 |
| `searchRequest.id` | 此特定搜索请求的唯一ID。 |
| `searchRequest.value` | 请求的可量化值。 |
| `siteSearch` | 包含有关搜索的信息。 |
| `siteSearch.filter` | 指示是否应用了任何过滤器来限制搜索结果。 |
| `siteSearch.filter.attribute` （过滤器） | 用于确定是否将其包含在搜索结果中的项目的方面。 |
| `siteSearch.filter.isRange` | 如果为true，则值表示值的可接受范围的端点。 |
| `siteSearch.filter.value` | 用于确定搜索结果中包含哪些项目的属性值。 |
| `siteSearch.sort` | 指示应如何对搜索结果排序。 |
| `siteSearch.sort.attribute` （排序） | 用于对搜索结果中的项目进行排序的属性。 |
| `siteSearch.sort.order` | 返回搜索结果的顺序。 |
| `siteSearch.query` | 搜索的词语。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### searchResponseReceived

| 描述 | XDM事件名称 |
|---|---|
| 当Live Search返回“键入时搜索”弹出框或搜索结果页面的结果时触发。 | `searchResponse` |

>[!NOTE]
>
>安装了B2B扩展的Adobe Commerce Enterprise Edition不支持搜索事件。

#### 从searchResponseReceived收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `searchResponse` | 指示是否已收到搜索响应。 |
| `searchResponse.id` | 此特定搜索响应的唯一ID。 |
| `searchResponse.value` | 响应的可量化值。 |
| `siteSearch.numberOfResults` | 返回的产品数。 |
| `siteSearch.suggestions` | 一个字符串数组，其中包含目录中存在的与搜索查询类似的产品和类别的名称。 |
| `productListItems` | 添加到购物车的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.productImageUrl` | 产品的主图像URL。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

## B2B事件

![适用于Adobe Commerce的B2B](../assets/b2b.svg) 对于B2B商家，您必须 [安装](install.md#install-the-b2b-extension) 该 `experience-platform-connector-b2b` 扩展以启用这些事件。

B2B事件包含 [申请列表](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 信息，例如创建、添加或删除申请列表。 通过跟踪特定于申请列表的事件，您可以查看客户经常购买的产品，并根据这些数据创建营销活动。

### createRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 购物者创建申购单列表时触发。 | `commerce.requisitionListOpens` |

#### 从createRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.requisitionListOpens` | 指示新申请列表的初始化。 |
| `commerce.requisitionList` | 客户创建的申请列表的属性。 |
| `commerce.requisitionList.ID` | 申购单列表的唯一标识符。 |
| `commerce.requisitionList.name` | 客户指定的申请列表的名称。 |
| `commerce.requisitionList.description` | 客户指定的申请列表的描述。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |

### addToRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 当购物者将产品添加到现有申请列表或创建列表时触发。 | `commerce.requisitionListAdds` |

#### 从addToRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.requisitionListAdds` | 指示向申请列表添加一个或多个产品。 |
| `commerce.requisitionList` | 客户创建的申请列表的属性。 |
| `commerce.requisitionList.ID` | 申购单列表的唯一标识符。 |
| `commerce.requisitionList.name` | 客户指定的申请列表的名称。 |
| `commerce.requisitionList.description` | 客户指定的申请列表的描述。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 已添加到申请列表的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

### removeFromRequisitionList

| 描述 | XDM事件名称 |
|---|---|
| 当购物者从申请列表中删除产品时触发。 | `commerce.requisitionListRemovals` |

#### 从removeFromRequisitionList收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.requsitionListRemovals` | 指示从申请列表中删除一个或多个产品。 |
| `commerce.requisitionList` | 客户创建的申请列表的属性。 |
| `commerce.requisitionList.ID` | 申购单列表的唯一标识符。 |
| `commerce.requisitionList.name` | 客户指定的申请列表的名称。 |
| `commerce.requisitionList.description` | 客户指定的申请列表的描述。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `productListItems` | 已添加到申请列表的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |

## 后台活动

后台事件包含有关订单状态的信息，例如订单是否已下达、取消、退款、已发运或已完成。 这些服务器端事件收集的数据显示购物者订单为360。 此视图可帮助商家在开发营销活动时更好地定位或分析整个订单状态。 例如，您可以发现特定产品类别中在一年中的不同时间表现出色的趋势。 例如，在较冷的月份销售较好的冬装或购物者多年来感兴趣的某些产品颜色。 此外，订单状态数据可帮助您通过了解购物者基于先前订单的转化倾向来计算存留期客户价值。

>[!NOTE]
>
>所有后台活动都包括 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，用于提供购物者的电子邮件地址。 通过在每个事件中包含此配置文件数据，您无需从Adobe Commerce中导入单独的用户帐户。

### orderPlaced

| 描述 | XDM事件名称 |
|---|---|
| 购物者下订单时触发。 | `commerce.backofficeOrderPlaced` |

#### 从orderPlaced收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.payments` | 此订单的付款清单。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易记录的唯一标识符。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此订单的付款方式。 计数，允许自定义值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 买方作为最终付款的一部分所支付的税额。 |
| `commerce.order.discountAmount` | 指示应用于整个订单的折扣金额。 |
| `commerce.order.createdDate` | 在商业系统中创建新订单的时间和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | 用于订单总额的ISO 4217货币代码。 |
| `commerce.shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.shippingMethod` | 客户选择的配送方式，如标准配送、加急配送、店内提货等。 |
| `commerce.shipping.shippingAmount` | 客户必须支付的运费。 |
| `commerce.shipping.currencyCode` | 用于装运总额的ISO 4217货币代码。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `commerce.billing.address` | 帐单邮寄地址。 |
| `commerce.billing.address.street1` | 主要街道级别信息、公寓号、街道号和街道名称 |
| `commerce.billing.address.street2` | 街道级别信息的附加字段。 |
| `commerce.billing.address.city` | 城市的名称。 |
| `commerce.billing.address.state` | 省/市/自治区名称。 这是自由格式字段。 |
| `commerce.billing.address.postalCode` | 位置的邮政编码。 并非所有国家/地区都提供邮政编码。 在一些国家/地区，这将仅包含邮政编码的一部分。 |
| `commerce.billing.address.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.id` | 此产品条目的行项目标识符。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |
| `productListItems.productImageUrl` | 产品的主图像URL。 |

### orderInvoiced

| 描述 | XDM事件名称 |
|---|---|
| 当商家提交发票以请求付款时触发。 | `commerce.backofficeOrderInvoiced` |

#### 从orderInvoiced收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.priceTotal` | 应用所有折扣和税费后此订单的总价。 |
| `commerce.order.currencyCode` | 用于订单总额的ISO 4217货币代码。 |
| `commerce.order.purchaseOrderNumber` | 购买者为此购买或合同分配的唯一标识符。 |
| `commerce.order.payments` | 此订单的付款清单。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.payments.paymentType` | 此订单的付款方式。 计数，允许自定义值。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.shippingMethod` | 客户选择的配送方式，如标准配送、加急配送、店内提货等。 |
| `commerce.shipping.shippingAmount` | 客户必须支付的运费。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.id` | 此产品条目的行项目标识符。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |

### orderItemsShipped

| 描述 | XDM事件名称 |
|---|---|
| 在发运订单时触发。 | `commerce.backofficeOrderItemsShipped` |

#### 从orderItemsShipped收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.payments` | 此订单的付款清单。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易记录的唯一标识符。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此订单的付款方式。 计数，允许自定义值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.priceTotal` | 应用所有折扣和税费后此订单的总价。 |
| `commerce.order.purchaseOrderNumber` | 购买者为此购买或合同分配的唯一标识符。 |
| `commerce.order.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.lastUpdatedDate` | 在商业系统中上次更新特定订单记录的时间。 |
| `commerce.shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.shippingMethod` | 客户选择的配送方式，如标准配送、加急配送、店内提货等。 |
| `commerce.shipping.shippingAmount` | 客户必须支付的运费。 |
| `commerce.shipping.address` | 实际配送地址。 |
| `commerce.shipping.address.street1` | 主要街道级别信息、公寓号、街道号和街道名称。 |
| `commerce.shipping.address.street2` | 可选街道信息第二行。 |
| `commerce.shipping.address.city` | 城市的名称。 |
| `commerce.shipping.address.state` | 国家的名称。 这是自由格式字段。 |
| `commerce.shipping.address.postalCode` | 位置的邮政编码。 并非所有国家/地区都提供邮政编码。 在一些国家/地区，这将仅包含邮政编码的一部分。 |
| `commerce.shipping.address.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `commerce.shipping.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.shipping.trackingNumber` | 装运承运人为订单项目装运提供的跟踪编号。 |
| `commerce.shipping.trackingURL` | 用于跟踪订单项目的装运状态的URL。 |
| `commerce.shipping.shipDate` | 订单中的一个或多个项目发运的日期。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `commerce.billing.address` | 帐单邮寄地址。 |
| `commerce.billing.address.street1` | 主要街道级别信息、公寓号、街道号和街道名称 |
| `commerce.billing.address.street2` | 街道级别信息的附加字段。 |
| `commerce.billing.address.city` | 城市的名称。 |
| `commerce.billing.address.state` | 省/市/自治区名称。 这是自由格式字段。 |
| `commerce.billing.address.postalCode` | 位置的邮政编码。 并非所有国家/地区都提供邮政编码。 在一些国家/地区，这将仅包含邮政编码的一部分。 |
| `commerce.billing.address.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |

### orderCanceled

| 描述 | XDM事件名称 |
|---|---|
| 购物者取消订单时触发。 | `commerce.backofficeOrderCancelled` |

#### 从orderCanceled收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.purchaseOrderNumber` | 购买者为此购买或合同分配的唯一标识符。 |
| `commerce.order.cancelDate` | 购物者取消订单的日期和时间。 |
| `commerce.order.lastUpdatedDate` | 在商业系统中上次更新特定订单记录的时间。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |

### orderLineItemRefreaded

| 描述 | XDM事件名称 |
|---|---|
| 当购物者为退货退款时触发。 | `commerce.backofficeCreditMemoIssued` |

#### 从orderLineItemRefreaded收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.lastUpdatedDate` | 在商业系统中上次更新特定订单记录的时间。 |
| `commerce.order.purchaseOrderNumber` | 购买者为此购买或合同分配的唯一标识符。 |
| `commerce.refunds` | 此订单的退款列表。 |
| `commerce.refunds.transactionID` | 此退款的唯一标识符。 |
| `commerce.refunds.refundAmount` | 退款的值。 |
| `commerce.refunds.refundPaymentType` | 此订单的付款方式。 计数，允许自定义值。 |
| `commerce.refunds.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |

### orderItemsReturnInitiated

| 描述 | XDM事件名称 |
|---|---|
| 购物者请求返回项目时触发。 | `commerce.backofficeOrderItemsReturnInitiated` |

#### 从orderItemsReturnInitiated收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.returns` | 此订单的RMA（退货授权）信息。 |
| `commerce.order.returns.returnID` | 此RMA（退货授权）的唯一标识符。 |
| `commerce.order.returns.returnStatus` | RMA（退货授权）的状态，如“待定”、“已关闭”等。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |
| `productListItems.returnItem` | 此物料的RMA（退货授权）信息。 |
| `productListItems.returnItem.returnStatus` | 返回项目的状态，如“待定”、“已批准”等。 |
| `productListItems.returnItem.returnReason` | 要求返回此项目的原因。 |
| `productListItems.returnItem.returnItemCondition` | 请求返回的项目的条件。 |
| `productListItems.returnItem.returnResolution` | 返回项目的请求解决方法，如退款、交换等。 |
| `productListItems.returnItem.returnQuantityRequested` | 购物者请求返回的此项目的编号。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 授权退回的此项目的编号。 |
| `productListItems.returnItem.eturnQuantityReceived` | 收到的返回项目数。 |
| `productListItems.returnItem.returnQuantityApproved` | 返回完全完成并批准的此项目的编号。 |

### orderItemReturnCompleted

| 描述 | XDM事件名称 |
|---|---|
| 当购物者请求返回的项完成时触发。 | `commerce.backofficeOrderItemsReturnCompleted` |

#### 从orderItemReturnCompleted收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.returns` | 此订单的RMA（退货授权）信息。 |
| `commerce.order.returns.returnID` | 此RMA（退货授权）的唯一标识符。 |
| `commerce.order.returns.returnStatus` | RMA（退货授权）的状态，如“待定”、“已关闭”等。 |
| `commerce.commerceScope` | 指示事件发生位置（商店视图、商店、网站等）。 |
| `commerce.commerceScope.environmentID` | 环境ID 32位数的字母数字ID，用连字符分隔。 |
| `commerce.commerceScope.storeCode` | 唯一商店代码。 每个网站可以有许多商店。 |
| `commerce.commerceScope.storeViewCode` | 唯一的商店视图代码。 每个商店可以有多个商店视图。 |
| `commerce.commerceScope.websiteCode` | 唯一的网站代码。 在一个环境中可以有许多网站。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |
| `productListItems.returnItem` | 此物料的RMA（退货授权）信息。 |
| `productListItems.returnItem.returnStatus` | 返回项目的状态，如“待定”、“已批准”等。 |
| `productListItems.returnItem.returnReason` | 要求返回此项目的原因。 |
| `productListItems.returnItem.returnItemCondition` | 请求返回的项目的条件。 |
| `productListItems.returnItem.returnResolution` | 返回项目的请求解决方法，如退款、交换等。 |
| `productListItems.returnItem.returnQuantityRequested` | 购物者请求返回的此项目的编号。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 授权退回的此项目的编号。 |
| `productListItems.returnItem.eturnQuantityReceived` | 收到的返回项目数。 |
| `productListItems.returnItem.returnQuantityApproved` | 返回完全完成并批准的此项目的编号。 |

### orderShipmentCompleted

| 描述 | XDM事件名称 |
|---|---|
| 在发运完成时触发。 | `commerce.backofficeOrderShipmentCompleted` |

#### 从orderShipmentCompleted收集的数据

下表描述了为此事件收集的数据。

| 字段 | 描述 |
|---|---|
| `commerce.order` | 包含有关订单的信息。 |
| `commerce.order.purchaseID` | 卖方为此购买或合同分配的唯一标识符。 无法保证ID是唯一的。 |
| `commerce.order.payments` | 此订单的付款清单。 |
| `commerce.order.payments.paymentTransactionID` | 此付款交易记录的唯一标识符。 |
| `commerce.order.payments.paymentAmount` | 付款的值。 |
| `commerce.order.payments.paymentType` | 此订单的付款方式。 计数，允许自定义值。 |
| `commerce.order.payments.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `commerce.order.taxAmount` | 买方作为最终付款的一部分所支付的税额。 |
| `commerce.order.createdDate` | 在商业系统中创建新订单的时间和日期。 例如， `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 一个或多个产品的运输详细信息。 |
| `commerce.shipping.shippingMethod` | 客户选择的配送方式，如标准配送、加急配送、店内提货等。 |
| `commerce.shipping.shippingAmount` | 客户必须支付的运费。 |
| `commerce.shipping.shipDate` | 订单中的一个或多个项目发运的日期。 |
| `commerce.shipping.address` | 实际配送地址。 |
| `commerce.shipping.address.street1` | 主要街道级别信息、公寓号、街道号和街道名称。 |
| `commerce.shipping.address.street2` | 可选街道信息第二行。 |
| `commerce.shipping.address.city` | 城市的名称。 |
| `commerce.shipping.address.state` | 国家的名称。 这是自由格式字段。 |
| `commerce.shipping.address.postalCode` | 位置的邮政编码。 并非所有国家/地区都提供邮政编码。 在一些国家/地区，这将仅包含邮政编码的一部分。 |
| `commerce.shipping.address.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `commerce.billing.address` | 帐单邮寄地址。 |
| `commerce.billing.address.street1` | 主要街道级别信息、公寓号、街道号和街道名称 |
| `commerce.billing.address.street2` | 街道级别信息的附加字段。 |
| `commerce.billing.address.city` | 城市的名称。 |
| `commerce.billing.address.state` | 省/市/自治区名称。 这是自由格式字段。 |
| `commerce.billing.address.postalCode` | 位置的邮政编码。 并非所有国家/地区都提供邮政编码。 在一些国家/地区，这将仅包含邮政编码的一部分。 |
| `commerce.billing.address.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `productListItems` | 订单中的一系列产品。 |
| `productListItems.SKU` | 库存单位。 产品的唯一标识符。 |
| `productListItems.name` | 产品的显示名称或人类可读的名称。 |
| `productListItems.priceTotal` | 产品行项目的总价。 |
| `productListItems.quantity` | 购物车中的产品件数。 |
| `productListItems.discountAmount` | 指示应用的折扣金额。 |
| `productListItems.currencyCode` | 此 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用的货币代码，如 `USD` 或 `EUR`. |
| `productListItems.selectedOptions` | 用于可配置产品的字段。 |
| `productListItems.selectedOptions.attribute` | 标识可配置产品的属性，如 `size` 或 `color`. |
| `productListItems.selectedOptions.value` | 标识属性的值，例如 `small` 或 `black`. |
| `productListItems.categories` | 包含有关产品类别的信息。 |
| `productListItems.categories.id` | 类别的唯一标识符。 |
| `productListItems.categories.name` | 类别的名称。 |
| `productListItems.categories.path` | 类别的路径。 |
