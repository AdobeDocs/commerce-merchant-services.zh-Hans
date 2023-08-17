---
title: Store Fulfillment Services入门概述
description: ’[!DNL Live Search] 载入流程、系统要求、边界和限制。”
role: Admin, Leader
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 商店功能的入门概述

开始使用 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 设置、配置和启用以下组件：

- **商店履单扩展** — 在Adobe Commerce实例上安装并配置此第三方扩展。 安装后，您可以从管理员处配置和管理Store Fulfillment解决方案以支持 [!DNL buys online, pickup in store] (BOPIS)方案。

  ![[!DNL Store Fulfillment Service] 管理员视图中的配置](assets/store-fulfillment-admin-home.png)

- **商店履行帐户** — 在启用过程中，客户经理会创建您的Store Fulfillment帐户，并为您提供帐户信息和凭据。 启用Adobe Commerce与“商店履行”解决方案之间的连接需要这些凭据。

- **商店协助应用程序** — 为商店关联提供端到端商店履行工作流，以管理来自移动设备的BOPIS订单。 Store Associates可以下载并安装沃尔玛 [!DNL Store Assist] 适用于iOS和Android™设备。 应用程序载入流程由沃尔玛商业技术客户中心作为单独流程管理。 但是， [一些应用程序配置设置](user-setup.md) 是从Adobe Commerce管理员处完成的。

  | 商店协助应用程序 — 入门视图 | 应用商店助手应用程序 — 模块视图 |
  |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
  | ![[!DNL Store Assist App Getting Started] 在移动设备上查看](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] 在移动设备上](assets/store-assist-orders-small.png) |

## 配置步骤

- **注册[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]** — 完成注册表单，日期： [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)，或联系Adobe Commerce客户经理寻求帮助。

- **启动“商店履行”的配置请求** — 填写客户经理提供的录取表单，以提供开始设置过程所需的信息。

- **获取商店履行帐户凭据** — 为您创建Store Fulfillment帐户后，您将收到将Store Fulfillment解决方案与Adobe Commerce集成所需的凭据。

- **[下载源代码以安装 [!DNL Store Fulfillment] 扩展](install.md)**

## 载入步骤

1. [安装适用于Adobe Commerce的Store Fulfillment扩展](install.md).

1. 来自管理员， [启用解决方案](enable-general.md).

1. [从Adobe Commerce管理员配置“商店履行”扩展](service-config-settings-overview.md).

1. [连接 [!DNL Store Fulfillment] 使用提供给您的商店履行凭据的服务](connect-set-up-service.md).

1. [为Store Assist应用程序创建用户和角色](user-setup.md).

1. [下载沃尔玛 [!DNL Store Assist] 将应用程序安装到所需的设备。 该应用程序在Apple应用程序(iOS)和Google Play (Android™)上均可用](app-setup.md) 商店。

在成功安装、配置、完成载入并有权访问 [!DNL Store Assist] 应用程序，您可以 [开始创建订单并进行测试](test-and-deploy.md).
