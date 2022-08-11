---
title: 连接实例
description: 使用API密钥和私钥连接您的商务实例，并在配置中指定数据空间。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: a983cf30872544d72bd13c3f04f04a35eebcf85d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 连接实例

[!DNL Payment Services] 由Commerce Services提供支持并部署为SaaS（软件即服务）。 您可以使用API密钥和私钥连接Commerce实例，然后使用 [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **只设置一次此连接。**

* 如果 *已连接实例*，通过获取和使用您的API凭据并配置Commerce Services，您可以继续 [设置测试沙盒](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 如果你还在 *需要连接实例*，请参阅本主题中关于 [获取API凭据](#obtain-api-credentials) 和 [配置商务服务](#configure-commerce-services).
* 如果您 *不确定您的实例是否已连接*，导航到 **系统** >服务> **Commerce Services Connector** 和查看 [!UICONTROL Sandbox Keys] 和 [!UICONTROL Production Keys] 部分和 *项目* 和 *数据空间* 字段 [!UICONTROL SaaS Identifier] 中。 如果存在这些值，则表示已连接您的实例。

## 获取API凭据

要使用商务SaaS服务，您必须将实例的API密钥（商务公共API密钥和私钥）用于沙盒和生产，这些密钥在您的 [“我的帐户”功能板](https://account.magento.com/customer/account/login). [键对](https://docs.magento.com/user-guide/configuration/services/saas.html) 可以为商务帐户（一个用于沙盒，一个用于生产）创建，但一次只能主动使用一对。

>[!NOTE]
>
>需要有关访问 [!UICONTROL My Account] 仪表板？ 请参阅 [创建商务帐户](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公共API密钥一经创建，便始终可在“我的帐户”功能板中使用。 可以根据需要复制或删除该数据。 在为沙盒或生产创建公共API密钥时，专用API密钥会变得可见；它只能从后续对话框中复制或保存，以后无法访问。

给定的API密钥对对于环境中的所有商务服务都有效，因此，如果您已经为实例配置了商务服务，则您的API密钥对已存在于商务服务连接器中。

如果您的API密钥丢失，则必须为 [生成](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 和 [应用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) 到“管理员”中的Commerce Services Connector配置。 如果配置了错误的密钥或配置中不存在密钥，则Payment Services中会显示一个帐户验证错误对话框，通知您帐户未验证。

查看 [使用API的可用商务服务列表](https://docs.magento.com/user-guide/system/saas.html#available-services).

要了解如何为沙盒或生产环境生成API密钥，请参阅 [凭据](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>建议您不要重新生成API密钥对 *和* 更改活动生产实例上的SaaS标识符和/或数据空间。 如果对实例进行了修改，您将丢失其数据。

## 配置Commerce Services

可以在实例之间使用相同的API密钥，但每个实例必须具有自己的 [SaaS数据空间](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

现在，您已获得凭据，接下来可以配置SaaS项目和Saas数据空间。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 单击 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未为帐户配置Commerce Services，则会显示此选项。

   系统会将您定向到管理员中的配置区域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以配置Commerce Services Connector。

1. 要配置Commerce Services，请按照 [SaaS配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
