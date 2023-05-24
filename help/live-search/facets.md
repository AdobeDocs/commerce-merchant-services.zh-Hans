---
title: "Facet"
description: ”[!DNL Live Search] Facet使用属性值的多个维度作为搜索条件。”
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: e1a512d2c9738f05bb8dcb929dccc7ad81cf7e3e
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# Facet

分面是一种高性能筛选方法，使用多个属性值的维度作为搜索条件。 分面搜索类似，但比标准“智能”得多 [分层导航](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 可用过滤器的列表由 [可过滤属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 搜索结果中返回的产品数量。

![过滤的搜索结果](assets/storefront-search-results-run.png)

## 彩块化要求

分面的类别和产品属性要求类似于用于分层导航的可筛选属性。 每个属性的店面属性必须设置为 `filterable (with results)`.

[!DNL Live Search] 最多支持：

* 200个属性配置为Facet
* 50个可排序的属性
* 200个可过滤属性
* 200个可搜索属性

| 设置 | 描述 |
|--- |--- |
| [类别显示设置](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | 锚点 —  `Yes` |
| [属性属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [目录输入类型](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`， `Dropdown`， `Multiple Select`， `Price`， `Visual swatch` （仅限构件）， `Text swatch` （仅限构件） |
| 属性店面属性 | 在搜索结果分层导航中使用 —  `Yes` |

## 默认属性值

以下产品属性具有 [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 使用方式 [!DNL Live Search] 和默认启用。

| 属性 | 店面属性 | 属性 |
|---|---|---|
| 可排序 | 用于产品列表中的排序 | `price` |
| 可搜索 | 在搜索中使用 | `price` <br />`sku`<br />`name` |
| 可过滤搜索 | 在分层导航中使用 — 可过滤（包含结果） | `price`<br />`visibility`<br />`category_name` |

## 默认的非系统属性属性

下表显示了非系统属性（包括特定于Luma示例数据的属性）的默认搜索和可过滤属性。 设置 *在搜索中使用* 属性属性到 `Yes` 使属性在两者中均可搜索 [!DNL Live Search] 以及本机Adobe Commerce。

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
| 带袋 | 是 | 可筛选（包含结果） |
| style_general | 是 | 可筛选（包含结果） |

## 默认系统属性属性

下表显示了系统属性的默认搜索和可过滤属性。

| 属性代码 | 可搜索 | 在分层导航中使用 |
|--- |--- |--- |
| allow_open_amount | 是 | 可筛选（包含结果） |
| 描述 | 是 | 否 |
| name | 是 | 否 |
| 价格 | 是 | 可筛选（包含结果） |
| short_description | 是 | 否 |
| sku | 是 | 否 |
| 状态 | 是 | 否 |
| tax_class_id | 是 | 否 |
| url_key | 是 | 否 |
| 权重 | 是 | 否 |
