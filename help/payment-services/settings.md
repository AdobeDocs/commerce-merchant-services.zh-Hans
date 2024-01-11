---
title: 付款服务设置
description: 安装后，您可以配置 [!DNL Payment Services] 在家里。
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration
source-git-commit: a7ad4130745957d596cba38892d77107e977e2e7
workflow-type: tm+mt
source-wordcount: '2364'
ht-degree: 0%

---

# 设置

您可以自定义 [!DNL Payment Services] 有用的设置，满足您的需求 [!DNL Payment Services] 家。

配置 [!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 单击 **[!UICONTROL Settings]**. 这些配置选项仅适用于在中设置的环境。 _[!UICONTROL Payment mode]_字段[_&#x200B;常规&#x200B;_配置选项](#configure-general-settings).

有关多存储或旧版配置，请参阅 [在Admin中配置](configure-admin.md).

## 配置常规设置

此 [!UICONTROL General] 通过设置，您可以启用或禁用“付款服务”作为付款方法，并向客户交易添加信息，以使用自定义信息标记或加盖网站或商店视图的前缀。

### 启用付款服务

您可以启用 [!DNL Payment Services] 并启用沙盒测试或实时支付。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![主视图](assets/payment-services-menu-small.png){width="400" zoomable="yes"}

1. 单击 **[!UICONTROL Settings]**. 请参阅 [简介 [!DNL Payment Services] 主页](payments-home.md) 以了解更多信息。

   此 _[!UICONTROL General]_部分包含用于启用的设置 [!DNL Payment Services] 作为付款方式。

1. 要启用 [!DNL Payment Services] 作为您商店的付款方式，在 _[!UICONTROL General]_部分，切换&#x200B;**[!UICONTROL Enable Payment Services as payment method]**到 `Yes`.

1. 如果您仍在测试 [!DNL Payment Services] 对于您的商店，设置 **付款方式** 到 `Sandbox`. 如果您已准备好启用实时支付，请将其设置为 `Production`.

   >[!NOTE]
   >
   >您的 _[!UICONTROL Sandbox Merchant ID]_和_[!UICONTROL Production Merchant ID]_ 当您完成沙盒和/或生产载入时，会自动生成并出现在他们的相应字段中。

1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 并单击 **[!UICONTROL Flush Cache]** 以刷新所有无效缓存。

您现在可以继续更改的默认设置 [付款选项](#configure-payment-options) 功能和店面显示器。

### 添加软描述符

您可以添加 [!UICONTROL Soft Descriptor] 至您的网站或单个商店视图配置。 客户交易银行对帐单上显示软描述符。 例如，如果您有多个商店/品牌/目录，则可以通过将自定义文本添加到 [!UICONTROL Soft Descriptor] 字段。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Settings]**. 请参阅 [简介 [!DNL Payment Services] 主页](payments-home.md) 以了解更多信息。
1. 选择网站或商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其创建软描述符。 对于初始设置，请将其保留为 **[!UICONTROL Default]** 以设置默认值。
1. 在文本字段中添加自定义文本（最多22个字符），替换 `Custom descriptor`.
1. 单击 **[!UICONTROL Save]**.
1. 要为网站或商店视图创建除已配置默认描述符之外的软描述符，请执行以下操作：
   1. 选择网站或商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其创建软描述符。
   1. 切换 _关_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，具体取决于您选择的范围)。
   1. 在文本字段中添加自定义文本。
   1. 单击 **[!UICONTROL Save]**.
1. 要为网站或商店启用以查看默认软描述符，请执行以下操作 _或_ 用于父网站的软描述符：
   1. 选择网站或商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其启用现有的软描述符。
   1. 切换 _日期_ **[!UICONTROL Use website]** (或 **[!UICONTROL Use default]**，具体取决于您选择的范围)。
   1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Enable] | 网站 | 启用或禁用 [!DNL Payment Services] 用于您的网站。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | 商店视图 | 为存储设置方法或环境。 选项： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 商店视图 | 您的沙盒商家ID，在沙盒载入期间自动生成。 |
| [!UICONTROL Production Merchant ID] | 商店视图 | 您的生产商家ID，在沙盒载入期间自动生成。 |
| [!UICONTROL Soft Descriptor] | 网站或商店视图 | 向您的网站和商店视图添加软描述符，以将信息添加到描述品牌、商店或产品线的客户交易。 此 [!UICONTROL Use website] 切换可应用在网站级别添加的任何软描述符。 此 [!UICONTROL Use default] 切换可应用添加为默认设置的任何软描述符。 |

## 配置付款选项

现在您已启用 [!UICONTROL Payment Services] 对于您的网站，您可以更改付款功能和店面显示的默认设置。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Settings]**. 请参阅 [简介 [!DNL Payment Services] 主页](payments-home.md) 以了解更多信息。
1. 配置付款选项 [信用卡](#credit-card-fields)， [付款按钮](#payment-buttons)、和 [按钮样式](#button-style)，详见以下部分。

### 信用卡字段

此 _[!UICONTROL Credit Card Fields]_这些设置为信用卡或借记卡支付方法提供了一个简单且安全的签出选项。

请参阅 [支付选项](payments-options.md#credit-card-fields) 以了解更多信息。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 选择商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其启用付款方式。
1. 在 **[!UICONTROL Credit card fields]** 部分中，编辑值 **[!UICONTROL Checkout title]** 用于更改结帐期间显示的付款方式名称的字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** 到 `Authorize` 或 `Authorize and Capture`.
1. 要在结账页面上排定付款方法的优先级，请提供 `Numeric Only` 中的值 **[!UICONTROL Sort order]** 字段。
1. 要启用 [3DS安全身份验证](security.md#3ds) (`Off` 默认情况下)切换 **[!UICONTROL 3DS Secure authentication]** 选择器到 `Always` 或 `When required`.
1. 要启用或禁用结账页面上的信用卡字段，请切换 **[!UICONTROL Show on checkout page]** 选择器。
1. 启用或禁用 [卡保险存储](#card-vaulting)，切换 **[!UICONTROL Vault enabled]** 选择器。
1. 启用或禁用 [管理员中的保管库支付方式](#card-vaulting) （对于商家要使用保险存储支付方式在管理员中为客户完成订单），请切换 **[!UICONTROL Show vaulted methods in Admin]** 选择器。
1. 要启用或禁用调试模式，请切换 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. [刷新缓存](#flush-the-cache).

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间在“付款方式”视图中添加文本，以显示此付款选项的标题。 选项： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 网站 | 此 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | 商店视图 | 结账页面上指定支付方式的排序顺序。 `Numeric Only` 值 |
| [!UICONTROL 3DS Secure authentication] | 网站 | 启用或禁用 [3DS安全身份验证](security.md#3ds). 选项： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | 网站 | 启用或禁用要在结账页面上显示的信用卡字段。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | 商店视图 | 启用或禁用 [信用卡保险存储](vaulting.md). 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | 商店视图 | 启用或禁用商家在管理员中为客户完成订单的功能 [使用保管式支付方式](vaulting.md). 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

此 [!UICONTROL Apple Pay] 按钮付款选项允许您提供 [!UICONTROL Apple Pay] 您商店从Safari浏览器结账的付款按钮。

只有在完成后才能使用Apple Pay [Apple Pay通过Paypal自助注册](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) 然后 [配置Apple Pay](settings.md/#payment-buttons) 你商店里的。 请参阅 [支付选项](payments-options.md#apple-pay-button) 以了解更多信息。

您可以启用和配置 [!UICONTROL Apple Pay] 按钮付款选项：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 选择商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其启用付款方式。
1. 在 **[!UICONTROL Apple Pay]** 部分中，编辑值 _[!UICONTROL Checkout title]_用于更改结帐期间显示的付款方式名称的字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** 到 `Authorize` 或 `Authorize and Capture`.
1. 要在结账页面上启用或禁用Apple Pay，请切换 **[!UICONTROL Show Apple Pay on checkout page]** 选择器。
1. 要在产品详细信息页面上启用或禁用Apple Pay，请切换 **[!UICONTROL Show Apple Pay on product detail page]** 选择器。
1. 要在迷你购物车预览中启用或禁用Apple Pay，请切换 **[!UICONTROL Show Apple Pay on the mini cart preview]** 选择器。
1. 要在购物车页面上启用或禁用Apple Pay，请切换 **[!UICONTROL Show Apple Pay on cart page]** 选择器。
1. 要启用或禁用调试模式，请切换 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. [刷新缓存](#flush-the-cache).

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Checkout title] | 商店视图 | 在结帐期间在“付款方式”视图中添加文本，以显示此付款选项的标题。 选项： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 网站 | 此 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions) 指定付款方式的。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | 网站 | 启用或禁用“Apple支付”按钮以在结账页面上显示。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | 网站 | 启用或禁用“Apple支付”按钮以在产品详细信息页面上显示。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | 网站 | 启用或禁用“Apple支付”按钮以在迷你购物车预览中显示。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | 网站 | 启用或禁用“Apple支付”按钮以在购物车页面上显示。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Off] / [!UICONTROL On] |

### 付款按钮

此 [!DNL PayPal Smart Buttons] 支付选项为您的客户提供简单、快速和安全的结账过程。 请参阅 [支付选项](payments-options.md#paypal-smart-buttons) 以了解更多信息。

您可以启用和配置PayPal智能按钮付款选项：

1. 选择商店视图，在 **[!UICONTROL Scope]** 下拉菜单，您要为其启用付款方式。
1. 要更改结账期间显示的付款方式名称，请编辑 **[!UICONTROL Checkout Title]** 字段。
1. 至 [设置付款操作](production.md#set-payment-services-as-payment-method)，切换 **[!UICONTROL Payment action]** 到 `Authorize` 或 `Authorize and Capture`.
1. 要在结账页面上排定付款方法的优先级，请提供 `Numeric Only` 中的值 **[!UICONTROL Sort order]** 字段。
1. 使用切换选择器启用或禁用 [!DNL PayPal smart button] 显示功能：

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > 使用Apple付费 [必须具有Apple sandbox tester帐户](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) （包括虚假信用卡和账单信息）进行测试。 当您准备好使用沙盒中的Apple Pay时 _或_ 生产模式，完成任意 [测试和验证](test-validate.md#test-in-sandbox-environment)，完成 [自助注册 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_注册您的实时域_ 部分)和 [在中为您的商店配置它 [!DNL Payment Services]](settings.md#payment-buttons).

     当您打开/关闭付款按钮或PayPal Pay Later消息的可见性时，“设置”页面底部会显示该配置的可视预览。

1. 要启用调试模式，请切换 **[!UICONTROL Debug Mode]** 选择器。
1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. [刷新缓存](#flush-the-cache).

#### 配置选项

| 字段 | 范围 | 描述 |
|---|---|---|
| [!UICONTROL Title] | 商店视图 | 在结帐期间，在“付款方式”视图中添加要作为此付款选项的标题显示的文本。 选项：文本字段 |
| [!UICONTROL Payment Action] | 网站 | 此 [付款操作](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定付款方式的。 选项： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | 商店视图 | 结账页面上指定支付方式的排序顺序。 `Numeric Only` 值 |
| [!UICONTROL Show PayPal buttons on checkout page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在结帐页面上。 选项： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在产品详细信息页面上。 选项： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在迷你购物车预览中。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | 商店视图 | 启用或禁用 [!DNL PayPal Smart Buttons] 在购物车页面上。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | 商店视图 | 启用或禁用显示付款按钮的稍后付款选项外观。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | 网站 | 在购物车、产品页面、迷你购物车和结帐流程中启用或禁用“稍后付款”消息。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | 商店视图 | 启用或禁用显示付款按钮的Venmo付款选项。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | 商店视图 | 启用或禁用显示付款按钮的Apple支付付款选项。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | 商店视图 | 启用或禁用显示付款按钮的信用卡和借记卡付款选项。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | 网站 | 启用或禁用调试模式。 选项： [!UICONTROL Off] / [!UICONTROL On] |

### 按钮样式

您还可以配置 _[!UICONTROL Button style]_付款按钮的选项：

1. 要更改 **[!UICONTROL Layout]**，选择 `Vertical` 或 `Horizontal`.

   >[!NOTE]
   >
   > 如果按钮样式配置为 `Horizontal` 且您的商店配置为显示多个付款按钮，则您只能看到产品页面、结帐页面和迷你购物车上显示两个按钮，购物车中显示的一个按钮。

1. 要在水平布局中启用标语，请切换 **[!UICONTROL Show tagline]** 选择器。
1. 要修改 **[!UICONTROL Color]**，选择所需的颜色选项。
1. 要修改 **[!UICONTROL Shape]**，选择 `Pill` 或 `Rectangle`.
1. 要启用按钮高度选择器，请切换 **[!UICONTROL Responsive button height]** 选择器。
1. 要修改 **[!UICONTROL Label]**，选择所需的标签选项。

   当您更改布局、颜色、形状、高度和标签的配置选项时，该配置的可视预览会显示在“设置”页面的底部。 在下图中， **[!UICONTROL Shape]** 设置为 _矩形_ 和 **[!UICONTROL Label]** 设置为 _PayPal（推荐）_.

   ![[!DNL PayPal Smart Buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

1. 单击 **[!UICONTROL Save]**.

   如果尝试离开此视图而不保存更改，会出现一个模式窗口，提示您放弃更改、继续编辑或保存更改。

1. [刷新缓存](#flush-the-cache).

您可以配置付款按钮样式 [在管理员的旧版配置中](configure-admin.md#configure-paypal-smart-buttons) 或此处输入 [!DNL Payment Services Home]. 请参阅 [PayPal按钮样式指南](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 有关设置PayPal付款按钮样式的详细信息。

#### 配置选项

| 字段 | 范围 | 描述 |
|--- |--- |--- |
| [!UICONTROL Layout] | 商店视图 | 定义付款按钮的布局样式。 选项： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 商店视图 | 启用/禁用标语。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | 商店视图 | 定义付款按钮的颜色。 选项： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 商店视图 | 定义付款按钮的形状。 选项： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 商店视图 | 定义付款按钮是否使用默认高度。 选项： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | 商店视图 | 定义付款按钮的高度。 默认值：无 |
| [!UICONTROL Label] | 商店视图 | 定义付款按钮中显示的标签。 选项： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 配置角色

要确保管理员用户能够在商务管理员中创建和管理订单，请启用 [!DNL Payment Services]特定于用户角色的资源。

请参阅 [用户角色](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) 以了解如何管理角色。

将资源分配给角色时，必须选择：

- **付款方式[!DNL Payment Services]** — 此资源可确保当您在Admin中创建订单时， [!DNL Payment Services] 信用卡可作为付款方式使用。 如果您选择 **操作** 父资源，也将选择此资源。
- **[!DNL Payment Services]** — 此资源包括 **仪表板** 和 **SaaS服务代理** 资源，也必须选择该属性。 它们确保 [!DNL Payment Services] 显示在 _销售_ 菜单。

  ![Payment Services资源](assets/roles-payments.png){width="400" zoomable="yes"}

## 刷新缓存

如果您在中更改配置 _设置_&#x200B;例如，切换Apple Pay、Venmo或PayPal PayLater按钮，手动刷新缓存，以便您的商店显示最新配置。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 单击 **[!UICONTROL Flush Cache]** 以刷新所有无效缓存。

如果高速缓存管理表中的任何高速缓存类型具有 `INVALIDATED` 状态，您的存储可能没有显示该项目的最新配置。 刷新缓存以更新存储以显示最新配置。

为确保您的商店显示正确的配置，请定期执行 [刷新缓存](https://docs.magento.com/user-guide/system/cache-management.html).

## 卡保险存储

您可以启用一些功能，使客户能够保存其“我的帐户”中的信用卡信息，以便将来购买时使用。

您也可以在“管理员”中使用卡保险存储来完成现有客户的后续订单。

启用或禁用中的信息卡保险存储 [信用卡字段设置](#credit-card-fields).

请参阅 [信用卡保险存储](vaulting.md) 以了解更多信息。

## 3DS

3DS可保护客户和商户免受其商店中的欺诈行为之害，并实现对欧盟(EU)标准的遵守。

在中启用或禁用3DS [信用卡字段设置](#credit-card-fields).

请参阅 [3DS的安全性](security.md#3ds) 以了解更多信息。

## 使用多个PayPal帐户

在 [!UICONTROL Payment Services]，您可以在以下位置使用多个PayPal帐户： **一** 网站级别的商家帐户。 例如，如果您在多个国家/地区(这些国家使用不同的 [货币](https://docs.magento.com/user-guide/stores/currency.html))或希望将Adobe Commerce用于部分业务，但不是 _所有_，您可以设置商家帐户以使用多个PayPal帐户。

请参阅 [站点、存储和查看范围](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 有关网站、商店和商店视图层次结构的更多信息。

您的销售代表可以创建 [范围](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) ，并使用PayPal登录其他网站，以便在您的网站上显示您配置的任何PayPal按钮。 请与您的销售代表联系，以获得有关为网站使用多个PayPal帐户的帮助。
