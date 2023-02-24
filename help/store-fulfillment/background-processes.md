---
title: 后台进程配置
description: '"配置 [!DNL Store Fulfillment] 后台流程，用于将数据与履行服务同步。”'
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 后台进程配置

“商店完成”集成使用后台流程和消息队列来获得最佳性能和规模。 使用为Adobe Commerce存储构建环境 [部署变量](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 自动启动 [消息队列管理者](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

后台进程使用标准Adobe Commerce进行管理 [计划任务](https://docs.magento.com/user-guide/system/cron.html) 功能。 这些流程负责将订单和商家商店配置数据与商店履行Web服务同步。

## 管理存储完成的计划任务

从管理员中，转到 **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

查看商店履行服务的默认配置。 根据您的订单处理量和资源可用性，您可能需要调整这些设置。
