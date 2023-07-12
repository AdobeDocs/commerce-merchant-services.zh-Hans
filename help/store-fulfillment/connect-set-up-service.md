---
title: 连接Store Fulfillment解决方案
description: 通过创建和授权Adobe Commerce集成，并将商店完成帐户凭据添加到Adobe Commerce服务配置，建立Adobe Commerce与Store Fulfillment解决方案之间的关系。
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 19c4d3263c22914672b38c5dc5ec9908889bb9b6
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# 连接Store Fulfillment解决方案

通过将所需的身份验证凭据和连接数据添加到Adobe Commerce管理员，将Connect Store Fulfillment Services与Adobe Commerce连接。

- **[配置 [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** — 为商店履行服务创建Adobe Commerce集成，并生成访问令牌以对来自商店履行服务器的传入请求进行身份验证。

- **[配置存储履行服务的帐户凭据](#configure-store-fulfillment-account-credentials)** — 添加凭据以将Adobe Commerce连接到应用商店履行帐户。

>[!NOTE]
>
>请先完成连接配置并成功验证连接，然后再开始测试。

## 创建Adobe Commerce集成

要将Adobe Commerce与商店履行服务集成，您需要创建一个Commerce集成并生成可用于对来自商店履行服务器的请求进行身份验证的访问令牌。 您还必须更新Adobe Commerce [!UICONTROL Consumer Settings] 要阻止的选项 `The consumer isn't authorized to access %resources.` 对来自Adobe Commerce的请求的响应错误 [!DNL Store Fulfillment] 服务。

1. 在“管理员”中，创建“商店履行”的集成。

   - 为扩展命名
   - 输入您的电子邮件地址
   - 输入您的管理员帐户密码

1. 为与以下项的集成配置API资源访问权限：

   - 销售> BOPIS订单更新
   - 系统>商店履行应用程序权限

1. 通过保存和激活集成，生成用于身份验证的访问令牌。

1. 将访问令牌复制并保存到安全的加密位置。

1. 与您的客户经理合作，完成商店履行方面的配置并授权集成。

1. 启用Adobe Commerce [!UICONTROL Consumer Settings] 选项至 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - 从管理员转到 **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - 设置 [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] 选项至 **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> 集成令牌特定于环境。 如果您使用来自其他环境的源数据恢复某个环境的数据库（例如，从暂存环境恢复生产数据），请排除 `oauth_token` 表，以便在还原操作期间不会覆盖集成令牌详细信息。


## 配置存储履行帐户凭据

在您填写完接收表单后，系统将为您创建一个“沃尔玛商店履行”帐户。 当凭据可用时，您将收到以下凭据：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常与上述配置相同）

配置和使用“存储履行”需要这些凭据。

>[!NOTE]
>
>帐户创建过程可能需要一些时间才能完成。 在等待凭据时， [查看和配置“商店履行”解决方案的其他设置](service-config-settings-overview.md).

### 添加凭据以连接到商店履行

1. 配置 [帐户凭据](enable-general.md) 用于生产和沙盒环境。

1. 从管理员转到 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 输入为提供的帐户凭据 **[!UICONTROL Production environment]**. 所有字段均为必填字段。

1. 选择 **[!UICONTROL Save Config]**.

1. 通过选择测试连接 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>如果凭据无效，请验证您为每个环境输入的值是否正确，然后重新验证。 如果您在连接时仍然遇到问题，请联系您的客户代表。
