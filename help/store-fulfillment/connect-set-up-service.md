---
title: 连接Store Fulfillment解决方案
description: 在Adobe Commerce和Store Fulfillment解决方案之间建立连接。 创建和授权Adobe Commerce集成，并将商店履行帐户凭据添加到Adobe Commerce服务配置。
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# 连接Store Fulfillment解决方案

通过将所需的身份验证凭据和连接数据添加到Adobe Commerce管理员，将Store Fulfillment Services连接到Adobe Commerce。

- **[配置 [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** — 为商店履行服务创建Adobe Commerce集成，并生成访问令牌以验证来自商店履行服务器的传入请求。

- **[配置存储履行服务的帐户凭据](#configure-store-fulfillment-account-credentials)** — 添加凭据以将Adobe Commerce连接到您的“商店履行”帐户。

>[!NOTE]
>
>请先完成连接配置并成功验证连接，然后再开始测试。

## 创建Adobe Commerce集成

要将Adobe Commerce与商店履行服务集成，您需要创建一个Commerce集成并生成可用于对来自商店履行服务器的请求进行身份验证的访问令牌。 您还必须更新Adobe Commerce [!UICONTROL Consumer Settings] 要阻止的选项 `The consumer isn't authorized to access %resources.` 响应来自Adobe Commerce的请求的错误 [!DNL Store Fulfillment] 服务。

1. 在“管理员”中，创建“商店履行”的集成。

   - 命名扩展
   - 输入您的电子邮件地址
   - 输入您的管理员帐户密码

1. 为与以下项的集成配置API资源访问权限：

   - Sales > BOPIS订单更新
   - 系统>商店履行应用程序权限

1. 通过保存和激活集成，生成用于身份验证的访问令牌。

1. 将访问令牌复制并保存到安全的加密位置。

1. 与您的客户经理合作，完成商店履行方面的配置并授权集成。

1. 启用Adobe Commerce [!UICONTROL Consumer Settings] 选项至 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - 从管理员，转到 **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - 设置 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] 选项至 **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> 集成令牌因环境而异。 如果您使用来自其他环境的源数据恢复某个环境的数据库（例如，从暂存环境恢复生产数据），请排除 `oauth_token` 表，以便在还原操作期间不会覆盖集成令牌详细信息。


## 配置存储履行帐户凭据

完成接收表单后，将为您创建一个“沃尔玛商店履行”帐户。 当以下凭据可用时，您将收到这些凭据：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常与上述配置相同）

配置和使用“商店履行”需要这些凭据。

>[!NOTE]
>
>帐户创建过程可能需要一些时间才能完成。 在等待凭据时， [查看和配置“商店履行”解决方案的其他设置](service-config-settings-overview.md).

### 添加凭据以连接到商店履行

1. 配置 [帐户凭据](enable-general.md) 用于生产和沙盒环境。

1. 从管理员，转到 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 输入为提供的帐户凭据 **[!UICONTROL Production environment]**. 所有字段都是必填字段。

1. 选择 **[!UICONTROL Save Config]**.

1. 通过选择测试连接 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>如果凭据无效，请验证您为每个环境输入的值是否正确，然后重新验证。 如果连接时仍有问题，请联系您的客户代表。
