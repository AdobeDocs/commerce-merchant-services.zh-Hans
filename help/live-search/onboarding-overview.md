---
title: “入门概述”
description: '"[!DNL Live Search] 载入流程、系统要求、边界和限制”'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 入门概述

开始使用 [!DNL Live Search] 对于Adobe Commerce，请完成载入过程以安装扩展、配置API密钥并同步目录。

## 载入流程

![[!DNL Live Search] 载入图](assets/onboarding-flow.svg)

## 要求 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* 8.1菲律宾比索/8.2
* [!DNL Composer]

### 支持的平台

* Adobe Commerce内部部署(EE):2.4.4+
* Adobe Commerce on Cloud(ECE):2.4.4+

## 边界和阈值

目前， [!DNL Live Search] 搜索/类别API具有以下受支持的限制和静态边界：

### 索引

* 每个商店视图最多可为300个产品属性建立索引。
* 仅对Adobe Commerce数据库中的产品进行索引。
* 产品必须位于默认共享目录中。
* CMS页面未编入索引。

### 查询

* [!DNL Live Search] 无权访问类别树的完整分类，这会导致某些分层导航搜索方案超出其覆盖范围。
* [!DNL Live Search] 对查询使用唯一的GraphQL端点来支持动态分面和“按类型搜索”等功能。 尽管与 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)，则存在一些差异，某些字段可能不完全兼容。

要使用“目录”权限限制客户群组，请执行以下操作：

* 必须将产品分配到根类别。
* 必须为“未登录”客户组授予“允许”浏览权限。
* 要将产品限制为“未登录”客户组，请转到每个类别并设置每个客户组的权限。

### 规则

* 每个存储视图的最大规则数为50。
* 每个规则的最大条件数为10。
* 每个规则的最大事件数为25。

### 同义词

* [!DNL Live Search] 每个存储视图最多可管理200个同义词。

## 价格索引器

Live Search客户可以使用 [SaaS价格索引器](../price-index/index.md)，可提供更快的价格更新和同步时间。

### PWA支持

实时搜索支持被认为属于测试版，因为并非所有PWA都已通过测试 [!DNL Live Search]. 搜索和产品清单页面等基本功能在Venia中可用，但Graphql的某些排列可能无法正常工作。

* 的当前测试版PWA实施 [!DNL Live Search] 返回搜索结果所需的处理时间超过 [!DNL Live Search] 与本地商务店面。
* [!DNL Live Search] PWA不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 直接在上筛选 `description`, `name`, `short_description` GraphQL不支持将 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但返回时会提供一个更常规的过滤器。

### 当前不支持

* 的 [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 模块在 [!DNL Live Search] ，并且会删除店面页脚中的高级搜索链接。
* 使用的多个库存位置 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 或其他OMS扩展
* 产品价格不包括 [增值税](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) （增值税）。
* [层价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 实时搜索弹出窗口和产品列表页面小组件中不支持此功能。

## Cookie

[!DNL Live Search] 收集用户交互数据作为其基本功能的一部分，并使用cookie存储此数据。 在收集任何用户信息时，用户必须同意存储Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共享数据流，因此共享相同的cookie机制。 有关更多信息，请参阅 [处理Cookie限制](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
