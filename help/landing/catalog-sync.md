---
title: 目录同步
description: 了解如何从导出产品数据 [!DNL Commerce] 服务器至 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# 目录同步

>[!NOTE]
>
> “目录同步”功能板现在是“数据管理功能板”。 此改版后的功能板现在支持 [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md)， [[!DNL Live Search]](../live-search/overview.md)、和 [[!DNL Catalog Service]](../catalog-service/overview.md). 客户可以通过更新到其中一项服务的最新版本来获取数据管理功能板。 欲知更多信息，请参阅 [数据管理功能板](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 文档。 对于尚未升级但仍拥有目录同步功能板的用户，此当前主题仍然适用。

Adobe Commerce使用索引器将目录数据编译到表中。 该进程由自动触发 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如产品价格或库存水平改变。

目录同步服务将产品数据从 [!DNL Adobe Commerce] 实例到 [!DNL Commerce Services] 平台，持续保持数据最新。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要当前的目录信息才能准确地返回具有正确名称、定价和可用性的推荐。 使用 _目录同步_ 功能板，用于观察和管理同步过程或命令行界面以触发目录同步并重新索引产品数据以供使用。 [!DNL Commerce Services]. 请参阅 [命令行界面参考](../data-export/data-export-cli-commands.md) 在 _SaaS数据导出_ 指南。

## 访问目录同步仪表板

要访问“目录同步”仪表板，请选择 **系统** > _数据传输_ > **目录同步**.

使用 **目录同步** 功能板您可以：

- 查看同步状态(**进行中**， **成功**， **失败**)
- 查看同步的产品总数
- 搜索同步的产品以查看其当前状态
- 按名称、SKU等搜索存储目录。
- 在JSON中查看同步的产品详细信息，以帮助诊断同步差异
- 重新启动同步过程

### 上次同步

报告同步状态：

- **成功**  — 显示同步成功的日期和时间以及更新的产品数
- **失败**  — 显示尝试同步的日期和时间
- **进行中**  — 显示上次成功同步的日期和时间

目录同步过程每小时自动运行一次。 如果您在店面中没有看到预期的产品，或者这些产品没有反映您最近所做的更改，您可以解决 [目录同步问题](#resolvesync).

### 产品已同步

显示从您的 [!DNL Commerce] 目录。 初次同步后，只应同步已更改的产品。

## 重新同步 {#resync}

如果在进行每小时计划同步之前必须启动目录的重新同步，则可以强制进行重新同步。

>[!NOTE]
>
> 强制重新同步会触发整个产品目录的重新同步，这会增加硬件资源的负载。

1. 从 _目录同步_ 仪表板，选择 **设置**.

   此 _目录同步设置_ 页面。

1. 在 _重新同步数据_ 部分，单击 [!UICONTROL Resync].

   [!DNL Commerce] 在下一个计划同步窗口同步您的目录。 根据目录的大小，此操作可能需要较长时间。

## 已同步的目录产品

此 **已同步的目录产品** 表格显示了以下信息。

| 字段 | 描述 |
|---|---|
| ID | 产品的唯一标识符 |
| 名称 | 产品的店面名称 |
| 类型 | 标识产品类型，例如简单、可配置或可下载 |
| 上次导出 | 上次成功从目录中导出产品的日期 |
| 上次修改时间 | 上次在目录中修改产品的日期 |
| SKU | 显示产品的库存单位 |
| 价格 | 产品的价格 |
| 可见性 | 产品的可见性设置，如 [!DNL Commerce] 目录 |

## 解决目录同步问题 {#resolvesync}

请参阅 [日志和疑难解答](../data-export/troubleshooting-logging.md#troubleshooting) 在 _SaaS数据导出指南_.
