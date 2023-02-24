---
title: 连接商店履行解决方案
description: 通过创建和授权Adobe Commerce集成，并将存储履行帐户凭据添加到Adobe Commerce服务配置，在Adobe Commerce与存储履行解决方案之间建立连接。
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 连接商店履行解决方案

通过向Adobe Commerce管理员添加所需的身份验证凭据和连接数据，将应用商店履行服务与Adobe Commerce连接。

- **[配置 [!DNL Commerce integration settings]](#create-the-commerce-integration)** — 为存储履行服务创建Adobe Commerce集成，并生成访问令牌以验证来自存储履行服务器的传入请求。

- **[为存储履行服务配置帐户凭据](#configure-store-fulfillment-account-credentials)** — 添加凭据将Adobe Commerce连接到您的商店履行帐户。

>[!NOTE]
>
>在开始测试之前，请完成连接配置并成功验证连接。

## 创建Adobe Commerce集成

要将Adobe Commerce与商店履行服务集成，您需要创建商务集成并生成访问令牌，以用于验证来自商店履行服务器的请求。

1. 从管理员中，创建用于商店履行的集成。

   - 将扩展命名为
   - 输入您的电子邮件地址
   - 输入管理员帐户密码

1. 配置 [!UICONTROL API Resource Access permissions] 对于集成 — 选择 `[!UICONTROL All]`

1. 通过保存和激活集成，生成用于身份验证的访问令牌。

1. 将访问令牌复制并保存到安全的加密位置。

1. 与您的客户经理合作，完成商店履行端的配置并授权集成。


>[!NOTE]
>
>有关详细说明，请参阅 [集成](https://docs.magento.com/user-guide/system/integrations.html) 在 _Adobe Commerce用户指南_.

## 配置存储履行帐户凭据

完成入伙表后，将为您创建一个沃尔玛商店履行帐户。 当凭据可用时，您将收到以下凭据：

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常与上述配置相同）

配置和使用“商店履行”时需要这些凭据。

>[!NOTE]
>
>帐户创建过程可能需要一些时间才能完成。 等待凭据时， [查看并配置商店履行解决方案的其他设置](service-config-settings-overview.md).

### 添加凭据以连接到存储履行

1. 配置 [帐户凭据](enable-general.md) （用于生产和沙盒环境）。

1. 从管理员中，转到 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 输入为 **[!UICONTROL Production environment]**. 所有字段均为必填字段。

1. 选择 **[!UICONTROL Save Config]**.

1. 通过选择 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>如果凭据无效，请验证您为每个环境输入了正确的值并重新验证。 如果在连接时仍然遇到问题，请联系您的客服专员。
