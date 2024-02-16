---
title: 商业数据类型
description: 了解您可以收集并发送到Experience Platform的数据类型。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# 商业数据类型

此 [数据连接扩展](overview.md) 将您的Commerce数据连接到Experience Platform。 用于Experience Platform的数据分为两种行为类型：时间序列数据，它属于 **体验事件** 类并记录数据，这些数据属于 **个人资料** 类。

了解有关 [数据行为](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) 和 [类](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) Experience Platform中。

## 时间序列数据

时序数据提供记录主体直接或间接执行操作时的系统快照。 例如，当购物者浏览您网站上的产品、将产品添加到购物车、下订单时，等等。 使用将类设置为的架构将时间序列数据摄取到Experience Platform中 **体验事件**.

### 捕获的时间序列数据

请参阅 [行为事件](events.md) 和 [后台活动](events-backoffice.md) 以了解在生成时间序列事件时捕获哪些数据。

### 摄取时间序列事件数据所需的架构

了解如何 [创建架构](update-xdm.md) 可以摄取行为和后台时间序列事件数据。

## 记录数据

>[!NOTE]
>
>此功能处于测试阶段。 如果您想加入Beta计划，请发送请求至 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

记录数据提供有关主题属性的信息。 主体可以是组织，也可以是个人。 例如，您网站上的购物者创建一个帐户并生成记录数据。 使用将类设置为的架构将此数据摄取到Experience Platform **个人资料**. 您可以将该记录数据发送到Adobe的用户档案管理和分段服务： [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### 捕获的配置文件记录数据

请参阅 [客户个人资料记录数据](events-profilerecord.md) 以了解在生成配置文件记录时捕获哪些数据。

### 摄取配置文件记录数据所需的架构

了解如何 [创建架构](profile-data.md) 可以摄取个人资料记录数据的服务器。
