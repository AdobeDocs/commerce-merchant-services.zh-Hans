---
title: 付款选项
description: 设置付款选项以自定义商店客户可用的方法。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 31665f90909ce2364579fc7f9c97087e2376c0a6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# 付款选项

替换为 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] [!DNL Payment Services]，您有多个可用的支付选项。 您可以通过以下方式配置这些付款选项：

* [主页设置](payments-home.md)
* [存储配置](configure-admin.md) （建议使用旧版支付选项或多商店设置）

根据您在结帐过程中的位置，每种付款方法都有不同的行为：

* 产品页面 — 项目的产品页面
* 迷你购物车 — 将产品添加到购物车后，单击购物车图标即可使用
* 购物车 — 单击后即可使用 _查看和编辑购物车_ 从mini-cart
* 签出视图 — 单击时可用 _继续结帐_ 从迷你购物车或购物车

>[!IMPORTANT]
>
>必须先完成支付服务载入，然后才能处理支付。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 为信用卡或借记卡支付方法提供简单安全的结账。 当购物者使用信用卡字段结账时，他们输入姓名、帐单地址以及信用卡或借记卡信息以下订单。 客户信息在购买会话期间被安全地使用，以无缝地引导他们完成结账流程。

启用 [信用卡保险存储](#vaulting) 让您的商店允许购物者保存（保存）其信用卡信息，以便稍后快速结账。

您可以配置 [!UICONTROL Credit Card Fields] 在商店配置或Payment Services主页中。 参见 [设置](settings.md#credit-card-fields) 了解更多信息。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]，使用PayPal完成购买，存储购物者的送货地址、帐单地址和付款详细信息以供将来使用。 购物者可以使用PayPal以前存储或提供的任何支付方式。

![[!DNL PayPal Smart Buttons] options](assets/buttons-md.png)

您可以配置 [!UICONTROL PayPal Smart Buttons] 在商店配置或Payment Services主页中。  参见 [设置](settings.md#payment-buttons) 了解更多信息。

### [!DNL PayPal] 按钮

客户可以使用PayPal按钮轻松自信地结账。

此 [!DNL PayPal] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

### [!DNL Venmo] 按钮

客户可使用以下工具结帐： [Venmo](https://venmo.com/) 按钮。

此 [!DNL Venmo] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

### [!DNL Apple Pay] 按钮

客户可以在他们的设备上使用Touch ID来使用 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)，它会使用存储在其iOS或macOS设备上的信用卡和借记卡支付凭据。

此 [!DNL Apple Pay] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

>[!NOTE]
>
> 要使用Apple Pay，请联系您的销售代表或Adobe客户团队，为您的实时商店启用它。

### [!DNL Pay Later] 按钮

为客户提供短期、无息支付和其他融资选项，以便他们现在购买以后使用 [!DNL Pay Later] 按钮。

此 [!DNL Pay Later] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见：

* **当客户选择$30至$600的产品时**，PayPal下的消息传送和 [!DNL Pay Later] 按钮为客户提供了更多关于 [!DNL Pay in 4] 付款选项。 客户可以点击 **了解详情** 以了解“[!DNL Pay in 4]”选项 _或_ 单击弹出窗口中的“或查看6个月特别融资”文本，了解并申请PayPal信用选项。
* **当客户选择超过$98.99的产品时**，PayPal下的消息传送和 [!DNL Pay Later] 按钮为客户提供了有关PayPal信用支付选项的更多信息。 客户可以点击 **了解详情** 要了解并申请PayPal点数选项， _或_ 单击弹出窗口中的“或参阅按4付费”文本以了解 [!DNL Pay in 4] 选项。

   >[!NOTE]
   >
   >上述金额可能有所变动。

参见 [设置](settings.md#payment-buttons) 以了解如何禁用/启用 [!DNL Pay Later] 消息传送。

有两种付款方式 [!DNL Pay Later] 按钮：

* **4小时付费** — 初次支付首期付款后，客户可以通过四次免息付款（每两周）支付其订单余额。 请参阅 [以4个文档付款](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 了解更多信息。
* **PayPal点数** — 客户可在六个月后支付全部订单余额，且免息。 请参阅 [PayPal信用文档](https://www.paypal.com/us/webapps/mpp/paypal-credit) 了解更多信息。

### [!DNL Pay Now] 按钮

此 [!DNL Pay Now] 当客户单击付款屏幕上的付款按钮时，按钮在PayPal弹出窗口中可见。

如果最终订单金额未知（例如，当您还没有送货地址信息时），并且客户正在从产品页面、迷你购物车或购物车中结帐，则 _继续_ 按钮可用。 客户点击时 _继续_，在确认其支付方式后，客户将转到订单审核页面，以在完成结账之前收集所需的详细信息。

## 订单重新计算

当客户从迷你购物车、购物车或产品页面进入结帐流程时，会被定向到订单审核页面，他们可以在PayPal弹出窗口中看到选定的送货地址。 客户选择发运方法后，订单金额会进行适当重新计算，并且客户可以看到发运成本和税额。

当客户从结帐页面进入结帐流程时，系统已知道送货地址和最终计算金额，并且总数已适当显示。

免税期、运费和销售税可能因地点而异。 晚于 [!DNL Payment Services] 接收送货地址和运费，然后快速重新计算所有适用的成本，并在结账的最后阶段适当地显示这些成本。

## 从产品页面中结帐

客户使用PayPal或 [!DNL Pay Later] 按钮时，只会购买当前产品页面中显示的项目。 已存在于客户购物车中的商品不会添加到结账流程中，也不会购买。

如果客户取消订单，则当前产品页面中的项目将添加到客户的购物车中，加入购物车中存在的任何其他项目。 此功能允许客户快速购买他们当前正在查看的项目，同时还可以保留他们之前浏览产品时添加到购物车的任何其他项目。

当客户从产品页面进入结帐流程时，结帐页面得到简化，视图仅显示与订单相关的数据和选项。

## 信用卡保险存储

购物者可以将其信用卡信息保存或“保存”，以便将来在网站级别（同一商家帐户内的任何商店）进行购买。

参见 [信用卡保险存储](vaulting.md) 了解更多信息。

## 安全性

参见 [PCI合规性](security.md#pci-compliance) 了解更多信息。
