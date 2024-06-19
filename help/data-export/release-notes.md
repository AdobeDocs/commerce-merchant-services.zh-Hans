---
title: '"[!DNL SaaS Data Export Extension] 发行说明”'
description: 的最新发行信息 [!DNL Data Export Extension] 用于Adobe Commerce。
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 扩展发行说明

以下发行说明介绍了 [!DNL SaaS data export] 扩展。 为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。

更新包括：

![新建](../assets/new.svg) 新增功能
![修复](../assets/fix.svg) 修复和改进功能
![错误](../assets/bug.svg) 已知问题


>[!NOTE]
>
>SaaS数据导出扩展是随Live Search、Product Recommendations和Catalog Service一起自动安装的模块集合。 您可以使用编辑器检查系统上安装的版本。 在某些情况下，您可能希望升级系统上的数据导出扩展以获取修复或新功能，而不更新Commerce服务版本。

## 当前主要版本

## 103.3.5发行版

![修复](../assets/fix.svg) 为SaaS公共模块的最新兼容数据导出版本设置依赖关系。

![修复](../assets/fix.svg) 已替换 `ScopeConfig` 实例 `ServiceConfigInterface` 以支持不同的服务配置。

## 103.3.4发行版

![修复](../assets/fix.svg) 通过添加有关重新索引过程的更多详细信息，改进Commerce SaaS数据导出日志记录。

## 103.3.3发行版

![新建](../assets/new.svg) 现在，SaaS数据导出会为属性元数据查询缓存Entity-Attribute-Value (EAV)属性。

![修复](../assets/fix.svg) 修复了以下问题 `InventoryStockStatus` 如果产品被删除，则在重试时未保存信息源。

## 103.3.2发行版

![修复](../assets/fix.svg) 修复了以下问题 `modifiedAt` 已删除的实体源中缺少字段。

## 103.3.1发行版

![修复](../assets/fix.svg) 修复了导致 `Invalid Template File` 安装Page Builder后，在产品信息源重新索引期间显示的消息。

## 103.3.0发行版

![新建](../assets/new.svg) 已将立即导出信息源表迁移到统一结构：
`id`， `source_entity_id`， `feed_id`， `modified_at`， `is_deleted`， `status`， `feed_data`， `feed_hash`， `errors`

![新建](../assets/new.svg) 已将目录和清单信息源迁移到立即导出解决方案。

![新建](../assets/new.svg) 将立即导出信息源cron-job重命名为 `*_feed_resend_failed_items`.

![新建](../assets/new.svg) 重命名了立即导出信息源并更改日志表。

![修复](../assets/fix.svg) 设置 `modified_at` 字段仅供需要它的信息源使用。

![修复](../assets/fix.svg) 修改 `productAttributes` 查询以仅检索产品属性。

## 103.2.6发行版

![修复](../assets/fix.svg) 修复了在表具有前缀时阻止重新索引馈送的问题。

## 103.2.5发行版

![修复](../assets/fix.svg) 优化了价格查询。

## 103.2.4发行版

![修复](../assets/fix.svg) 修复了在启用Commerce Inventory management时为产品显示的不正确的Stock状态。

## 103.2.3发行版

![修复](../assets/fix.svg) 修复了网站级别的特别定价。
![修复](../assets/fix.svg) 为所有已处理的馈送添加了互斥锁。


## 103.2.2发行版

![修复](../assets/fix.svg) 改进了大型目录的信息源批量处理策略。 现在，批处理表中填入了有限数量的ID，以减少内存使用。

![修复](../assets/fix.svg) 消除了CommerceInventoryDataExporter对MSI模块的硬依赖性。

![修复](../assets/fix.svg) 已改进 `commerce-data-exporter` 日志，用于收集更多信息并按不同的导出阶段进行组织。

## 103.2.1发行版

- 已发布更新版本。

## 103.2.0发行版

- 为产品和价格添加了多线程数据同步。

