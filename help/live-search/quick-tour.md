---
title: “快速导览”
description: “快速浏览一下 [!DNL Live Search] 从店面。”
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 9cf48f6f900385a5cb772adee8834ec9cfe5ee13
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 快速导览

注重速度、相关性和易用性， [!DNL Live Search] 对购物者和商家来说都是一个游戏规则的改变者。 跟随以快速浏览 [!DNL Live Search] 从店面。

## 按键入内容搜索

[!DNL Live Search] 在中，以建议的产品和排名最前的搜索结果的缩略图图像做出响应 [弹出框](storefront-popover.md) 因为购物者在 [Search](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 盒子。 此 [产品详细信息](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) 当购物者单击建议或特色产品时，将显示页面。 A _查看全部_ 弹出框页脚中的链接将显示搜索结果页面。

[!DNL Live Search] 对于包含两个或更多字符的查询，返回“键入时搜索”结果。 对于部分匹配，每个单词的最大字符数为20。 查询中的字符数无法配置。 弹出框中包含以下字段： `name`， `sku`、和 `category_ids`.

![示例店面 — 键入时搜索](assets/storefront-search-as-you-type.png)

## 查看所有搜索结果

要列出“键入时搜索”查询返回的所有产品，请单击 _查看全部_ 在弹出框的页脚中。

![店面示例 — 价格Facet](assets/storefront-view-all-search-results.png)

## 带有Facet的过滤搜索

过滤搜索使用属性值的多个维，或者 [Facet](facets.md)，作为搜索条件。 过滤器的选择由商家定义，并根据返回的产品而发生更改，其中最常用的Facet将固定到列表顶部。

将Facet用作URL参数：`http://yourwebsite.com?color=red`和实时搜索会根据这些属性值筛选结果。

## 同义词

[同义词](synonyms.md) 通过包含购物者可能使用的与目录不同的词语，扩展查询范围并突出查询重点。 您可以微调同义词词典，让购物者保持参与和购买路径。

## 促销规则

促销 [规则](rules.md) 使用向搜索添加逻辑和事件的if-then语句塑造购物体验。 您可以轻松地提升或隐藏促销、季节或其他时间段内的产品。
