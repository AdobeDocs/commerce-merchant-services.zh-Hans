---
title: 载入 [!DNL Payment Services]
description: 将您的实例连接到 [!DNL Payment Services] 功能，完成几个入门步骤。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 载入 [!DNL Payment Services]

开始使用 [!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，您必须完成一些入门步骤，将您的实例与支付功能相连接。

## 载入流程

![载入流程](assets/onboarding-diagram.svg)

此载入流程图显示了载入的一般流程 [!DNL Payment Services].

完成沙盒或实时支付入门后，可从以下位置访问Financial Reporting： [!DNL Payment Services] 在“管理员”中。

如果沙盒和实时支付都已载入并启用，则您可以轻松地在 [!DNL Payment Services] 家。

## 先决条件

要使用 [!DNL Payment Services]中，您必须为实例提供以下内容：

* 服务连接器模块
* 服务ID模块
* API密钥

服务连接器和服务ID模块会在 [安装 [!DNL Payment Services]](install.md). 安装完成后，您可以在配置设置(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

要了解如何创建或访问API密钥，请参阅 [API凭据](#obtain-api-credentials).

## 载入步骤

1. [安装 [!DNL Payment Services] 扩展](install.md#get-payment-services).
1. [获取API凭据](connect.md#obtain-api-credentials).
1. [连接实例](connect.md#configure-commerce-services) 到Commerce Services。 每个商务实例只能完成一次此连接。
1. [设置沙盒服务](sandbox.md#enable-sandbox-testing) (或者，也可以继续执行 [启用实时支付](sandbox.md#enable-live-payments) 如果您已在其他环境中测试过功能)，请使用测试的PayPal支付处理帐户。
1. [设置 [!DNL Payment Services] 作为您的付款方式](production.md#set-payment-services-as-payment-method)，以开始处理测试支付。
1. [请求付款权利](production.md#request-payments-entitlement-from-adobe) 以启用实时载入。
1. [完成商户入门](production.md#complete-merchant-onboarding) 以启用您的Commerce网站的实时支付。
1. [获取您的 [!DNL Payment Services] 商家ID](production.md#configure-pricing-tier) 然后交给销售人员来配置正确的定价层。
1. [启用 [!DNL Payment Services] 在实时模式下](production.md#enable-live-payments) 以开始处理实时支付。
1. 测试支付，两者 [沙盒](sandbox.md#test-in-sandbox-environment) 和 [生产](production.md#test-in-production) 环境。

>[!NOTE]
>
>如果您未在管理员（步骤3）中配置Commerce Services，则无法设置沙盒或实时支付。

## 故障排除

* [疑难解答 [!DNL Payment Services] 安装](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [未验证PayPal沙盒帐户](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [延迟 [!DNL Payment Services] 报表数据](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [在Sandbox环境中处理付款时，使用PayPal测试信用卡失败](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
