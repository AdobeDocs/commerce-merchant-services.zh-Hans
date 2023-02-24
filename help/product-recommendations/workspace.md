---
title: '''[!DNL Product Recommendations] 工作区的'
description: 了解如何配置、管理和监控产品推荐性能。
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 25d5321b6f29bab5d8cf329170f3644f35100438
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL Product Recommendations] 工作区

的 [!DNL Product Recommendations] 工作区会显示以前配置的推荐列表，其中包含可帮助您跟踪每个推荐成功与否的量度。 该列表可配置为计算最后一天、周或月的量度。 您可以使用这些量度根据推荐单元的查看或点击频率创建切实可行的分析，或分析推荐的效果。

![Recommendations工作区](assets/workspace.png)
_Recommendations Workspace_

## 设置范围

最初， [范围](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 设置为 `Default Store View`. 如果您的Commerce安装包含多个商店视图，请设置 **范围** 到 [商店视图](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 推荐的位置。

## 设置量度日期范围

1. 单击 **日历** ![日历选择器](assets/icon-calendar.png) 控制。

1. 选择以下选项之一：

   - 最近24小时
   - 最近7天
   - 最近30天

   量度列中的计算值会发生更改，以反映当前日期范围。

## 显示/隐藏列

1. 在左上角，单击 **显示/隐藏** ![列选择器](assets/icon-show-hide-columns.png) 列。

   可见列具有蓝色复选标记。

1. 在菜单中，执行以下任一操作：

   - 要显示隐藏列，请单击任意列名称，但不带复选标记。
   - 要隐藏可见列，请单击带复选标记的任何列名称。

   将刷新表以仅包含所选列。

   ![Recommendations工作区](assets/workspace-select-columns.png)
   _显示/隐藏列_

## 设置

这些设置可确定提供推荐行为数据的SaaS数据空间。

- 要更改推荐行为数据的来源，请选择不同的SaaS数据空间。

- 要配置新的SaaS数据空间，请单击 **编辑配置**. 要了解更多信息，请参阅 [设置](settings.md).

![Recommendations设置](assets/settings.png)
_Recommendations设置_

## 查看详细信息

1. 在表格中，单击要检查的推荐。

   ![Recommendations工作区](assets/recommendation-detail.png)
   _主页转化率详细信息_

1. 要更改推荐的状态，请单击 **激活** 或 **停用**.

## 编辑推荐

在推荐详细信息页面中，单击 **编辑**. 要了解更多信息，请转到 [编辑Recommendations](edit.md).

## 创建推荐

在推荐详细信息页面中，单击 **创建**. 要了解更多信息，请转到 [创建Recommendations](create.md).

## 工作区控件

| 控制 | 描述 |
|---|---|
| ![日历选择器](assets/icon-calendar.png) | 确定用于量度计算的时间范围。 选项：24小时/7天/30天 |
| ![列选择器](assets/icon-show-hide-columns.png) | 确定在 [!DNL Product Recommendations] 表。 |
| 设置 | 确定获取推荐行为数据的SaaS数据空间，并启用可视相似性推荐类型。 |
| 创建推荐 | 打开 [创建新推荐](create.md) 页面。 |

## 列描述

| 列 | 描述 |
|---|---|
| 名称 | 推荐的名称。 |
| 页面 | 显示推荐的页面。 |
| 类型 | 推荐类型。 |
| 状态 | 推荐状态。 选项：不活动/活动/草稿 |
| 已创建 | 创建推荐的日期。 |
| 上次编辑时间 | 上次编辑推荐的日期。 |
| 展示次数 | 在页面上加载和渲染推荐单元的次数。 页面上呈现的推荐单位低于浏览器视区的折页，但购物者并未查看。 在这种情况下，呈现的单位将被计为一次展示，但仅当用户将单位滚动到视图中时，才会计为一次视图。 |
| vImpressions | （可查看展示次数）至少注册一个视图的推荐单位数。 |
| 视图 | 购物者浏览器视区中显示的推荐单位数。 此事件在页面上可以触发多次。 |
| 点击次数 | 购物者点击推荐单位中的项目的次数总和，以及购物者点击 **添加到购物车** 按钮 |
| 收入 | 由推荐在当前时间范围内驱动的收入。 |
| Lt收入 | （存留期收入）由推荐驱动的存留期收入。 |
| 可视性 | 注册查看的推荐单位的百分比。 |
| Ctr | （点进率）注册点击的推荐的单位展示次数百分比。 |
| vCtr | （可查看点进率）注册点击的推荐单元的可查看展示次数百分比。 |
