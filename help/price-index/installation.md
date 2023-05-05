---
title: SaaS价格索引安装
description: 安装SaaS价格索引
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# SaaS价格索引安装

设置SaaS价格索引需要安装新模块并运行CLI命令。 管理员需要命令行访问权限才能完成此安装。

## 先决条件

* Adobe Commerce 2.4.4+
* 至少安装了以下SaaS服务之一：

   * [目录服务](../catalog-service/overview.md)
   * [实时搜索](../live-search/guide-overview.md)
   * [产品Recommendations](../product-recommendations/guide-overview.md)

## 安装所需模块

根据您的设置，安装过程可能会略有不同。
有一些扩展会添加新馈送和支持代码，还有一些扩展会删除默认价格馈送。

1. 将以下模块添加到 `composer.json` 文件：

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

升级后，提供了三个新信息源：

* `prices`  — 负责向服务提供价格数据
* `scopesCustomerGroup`  — 负责将客户组交付到服务
* `scopesWebsite`  — 负责将网站、商店组和商店视图交付到服务


1. 将新馈送配置为“按计划更新”模式：

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 重新编入新馈送的索引：

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

根据需要手动运行上述索引器。 否则，数据将在标准同步过程中刷新。 有关 [目录同步](../landing/catalog-sync.md) 服务。

Luma和Adobe Commerce Core GraphQL用户可以安装 `catalog-adapter` 提供Luma与Core GraphQl兼容性并禁用PHP核心价格索引器的模块。
使用 `catalog-adapter` 模块， [!DNL Live Search] 和 [!DNL Catalog Service] 必须先安装和配置。 关注 [安装 [!DNL Live Search]](../live-search/install.md) 和 [目录服务安装](../catalog-service/installation.md) 说明。

要配置Live Search和Catalog Adapter，请按照 [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 说明。

```bash
composer require adobe-commerce/catalog-adapter
```

如果需要，可使用以下命令重新启用PHP核心价格索引器：

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
