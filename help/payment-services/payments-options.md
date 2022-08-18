---
title: 付款选项
description: 设置付款选项以自定义商店客户可用的方法。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: c7afa798096e07409fb36a3d08f7e5b2a5ce40db
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# 付款选项

使用 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] [!DNL Payment Services]，则您可以使用多个付款选项。 您可以通过以下方式配置这些付款选项：

* [主页设置](payments-home.md)
* [存储配置](configure-admin.md) （建议使用旧版付款选项或多商店设置）

每种付款方法的行为取决于您在结账流程中的位置：

* 产品页面 — 项目的产品页面
* 迷你购物车 — 将产品添加到购物车后，单击购物车图标即可使用
* 购物车 — 单击 _查看和编辑购物车_ 从迷你车上
* 结帐视图 — 单击时可用 _继续结帐_ 从迷你购物车或购物车

>[!IMPORTANT]
>
>必须先完成支付服务载入，然后才能处理付款。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 为信用卡或借记卡付款方法提供简单且安全的结账。 当购物者使用信用卡字段签出时，他们会输入其名称、帐单地址以及信用卡或借记卡信息，以下单。 在购买会话期间，可安全地使用客户信息，以无缝指导客户完成结账流程。

您可以配置 [!UICONTROL Credit Card Fields] 在存储配置或支付服务主页中。 请参阅 [设置](settings.md#credit-card-fields) 以了解更多信息。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]，后者使用PayPal完成购买，存储购物者的送货地址、帐单地址和付款详细信息以供日后使用。 购物者可以使用PayPal之前存储或提供的任何付款方法。

![[!DNL PayPal Smart Buttons] 选项](assets/buttons-md.png)

您可以配置 [!UICONTROL PayPal Smart Buttons] 在存储配置或支付服务主页中。  请参阅 [设置](settings.md#payment-buttons) 以了解更多信息。

### [!DNL PayPal] 按钮

使用PayPal按钮，客户可以轻松、放心地结帐。

的 [!DNL PayPal] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

### [!DNL Venmo] 按钮

客户可以使用 [Venmo](https://venmo.com/) 按钮。

的 [!DNL Venmo] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

### [!DNL Apple Pay] 按钮

客户可以在其设备上使用触屏ID以使用 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)，它利用存储在其iOS或macOS设备上的信用卡和借记卡付款凭据。

的 [!DNL Apple Pay] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见。

>[!NOTE]
>
> 要使用Apple Pay ，请联系您的销售代表以将其启用到实时商店。

### [!DNL Pay Later] 按钮

为客户提供短期、免息的付款和其他融资选项，以便他们现在购买并稍后使用 [!DNL Pay Later] 按钮。

的 [!DNL Pay Later] 按钮在产品页面、迷你购物车、购物车和结帐视图中可见：

* **客户选择30美元到600美元之间的产品时**，在PayPal和 [!DNL Pay Later] 按钮可为客户提供有关 [!DNL Pay in 4] 付款选项。 客户可以单击 **了解更多** 了解“[!DNL Pay in 4]&quot;选项 _或_ 单击弹出式窗口中的“或查看6个月特殊融资”文本，了解并申请PayPal信用选项。
* **当客户选择的产品或产品超过$98.99时**，在PayPal和 [!DNL Pay Later] 按钮为客户提供了有关PayPal信用付款选项的更多信息。 客户可以单击 **了解更多** 了解并申请PayPal信用选项， _或_ 单击弹出式窗口中的“或查看4中的付费”文本，以了解 [!DNL Pay in 4] 选项。

   >[!NOTE]
   >
   >上列金额可能有变动。

请参阅 [设置](settings.md#payment-buttons) 了解如何禁用/启用 [!DNL Pay Later] 消息传送。

在 [!DNL Pay Later] 按钮：

* **在4分钟内付款** — 客户在首次首付后，可以以四次免息付款（每两周）支付订单余额。 请参阅 [在4个文档中支付](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 以了解更多信息。
* **PayPal信用** — 客户可以在6个月内足额支付订单余额，无息。 请参阅 [PayPal信用文档](https://www.paypal.com/us/webapps/mpp/paypal-credit) 以了解更多信息。

### [!DNL Pay Now] 按钮

的 [!DNL Pay Now] 按钮在客户单击付款屏幕上的付款按钮时显示在PayPal弹出窗口中。

如果最终订单金额尚未知晓（例如，当您还没有送货地址信息时），并且客户正在从产品页面、迷你购物车或购物车中签出，则 _继续_ 按钮。 客户单击 _继续_，在确认其付款方法后，系统会将他们定向到订单审核页面，以在完成结帐之前收集所需的详细信息。

## 订单重新计算

当客户从迷你购物车、购物车或产品页面进入结帐流程时，他们将被定向到订单审核页面，在该页面中，他们可以在PayPal弹出窗口中查看所选送货地址。 在客户选择发运方法后，将相应地重新计算订单金额，并且客户可以查看发运成本和税。

当客户从结帐页面进入结帐流程时，系统已知道送货地址和最终计算金额，并且总数会相应地显示出来。

免税期、运费和销售税因地点而异。 之后 [!DNL Payment Services] 接收送货地址和费率后，系统会快速重新计算所有适用的成本，并在结帐的最后阶段相应地显示这些成本。

## 从产品页面结账

当客户使用PayPal或 [!DNL Pay Later] 按钮，则仅购买当前产品页面中表示的项目。 客户购物车中已存在的项目不会添加到结帐流程中，也不会进行购买。

如果客户取消订单，则当前产品页面中的项目将添加到客户的购物车，并加入购物车中存在的任何其他项目。 此函数允许客户快速购买其当前正在查看的项目，同时保留之前在浏览产品时添加到购物车的任何其他项目。

当客户从产品页面进入结账流程时，结账页面会得到简化，该视图仅显示与订单相关的数据和选项。

## 安全性

请参阅 [PCI合规性](security.md#pci-compliance) 以了解更多信息。
