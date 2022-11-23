---
title: "安装 [!DNL Live Search]"
description: “了解如何安装、更新和卸载 [!DNL Live Search] 来自Adobe Commerce。”
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 11f961ea7e2e01d5d9efdaf2191f25f3a1dc8878
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---

# 安装 [!DNL Live Search]

Live Search作为Marketplace的扩展安装。 在 [!DNL Live Search] 模块（以目录模块作为依赖项）已安装和配置， [!DNL Commerce] 开始与SaaS服务共享搜索和目录数据。 此时， *管理员* 用户可以设置、自定义和管理搜索彩块化、同义词和促销规则。

本主题提供了执行以下操作的说明：

* 安装 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [卸载 [!DNL Live Search]](#uninstall)

## 开始之前 {#before-you-begin}

执行以下操作：

1. 确认 [cron作业](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 和 [索引器](https://docs.magento.com/user-guide/system/index-management.html) 正在运行。

1. 选择符合您要求的载入方法，然后按照说明操作。

   * [方法1](#method-1):不安装 [!DNL Elasticsearch]
   * [方法2](#method-2):安装方式 [!DNL Elasticsearch] （无停机）

## 方法1:不Elasticsearch安装 {#method-1}

安装时建议使用此载入方法 [!DNL Live Search] 更改为a:

* 新建 [!DNL Commerce] 安装
* 暂存环境

在此方案中，店面操作在 [!DNL Live Search] 服务为目录中的所有产品编制索引。 安装期间， [!DNL Live Search] 模块已启用并 [!DNL Elasticsearch] 模块被禁用。

>[!TIP]
>
>要避免键入错误，请将鼠标悬停在代码框的最右侧，单击 [!UICONTROL **复制**] 链接，并将其粘贴到命令行中。

1. 安装Adobe Commerce 2.4.x(不含 [!DNL Live Search].

1. 要下载 `live-search` 包中，从命令行中运行以下命令：

   ```bash
   composer require magento/live-search
   ```

   有关更多信息，请参阅 [!DNL Live Search] [依赖](#dependencies) 捕获者 [!DNL Composer].

1. 运行以下命令以禁用 [!DNL Elasticsearch] 和相关模块，并安装 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
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

1. 配置 [API密钥](#configure-api-keys) 并验证您的目录数据是否 [已同步](#synchronize-catalog-data) with [!DNL Live Search] 服务。

1. 要使Facet在店面中可用作过滤器，请将 [facet](facets-add.md) 你需要，根据 [分面要求](facets.md).

   您应该能够在 `cron` 运行属性馈送和导出属性元数据。

1. 在 `cron` 运行以同步数据。 然后， [验证](#verify-export) 数据已导出。

1. [测试](#test-the-connection) 店面的连接。

## 方法2:使用Elasticsearch安装 {#method-2}

安装时建议使用此载入方法 [!DNL Live Search] 至：

* 现有生产 [!DNL Commerce] 安装

在这种情况下， [!DNL Elasticsearch] 临时管理来自店面的搜索请求，而 [!DNL Live Search] 服务可对后台的所有产品进行索引，不会中断正常的店面操作。 [!DNL Elasticsearch] 已禁用， [!DNL Live Search] 在索引并同步所有目录数据后启用。

>[!TIP]
>
>要避免键入错误，请将鼠标悬停在代码框的最右侧，单击 [!UICONTROL **复制**] 链接，并将其粘贴到命令行中。

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

1. 配置 [API密钥](#configure-api-keys) 并验证您的目录数据是否 [已同步](#synchronize-catalog-data) with [!DNL Live Search] 服务。

1. 要使Facet在店面中可用作过滤器，请将 [facet](facets-add.md) 你需要，根据 [分面要求](facets.md).

   您应该能够在 `cron` 运行产品和属性信息源，并将属性元数据导出到 [!DNL Live Search] 服务。

1. 请至少等待一小时，数据才会被编入索引并同步。 然后，使用 [GraphQL操场](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) 使用默认查询验证以下内容：

   * 返回的产品计数接近您对商店视图的预期值。
   * 返回Facet。

1. 运行以下命令以启用 [!DNL Live Search] 模块，禁用 [!DNL Elasticsearch]，然后运行 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
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

连接时需要Adobe Commerce API密钥及其关联的私钥 [!DNL Live Search] 安装Adobe Commerce。 API密钥在的帐户中生成并维护 [!DNL Commerce] 许可证持有者，他们可以与开发人员或SI共享该许可证。 然后，开发人员可以代表许可证持有者创建和管理SaaS数据空间。  如果您已经有一组API密钥，则无需重新生成它们。

### Adobe Commerce持证人

要生成API密钥和私钥，请参阅 [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce开发人员或SI

开发人员或SI按照 *商务服务* 部分。 在 *管理员*，商务服务将在 *配置* 侧栏。

## 同步目录数据 {#synchronize-catalog-data}

[!DNL Live Search] 需要同步的产品数据才能执行搜索操作，并且需要同步的属性数据才能配置facet。 产品目录与目录服务之间的初始同步从 [!DNL Live Search] 的次数。 根据目录的安装方法和大小，可能需要长达八小时才能导出和索引数据 [!DNL Live Search]. 可在架构中找到与目录服务同步和共享的数据列表，该架构在中定义：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 验证导出 {#verify-export}

验证目录数据是否已从您的Adobe Commerce实例导出并同步，以便 [!DNL Live Search]，在下表中查找条目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

如需其他帮助，请参阅 [[!DNL Live Search] 目录未同步](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) 在支持知识库中。

### 将来的产品更新

初始同步后，增量产品更新可能最多需要15分钟才能用于店面搜索。 要了解更多信息，请转到 [索引 — 流式产品更新](indexing.md).

## 测试连接 {#test-connection}

在店面中，验证以下内容：

* 的 [!UICONTROL Search] 框正确返回结果
* 类别浏览正确返回结果
* Facet可用作搜索结果页面上的过滤器

如果一切正常，恭喜！ [!DNL Live Search] 已安装、已连接并可供使用。

如果在店面遇到问题，请检查 `var/log/system.log` 文件，以了解服务端的API通信故障或错误。

## 检查已安装的版本

在更新Live Search之前，从命令行中运行以下命令来检查当前安装的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 更新 [!DNL Live Search] {#update}

要更新 [!DNL Live Search]，从命令行中运行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

要从1.0.0更新到主版本（如从1.0.0更新到2.0.0），请编辑项目的根 [!DNL Composer] `.json` 文件如下：

1. 如果当前已安装 `magento/live-search` 版本 `1.3.1` 或更低版本，并且您已升级到版本 `2.0.0` 或更高版本，请在升级前运行以下命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有关当前安装的 `magento/live-search` 版本中，运行以下命令：

   ```bash
   composer show magento/live-search
   ```

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
| `module-live-search` | 允许商家为分面、同义词、查询规则等配置其搜索设置，并提供对只读GraphQL操场的访问，以测试来自 *管理员*. |
| `module-live-search-adapter` | 将搜索请求从店面路由到 [!DNL Live Search] 服务，并在店面中呈现结果。 <br /> — 类别浏览 — 从店面路由请求 [顶部导航](https://docs.magento.com/user-guide/catalog/navigation-top.html) 到搜索服务。<br /> — 全局搜索 — 路由来自 [快速搜索](https://docs.magento.com/user-guide/catalog/search-quick.html) 的 [!DNL Live Search] 服务。 |
| `module-live-search-storefront-popover` | “键入时搜索”弹出窗口取代了标准快速搜索，并返回了热门搜索结果的数据和缩略图。 |

## [!DNL Live Search] 依赖 {#dependencies}

以下 [!DNL Live Search] 依赖项由 [!DNL Composer]:

| 依赖关系 | 描述 |
|--- |--- |
| 导出模块 | 以下模块收集和同步目录数据：<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | 配置与Commerce Services的连接时需要。 |
| `module-services-id` | 配置与Commerce Services的连接时需要。 |
