---
title: "安装 [!DNL Live Search]"
description: “了解如何安装、更新和卸载 [!DNL Live Search] 来自Adobe Commerce。”
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# 安装 [!DNL Live Search]

[!DNL Live Search] 将作为扩展从Adobe市场安装。 在 [!DNL Live Search] 模块（将目录模块作为依赖项）安装并配置， [!DNL Commerce] 开始与SaaS服务共享搜索和目录数据。 此时， *管理员* 用户可以设置、自定义和管理搜索彩块化、同义词和促销规则。

本主题提供了用于执行以下操作的说明：

* 安装 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [卸载 [!DNL Live Search]](#uninstall)

## 开始之前 {#before-you-begin}

执行以下操作：

1. 确认 [cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) 和 [索引器](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 正在运行。

1. 选择符合您要求的载入方法并按照说明操作。

   * [方法1](#method-1)：安装，不安装 [!DNL OpenSearch]
   * [方法2](#method-2)：使用安装 [!DNL OpenSearch] （无停机时间）

>[!IMPORTANT]
>
>由于Elasticsearch7将于2023年8月宣布终止支持，建议所有Adobe Commerce客户迁移到OpenSearch 2.x搜索引擎。 有关在产品升级期间迁移搜索引擎的信息，请参阅 [迁移到OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) 在 _升级指南_.

## 方法1：不使用OpenSearch安装 {#method-1}

安装时建议使用此载入方法 [!DNL Live Search] 更改为：

* 新建 [!DNL Commerce] 安装
* 暂存环境

在此方案中，店面操作因以下原因中断： [!DNL Live Search] 服务对目录中的所有产品编制索引。 在安装过程中， [!DNL Live Search] 模块已启用且 [!DNL OpenSearch] 模块已禁用。

1. 安装Adobe Commerce 2.4.4+，不安装 [!DNL Live Search].

1. 要下载 `live-search` 包，从命令行运行以下命令：

   ```bash
   composer require magento/live-search
   ```

1. 运行以下命令以禁用 [!DNL OpenSearch] 和相关模块，以及安装 [!DNL Live Search]：

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 当数据已编制索引并同步时，店面中无法使用搜索和类别浏览操作。 根据目录的大小，此过程可能至少需要一个小时 `cron` 运行以将数据同步到 [!DNL Live Search] 服务。

1. 验证以下各项 [索引器](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 设置为“按计划更新”：

   * 产品信息源
   * 产品变型馈送
   * 目录属性信息源
   * 产品价格信息源
   * 范围网站数据馈送
   * 范围客户组数据馈送
   * 类别信息源
   * 类别权限信息源

1. 配置您的 [API密钥](#configure-api-keys) 并验证您的目录数据是否为 [已同步](#synchronize-catalog-data) 替换为 [!DNL Live Search] 服务。

1. 要使Facet在店面中作为过滤器使用，请添加 [Facet](facets-add.md) 您需要，根据 [分面要求](facets.md).

   之后您应该能够添加Facet `cron` 运行属性馈送和导出属性元数据。

1. 按以下顺序运行以下命令：

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [验证](#verify-export) 已导出数据。

1. [测试](#test-the-connection) 店面的连接。

## 方法2：使用OpenSearch安装 {#method-2}

安装时建议使用此载入方法 [!DNL Live Search] 至：

* 现有生产 [!DNL Commerce] 安装

在此方案中， [!DNL OpenSearch] 临时管理来自店面的搜索请求，同时 [!DNL Live Search] 服务在后台对所有产品编制索引，不中断正常店面操作。 [!DNL OpenSearch] 已禁用，并且 [!DNL Live Search] 在对所有目录数据进行索引和同步后启用。

1. 要下载 `live-search` 包，从命令行运行以下命令：

   ```bash
   composer require magento/live-search
   ```

1. 运行以下命令以暂时禁用 [!DNL Live Search] 提供店面搜索结果的模块。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 继续管理店面的搜索请求，同时 [!DNL Live Search] 服务在后台同步目录数据和索引产品。

1. 验证以下各项 [索引器](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 设置为“按计划更新”：

   * 产品信息源
   * 产品变型馈送
   * 目录属性信息源
   * 产品价格信息源
   * 范围网站数据馈送
   * 范围客户组数据馈送

1. 配置您的 [API密钥](#configure-api-keys) 并验证您的目录数据是否为 [已同步](#synchronize-catalog-data) 替换为 [!DNL Live Search] 服务。

1. 要使Facet在店面中作为过滤器使用，请添加 [Facet](facets-add.md) 您需要，根据 [分面要求](facets.md).

   之后您应该能够添加Facet `cron` 运行产品和属性信息源，并将属性元数据导出到 [!DNL Live Search] 服务。

1. 按以下顺序运行以下命令：

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. 同步完成后，请使用 [GraphQL游乐场](https://developer.adobe.com/commerce/services/graphql/live-search/) 以验证以下内容：

   * 返回的产品计数接近您对商店视图的预期。
   * 返回Facet。

1. 运行以下命令以启用 [!DNL Live Search] 模块，禁用 [!DNL OpenSearch]，并运行 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [测试](#test-the-connection) 店面的连接。

## 配置API密钥 {#configure-api-keys}

需要Adobe Commerce API密钥及其关联的私钥才能连接 [!DNL Live Search] 到Adobe Commerce的安装。 API密钥在的帐户中生成和维护 [!DNL Commerce] 许可证持有者，可与开发人员或SI共享该许可证。 然后，开发人员可以代表许可证持有人创建和管理SaaS数据空间。  如果您已经有一组API密钥，则无需重新生成它们。

### Adobe Commerce许可证持有者

要生成API密钥和私钥，请参阅 [Commerce服务连接器](../landing/saas.md).

### Adobe Commerce开发人员或SI

开发人员或SI会配置SaaS数据空间，如 *Commerce服务* 部分配置。 在 *管理员*，Commerce Services将在以下位置提供： *配置* 在安装SaaS模块时显示侧栏。

## 同步目录数据 {#synchronize-catalog-data}

[!DNL Live Search] 需要同步的产品数据来执行搜索操作，并需要同步属性数据来配置Facet。 产品目录与目录服务之间的初始同步始于 [!DNL Live Search] 首先连接。 根据目录的安装方法和大小，导出和索引数据最多可能需要30分钟 [!DNL Live Search]. 在架构中可以找到与目录服务同步和共享的数据列表，该架构定义于：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 验证导出 {#verify-export}

验证是否已从Adobe Commerce实例导出目录数据并且已为其同步： [!DNL Live Search]，请在以下表中查找条目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

有关其他帮助，请参阅 [[!DNL Live Search] 目录未同步](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) 在支持知识库中。

### 将来的产品更新

初始同步后，增量产品更新最多可能需要15分钟才能用于店面搜索。 要了解更多信息，请访问 [索引 — 流式产品更新](indexing.md).

## 测试连接 {#test-connection}

在店面，验证以下内容：

* 此 [!UICONTROL Search] 框正确返回结果
* 类别浏览正确返回结果
* Facet(s)在搜索结果页面上可用作过滤器

如果一切运行正常，恭喜您！ [!DNL Live Search] 已安装、已连接并已准备就绪。

如果您在店面中遇到问题，请检查 `var/log/system.log` API通信失败或服务端错误的文件。

要允许通过防火墙进行实时搜索，请添加 `commerce.adobe.io` 到允许列表。

## 检查已安装的版本

在更新Live Search之前，请从命令行运行以下命令以检查已安装的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 正在更新 [!DNL Live Search] {#update}

更新 [!DNL Live Search]，从命令行运行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

要更新到主要版本，例如从3.1.1到4.0.0，请编辑项目的根 [!DNL Composer] `.json` 文件如下所示：

1. 如果您当前已安装 `magento/live-search` 版本为 `3.1.1` 或更低版本，并且您正在升级到版本 `4.0.0` 或更高版本，请在升级之前运行以下命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有关当前安装的信息 `magento/live-search` 版本，请运行以下命令：

   ```bash
   composer show magento/live-search
   ```

1. 打开根 `composer.json` 文件和搜索 `magento/live-search`.

1. 在 `require` 部分，按如下方式更新版本号：

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **保存** `composer.json`. 然后，从命令行运行以下命令：

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 正在卸载 [!DNL Live Search] {#uninstall}

卸载 [!DNL Live Search]，请参阅 [卸载模块](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] 包 {#packages}

| 包 | 描述 |
|--- |--- |
| `module-live-search` | 允许商家配置其搜索设置以进行分面、同义词、查询规则等，并提供对只读GraphQL游乐场的访问权限，以测试来自 *管理员*. |
| `module-live-search-adapter` | 将搜索请求从店面路由到 [!DNL Live Search] 服务，并在店面中呈现结果。 <br /> — 类别浏览 — 从店面路由请求 [顶部导航](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) 搜索服务。<br /> — 全局搜索 — 路由来自的请求 [快速搜索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 位于店面右上角的盒子 [!DNL Live Search] 服务。 |
| `module-live-search-storefront-popover` | “键入时搜索”弹出框取代了标准快速搜索，并返回排名最前的搜索结果的数据和缩略图。 |

## [!DNL Live Search] 依赖关系 {#dependencies}

以下各项 [!DNL Live Search] 依赖项由捕获 [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
