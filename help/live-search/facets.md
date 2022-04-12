---
title: Facet
description: 实时搜索彩块化使用多个属性值维度作为搜索条件。
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 554b07c233da2af2ca2d9aacf56bdfe09dc67cd3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Facet

分面是一种高性能过滤方法，它使用多个属性值维度作为搜索条件。 多面搜索相似，但比标准“更智能” [分层导航](https://docs.magento.com/user-guide/catalog/navigation-layered.html). 可用过滤器的列表由 [可过滤属性](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) 搜索结果中返回的产品数量。

![筛选的搜索结果](assets/storefront-search-results-run.png)

## 分面要求

分面的类别和产品属性要求与用于分层导航的可过滤属性类似。 每个属性的storefront属性必须设置为 `filterable (with results)`.

* 最多可以将100个属性配置为带有 [!DNL Live Search].
* [!DNL Live Search] 索引最多300个属性，以作为可过滤/可搜索/可排序的属性，并在搜索中可见。

| 设置 | 描述 |
|--- |--- |
| [类别显示设置](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | 锚点 —  `Yes` |
| [属性属性](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [目录输入类型](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| 属性店面属性 | 在分层导航中使用 —  `Filterable (with results)` |

## 默认属性值

以下产品属性具有 [店面属性](https://docs.magento.com/user-guide/stores/attributes-product.html) 的 [!DNL Live Search] 和默认启用。

| 属性 | Storefront属性 | 属性 |
|---|---|---|
| 可排序 | 用于在产品清单中排序 | `price` |
| 可搜索 | 在搜索中使用 | `price` <br />`sku`<br />`name` |
| 可过滤InSearch | 在分层导航中使用 — 可过滤（包含结果） | `price`<br />`visibility`<br />`category_name` |

## 默认的非系统属性

下表显示了非系统属性的默认搜索和可过滤属性，包括特定于Luma示例数据的属性。 设置 *在搜索中使用* 属性属性 `Yes` 使属性可在 [!DNL Live Search] 和本地Adobe Commerce。

| 属性代码 | 可搜索 | 在分层导航中使用 |
|--- |--- |--- |
| 活动 | 是 | 可过滤（包含结果） |
| attributes_brand | 是 | 否 |
| 品牌 | 是 | 否 |
| 气候 | 是 | 可过滤（包含结果） |
| 领口 | 是 | 可过滤（包含结果） |
| 颜色 | 是 | 可过滤（包含结果） |
| 成本 | 是 | 否 |
| eco_collection | 是 | 可过滤（包含结果） |
| 性别 | 是 | 可过滤（包含结果） |
| 制造商 | 是 | 可过滤（包含结果） |
| 材料 | 是 | 可过滤（包含结果） |
| 用途 | 是 | 可过滤（包含结果） |
| strap_bags | 是 | 可过滤（包含结果） |
| style_general | 是 | 可过滤（包含结果） |

## 默认系统属性

下表显示了系统属性的默认搜索和可过滤属性。

| 属性代码 | 可搜索 | 在分层导航中使用 |
|--- |--- |--- |
| allow_open_amount | 是 | 可过滤（包含结果） |
| 描述 | 是 | 否 |
| name | 是 | 否 |
| 价格 | 是 | 可过滤（包含结果） |
| short_description | 是 | 否 |
| sku | 是 | 否 |
| 状态 | 是 | 否 |
| tax_class_id | 是 | 否 |
| url_key | 是 | 否 |
| 权重 | 是 | 否 |
