---
title: 目录适配器扩展
description: 使用目录适配器呈现来自Commerce Services的价格
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: 6b578e7113c278a05a64f2db5e032bccc4a9580a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# 目录适配器

此 `Catalog Adapter` 扩展禁用默认的Adobe Commerce产品价格索引器，改为使用 [目录服务](../catalog-service/overview.md).
Adobe Commerce产品价格索引器已禁用，在安装这些扩展模块后无法打开。 只有通过删除或禁用此扩展，才能重新启用默认的产品价格索引器。

## 要求

* Adobe Commerce 2.4.4+
* 已安装以下Commerce Services之一：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)

## 安装

要使用 `catalog-adapter` 模块， [!DNL Live Search] 和 [!DNL Catalog Service] 必须先安装和配置。 请遵循 [安装 [!DNL Live Search]](../live-search/install.md) 和 [目录服务安装](../catalog-service/installation.md) 说明，然后再继续。

安装这些服务后，请运行以下命令：

```bash
composer require adobe-commerce/catalog-adapter
```

## 重命名Adobe Commerce产品价格索引器

如果您的第三方应用程序依赖于默认的Adobe Commerce产品价格索引器，则可以使用以下命令重新启用它：

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## 禁用Headless店面的产品价格索引器方案

如果您有Headless Commerce实例，则可能需要禁用Adobe Commerce产品价格索引器以减少Adobe Commerce实例的负载。
这可以通过安装 `magento/module-price-indexer-disabler` 模块：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用方案

以下是一些常见的 `Catalog Adapter` 方案。

### 不依赖于Adobe Commerce产品价格索引器

* 您是已安装所需服务(Live Search、Product Recommendations、Catalog Service)的Luma或Adobe Commerce Core GraphQL商家
* 没有依赖于Adobe Commerce产品价格索引器的第三方扩展

1. 安装目录适配器。

### 依赖于Adobe Commerce产品价格索引器

* 您是已安装支持服务(Live Search、Product Recommendations、Catalog Service)的Luma或Adobe Commerce Core GraphQL商家
* 您使用依赖于Adobe Commerce产品价格索引器的第三方扩展

1. 安装目录适配器。
1. 重新启用默认的Adobe Commerce产品价格索引器。

### Headless Commerce实例

* 具有Headless Commerce实例并安装了所需服务(实时搜索、产品Recommendations、目录服务)的商家
* 不依赖默认的Adobe Commerce产品价格索引器

1. 从目录适配器软件包安装“价格禁用程序”
