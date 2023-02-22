---
title: 旧版支付服务配置
description: 安装后，您可以配置 [!DNL Payment Services] 在存储配置的管理员中。
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 旧版 [!DNL Payment Services] 配置

您可以自定义 [!DNL Payment Services] 使用管理员中的有用配置选项来满足您的需求。

配置 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 在“管理员”中，这些配置仅适用于在 _[!UICONTROL Method]_字段_[!UICONTROL General Configuration]_. 您在配置字段中所做的任何更改都与切换 _[!UICONTROL Method]_选择(selection) — 如果切换方法，则不会重置选择。

## 常规配置

您可以启用 [!DNL Payment Services] ，并在中启用沙盒测试或实时付款 _[!UICONTROL General Configuration]_中。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左侧面板中，展开 **[!UICONTROL Sales]** 选择 **[!UICONTROL Payment Methods]**.

   ![“方法”视图](assets/methods-view.png)

1. 展开 _[!UICONTROL Recommended Solutions]_中。
1. 在 _[!UICONTROL [!DNL Payment Services]]_部分，展开_[!UICONTROL General Configuration]_ 中。
1. 对于 **启用**，将其设置为 `Yes` 启用 [!DNL Payment Services] 你的店。
1. 对于 **方法**，将其设置为 `Sandbox` 如果您仍在测试 [!DNL Payment Services] 或 `Production` 如果您已准备好启用实时付款。

   >[!WARNING]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在您完成沙盒和/或生产的入门后，将自动生成并显示在其受人尊敬的字段中。 请勿删除或更改这些ID。

1. 单击 **[!UICONTROL Save Config]** 以保存更改。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然后单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Enable] | 网站 | 启用或禁用 [!DNL Payment Services] 的URL。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 商店视图 | 为存储设置方法或环境。 选项： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店视图 | 您的沙盒商户ID，在沙盒载入期间自动生成。 请勿更改或更改此ID。 |
| [!UICONTROL Production Merchant ID] | 商店视图 | 您的生产商户ID，在沙盒载入期间自动生成。 请勿更改或更改此ID。 |

## [!UICONTROL Credit Card Fields]

的 [!UICONTROL Credit Card Fields] 付款选项为信用卡或借记卡付款方法提供简单且安全的结账。

请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

### 配置信用卡字段

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左侧面板中，展开 **[!UICONTROL Sales]** 选择 **[!UICONTROL Payment Methods]**.
1. 展开 _[!UICONTROL Recommended Solutions]_中。
1. 在 _[!UICONTROL Payment Services]_部分，展开_[!UICONTROL Credit Card Fields]_ 中。
1. 对于 **[!UICONTROL Title]**，输入文本（如果需要）以更改付款方法的名称，如在结帐期间所示。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，选择 **[!UICONTROL Authorize]** 或 **授权和捕获**.
1. 对于 **[!UICONTROL Show on checkout page]**，选择 `Yes` 启用结帐页面上的信用卡字段。
1. 对于 **[!UICONTROL Vault Enabled]**，选择 `Yes` 启用信用卡保险存储以进行结帐。
1. 对于 **[!UICONTROL Vault Enabled in Admin]**，选择 `Yes` 使商家能够使用其拱形信用卡为客户创建订单。
1. 对于 **[!UICONTROL Debug Mode]**，选择 `Yes` 启用调试模式(或 `No` 禁用)。
1. 启用 **[!UICONTROL 3DS Secure authentication]** (`Off` 默认)选择 `Always` 或 `When required`.
1. 单击 **[!UICONTROL Save Config]** 以保存更改。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然后单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间，在“付款方法”视图中添加要显示为此付款选项标题的文本。 选项： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 网站 | 的 [付款操作](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 指定付款方式。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | 网站 | 在结帐页面上启用或禁用信用卡字段。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 商店视图 | 启用或禁用 [信用卡保险](vaulting.md). 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | 商店视图 | 启用或禁用 [商家完成管理员中客户的订单](vaulting.md) 使用拱形支付方法。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | 网站 | 启用或禁用 [3DS安全身份验证](security.md#3ds). 选项： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

的 [!DNL PayPal Smart Buttons] 付款选项可为您的客户提供简单、快速且安全的结账流程。

请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

### 配置 [!DNL PayPal Smart Buttons]

您可以在管理员中启用和配置PayPal智能按钮付款选项：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左侧面板中，展开 **[!UICONTROL Sales]** 选择 **[!UICONTROL Payment Methods]**.
1. 展开 _[!UICONTROL Recommended Solutions]_中。
1. 在 _[!UICONTROL Payment Services]_部分，展开_[!UICONTROL PayPal Smart Buttons]_ 中。
1. 要更改结帐期间显示的付款方法名称，请编辑 _[!UICONTROL Title]_字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，选择 **[!UICONTROL Authorize]** 或 **[!UICONTROL Authorize and Capture]**.
1. 禁用 [稍后付费消息传送](payments-options.md#pay-later-button) （如果需要），选择 `No` 表示 **[!UICONTROL Display Pay Later Message]**.
1. 要启用调试模式，请选择 `Yes` 对于 **[!UICONTROL Debug Mode]** (`No` 禁用)。
1. 要保存更改，请单击 **[!UICONTROL Save Config]** .
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**，然后单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间，在“付款方法”视图中添加要显示为此付款选项标题的文本。 选项：文本字段 |
| [!UICONTROL Payment Action] | 网站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 网站 | 在购物车、产品页面、迷你购物车和结帐流程期间，启用或禁用“稍后付费”消息传送。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | 商店视图 | 在显示付款按钮的位置启用或禁用维恩莫付款选项。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | 商店视图 | 在显示付款按钮的位置启用或禁用Apple付款选项。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | 商店视图 | 在显示付款按钮的情况下，启用或禁用以后付款选项外观。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在产品详细信息页面上。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在mini-cart预览中。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在购物车页面上。 选项： [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] 样式选项

| 字段 | 范围 | 描述 |
|--- |--- |--- |
| [!UICONTROL Layout] | 存储视图 | 为Paypal智能按钮定义布局样式。 选项： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | 存储视图 | 定义Paypal智能按钮的颜色。 选项： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 存储视图 | 定义Paypal智能按钮的形状。 选项： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | 存储视图 | 定义PayPal智能按钮是否使用默认高度。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 存储视图 | 定义PayPal智能按钮的高度。 默认值：无 |
| [!UICONTROL Label] | 存储视图 | 定义显示在PayPal智能按钮中的标签。 选项： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | 存储视图 | 启用标记。 选项： [!UICONTROL Yes] / [!UICONTROL No] |

## 刷新缓存

如果更改配置， [手动刷新缓存](/help/payment-services/settings.md#flush-the-cache) 以便您的商店显示最新的配置设置。

