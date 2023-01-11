---
title: “Facet类型”
description: '"[!DNL Live Search] facet是动态的，并在相关时显示在“过滤器”列表中。'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# 彩块化类型

全部 [!DNL Live Search] 彩块化是动态的，并显示在 *过滤器* 列表。 可用Facet的列表会根据返回的产品而发生更改。 以下特征会影响其呈现方式和行为：

* 已固定的Facet — 最常用的Facet可以固定到列表顶部。 其余彩块化均列于 *排序类型* 在已固定的彩块面之后排序。
* 智能Facet — 适用于 [Adobe Sensei](https://www.adobe.com/sensei.html) 查找与产品集和查询最相关的内容。 此计算会考虑整个目录的属性元数据，并在查询时确定查询的最相关方面。
* 热门彩块化 — 搜索结果中最常出现的产品属性。
* 价格彩块化 — 按价格范围返回产品。 您可以在 [*设置*](settings.md) 选项卡。

查询时， [!DNL Live Search] 会在智能和常用facet组中生成搜索结果。

![Facet — 价格](assets/storefront-search-results-run-price.png)

## 店面和无头选项

为 [!DNL Commerce] storefront由搜索适配器处理，该适配器将路由请求并在storefront中呈现结果。 全部 [!DNL Commerce] 无论分配给相应属性的输入类型如何，店面彩块化都会使用单选选项按字母顺序排序。 店面中可用的Facet会根据当前主题进行渲染，并反映对分层导航的呈现方式所做的任何自定义设置。

相比之下， [无头](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) 实施由API处理，并支持其他选项。 无标题彩块化可以按字母顺序或按计数排序，并且可以有单选或多选选项。

### 选择类型

对于无头实施，Facet可定义为 `single select` 或 `multi-select` 逻辑运算符来确定返回的产品集。 例如， `green AND blue` 或 `green OR blue`.

![Facet — 选择类型](assets/facets-select-type.png)

| 选择类型 | 描述 |
|--- |--- |
| 单选 | 单选Facet可提供多个选项，但允许购物者仅选择一个值。 |
| 多选（或） | （仅限无头）购物者可以选择多个选项，并且返回的产品可以匹配任何选定的值。 示例： `green OR blue` |
| 多选（和） | （仅限无头）购物者可以选择多个选项，并且返回的产品必须匹配所有选定的值。 示例： `green AND blue` |

### Facet标签

对于 [!DNL Commerce] 店面，小面标签由 [*属性属性*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). 对于具有多个视图的商店，可在 *管理标签*. 对于无头实施，会从 [分面工作区](faceting-workspace.md).

### 排序类型

为店面呈现的所有Facet都按字母顺序排序。 对于无头实施，Facet可以按字母顺序或按计数进行排序。

| 排序类型 | 描述 |
|--- |--- |
| 字母 | 在店面 *过滤器* 列表中，彩块化按字母顺序排序。 |
| 计数 | （仅限无头）对于无头实施，Facet也可以按当前返回产品集中每个Facet找到的值数进行排序。 |
