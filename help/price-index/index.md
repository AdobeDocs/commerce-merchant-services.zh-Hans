---
title: SaaS价格索引
description: 使用SaaS价格索引提高性能
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 45999b6499f248ea4138f7de4e910c274e747a04
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# SaaS价格索引

SaaS价格指数化可加快客户在提交价格更改后在网站上反映价格更改所花费的时间。 此可选模块允许具有大型、复杂目录或具有多个网站或客户群的商家更快速、持续地处理价格变化。

管道的最大瓶颈是：计算繁琐的流程（如索引和价格计算）已从PHP核心移至Adobe的云基础架构。 这使商家能够快速扩展资源以加快价格指数化时间，并以更快的速度反映对网站所做的这些更改。

所有符合要求的商家都可以从这些改进中受益，但获得最大收益的商家是客户：

* 价格不断变化：需要反复更改价格以实现策略目标的商户，例如频繁促销、季节性折扣或库存折扣。
* 多个网站和/或客户群组：具有跨多个网站（域/品牌）和/或客户群组的共享产品目录的商户。
* 网站或客户群组中的大量独特价格：具有广泛共享产品目录的商户，这些目录包含网站或客户群中的独特价格，例如具有预先协商价格的B2B商户、具有不同定价策略的品牌。

如果您有依赖PHP核心价格索引器的第三方应用程序，请阅读相关文档并咨询扩展提供商，然后再进行任何更改。

使用Adobe Commerce服务的客户可免费获取SaaS价格索引。

本小指南介绍了SaaS价格索引的工作方式以及如何启用它。

## 系统要求

要使用SaaS价格索引，您需要：

* Adobe Commerce 2.4.4+
* 至少安装了以下SaaS服务之一：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

## 模块

SaaS价格索引使用一组模块来提供功能。 所需模块的列表可能会略有不同，具体取决于存储设置。

这些模块将新信息源添加到管理员。 这些信息源将向SaaS索引器传输价格计算所需的数据，并忽略PHP核心价格索引器。

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

使用Luma和Adobe Commerce Core GraphQL的客户可以安装提供Luma兼容性的模块，并禁用PHP核心价格索引器：

```
adobe-commerce/catalog-adapter
```

的 `catalog-adapter` 仅与2.4.5兼容。对2.4.4和2.4.6的支持将在不久的将来发布。
如果第三方扩展或任何其他原因需要，可以重新启用PHP核心价格索引器。

## 注意事项

根据产品类型、价格复杂性和目录大小等因素，SaaS价格索引可能是您商店的正确解决方案。 阅读以下限制并确定这是否是适合您网站的良好解决方案。

目前，SaaS价格索引支持简单、分组、虚拟、可配置和捆绑动态产品类型。
即将支持可下载、礼品卡和捆绑固定产品类型。

SaaS价格指数支持基价：

* 最低/最高正常价格
* 最低/最高最终价格
* 特价
* 客户群价格
* 目录规则价格

选择使用新的定价信息源后，您可以联系 [支持](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 来帮助您撤消。

新信息源应与 `resync` [CLI命令](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 否则，数据将在标准同步过程中刷新。 获取有关 [目录同步](../landing/catalog-sync.md) 进程。

## 使用方案

### 没有扩展依赖项的Luma

* Luma或Abode Commerce Core GraphQL商家，已安装所需服务(实时搜索、产品Recommendations、目录服务)
* 没有依赖PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源。
1. 安装目录适配器。

### 具有PHP核心价格索引器依赖关系的Luma和Adobe Commerce Core GraphQl

* 已安装受支持服务(实时搜索、产品Recommendations、目录服务)的Luma或Abode Commerce核心GraphQL商家
* 依赖PHP核心价格索引器的第三方扩展
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器。
1. 重新启用PHP核心价格索引器。
1. 在 `catalog-adapter` 模块。

### 无头商人

* 安装了受支持服务(实时搜索、产品Recommendations、目录服务)的无头商家
* 不依赖PHP核心价格指数公司
* 销售简单、可配置、分组、虚拟和捆绑的动态产品

1. 启用新信息源
1. 安装目录适配器，这将禁用PHP核心价格索引器。

### Luma/Core GraphQL/Headless中不支持的产品类型

* 卢马/无头商户
* 销售礼品卡、可下载或捆绑固定产品

如果当前不支持的产品类型，请等待完全支持产品类型。
