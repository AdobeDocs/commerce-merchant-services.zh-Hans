---
title: 商店功能的配置概述
description: 了解可用于自定义“商店履行”解决方案提供的扩展履行功能的管理员配置设置类型，以及指向完成配置说明的链接。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Configuration
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 商店功能的配置概述

在“Adobe Commerce管理员”中，Walmart Commerce Technologies的“商店履行服务”的配置设置按类型进行分类。

**按类型存储履行配置设置**

| **类型** | **描述** | **API可配置** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [常规配置](enable-general.md) | 为Store Fulfillment解决方案设置的常规集成、其活动功能以及用于连接履行服务的凭据。 | 否 |
| [销售电子邮件配置](sales-emails.md) | 为登记入住过程中发送的客户通知设置其他电子邮件模板。 | 否 |
| [商户存储配置](merchant-store-configuration.md) | 将增强的Inventory management源设置为商户商店。 | 是 |
| [产品库存管理](product-stock.md) | 配置可供客户使用的商家股票消息传递和功能。 | 是 |
| [Inventory management源传输](inventory-stock-transfer.md) | 设置新库存，将库存转移出默认库存。 | 是 |
| [多个网站/范围配置](multi-site-and-scope-config.md) | 为多个网站/商店范围配置库存和投放方法。 | 否 |
| [后台进程系统配置](background-processes.md) | 配置用于与履行服务同步数据的后台进程的计划。 | 否 |
| [存储位置和映射设置](store-location-map-provider-setup.md) | 配置使用距离提供商搜索零售商店并在SLS地图中显示此信息的功能 | 是 |
| [签入体验设置](check-in-experience-setup.md) | 配置在检入过程中可用的汽车颜色和汽车制造选项 | 是 |
| [用户设置](user-setup.md) | 管理使用Store Assist应用程序的商店关联的用户帐户、角色和权限。 范围。 | 是 |
| [应用程序设置](app-setup.md) | 查看完成载入流程所需的应用商店助手应用程序的可用配置。 无法从Adobe Commerce管理员配置这些设置。 | 是 |

## 使用配置引用

通过在每个设置类型中选择类型名称来查看配置引用 _按类型存储履行配置设置_ 表格。

在每种类型的配置参考中，配置详细信息都显示在具有以下列标题的表中：

- **字段** 是指要配置的字段的名称

- **描述** 提供了有关字段用途和行为的重要详细信息

- **范围** 指示设置的Adobe Commerce配置范围（全局、网站、商店）

- **必填** 值指示是否必须在字段上设置值

如需技术参考，您还可以找到每个字段的内部配置路径。
