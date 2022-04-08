---
title: 测试 [!DNL Express Checkout] 适用于Adobe Commerce扩展
description: 测试和验证可确保 [!DNL Express Checkout] 扩展可按预期工作。
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 测试 [!DNL Express Checkout] 适用于Adobe Commerce扩展

>[!IMPORTANT]
>
> 该功能仅面向提前采纳者计划(EAP)用户，并且尚未可供所有客户访问。 目前仅限于美国客户。 如需帮助和问题，请联系Adobe Commerce支持。

在您公开 [!DNL Express Checkout] 对于面向购物者的Adobe Commerce扩展，建议在沙盒环境和生产环境中进行测试。 测试和验证有助于确保 [!DNL Express Checkout] 可按预期工作，为您的商店和客户提供无缝的结账体验。

在配置 [!DNL Express Checkout] 在Adobe Commerce管理员中，需要创建 [生产](https://merchant.bolt.com/register){target=&quot;_blank&quot;}和 [沙盒](https://merchant-sandbox.bolt.com/register)Bolt中的{target=&quot;_blank&quot;}商户帐户。

## 在沙盒中测试

测试 [!DNL Express Checkout] 在沙盒环境中，验证步骤非常重要，即使它是仅与Bolt沙盒帐户连接的模拟环境，而不是与真实银行或商户连接。

### 使用沙盒帐户

在测试和验证沙盒时，您必须使用假信用卡号和 [沙盒](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}中的商户帐户 [!DNL Bolt]，以便您不会对现有信用卡帐户创建实际费用。

## 在生产中测试

>[!NOTE]
>
> 强烈建议您测试 [!DNL Express Checkout] 在生产环境中，使用真实信用卡和银行，然后再向购物者公开延期。 尽管在沙盒中测试很重要，但在生产中测试是确保其按预期工作的最蠢方法。

建议在生产环境中通过以下两种方式之一进行测试：

- 选择您知道购物者不会下订单的时间。
- 使用网店，该商店暂时无法访问购物者，但您可以访问该网店进行测试。

使用真实的信用卡和Bolt生产帐户完成生产测试，测试结账的整个生命周期。 在测试期间完成整个结账流程后，您可以清楚地了解当现场购物者使用该功能时，功能的工作方式。

您还应验证在银行对帐单中显示的有关您在生产测试中使用的付款方法的信息是否正确且符合预期（包括业务说明）。

## 如何测试 [!DNL Express Checkout] 扩展

按照以下步骤从您的商店中成功完成结帐：

1. 转到店面，并将所需物品放入购物车。
1. 继续结帐。
1. 输入与 [!DNL Bolt] 帐户。
1. 输入发送到帐户电子邮件地址的一次性密码(OTP)。
1. 选择环境功能板：

   - 沙盒
   - 生产

1. 下单。

下订单后，您可以在 _订单网格_ 视图：

1. 导航到 _销售_ > _订单数_.
1. 请参阅所有已下单的列表。

请参阅 [订购](https://docs.magento.com/user-guide/sales/orders.html) 主题，以了解有关 _订单网格_ 中。
