---
title: 入门概述
description: “连接您的 [!DNL Commerce] 实例 [!DNL Store Fulfillment Manager] 服务，只需完成几个入门步骤。”
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# 入门概述

板载商店实施，方法是在您的商务实例上安装扩展并配置API连接。 这些连接支持在您的商务实例、用于库存管理的第三方系统和商店辅助应用程序之间进行通信和数据同步。

完成载入后，请通过商务管理员配置和管理解决方案

![[!DNL Store Fulfillment Service] 管理视图中的配置](assets/store-fulfillment-admin-home.png)

## 入门概述

1. 安装Walmart Technologies for Adobe Commerce的Store Fulfillment扩展。

1. 从管理员处，启用解决方案并完成集成及其活动功能的常规配置，并完成入门入门单以连接到实施服务。

1. 配置投放方法。

1. 将源设置为物理商店，并在目录中配置产品。

1. 选择并配置电子邮件模板，以管理用于在线购买、店内装货(BOPI)交易的客户通信。

1. 为Store Assist应用程序创建用户和角色。

1. 配置后台进程的计划，以将数据同步到履行服务。

## 要求

您必须满足以下要求才能安装、部署和使用解决方案。

* **商务帐户信息** — 安装 [!DNL Channel Manager] 需要 [商务帐户](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}。 您需要具有以下权限的帐户ID和凭据：拥有 [!DNL Adobe Commerce] 实例。

* 对于 [!DNL Adobe Commerce] 在云基础架构项目上，软件安装程序必须拥有对云项目的管理员访问权限。 请参阅 [管理用户访问权限](https://devdocs.magento.com/cloud/project/user-admin.html).

* **通过Walmart Technologies软件存档（.zip文件）访问商店履行，以安装商店履行解决方案** — 在载入和启用过程中，您的客户客户代表将提供安装文件的下载访问权限。

* **使用编辑器和[!DNL Commerce CLI]** — 请参阅 [常规CLI安装](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;}以了解有关使用这些工具在上安装和配置扩展的信息 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 平台。

* [!DNL Inventory Management] Adobe Commerce和Magento Open Source的扩展

   您必须在Adobe Commerce和Inventory management实例上安装并启用Magento Open Source扩展。 通常，此扩展会在Adobe Commerce 2.3.x及更高版本上默认安装并启用。 有关更多信息，请参阅 [安装Inventory management](https://devdocs.magento.com/extensions/inventory-management/) ，位于Adobe Commerce开发人员文档中。

## 平台和版本要求

的 [!DNL Store Fulfillment] 解决方案可在以下平台上向Adobe Commerce客户提供。

* Adobe Commerce云基础架构(ECE)
* Adobe Commerce本地(EE)

“商店履行”解决方案与以下软件版本兼容。

**软件兼容性**

| **软件** | **最低版本** | **最大版本** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| 编辑器 | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

有关详细要求，请参阅Adobe Commerce [系统要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) （位于开发人员文档中）。

### 业务要求

您的企业必须满足以下最低标准才能实施商店完成解决方案。

* 仅限美国企业

* B2C零售商、销售D2C的CPG制造商，或销售D2C或面向小型企业的分销商

* 至少一个实体商店或仓库

* 使用Inventory management for Adobe Commerce(MSI)管理您的产品清单

* 将商户库存集中的能力

* 将Wi-Fi可用性存储在支持“商店履行”解决方案的所有位置

* 商店和仓库关联商可以在移动期间访问iOS或Android移动设备（无论是个人设备还是商家提供的设备）

* 使用商店履行解决方案管理的产品必须具有包含SKU或UPC产品代码的产品属性
