---
title: ‘[!DNL Live Search] 发行说明
description: “的最新发行信息 [!DNL Live Search] 来自Adobe Commerce。”
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] 发行说明

以下发行说明介绍了最新版本的 [!DNL Live Search].
为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。
更新包括：

![新](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题


_2023年4月25日_

![新](../assets/new.svg) Live Search客户现在可以利用新的 [SaaS价格索引器](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_2023年3月14日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

### 新增功能

* 规则预览中的产品项目卡
* [产品列表页面构件](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [类别筛选选项](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 添加了通过拖放操作创建Pin事件的功能
* 新的Pin操作：
   * 固定至点 — 单击一次即可固定按钮以创建固定事件
   * 固定到顶部 — 将产品放在第一个位置
   * 固定到底部 — 将产品放在结果的底部
   * 只需单击一下即可取消固定事件
* [规则的智能排名](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 更新

* 现在，配置规则会自动对位置进行唯一排序
* 删除现有事件现在会更新预览
* 可以保存没有事件的规则
* 删除彩块化“选择类型”选择器
* 为未保存的规则添加了新的“编辑”状态

### 修复

* 修复了保存过程中存在未完成事件时的服务器错误
* 修复了在存在多个事件时正确删除特定事件的问题
* 修复了在添加新事件后现有规则事件未更新的问题
* 修复了来自详细信息的第二次“编辑”点击， [!DNL Live Search] 需要重新加载的页面
* 同义词：修复了当用户点击退出输入时，无法将焦点返回到字段的问题
* 其他次要错误修复和性能更新


* ![错误](../assets/bug.svg)  — 仅在实时搜索小组件中支持按“为您推荐”进行排名。 默认的Luma和PWA搜索功能不支持此功能。
* ![错误](../assets/bug.svg)  — 自定义价格属性Facet在Luma中无法正确呈现，但API会正确筛选它们。

商家必须升级 [!DNL Live Search] 扩展版本>= 3.0.1以访问这些功能。

建议在推送到生产环境之前进行升级和测试。 在验证其测试环境结果后，请考虑在非高峰时段升级生产环境。

## 以前的版本

+++2.0.5和之前的版本

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

* ![修复](../assets/fix.svg)  — 当SDK资源因网络问题而不可用时，Live Search会引发错误。 此错误已修复。

商家必须升级Live Search扩展版本>= 2.0.5才能访问这些功能。

建议在推送到生产环境之前进行升级和测试。 在验证其测试环境结果后，请考虑在非高峰时段升级生产环境。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) Live Search现在支持通过管理员中的“显示缺货产品”设置进行筛选。 如果“显示缺货产品”设置为false， `inStock = true` 会添加到过滤器中。
![修复](../assets/fix.svg) 为了提高性能，已从“实时搜索”弹出窗口中删除“建议”块。 如果要替换该功能，数据仍会通过GraphQL传递。
![修复](../assets/fix.svg) `categories` 和 `categoryPath` 已替换 `categoryIds` 用于类别筛选。 有关更多信息，请参阅 [产品搜索](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 主题。
![修复](../assets/fix.svg) 以前，与B2B公司绑定的用户在搜索时会收到不正确的客户组代码。 Live Search现在返回正确的值。
![修复](../assets/fix.svg) 以前，在搜索不存在的术语时，Live Search会返回错误。 此错误现已修复。

商家必须升级 [!DNL Live Search] 扩展版本>= 2.0.4以访问这些功能。

建议用户在推送至生产环境之前进行升级和测试。 在验证其测试环境结果后，请考虑在非高峰时段升级生产环境。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) Live Search现在通过遵循类别权限、共享目录和特定于客户组的定价来支持B2B功能。

商家必须升级 [!DNL Live Search] 扩展版本>= 2.0.3以访问这些功能。

建议用户在推送至生产环境之前进行升级和测试。 在验证其测试环境结果后，请考虑在非高峰时段升级生产环境。

### [!DNL Live Search] 2.0 {#20}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

现有 [!DNL Live Search] 安装必须升级到 [!DNL Live Search] 2.0.0以利用以下新功能、修复和改进：

![新](../assets/new.svg) [!DNL Live Search] 现在，对于运行Adobe Commerce 2.4.4的安装，支持PHP 8.1。
![新](../assets/new.svg) 此 `Magento_ElasticsearchCatalogPermissionsGraphQl` 模块会添加到安装期间禁用的模块列表中。
![新](../assets/new.svg) 中可用的行数 [[!DNL storefront popover]](quick-tour.md) 可以从以下位置配置： *管理员*.
![新](../assets/new.svg) 测试版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 兼容性 [!DNL Live Search].
![新](../assets/new.svg) 此 [!DNL Live Search] 安装过程随高级过程更改而更新。
![修复](../assets/fix.svg) [高级搜索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 链接已从店面页脚中移除。
![错误](../assets/bug.svg) 以下产品属性不受支持 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) 在与PWA的Beta版一起使用时： `description`， `name`， `short_description`
![错误](../assets/bug.svg) 的PWA测试版 [!DNL Live Search] 不支持 [事件处理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复](../assets/fix.svg) [自定义价格属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 配置为时，不再返回错误 [Facet]({%链接live-search/facets-add.md %})。
![修复](../assets/fix.svg) 修复了以下情况导致出现错误的问题： [货币符号](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)可用。
![修复](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 现在显示 [特价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最低最终价格）。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) [性能](performance.md) 报表仪表板提供有关购物者使用的搜索词的洞察。
![新](../assets/new.svg) [!DNL Live Search] [店面事件SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 通过事件发布和订阅服务以及量度提供对公共数据层的访问。
![修复](../assets/fix.svg) 此 [[!DNL Storefront popover]](storefront-popover.md) 有新的 `active` 的类 `.search-autocomplete` 控制可见性的容器。
![修复](../assets/fix.svg) 在店面 [搜索词](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 已删除页脚链接，并且已为禁用其缓存 [!DNL Live Search] 安装。
![错误](../assets/bug.svg) Search适配器的修补程序处理重复的产品。
![错误](../assets/bug.svg) [!DNL Live Search] 支持 [单源](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) 具有多个（虚拟）的（物理）盘点地点 [库存](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 现在不支持多个清单源。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 当购物者在“搜索”框中键入查询时，显示推荐的产品和排名最前的搜索结果的缩略图图像。
![新](../assets/new.svg) 商务 *管理员* 在长时间键盘不活动期间，会话保持打开状态
![新](../assets/new.svg) [!DNL Live Search] 载入后自动启用
![修复](../assets/fix.svg) 初始索引时间不到一小时
![修复](../assets/fix.svg) 近乎实时的增量产品更新（安装和设置后）
![修复](../assets/fix.svg) 同义词编辑器中的可排序列
![修复](../assets/fix.svg) [!DNL Live Search] 如果搜索条件包含空的排序顺序值，则不再引发错误
![修复](../assets/fix.svg) 如果属性代码包含字符串“to”或“from”，则范围筛选不再中断

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![错误](../assets/bug.svg) 此 [!DNL Live Search] 服务仅支持 [基础货币](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce安装的信息。
![错误](../assets/bug.svg) 添加Facet时，产品属性信息源在设置为时无法正确更新 `Update on Save`. 要避免出现此问题，请转到 [索引管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 并将产品属性信息源设置为 `Update by Schedule`.
![错误](../assets/bug.svg) [!DNL Live Search] 同义词是按商店视图定义的，但当前按网站存储，并通过以下组合进行标识 `environmentId` 和 `storeViewCode`. 因此，Adobe Commerce安装中的所有网站和存储视图会共享同义词。 最近为存储视图创建的同义词集优先。
![错误](../assets/bug.svg) 如果一个同义词包含多个单词，则每个单词都被视为单独的同义词。 例如，如果将“time piece”定义为“watch”的同义词，则“time”和“piece”均被视为手表的同义词。

+++

## 文档

要了解更多信息，请执行以下操作：

* [Adobe Commerce开发人员文档](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce用户指南](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 在商城上](https://marketplace.magento.com/magento-live-search.html)
