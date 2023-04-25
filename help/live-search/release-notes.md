---
title: '[!DNL Live Search] 发行说明'
description: “ [!DNL Live Search] 来自Adobe Commerce。”
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 6371d737ef9591e4ad647650c9c9974dbd8b4555
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# [!DNL Live Search] 发行说明

以下发行说明介绍了 [!DNL Live Search] 包括：

![新建](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题


_2023年4月25日_

![新建](../assets/new.svg) Live Search客户现在可以利用 [SaaS价格索引器](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

### 新增功能

* “规则”预览中的产品项目卡
* [产品列表页面小组件](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [类别筛选选项](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 添加了拖放功能以创建固定事件
* 新的固定操作：
   * 固定到专用位置 — 通过单击一次即可创建“固定”事件的“固定”按钮
   * 固定到顶部 — 将产品放在首位
   * 固定到底部 — 将产品放在结果的底部
   * 通过一次单击取消固定事件
* [规则的智能排名](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 更新

* “配置规则”现在会自动对位置进行唯一排序
* 删除现有事件现在会更新预览
* 无法保存没有事件的规则
* 删除分面“选择类型”选择器
* 为未保存的规则添加了新的“编辑”状态

### 修复

* 修复了在保存期间发生未完成事件时的服务器错误
* 修复了当存在多个事件时正确删除特定事件的问题
* 修复了在添加新事件时不更新现有规则事件的问题
* 修复了在详细信息中第二次“编辑”点击时， [!DNL Live Search] 页面需要重新加载
* 同义词：修复了用户点击退出输入后无法将焦点返回到字段的问题
* 其他小错误修复和性能更新


* ![错误](../assets/bug.svg)  — 仅在实时搜索小组件中支持按“为您推荐”进行排名。 默认的Luma和PWA搜索功能不支持此功能。
* ![错误](../assets/bug.svg)  — 自定义价格属性Facet无法在Luma中正确呈现，但API会对这些Facet进行正确筛选。

商家必须升级 [!DNL Live Search] 扩展版本>= 3.0.1以访问这些功能。

建议在推送到生产环境之前先进行升级和测试。 在验证其测试环境结果后，考虑在非高峰时间升级生产环境。

## 早期版本

+++2.0.5及更低版本

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![修复](../assets/fix.svg)  — 当SDK资源由于网络问题而不可用时，实时搜索将引发错误。 此错误已修复。

商户必须升级实时搜索扩展版本>= 2.0.5才能访问这些功能。

建议在推送到生产环境之前先进行升级和测试。 在验证其测试环境结果后，考虑在非高峰时间升级生产环境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 现在，实时搜索支持通过管理员中的“显示无现货产品”设置进行过滤。 如果“显示缺货产品”设置为false， `inStock = true` 会添加到过滤器。
![修复](../assets/fix.svg) 为了提高性能，已从“实时搜索”弹出窗口中删除“建议”块。 如果要替换该功能，数据仍会通过GraphQL进行传递。
![修复](../assets/fix.svg) `categories` 和 `categoryPath` 已更换 `categoryIds` ，以便进行类别筛选。 有关更多信息，请参阅 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主题。
![修复](../assets/fix.svg) 以前，与B2B公司绑定的用户在执行搜索时会收到错误的客户组代码。 现在，实时搜索会返回正确的值。
![修复](../assets/fix.svg) 以前，在搜索不存在的术语时，实时搜索将返回错误。 该错误现已修复。

商家必须升级 [!DNL Live Search] 扩展版本>= 2.0.4以访问这些功能。

建议用户在推送到生产环境之前先进行升级和测试。 在验证其测试环境结果后，考虑在非高峰时间升级生产环境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) 现在， Live Search通过尊重类别权限、共享目录和特定于客户组的定价来支持B2B功能。

商家必须升级 [!DNL Live Search] 扩展版本>= 2.0.3以访问这些功能。

建议用户在推送到生产环境之前先进行升级和测试。 在验证其测试环境结果后，考虑在非高峰时间升级生产环境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

现有 [!DNL Live Search] 安装必须升级到 [!DNL Live Search] 2.0.0可利用以下新增功能、修复和改进功能：

![新建](../assets/new.svg) [!DNL Live Search] 现在，运行Adobe Commerce 2.4.4的安装支持PHP 8.1。
![新建](../assets/new.svg) 的 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模块会添加到安装过程中禁用的模块列表。
![新建](../assets/new.svg) 中的可用行数 [[!DNL storefront popover]](quick-tour.md) 可以通过 *管理员*.
![新建](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) 兼容性 [!DNL Live Search].
![新建](../assets/new.svg) 的 [!DNL Live Search] 安装过程会更新高级过程更改。
![修复](../assets/fix.svg) [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 链接已从storefront footer中删除。
![错误](../assets/bug.svg) 不支持以下产品属性 [商务GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 与测试版PWA相关时： `description`, `name`, `short_description`
![错误](../assets/bug.svg) 测试版PWA [!DNL Live Search] 不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) [自定义价格属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 当配置为 [面]({% link live-search/facets-add.md %})。
![修复](../assets/fix.svg) 修复了导致在没有 [货币符号](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)可用。
![修复](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 现在显示 [特价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最低最终价格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) [性能](performance.md) 报表功能板提供有关购物者使用的搜索词的分析。
![新建](../assets/new.svg) [!DNL Live Search] [Storefront事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 通过事件发布和订阅服务以及量度，提供对常用数据层的访问。
![修复](../assets/fix.svg) 的 [[!DNL Storefront popover]](storefront-popover.md) 具有新 `active` 类 `.search-autocomplete` 可控制可见性的容器。
![修复](../assets/fix.svg) 在店面， [搜索词](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 页脚链接已删除，且其缓存已禁用 [!DNL Live Search] 安装。
![错误](../assets/bug.svg) Search适配器的修补程序可处理重复产品。
![错误](../assets/bug.svg) [!DNL Live Search] 支持 [单源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) 具有多个（虚拟）库存位置的（实际）库存位置 [股票](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 当前不支持多个库存源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 当购物者在“搜索”框中键入查询时，显示热门搜索结果的建议产品和缩略图。
![新建](../assets/new.svg) 商务 *管理员* 会话在键盘长时间不活动期间保持打开状态
![新建](../assets/new.svg) [!DNL Live Search] 载入后自动启用
![修复](../assets/fix.svg) 初始索引时间不到1小时
![修复](../assets/fix.svg) 近乎实时的增量产品更新（安装和设置后）
![修复](../assets/fix.svg) 同义词编辑器中的可排序列
![修复](../assets/fix.svg) [!DNL Live Search] 如果搜索标准包含空排序顺序值，则不再引发错误
![修复](../assets/fix.svg) 如果属性代码包含字符串“to”或“from”，则范围过滤不再中断

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![错误](../assets/bug.svg) 的 [!DNL Live Search] 服务仅支持 [基本货币](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce装置。
![错误](../assets/bug.svg) 添加Facet时，如果将设置为 `Update on Save`. 要避免出现此问题，请转到 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 和将产品属性信息源设置为 `Update by Schedule`.
![错误](../assets/bug.svg) [!DNL Live Search] 同义词是在每个商店视图中定义的，但当前是按每个网站存储的，并通过组合标识 `environmentId` 和 `storeViewCode`. 因此，所有网站和Adobe Commerce安装内的视图都共享同义词。 优先使用最近为存储视图创建的一组同义词。
![错误](../assets/bug.svg) 如果同义词词包含多个词，则每个词都被视为单独的同义词。 例如，如果将“time pice”定义为“watch”的同义词，则“time”和“piece”都将被视为watch的同义词。

+++

## 文档

要了解更多信息：

* [Adobe Commerce开发人员文档](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce用户指南](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] Marketplace上](https://marketplace.magento.com/magento-live-search.html)
