---
title: "[!DNL Storefront Popover]"
description: “ [!DNL Live Search storefront popover] 会动态返回建议的产品和缩略图。”
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 44c5d3f73d9cf658a978829ffaef6a79c5d90216
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# [!DNL Storefront Popover]

时间 [!DNL Live Search] 是 [已安装](install.md)， a [!DNL popover] 出现在店面时，购物者键入 [Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 盒子。 键入每个字符后， [!DNL popover] 将更新为推荐的产品和排名最前的搜索结果的缩略图图像。

[!DNL Live Search] 返回两个字符或更多字符的查询结果。 对于部分匹配，每个单词的最大字符数为20。 “键入时搜索”查询中的字符数无法配置。

## 可搜索属性

要生成具有高度针对性的结果，请查看 [可搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`)产品属性。 为确保相关性，请仅在属性包含含义清晰而简洁的内容时才允许搜索属性。 避免使用包含不太精确、较长的文本的属性，例如 `description`尽管默认情况下启用了搜索，但可能会降低搜索结果的精度。 例如，如果人员搜索“短裤”，并且有描述包含“短袖”一词的衬衫，则衬衫将包含在搜索结果中。

以下属性始终可搜索：

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 页面大小

的页面大小 [!DNL popover] 确定可以返回多少行自动完成产品。 以前，页面大小硬编码为六行。 但是， `page_size` value现在是一个设置，可以从以下位置配置： *管理员*. 在Live Search安装过程中， `page_size` 的值将更改为的当前 [目录搜索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 设置。

默认情况下，“目录搜索 — 自动完成限制”值设置为八行。 要更改 [!DNL popover]，请执行以下操作：

1. 在 *管理员* 侧栏，转到 **商店** >设置> **配置**.
1. 在左侧面板中，展开 **目录** 并选择 **目录** 从设置列表中。
1. 展开 *目录搜索* 部分。
1. 设置 **自动完成限制** 到您希望在 [!DNL popover].
1. 完成后，单击 **保存配置**.

## 目录服务

此 [Adobe Commerce的目录服务](../catalog-service/overview.md) 扩展提供了丰富的视图模型目录数据，以便快速和完全呈现与产品相关的店面体验。 目录服务可以与Live Search结合使用，以提供本机扩展当前不支持的功能：

* 色板
* 扩展属性
* 还可以引入其他产品信息

商家可以使用目录服务自定义和扩展小部件或店面元素，但这不属于Adobe支持团队的范围。

## Headless实施

对于具有Headless实施的客户，可以使用安装实时搜索弹出框 [npm包](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## 限制

* 此 [!DNL Live Search] [!DNL storefront popover] 仅适用于使用 *Luma* 主题，或基于 *Luma*. 搜索结果页面上的痕迹导航不具有 *Luma* 样式。
* 此 [!DNL popover] 不支持 *空白* 主题。 请参阅 [样式 [!DNL Popover] 元素](storefront-popover-styling.md) 了解更多信息。
* 此 [!DNL popover] 快速订购表单上不支持。
* 不支持愿望清单和产品比较。
