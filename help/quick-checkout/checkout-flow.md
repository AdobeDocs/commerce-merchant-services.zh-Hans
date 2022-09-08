---
title: “Adobe Commerce中的结帐流程”
description: “概述 [!DNL Quick Checkout] 在Adobe Commerce流动。”
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: d4b58b0ee3da866d460cf18d96ec9dd27b195f7a
workflow-type: tm+mt
source-wordcount: '194'
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

![OTP弹出窗口](assets/pop-up.png)

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

- [来宾用户](../quick-checkout/checkout-bolt.md) 注册或新 [!DNL Bolt] 帐户。
- 现有 [Adobe Commerce用户](../quick-checkout/checkout-adobe-commerce.md) 注册（无） [!DNL Bolt] 帐户。

## 获取帮助

通过与Adobe Commerce支持部门联系 [Adobe Commerce帮助中心](https://support.magento.com/hc/en-us/articles/360000913794-Adobe-Commerce-Help-Center-User-Guide) 来寻求帮助。
