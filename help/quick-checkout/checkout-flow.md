---
title: “Adobe Commerce中的结账流程”
description: “概述 [!DNL Quick Checkout] Adobe Commerce中的flow。”
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流量

此部分概述了使用的典型签出体验 [!DNL Quick Checkout] (适用于Adobe Commerce扩展)。

成功 [!DNL Quick Checkout] 流程包含以下步骤：

1. 打开店面并在购物车中添加商品。
1. 继续结帐。

![结账](assets/proceed-checkout.png)

>[!NOTE]
>
> 您可以为商家启用自动登录。 参见 [Bolt的“启用自动登录”主题](https://help.bolt.com/products/embedded/direct-api/auto-login/) 了解更多信息。

1. 出现提示时，输入与关联的电子邮件地址 [!DNL Bolt] 帐户。
1. 输入发送给该用户的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或电话号码。

![OTP弹出窗口](assets/new-logo-otp-email.png)

1. 使用登录后 [!DNL Bolt] 帐户，签出详细信息会自动填写：

   - 配送信息
   - 付款方式

   >[!NOTE]
   >
   > 即使自动填写了结帐详细信息，您也可以使用现有的wallet信息（地址或信用卡信息）。

1. 下订单。

此 [!DNL Quick Checkout] 与标准的其他Adobe Commerce签出选项兼容，例如 [礼品卡](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 或 [折扣代码](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] 用例

此 [!DNL Quick Checkout] 允许在结账流程期间使用多个用例：

- [访客用户](../quick-checkout/checkout-bolt.md) 已注册或新增 [!DNL Bolt] 帐户。
- 现有 [Adobe Commerce用户](../quick-checkout/checkout-adobe-commerce.md) 无论是否拥有已注册的 [!DNL Bolt] 帐户。

## 获取帮助

请通过以下方式联系Adobe Commerce支持： [Adobe Commerce帮助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) 以寻求任何帮助。
