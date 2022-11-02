---
title: '"[!DNL Quick Checkout] 报告”'
description: '"[!DNL Quick Checkout] 提供全面的报告信息。”'
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 报告

[!DNL Quick Checkout] 对于Adobe Commerce和Magento Open Source，您可以提供全面的报表，以便获得商店结账体验统计信息的详细信息。

![报表视图](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 必须启用 [**结帐跟踪**](../quick-checkout/settings-quick-checkout.md) ，以便Adobe Commerce可以与Bolt共享签出信息。 默认情况下，此配置选项设置为 **是**. 如果禁用此选项(设置为 **否**)，则报表将受到影响。

## 概述报表

“概述”部分中的图表显示有关商店结帐性能的详细信息，包括平均结帐时间、结帐或结帐放弃期间创建的新帐户。

![报表概述](assets/overview-report-checkout.png)

| 图表 | 描述 |
|---|---|
| [!UICONTROL Checkout abandonment] | 退出结帐流程但未完成购买的访客百分比。 |
| [!UICONTROL Checkout abandonment breakdown] | 结账放弃除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 访客完成结帐流程所花费的平均时间。 |
| [!UICONTROL Average checkout time breakdown] | 平均结帐时间除以访客类型。 选项： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
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

