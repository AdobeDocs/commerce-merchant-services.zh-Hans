---
title: 存储完成要求
description: 配置和入门要求 [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Adobe Commerce的存储实现要求

以下部分详细介绍了安装和启用Adobe Commerce商店完成解决方案的技术和业务需求。

## 平台和软件版本要求

的 [!DNL Store Fulfillment] 解决方案可在以下平台上向Adobe Commerce客户提供。

- Adobe Commerce云基础架构(ECE)
- Adobe Commerce本地(EE)

“商店履行”解决方案与 *软件兼容性* 表。

**软件兼容性**

| **软件** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| 编辑器 | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

有关详细要求，请参阅Adobe Commerce [系统要求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) 在 *Adobe Commerce安装指南*.

## 商店协助应用程序要求

管理商店提货单的端到端流程通过移动设备上安装的商店辅助应用程序进行管理。 这些设备（由零售商提供或由使用个人智能手机的商店员工提供）必须满足以下要求：

**最低操作系统要求**

- Android 6
- iOS 12

**最低硬件要求**

- 1 GB RAM
- 600 MB可用磁盘空间

## 业务要求

您的企业必须满足以下最低标准才能实施商店实施解决方案：

- 仅限美国企业

- 企业对消费者(B2C)零售商、消费者包装产品(CPG)制造商直接向消费者销售(D2C)，或直接向消费者或小型企业销售的分销商

- 至少一个实体商店或仓库

- 使用Inventory management for Adobe Commerce（即MSI）管理您的产品清单

- 将商户库存集中的能力

- 在支持“商店履行”解决方案的所有位置存储Wi-Fi可用性：最低Internet速度为3 Mbps

- 商店和仓库关联商可以在移动期间访问iOS或Android移动设备（无论是个人设备还是商家提供的设备）

- 使用商店履行解决方案管理的产品必须具有包含SKU或UPC产品代码的产品属性
