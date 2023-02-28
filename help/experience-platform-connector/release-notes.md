---
title: 发行说明
description: 来自Adobe Commerce的Adobe Experience Platform Connector的最新发行信息。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 57d0d0604e871a0d8a76bfd2c006250b55f0eeb1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 发行说明

以下发行说明包含对Experience Platform连接器的更新，其中包括：

* ![新建](../assets/new.svg)  — 新增功能
* ![修复](../assets/fix.svg)  — 修复和改进功能
* ![错误](../assets/bug.svg)  — 已知问题

有关与Experience Platform连接器使用的扩展相关的功能更改和修复，请参阅 **支持的服务更新**.

请参阅 [即将发行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) 了解发行计划和支持。

请参阅 [可用性](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) 以了解产品兼容性。

## 支持的服务更新

以下发行说明介绍了与Experience Platform连接器使用的扩展相关的功能更改和修复。

+++支持的服务更新

_2022年10月12日_

* ![新建](../assets/new.svg)  — 添加了两个 [storefront事件](events.md): `openCart` 和 `removeFromCart` 到Adobe Commerce Storefront Events SDK和收集器
* ![新建](../assets/new.svg)  — 添加了对 [AEM storefront](overview.md#aem-support)

+++

## 2.1.1

_2023年2月28日_

* ![新建](../assets/new.svg)  — 为所有Experience Platform连接器模块添加了对PHP 8.2的支持

## 2.1.0

_2023年1月17日_

* ![新建](../assets/new.svg)  — 更新了 [Experience Platform连接器管理](connect-data.md) 以便您可以指定自己的AEP Web SDK(alloy)。 此外，还为注册了后台测试版计划的商家添加了一个选项，以便向 [后台事件数据](connect-data.md#data-collection) 到边缘。 这些事件包含 [订单状态信息](events.md#beta-order-status-events) 关于订单，例如订单被下达、取消、退还或发运。 如果您想参加后台测试版计划，请联系 [drios@adobe.com](mailto:drios@adobe.com).
* ![修复](../assets/fix.svg) 已更改为使用 `identityMap` 而不是 `personID` 为推送到边缘的任何数据设置主标识时。

## 2.0.1

_2022年11月10日_

* ![修复的问题](../assets/fix.svg)  — 现在，仅在成功加载Storefront事件收集器和Storefront事件SDK后，才设置Adobe Experience Platform上下文。

## 2.0.0

_2022年10月12日_

* ![新建](../assets/new.svg)  — 添加了在以下情况下指定您自己的AEP Web SDK的功能： [连接](connect-data.md) 您的Adobe Commerce实例到Experience Platform
* ![修复](../assets/fix.svg)  — 更新了数据流范围要求，以便数据流ID的范围必须限于网站，而不是storeview

## 1.0.0

_2022年8月9日_

* ![新建](../assets/new.svg)  — 正式发布

## 文档

要了解更多信息：

* [Adobe Commerce开发人员文档](https://devdocs.magento.com/)
* [Adobe Commerce用户指南](https://docs.magento.com/user-guide/)
