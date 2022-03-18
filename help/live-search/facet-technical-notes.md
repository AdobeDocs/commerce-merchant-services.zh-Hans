---
title: Facet技术说明
description: 有关使用实时搜索彩块化的技术说明。
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
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

## 默认属性值

以下产品属性具有 [店面属性](https://docs.magento.com/user-guide/stores/attributes-product.html) 默认情况下处于启用状态。

| 属性 | Storefront属性 | 属性 |
|---|---|---|
| 可排序 | 用于在产品清单中排序 | `price` |
| 可搜索 | 在搜索中使用 | `price` <br />`sku`<br />`name` |
| 可过滤InSearch | 在分层导航中使用 — 可过滤（包含结果） | `price`<br />`visibility`<br />`category_name` |
