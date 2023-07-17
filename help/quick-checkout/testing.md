---
title: “测试 [!DNL Quick Checkout] for Adobe Commerce扩展”
description: “测试和验证可确保 [!DNL Quick Checkout] 扩展按预期工作。”
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 测试 [!DNL Quick Checkout] 扩展

在您公开 [!DNL Quick Checkout] 对于面向购物者的Adobe Commerce扩展，建议在沙盒环境和生产环境中进行测试。 测试和验证有助于确保 [!DNL Quick Checkout] 可按预期工作，并为您的商店和客户提供无缝的结账体验。

配置之前 [!DNL Quick Checkout] 在Adobe Commerce管理员中，需要创建  [生产](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帐户 [!DNL Bolt].

## 在沙盒中测试

测试 [!DNL Quick Checkout] 在沙盒环境中，是一个非常重要的验证步骤，即使它是仅连接到 [!DNL Bolt] 沙盒账户，而不是给真正的银行或商家。

### 使用沙盒帐户

在测试和验证沙盒时，您必须使用假信用卡号码和 [沙盒](https://merchant-sandbox.bolt.com/register){target="_blank"} 中的商家帐户 [!DNL Bolt]，这样就不会对现有信用卡帐户产生实际费用。

## 在生产环境中测试

>[!NOTE]
>
> 强烈建议您测试 [!DNL Quick Checkout] 在真实信用卡和银行的生产环境中，向购物者展示这一扩展。 虽然在沙盒中测试很重要，但在生产环境中测试是确保沙盒按预期工作的最万无一失的方法。

使用以下两种推荐方法之一测试您的生产环境：

- 选择您知道购物者不会下订单的时间。
- 使用购物者暂时无法访问，但可供您进行测试的网络商店。

用真正的信用卡和信用卡，完成您的生产测试 [!DNL Bolt] 生产帐户，测试结账的整个生命周期。 当您在测试期间完成整个结账流程时，它将让您清楚地了解当现场购物者使用您的功能时它是如何工作的。

您还应该验证银行对帐单上针对您在生产测试中使用的支付方式显示的信息是否正确和符合预期（包括您的业务描述）。

## 如何测试 [!DNL Quick Checkout] 扩展

从您的商店成功结帐：

1. 转到店面并将所需商品放入购物车中。
1. 继续结帐。
1. 输入与关联的电子邮件地址 [!DNL Bolt] 帐户。
1. 输入发送到帐户电子邮件地址的一次性密码(OTP)。
1. 选择环境功能板：

   - 沙盒
   - 生产

1. 下订单。

下订单后，您可以在以下位置查看订单的详细信息： _订单网格_ 视图：

1. 导航到 _销售_ > _订单_.
1. 查看所有已下订单的列表。

请参阅 [订单](https://docs.magento.com/user-guide/sales/orders.html) 主题以了解有关 _订单网格_ 视图。
