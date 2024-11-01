---
title: 后台进程配置
description: “为用于与履行服务同步数据的 [!DNL Store Fulfillment] 后台进程配置计划。”
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# 后台进程配置

Store Fulfillment集成使用后台流程和报文队列以获得最佳性能和规模。 使用自动启动[消息队列运行者](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework)的[部署变量](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner)为您的Adobe Commerce存储区构建环境。

后台进程使用标准Adobe Commerce [计划任务](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron)功能进行管理。 这些流程负责将订单和商家商店配置数据与商店履行Web服务同步。

## 管理“商店履行”的计划任务

从管理员转到&#x200B;**[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**。

查看“商店履行”服务的默认配置。 您可以根据订单处理量和资源可用性自定义这些设置。
