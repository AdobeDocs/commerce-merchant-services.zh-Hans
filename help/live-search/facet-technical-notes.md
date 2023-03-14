---
title: "Facet技术说明"
description: “有关使用的技术说明 [!DNL Live Search] 多方面。”
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Facet技术说明

分面是一种高性能筛选方法，使用多个可搜索的静态和动态属性值维度作为搜索标准。

[!DNL Live Search] 使用 `productSearch` 返回面向和特定于的其他数据的查询 [!DNL Live Search]. 请参阅 [`productSearch` 查询](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 以了解代码示例。

## Facet聚合

分面聚合按如下方式执行：如果店面具有三个分面（类别、颜色和价格），并且购物者对所有三个分面都进行过滤(颜色=蓝色，价格为$10.00-50.00，类别= `promotions`)。

* `categories` 聚合 — 聚合 `categories`，然后应用 `color` 和 `price` 过滤器，但不匹配 `categories` 筛选条件。
* `color` 聚合 — 聚合 `color`，然后应用`price` 和 `categories` 过滤器，但不匹配 `color` 筛选条件。
* `price` 聚合 — 聚合 `price`，然后应用 `color` 和 `categories` 过滤器，但不匹配 `price` 筛选条件。
