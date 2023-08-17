---
title: '"[!DNL Live Search] 索引”'
description: “了解如何 [!DNL Live Search] 索引产品属性属性。”
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 索引

产品属性属性（元数据）确定：

* 如何在目录中使用属性
* 它在商店中的外观和行为
* 数据传输操作中包含的数据

属性元数据的范围是 `website/store/store view`.

此 [!DNL Live Search] API允许客户端按具有以下属性的任何产品属性进行排序： [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 设置为 `Yes` 在Adobe Commerce Admin中。 启用时， `Search Weight` 和 `Visible in Advanced Search` 可以为属性设置。

[!DNL Live Search] 不会为已删除的产品或设置为的产品编制索引 `Not Visible Individually`.

>[!NOTE]
>
> 商业客户具有 [!DNL Live Search] 可在其网站上利用更快的价格变化更新和同步时间， [SaaS价格索引器](../price-index/index.md).

## 索引管道

客户端从店面调用搜索服务以检索（可筛选、可排序）索引元数据。 仅限具有下列项的可搜索产品属性： *在分层导航中使用* 属性设置为 `Filterable (with results)` 和 *在产品列表中使用排序* 设置为 `Yes` 可以由搜索服务调用。
为了构建动态查询，搜索服务需要知道哪些属性是可搜索的，以及它们的权重。 [!DNL Live Search] 遵循Adobe Commerce搜索权重（1-10，其中10是最高优先级）。 可以在架构中找到同步并与目录服务共享的数据列表，架构定义于：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引客户端搜索图](assets/indexing-pipeline.svg)

1. 检查贸易商 [!DNL Live Search] 权利。
1. 获取对属性元数据进行了更改的存储视图。
1. 存储索引属性。
1. 重新索引搜索索引。

### 完整索引

时间 [!DNL Live Search] 已配置并在载入期间同步，最多可能需要30分钟才能构建初始索引。 大型目录可能需要更长的时间来编制索引。 该过程在之后开始 `cron` 提交信息源并结束运行。

以下事件会触发完全同步和索引生成：

* 入门 [目录数据同步](install.md#synchronize-catalog-data)
* 属性元数据的更改

例如，更改 `Use in Search` 的属性 `color` 属性来源 `No` 到 `Yes` 将属性元数据更改为 `searchable=true`，并触发完全同步和重新索引。 更改时，以下属性元数据会触发完全同步和重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 流式产品更新

生成初始索引后，于 [入门](install.md#synchronize-catalog-data)，则以下增量产品更新将持续同步并重新索引：

* 添加到目录的新产品
* 产品属性值的更改

例如，将新的样本值添加到 `color` 属性作为流式产品更新处理。
流式更新工作流：

1. 更新的产品已从Adobe Commerce实例同步到目录服务。
1. 索引服务不断从目录服务中查找产品更新。 更新的产品在到达目录服务时会编制索引。
1. 产品更新可能需要15分钟才能在中可用 [!DNL Live Search].

## 客户端搜索

此 [!DNL Live Search] API允许客户端通过设置 [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)， *用于在产品列表中排序* 到 `Yes`. 根据主题，此设置会导致将属性作为选项包含在 [排序方式](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 目录页面上的分页控件。 索引产品属性最多可达200个 [!DNL Live Search]，替换为 [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可搜索和可过滤的页面。
索引元数据存储在索引管道中，可供搜索服务访问。

![[!DNL Live Search] 索引元数据API图](assets/index-metadata-api.svg)

### 可排序的属性工作流

1. 客户端调用搜索服务。
1. 搜索服务调用搜索管理员服务。
1. 搜索服务调用索引管道。

## 已为所有产品编制索引

此列表中字段的顺序反映了导出产品数据中的典型列顺序。

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

以下字段已针对所有可配置产品编制索引：

* `childrenSkus`
