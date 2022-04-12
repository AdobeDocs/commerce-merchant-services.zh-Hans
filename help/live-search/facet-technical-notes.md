---
title: Facet技术说明
description: 有关使用实时搜索彩块化的技术说明。
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Facet技术说明

Faceting是一种高性能的过滤方法，它使用可搜索的静态和动态属性值的多个维度作为搜索条件。

[!DNL Live Search] 使用 `productSearch` 返回分面的查询以及特定于 [!DNL Live Search]. 请参阅 [`productSearch` 查询](https://devdocs.magento.com/live-search/product-search.html) ，以了解代码示例。

## 面聚合

如果店面有三个Facet（类别、颜色和价格），且购物者在所有三个Facet（颜色=蓝色，价格介于$10.00-50.00，类别=）上过滤，则会按如下方式执行Facet聚合 `promotions`)。

* `categories` 聚合 — 聚合 `categories`，应用 `color` 和 `price` 过滤器，但不是 `categories` 过滤器。
* `color` 聚合 — 聚合 `color`，应用 `price` 和 `categories` 过滤器，但不是 `color` 过滤器。
* `price` 聚合 — 聚合 `price`，应用 `color` 和 `categories` 过滤器，但不是 `price` 过滤器。
