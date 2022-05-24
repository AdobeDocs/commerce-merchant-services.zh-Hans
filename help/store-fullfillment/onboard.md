---
title: 板载“[!DNL Store Fulfillment]"
description: 将您的Commerce实例连接到 [!DNL Store Fulfillment Manager] 服务，方法是完成一些入门步骤。
role: User, Admin
level: Intermediate
source-git-commit: 24639b75d3c629856fbb8fc74e7eb072d4197815
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---


# 沃尔玛技术公司实现门店销售

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

## 先决条件

* **商务帐户信息** — 下载和安装 [!DNL Channel Manager] 需要 [商务帐户](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}。 您需要具有以下权限的帐户ID和凭据：拥有 [!DNL Adobe Commerce] 或 [!DNL Magento Open Source] 实例。

* 对于 [!DNL Adobe Commerce] 在云基础架构项目上，软件安装程序必须具有以下访问 [!DNL Commerce] 实例：

   * 超级用户对云项目的访问权限
   * 对特定环境的管理员访问权限
   * 安 [!DNL Adobe Commerce] 或 [!DNL Magento Open Source] 具有访问编辑器存储库权限的帐户

      请参阅 [管理用户访问权限](https://devdocs.magento.com/cloud/project/user-admin.html).

* **通过Walmart Technologies软件存档访问商店履行，以在您的Adobe Commerce实例上安装商店履行解决方案** — 您的客户客户代表可以访问扩展安装文件。

* **使用编辑器和[!DNL Commerce CLI]**  — 请参阅 [常规CLI安装](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;}以了解有关使用这些工具在上安装和配置扩展的信息 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 平台。

* [!DNL Inventory Management] Adobe Commerce和Magento Open Source的扩展

   您必须在Adobe Commerce和Inventory management实例上安装并启用Magento Open Source扩展。 通常，此扩展默认安装并在Adobe Commerce和Magento Open Source2.3.x及更高版本上启用。 有关更多信息，请参阅 [安装Inventory management](https://devdocs.magento.com/extensions/inventory-management/) ，位于Adobe Commerce开发人员文档中。

## 要求

Adobe Commerce和Magento Open Source客户可以使用商店履行解决方案。 安装、部署和使用解决方案必须满足以下系统和业务要求。

### 系统要求

Walmart Technologies的“商店完成”扩展已测试与以下软件版本的兼容性。

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

* 美国企业

* B2C零售商、销售D2C的CPG制造商，或销售D2C或面向小型企业的分销商

* 至少一个实体商店或仓库

* 使用Inventory management for Commerce（以前为MSI）管理您的产品清单

* 将商户库存集中的能力

* 将Wi-Fi可用性存储在支持“商店履行”解决方案的所有位置

* 商店和仓库关联商可以在移动期间访问iOS或Android移动设备（无论是个人设备还是商家提供的设备）

* 使用商店履行解决方案管理的产品必须具有包含SKU或UPC产品的产品属性。

### 支持的平台

* Adobe Commerce on Cloud(ECE):2.4.x
* Adobe Commerce on premise(EE):2.4.x
* Magento Open Source2.4.x
