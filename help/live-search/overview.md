---
title: 什么是 [!DNL Live Search]？
description: '"[!DNL Live Search] Adobe Commerce提供了快速、相关且直观的搜索体验。”'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 362592eae354b43a3bf98e2839ffe90c21fd3593
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# 什么是 [!DNL Live Search]？

[!DNL Live Search] 是一项功能，取代了Adobe Commerce中的标准搜索功能。 此 [!DNL Live Search] 功能随Composer一起安装，并连接 [!DNL Commerce] 存储到 [Commerce服务连接器](../landing/saas.md). 配置后，默认搜索文本字段会被替换为 [!DNL Live Search] 文本字段。 [!DNL Live Search] 此外，还安装产品列表页面(PLP)小组件，该小组件在浏览搜索结果时提供强大的筛选功能。

替换为 [!DNL Live Search]，您可以：

- 创建有意义的搜索体验，帮助购物者和买家尽最大努力找到他们想要的。
- 利用AI支持的动态分面和响应会话内购物者行为对搜索结果进行重新排名。
- 使用基于SaaS的轻量级服务，该服务可轻松进行更新并包含在您的许可证中，从而降低了总拥有成本。
- 通过启用graphQL API、Headless灵活性、API沙盒环境和超快SaaS来获得技术性。

>[!IMPORTANT]
>
>在网站搜索方面，Adobe Commerce会为您提供各种选项。 在实施之前，请查看 [边界和限制](boundaries-limits.md) 确保以下各项 [!DNL Live Search] 适合您的业务需求。

## 架构

架构的Adobe Commerce端包括托管搜索 *管理员*，同步目录数据，并运行查询服务。 之后 [!DNL Live Search] 安装和配置后，Adobe Commerce开始与SaaS服务共享搜索和目录数据。 此时，管理员用户可以设置、自定义和管理搜索 [Facet](facets.md)， [同义词](synonyms.md)、和 [促销规则](category-merch.md).

![实时搜索数据流](assets/ls-cs-data-flow.png)

## 快速导览

注重速度、相关性和易用性， [!DNL Live Search] 对购物者和商家来说都是一个游戏规则的改变者。 请观看以下视频，然后快速浏览 [!DNL Live Search] 从店面。

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

有关使用和配置Live Search的更深入视频，请参见 [完整演示 [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) 主题。

### 按键入内容搜索

[!DNL Live Search] 在中，以建议的产品和排名最前的搜索结果的缩略图图像做出响应 [弹出框](storefront-popover.md) 因为购物者在 [Search](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 盒子。 此 [产品详细信息](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) 当购物者单击建议或特色产品时显示的页面。 A _查看全部_ 弹出框页脚中的链接将显示搜索结果页面。

[!DNL Live Search] 对于包含两个或更多字符的查询，返回“键入时搜索”结果。 对于部分匹配，每个单词的最大字符数为20。 查询中的字符数无法配置。 弹出框包括`name`， `sku`、和 `category_ids` 字段。

![示例店面 — 键入时搜索](assets/storefront-search-as-you-type.png)

### 查看所有搜索结果

要列出“键入时搜索”查询返回的所有产品，请单击 _查看全部_ 在弹出框的页脚中。

![店面示例 — 价格Facet](assets/storefront-view-all-search-results.png)

### 带有Facet的过滤搜索

过滤搜索使用属性值的多个维，或者 [Facet](facets.md)，作为搜索条件。 过滤器的选择由商家定义，并根据返回的产品而发生更改，最常用的方面将固定到列表顶部。

将Facet用作URL参数：`http://yourwebsite.com?color=red`和实时搜索会根据这些属性值筛选结果。

### 同义词

[同义词](synonyms.md) 通过包含购物者可能使用的与目录不同的词语，扩展查询范围并突出查询重点。 您可以微调同义词词典，让购物者保持参与和购买路径。

### 促销规则

促销 [规则](rules.md) 使用向搜索添加逻辑和事件的if-then语句塑造购物体验。 您可以轻松地提升或隐藏促销、季节或其他时间段内的产品。

### 搜索词支持

[!DNL Live Search] 支持Commerce [搜索词重定向](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms). 例如，用户可以搜索诸如“运费”之类的术语，并直接转到运费页面。

## 实时搜索组件

- [!DNL Live Search] [弹出框小组件](storefront-popover.md) 是在包含搜索结果的搜索字段下打开的框。
- [产品列表页面小组件](plp-styling.md) (PLP)提供了一个可搜索的产品列表页面，其中支持方面和同义词。 构件在Live Search 4.0.0+中已安装和启用。
- (**已弃用**)搜索适配器是PLP小组件的前身，随Live Search &lt; 4.0.0安装。如果您使用的是低于4.0.0的Live Search版本，Commerce建议您进行升级，以便享受PLP构件功能和未来改进带来的好处。

## [!DNL Live Search] 工作区

此 [!DNL Live Search] [工作区](workspace.md) 是管理员中您配置文件的区域 [!DNL Live Search] 同义词、彩块化和类别促销等功能。

## 活动

[!DNL Live Search] 用途 [事件](events.md) 以计算 [智能促销](category-merch.md) 和 [性能](performance.md) 功能板。 事件随默认实施一起提供。 Headless店面的事件应该手动启用。
