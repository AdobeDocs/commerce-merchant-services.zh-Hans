---
title: '[!DNL Quick Checkout] 报告'
description: '''[!DNL Quick Checkout] 提供全面的报告信息。'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
source-git-commit: bdfac90aa221f39dfc53eee833c473c7dcb0a042
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 报告

[!DNL Quick Checkout] 对于Adobe Commerce和Magento Open Source，您可以提供全面的报表，以便获得商店结账体验统计信息的详细信息。

![报表视图](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 要允许Adobe Commerce与Bolt共享签出信息，请 [**结帐跟踪**](../quick-checkout/settings-quick-checkout.md)  必须在管理员中启用设置。 默认情况下，此配置选项设置为 **是**. 如果此选项设置为 **否**，则报表会受到影响。 Bolt每天在东部标准时间(EST)凌晨3:00刷新报表信息一次。

## 概述报表

“概述”部分中的图表显示有关商店结帐性能的详细信息，包括平均结帐时间、结帐或结帐放弃期间创建的新帐户。

![报表概述](assets/overview-report-checkout.png)

| 图表 | 描述 |
|---|---|
| [!UICONTROL Checkout abandonment] | 退出结帐流程但未完成购买的访客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 结账放弃除以访客类型。 工具提示显示“Bolt”（螺栓）和“Guest”（来宾）之间的百分比差。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 访客完成结帐流程所花费的平均时间。 |
| [!UICONTROL Average checkout time breakdown] | 平均结帐时间除以访客类型。 工具提示显示“Bolt”（螺栓）和“Guest”（来宾）之间的百分比差。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 订单数除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趋势报表

“趋势”部分中的图表显示按帐户类型或在结帐期间创建的新帐户过滤的结帐体验趋势。

![报表趋势](assets/trends-report-checkout.png)

| 图表 | 描述 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 结帐放弃趋势除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 订单按访客类型划分的趋势。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 您的商店趋势中的新帐户。 |

## 过滤数据

您可以按日期或现有预设(如 **最近30天**.

![过滤器视图](assets/filter-view.png)

| 字段 | 描述 |
|---|---|
| [!UICONTROL Preset] | 一个下拉列表，其中显示可用于显示特定范围数据的默认预设。 默认情况下：最近30天 |
| [!UICONTROL Date range] | 允许您根据所选日期选择特定范围的数据的下拉菜单。 |
