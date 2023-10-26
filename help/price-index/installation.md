---
title: SaaS Price Indexing手动安装
description: 为旧版本安装SaaS价格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: 4577111a-64a4-4e20-b970-3abfa6758247
role: Admin, Developer
source-git-commit: 3809d27fc3689519e4a162aa52f481d254aec656
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# SaaS Price Indexing手动安装

SaaS价格索引现成可用于受支持 [最新版本](index.md#Requirements) Commerce Services的。
如果您没有最新版本，并且希望为您的Adobe Commerce实例启用SaaS价格索引，请使用此Mini-Guide。

## 先决条件

* Adobe Commerce 2.4.4+
* 至少安装了以下SaaS服务之一：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

## 安装所需模块

根据您的设置，安装过程可能会略有不同。
有些扩展可添加新馈送和支持代码。

1. 将以下模块添加到您的 `composer.json` 文件：

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. 运行升级命令：

   ```bash
   bin/magento setup:upgrade
   ```

升级后，提供了三个新馈送：

* `prices`  — 负责向服务交付价格数据
* `scopesCustomerGroup`  — 负责将客户组交付到服务
* `scopesWebsite`  — 负责向服务交付网站、商店群组和商店视图


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

根据需要手动运行上述索引器。 否则，数据将在标准同步过程中刷新。 详细了解 [目录同步](../landing/catalog-sync.md) 服务。


要配置Live Search and Catalog Adapter，请按照 [Commerce服务连接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 说明。

## 注意事项

早于 `103.0.0` 版本、SaaS价格索引支持简单、分组、虚拟、可配置和捆绑动态产品类型。
对可下载、礼品卡和捆绑固定产品类型的支持可从 `magento/module-saas-price:103.0.0` 版本，可开箱即用于支持的Commerce Services。

新馈送应手动与同步 `resync` [CLI命令](../landing/catalog-sync.md#resynccmdline). 否则，数据将在标准同步过程中刷新。 获取有关 [目录同步](../landing/catalog-sync.md) 进程。
