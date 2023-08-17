---
title: “载入 [!DNL Quick Checkout] for Adobe Commerce扩展”
description: “了解如何 [!DNL Quick Checkout] 可能会对您的Adobe Commerce实例以及如何成功载入和设置扩展有所帮助。”
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# [!DNL Quick Checkout] 入门

要开始使用 [!DNL Quick Checkout] 对于Adobe Commerce扩展，您必须完成一些载入步骤，以将您的实例与我们的签出功能连接起来。

![快速签出](assets/overview-admin-panel.png)

1. [获取扩展](#get-extension).
1. [使用以下方式创建生产或沙盒商家帐户 [!DNL Bolt]](#create-account-with-bolt). 提供验证您的身份所需的所有信息。
1. [提供唯一 [!DNL API Key] 和 [!DNL Publishable Key]](#obtain-api-credentials) 生成于 [!DNL Bolt].
1. [在中设置付款提供商 [!DNL Bolt] 帐户](#configure-payment-providers).
1. [将“启用”下拉列表设置为“是”](#enable-extension) 以激活该扩展。
1. [定义您的服务设置](#complete-admin-configuration) 配置 [!DNL Quick Checkout] 扩展。
1. [单击保存配置](#enable-live-quick-checkout) 按钮以启用扩展。
1. 将范围切换到 **主网站** 和 [单击配置回调URL](#check-shopper-valid-account) 按钮。

如果启用了Gainsight，则会触发 **观看导览** 中的按钮 [!DNL Quick Checkout] 管理面板关于 [!DNL Quick Checkout] 对于Adobe Commerce：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** >高级：

   ![快速签出](assets/gainsight-admin.png)

如果未启用Gainsight，请继续执行载入步骤。

请参阅 [[!DNL Quick Checkout] 管理面板](../quick-checkout/admin-panel.md) 主题以了解更多信息。

>[!NOTE]
>
> 如果您未配置 [!DNL Bolt] 帐户无法设置沙盒或生产环境。

## 先决条件

要使用 [!DNL Quick Checkout]，您必须具备以下可用于 [!DNL Bolt]：

- 支持的支付提供商
- 中的商家和生产帐户 [!DNL Bolt]
- API和 [!DNL Publishable key] 生成于 [!DNL Bolt]

请参阅 [先决条件](../quick-checkout/prerequisites.md) 主题以了解更多信息。

请参阅 [API凭据](#obtain-api-credentials) 以了解如何创建或访问 [!DNL API keys] 对于您的实例。

## 获取扩展

请参阅 [安装](../quick-checkout/install.md) 主题，以了解有关获取扩展的详细信息。

## 创建帐户 [!DNL Bolt]

配置之前 [!DNL Quick Checkout] 在Adobe Commerce管理员中，需要创建 [沙盒](https://merchant-sandbox.bolt.com/register?platform=magento2){target="_blank"} and [production](https://merchant.bolt.com/register?platform=magento2){target="_blank"}  中的商家帐户 [!DNL Bolt]. 提供在中创建帐户所需的所有详细信息 [!DNL Bolt].

请参阅 [测试和验证](../quick-checkout/testing.md) 主题以了解更多信息。

## 获取API凭据

要使用 [!DNL Quick Checkout] 您需要 [!DNL Bolt] 唯一键和 [!DNL signing secret]. 获取以下内容 [!DNL API keys] 导航到 **开发人员** > **API** > **键** 在 **螺栓商家仪表板**.

- [!DNL API key]：后端用来与交互的私钥 [!DNL Bolt] API。
- [!DNL Publishable key]：前端用于与进行交互的密钥 [!DNL Bolt] API。
- [!DNL Signing secret]：用于对从收到的请求进行签名验证 [!DNL Bolt].

  ![快速签出](assets/account-credentials.png)

请参阅 [[!DNL Bolt] 环境详细信息](https://help.bolt.com/developers/references/environment-details/#about-keys){target="_blank"} 要从中了解密钥和签名密钥的页面 [!DNL Bolt] 对于 [!DNL Quick Checkout] 扩展。

>[!CAUTION]
>
> 您必须创建 [!DNL API keys] 适用于沙盒环境和生产环境。

## 配置支付提供商

要连接您的支付服务提供商，请按照 [处理器设置](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target="_blank"} 开发人员 [!DNL Bolt] 页面。

## 启用扩展

1. 在 _管理员_ 侧栏，转到 **商店** > _设置_ > **配置**.
1. 在左侧面板中，展开 **销售** 并选择 **结帐**.
1. 在 [!DNL Quick Checkout] 视图，设置 **启用** 到 `Yes`.

![快速签出](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> 仅当出现以下问题时，快速签出字段才可见 **启用** 设置为 `Yes`.

1. 选择要使用的方法（沙盒或生产）。

   - 用于测试和开发的沙盒
   - 使用实时支付处理器处理交易的生产

1. 提供唯一的API并验证凭据后 [!DNL Publishable keys].

![快速签出](assets/quick-checkout-main-view.png)

请参阅 [设置](../quick-checkout/settings-quick-checkout.md) 主题以了解有关配置选项的详细信息 [!DNL Quick Checkout] 适用于Adobe Commerce扩展。

>[!CAUTION]
>
> 您必须提供唯一的API和 [!DNL Publishable] 扩展前的键值，否则客户将看到付款表单，并且无法下订单。

## 完成管理员配置

1. 在 _管理员_ 侧栏，导航到 **商店** > **配置** > **结帐** 以访问常规签出管理配置页面。
1. 在 _服务设置_ 部分，提供启用扩展所需的所有详细信息。
1. 设置 _付款操作_ 到任一选项：

   - `Authorize`：不会在授权时自动捕获事务。
   - `Authorize and Capture`：根据授权自动捕获事务。

有关Adobe Commerce标准签出选项的更多信息，请参阅 [结账](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主题。

## 启用Live Quick Checkout

要启用 [!DNL Quick Checkout] 对于Adobe Commerce扩展：

1. 检查 [!UICONTROL Enable] 下拉列表设置为 **是** 以激活该扩展。
1. 单击 **保存配置**.

## 检查购物者有效帐户

检查购物者是否具有 [!DNL Bolt] 帐户：

1. 将范围切换到 **主网站**.
1. 单击 **配置回调URL** 按钮。 这样可启用 [!DNL Bolt] 以确定购物者是否有帐户。 如果是，则会出现OTP弹出窗口。

   >[!CAUTION]
   >
   > 将范围切换到 **主网站** 确保设置了正确的URL。 每个网站可以有多个域。

请参阅 [站点、存储和查看范围](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target="_blank"} 有关Adobe Commerce中作用域的更多信息，请参阅主题。

## 配置服务设置

![快速签出](assets/service-settings.png)

1. 设置 **启用签出跟踪** 到 `Yes`.

   >[!CAUTION]
   >
   > 禁用此选项将影响报表，因为Adobe Commerce不允许与Bolt共享签出跟踪信息。

1. 选择 **登录后的下一阶段** 选项，用于在客户登录后更改导航流程。 默认情况下，它设置为 **支付** 页面。
1. 定义 [!DNL Quick Checkout] 允许使用 **自动登录** 结账期间。 默认情况下，该功能允许自动登录到 [!DNL Bolt] 网络。

   >[!NOTE]
   >
   > 请参阅 [Bolt的“启用自动登录”文档](https://help.bolt.com/products/embedded/direct-api/auto-login/) 以了解更多信息。

## 获取帮助

载入流程旨在指导您完成设置和启用 [!DNL Express Checkout] 功能。

请通过以下方式联系Adobe Commerce支持人员： [Adobe Commerce帮助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 任何帮助。

请参阅 [测试和验证](../quick-checkout/testing.md) 主题以了解更多信息。
