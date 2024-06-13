---
title: “开始使用 [!DNL Live Search]"
description: “了解的系统要求和安装步骤 [!DNL Live Search] 来自Adobe Commerce。”
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '2266'
ht-degree: 0%

---

# 设置以取得成功 [!DNL Live Search]

Adobe Commerce [!DNL Live Search] 和 [[!DNL Catalog Service]](../catalog-service/guide-overview.md) 共同努力提供高性能、相关且直观的搜索解决方案，让您的客户能够快速准确地找到所需的内容。 具体来说， [!DNL Catalog Service] 显示用于SaaS服务的目录数据，例如 [!DNL Live Search] 以使用。

本文提供了关于实施的分步说明 [!DNL Live Search] 替换为 [!DNL Catalog Service].

>[!IMPORTANT]
>
>在网站搜索方面，Adobe Commerce会为您提供各种选项。 请务必阅读 [边界和限制](boundaries-limits.md) 实施之前，确保 [!DNL Live Search] 适合您的业务需求。

## 受众

本文面向负责安装和配置Adobe Commerce实例的开发人员或团队中的系统集成商。

## 要求

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## 支持的平台

- Adobe Commerce on Cloud (ECE) ：2.4.4+
- Adobe Commerce内部部署(EE) ：2.4.4+

## 工作流概述

在高级别，入门 [!DNL Live Search] 要求您：

![实时搜索工作流程](assets/livesearch-workflow.png)

## 1.安装 [!DNL Live Search] 扩展

[!DNL Live Search] 作为扩展从安装 [Adobe市场](https://commercemarketplace.adobe.com/magento-live-search.html) 到 [Composer](https://getcomposer.org/). 安装和配置之后 [!DNL Live Search]，Adobe [!DNL Commerce] 开始与SaaS服务共享搜索和目录数据。 此时， *管理员* 用户可以设置、自定义和管理搜索彩块化、同义词和促销规则。

>[!NOTE]
>
>截至 [!DNL Live Search] 3.0.2， [!DNL Catalog Service] 扩展与捆绑在一起 [!DNL Live Search] 安装。

1. 确认 [cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) 和 [索引器](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 正在运行。

   >[!IMPORTANT]
   >
   >由于Elasticsearch7将于2023年8月宣布终止支持，建议所有Adobe Commerce客户迁移到OpenSearch 2.x搜索引擎。 有关在产品升级期间迁移搜索引擎的信息，请参阅 [迁移到OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) 在 _升级指南_.

1. 下载 `live-search` 来自的包 [Adobe市场](https://commercemarketplace.adobe.com/magento-live-search.html).

1. 从命令行运行以下命令：

   ```bash
   composer require magento/live-search
   ```

   如果您要添加 [!DNL Live Search] 扩展到 **新建** Adobe Commerce安装，请运行以下命令以禁用 [!DNL OpenSearch] 和相关模块，以及安装 [!DNL Live Search]. 然后继续执行步骤4。

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   如果您要添加 [!DNL Live Search] 的扩展 **现有** Adobe Commerce安装后，请运行以下命令以暂时禁用 [!DNL Live Search] 提供店面搜索结果的模块。 然后继续执行步骤4：

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] 继续管理店面的搜索请求，同时 [!DNL Live Search] 服务在后台同步目录数据和索引产品。

1. 运行以下命令：

   ```bash
   bin/magento setup:upgrade
   ```

1. 验证以下各项 [索引器](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 设置为“按计划更新”：

   - 产品信息源
   - 产品变型馈送
   - 目录属性信息源
   - 产品价格信息源
   - 范围网站数据馈送
   - 范围客户组数据馈送
   - 类别信息源
   - 类别权限信息源

1. 如果您正在安装 [!DNL Live Search] 在新的Commerce实例上，您已完成，可以跳至 [2. 配置API密钥](#2-configure-api-keys) 部分。 如果您要将Live Search安装到现有Commerce实例，请继续执行下一步。

1. 运行以下命令以启用 [!DNL Live Search] 扩展，禁用 [!DNL OpenSearch]，并运行 `setup`.

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

## 2.配置API密钥

需要Adobe Commerce API密钥及其关联的私钥才能连接 [!DNL Live Search] 到Adobe Commerce的安装。 API密钥在的帐户中生成和维护 [!DNL Commerce] 许可证持有者，可与开发人员或系统集成商共享。 然后，开发人员可以代表许可证持有人创建和管理SaaS数据空间。 如果您已经有一组API密钥，则无需重新生成它们。

了解如何在中配置API密钥 [Commerce服务连接器](../landing/saas.md) 文章。

## 3.同步您的目录数据 {#synchronize-catalog-data}

[!DNL Live Search] 将目录数据移动到Adobe的SaaS基础架构。 数据被编入索引，搜索结果从此索引直接传送到店面。 根据大小和复杂性，索引可能需要30分钟到几个小时。

要开始将目录数据初始同步到SaaS服务，请按照以下顺序运行以下命令：

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

运行这些命令时，将开始将目录数据与SaaS服务进行初始同步。

>[!WARNING]
>
> 当数据已编制索引并同步时，店面中无法使用搜索和类别浏览操作。 根据目录的大小，此过程可能至少需要一个小时 `cron` 运行以将数据同步到SaaS服务。

### 监视器同步进度

您可以使用查看已同步和共享的数据 [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). 此仪表板提供关于您店面产品数据可用性的宝贵见解，确保可及时向购物者显示这些数据。

![数据管理功能板](assets/data-management-dashboard.png)

#### 将来的产品更新

初始同步后，增量产品更新最多可能需要15分钟才能用于店面搜索。 要了解更多信息，请参阅 [索引 — 流式产品更新](indexing.md).

## 4.验证是否已导出数据 {#verify-export}

验证是否已从Adobe Commerce实例导出目录数据并且已为其同步： [!DNL Live Search]，您有几个选项：

- 在以下表中查找条目：

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- 使用 [GraphQL游乐场](https://developer.adobe.com/commerce/services/graphql/live-search/) 以验证以下内容：

   - 返回的产品计数接近您对商店视图的预期。
   - 将返回Facet。

有关其他帮助，请参阅 [[!DNL Live Search] 目录未同步](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) 在支持知识库中。

## 5.配置数据

正确配置产品数据可确保为您的客户获得良好的搜索结果。 在此部分中，您可以启用产品列表构件并分配类别。

### 启用产品列表小组件

安装时 [!DNL Live Search] 4.0.0及更高版本默认情况下启用产品列表小组件。 启用小组件后，将对搜索结果页面和类别浏览产品列表页面使用不同的UI组件。 此UI组件直接调用 [目录服务API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/)，这将缩短响应时间。

如果您拥有 [!DNL Live Search] 低于4.0.0+版本，您需要手动启用产品列表构件。

1. 从 *管理员*，转到 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 下 **[!UICONTROL Live Search]**，选择 **[!UICONTROL Storefront Features]**.
1. 设置 **[!UICONTROL Enable Product Listing Widgets]** 到 `Yes`.

   ![启用产品列表小组件](assets/ls-admin-enable-widget.png)

更改此配置时，将显示以下消息： `Page cache is invalidated` 显示。 您需要刷新Magento缓存以保存更改。

1. 访问 [缓存管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) 执行下列操作之一，创建页面：

   - 单击 **[!UICONTROL Cache Management]** 工作区上方消息中的链接。
   - 在 _管理员_ 侧栏，转到 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. 选择 **配置** [!UICONTROL Cache Type] 并单击 **[!UICONTROL Flush Magento Cache]**.

   刷新缓存后，立即对店面进行更改。

### 分配类别

产品返回于 [!DNL Live Search] 必须分配给 [类别](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). 例如，在Luma中，产品被划分为“男性”、“女性”和“齿轮”等类别。 “Top”、“Bottoms”和“Watches”也设置了子类别。 这可以提高筛选时的粒度。

## 6.测试连接 {#test-connection}

现在，在SaaS中使用目录数据，测试以确保在以下情况下返回产品数据：

- 此 [!UICONTROL Search] 框正确返回结果
- 类别浏览正确返回结果
- Facet在搜索结果页面上可用作过滤器

如果一切正常， [!DNL Live Search] 已安装、已连接并已准备就绪。

如果您在店面中遇到问题，请检查 `var/log/system.log` API通信失败或服务端错误的文件。

允许 [!DNL Live Search] 通过防火墙，添加 `commerce.adobe.io` 给允许列表。

## 7.针对您的店面进行定制

您已安装 [!DNL Live Search] 扩展、同步、验证和配置您的数据。 现在，您需要确保 [!DNL Live Search] 构件符合您商店的外观。

您可以根据需要通过定义自定义CSS规则来设置弹出框和PLP小组件的样式。 请参阅 [样式弹出框元素](storefront-popover-styling.md) 和 [产品列表页面小组件](plp-styling.md).

如果您希望扩展小组件的功能，则每个小组件的源代码在公共存储库中可用。
在此方案中，您可以根据自己的需求自定义JavaScript，然后将自定义代码托管在CDN上。 此自定义脚本与 [!DNL Live Search] 并返回正常结果，使您能够控制小组件的功能。

- [PLP构件存储库](https://github.com/adobe/storefront-product-listing-page)
- [搜索栏存储库](https://github.com/adobe/storefront-search-as-you-type)

## 正在更新 [!DNL Live Search] {#update}

在更新Live Search之前，请从命令行运行以下命令以检查已安装的Live Search版本：

```bash
composer show magento/module-live-search | grep version
```

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

1. 保存 `composer.json`. 然后，从命令行运行以下命令：

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 正在卸载 [!DNL Live Search] {#uninstall}

卸载 [!DNL Live Search]，请参阅 [卸载模块](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] 包 {#packages}

此 [!DNL Live Search] 扩展包含以下包：

| 包 | 描述 |
|--- |--- |
| `module-live-search` | 允许商家配置其搜索设置以进行分面、同义词、查询规则等，并提供对只读GraphQL游乐场的访问权限，以测试来自 *管理员*. |
| `module-live-search-adapter` | 将搜索请求从店面路由到 [!DNL Live Search] 服务，并在店面中呈现结果。 <br /> — 类别浏览 — 从店面路由请求 [顶部导航](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) 搜索服务。<br /> — 全局搜索 — 路由来自的请求 [快速搜索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 位于店面右上角的盒子 [!DNL Live Search] 服务。 |
| `module-live-search-storefront-popover` | “键入时搜索”弹出框取代了标准快速搜索，并返回排名最前的搜索结果的数据和缩略图。 |

## [!DNL Live Search] 依赖关系 {#dependencies}

以下各项 [!DNL Live Search] 依赖项由捕获 [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## 高级概念

以下部分提供了在使用时 [!DNL Live Search] 和 [!DNL Catalog Service].

### 端点

[!DNL Live Search] 通过上的端点通信 `https://catalog-service.adobe.io/graphql`.

作为 [!DNL Live Search] 没有访问完整产品数据库的权限， [!DNL Live Search] GraphQL和Commerce核心GraphQL不具备完全对等性。

建议直接调用SaaS API — 特别是目录服务端点。

- 通过绕过Commerce数据库/Graphql进程来提高性能并降低处理器负载
- 利用 [!DNL Catalog Service] 要调用的联盟 [!DNL Live Search]， [!DNL Catalog Service]、和 [!DNL Product Recommendations] 从单个端点删除。

对于某些用例，调用 [!DNL Catalog Service] 产品详细信息和类似案例。 请参阅 [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) 以了解更多信息。

如果您有自定义Headless实施，请查看 [!DNL Live Search] 参考实施：

- [PLP小组件](https://github.com/adobe/storefront-product-listing-page)
- [实时搜索字段](https://github.com/adobe/storefront-search-as-you-type)

如果您未使用默认组件(如Luma上的搜索适配器或小组件，或AEM CIF小组件)，事件(为Adobe Sensei提供智能推销和性能量度的点击流数据)将无法开箱即用，并且需要自定义开发来实施headless事件。

最新版本的 [!DNL Live Search] 已使用 [!DNL Catalog Service].

### 语言支持

[!DNL Live Search] 小组件支持以下语言：

|  |  |  |  |
|--- |--- |--- |--- |
| 语言 | 区域 | 语言代码 | Magento区域设置 |
| 保加利亚语 | 保加利亚 | bg_BG | bg_BG |
| 加泰罗尼亚语 | 西班牙 | ca_ES | ca_ES |
| 捷克语 | 捷克共和国 | cs_CZ | cs_CZ |
| 丹麦语 | 丹麦 | da_DK | da_DK |
| 德语 | 德国 | de_DE | de_DE |
| 希腊语 | 希腊 | el_GR | el_GR |
| 英语 | 英国 | en_GB | en_GB |
| 英语 | 美国 | en_US | en_US |
| 西班牙语 | 西班牙 | es_ES | es_ES |
| 爱沙尼亚语 | 爱沙尼亚 | et_EE | et_EE |
| 巴斯克语 | 西班牙 | eu_ES | eu_ES |
| 波斯语 | 伊朗 | fa_IR | fa_IR |
| 芬兰语 | 芬兰 | fi_FI | fi_FI |
| 法语 | 法国 | fr_FR | fr_FR |
| 加利西亚语 | 西班牙 | gl_ES | gl_ES |
| 印地语 | 印度 | hi_IN | hi_IN |
| 匈牙利语 | 匈牙利 | hu_HU | hu_HU |
| 印尼语 | 印度尼西亚 | id_ID | id_ID |
| 意大利语 | 意大利 | it_IT | it_IT |
| 朝鲜语 | 韩国 | ko_KR | ko_KR |
| 立陶宛语 | 立陶宛 | lt_LT | lt_LT |
| 拉脱维亚语 | 拉脱维亚 | lv_LV | lv_LV |
| 挪威语 | 挪威博克马尔语 | nb_NO | nb_NO |
| 荷兰语 | 荷兰 | nl_NL | nl_NL |
| 波兰语 | 波兰 | pl_PL | pl_PL |
| 葡萄牙语 | 巴西 | pt_BR | pt_BR |
| 葡萄牙语 | 葡萄牙 | pt_PT | pt_PT |
| 罗马尼亚语 | 罗马尼亚 | ro_RO | ro_RO |
| 俄语 | 俄罗斯 | ru_RU | ru_RU |
| 瑞典语 | 瑞典 | sv_SE | sv_SE |
| 泰语 | 泰国 | th_TH | th_TH |
| 土耳其语 | 土耳其 | tr_TR | tr_TR |
| 中文 | 中国 | zh_CN | zh_Hans_CN |
| 中文 | 台湾 | zh_TW | zh_Hant_TW |

如果构件检测到Commerce管理语言设置(_商店_ >设置> _配置_ > _常规_ >国家/地区选项)与支持的语言匹配，默认为该语言。 否则，小组件将默认使用英语。

管理员还可以设置 [搜索索引](settings.md#language)，以帮助确保获得更好的搜索结果。

### 构件代码存储库

产品列表页面构件和实时搜索字段构件均可以从其github存储库下载。

这允许开发人员完全自定义功能和样式。 这些用户自行托管代码，同时仍利用 [!DNL Live Search] 服务。

- [PLP小组件](https://github.com/adobe/storefront-product-listing-page)
- [搜索栏](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] 支持 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerce中的功能（以前称为多源清单，或MSI）。 要启用全面支持，您必须 [更新](install.md#update) 依赖关系模块 `commerce-data-export` 到版本102.2.0+。

[!DNL Live Search] 返回一个布尔值，表明某个产品在Inventory management中是否可用，但不包含有关哪个来源具有库存的信息。

### 价格索引器

Live Search客户可以使用新的 [SaaS价格索引器](../price-index/price-indexing.md)，可以加快价格变更更新和同步时间。

### 价格支持

Live Search小组件支持Adobe Commerce支持的大多数价格类型，但不是所有价格类型。

目前支持基本价格。 不受支持的高级价格包括：

- 成本
- 最低广告价格

查看 [API网格](../catalog-service/mesh.md) 进行更复杂的价格计算。

价格格式支持Commerce实例中的区域设置配置设置： *商店* >设置> *配置* >常规> *常规* >本地选项>区域设置。

### Headless店面支持

或者，您可能需要安装 `module-data-services-graphql` 模块，用于扩展应用程序的现有GraphQL覆盖范围，以包含店面行为数据收集所需的字段。

```bash
composer require magento/module-data-services-graphql
```

此模块可向GraphQL查询添加其他上下文：

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### B2B支持

[!DNL Live Search] 支持 [B2B功能](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) 附加 [限制](boundaries-limits.md#b2b-and-category-permissions).

### PWA支持

[!DNL Live Search] 可与PWA Studio配合使用，但用户可能会看到与其他Commerce实施相比的细微差异。 在威尼亚省可以使用搜索和产品列表页面等基本功能，但Graphql的某些排列可能无法正常工作。 此外，可能存在性能差异。

- 的当前PWA实现 [!DNL Live Search] 返回搜索结果所需的处理时间大于 [!DNL Live Search] 与原生Commerce店面合作。
- [!DNL Live Search] PWA不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 因此，搜索报表和智能促销都将正常工作。
- 直接筛选 `description`， `name`， `short_description` GraphQL不支持与一起使用 [PWA](https://developer.adobe.com/commerce/pwa-studio/)，但会使用更一般的过滤器返回它们。

使用 [!DNL Live Search] 对于PWA Studio，集成商还必须：

1. 安装 [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. 设置 `environmentId` 在 `storeDetails` 对象。

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] 收集用户交互数据作为其基本功能的一部分，并且Cookie用于存储此数据。 在收集任何用户信息时，用户必须同意存储Cookie。 [!DNL Live Search] 和 [!DNL Product Recommendations] 共享数据流，因此使用相同的Cookie机制。 有关更多信息，请参阅 [处理Cookie限制](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
