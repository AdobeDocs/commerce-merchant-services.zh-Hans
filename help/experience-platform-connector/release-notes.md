---
title: 发行说明
description: Adobe Commerce中的Adobe Experience Platform连接器的最新发行信息。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 9dcb5a38f6ec2ed13a07d80b6a9d5a64efcc13ee
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---

# 发行说明

这些发行说明包含对Experience Platform连接器的更新，其中包括：

* ![新](../assets/new.svg)  — 新增功能
* ![修复](../assets/fix.svg)  — 修复和改进
* ![错误](../assets/bug.svg)  — 已知问题

有关Experience Platform连接器使用的扩展的功能更改和修复，请参阅 **支持的服务更新**.

参见 [即将发行的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 了解发布时间表和支持。

请参阅开发人员文档，以访问 [了解产品兼容性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 支持的服务更新

以下发行说明介绍了与Experience Platform连接器使用的扩展相关的功能更改和修复。

+++支持的服务更新

_2023年6月10日_

* ![修复](../assets/fix.svg)  — 修复了以下情况下出现的问题： `orderId` 由于商务订单标识符中的前缀，无法在上下文中传递。
* ![修复](../assets/fix.svg)  — 更新了内容安全策略配置。

_2023年3月30日_

* ![新](../assets/new.svg)  — 添加了一个名为的新扩展 `data-services-b2b` 包括 [申请列表事件](events.md#b2b-events) B2B商家。
* ![新](../assets/new.svg)  — 添加了 `uniqueIdentifier` 字段至 [搜索](events.md#search-events) 事件。 此新字段允许商家交叉引用与哪些搜索响应对应的搜索请求。

_2022年10月12日_

* ![新](../assets/new.svg)  — 添加了两个 [店面活动](events.md)： `openCart` 和 `removeFromCart` 到Adobe Commerce店面事件SDK和收集器。
* ![新](../assets/new.svg)  — 增加了对 [AEM店面](overview.md#aem-support).

+++

## 2.3.0

_2023年6月27日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 增加了以下功能： [关闭发送店面活动](connect-data.md#data-collection) 到Experience Platform。
* ![修复](../assets/fix.svg)  — 更新了内容安全策略配置。
* ![修复](../assets/fix.svg)  — 修复了对Commerce 2.4.7版本上的后台事件的支持。
* ![新](../assets/new.svg)  — 添加了有关在保存对Experience Platform连接器表单所做的更改时缓存失效的通知消息。


## 3.0.0-beta1（仅限内部）

_2023年6月13日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — （测试版）添加了以下功能： [发送历史订单](connect-data.md#beta-send-historical-order-data) Experience Platform的数据和状态。 此功能仅适用于Beta版用户。 您可以通过向以下地址发送电子邮件来加入测试版： [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

## 2.2.0

_2023年3月30日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 捆绑了 `commerce-data-export` 和 `saas-export` 与的依赖关系 `experience-platform-connector` 扩展。 以前，必须单独安装这些依赖项。 这些依赖项以及商家配置使服务器端处理能够 [后台活动](events.md#back-office-events).
* ![新](../assets/new.svg)  — 添加了名为的新后台事件 [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023年2月28日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 为所有Experience Platform连接器扩展添加了对PHP 8.2的支持。

## 2.1.0

_2023年1月17日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 已更新 [Experience Platform连接器管理员](connect-data.md) 以便您指定自己的AEP Web SDK (alloy)。
* ![修复](../assets/fix.svg) 更改为使用 `identityMap` 而不是 `personID` 为推送到边缘的任何数据设置主标识时。

## 2.0.1

_2022年11月10日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![已修复的问题](../assets/fix.svg)  — 现在，Adobe Experience Platform上下文仅在成功加载店面事件收集器和店面事件SDK后设置。

## 2.0.0

_2022年10月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 添加了以下情况下指定您自己的AEP Web SDK的功能 [连接](connect-data.md) 将您的Adobe Commerce实例添加到Experience Platform。
* ![修复](../assets/fix.svg)  — 更新了数据流范围要求，以便数据流ID的范围必须限定在网站中而不是存储审阅。

## 1.0.0

_2022年8月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![新](../assets/new.svg)  — 正式发布。
