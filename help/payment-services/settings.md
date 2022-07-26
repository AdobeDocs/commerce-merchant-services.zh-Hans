---
title: 付款服务设置
description: 安装后，您可以配置 [!DNL Payment Services] 在家里。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 89fa175b70a2b4b37d5999dedc56a7e41ae28b7d
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# 设置

您可以自定义 [!DNL Payment Services] 中的有用设置，以满足您的需求 [!DNL Payment Services] 回家。

配置 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 单击 **[!UICONTROL Settings]**. 这些配置选项仅适用于在 _[!UICONTROL Payment mode]_字段_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> 有关多存储或旧版配置，请参阅 [在管理员中配置](configure-admin.md) 主题。

## 启用支付服务

您可以启用 [!DNL Payment Services] ，并在 [!UICONTROL General] 中。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![主页视图](assets/payment-services-menu-small.png)

1. 单击 **[!UICONTROL Settings]**. 请参阅 [简介 [!DNL Payment Services] 主页](payments-home.md) 以了解更多信息。

   的 _[!UICONTROL General]_部分包括用于启用的设置 [!DNL Payment Services] 付款方式。

1. 启用 [!DNL Payment Services] 作为您店的付款方式， _[!UICONTROL General]_部分，切换(**[!UICONTROL Enable Payment Services as payment method]**) `Yes`.

1. 如果您仍在测试 [!DNL Payment Services] 为您的商店设置 **付款模式** to `Sandbox`. 如果您已准备好启用实时付款，请将其设置为 `Production`.

   >[!NOTE]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 在沙盒和/或生产入门后，将自动生成并显示在其受人尊敬的字段中。

1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

您现在可以继续更改 [付款选项](#configure-payment-options) 功能和店面显示。

### 常规配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Enable] | 网站 | 启用或禁用 [!DNL Payment Services] 的URL。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 商店视图 | 为存储设置方法或环境。 选项： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店视图 | 您的沙盒商户ID，在沙盒载入期间自动生成。 |
| [!UICONTROL Production Merchant ID] | 商店视图 | 您的生产商户ID，在沙盒载入期间自动生成。 |

## 配置付款选项

现在，您已为网站启用“付款服务”，接下来可以更改付款功能和店面显示的默认设置。

### 信用卡字段

的 _[!UICONTROL Credit Card Fields]_设置为信用卡或借记卡付款方法提供简单且安全的结账选项。

请参阅 [付款选项](payments-options.md#credit-card-fields) 以了解更多信息。

1. 在 **[!UICONTROL Scope]** 下拉菜单中，您希望为其启用付款方法。
1. 要更改结帐期间显示的付款方法名称，请编辑 **[!UICONTROL Checkout title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 要启用调试模式，请将 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间，在“付款方法”视图中添加要显示为此付款选项标题的文本。 选项： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 网站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Yes] / [!UICONTROL No] |

### 付款按钮

的 [!DNL PayPal Smart Buttons] 付款选项可为您的客户提供简单、快速且安全的结账流程。 请参阅 [付款选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

您可以启用和配置PayPal智能按钮付款选项：

1. 在 **[!UICONTROL Scope]** 下拉菜单中，您希望为其启用付款方法。
1. 要更改结帐期间显示的付款方法名称，请编辑 **[!UICONTROL Checkout Title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** to `Authorize` 或 `Authorize and Capture`.
1. 使用切换选择器启用或禁用 [!DNL PayPal smart button] 显示功能：
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple付款默认为沙盒模式启用，但您也 [必须拥有Apple开发人员帐户](test-validate.md#test-in-sandbox-environment) （包括假信用卡和账单信息）以进行测试。 在完成任何以下操作后，当您准备好在生产模式下使用Apple Pay时 [测试和验证](test-validate.md)，请联系销售人员为您的实时商店启用此功能。

1. 要启用调试模式，请将 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试在不保存更改的情况下离开此视图，则会显示一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 单击 **[!UICONTROL Flush Cache]** 刷新所有无效的缓存。

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间，在“付款方法”视图中添加要显示为此付款选项标题的文本。 选项：文本字段 |
| [!UICONTROL Payment Action] | 网站 | 的 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在产品详细信息页面上。 选项： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在迷你购物车预览中。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在购物车页面上。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 商店视图 | 在显示付款按钮的情况下，启用或禁用以后付款选项外观。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 网站 | 在购物车、产品页面、迷你购物车和结帐流程期间，启用或禁用“稍后付费”消息传送。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 商店视图 | 在显示付款按钮的位置启用或禁用维恩莫付款选项。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 商店视图 | 在显示付款按钮的位置启用或禁用Apple付款选项。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Yes] / [!UICONTROL No] |

### 按钮样式

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

您可以配置 [!DNL PayPal Smart Buttons] 样式 [的旧版配置中](configure-admin.md#configure-paypal-smart-buttons) 或此处 [!DNL Payment Services Home]. 请参阅 [PayPal&#39;s Buttons风格指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 以了解有关选项的更多信息。

#### 配置选项

| 字段 | 范围 | 描述 |
|--- |--- |--- |
| [!UICONTROL Layout] | 存储视图 | 为付款按钮定义布局样式。 选项： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 存储视图 | 启用/禁用标记。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 存储视图 | 定义付款按钮的颜色。 选项： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 存储视图 | 定义付款按钮的形状。 选项： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 存储视图 | 定义付款按钮是否使用默认高度。 选项： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 存储视图 | 定义付款按钮的高度。 默认值：无 |
| [!UICONTROL Label] | 存储视图 | 定义在付款按钮中显示的标签。 选项： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
