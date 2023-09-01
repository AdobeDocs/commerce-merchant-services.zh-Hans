---
title: 重要的防欺诈功能
description: 为以下项目启用自动欺诈防护 [!DNL Payment Services] 和西尼菲德在一起。
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: 400d1f8a384fceebcd13e9496f8e218e694d2752
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# 有效保护欺诈行为

您可以为以下项启用自动欺诈防护 [!DNL Payment Services] 使用 [显着扩展](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce支持Signifyd版本5.4.0及更高版本。 [!DNL Payment Services] 支持身份验证前和身份验证后签名流程。

请参阅 [重要文档](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) 了解有关安装和配置扩展的信息。

## 集成限制

目前，以下限制适用于Signifyd与 [!DNL Payment Services]：

* 含义/[!DNL Payment Services] 集成仅支持 [信用卡字段](../payment-services/payments-options.md#credit-card-fields) (不是PayPal支付按钮或Apple Pay)。 [!DNL Payment Services] 将通过PayPal支付按钮和Apple Pay接收的订单数据发送到Signifyd，但集成仅提供通过信用卡字段下订单的详细信息。
* 表示不支持商家为购物者向管理员下达的订单。
* Signid不支持以下内容的订单： [保险存储信用卡](../payment-services/vaulting.md).

## 入门

您必须直接与Signifyd通信才能载入扩展以用于 [!DNL Payment Services] — 没有 [!DNL Payment Services] 需要配置。 安装后，您可以在Admin中配置Signifyd扩展。 与此扩展相关的任何支持都将由Signifyd管理。

使用Signfyd登录时，您必须：

1. 联系Signid以设置新帐户。
1. 默认情况下，表示为 [已列入允许列表](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) 为确保Signifyd不会触发它当前不支持的其他支付选项。 如果要禁止特定付款方式，则必须进行更改。
1. 通过Signifyd确认贝宝不会拒绝可能由Signifyd批准的订单，具体方式是通过Paypal中的商家欺诈保护设置。
1. 启用要兼容的已签名扩展 [!DNL Payment Services]：
   * 使用时 [!DNL Payment Services] 在 _实时_ 模式，表示必须处于生产模式。
   * 使用时 [!DNL Payment Services] 在 _沙盒_ 模式，表示必须处于测试模式。

## 配置

由于表示对订单执行了某些活动，因此必须配置扩展以使其根据您为设置的付款活动适当地运行 [!DNL Payment Services].

这些配置选项与Payment Services和Signifyd集成不兼容：

* 时间 [!DNL Payment Services] 配置有 `Authorize` 付款操作 _和_ 表示已加入 `PostAuth` 模式 _[!UICONTROL Decline Guarantees]_选项设置为&#x200B;**创建贷项通知单**.

  原因： [!DNL Payment Services] 创建授权交易记录，表示然后尝试退款。


* [!DNL Payment Services] 配置有 `Authorize and Capture` 付款操作 _和_ 表示已加入 `PostAuth` 模式 _[!UICONTROL Decline Guarantees]_选项设置为&#x200B;**取消订单**.

  原因： [!DNL Payment Services] 创建捕获事务，表示随后尝试作废。


有关以下内容的信息，请参阅重要文档 [配置扩展](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

请参阅重要文档，以 [了解有关订单工作流的更多信息](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
