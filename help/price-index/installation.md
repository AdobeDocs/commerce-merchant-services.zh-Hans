---
title: SaaS价格索引安装
description: 安装SaaS价格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# SaaS价格索引安装

设置SaaS价格索引需要安装新模块和运行CLI命令。 管理员需要命令行访问权限才能完成此安装。

## 先决条件

* Adobe Commerce 2.4.4+
* 至少安装了下列其中一个SaaS服务：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

## 安装所需的模块

根据您的设置，安装过程可能会略有不同。
其中有一个扩展可添加新信息源和支持代码，另一个扩展可删除默认价格信息源。

1. 将以下模块添加到您的 `composer.json` 文件：

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
   ```

1. 运行升级命令：

   ```bash
   bin/magento setup:upgrade
   ```

升级后，提供了三个新馈送：

* `prices`  — 负责向服务交付价格数据
* `scopesCustomerGroup`  — 负责向服务交付客户组
* `scopesWebsite`  — 负责向服务交付网站、商店组和商店视图


1. 将新馈送配置为设置为“按计划更新”模式：

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 重新索引新信息源：

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

根据需要手动运行上述索引器。 否则，数据将在标准同步进程中刷新。 详细了解 [目录同步](../landing/catalog-sync.md) 服务。

Luma和Adobe Commerce Core GraphQL用户可以安装 `catalog-adapter` 提供Luma和核心GraphQl兼容性并禁用PHP核心价格索引器的模块。
要使用 `catalog-adapter` 模块， [!DNL Live Search] 和 [!DNL Catalog Service] 必须先安装和配置。 请遵循 [安装 [!DNL Live Search]](../live-search/install.md) 和 [目录服务安装](../catalog-service/installation.md) 说明，然后再继续。

要配置Live Search和Catalog Adapter，请按照 [商务服务连接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 说明。

```bash
composer require adobe-commerce/catalog-adapter
```

如果需要，可以使用以下命令重新启用PHP核心价格索引器：

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
