---
title: “入门概述”
description: '"[!DNL Live Search] 载入流程、系统要求、边界和限制”'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: ee8c37dc5dab9fcbc47d3d66e3ae0f99c9cb82d8
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 入门概述

开始使用 [!DNL Live Search] 对于Adobe Commerce，请完成载入流程以安装扩展，配置API密钥，并同步目录。

## 载入流程

![[!DNL Live Search] 载入流程图](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 支持的平台

* Adobe Commerce内部部署(EE) ：2.4.4+
* Adobe Commerce on Cloud (ECE) ：2.4.4+

## 端点

[!DNL Live Search] 通过上的端点通信 `https://catalog-service.adobe.io/graphql`.

## 边界和阈值

目前， [!DNL Live Search] 搜索/类别API具有以下支持的限制和静态边界：

### 索引

* 每个存储视图最多索引300个产品属性。
* 仅对Adobe Commerce数据库中的产品编制索引。
* 产品必须位于默认共享目录中。
* CMS页面未编制索引。

### 查询

* [!DNL Live Search] 无法访问类别树的完整分类，这使得某些分层导航搜索场景无法访问。
* [!DNL Live Search] 在查询中使用唯一的GraphQL端点来支持动态彩块化和按类型搜索等功能。 虽然与 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差异，一些字段可能不完全兼容。

要使用目录权限限制客户组，请执行以下操作：

* 必须将产品分配到根类别。
* 必须向“未登录”客户组提供“允许”浏览权限。
* 要将产品限制在“未登录”客户组，请转至每个类别并为每个客户组设置权限。

### 规则

* 每个存储视图的最大规则数为50。
* 每个规则的最大条件数为10。
* 每个规则的最大事件数为25。

### 同义词

* [!DNL Live Search] 每个存储视图最多可管理200个同义词。

## 价格索引器

Live Search客户可以使用新的 [SaaS价格索引器](../price-index/index.md)，可以加快价格变更更新和同步时间。

### PWA支持

[!DNL Live Search] 适用于PWA Studio，但用户可能会看到与其他Commerce实施相比的细微差异。 在威尼亚省可以使用搜索和产品列表页面等基本功能，但Graphql的某些排列可能无法正确工作。 此外，可能存在性能差异。

* 的当前PWA实现 [!DNL Live Search] 返回搜索结果所需的处理时间大于 [!DNL Live Search] 在本地Commerce店面中使用。
* [!DNL Live Search] PWA不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 因此，智能促销将无法正常运行。
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

### 当前不支持

* 此 [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 在以下情况下将禁用模块 [!DNL Live Search] ，并删除店面页脚中的高级搜索链接。
* 由使用的多个库存库位 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS扩展
* 产品价格不包括 [增值税](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值税）。
* [层价格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 在“实时搜索”弹出框和产品列表页面构件中不受支持。

## Cookies

[!DNL Live Search] 收集用户交互数据作为其基本功能的一部分，并且Cookie用于存储此数据。 在收集任何用户信息时，用户必须同意存储Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共享数据流，因此使用相同的Cookie机制。 有关更多信息，请参阅 [处理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
