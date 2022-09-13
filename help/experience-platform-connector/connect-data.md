---
title: 将商务数据连接到Adobe Experience Platform
description: 了解如何将您的商务数据连接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform {#connectaep}

要将Adobe Commerce实例连接到Adobe Experience Platform，您必须提供组织ID和数据流ID。

![Experience Platform连接器配置](assets/epc-config.png)

1. 登录到您的Adobe帐户(位于 [Commerce Services Connector](../landing/saas.md#organizationid) ，然后选择您的组织ID。

1. 在管理员中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表中，选择存储视图的上下文或“范围”。

1. 在 **组织ID** 字段中，您将看到与Adobe Experience Platform帐户关联的ID，该ID在 [Commerce Services Connector](../landing/saas.md#organizationid). 组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. 在 **数据流ID** 字段中，粘贴您的数据流的ID [已创建](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 在Adobe Experience Platform。

## 数据流ID与您的商务实例存储视图的关系

数据流ID支持将事件从Adobe Experience Platform转发到其他AdobeDX产品，并且可以关联到您特定Adobe Commerce实例内的特定存储视图。 您还可以将多个存储视图与同一数据流ID关联。 这取决于对您的业务最有意义的内容。 [了解更多](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) 关于事件转发。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 范围 | 您希望应用配置设置的特定商店视图。 |
| 组织ID（全局） | 属于购买AdobeDX产品的组织的ID。 此ID可将您的Adobe Commerce实例链接到Adobe Experience Platform。 |
| 数据流ID（存储视图） | 允许数据从Adobe Experience Platform流到其他AdobeDX产品的ID。 此ID可以与您特定Adobe Commerce实例中的特定商店视图关联。 |

安装了Experience Platform连接器扩展、创建了Adobe Commerce和Adobe Experience Platform之间的链接，并指定了数据流ID后，商务数据开始流向Adobe Experience Platform边缘和其他AdobeDX产品。

>[!NOTE]
>
> 数据从边缘流向其他AdobeDX产品所花费的时间可能会有所不同。

## 边缘商务数据

将商务数据发送到Adobe Experience Platform边缘时，您可以构建如下报表：

![Adobe Experience Manager中的商务数据](assets/aem-data-1.png)
_Adobe Experience Manager中的商务数据_
