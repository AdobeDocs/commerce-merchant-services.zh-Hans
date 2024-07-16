---
title: '[!DNL SaaS Data Export Extension]发行说明'
description: Adobe Commerce的 [!DNL Data Export Extension] 的最新发行信息。
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 051e558f9aa9760c2d6e993713e49a5997270f1b
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# [!DNL SaaS Data Export]扩展发行说明

以下发行说明介绍了[!DNL SaaS data export]扩展的最新版本。 为当前的主要发行版本提供支持。 提供了旧版本的发行说明以供参考。

更新包括：

![新](../assets/new.svg)新功能
![修复](../assets/fix.svg)修复和改进
![错误](../assets/bug.svg)已知问题


>[!NOTE]
>
>SaaS数据导出扩展是随Live Search、Product Recommendations和Catalog Service一起自动安装的模块集合。 您可以使用编辑器检查系统上安装的版本。 在某些情况下，您可能希望升级系统上的数据导出扩展以获取修复或新功能，而不更新Commerce服务版本。

## 当前主要版本

## 103.3.7发行版

![修复](../assets/fix.svg)从InventoryDataExporter模块中删除了不必要的依赖项。
![修复](../assets/fix.svg)更改了CatalogInventoryDataExporter模块中包含的清单模块的必需版本，以支持Adobe Commerce版本2.4.4。

## 103.3.6发行版

![修复](../assets/fix.svg)修复了在多线程模式下重新索引馈送期间发生的死锁。 现在，查询分为插入和更新操作。
![Fix](../assets/fix.svg)已针对包含许多网站的大型目录优化价格查询。
![New](../assets/new.svg)添加了重试逻辑，以便在发生死锁时重新运行失败的事务。

## 103.3.5发行版

![修复](../assets/fix.svg)设置SaaS公共模块的最新兼容数据导出版本的依赖关系。

![修复](../assets/fix.svg)已将`ScopeConfig`实例替换为`ServiceConfigInterface`以支持不同的服务配置。

## 103.3.4发行版

![修复](../assets/fix.svg)通过添加有关重新索引过程的更多详细信息，改进Commerce SaaS数据导出日志记录。

## 103.3.3发行版

![新](../assets/new.svg) SaaS数据导出现在为属性元数据查询缓存Entity-Attribute-Value (EAV)属性。

![修复](../assets/fix.svg)修复了在删除产品时，重试时未保存`InventoryStockStatus`馈送的问题。

## 103.3.2发行版

![修复](../assets/fix.svg)修复了已删除的实体源中缺少`modifiedAt`字段的问题。

## 103.3.1发行版

![修复](../assets/fix.svg)修复了在安装页面生成器时导致在产品馈送重新索引期间显示`Invalid Template File`消息的问题。

## 103.3.0发行版

![新](../assets/new.svg)已将立即导出信息源表迁移到统一结构：
`id`、`source_entity_id`、`feed_id`、`modified_at`、`is_deleted`、`status`、`feed_data`、`feed_hash`、`errors`

![新](../assets/new.svg)已将目录和清单源迁移到立即导出解决方案。

![新](../assets/new.svg)已将立即导出源cron-job重命名为`*_feed_resend_failed_items`。

![新](../assets/new.svg)重命名了立即导出信息源并更改日志表。

![修复](../assets/fix.svg)仅为需要它的馈送设置馈送数据中的`modified_at`字段。

![修复](../assets/fix.svg)修改`productAttributes`查询以仅检索产品属性。

## 103.2.6发行版

![修复](../assets/fix.svg)修复了在表具有前缀时阻止重新索引馈送的问题。

## 103.2.5发行版

![修复](../assets/fix.svg)已优化价格查询。

## 103.2.4发行版

![修复](../assets/fix.svg)修复了在启用Commerce Inventory management时为产品显示的错误库存状态。

## 103.2.3发行版

![Fix](../assets/fix.svg)修复了网站级别的特别定价。
![Fix](../assets/fix.svg)为所有已处理的馈送添加了Mutex。


## 103.2.2发行版

![修复](../assets/fix.svg)已改进大型目录的馈送批量处理策略。 现在，批处理表中填入了有限数量的ID，以减少内存使用。

![修复](../assets/fix.svg)消除了CommerceInventoryDataExporter对MSI模块的硬依赖关系。

![修复](../assets/fix.svg)改进了`commerce-data-exporter`日志，以收集更多信息并按不同的导出阶段进行组织。

## 103.2.1发行版

- 已发布更新版本。

## 103.2.0发行版

- 为产品和价格添加了多线程数据同步。
