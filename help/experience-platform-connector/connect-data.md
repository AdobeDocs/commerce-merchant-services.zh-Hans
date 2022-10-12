---
title: 将商务数据连接到Adobe Experience Platform
description: 了解如何将您的商务数据连接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform {#connectaep}

要将Adobe Commerce实例连接到Adobe Experience Platform，您必须提供组织ID和数据流ID。

![Experience Platform连接器配置](assets/epc-config.png)

1. 登录到您的Adobe帐户(位于 [Commerce Services Connector](../landing/saas.md#organizationid) ，然后选择您的组织ID。

1. 在管理员中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表中，将上下文设置为 **网站**.

1. 在 **组织ID** 字段中，您将看到与Adobe Experience Platform帐户关联的ID，该ID在 [Commerce Services Connector](../landing/saas.md#organizationid). 组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. 在 **数据流ID** 字段中，粘贴您的数据流的ID [已创建](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) 在Adobe Experience Platform。

   >[!NOTE]
   >
   >数据流ID的范围必须在网站级别或更高级别设置。 在该级别，层级中的每个网站都使用相同的数据流ID。 不能在存储视图级别设置数据流ID范围。

1. （可选）如果您没有将AEP Web SDK部署到站点，请将此字段留空，Experience Platform连接器将为您部署一个AEP Web SDK。 否则，请添加AEP Web SDK的名称。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 范围 | 您希望应用配置设置的特定网站。 |
| 组织ID（全局） | 属于购买AdobeDX产品的组织的ID。 此ID可将您的Adobe Commerce实例链接到Adobe Experience Platform。 |
| 数据流ID（网站） | 允许数据从Adobe Experience Platform流到其他AdobeDX产品的ID。 此ID必须与您特定Adobe Commerce实例中的特定网站关联。 |
| AEP Web SDK名称（全局） | 如果您的站点尚未部署AEP Web SDK，请将此字段留空，Experience Platform连接器会为您部署一个AEP Web SDK。 如果您已将AEP Web SDK部署到站点，请在此字段中指定该SDK的名称。 这允许Storefront事件收集器和Storefront事件SDK使用您的AEP Web SDK，而不是Experience Platform连接器部署的版本。 |

安装了Experience Platform连接器扩展、创建了Adobe Commerce和Adobe Experience Platform之间的链接，并指定了数据流ID后，商务数据开始流向Adobe Experience Platform边缘和其他AdobeDX产品。

>[!NOTE]
>
> 数据从边缘流向其他AdobeDX产品所花费的时间可能会有所不同。

## 边缘商务数据

将商务数据发送到Adobe Experience Platform边缘时，您可以构建如下报表：

![Adobe Experience Manager中的商务数据](assets/aem-data-1.png)
_Adobe Experience Manager中的商务数据_
