---
title: ’[!DNL Quick Checkout] 报告
description: ’[!DNL Quick Checkout] 提供了全面的报表信息。”
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---

# 报表

[!DNL Quick Checkout] 对于Adobe Commerce和Magento Open Source，提供了全面的报表，以便您能够获得有关商店结账体验统计的详细信息。

![“报表”视图](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 要允许Adobe Commerce与Bolt共享签出信息，请 [**结账跟踪**](../quick-checkout/settings-quick-checkout.md)  必须在“管理员”中启用设置。 默认情况下，此配置选项设置为 **是**. 如果将此选项设置为 **否**，报表将受影响。 Bolt在东部标准时间(EST)凌晨03:00刷新一次报表信息。

## 概述报表

“概述”部分中的图表显示有关商店结账性能的详细信息，包括平均结账时间、结账或结账放弃期间创建的新帐户。

![报表概述](assets/overview-report-checkout.png)

| 图表 | 描述 |
|---|---|
| [!UICONTROL Checkout abandonment] | 退出结账流程但未完成购买的访客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 结账放弃次数除以访客类型。 工具提示显示Bolt和Guest之间的百分比差异。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 访客完成结账流程所用的平均时间。 |
| [!UICONTROL Average checkout time breakdown] | 平均结账时间除以访客类型。 工具提示显示Bolt和Guest之间的百分比差异。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 所下的订单数除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 趋势报表

“趋势”部分中的图表显示按帐户类型过滤的结账体验趋势，或在结账期间创建的新帐户。

![报表趋势](assets/trends-report-checkout.png)

| 图表 | 描述 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 结账放弃趋势除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 订购次数趋势除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 关于您的商店趋势的新帐户。 |

## 筛选数据

您可以按日期或现有预设过滤显示的结果，如 **最近30天**.

![筛选器视图](assets/filter-view.png)

| 字段 | 描述 |
|---|---|
| [!UICONTROL Preset] | 显示默认预设的下拉列表，可用于显示特定范围的数据。 默认情况下：最近30天 |
| [!UICONTROL Date range] | 一个下拉列表，允许您根据选定的日期选择特定范围的数据。 |
