---
title: 启用 [!DNL Payment Services] 用于生产
description: 通过启用 [!DNL Payment Services] 用于生产。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# 启用 [!DNL Payment Services] 用于生产

您可以将服务投入生产并完成 [载入流程](onboard.md)，按照本主题中的步骤，在您：

* [安装](install.md) 支付服务扩展
* [配置并连接](connect.md) 您的实例
* [设置](sandbox.md) 和 [测试](test-validate.md) 您的沙盒

## 设置 [!DNL Payment Services] 作为支付方式

在您之后 [配置Commerce服务](connect.md#configure-commerce-services) 并启用 [沙盒测试](sandbox.md#enable-sandbox-testing) 或 [实时支付](#enable-live-payments)，您必须设置 [!DNL Payment Services] 作为您的付款方式。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Enable Payment Services]**.

   如果尚未配置，则此选项可见 [!DNL Payment Services] 作为一个或多个网站的付款方式。

   您将被定向到“主页”视图中的设置区域，并展开相关选项(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_)，您可以在此处启用 [!DNL Payment Services] 选项作为 [支付方式](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. 在 _[!UICONTROL General Configuration]_，设置&#x200B;**[!UICONTROL Enable]**到 `Yes`.
1. 设置 **[!UICONTROL Payment Action]**，表示两者 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal payment buttons]_，更改为以下任一项：

   | 设置 | 描述 |
   |---|---|
   | `Authorize` | 批准购买并暂停资金。 该金额在商户将该金额“扣押”前不予提取。 |
   | `Authorize and Capture` | 批准购买，商家则“捕获”资金。 |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] 支持部分捕获。 商家可以部分捕获（开票）订单部分。 例如，您可以单独捕获每个项目，或者现在捕获一个项目，稍后捕获其余项目。

1. 单击 **[!UICONTROL Save]**.
1. 单击 **[!UICONTROL Go to Payment Services]** 将定向回 [!DNL Payment Services] 家。
1. [清除缓存](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   应在每次配置更改后进行清除。

请参阅 [配置支付服务](settings.md) 有关配置信用卡字段和PayPal付款按钮的详细信息。

## 完成商户入门

使您的商店启用Payment Services的下一步是完成实时上线。

支付服务提供 [**高级** （完全支持）和 **标准** （快速结帐）付款选项](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) 以及载入流程，具体取决于您运营的国家/地区和首选支付体验。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Live onboarding]**.

   如果您尚未为完成实时载入，则可以看到此选项 [!DNL Payment Services].

1. 在 _选择您的国家/地区_ 模式中，选择您运营的国家/地区。

   Payment Services全面支持以下位置的所有支付选项： [5个国家](../payment-services/overview.md#availability) 当前。 Payment Services为国家/地区列表中表示的所有其他国家/地区提供快速结账功能（付款选项的子集）。

   您从列表中选择的国家/地区将决定支付选项和登录流程 — [高级](#advanced-onboarding) （完全支持）或 [标准](#standard-onboarding) （快速签出） — 可供您使用。

>[!TIP]
>
> 选择并继续载入选项（“标准”或“高级”）后，您必须重新完成入门，才能从初始选择进行升级或降级。

### 高级入门

此载入流程适用于以下地区的商家： [得到充分支持的国家](../payment-services/overview.md#availability).

选择国家/地区后：

1. 在显示的模式窗口中，选择 **高级**.

   对于 **标准** 选项，请转到 [标准载入流程](#standard-onboarding).

1. 单击 **继续**.
1. 使用您的PayPal帐户凭据（而不是沙盒帐户凭据）继续使用PayPal流程获取完全支持的高级入门培训 _或_ 注册一个新的PayPal帐户。

>[!IMPORTANT]
>
>**高级入门** 要求商家 [请求付款权利](#request-payments-entitlement-from-adobe) 以启用实时载入。

### 标准载入

此标准载入流程适用于位于以下国家/地区的商家： [仅支持Express结帐](../payment-services/overview.md#availability) 提供了。

选择国家/地区后：

1. 在 _支付服务协议_ 在出现的模式窗口中，单击 **支付服务协议** 用于查看Adobe Commerce Payment Services协议的链接。
1. 在 _支付服务协议_ 模式窗口，单击 **我接受**.
1. 继续使用PayPal流程进行快速结帐，使用您的PayPal帐户凭据（不是沙盒帐户凭据）或注册新的PayPal帐户。

>[!IMPORTANT]
>
>[Apple支付和信用卡字段](../payment-services/payments-options.md) 不可用于 **标准载入**.

## 确认电子邮件地址

1. 在管理员侧边栏上，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   此 _[!UICONTROL Live onboarding]_按钮不再可见，并且您看到“[!UICONTROL Live payments pending]“文本框。

   在该文本框中，系统可能还会要求您通过PayPal确认您的电子邮件地址以完成入门。

1. 如果系统提示您确认电子邮件地址，请检查从PayPal发送的确认消息的电子邮件，然后单击确认您的电子邮件地址。
1. 在管理员侧边栏上，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 刷新浏览器窗口。

   当您的PayPal商家注册被批准时，您应该会看到一则通知，声明您的支付系统处于沙盒模式并且不处理实时支付。

   >[!IMPORTANT]
   >
   >如果您撤销对 [!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 为了处理您的付款（在您的PayPal帐户设置中），您商店中的订单不能由处理 [!DNL Payment Services]. 在您的Payment Services主页上，会显示有关撤销同意的警报。

## 从Adobe请求付款权利

要启用您的商店，请从Adobe请求付款权利(对于 [仅高级载入](#advanced-onboarding))：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Get Live Payments]** 在您的 [!DNL Payment Services] 家。

   ![请求权利](assets/request-entitlements.png){width="500" zoomable="yes"}

1. 完成表单。
1. 销售团队的成员将与您联系。

或者，您可以向Adobe请求付款权利，网址为 [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**实时上线** 在批准付款权利之前不可访问。

## 配置定价层

获取您的 [!DNL Payment Services] _商家ID_：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在“主页”视图中，单击 **[!UICONTROL Settings]**. 请参阅 [主页](payments-home.md) 以了解更多信息。
1. 选择所需的 _商家ID_ 然后将其提交给您的销售代表，销售代表将配置正确的定价层。

请参阅 [2级和3级处理](levels-card-payment-transactions.md) 以了解有关付款交易记录的详细信息。

## 启用实时支付

A _生产贸易商ID_ 是自动生成的，并填充在 [配置](configure-admin.md). 请勿更改或更改此ID。

启用实时支付：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在主页上，单击 **[!UICONTROL Settings]** 页面右上角的。 请参阅 [主页](payments-home.md) 以了解更多信息。
1. 在 _[!UICONTROL General Configuration]_节集&#x200B;**[!UICONTROL Payment mode]**到 `Production`.
1. 单击 **[!UICONTROL Save]**.
1. [清除缓存](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >如果不清除缓存，客户在结账期间将无法看到PayPal付款选项。

如果您导航回 [!DNL Payment Services] 主页，沙盒支付模式消息不再显示，因为您现在正在处理实时支付。

请参阅 [在Admin中配置](configure-admin.md) 旧版配置选项。

>[!IMPORTANT]
>
>如果您撤销对 [!DNL Payment Services] 为了处理您的付款（在您的PayPal帐户设置中），您商店中的订单不能由处理 [!DNL Payment Services]. 如果您希望重新启用支付处理，则必须重新完成入门培训。 在您的Payment Services主页上，会显示有关撤销同意的警报。

## 在生产环境中测试

强烈建议您在向购物者公开此功能之前，使用真正的信用卡和银行在生产环境中测试支付。

请参阅 [测试和验证](test-validate.md) 以了解更多信息。
