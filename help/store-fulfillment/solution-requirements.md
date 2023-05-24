---
title: 商店履行要求
description: 配置和入门的要求 [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Adobe Commerce的存储履行要求

以下部分详细说明了安装和启用Adobe Commerce的商店交付解决方案的技术和业务要求。

## 平台和软件版本要求

此 [!DNL Store Fulfillment] 解决方案在以下平台上向Adobe Commerce客户提供。

- 云基础架构上的Adobe Commerce (ECE)
- Adobe Commerce内部部署(EE)

Store Fillment解决方案与 *软件兼容性* 表格。

**软件兼容性**

| **软件** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Composer | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

有关详细要求，请查看Adobe Commerce [系统要求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) 在 *Adobe Commerce安装指南*.

## 商店协助应用程序要求

通过安装在移动设备上的Store Assist应用程序来管理商店提货订单的端到端流程。 这些设备（由零售商提供，或由商店员工使用其个人智能手机提供）必须符合以下要求：

**最低操作系统要求**

- Android 6
- iOS 12

**最低硬件要求**

- 1 GB RAM
- 600 MB可用磁盘空间

## 业务要求

贵企业必须满足以下最低标准才能实施商店供货解决方案：

- 仅限美国企业

- 企业对消费者(B2C)零售商、消费性包装品(CPG)制造商直接销售给消费者(D2C)，或者直接销售给消费者或小型企业的分销商

- 至少一个实体商店或仓库

- 使用Inventory management for Adobe Commerce （又称MSI）管理产品库存

- 整合商户库存的能力

- 在支持“商店履行”解决方案的所有位置都提供Wi-Fi服务：最低3 Mbps Internet速度

- 店铺和仓库联系人可以在轮班期间访问iOS或Android移动设备，可以是个人设备，也可以由商家提供

- 使用“商店履行”解决方案管理的产品必须具有包含SKU或UPC产品代码的产品属性
