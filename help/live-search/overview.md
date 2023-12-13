---
title: 简介 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerce提供了闪电般快速、超级相关且直观的搜索体验。”'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 9460d7cf2de677557ee3792665c65d2a52a52569
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 简介 [!DNL Live Search]

[!DNL Live Search] 是一项用于Adobe Commerce的服务，取代了标准搜索功能。 此 [!DNL Live Search] 模块随Composer一起安装，并连接 [!DNL Commerce] 安装到 [!DNL Live Search] [服务](../landing/saas.md). 配置后，默认搜索文本字段会被替换为 [!DNL Live Search] 文本字段。 [!DNL Live Search] 此外，还安装产品列表页面(PLP)小组件，该小组件在浏览搜索结果时提供强大的筛选功能。

[!DNL Live Search] 显示在 *营销* 下的菜单 *SEO和搜索* 在 [!DNL Commerce] *管理员*.

架构的Adobe Commerce端包括托管搜索 *管理员*，同步目录数据，并运行查询服务。 之后 [!DNL Live Search] 安装和配置后，Adobe Commerce开始与SaaS服务共享搜索和目录数据。 此时，管理员用户可以设置、自定义和管理搜索 [Facet](facets.md)， [同义词](synonyms.md)、和 [促销规则](category-merch.md).

## 实时搜索组件

* [!DNL Live Search] [弹出框小组件](storefront-popover.md) 是在包含搜索结果的搜索字段下打开的框。
* [产品列表页面小组件](plp-styling.md) 提供了一个可搜索的产品列表页面，该页面支持彩块化和同义词。
* AEM CIF组件： [弹出窗口小组件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) 和 [PLP小组件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) 允许AEM站点利用 [!DNL Live Search].
* [[!DNL Live Search] 管理员](workspace.md) 是配置规则、彩块化和同义词的位置。

## 工作流概述

[!DNL Live Search] 通过将目录数据移动到Adobe Commerce SaaS基础架构并构建用于按用户类型快速提供搜索结果的索引来进行工作。

### 1.安装

[!DNL Live Search] 是 [已安装](install.md) 到您的Adobe Commerce实例中 [Composer](https://getcomposer.org/). 这将安装连接到服务的所需模块，并配置Commerce实例以覆盖默认搜索字段。 此外，它还安装用于配置服务的Commerce Admin选项。

### 2.同步数据

[!DNL Live Search] 将目录数据移动到Adobe的SaaS基础架构。 数据被编入索引，搜索结果从此索引直接传送到店面。 根据大小和复杂性，索引可能需要30分钟到几个小时。

### 3.配置数据

正确配置产品数据可确保为您的客户获得良好的搜索结果。 需要执行几个设置步骤：分配类别和配置属性。

#### 分配类别

产品返回于 [!DNL Live Search] 必须为分配 [类别](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). 例如，在Luma中，产品被划分为“男性”、“女性”和“齿轮”等类别。 “Top”、“Bottoms”和“Watches”也设置了子类别。 这可以提高筛选时的粒度。

#### 可搜索和可过滤的字段

已分配产品 [属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可用于搜索和筛选的规则。 属性包括“颜色”、“大小”、“材质类型”等。 利用这些属性，用户可以查找“绿色顶盖”。 每个产品可能在Commerce管理员中定义了许多属性。

这些属性中的每一个都可以定义为 [&quot;searchable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) 在管理员中。 当设置为“可搜索”时，这些属性可供搜索 [!DNL Live Search].

[Facet](facets.md) 是在中定义的产品属性 [!DNL Live Search] 可筛选。 任何可过滤的属性都可以设置为中的Facet [!DNL Live Search] 但是，一次可以搜索多少个方面是有限制的。

[同义词](synonyms.md) 是一些术语，您可以定义这些术语以帮助引导用户使用正确的产品。 寻找裤子的用户可能会输入“裤子”或“长裤”。 您可以设置同义词，以便这些搜索词将用户引进“裤子”结果。

## [!DNL Live Search] 工作区

此 [!DNL Live Search] [工作区](workspace.md) 是管理员中您配置文件的区域 [!DNL Live Search] 同义词、彩块化和类别促销等功能。

## 活动

[!DNL Live Search] 用途 [事件](events.md) 以计算 [智能促销](category-merch.md) 和 [性能](performance.md) 功能板。 事件随默认实施一起提供。 Headless店面的事件应该手动启用。

## 自定义构件

大多数商店所有者将希望确保 [!DNL Live Search] 构件符合其存储的外观。

弹出框和PLP构件可以根据需要通过定义自定义CSS规则来设置样式。 请参阅 [样式弹出框元素](storefront-popover-styling.md) 和 [产品列表页面小组件](plp-styling.md).

如果您希望扩展小组件的功能，则每个小组件的源代码在公共存储库中可用。
在此方案中，您可以根据自己的需求自定义JavaScript，然后将自定义代码托管在您的网站上。 此自定义脚本与 [!DNL Live Search] 并返回正常结果，使您能够控制小组件的功能。

* [PLP构件存储库](https://github.com/adobe/storefront-product-listing-page)
* [搜索栏存储库](https://github.com/adobe/storefront-search-as-you-type)

获取有关以下内容的更多详细信息 [!DNL Live Search] 在 [技术概述](technical-overview.md).

## [!DNL Live Search] 演示

观看本视频以了解 [!DNL Live Search]：

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

有关如何使用和配置Live Search的更深入视频，请参阅 [完整演示 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) 主题。
