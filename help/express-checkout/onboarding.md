---
title: 载上 [!DNL Express Checkout] 适用于Adobe Commerce扩展
description: 了解 [!DNL Express Checkout] 可能会对您的Adobe Commerce实例以及如何成功载入和设置扩展有好处。
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# [!DNL Express Checkout] 载入

>[!IMPORTANT]
>
> 该功能仅面向提前采纳者计划(EAP)用户，并且尚未可供所有客户访问。 目前仅限于美国客户。 如需帮助和问题，请联系Adobe Commerce支持。

开始使用 [!DNL Express Checkout] 对于Adobe Commerce扩展，您必须完成一些入门步骤，才能将您的实例与我们的签出功能连接起来。

1. [获取扩展](#get-extension).
1. [使用创建生产或沙盒商户帐户 [!DNL Bolt]](#create-account-with-bolt). 提供验证您的身份所需的所有信息。
1. [提供在 [!DNL Bolt]](#obtain-api-credentials).
1. [在 [!DNL Bolt] 帐户](#configure-payment-providers).
1. [将“启用”下拉列表设置为“是”](#enable-extension) 激活扩展。
1. [定义服务设置](#complete-admin-configuration) 配置 [!DNL Express Checkout] 扩展。
1. [单击Save Config按钮](#enable-live-express-checkout) 启用扩展。

>[!NOTE]
>
> 如果您未配置 [!DNL Bolt] 帐户（上述步骤2）您无法设置沙盒或生产环境。

## 先决条件

为了使用 [!DNL Express Checkout]，则您必须在 [!DNL Bolt]:

- 支持的支付提供商
- 中的商家和生产帐户 [!DNL Bolt]
- 在中生成的API和可发布密钥 [!DNL Bolt]

请参阅 [先决条件](../express-checkout/prerequisites.md) 主题以了解更多信息。

请参阅 [API凭据](#obtain-api-credentials) 了解如何为实例创建或访问API密钥。

## 获取扩展

请参阅 [安装](../express-checkout/install.md) 有关获取扩展的详细信息的主题。

## 使用Bolt创建帐户

在配置 [!DNL Express Checkout] 在Adobe Commerce管理员中，需要创建 [沙盒](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}和 [生产](https://merchant.bolt.com/register){target=&quot;_blank&quot;}中的商户帐户 [!DNL Bolt]. 提供在中创建帐户所需的所有详细信息 [!DNL Bolt].

请参阅 [测试和验证](../express-checkout/testing.md) 主题以了解更多信息。

## 获取API凭据

使用 [!DNL Express Checkout] 您需要 [!DNL Bolt] 唯一键。 通过导航到 **开发人员** > **API** > **键** 在 **螺栓商户仪表板**.

- API密钥：后端用于与交互的私钥 [!DNL Bolt] API。
- 可发布键：前端用于与交互的键 [!DNL Bolt] API。

请参阅 [[!DNL Bolt] 环境详细信息](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;}页，了解 [!DNL Express Checkout] 扩展。

>[!CAUTION]
>
> 您必须为沙盒和生产环境创建API密钥。

## 配置支付提供商

要连接您的支付服务提供商，请按照 [处理器设置](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;}开发人员 [!DNL Bolt] 页面。

## 启用扩展

1. 在 _管理员_ 侧栏，导航到 **商店** > **配置** > **结帐** 以访问“结帐管理员”配置页面。

   ![快速结账](assets/admin-view.png)

1. 在 [!DNL Express Checkout] 视图，设置 **启用** to `Yes`.
1. 选择要使用的方法（沙盒或生产）。

   - 用于测试和开发的沙盒
   - 生产以处理与实时支付处理器的交易

1. 在提供您的唯一API和可发布密钥后验证凭据。

>[!CAUTION]
>
> 在启用扩展之前，您必须提供唯一的API和可发布密钥，否则客户将看到付款表单，并且无法下订单。

## 完整的管理员配置

1. 在 _管理员_ 侧栏，导航到 **商店** > **配置** > **结帐** 访问常规的“结帐管理员配置”页面。
1. 在 _服务设置_ 部分，提供启用扩展所需的所有详细信息。
1. 已设置 _付款活动_ 为：

   - 授权：请勿在授权时自动捕获事务。
   - 授权和捕获：根据授权自动捕获事务。

有关Adobe Commerce标准结账选项的更多信息，请参阅 [结账](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主题。

## 启用Live Express结账

启用 [!DNL Express Checkout] 对于Adobe Commerce扩展：

1. 单击 **保存配置**.

## 获取帮助

入门流程旨在指导您完成设置和启用所有 [!DNL Express Checkout] 功能。 请联系Adobe Commerce支持部门以获取任何帮助。

请参阅 [测试和验证](../express-checkout/testing.md) 主题以了解更多信息。
