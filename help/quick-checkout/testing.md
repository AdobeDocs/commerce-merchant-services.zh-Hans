---
title: “测试 [!DNL Quick Checkout] (对于Adobe Commerce扩展)
description: “测试和验证可确保 [!DNL Quick Checkout] 扩展可按预期工作。”
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 测试 [!DNL Quick Checkout] 扩展

在您公开 [!DNL Quick Checkout] 对于面向购物者的Adobe Commerce扩展，建议在沙盒环境和生产环境中进行测试。 测试和验证有助于确保 [!DNL Quick Checkout] 可按预期工作，为您的商店和客户提供无缝的结账体验。

在配置 [!DNL Quick Checkout] 在Adobe Commerce管理员中，需要创建  [生产](https://merchant.bolt.com/register){target=&quot;_blank&quot;}和 [沙盒](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}中的商户帐户 [!DNL Bolt].

## 在沙盒中测试

测试 [!DNL Quick Checkout] 沙盒环境中的验证步骤非常重要，即使它是仅与连接的模拟环境 [!DNL Bolt] 沙盒帐户，而不是真正的银行或商户。

### 使用沙盒帐户

在测试和验证沙盒时，您必须使用假信用卡号和 [沙盒](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}中的商户帐户 [!DNL Bolt]，以便您不会对现有信用卡帐户创建实际费用。

## 在生产中测试

>[!NOTE]
>
> 强烈建议您测试 [!DNL Quick Checkout] 在生产环境中，使用真实信用卡和银行，然后再向购物者公开延期。 尽管在沙盒中测试很重要，但在生产中测试是确保其按预期工作的最蠢方法。

使用以下两种推荐方式之一测试生产环境：

- 选择您知道购物者不会下订单的时间。
- 使用网店，该商店暂时无法访问购物者，但您可以访问该网店进行测试。

使用真实信用卡完成您的生产测试，并 [!DNL Bolt] 生产帐户，测试结账的整个生命周期。 在测试期间完成整个结账流程后，您可以清楚地了解实时购物者使用功能时的工作方式。

您还应验证在银行对帐单中显示的有关您在生产测试中使用的付款方法的信息是否正确且符合预期（包括业务说明）。

## 如何测试 [!DNL Quick Checkout] 扩展

从您的商店中成功完成结帐：

1. 转到店面，并将所需物品放入购物车。
1. 继续结帐。
1. 输入与 [!DNL Bolt] 帐户。
1. 输入发送到帐户电子邮件地址的一次性密码(OTP)。
1. 选择环境功能板：

   - 沙盒
   - 生产

1. 下订单。

下订单后，您可以在 _订单网格_ 视图：

1. 导航到 _销售_ > _订单数_.
1. 请参阅所有已下单的列表。

请参阅 [订单数](https://docs.magento.com/user-guide/sales/orders.html) 主题，以了解有关 _订单网格_ 中。
