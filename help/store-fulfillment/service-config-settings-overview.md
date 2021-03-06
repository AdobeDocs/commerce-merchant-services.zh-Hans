---
title: 存储实现的配置概述
description: 了解可用于自定义商店履行解决方案提供的扩展履行功能的管理员配置设置类型，以及有关完成配置的说明的链接。
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# 存储实现的配置概述

在Adobe Commerce管理员中，由Walmart Commerce Technologies划分的“商店履行服务”的配置设置按类型进行分类。

**按类型存储履行配置设置**

| **类型** | **描述** | **可配置API** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [常规配置](enable-general.md) | 为“商店履行”解决方案、其活动功能和用于连接到履行服务的凭据设置的常规集成。 | 否 |
| [销售电子邮件配置](sales-emails.md) | 为签入过程中发送的客户通知设置其他电子邮件模板。 | 否 |
| [商户商店配置](merchant-store-configuration.md) | 将增强的Inventory management源设置为商店。 | 是 |
| [产品库存管理](product-stock.md) | 配置可供客户使用的商户股票报文传送和功能。 | 是 |
| [Inventory management源传输](inventory-stock-transfer.md) | 设置新库存，从默认库存中转移库存。 | 是 |
| [多个网站/范围配置](multi-site-and-scope-config.md) | 为多个网站/商店范围配置库存和交付方法。 | 否 |
| [后台进程系统配置](background-processes.md) | 为与履行服务同步数据时使用的后台进程配置计划。 | 否 |
| [存储位置和映射设置](store-location-map-provider-setup.md) | 配置使用距离提供程序搜索零售商店并在SLS映射中显示此信息的功能 | 是 |
| [签入体验设置](check-in-experience-setup.md) | 配置在签入过程中可用的车色和车牌选项 | 是 |
| [用户设置](user-setup.md) | 管理使用Store Assist应用程序的商店关联的用户帐户、角色和权限。 范围。 | 是 |
| [应用程序设置](app-setup.md) | 查看完成载入过程所需的商店辅助应用程序的可用配置。 无法从Adobe Commerce管理员配置这些设置。 | 是 |

## 使用配置参考

通过在 _按类型存储履行配置设置_ 表。

在每种类型的配置引用中，配置详细信息都显示在具有以下列标题的表中：

- **字段** 是指要配置的字段的名称

- **描述** 提供有关字段用途和行为的重要详细信息

- **范围** 指示设置的Adobe Commerce配置范围（全局、网站、商店）

- **必需** 值指示是否必须在字段中设置值

有关技术参考，您还可以找到每个字段的内部配置路径。
