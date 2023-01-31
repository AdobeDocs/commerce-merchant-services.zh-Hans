---
title: 板载 [!DNL Payment Services]
description: 将实例与 [!DNL Payment Services] 功能。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 板载 [!DNL Payment Services]

开始使用 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，则必须完成一些入门步骤，以便将实例与付款功能连接。

## 载入流程

![载入流程](assets/onboarding-diagram.svg)

此载入流程图显示了载入的一般流程 [!DNL Payment Services].

在您完成沙盒或实时支付入门后，即可从访问财务报告 [!DNL Payment Services] 中。

如果载入并启用了沙盒和实时支付，则可以从 [!DNL Payment Services] 回家。

## 先决条件

为了使用 [!DNL Payment Services]，则您必须在实例中使用以下内容：

* 服务连接器模块
* 服务ID模块
* API密钥

服务连接器和服务ID模块在 [安装 [!DNL Payment Services]](install.md). 安装完成后，您可以在配置设置(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

要了解如何创建或访问API密钥，请参阅 [API凭据](#obtain-api-credentials).

## 入门步骤

1. [安装 [!DNL Payment Services] 扩展](install.md#get-payment-services).
1. [获取API凭据](connect.md#obtain-api-credentials).
1. [连接实例](connect.md#configure-commerce-services) 到Commerce Services。 每个Commerce实例只能完成一次此连接。
1. [设置沙盒服务](sandbox.md#enable-sandbox-testing) (或者，继续 [启用实时支付](sandbox.md#enable-live-payments) 如果您已在其他环境中测试了功能)，则使用测试PayPal付款处理帐户。
1. [已设置 [!DNL Payment Services] 作为付款方式](production.md#set-payment-services-as-payment-method)，以开始处理测试付款。
1. [请求付款权利](production.md#request-payments-entitlement-from-adobe) 启用实时载入。
1. [完整的商户登入](production.md#complete-merchant-onboarding) 为您的商务网站启用实时付款。
1. [获取 [!DNL Payment Services] 商户ID](production.md#configure-pricing-tier) 并将其交给销售部，以配置正确的定价层。
1. [启用 [!DNL Payment Services] 处于实时模式](production.md#enable-live-payments) 开始处理实时支付。
1. 测试支付，在 [沙盒](sandbox.md#test-in-sandbox-environment) 和 [生产](production.md#test-in-production) 环境。

>[!NOTE]
>
>如果您未在管理员（步骤3）中配置Commerce Services，则无法设置沙盒或实时支付。

## 疑难解答

* [故障诊断 [!DNL Payment Services] 安装](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal沙盒帐户未验证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [延迟 [!DNL Payment Services] 报告数据](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [在沙盒环境中处理付款时，测试信用卡失败并出现PayPal错误](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
