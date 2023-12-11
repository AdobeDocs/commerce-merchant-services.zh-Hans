---
title: “技术概述”
description: '"[!DNL Live Search] 载入流程、系统要求、边界和限制”'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: ab09bc53666915713bd0180d87b3e40aec430a86
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# 技术概述

本主题回顾安装和优化的技术要求和提示 [!DNL Live Search] 用于Adobe Commerce。

## 要求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 支持的平台

* Adobe Commerce内部部署(EE) ：2.4.4+
* Adobe Commerce on Cloud (ECE) ：2.4.4+

## 端点

[!DNL Live Search] 通过上的端点通信 `https://catalog-service.adobe.io/graphql`.

>[!NOTE]
>
>作为 [!DNL Live Search] 没有访问完整产品数据库的权限， [!DNL Live Search] GraphQL和Commerce核心GraphQL不具备完全对等性。

## 边界和阈值

目前， [!DNL Live Search] 搜索/类别API具有以下支持的限制和静态边界：

### 索引

* [索引](indexing.md) 每个商店视图最多300个产品属性。
* 仅对Adobe Commerce数据库中的产品编制索引。
* CMS页面未编制索引。

### 查询

* [!DNL Live Search] 无法访问类别树的完整分类，这使得某些分层导航搜索场景无法访问。
* [!DNL Live Search] 在查询中使用唯一的GraphQL端点来支持动态彩块化和按类型搜索等功能。 虽然与 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差异，一些字段可能不完全兼容。

要使用目录权限限制客户组，请执行以下操作：

* 必须将产品分配到根类别。
* 必须向“未登录”客户组提供“允许”浏览权限。
* 要将产品限制在“未登录”客户组，请转至每个类别并为每个客户组设置权限。

### 规则

* 搜索促销的最大数量 [规则](rules.md) 每个商店视图为50。
* 类别促销在每个类别中可以有一个规则。
* 每个规则的最大条件数为10。
* 每个规则的最大事件数为25。

### 同义词

* [!DNL Live Search] 最多可管理200个 [同义词](synonyms.md) 每个商店视图。

## 语言支持

[!DNL Live Search] 小组件支持以下语言：

* en_US（默认）
* de_DE
* es_MX
* fr_FR
* it_IT
* ja_JA
* nl_NL
* no_NO
* pt_PT

如果小组件检测到Commerce管理语言设置(_商店_ >设置> _配置_ > _常规_ >国家/地区选项)与支持的语言匹配，默认为该语言。 否则，小组件将默认使用英语。

## 类别促销

[类别促销](category-merch.md) 允许您配置 [!DNL Live Search] 在产品类别级别工作。

本视频介绍了类别推销。

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## 构件代码存储库

产品列表页面构件和搜索弹出框构件均可从其github存储库下载。

这允许开发人员完全自定义功能和样式。 这些用户自行托管代码，同时仍利用 [!DNL Live Search] 服务。

* [PLP小组件](https://github.com/adobe/storefront-product-listing-page)
* [搜索栏](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] 支持 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) commerce（以前称为多源清单，或MSI）中的功能。 要启用全面支持，您必须 [更新](install.md#update) 依赖关系模块 `commerce-data-export` 到版本102.2.0+。

[!DNL Live Search] 返回一个布尔值，表明某个产品在Inventory management中是否可用，但不包含有关哪个来源具有库存的信息。

## 价格索引器

Live Search客户可以使用新的 [SaaS价格索引器](../price-index/index.md)，可以加快价格变更更新和同步时间。

## PWA支持

[!DNL Live Search] 适用于PWA Studio，但用户可能会看到与其他Commerce实施相比的细微差异。 在威尼亚省可以使用搜索和产品列表页面等基本功能，但Graphql的某些排列可能无法正确工作。 此外，可能存在性能差异。

* 的当前PWA实现 [!DNL Live Search] 返回搜索结果所需的处理时间大于 [!DNL Live Search] 在本地Commerce店面中使用。
* [!DNL Live Search] PWA不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 因此，智能营销将无法奏效。
* 直接筛选 `description`， `name`， `short_description` GraphQL不支持与一起使用 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但会使用更一般的过滤器返回它们。

使用 [!DNL Live Search] 对于PWA Studio，集成商还必须：

1. 安装 [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. 设置 `environmentId` 在 `storeDetails` 对象。

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

## 当前不支持

* 此 [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 在以下情况下将禁用模块 [!DNL Live Search] ，并删除店面页脚中的高级搜索链接。
* [分层定价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 和 [特殊定价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) 不支持 [!DNL Live Search] 弹出框和产品列表页面小组件。

## Cookies

[!DNL Live Search] 收集用户交互数据作为其基本功能的一部分，并且Cookie用于存储此数据。 在收集任何用户信息时，用户必须同意存储Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共享数据流，因此使用相同的Cookie机制。 有关更多信息，请参阅 [处理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
