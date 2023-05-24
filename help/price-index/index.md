---
title: SaaS价格索引
description: 使用SaaS价格索引提高性能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# SaaS价格索引

SaaS价格索引加快了价格更改提交后反映在SaaS客户网站上的时间。 此可选模块允许拥有大型复杂目录或拥有多个网站或客户组的商家更快速、更持续地处理价格变化。

该管道的最大瓶颈：索引和价格计算等计算密集型流程已从PHP核心转移到该Adobe的云基础架构。 这允许商家快速扩展资源以缩短价格指数化时间，并以更快的速度在网站上反映这些变化。

核心索引数据将流向SaaS服务，如下所示：

![默认数据流](assets/old_way.png)

通过SaaS价格指数，流程是：

![SaaS价格指数数据流](assets/new_way.png)

所有符合要求的商户都可以从这些改进中受益，但那些将看到最大收益的商户是具有以下特征的客户：

* 价格不断变化：商家需要重复更改价格以实现战略目标，例如频繁促销、季节性折扣或库存减价。
* 多个网站和/或客户组：在多个网站（域/品牌）和/或客户组之间共享产品目录的商家。
* 跨网站或客户组的大量唯一价格：具有大量共享产品目录的商家，其中包含跨网站或客户组的唯一价格，例如具有预先协商价格的B2B商家，以及具有不同定价策略的品牌。

如果您有依赖于PHP核心价格索引器的第三方应用程序，请在进行任何更改之前阅读文档并咨询扩展提供商。

使用Adobe Commerce服务的客户可以免费获取SaaS价格索引。

本小型指南介绍了SaaS价格索引的工作原理以及如何启用它。

## 系统要求

要使用SaaS价格索引，您需要：

* Adobe Commerce 2.4.4+
* 至少安装了下列其中一个SaaS服务：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

## 模块

SaaS价格索引使用一组模块来提供功能。 所需模块的列表可能略有不同，具体取决于商店设置。

这些模块会将新信息源添加到管理员。 这些馈送将价格计算所需的数据传输到SaaS索引器，并忽略PHP核心价格索引器。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

使用Luma和Adobe Commerce Core GraphQL的客户可以安装一个模块，该模块提供Luma和Core GraphQL兼容性并禁用PHP核心价格索引器：

```
adobe-commerce/catalog-adapter
```

此 `catalog-adapter` 仅与2.4.5兼容。不久的将来将发布对2.4.4和2.4.6的支持。
如果第三方扩展或任何其他原因需要，可以重新启用PHP核心价格索引器。

## 注意事项

根据产品类型、价格复杂性和目录大小等因素， SaaS价格索引可能是您商店的正确解决方案。 请阅读以下限制并确定这是否适用于您的网站。

目前， SaaS价格索引支持简单、分组、虚拟、可配置和捆绑动态产品类型。
即将支持可下载、礼品卡和捆绑包固定产品类型。

新馈送应手动与 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否则，数据将在标准同步进程中刷新。 获取有关 [目录同步](../landing/catalog-sync.md) 进程。

## 使用方案

### 没有扩展依赖性的Luma

* 已安装所需服务(Live Search、Product Recommendations、Catalog Service)的Luma或Abode Commerce核心GraphQL商家
* 没有依赖于PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源。
1. 安装目录适配器。

### 带有PHP核心价格索引器依赖项的Luma和Abode Commerce核心GraphQl

* 已安装受支持服务(Live Search、Product Recommendations、Catalog Service)的Luma或Abode Commerce核心GraphQL商家
* 通过依赖于PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器。
1. 重新启用PHP核心价格索引器。
1. 在中使用新信息源和Luma兼容性代码 `catalog-adapter` 模块。

### Headless商家

* 已安装受支持服务(Live Search、产品Recommendations、目录服务)的Headless商家
* 不依赖PHP核心价格索引器
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器，该适配器将禁用PHP核心价格索引器。

### Luma/Core GraphQL/Headless与不受支持的产品类型

* Luma/Headless商家
* 销售礼品卡、可下载或捆绑固定产品

对于当前不支持的产品类型，请等待完整的产品类型支持。
