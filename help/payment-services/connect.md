---
title: 连接实例
description: 使用API密钥和私钥连接您的Commerce实例，并在配置中指定数据空间。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 57b140463d457404b57dd23d33c72e48b4c3ac89
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# 连接实例

[!DNL Payment Services] 由Commerce Services提供支持，并部署为SaaS（软件即服务）。 您使用API密钥和私钥连接Commerce实例，并使用指定配置中的数据空间 [Commerce服务连接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **您只设置一次此连接。**

* 如果您拥有 *已连接您的实例*，通过获取和使用您的API凭据并配置Commerce Services，您可以继续 [设置测试沙盒](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 如果你还在 *需要连接您的实例*，请参阅本主题中关于 [获取API凭据](#obtain-api-credentials) 和 [配置Commerce服务](#configure-commerce-services).
* 如果您是 *不确定您的实例是否已连接*，导航到 **系统** >服务> **Commerce服务连接器** 并在中查看公共API密钥和私有API密钥值 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 部分，以及 *项目* 和 *数据空间* 中的字段 [!UICONTROL SaaS Identifier] 部分。 如果这些值存在，则表示您的实例已连接。

>[!NOTE]
>
>所有有权使用支付服务的商家都可以使用一个生产数据空间和两个测试数据空间。

## 获取API凭据

要使用Commerce SaaS服务，您必须对沙盒和生产实例使用API密钥（Commerce公共API密钥和私钥），这些API密钥是在您的中创建和管理的。 [我的帐户信息板](https://account.magento.com/customer/account/login). [密钥对](https://docs.magento.com/user-guide/configuration/services/saas.html) 可以为Commerce帐户创建（一个用于沙盒，一个用于生产），但一次只能活动使用一对。

>[!NOTE]
>
>需要访问的相关帮助 [!UICONTROL My Account] 仪表板？ 请参阅 [创建Commerce帐户](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公共API密钥创建后，始终可在“我的帐户”信息板中使用。 您可以根据需要复制或删除它。 在为沙盒或生产环境创建公共API密钥时，私有API密钥将变得可见；它只能从后续对话框中复制或保存，并且以后无法访问。

给定的API密钥对对适用于环境中的所有Commerce Services，因此，如果您已经为您的实例配置了Commerce Services，则Commerce Services Connector中已存在您的API密钥对。

如果您的API密钥丢失，则新的API密钥对必须为 [已生成](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [已应用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 到管理员中的Commerce Services Connector配置。 如果配置的密钥有误或配置中不存在任何密钥，则付款服务中将显示帐户验证错误对话框，通知您未验证帐户。

查看 [使用API的可用Commerce服务列表](https://docs.magento.com/user-guide/system/saas.html#available-services).

要了解如何为沙盒或生产环境生成API密钥，请参阅 [凭据](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>建议您不要重新生成API密钥对 *和* 更改活动生产实例上的SaaS标识符和/或数据空间。 如果对实例进行修改，您将丢失实例的数据。

## 配置Commerce服务

可以在各个实例中使用相同的API密钥，但每个实例必须具有自己的密钥 [SaaS数据空间](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>商家必须使用为MageID生成的相同密钥来获取他们的付款权利。

现在您已获得凭据，可以配置SaaS项目和Saas数据空间了。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 单击 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未为帐户配置Commerce Services，则此选项可见。

   您将被定向到“管理员”中的配置区域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以配置您的Commerce Services连接器。

1. 要配置Commerce服务，请按照中所述的步骤操作 [SaaS配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
