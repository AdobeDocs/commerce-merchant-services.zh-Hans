---
title: 安装Live Search
description: 了解如何从Adobe Commerce安装、更新和卸载Live Search。
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 安装 [!DNL Live Search]

[!DNL Live Search] 是一组独立的 [软件包](#live-search-packages) 取代了标准Magento Open Source和Adobe Commerce搜索功能。 的 [!DNL Live Search] 模块从服务器的命令行安装，并作为 [服务](https://docs.magento.com/user-guide/system/saas.html). 完成该过程后， [!DNL Live Search] 在 *营销* 菜单下 *SEO和搜索* 在 [!DNL Commerce] 管理员。

Adobe Commerce端包括托管搜索管理员、同步目录数据并运行查询服务。

![实时搜索架构图](assets/architecture-diagram.svg)

在 [!DNL Live Search] 模块（以目录模块作为依赖项）已安装和配置， [!DNL Commerce] 开始与SaaS服务共享搜索和目录数据。 此时，管理员用户可以设置、自定义和管理搜索彩块化、同义词和促销规则。

本主题提供了执行以下操作的说明：

* [安装 [!DNL Live Search]](#before-you-begin) （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [卸载 [!DNL Live Search]](#uninstall)

## 要求 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* 7.3菲律宾比索/7.4
* [!DNL Composer]

### 支持的平台

* Adobe Commerce on prem(EE):2.4.x
* Adobe Commerce on Cloud(ECE):2.4.x

## 边界和阈值

目前，实时搜索类别搜索/类别API具有以下受支持的限制和静态边界：

### 索引

* 每个商店视图最多可为300个产品属性建立索引
* 仅对Adobe Commerce数据库中的产品进行索引
* 不为CMS页面编入索引

### 功能

* 店面 [高级（表单）搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 模块
* [客户群组](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [自定义价格组](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用的多个库存位置 [MCOM](https://docs.magento.com/user-guide/mcom.html) 或其他OMS扩展
* [集成的B2B功能](https://business.adobe.com/products/magento/b2b-ecommerce.html)

### 查询

* 实时搜索无权访问类别树的完整分类，这会导致某些分层导航搜索方案超出其覆盖范围。
* 实时搜索使用唯一的GraphQL端点进行查询，以支持智能分面和按类型搜索等功能。 尽管与 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)，则存在一些差异，某些字段当前可能不完全兼容。

### Progressive Web Application(PWA)

* 实时搜索不支持 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 此时。

## 开始之前 {#before-you-begin}

执行以下操作：

1. 确认 [cron作业](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 和 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 正在运行。

1. 选择符合您要求的载入方法，然后按照说明操作。

   * [方法1](#method-1):不安装 [!DNL Elasticsearch]
   * [方法2](#method-2):安装方式 [!DNL Elasticsearch] （无停机）

   >[!TIP]
   >
   >要在命令行中输入说明，请将鼠标悬停在代码框的最右侧，然后单击 [!UICONTROL **复制**] 链接。 然后，将其粘贴到命令行中。 如果您没有从命令行工作的经验，请咨询系统集成商或开发人员以获取帮助。

## 方法1:不Elasticsearch安装 {#method-1}

安装时建议使用此载入方法 [!DNL Live Search] 更改为a:

* 新建 [!DNL Commerce] 安装
* 暂存环境

在此方案中，店面操作在 [!DNL Live Search] 服务为目录中的所有产品编制索引。 安装期间， [!DNL Live Search] 模块已启用并 [!DNL Elasticsearch] 模块被禁用。

1. 安装Adobe Commerce 2.4.x(不含 [!DNL Live Search].

1. 要下载 `live-search` 包中，从命令行中运行以下命令：

   ```bash
   composer require magento/DNL live-search
   ```

   有关更多信息，请参阅 [!DNL Live Search] [依赖](#dependencies) 捕获者 [!DNL Composer].

1. 运行以下命令以禁用 [!DNL Elasticsearch] 和相关模块，并安装 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch  Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 当数据已编入索引并同步时，搜索和类别浏览操作在店面中不可用。 根据目录的大小，该过程可能至少需要一小时的时间 `cron` 运行以同步数据 [!DNL Live Search] 服务。

1. 确认以下 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 设置为 `Update by Schedule`:

   * 产品信息源
   * 产品变体信息源
   * 目录属性信息源

1. 配置 [API密钥](#configure-api-keys) to [同步](#synchronize-catalog-data) 您的目录数据 [!DNL Live Search] 服务。

1. 要使Facet在店面中可用作过滤器，请将 [facet](https://docs.magento.com/user-guide/live-search/facets-add.html) 你需要，根据 [分面要求](https://docs.magento.com/user-guide/live-search/facets.html).

   您应该能够在 `cron` 运行属性馈送和导出属性元数据。

1. 在 `cron` 运行以同步数据。 然后， [验证](#verify-export) 数据已导出。

1. [测试](#test-the-connection) 店面的连接。

## 方法2:使用Elasticsearch安装 {#method-2}

安装时建议使用此载入方法 [!DNL Live Search] 至：

* 现有生产 [!DNL Commerce] 安装

在这种情况下， [!DNL Elasticsearch] 临时管理来自店面的搜索请求，而 [!DNL Live Search] 服务可对后台的所有产品进行索引，不会中断正常的店面操作。 [!DNL Elasticsearch] 已禁用， [!DNL Live Search] 在索引并同步所有目录数据后启用。

1. 要下载 `live-search` 包中，从命令行中运行以下命令：

   ```bash
   composer require magento/live-search
   ```

   有关更多信息，请参阅 [!DNL Live Search] [依赖](#live-search-dependencies) 捕获者 [!DNL Composer].

1. 运行以下命令以临时禁用 [!DNL Live Search] 提供存储前搜索结果的模块。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 继续管理来自店面的搜索请求，而 [!DNL Live Search] 服务在后台同步目录数据和索引产品。

1. 确认以下 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 设置为 `Update by Schedule`:

   * 产品信息源
   * 产品变体信息源
   * 目录属性信息源

1. 配置 [API密钥](#configure-api-keys) to [同步](#synchronize-catalog-data) 您的目录数据 [!DNL Live Search] 服务。

1. 要使Facet在店面中可用作过滤器，请将 [facet](https://docs.magento.com/user-guide/live-search/facets-add.html) 你需要，根据 [分面要求](https://docs.magento.com/user-guide/live-search/facets.html).

   您应该能够在 `cron` 运行产品和属性信息源，并将属性元数据导出到 [!DNL Live Search] 服务。

1. 请至少等待一小时，数据才会被编入索引并同步。 然后，使用 [GraphQL操场](https://devdocs.magento.com/live-search/graphql-support.html) 使用默认查询验证以下内容：

   * 返回的产品计数接近您对商店视图的预期值
   * 返回Facet

1. 运行以下命令以禁用 [!DNL Elasticsearch] 模块，启用 [!DNL Live Search] 模块和运行 `setup`:

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [测试](#test-the-connection) 店面的连接。

## 配置API密钥 {#configure-api-keys}

连接时需要Adobe Commerce API密钥及其关联的私钥 [!DNL Live Search] 安装Adobe Commerce。 API密钥在的帐户中生成并维护 [!DNL Commerce] 许可证持有者，他们可以与开发人员或SI共享该许可证。 然后，开发人员可以代表许可证持有者创建和管理SaaS数据空间。

### Adobe Commerce持证人

要生成API密钥和私钥，请参阅 [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html).

### Adobe Commerce开发人员或SI

开发人员或SI按照配置的Commerce Services部分中所述配置SaaS数据空间。 安装SaaS模块后，Commerce Services将在“管理员配置”侧栏中可用。

## 同步目录数据 {#synchronize-catalog-data}

[!DNL Live Search] 需要同步的产品数据才能执行搜索操作，并且需要同步的属性数据才能配置facet。 产品目录与目录服务之间的初始同步从 [!DNL Live Search] 的次数。 根据目录的安装方法和大小，可能需要长达八小时才能导出和索引数据 [!DNL Live Search]. 可在架构中找到与目录服务同步和共享的数据列表，该架构在中定义：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 验证导出 {#verify-export}

验证目录数据是否已从您的Adobe Commerce实例导出并同步，以便 [!DNL Live Search]，在下表中查找条目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

如需其他帮助，请参阅 [[!DNL Live Search] 目录未同步](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) 在支持知识库中。

### 将来的产品更新

初始同步后，增量产品更新可能最多需要15分钟才能用于店面搜索。 要了解更多信息，请转到 [流产品更新](https://devdocs.magento.com/live-search/indexing.html).

## 测试连接 {#test-connection}

在店面中，验证以下内容：

* 的 [!UICONTROL Search] 框正确返回结果
* 类别浏览正确返回结果
* Facet可用作搜索结果页面上的过滤器

如果一切正常，恭喜！ [!DNL Live Search] 已安装、已连接并可供使用。

如果在店面遇到问题，请检查 `var/log/system.log` 文件，以了解服务端的API通信故障或错误。

## 更新 [!DNL Live Search] {#update}

要更新 [!DNL Live Search]，从命令行中运行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

要更新到主版本（如从1.0更新到2.0），请编辑项目的根 [!DNL Composer] `.json` 文件如下：

1. 打开根 `composer.json` 文件和搜索 `magento/live-search`.

1. 在 `require` 部分更新版本号，如下所示：

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 然后，从命令行中运行以下命令：

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## 卸载 [!DNL Live Search] {#uninstall}

卸载 [!DNL Live Search]，请参阅 [卸载模块](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] 软件包 {#packages}

| 包 | 描述 |
|--- |--- |
| `module-live-search` | 允许商户为分面、同义词、查询规则等配置其搜索设置，并提供对只读GraphQL操场的访问权限，以测试管理员的查询。 |
| `module-live-search-adapter` | 将搜索请求从店面路由到 [!DNL Live Search] 服务，并在店面中呈现结果。 <br /> — 类别浏览 — 从店面路由请求 [顶部导航](https://docs.magento.com/user-guide/catalog/navigation-top.html) 到搜索服务。<br /> — 全局搜索 — 路由来自 [快速搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 的 [!DNL Live Search] 服务。 |
| `module-live-search-storefront-popover` | “键入时搜索”弹出窗口取代了标准快速搜索，并返回顶部搜索结果的动态产品建议和缩略图。 |

## [!DNL Live Search] 依赖 {#dependencies}

以下 [!DNL Live Search] 依赖项由 [!DNL Composer]:

| 依赖关系 | 描述 |
|--- |--- |
| 导出模块 | 以下模块收集和同步目录数据：<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | 配置与Commerce Services的连接时需要。 |
| `module-services-id` | 配置与Commerce Services的连接时需要。 |
