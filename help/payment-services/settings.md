---
title: 付款服务设置
description: 安装后，您可以配置 [!DNL Payment Services] 在家里。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: b30c15ab808be4526424a4a3be19e3d0aedcc662
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 设置

您可以自定义 [!DNL Payment Services] 中的有用设置，以满足您的需求 [!DNL Payment Services] 回家。

配置 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 单击 **[!UICONTROL Settings]**. 这些配置选项仅适用于在 _[!UICONTROL Payment mode]_字段。

请参阅 [[!UICONTROL General] 设置部分](#general-settings) 以了解更多信息。

>[!IMPORTANT]
>
> 有关多存储或旧版配置，请参阅 [在管理员中配置](configure-admin.md) 主题。

## 启用支付服务

您可以启用 [!DNL Payment Services] ，并在 [!UICONTROL General] 中。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![主页视图](assets/payment-services-menu-small.png)

1. 单击 **[!UICONTROL Settings]**. 请参阅 [简介 [!DNL Payment Services] 主页](payments-home.md) 以了解更多信息。

   的 _[!UICONTROL General]_部分包括用于启用的设置 [!DNL Payment Services] 付款方式。

1. 启用 [!DNL Payment Services] 作为您商店的付款方式，切换(**[!UICONTROL Enable Payment Services as payment method]**) `Yes`.

1. 如果您仍在测试 [!DNL Payment Services] 为您的商店设置 **付款模式** to `Sandbox`. 如果您已准备好启用实时付款，请将其设置为 `Production`.

   >[!WARNING]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在沙盒和/或生产入门后，将自动生成并显示在其受人尊敬的字段中。 请勿删除或更改这些ID。

1. 要更改付款功能和店面显示的默认设置，请根据需要设置附加选项：

   - [信用卡字段](#credit-card-fields)
   - [PayPal智能按钮](#paypal-smart-buttons)
   - [按钮样式](#button-style)

1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### 信用卡字段

的 _[!UICONTROL Credit Card Fields]_设置为信用卡或借记卡付款方法提供简单且安全的结账选项。

请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

1. 要更改结帐期间显示的付款方法名称，请编辑 **[!UICONTROL Checkout title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 要启用调试模式，请将 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### PayPal智能按钮

的 [!DNL PayPal Smart Buttons] 付款选项可为您的客户提供简单、快速且安全的结账流程。 请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

您可以启用和配置PayPal智能按钮付款选项：

1. 要更改结帐期间显示的付款方法名称，请编辑 **[!UICONTROL Checkout Title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 使用切换选择器启用或禁用 [!DNL PayPal smart button] 显示功能：
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. 要更改 [稍后付费消息传送](payments-options.md#pay-later-button)，切换 **[!UICONTROL Display Pay Later message]** 选项。
1. 要启用调试模式，请将 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

#### 按钮样式

您还可以配置 _[!UICONTROL Button style]_PayPal智能按钮的选项：

1. 要更改 **[!UICONTROL Layout]**，选择 `Vertical` 或 `Horizontal`.

   >[!NOTE]
   >
   > 如果按钮样式配置为 `Horizontal` 而您的商店配置为显示多个PayPal智能按钮，则您可能只会在产品页面、结帐页面和迷你购物车上显示两个按钮，在购物车中显示一个按钮。

1. 要在水平布局中启用标记线，请切换 **[!UICONTROL Show tagline]** 选择器。
1. 修改 **[!UICONTROL Color]**，请选择所需的颜色选项。
1. 修改 **[!UICONTROL Shape]**，选择 `Pill` 或 `Rect`.
1. 要启用按钮高度选择器，请切换 **[!UICONTROL Responsive button height]** 选择器。
1. 修改 **[!UICONTROL Label]**，请选择所需的标签选项。
1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

您可以配置 [!DNL PayPal Smart Buttons] 样式 [!DNL Payment Services Home]. 请参阅 [PayPal&#39;s Buttons风格指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 以了解更多信息。
