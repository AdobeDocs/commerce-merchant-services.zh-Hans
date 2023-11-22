---
title: 启用 [!DNL Payment Services] 用于生产
description: 通过启用 [!DNL Payment Services] 用于生产。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '731'
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
1. 设置 **[!UICONTROL Payment Action]**，表示两者 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal Smart Buttons]_，更改为以下任一项：

   | 设置 | 描述 |
   |---|---|
   | `Authorize` | 批准购买并暂停资金。 该金额在商户将该金额“扣押”前不予提取。 |
   | `Authorize and Capture` | 批准购买，商家则“捕获”资金。 |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] 支持部分捕获。 商家可以部分捕获（开票）订单部分。 例如，您可以单独捕获每个项目，或者现在捕获一个项目，稍后捕获其余项目。

1. 单击 **[!UICONTROL Save]**.
1. 单击 **[!UICONTROL Go to Payment Services]** 将定向回 [!DNL Payment Services] 家。
1. [清除缓存](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   应在每次配置更改后进行清除。

请参阅 [配置支付服务](settings.md) 有关配置信用卡字段和PayPal智能按钮的详细信息。

## 完成商户入门

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Live onboarding]**.

   如果您尚未为完成实时载入，则可以看到此选项 [!DNL Payment Services].

   您会看到一个PayPal窗口。

1. 继续使用PayPal流程，使用您的PayPal帐户凭据（不是沙盒帐户凭据）或注册新的PayPal帐户。
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

要启用实时入门，您必须向Adobe请求付款权利：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Get Live Payments]** 在您的 [!DNL Payment Services] 家。

   ![请求权利](assets/request-entitlements.png){width="500" zoomable="yes"}

1. 完成表单。
1. 销售团队的成员将与您联系。

或者，您也可以Adobe以下地址申请支付权限： [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**实时上线** 在批准付款权利之前不可访问。

## 配置定价层

获取您的 [!DNL Payment Services] _商家ID_：


1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在“主页”视图中，单击 **[!UICONTROL Settings]**. 请参阅 [主页](payments-home.md) 以了解更多信息。
1. 选择所需的 _商家ID_ 然后将其提交给您的销售代表，销售代表将配置正确的定价层。

## 启用实时支付

A _生产贸易商ID_ 是自动生成的，并填充在 [配置](configure-admin.md). 请勿更改或更改此ID。

要启用实时付款，请执行以下操作：

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
