---
title: 在功能板中配置
description: 安装后，您可以配置 [!DNL Payment Services] 中。
role: Admin, User
level: Intermediate
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# 在功能板中配置

您可以自定义 [!DNL Payment Services] 功能板中的有用配置选项，以满足您的需求。

单击 [!UICONTROL Settings] 在功能板中，您可以快速配置 [!DNL Payment Services] Adobe Commerce和Magento Open Source。 这些配置选项仅适用于在 [!UICONTROL Payment mode] 字段。

请参阅 [[!UICONTROL General] 设置部分](#general-settings) 以了解更多信息。

>[!IMPORTANT]
>
> 有关多存储或旧版配置，请参阅 [在管理员中配置](configure-admin.md) 主题。

## 配置支付服务

您可以启用 [!DNL Payment Services] ，并在中启用沙盒测试或实时付款 [!UICONTROL General] 设置部分。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![功能板视图](assets/payment-services-menu-small.png)

1. 在功能板上，单击 **[!UICONTROL Settings]** 的双曲余切值。

   的 _[!UICONTROL General]_部分包括用于设置 [!DNL Payment Services] 付款方式。

1. 对于顶部的切换选项(**[!UICONTROL Enable Payment Services as payment method]**)，将其设置为 `Yes` 启用 [!DNL Payment Services] 的URL。

1. 对于 **付款模式**，将其设置为 `Sandbox` 如果您仍在测试 [!DNL Payment Services] 或 `Production` 如果您已准备好启用实时付款。

   >[!WARNING]
   >
   >您的 [!UICONTROL Sandbox Merchant ID] 和 [!UICONTROL Production Merchant ID] 在您完成沙盒和/或生产的入门后，将自动生成并显示在其受人尊敬的字段中。 请勿删除或更改这些ID。

1. 要更改付款功能和店面显示的默认设置，请根据需要设置附加选项：

   - [信用卡字段](#credit-card-fields)
   - [PayPal智能按钮](#paypal-smart-buttons)
   - [按钮样式](#button-style)

1. 要保存更改，请单击 **[!UICONTROL Save]** 的双曲余切值。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### 信用卡字段

的 [!UICONTROL Credit Card Fields] 付款选项为信用卡或借记卡付款方法提供简单且安全的结账。

请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

1. 对于 **[!UICONTROL Checkout title]**，输入文本（如果需要）以更改结帐期间显示的付款方法名称。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，设置 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 对于 **[!UICONTROL Debug Mode]**，切换选择器以启用调试模式。
1. 要保存更改，请单击 **[!UICONTROL Save]** 的双曲余切值。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### PayPal智能按钮

的 [!DNL PayPal Smart Buttons] 付款选项可为您的客户提供简单、快速且安全的结账流程。 请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

您可以在仪表板中启用PayPal智能按钮付款选项：

1. 要更改结帐期间显示的付款方法名称，请编辑 **[!UICONTROL Checkout Title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，设置 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 使用切换选择器启用或禁用 [!DNL PayPal smart button] 显示功能：
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** 启用在结帐期间显示按钮的选项。

1. 要更改 [稍后付费消息传送](payments-options.md#pay-later-button) （如果需要）切换 **[!UICONTROL Display Pay Later message]** 选项。
1. 要启用调试模式，请单击 **[!UICONTROL Debug Mode]**,
1. 要保存更改，请单击 **[!UICONTROL Save]** 的双曲余切值。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### 按钮样式

您还可以配置 _[!UICONTROL Button style]_功能板中PayPal智能按钮的选项：

1. 要更改 **[!UICONTROL Layout]**，选择 `Vertical` 或 `Horizontal`.
1. 要在水平布局中启用标记线，请单击 **[!UICONTROL Show tagline]**.
1. 修改 **[!UICONTROL Color]**，请选择所需的颜色选项。
1. 要更改 **[!UICONTROL Shape]**，选择 `Pill` 或 `Rect`.
1. 要启用按钮高度选择器，请单击 **[!UICONTROL Responsive button height]**.
1. 修改 **[!UICONTROL Label]**，请选择所需的标签选项。
1. 要保存更改，请单击 **[!UICONTROL Save]** 的双曲余切值。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

您可以配置 [!DNL PayPal Smart Buttons] 样式。 请参阅 [配置 [!DNL PayPal Smart Buttons style]](configure-admin.md#configure-paypal-smart-button-styling) 以了解更多信息。