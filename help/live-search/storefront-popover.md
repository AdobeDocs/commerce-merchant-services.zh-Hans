---
title: 店面弹出窗口
description: 实时搜索店面弹出窗口可动态返回建议的产品和缩略图。
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 店面弹出窗口

When [!DNL Live Search] is [已安装](install.md)，则当购物者在 [搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 框中。 键入每个字符后，弹出窗口会更新为建议的产品以及顶部搜索结果的缩略图图像。

[!DNL Live Search] 返回包含两个或更多字符的查询的结果。 对于部分匹配，每个词的最大字符数为20。 “键入搜索”查询中的字符数不可配置。

>[!NOTE]
>
>的 [!DNL Live Search] 店面弹出窗口仅适用于使用 *卢马* 主题，或基于 *卢马*. 的 *卢马* 主题包含在 [!DNL Commerce] 示例数据。 弹出窗口不支持 *空白* 主题。 请参阅 [使用修改的主题](#working-with-modified-theme) 以了解更多信息。

## 可搜索属性

要生成高度定位的结果，请查看 [可搜索](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`)产品属性。 为确保相关性，仅当属性包含含义清晰且简洁的内容时，才可对其进行搜索。 避免使用包含较不精确、较长文本的属性，例如 `description`，虽然默认情况下启用了搜索功能，但可能会降低搜索结果的精度。 例如，如果某人搜索“短裤”，并且有描述中包含“短袖”一词的衬衫，则该衬衫将包含在搜索结果中。

始终可以搜索以下属性：

* `sku`
* `name`
* `categories`

![实时搜索弹出窗口](assets/storefront-search-as-you-type.png)
