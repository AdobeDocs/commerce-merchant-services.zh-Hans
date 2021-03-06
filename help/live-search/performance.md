---
title: '"性能"'
description: “ [!DNL Live Search] 性能功能板提供对购物者使用的搜索词的分析。”
exl-id: ee2053fc-98c5-4d2c-9345-4d1f9a3180fb
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# 性能

的 [!DNL Live Search] “性能”功能板提供对购物者使用的搜索词的分析。 信息可用于识别趋势、增加点进率并提高转化率。 “性能”功能板提供了特定日期范围的搜索量度快照，并包括以下报表：

* 独特搜索
* 零结果
* 热门结果

![性能](assets/performance-unique-searches.png)

## 查看报表

1. 输入 **日期范围**，单击日历(![日历](assets/btn-calendar.png))并执行以下操作之一：

   * 要指定单个日期，请双击日历上的日期。
   * 要指定日期范围，请单击日历上的第一个日期和最后一个日期。

   ![性能报表时间范围](assets/performance-calendar.png)

1. 单击要查看的报表选项卡。

   ![性能热门结果](assets/performance-popular-results.png)

## 字段描述

| 快照数据 | 描述 |
|--- |--- |
| 独特搜索 | 指定日期范围内的唯一搜索总数。 同一购物者进行的多次搜索（即使针对同一查询），如果在间隔超过一小时的时间内提交，则会被视为唯一搜索。 |
| 点进率 | 购物者点击产品后结束的搜索百分比。 例如，如果购物者搜索“paint”和“strit”，然后在“shirt”搜索中点击一个结果，则点进率为50%。 |
| 转化率 | 购物者购买的产品百分比与购物者在指定日期范围内点击的产品数量。 例如，如果购物者在弹出窗口中查看了6个产品，单击1个产品，然后进行购买，则交互的转化率为100%。 <br /><br />转化率不受给定产品查看次数的影响。 例如，如果购物者使用搜索但未单击任何产品，则转化率保持不变。 |
| 零结果率 | 在指定的日期范围内不返回任何结果的唯一搜索的百分比。 例如，如果购物者搜索“fjjajfjfjf”两次（没有结果），搜索“pants”一次（有结果），则零结果率为66.67%。 |
| 平均 单击位置 | 基于对指定日期范围的唯一搜索的平均点进率的相对位置。 |

| 报告 | 描述 |
|--- |--- |
| 独特搜索 | 列出在指定日期范围内使用的唯一搜索查询。 报表数据的计算方式与唯一搜索快照数据的计算方式相同。 如果购物者键入同一搜索查询两次，但间隔超过一小时，则该搜索将被视为两个唯一搜索。 报表限制：前500个术语 |
| 零结果 | 列出未返回任何结果的搜索查询以及指定日期范围内使用的次数。 报表限制：前500个术语 |
| 热门结果 | 列出在指定日期范围内收到最多查看的产品名称。 热门结果仅基于展示次数计算，不受点击次数或产生的收入的影响。 报表限制：前500个术语 |
