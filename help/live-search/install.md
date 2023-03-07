---
title: '"安装 [!DNL Live Search]”'
description: “了解如何安装、更新和卸载 [!DNL Live Search] 来自Adobe Commerce。”
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 0%

---

# 安装 [!DNL Live Search]

Live Search作为扩展安装在Adobe商城中。 在 [!DNL Live Search] 模块（将目录模块作为依赖项）安装并配置， [!DNL Commerce] 开始与SaaS服务共享搜索和目录数据。 此时， *管理员* 用户可以设置、自定义和管理搜索彩块化、同义词和促销规则。

本主题提供了执行以下操作的说明：

* 安装 [!DNL Live Search] （方法1和2）
* [更新 [!DNL Live Search]](#update)
* [卸载 [!DNL Live Search]](#uninstall)

## 开始之前 {#before-you-begin}

执行以下操作：

1. 确认 [cron作业](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 和 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 正在运行。

1. 选择符合您要求的载入方法并按照说明操作。

   * [方法1](#method-1)：安装，不安装 [!DNL Elasticsearch]
   * [方法2](#method-2)：使用安装 [!DNL Elasticsearch] （无停机）

## 方法1：不使用Elasticsearch安装 {#method-1}

安装时建议使用此载入方法 [!DNL Live Search] 更改为：

* 新 [!DNL Commerce] 安装
* 暂存环境

在此场景中，店面操作因以下原因中断： [!DNL Live Search] 服务索引目录中的所有产品。 在安装过程中， [!DNL Live Search] 模块已启用，并且 [!DNL Elasticsearch] 模块已禁用。

>[!NOTE]
>
>自2023年3月起，Live Search仅支持版本2.4.4及更高版本。

1. 安装Adobe Commerce 2.4.4+，不安装 [!DNL Live Search].

1. 要下载 `live-search` 软件包中，从命令行运行以下命令：

   ```bash
   composer require magento/live-search
   ```

   有关更多信息，请参阅 [!DNL Live Search] [依赖关系](#dependencies) 由捕获的 [!DNL Composer].

1. 运行以下命令以禁用 [!DNL Elasticsearch] 和相关模块，以及安装 [!DNL Live Search]：

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 当数据被索引并同步时，搜索和类别浏览操作在店面中不可用。 根据目录的大小，此过程可能至少需要一个小时 `cron` 运行以将数据同步到 [!DNL Live Search] 服务。

1. 验证以下各项 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 设置为 `Update by Schedule`：

   * 产品信息源
   * 产品变体馈送
   * 目录属性信息源

1. 配置您的 [API密钥](#configure-api-keys) 并验证您的目录数据是否为 [已同步](#synchronize-catalog-data) 替换为 [!DNL Live Search] 服务。

1. 要使Facet可用作店面中的过滤器，请添加 [彩块化](facets-add.md) 根据 [分面要求](facets.md).

   您应该能够在以下时间后添加Facet `cron` 运行属性馈送和导出属性元数据。

1. 之后至少等待一小时 `cron` 运行以同步数据。 那么， [验证](#verify-export) 已导出数据。

1. [测试](#test-the-connection) 店面的连接。

## 方法2：使用Elasticsearch安装 {#method-2}

安装时建议使用此载入方法 [!DNL Live Search] 至：

* 现有生产 [!DNL Commerce] 安装

在此方案中， [!DNL Elasticsearch] 临时管理来自店面的搜索请求，同时 [!DNL Live Search] 服务会在后台对所有产品编制索引，而不会中断正常店面操作。 [!DNL Elasticsearch] 已禁用，并且 [!DNL Live Search] 在对所有目录数据进行索引和同步后启用。

>[!TIP]
>
>要避免键入错误，请将鼠标悬停在代码框的最右侧，单击 [!UICONTROL **复制**] 链接，并将其粘贴到命令行中。

1. 要下载 `live-search` 软件包中，从命令行运行以下命令：

   ```bash
   composer require magento/live-search
   ```

   有关更多信息，请参阅 [!DNL Live Search] [依赖关系](#live-search-dependencies) 由捕获的 [!DNL Composer].

1. 运行以下命令以暂时禁用 [!DNL Live Search] 提供店面搜索结果的模块。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 继续管理来自店面的搜索请求，同时 [!DNL Live Search] 服务在后台同步目录数据和索引产品。

1. 验证以下各项 [索引器](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 设置为 `Update by Schedule`：

   * 产品信息源
   * 产品变体馈送
   * 目录属性信息源

1. 配置您的 [API密钥](#configure-api-keys) 并验证您的目录数据是否为 [已同步](#synchronize-catalog-data) 替换为 [!DNL Live Search] 服务。

1. 要使Facet可用作店面中的过滤器，请添加 [彩块化](facets-add.md) 根据 [分面要求](facets.md).

   您应该能够在以下时间后添加Facet `cron` 运行产品和属性信息源，并将属性元数据导出到 [!DNL Live Search] 服务。

1. 至少等待一小时，以便数据编制索引并同步。 然后，使用 [GraphQL运动场](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) 以验证以下内容：

   * 返回的产品计数接近您对商店视图的预期。
   * 返回Facet。

1. 运行以下命令以启用 [!DNL Live Search] 模块，禁用 [!DNL Elasticsearch]，并运行 `setup`.

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

连接需要Adobe Commerce API密钥及其关联的私钥 [!DNL Live Search] 到Adobe Commerce的安装。 API密钥是在的帐户中生成和维护的 [!DNL Commerce] 许可证持有者，可与开发人员或SI共享该许可证。 然后，开发人员可以代表许可证持有人创建和管理SaaS数据空间。  如果您已经有一组API密钥，则无需重新生成它们。

### Adobe Commerce许可证持有者

要生成API密钥和私钥，请参阅 [商务服务连接器](../landing/saas.md).

### Adobe Commerce开发人员或SI

开发人员或SI会配置SaaS数据空间，如 *Commerce服务* 部分。 在 *管理员*，Commerce Services将可用于 *配置* 侧栏（安装SaaS模块时）。

## 同步目录数据 {#synchronize-catalog-data}

[!DNL Live Search] 搜索操作需要同步的产品数据，而配置Facet需要同步属性数据。 产品目录与目录服务之间的初始同步始于 [!DNL Live Search] 第一次连接。 根据目录的安装方法和大小，导出和索引数据最多可能需要8小时 [!DNL Live Search]. 在架构中可以找到与目录服务同步和共享的数据列表，架构定义于：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 验证导出 {#verify-export}

验证目录数据是否已从Adobe Commerce实例导出并为以下项同步： [!DNL Live Search]，请在以下表中查找条目：

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

有关其他帮助，请参阅 [[!DNL Live Search] 目录未同步](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync.html) 支持知识库中的。

### 将来的产品更新

初始同步后，增量产品更新最多可能需要15分钟才能用于店面搜索。 要了解更多信息，请转到 [索引 — 流式产品更新](indexing.md).

## 测试连接 {#test-connection}

在店面，验证以下内容：

* 此 [!UICONTROL Search] 框正确返回结果
* 类别浏览正确返回结果
* 可在搜索结果页面上将Facet作为过滤器使用

如果一切运行正常，恭喜您！ [!DNL Live Search] 已安装、已连接并已准备就绪。

如果您在店面遇到问题，请检查 `var/log/system.log` API通信失败或服务端错误的文件。

## 检查已安装的版本

在更新Live Search之前，请从命令行运行以下命令，以检查当前安装的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

## 正在更新 [!DNL Live Search] {#update}

要更新 [!DNL Live Search]，从命令行运行以下命令：

```bash
composer update magento/live-search --with-dependencies
```

要更新到主要版本（例如从1.0.0到2.0.0），请编辑项目的根 [!DNL Composer] `.json` 文件如下所示：

1. 如果您当前已安装 `magento/live-search` 版本为 `1.3.1` 或更低版本，并且您正在升级到版本 `2.0.0` 或更高版本，请在升级之前运行以下命令：

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   有关当前安装的信息 `magento/live-search` 版本，运行以下命令：

   ```bash
   composer show magento/live-search
   ```

1. 打开根 `composer.json` 文件和搜索 `magento/live-search`.

1. 在 `require` 部分，按如下方式更新版本号：

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 然后，从命令行运行以下命令：

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## 正在卸载 [!DNL Live Search] {#uninstall}

卸载 [!DNL Live Search]，请参阅 [卸载模块](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] 包 {#packages}

| 包 | 描述 |
|--- |--- |
| `module-live-search` | 允许商家为其搜索设置配置分面、同义词、查询规则等，并提供对只读GraphQL游乐场的访问权限，以测试来自 *管理员*. |
| `module-live-search-adapter` | 将搜索请求从店面路由到 [!DNL Live Search] 服务并渲染店面中的结果。 <br /> — 类别浏览 — 从店面路由请求 [顶部导航](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 到搜索服务。<br /> — 全局搜索 — 路由来自的请求 [快速搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 方框的右上角的100%的区域 [!DNL Live Search] 服务。 |
| `module-live-search-storefront-popover` | “键入时搜索”弹出窗口取代了标准快速搜索，并返回热门搜索结果的数据和缩略图。 |

## [!DNL Live Search] 依赖关系 {#dependencies}

以下各项 [!DNL Live Search] 依赖项由捕获 [!DNL Composer]：

| 依赖关系 | 描述 |
|--- |--- |
| 导出模块 | 以下模块收集并同步目录数据：<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | 需要配置与Commerce Services的连接。 |
| `module-services-id` | 需要配置与Commerce Services的连接。 |
