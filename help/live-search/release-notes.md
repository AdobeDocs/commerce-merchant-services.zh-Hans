---
title: 实时搜索发行说明
description: 有关Adobe Commerce中实时搜索的最新发行信息。
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 65126f10574801f7ea8d0a863e9bb512dca13f39
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 1%

---

# [!DNL Live Search] 发行说明

以下发行说明介绍了 [!DNL Live Search] 包括：

* ![新建](../assets/new.svg)  — 新增功能
* ![修复](../assets/fix.svg)  — 修复和改进功能
* ![错误](../assets/bug.svg)  — 已知问题

## [!DNL Live Search] 2.0

* 与Adobe Commerce(EE)兼容：2.4.x
* 与Adobe Commerce for Cloud(ECE)兼容：2.4.x
* 稳定性：稳定

现有 [!DNL Live Search] 安装必须升级到 [!DNL Live Search] 2.0.0可利用以下新增功能、修复和改进功能：

* ![新建](../assets/new.svg) - [!DNL Live Search] 现在，运行Adobe Commerce 2.4.4的安装支持PHP 8.1。
* ![新建](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` 模块会添加到安装过程中禁用的模块列表。
* ![新建](../assets/new.svg) - [[!DNL storefront popover]](quick-tour.md) 可以通过 *管理员*.
* ![新建](../assets/new.svg)  — 测试版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 兼容性 [!DNL Live Search].
* ![新建](../assets/new.svg) - [!DNL Live Search] 安装过程会更新高级过程更改。
* ![修复](../assets/fix.svg) - [高级搜索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 链接已从storefront footer中删除。
* ![错误](../assets/bug.svg)  — 不支持以下产品属性 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql) 与测试版PWA相关时： `description`, `name`, `short_description`
* ![错误](../assets/bug.svg)  — 测试版PWA [!DNL Live Search] 不支持 [事件处理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* 与Adobe Commerce(EE)兼容：2.4.x
* 与Adobe Commerce for Cloud(ECE)兼容：2.4.x
* 稳定性：稳定

* ![修复](../assets/fix.svg) - [自定义价格属性](https://docs.magento.com/user-guide/stores/attributes-input-types.html) 当配置为 [面]({% link live-search/facets-add.md %})。
* ![修复](../assets/fix.svg)  — 修复了在没有 [货币符号](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`)可用。
* ![修复](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 现在显示 [特价](https://docs.magento.com/user-guide/catalog/product-price-special.html) （最低最终价格）。

## [!DNL Live Search] 1.3.0

* 与Adobe Commerce(EE)兼容：2.4.x
* 与Adobe Commerce for Cloud(ECE)兼容：2.4.x
* 稳定性：稳定

* ![新建](../assets/new.svg) - [性能](performance.md) 报表功能板提供有关购物者使用的搜索词的分析。
* ![新建](../assets/new.svg) - [!DNL Live Search] [Storefront事件SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 通过事件发布和订阅服务以及量度，提供对常用数据层的访问。
* ![修复](../assets/fix.svg) - [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) 具有新 `active` 类 `.search-autocomplete` 可控制可见性的容器。
* ![修复](../assets/fix.svg)  — 在店面， [搜索词](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) 页脚链接已删除，且其缓存已禁用 [!DNL Live Search] 安装。
* ![错误](../assets/bug.svg) - Search适配器的修补程序处理重复产品。
* ![错误](../assets/bug.svg) - [!DNL Live Search] 支持 [单源](https://docs.magento.com/user-guide/catalog/inventory-sources.html) 具有多个（虚拟）库存位置的（实际）库存位置 [股票](https://docs.magento.com/user-guide/catalog/inventory-stock.html). 当前不支持多个库存源。

## [!DNL Live Search] 1.2.0

* 与Adobe Commerce(EE)兼容：2.4.x
* 与Adobe Commerce for Cloud(ECE)兼容：2.4.x
* 稳定性：稳定

* ![新建](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) 当购物者在“搜索”框中键入查询时，显示热门搜索结果的建议产品和缩略图。
* ![新建](../assets/new.svg)  — 商务 *管理员* 会话在键盘长时间不活动期间保持打开状态
* ![新建](../assets/new.svg) - [!DNL Live Search] 载入后自动启用
* ![修复](../assets/fix.svg)  — 初始索引时间不到1小时
* ![修复](../assets/fix.svg)  — 近乎实时的增量产品更新（安装和设置后）
* ![修复](../assets/fix.svg)  — 同义词编辑器中的可排序列
* ![修复](../assets/fix.svg) - [!DNL Live Search] 如果搜索标准包含空排序顺序值，则不再引发错误
* ![修复](../assets/fix.svg)  — 如果属性代码包含字符串“to”或“from”，则范围筛选不再中断

## [!DNL Live Search] 1.1.0

* 与Adobe Commerce(EE)兼容：2.4.x
* 与Adobe Commerce for Cloud(ECE)兼容：2.4.x
* 稳定性：稳定

* ![错误](../assets/bug.svg) - [!DNL Live Search] 服务仅支持 [基本货币](https://docs.magento.com/user-guide/stores/currency-configuration.html) Adobe Commerce装置。
* ![错误](../assets/bug.svg)  — 添加Facet时，如果将设置为 `Update on Save`. 要避免出现此问题，请转到 [索引管理](https://docs.magento.com/user-guide/system/index-management.html) 和将产品属性信息源设置为 `Update by Schedule`.
* ![错误](../assets/bug.svg) - [!DNL Live Search] 同义词是在每个商店视图中定义的，但当前是按每个网站存储的，并通过组合标识 `environmentId` + `storeViewCode`. 因此，Adobe Commerce安装中的所有网站和存储视图共享相同的同义词集。 优先使用最近为存储视图创建的一组同义词。
* ![错误](../assets/bug.svg)  — 如果同义词词包含多个词，则每个词都被视为单独的同义词。 例如，如果将“time pice”定义为“watch”的同义词，则“time”和“piece”都将被视为watch的同义词。

## 文档

要了解更多信息：

* [Adobe Commerce开发人员文档](https://devdocs.magento.com/)
* [Adobe Commerce用户指南](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] Marketplace上](https://marketplace.magento.com/magento-live-search.html)
