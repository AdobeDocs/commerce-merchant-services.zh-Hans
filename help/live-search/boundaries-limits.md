---
title: '边界和限制'
description: 了解的边界和限制 [!DNL Live Search] 确保它满足您的业务需求。
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# 边界和限制

在网站搜索方面，Adobe Commerce会为您提供各种选项。 检讨以下界限及限制，以确保 [!DNL Live Search] 和 [!DNL Catalog Service] 满足您的业务需求。 如果您需要高级搜索功能，例如内容搜索、自带算法(BYOA)或基于属性的促销，请考虑使用第三方搜索解决方案。

## 常规

- 此 [高级搜索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 在以下情况下将禁用模块 [!DNL Live Search] ，并删除店面页脚中的高级搜索链接。
- [分层定价](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) 和 [特殊定价](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) 不支持 [!DNL Live Search] 字段和产品列表页面小组件。
- [!DNL Live Search] 无法聚合来自多个源的库存数据。
- 产品价格不含增值税。
- 不支持内容搜索。
- 可分页的产品数量限制为10,000个。

## 索引

- [!DNL Live Search] [索引](indexing.md) 每个商店视图最多共有450个产品属性。 其分布情况如下：
   - 50个可排序的属性
   - 200个可过滤属性
   - 200个可搜索属性
- [!DNL Live Search] 仅对Adobe Commerce数据库中的产品编制索引。
- CMS页面未编制索引。

## Facet

- 最多可以将100个属性配置为可编制索引的200个可筛选属性中的Facet。
- 在一个Facet中，最多可返回30个分段。 如果需要返回30个以上的分段， [创建支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) 因此，Adobe可以分析性能影响并确定为您的环境提高此限制是否可行。
- 动态Facet会导致大型索引和高序度索引的性能问题。 如果您已创建动态Facet，并且发现任何性能下降或页面未加载但存在超时错误，请尝试将您的Facet更改为Pinded以确定这是否解决了您的性能问题。
- 库存状态(`quantity_and_stock_status`)不支持作为Facet。 您可以使用 `inStock: 'true'` 以筛选出缺货的产品。 开箱即用支持的应用程序位于 `LiveSearchAdapter` 模块（当中的“显示缺货产品”设置为“真”） [!DNL Commerce] 管理员。

## 查询

- [!DNL Live Search] 无法访问类别树的完整分类，这使得某些分层导航搜索场景无法访问。
- [!DNL Live Search] 使用唯一 [GraphQL端点](https://developer.adobe.com/commerce/services/graphql/live-search/) 用于支持动态彩块化和按类型搜索等功能的查询。 虽然与 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)存在一些差异，一些字段可能不完全兼容。
- 可在搜索查询中返回的结果的最大数量为10,000。

## 规则

- 搜索促销的最大数量 [规则](rules.md) 每个商店视图为50。
- 类别促销在每个类别中可以有一个规则。
- 每个规则的最大条件数为10。
- 每个规则的最大事件数为25。

## 同义词

- [!DNL Live Search] 最多可管理200个 [同义词](synonyms.md) 每个商店视图。
- 不支持多词同义词。

## 类别促销

- 可以为每个商店视图为每个类别创建一个规则。 每个规则可以具有：
   - 最多10个条件
   - 最多25个事件

## B2B和类别权限

- 如果产品未添加到默认共享目录，则不会显示产品。
- 要使用目录权限限制客户组，请执行以下操作：
   - 必须将产品分配到根类别。
   - 必须向“未登录”客户组提供“允许”浏览权限。
   - 要将产品限制为“未登录”客户组，请转至每个类别并为每个客户组设置权限。
- 目前不支持使用Live Search进行PWA Studio的B2B。
