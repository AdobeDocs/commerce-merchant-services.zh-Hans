---
title: “在 [!DNL Quick Checkout] (对于Adobe Commerce扩展)
description: “了解 [!DNL Quick Checkout] 可以为您的Adobe Commerce实例以及如何成功载入和设置扩展。”
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: ac55bf6354c8f5569ad83dc0ac2671b34c98d303
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] 载入

开始使用 [!DNL Quick Checkout] 对于Adobe Commerce扩展，您必须完成一些入门步骤，才能将您的实例与我们的签出功能连接起来。

1. [获取扩展](#get-extension).
1. [使用创建生产或沙盒商户帐户 [!DNL Bolt]](#create-account-with-bolt). 提供验证您的身份所需的所有信息。
1. [提供 [!DNL API Key] 和 [!DNL Publishable Key] 生成于 [!DNL Bolt]](#obtain-api-credentials).
1. [在 [!DNL Bolt] 帐户](#configure-payment-providers).
1. [将“启用”下拉列表设置为“是”](#enable-extension) 激活扩展。
1. [定义服务设置](#complete-admin-configuration) 配置 [!DNL Quick Checkout] 扩展。
1. [单击Save Config按钮](#enable-live-quick-checkout) 启用扩展。

>[!NOTE]
>
> 如果您未配置 [!DNL Bolt] 帐户无法设置沙盒或生产环境。

## 先决条件

为了使用 [!DNL Quick Checkout]，则您必须在 [!DNL Bolt]:

- 支持的支付提供商
- 中的商家和生产帐户 [!DNL Bolt]
- API和 [!DNL Publishable key] 生成于 [!DNL Bolt]

请参阅 [先决条件](../quick-checkout/prerequisites.md) 主题以了解更多信息。

请参阅 [API凭据](#obtain-api-credentials) 了解如何创建或访问 [!DNL API keys] 例如。

## 获取扩展

请参阅 [安装](../quick-checkout/install.md) 有关获取扩展的详细信息的主题。

## 创建帐户 [!DNL Bolt]

在配置 [!DNL Quick Checkout] 在Adobe Commerce管理员中，需要创建 [沙盒](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;}和 [生产](https://merchant.bolt.com/register){target=&quot;_blank&quot;}中的商户帐户 [!DNL Bolt]. 提供在中创建帐户所需的所有详细信息 [!DNL Bolt].

请参阅 [测试和验证](../quick-checkout/testing.md) 主题以了解更多信息。

## 获取API凭据

使用 [!DNL Quick Checkout] 您需要 [!DNL Bolt] 唯一键。 获取以下内容 [!DNL API keys] 导航至 **开发人员** > **API** > **键** 在 **螺栓商户仪表板**.

- [!DNL API key]:后端用于与交互的私钥 [!DNL Bolt] API。
- [!DNL Publishable key]:前端用于与交互的键 [!DNL Bolt] API。

请参阅 [[!DNL Bolt] 环境详细信息](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;}页面，了解有关API和 [!DNL Publishable keys] 对于 [!DNL Quick Checkout] 扩展。

>[!CAUTION]
>
> 您必须创建 [!DNL API keys] 适用于沙盒和生产环境。

## 配置支付提供商

要连接您的支付服务提供商，请按照 [处理器设置](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;}开发人员 [!DNL Bolt] 页面。

## 启用扩展

1. 在 _管理员_ 侧栏，转到 **商店** > _设置_ > **配置**.
1. 在左侧面板中，展开 **销售** 选择 **结帐**.

   ![快速结帐](assets/admin-view.png)

1. 在 [!DNL Quick Checkout] 视图，设置 **启用** to `Yes`.
1. 选择要使用的方法（沙盒或生产）。

   - 用于测试和开发的沙盒
   - 生产以处理与实时支付处理器的交易

1. 提供您的唯一API后验证凭据，并 [!DNL Publishable keys].

>[!CAUTION]
>
> 您必须提供唯一的API和 [!DNL Publishable keys] 在启用扩展之前，否则客户将看到付款表单，并且无法下订单。

## 完整的管理员配置

1. 在 _管理员_ 侧栏，导航到 **商店** > **配置** > **结帐** 访问常规的“结帐管理员配置”页面。
1. 在 _服务设置_ 部分，提供启用扩展所需的所有详细信息。
1. 已设置 _付款活动_ 选项之一：

   - `Authorize`:请勿在授权时自动捕获事务。
   - `Authorize and Capture`:根据授权自动捕获事务。

有关Adobe Commerce标准结账选项的更多信息，请参阅 [结账](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主题。

## 启用实时快速结帐

启用 [!DNL Quick Checkout] 对于Adobe Commerce扩展：

1. 检查 [!UICONTROL Enable] 下拉列表设置为 **是** 激活扩展。
1. 单击 **保存配置**.

## 获取帮助

入门流程旨在指导您完成设置和启用 [!DNL Express Checkout] 功能。 通过您分配的Slack，联系Adobe Commerce工程团队 [Adobe测试版计划渠道](http://adobe-beta-programs.slack.com/) 帮助渠道。

请参阅 [测试和验证](../quick-checkout/testing.md) 主题以了解更多信息。
