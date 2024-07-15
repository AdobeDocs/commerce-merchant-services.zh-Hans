---
title: '[!DNL Product Recommendations] Workspace'
description: 了解如何配置、管理和监控产品推荐性能。
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 25d5321b6f29bab5d8cf329170f3644f35100438
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

[!DNL Product Recommendations]工作区显示以前配置的推荐列表，其中包含可帮助您跟踪每个推荐是否成功的量度。 可将该列表配置为计算过去一天、一周或月的量度。 您可以使用量度，根据查看或单击推荐单位的频率创建切实可行的见解，或分析推荐的执行情况。

![Recommendations工作区](assets/workspace.png)
_Recommendations Workspace_

## 设置范围

最初，所有推荐设置的[范围](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)设置为`Default Store View`。 如果您的Commerce安装包含多个存储视图，请将&#x200B;**范围**&#x200B;设置为您的建议适用的[存储视图](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)。

## 设置量度日期范围

1. 单击&#x200B;**日历** ![日历选择器](assets/icon-calendar.png)控件。

1. 选择下列选项之一：

   - 最近24小时
   - 最近7天
   - 最近30天

   量度列中的计算值会发生更改，以反映当前日期范围。

## 显示/隐藏列

1. 单击左上角的&#x200B;**显示/隐藏** ![列选择器](assets/icon-show-hide-columns.png)列。

   可见的列具有蓝色复选标记。

1. 在菜单中，执行以下任一操作：

   - 要显示隐藏的列，请单击任何不带复选标记的列名称。
   - 要隐藏可见列，请单击带有复选标记的任何列名称。

   将刷新表以仅包含选定的列。

   ![Recommendations工作区](assets/workspace-select-columns.png)
   _显示/隐藏列_

## 设置

这些设置确定提供推荐行为数据的SaaS数据空间。

- 要更改推荐行为数据的来源位置，请选择其他SaaS数据空间。

- 要配置新的SaaS数据空间，请单击&#x200B;**编辑配置**。 若要了解详细信息，请参阅[设置](settings.md)。

![Recommendations设置](assets/settings.png)
_Recommendations设置_

## 查看详细信息

1. 在表中，单击要检查的建议案。

   ![Recommendations工作区](assets/recommendation-detail.png)
   _主页转化率详细信息_

1. 要更改推荐的状态，请单击&#x200B;**激活**&#x200B;或&#x200B;**停用**。

## 编辑推荐

在推荐详细信息页面中，单击&#x200B;**编辑**。 若要了解详细信息，请转到[编辑Recommendations](edit.md)。

## 创建推荐

在推荐详细信息页面中，单击&#x200B;**创建**。 若要了解详细信息，请转到[创建Recommendations](create.md)。

## Workspace控件

| 控件 | 描述 |
|---|---|
| ![日历选择器](assets/icon-calendar.png) | 确定用于量度计算的时间范围。 选项：24小时/7天/30天 |
| ![列选择器](assets/icon-show-hide-columns.png) | 确定[!DNL Product Recommendations]表中显示的列。 |
| 设置 | 确定从中获取推荐行为数据的SaaS数据空间，还启用视觉相似性推荐类型。 |
| 创建推荐 | 打开[新建推荐](create.md)页面。 |

## 列说明

| 列 | 描述 |
|---|---|
| 名称 | 推荐的名称。 |
| 页面 | 显示推荐的页面。 |
| 类型 | 推荐类型。 |
| 状态 | 推荐状态。 选项：不活动/活动/草稿 |
| 已创建 | 创建推荐的日期。 |
| 上次编辑时间 | 上次编辑推荐的日期。 |
| 展示次数 | 在页面上加载和呈现推荐单元的次数。 位于浏览器视区折叠下方的推荐单元会在页面上呈现，但购物者不会查看。 在这种情况下，呈现的单位被计为一次展示，但是仅当用户滚动该单位进入视图时才计为一次浏览。 |
| 展示次数 | （可视展示次数）注册至少一个视图的推荐单元数。 |
| 视图 | 购物者浏览器视区中显示的推荐单位数。 此事件可在页面上多次触发。 |
| 点击次数 | 购物者点击推荐单元中项目的次数与购物者点击推荐单元中&#x200B;**添加到购物车**&#x200B;按钮的次数之和 |
| 收入 | 在当前时间范围内由推荐驱动的收入。 |
| Lt收入 | （生命周期收入）由推荐驱动的生命周期收入。 |
| 可见性 | 注册查看的推荐单元的百分比。 |
| Ctr | （点进率）注册一次点击的推荐的单位展示次数百分比。 |
| vCtr | （可视点进率）注册点击的推荐单元的可查看展示次数百分比。 |
