---
title: "[!DNL Storefront Popover]"
description: “此 [!DNL Live Search storefront popover] 动态返回建议的产品和缩略图。”
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 92889130fd7482e0b99fb08746e6fd2830b0345e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# [!DNL Storefront Popover]

时间 [!DNL Live Search] 是 [已安装](install.md)， a [!DNL popover] 出现在店面，当顾客输入 [搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 盒子。 键入每个字符后， [!DNL popover] 将更新为推荐的产品和排名最前的搜索结果的缩略图图像。

[!DNL Live Search] 返回两个字符或更多字符的查询结果。 对于部分匹配，每个单词的最大字符数为20。 “键入时搜索”查询中的字符数无法配置。

## 可搜索属性

要生成目标明确的结果，请查看 [可搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`)产品属性。 为确保相关性，请仅在属性包含含义清晰简洁的内容时使其可搜索。 避免使用包含不太精确、冗长文本的属性，例如 `description`尽管默认情况下启用了搜索，但可能会降低搜索结果的精度。 例如，如果人员搜索“短裤”，并且衬衫的描述中包含术语“短袖口罩”，则衬衫将包含在搜索结果中。

以下属性始终可搜索：

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 页面大小

的页面大小 [!DNL popover] 确定可以返回多少行自动完成产品。 以前，页面大小被硬编码为六行。 但是， `page_size` value现在是一个设置，可以从以下位置配置： *管理员*. 在Live Search安装过程中， `page_size` 的值将更改为的当前 [目录搜索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 设置。

默认情况下，“目录搜索 — 自动完成限制”值设置为八行。 要更改的页面大小 [!DNL popover]，请执行以下操作：

1. 在 *管理员* 侧栏，转到 **商店** >设置> **配置**.
1. 在左侧面板中，展开 **目录** 并选择 **目录** 从设置列表中。
1. 展开 *目录搜索* 部分。
1. 设置 **自动完成限制** 到您希望在 [!DNL popover].
1. 完成后，单击 **保存配置**.

## 限制

* 此 [!DNL Live Search] [!DNL storefront popover] 仅适用于使用 *Luma* 主题，或基于 *Luma*.
* 此 [!DNL popover] 不支持 *空白* 主题。 参见 [样式 [!DNL Popover] 元素](storefront-popover-styling.md) 了解更多信息。
* 此 [!DNL popover] 快速订购单上不支持。
