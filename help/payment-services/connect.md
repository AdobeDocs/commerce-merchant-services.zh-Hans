---
title: 连接实例
description: 使用API密钥和私钥连接您的商务实例，并在配置中指定数据空间。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 连接实例

[!DNL Payment Services] 由Commerce Services提供支持并部署为SaaS（软件即服务）。 您可以使用API密钥和私钥连接Commerce实例，并在配置中指定数据空间。 只设置一次此连接。

请参阅 [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html)核心用户指南中的{target=&quot;_blank&quot;}以了解有关此服务的详细信息。

## 获取API凭据

要使用商务SaaS服务，您必须使用实例的API密钥，这些密钥是在 [“我的帐户”功能板](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}。 可以为商务帐户创建两个不同的API密钥对(一个用于沙盒，一个用于生产（实时支付）)，但一次只能主动使用一对。

>[!NOTE]
>
>需要有关访问 [!UICONTROL My Account] 仪表板？ 请参阅 [创建商务帐户](https://docs.magento.com/user-guide/magento/magento-account-create.html)核心用户指南中的{target=&quot;_blank&quot;}。

给定的API密钥对对于环境中的所有Commerce Services都有效，因此如果您已经为Commerce Services实例配置了Commerce Services，则管理员中已存在API密钥对。 如果您的专用API密钥丢失，则必须生成一个新的API密钥对，并将其应用于管理员中的Commerce Services配置。

要了解如何为沙盒或生产环境生成API密钥，请参阅 [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html)核心用户指南中的{target=&quot;_blank&quot;}。

>[!IMPORTANT]
>
>如果重新生成API密钥对并更改SaaS标识符，则此实例使用的所有Commerce Services都会连接到其他数据存储，并且您的访问（包括以前存储的数据）将丢失。 建议您不要重新生成API密钥对，而是在活动生产实例上更改SaaS标识符。

### 商务API密钥和私钥

某些Adobe Commerce和Magento Open Source功能部署为SaaS（软件即服务），称为Commerce Services。 要使用这些服务，您必须使用API密钥和私钥将您的Commerce实例连接到这些服务，并在 [配置](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}。

创建由MageID标识的商务帐户时，可以生成商务API密钥和私钥。 使用Commerce Services，例如 [!DNL Payment Services], [!DNL Product Recommendations]或 [!DNL Live Search]，则许可证持有者必须生成这些密钥，才能通过授权验证。 然后，这些密钥可以传递给代表许可证持有者管理项目和环境的系统集成商或开发团队。 如果您是解决方案集成商，则还有权根据自己的需要使用这些服务。 在这种情况下，商务合作伙伴合同的签名者应生成密钥。

### 生成API密钥和私钥

1. 登录您的Commerce帐户，网址为 [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. 在 **[!UICONTROL Magento]** 选项卡，选择 **[!UICONTROL API Portal]** 的问题。
1. 从 _[!UICONTROL Environment]_菜单，选择&#x200B;**[!UICONTROL Sandbox]**，则&#x200B;**[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >这两个环境都需要API密钥。

1. 在 _[!UICONTROL API Keys]_部分，单击&#x200B;**[!UICONTROL Add New]**.

   此操作将打开一个用于下载新密钥的对话框。

   >[!IMPORTANT]
   >
   >此对话框是您复制或下载密钥的唯一机会。

1. 单击 **[!UICONTROL Download]** 然后单击 **[!UICONTROL Cancel]**.

   的 _[!UICONTROL API Keys]_部分现在显示您的API密钥。

1. 选择或创建SaaS项目时，复制API密钥和私钥。

   请参阅 [SaaS](https://docs.magento.com/user-guide/system/saas.html)有关更多详细信息，请参阅核心用户指南中的{target=&quot;_blank&quot;}。

可以在多个实例中使用相同的API密钥，但每个实例必须具有自己的SaaS数据空间。

在创建SaaS项目时， Commerce会根据您的商务许可证生成一个或多个SaaS数据空间：

* Adobe Commerce — 一个生产数据空间；两个测试数据空间
* Magento Open Source — 一个生产数据空间；没有测试数据空间

### 配置SaaS项目

>[!NOTE]
>
>如果您没有看到 _[!UICONTROL Commerce Services Connector]_部分，您必须为所需的商务服务安装商务模块，例如 [[!DNL Payment Services]](install.md).

要选择或创建SaaS项目，请向商务许可证持有者请求您商店的商务API密钥。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 在左侧面板中，展开 **[!UICONTROL Services]** 选择 **[!UICONTROL Commerce Services Connector]**.
1. 在 _[!UICONTROL API Keys]_键值。

   >[!IMPORTANT]
   >
   >为这两者添加键值 **[!UICONTROL sandbox]** 和 **[!UICONTROL production]** 环境。

1. 单击 **[!UICONTROL Save Config]**.

   保存后，如果有任何SaaS项目与您的API密钥相关联，则这些项目会显示在 _[!UICONTROL SaaS Project]_字段_[!UICONTROL SaaS Identifier]_ 中。

1. 如果不存在SaaS项目，请单击 **[!UICONTROL Create Project]**. 然后，在 **[!UICONTROL Project Name]** 字段。
1. 要用于商务商店的当前配置，请选择 **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>如果在“我的帐户”的API门户部分中重新生成密钥，请立即更新“管理员”配置中的API密钥。 如果您在管理员中生成新密钥，并且不更新它们，则您的SaaS扩展将不再有效，并且您将丢失有价值的数据。

您可以通过单击 **[!UICONTROL Rename this Project]** 或 **[!UICONTROL Rename Data Space]** 按钮。

## 配置Commerce Services

入门的第一步 [!DNL Payment Services] 是在“管理员”中配置您的商务服务。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 单击 **[!UICONTROL Configure Commerce Services]**.

   如果您尚未为帐户配置Commerce Services，则会显示此选项。

   系统会将您定向到管理员中的配置区域， **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**，以配置Commerce Services Connector。

1. 要配置Commerce Services，请按照 [商务服务](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}。
