---
title: 将商务数据连接到Adobe Experience Platform
description: 了解如何将您的商务数据连接到Adobe Experience Platform。
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform {#connectaep}

在将Adobe Commerce数据连接到Adobe Experience Platform之前，必须在 [Commerce Services Connector](../landing/saas.md#organizationid). 登录并选择您的组织ID后，您可以在 **Experience Platform连接器** 页面。

1. 在管理员中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表中，选择存储视图的上下文或“范围”。

   组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. 在 **IMS组织** 字段中，您将看到与Adobe Experience Platform帐户关联的ID，该ID在 [Commerce Services Connector](../landing/saas.md#organizationid).

1. 在 **数据流ID** 字段中，粘贴您的数据流的ID [已创建](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) 在Adobe Experience Platform。

## 数据流ID与您的商务实例存储视图的关系

数据流ID允许事件从Adobe Experience Platform转发到其他AdobeDX产品，并且可以关联到您特定Adobe Commerce实例内的特定存储视图。 您还可以将多个存储视图与同一数据流ID关联。 这取决于对您的业务最有意义的内容。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 范围 | 您希望应用配置设置的特定存储视图。 |
| IMS组织（全球） | 属于购买AdobeDX产品的组织的ID。 此ID可将您的Adobe Commerce实例链接到Adobe Experience Platform。 |
| 数据流ID(Storeview) | 允许数据从Adobe Experience Platform流到其他AdobeDX产品的ID。 此ID可以与您特定Adobe Commerce实例中的特定storeView关联。 |

安装Experience Platform连接器扩展后，将创建Adobe Commerce和Adobe Experience Platform之间的链接，并指定数据流ID， [!DNL Commerce] 数据开始流向Adobe Experience Platform边缘和其他AdobeDX产品。

## 边缘商务数据

将商务数据发送到Adobe Experience Platform边缘时，您可以构建如下报表：

![Adobe Experience Manager中的商务数据](assets/aem-data-1.png)
_Adobe Experience Manager中的商务数据_
