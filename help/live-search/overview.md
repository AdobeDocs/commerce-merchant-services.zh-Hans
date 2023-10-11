---
title: 简介 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerce提供了闪电般快速、超级相关且直观的搜索体验。”'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 4eddad715405f35ea063bab3cf4651fec3beeae5
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 简介 [!DNL Live Search]

[!DNL Live Search] 是一项用于Adobe Commerce的服务，取代了标准搜索功能。 此 [!DNL Live Search] 模块随Composer一起安装，并连接 [!DNL Commerce] 安装到 [!DNL Live Search] [服务](../landing/saas.md). 配置后，默认搜索文本字段会被替换为 [!DNL Live Search] 文本字段。

[!DNL Live Search] 显示在 *营销* 下的菜单 *SEO和搜索* 在 [!DNL Commerce] *管理员*.

架构的Adobe Commerce端包括托管搜索 *管理员*，同步目录数据，并运行查询服务。 之后 [!DNL Live Search] 安装和配置后，Adobe Commerce开始与SaaS服务共享搜索和目录数据。 此时，管理员用户可以设置、自定义和管理搜索 [Facet](facets.md)， [同义词](synonyms.md)、和 [促销规则](category-merch.md).

![实时搜索架构图](assets/architecture-diagram.svg)

## 实时搜索组件

* [!DNL Live Search] [弹出框](storefront-popover.md) 是在包含搜索结果的搜索字段下打开的框。
* [产品列表页面小组件](plp-styling.md) 提供了一个可搜索的产品列表页面，该页面支持彩块化和同义词。
* AEM [CIF组件](https://github.com/adobe/aem-cif-guides-venia/pull/319) 允许AEM站点利用 [!DNL Live Search].
* [[!DNL Live Search] 管理员](workspace.md) 是配置规则、彩块化和同义词的位置。
* Search Adapter是的默认实施 [!DNL Live Search].

## [!DNL Live Search] 演示

观看本视频以了解 [!DNL Live Search]：

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

有关如何使用和配置Live Search的更深入视频，请参阅 [完整演示 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) 主题。
