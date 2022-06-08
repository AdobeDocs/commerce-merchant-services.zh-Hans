---
title: 启用 [!DNL Payment Services] 生产
description: 通过启用 [!DNL Payment Services] 生产。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 51722d7045ccb6ccfdc7ab5bd93d5ca46b52cf03
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# 启用 [!DNL Payment Services] 生产

在Payments Services扩展之后 [已安装](install.md)，则实例为 [已配置并连接](connect.md)，而您 [设置沙盒](sandbox.md) 经过测试后，您可以继续将服务投入生产并完成 [载入过程](onboard.md).

## 已设置 [!DNL Payment Services] 作为付款方式

在 [配置Commerce Services](connect.md#configure-commerce-services) 启用 [沙盒测试](sandbox.md#enable-sandbox-testing) 或 [实时支付](#enable-live-payments)，则必须设置 [!DNL Payment Services] 作为您的付款方式。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Enable Payment Services]**.

   如果尚未配置，则会显示此选项 [!DNL Payment Services] 作为一个或多个Magento网站的付款方法。

   将您定向到“主页”视图中的设置区域，并展开相关选项(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_)，您可以在其中启用 [!DNL Payment Services] 选项 [付款方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}。

1. 在 _[!UICONTROL General Configuration]_，设置&#x200B;**[!UICONTROL Enable]**to `Yes`.
1. 已设置 **[!UICONTROL Payment Action]**，用于 _[!UICONTROL Credit Card Fields]_和_[!UICONTROL PayPal Smart Buttons]_，更改为以下任一内容：

   | 设置 | 描述 |
   |---|---|
   | `Authorize` | 批准购买并暂停资金。 该金额在被商户“捕获”之前不会撤回。 |
   | `Authorize and Capture` | 批准购买，商家将“捕获”资金。 |

1. 单击 **[!UICONTROL Save]**.
1. 单击 **[!UICONTROL Go to Payment Services]** 被引回 [!DNL Payment Services] 回家。
1. [清除缓存](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   应在每次配置更改后完成清除。

请参阅 [配置支付服务](settings.md) 有关配置信用卡字段和PayPal智能按钮的详细信息。

## 完整的商户登入

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Live onboarding]**.

   如果尚未完成的实时载入，则会显示此选项 [!DNL Payment Services].

   您将看到一个PayPal窗口。

1. 使用您的PayPal帐户凭据（而非沙盒帐户凭据）继续PayPal流程，或注册新的PayPal帐户。
1. 在管理员侧栏中，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   的 _[!UICONTROL Live onboarding]_按钮将不再可见，并且您会看到[!UICONTROL Live payments pending]“ ”。

   在该文本框中，可能还会要求您与PayPal确认电子邮件地址以完成载入。

1. 如果系统提示您确认您的电子邮件地址，请检查您的电子邮件，以获取PayPal发送的确认消息，然后单击以确认您的电子邮件地址。
1. 在管理员侧栏中，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 刷新浏览器窗口。

   当您的PayPal商户入门获得批准后，您应会看到一则通知，指出您的支付系统处于沙盒模式且不处理实时支付。

   >[!IMPORTANT]
   >
   >如果您撤消对 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 处理付款时（在您的PayPal帐户设置中），您商店中的订单无法由 [!DNL Payment Services]. 在您的Payment Services主页上，会显示有关已吊销同意的警报。

## 从Adobe请求付款权利

要启用实时载入，您必须从Adobe请求付款权利：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Get Live Payments]** 在 [!DNL Payment Services] 回家。

   ![请求授权](assets/request-entitlements.png)

1. 填写表单。
1. 销售团队的一位成员将与您联系。

或者，您也可以在以下位置从Adobe请求付款授权： [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**实时载入** 在批准付款权利之前，无法访问。

## 配置定价层

获取 [!DNL Payment Services] _商户ID_:


1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在主页视图中，单击 **[!UICONTROL Settings]**. 请参阅 [主页](payments-home.md) 以了解更多信息。
1. 选择所需的 _商户ID_ 并将其提交给销售代表，销售代表将配置正确的定价层。

## 启用实时付款

A _生产商ID_ 会在 [配置](configure-admin.md). 请勿更改或更改此ID。

要启用实时付款，请执行以下操作：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 在主页上，单击 **[!UICONTROL Settings]** 的双曲余切值。 请参阅 [主页](payments-home.md) 以了解更多信息。
1. 在 _[!UICONTROL General Configuration]_节集&#x200B;**[!UICONTROL Payment mode]**to `Production`.
1. 单击 **[!UICONTROL Save]**.
1. [清除缓存](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   >[!IMPORTANT]
   >
   >如果您未清除缓存，客户在结帐期间将看不到PayPal付款选项。

如果您导航回 [!DNL Payment Services] 主页上，沙盒支付模式消息将不再显示，因为您现在正在处理实时支付。

请参阅 [在管理员中配置](configure-admin.md) ，以了解旧版配置选项。

>[!IMPORTANT]
>
>如果您撤消对 [!DNL Payment Services] 处理付款时（在您的PayPal帐户设置中），您商店中的订单无法由 [!DNL Payment Services]. 如果要重新启用付款处理，则必须再次完成载入。 在您的Payment Services主页上，会显示有关已吊销同意的警报。

## 在生产中测试

强烈建议您在生产中使用真实信用卡和银行测试付款，然后再向购物者公开此功能。

请参阅 [测试和验证](test-validate.md) 以了解更多信息。
