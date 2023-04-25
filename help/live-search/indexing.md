---
title: "[!DNL Live Search] 索引"
description: “了解如何 [!DNL Live Search] 索引产品属性。”
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# 索引

产品属性（元数据）确定：

* 如何在目录中使用属性
* 它在商店中的外观和行为
* 数据传输操作中包含的数据

属性元数据的范围是 `website/store/store view`.

的 [!DNL Live Search] API允许客户按具有 [storefront属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 设置为 `Yes` 在Adobe Commerce管理员中。 启用后， `Search Weight` 和 `Visible in Advanced Search` 可以为属性设置。

[!DNL Live Search] 不会将已删除的产品或设置为 `Not Visible Individually`.

>[!NOTE]
>
> 商务客户 [!DNL Live Search] 可以利用他们网站上更快的价格更新和同步时间 [SaaS价格索引器](../price-index/index.md).

## 索引管道

客户端从店面调用搜索服务以检索（可过滤、可排序）索引元数据。 仅可搜索的产品属性 *在分层导航中使用* 属性设置为 `Filterable (with results)` 和 *用于在产品列表中排序* 设置为 `Yes` 可由搜索服务调用。
要构建动态查询，搜索服务需要知道哪些属性可搜索及其权重。 [!DNL Live Search] 遵循Adobe Commerce搜索权重（1-10，其中10为最高优先级）。 可在架构中找到与目录服务同步和共享的数据列表，该架构在中定义：

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 索引客户端搜索图](assets/indexing-pipeline.svg)

1. 检查商户 [!DNL Live Search] 权利。
1. 获取包含属性元数据更改的存储视图。
1. 存储索引属性。
1. 重新索引搜索索引。

### 完整索引

When [!DNL Live Search] 已在载入期间配置并同步，则构建初始索引可能最多需要八小时。 该过程在 `cron` 提交馈送并完成运行。

以下事件会触发完全同步和索引生成：

* 入门 [目录数据同步](install.md#synchronize-catalog-data)
* 对属性元数据的更改

例如，更改 `Use in Search` 属性 `color` 属性来源 `No` to `Yes` 将属性元数据更改为 `searchable=true`、和会触发完全同步并重新编入索引。 以下属性元数据会在发生更改时触发完全同步并重新索引：

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 流产品更新

在 [载入](install.md#synchronize-catalog-data)，系统会持续同步以下增量产品更新并将其重新索引：

* 已向目录中添加新产品
* 产品属性值的更改

例如，向 `color` 属性作为流产品更新进行处理。
流更新工作流：

1. 更新的产品会从Adobe Commerce实例同步到目录服务。
1. 索引服务会持续从目录服务中查找产品更新。 更新的产品在进入目录服务时会进行索引。
1. 产品更新最多可能需要15分钟，才能在 [!DNL Live Search].

## 客户端搜索

的 [!DNL Live Search] API允许客户通过设置 [storefront属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *用于在产品列表中排序* to `Yes`. 根据主题，此设置将导致将属性作为选项包含在 [排序依据](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 对目录页面进行分页控制。 最多可以通过 [!DNL Live Search]，使用 [店面属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 可搜索和可过滤的ID。
索引元数据存储在索引管道中，并可由搜索服务访问。

![[!DNL Live Search] 索引元数据API图](assets/index-metadata-api.svg)

### 可排序的属性工作流

1. 客户端调用搜索服务。
1. 搜索服务调用搜索管理服务。
1. 搜索服务调用索引管道。

## 已为所有产品编入索引

此列表中字段的顺序反映了导出产品数据中列的典型顺序。

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

以下字段已针对所有可配置产品编入索引：

* `childrenSkus`
