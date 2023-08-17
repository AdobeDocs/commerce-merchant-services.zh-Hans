---
title: "彩块化的类型"
description: '"[!DNL Live Search] 彩块化是动态的，并在相关时显示在过滤器列表中。”'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# 彩块化的类型

[!DNL Live Search] 使用各种Facet类型，它们显示在 *过滤器* 仅在相关时列出。 可用Facet的列表会根据返回的产品而发生更改。 以下特征会影响其呈现方式和行为：

* 固定Facet — 最常用的Facet可以固定到列表顶部。 其余方面列于 *排序类型* 在固定Facet之后排序。
* 动态Facet — 具有以下功能的产品属性 [Adobe Sensei](https://www.adobe.com/sensei.html) 查找与产品集和查询最相关的项目。 该计算会考虑整个目录的属性元数据，并在查询时确定与查询最相关的Facet。
* 常用Facet — 搜索结果中最常出现的产品属性。
* 价格Facet — 按价格范围返回产品。 您可以在 [*设置*](settings.md) 选项卡。

在查询时， [!DNL Live Search] 在动态和常用Facet组中生成搜索结果。

![彩块化 — 价格](assets/storefront-search-results-run-price.png)

## 店面和无头选项

呈现的方面 [!DNL Commerce] 店面由搜索适配器处理，它将路由请求并在店面中显示结果。 全部 [!DNL Commerce] 店面多面使用单选选项按字母顺序排序，而不管分配给相应属性的输入类型如何。 店面中可用的Facet将根据当前主题进行渲染，并反映对分层导航的呈现所做的任何自定义设置。

相比之下， [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) 实施由API处理，并支持其他选项。 Headless Facet可以按字母顺序或计数排序，并且可以具有单选或多选选项。

### Facet标签

对象 [!DNL Commerce] “店面”，多面标签由 [*属性属性*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). 对于具有多个视图的商店，可以在下定义其他标签 *管理标签*. 对于Headless实施，标签是从 [彩块化工作区](faceting-workspace.md).

### 排序类型

为店面渲染的所有Facet按字母顺序排序。 对于Headless实施，Facet可以按字母顺序或计数排序。

| 排序类型 | 描述 |
|--- |--- |
| 字母 | 在店面 *过滤器* 列表，彩块化按字母顺序排序。 |
| 计数 | （仅限Headless）对于Headless实施，Facet也可以按在返回的当前产品集中每个Facet找到的值数排序。 |
