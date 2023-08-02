---
title: "Facet"
description: '"[!DNL Live Search] Facet使用属性值的多个维度作为搜索条件。”'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 9cf48f6f900385a5cb772adee8834ec9cfe5ee13
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Facet

分面是一种高性能筛选方法，它使用多个属性值的维度作为搜索条件。 多面向搜索与此类似，但比标准“更智能” [分层导航](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 可用过滤器的列表由 [可过滤属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 搜索结果中返回的产品数量。

![过滤的搜索结果](assets/storefront-search-results-run.png)

任何已定义的Facet都可以用作URL参数，并将根据参数值筛选结果： `http://yourstore.com?brand=acme&color=red`.

## 彩块化要求

分面的类别和产品属性要求与用于分层导航的可过滤属性类似。 必须将每个属性的店面属性设置为 `filterable (with results)`.

[!DNL Live Search] 最多支持：

* 100个配置为Facet的属性
* 50个可排序的属性
* 200个可过滤属性
* 200个可搜索属性

| 设置 | 描述 |
|--- |--- |
| [类别显示设置](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | 锚点 —  `Yes` |
| [属性属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [目录输入类型](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`， `Dropdown`， `Multiple Select`， `Price`， `Visual swatch` （仅限构件）， `Text swatch` （仅限构件） |
| 属性店面属性 | 在搜索结果分层导航中使用 —  `Yes` |

## 默认属性值

以下产品属性具有 [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 使用方： [!DNL Live Search] 默认情况下处于启用状态。

| 属性 | 店面属性 | 属性 |
|---|---|---|
| 可排序 | 用于产品列表中的排序 | `price` |
| 可搜索 | 在搜索中使用 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | 在分层导航中使用 — 可过滤（包含结果） | `price`<br />`visibility`<br />`category_name` |

## 默认的非系统属性属性

下表显示了非系统属性的默认搜索和可过滤属性，包括那些特定于Luma示例数据的属性。 设置 *在搜索中使用* 属性属性至 `Yes` 使属性在两者中均可搜索 [!DNL Live Search] 以及本机Adobe Commerce。

| 属性代码 | 可搜索 | 在分层导航中使用 |
|--- |--- |--- |
| 活动 | 是 | 可筛选（包含结果） |
| attributes_brand | 是 | 否 |
| 品牌 | 是 | 否 |
| 气候 | 是 | 可筛选（包含结果） |
| 项圈 | 是 | 可筛选（包含结果） |
| 颜色 | 是 | 可筛选（包含结果） |
| 成本 | 是 | 否 |
| eco_collection | 是 | 可筛选（包含结果） |
| 性别 | 是 | 可筛选（包含结果） |
| 制造商 | 是 | 可筛选（包含结果） |
| 材料 | 是 | 可筛选（包含结果） |
| 用途 | 是 | 可筛选（包含结果） |
| 捆绑_包 | 是 | 可筛选（包含结果） |
| style_general | 是 | 可筛选（包含结果） |

## 默认系统属性属性

下表显示了系统属性的默认搜索和可过滤属性。

| 属性代码 | 可搜索 | 在分层导航中使用 |
|--- |--- |--- |
| allow_open_amou | 是 | 可筛选（包含结果） |
| 描述 | 是 | 否 |
| name | 是 | 否 |
| 价格 | 是 | 可筛选（包含结果） |
| short_description | 是 | 否 |
| sku | 是 | 否 |
| 状态 | 是 | 否 |
| tax_class_id | 是 | 否 |
| url_key | 是 | 否 |
| 粗细 | 是 | 否 |
