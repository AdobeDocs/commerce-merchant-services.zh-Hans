---
title: “结帐流程”
description: “概述 [!DNL Quick Checkout] 在Adobe Commerce流动。”
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流量

本节概述了使用 [!DNL Quick Checkout] (对于Adobe Commerce扩展)。

成功 [!DNL Quick Checkout] 流程包含以下步骤：

1. 打开店面，并在购物车中添加商品。
1. 继续结帐。

![结帐](assets/proceed-checkout.png)

1. 出现提示时，输入与 [!DNL Bolt] 帐户。
1. 输入发送到该密码的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或电话号码。
1. 登录后 [!DNL Bolt] 帐户，结帐详细信息会自动填写：

   - 装运信息
   - 付款方法

   >[!NOTE]
   >
   > 即使您的结账详细信息已自动填写，您也可以使用现有的钱包信息（地址或信用卡信息）。

1. 下单。

的 [!DNL Quick Checkout] 与标准的其他Adobe Commerce结账选项(例如 [礼品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代码](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] 用例

的 [!DNL Quick Checkout] 允许在结帐流程期间使用多个用例：

- 已注册的来宾用户 [!DNL Bolt] 帐户。
- 以新用户作为来宾 [!DNL Bolt] 帐户。
- 已注册/未注册的现有Adobe Commerce用户 [!DNL Bolt] 帐户。

## 来宾用户结账：工作原理

来宾结帐体验与已登录的体验不同。 当购物者输入进入结账的电子邮件地址时， [!DNL Quick Checkout] 验证以查找现有 [!DNL Bolt] 帐户。

### 已注册 [!DNL Bolt] 帐户

如果 [!DNL Bolt] 帐户，购物者将继续其 [!DNL Quick Checkout] 无缝结账体验：

1. 输入发送到该密码的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或移动设备，具体取决于 [!DNL Bolt] 帐户。
1. 登录后 [!DNL Bolt] 帐户，它会自动填写结帐详细信息：

   - 装运信息
   - 付款方法

1. 下单。

>[!TIP]
>
> 来宾用户将下订单，并可在Adobe Commerce中注册。

### 新建 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 找到帐户后，购物者会继续其默认的现成Adobe Commerce结账，购物者会提供所有必需的详细信息以下订单：

- 运输和账单信息
- 装运方法
- 复核付款方法
- 此时会出现一个复选框以注册 [!DNL Bolt] 以便在下订单前更快地结帐。 他们可以同意创建其 [!DNL Bolt] 帐户。

   ![记住 [!DNL Bolt]](assets/checked-bolt.png)

- 来宾用户下订单，并可在Adobe Commerce中注册。

## 现有Adobe Commerce用户：工作原理

现有用户在使用 [!DNL Quick Checkout] 更快的结帐体验。

当购物者输入进入结账的电子邮件地址时， [!DNL Quick Checkout] 验证以查找现有 [!DNL Bolt] 帐户。

### 已注册 [!DNL Bolt] 帐户Adobe Commerce用户

如果 [!DNL Bolt] 找到帐户后，购物者会继续其默认的现成Adobe Commerce结账，购物者会提供所有必需的详细信息，然后下单：

- 运输和账单信息
- 装运方法
- 复核付款方法

请参阅 [疑难解答](../quick-checkout/troubleshooting.md) 主题。

>[!NOTE]
>
> 如果用户具有 [!DNL Bolt] 帐户和电子邮件在Adobe Commerce中未显示为已注册，它会触发一次性密码(OTP)登录。 请参阅 [注册 [!DNL Bolt] 帐户](#registered-bolt-account) 流量。

### 新建 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 找到帐户后，购物者会继续其默认的Adobe Commerce结账，购物者会从其保存的信息中选择所有必需的详细信息以下订单：

- 运输和账单信息
- 装运方法
- 复核付款方法
- 此时会出现一个复选框以注册 [!DNL Bolt] 以便在下订单前更快地结帐。 他们可以同意创建其 [!DNL Bolt] 帐户。

   ![记住 [!DNL Bolt]](assets/checked-bolt.png)

## 获取帮助

联系人 [Adobe Commerce支持](mailto:quick-checkout-support@adobe.com) 来寻求帮助。
