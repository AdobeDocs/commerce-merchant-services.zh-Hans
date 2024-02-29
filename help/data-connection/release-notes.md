---
title: 发行说明
description: 的最新发行信息 [!DNL Data Connection] 来自Adobe Commerce的扩展。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# 发行说明

>[!IMPORTANT]
>
>Experience Platform连接器已重命名为 [!DNL Data Connection].

本发行说明包含对以下项的更新： [!DNL Data Connection] 扩展并包括：

![新建](../assets/new.svg)  — 新增功能
![修复](../assets/fix.svg)  — 修复和改进功能
![错误](../assets/bug.svg)  — 已知问题

与使用的扩展相关的功能更改和修复 [!DNL Data Connection] 扩展，请参见 **支持的服务更新**.

请参阅 [即将发布的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 了解发布计划和支持。

请参阅开发人员文档以 [了解哪些商务版本支持此模块](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 支持的服务更新

以下发行说明介绍了与使用的扩展相关的功能更改和修复。 [!DNL Data Connection] 扩展。

+++支持的服务更新

_2024年1月24日_

![新建](../assets/new.svg)  — 已更新 `data-services-b2b` 扩展，以包含名为的新申请事件 [deleteRequisitionList](events.md#deleterequisitionlist) B2B商家。

_2023年11月16_

![修复](../assets/fix.svg)  — 修复了在您下具有多个配送地址的订单时错误消息显示的问题。
![修复](../assets/fix.svg)  — 修复了 [productPageView](events.md#productpageview) 事件其中 `productListItems.priceTotal` 在商店视图上切换货币后，事件字段未转换价格。
![修复](../assets/fix.svg)  — 修复了 `productListItems` 商家切换商店视图时货币代码未更新的事件字段。

_2023年10月10日_

![新建](../assets/new.svg)  — 添加了新订单状态事件： [已开票订单](events-backoffice.md#orderinvoiced)， [已起动订单物料退货](events-backoffice.md#orderitemsreturninitiated)、和 [订单物料退货已完成](events-backoffice.md#orderitemreturncompleted).
![修复](../assets/fix.svg)  — 修复了在刷新缓存后，货币配置更改未反映在事件中的问题。
![修复](../assets/fix.svg)  — 修复了在启用异步订单放置后未显示订单确认消息的错误。
![新建](../assets/new.svg)  — 向添加了数据 [addToRequisitionList](events.md#addtorequisitionlist) “类别”视图页面上的简单产品事件。
![修复](../assets/fix.svg)  — 修复了 `selectedOptions` 中的数据 [addToRequisitionList](events.md#addtorequisitionlist) 从订单确认页面添加产品时的事件。
![新建](../assets/new.svg)  — 已将产品数据添加到 [addToRequisitionList](events.md#addtorequisitionlist) 将产品从“类别”视图页面添加到申请列表时的事件。
![新建](../assets/new.svg)  — 已添加 [addToRequisitionList](events.md#addtorequisitionlist) 将可配置产品从“产品视图”页面添加到申请列表时的事件。
![新建](../assets/new.svg)  — 已添加 [addToRequisitionList](events.md#addtorequisitionlist) 和 [removeFromRequisitionList](events.md#removefromrequisitionlist) 从申请列表中增加和/或减少产品数量时的事件。

_2023年6月10日_

![修复](../assets/fix.svg)  — 修复了以下情况下出现的问题 `orderId` 由于商务订单标识符中的前缀，未在上下文中传递。
![修复](../assets/fix.svg)  — 更新了内容安全策略配置。

_2023年3月30日_

![新建](../assets/new.svg)  — 添加了一个扩展，名为 `data-services-b2b` 包括 [申购单列表事件](events.md#b2b-events) B2B商家。
![新建](../assets/new.svg)  — 添加了 `uniqueIdentifier` 字段至 [搜索](events.md#search-events) 事件。 此新字段允许商家交叉引用搜索请求和搜索响应。

_2022年10月12日_

![新建](../assets/new.svg)  — 添加了两个 [店面活动](events.md)， `openCart` 和 `removeFromCart`，转到Adobe Commerce店面事件SDK和收集器。
![新建](../assets/new.svg)  — 增加了对 [AEM店面](overview.md#aem-support).

+++

## 3.2.0-beta1

_2024年2月16日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)  — 如果您正在参与Beta测试，请确保您的 `composer.json` 文件在根级别具有以下内容： ` "minimum-stability": "beta"`.
![新建](../assets/new.svg)  — 添加了 [添加自定义属性](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![新建](../assets/new.svg)  — 添加了 [收集和发送配置文件记录](connect-data.md#send-customer-profile-data) 和要Experience Platform的数据。

## 3.1.0

_2023年11月16_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) -Experience Platform连接器已重命名为 [!DNL Data Connection].
![修复](../assets/new.svg)  — 添加了在Adobe IMS无法生成访问令牌时记录错误响应的功能。
![修复](../assets/new.svg)  — 如果您尝试同步历史订单但未指定帐户凭据，则添加了通知消息。

## 3.0.0

_2023年10月10日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

这是一个主版本发行版本。 [编辑](install.md#update-the-data-connection) 项目的根composer.json文件。

![新建](../assets/new.svg)  — 正式发布 [发送历史订单](connect-data.md#send-historical-order-data) Experience Platform的数据和状态。
![新建](../assets/new.svg)  — 当您使用OAuth 2.0时 [配置](connect-data.md#connect-commerce-data-to-adobe-experience-platform) 该 [!DNL Data Connection] 扩展。
![新建](../assets/new.svg)  — 停止支持Adobe Commerce 2.4.3。

## 2.3.0

_2023年6月27日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 添加了 [关闭发送店面活动](connect-data.md#data-collection) 到Experience Platform。
![修复](../assets/fix.svg)  — 更新了内容安全策略配置。
![修复](../assets/fix.svg)  — 修复了对Commerce 2.4.7版本上的后台事件的支持。
![新建](../assets/new.svg)  — 添加了关于将更改保存到时缓存失效的通知消息 [!DNL Data Connection] 扩展表单。


## 3.0.0-beta1（仅限内部）

_2023年6月13日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — （测试版）添加了以下功能 [发送历史订单](connect-data.md#beta-send-historical-order-data) Experience Platform的数据和状态。

## 2.2.0

_2023年3月30日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 捆绑 `commerce-data-export` 和 `saas-export` 与的依赖关系 `experience-platform-connector` 扩展。 以前，必须单独安装这些依赖项。 这些依赖项以及商家配置支持服务器端处理 [后台活动](events-backoffice.md).
![新建](../assets/new.svg)  — 添加了名为的新后台事件 [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_2023年2月28日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 为所有用户添加了对PHP 8.2的支持 [!DNL Data Connection] 扩展。

## 2.1.0

_2023年1月17日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 已更新 [[!DNL Data Connection] 扩展管理员](connect-data.md) 以便您指定自己的AEP Web SDK(alloy)。
![修复](../assets/fix.svg) 更改为使用 `identityMap` 而不是 `personID` 为推送到边缘的任何数据设置主标识时。

## 2.0.1

_2022年11月10日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)  — 现在，Adobe Experience Platform上下文仅在成功加载Storefront事件收集器和店面事件SDK之后设置。

## 2.0.0

_2022年10月12日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 添加了以下情况下指定您自己的AEP Web SDK的功能 [连接](connect-data.md) 将您的Adobe Commerce实例添加到Experience Platform。
![修复](../assets/fix.svg)  — 更新了数据流作用域要求，以便数据流ID的作用域必须限制在网站而不是存储审阅。

## 1.0.0

_2022年8月9日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)  — 正式发布。
