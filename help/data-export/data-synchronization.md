---
title: 将数据与SaaS数据导出同步
description: “了解如何 [!DNL SaaS Data Export] 在Adobe Commerce实例和连接的SaaS服务之间收集并同步数据。”
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# 将数据与SaaS数据导出同步

当您安装需要数据导出的Commerce服务(如Catalog Service、Live Search或Product Recommendations)时，将安装一组Saas数据导出模块以管理数据收集和同步过程。 下图显示了SaaS数据导出流程。

![适用于Adobe Commerce的SaaS数据导出收集和同步流程](assets/data-export-flow.png){width="900" zoomable="yes"}

SaaS数据导出流的主要组件包括：

- SaaS数据导出模块，用于从Adobe Commerce收集馈送数据、汇编馈送项目、侦听更新并保留馈送状态。
- SaaS导出模块，用于导出数据、配置路由并将馈送发布到连接的服务。
- Adobe Commerce服务可管理数据摄取过程，以验证传入馈送并将更新保留到连接的服务。

## 同步模式

SaaS数据导出有两种模式来处理实体馈送：

- **立即导出模式** — 在此模式下，收集数据并立即通过单次迭代发送到Commerce服务。 此模式可加快将实体更新交付到Commerce服务的速度，并减小信息源表的存储大小。

- **旧版导出模式** — 在此模式中，数据是在单个进程中收集的。 然后，cron作业将收集的数据发送到连接的商务服务。 在数据导出日志条目中，使用旧模式的馈送将进行标记 `(legacy)`.

## 同步类型

SaaS数据导出支持三种同步类型：完全同步、部分同步和重试失败的项同步。

### 完全同步

将Adobe Commerce实例连接到Commerce服务后，执行完全同步以将实体馈送数据从Adobe Commerce发送到连接的服务。

>[!NOTE]
>
>完全同步主要用于载入阶段。 避免常规使用，以防止数据库过载。 初始同步后，使用部分同步自动同步正在进行的更改。

### 部分同步

通过部分同步，SaaS数据导出会自动将Commerce应用程序中的更新（例如产品名称更改或价格更新）发送到连接的商务服务。

数据导出过程使用以下cron作业来自动执行部分同步操作。

- “索引”cron组作业：
   - 此 `indexer_reindex_all_invalid` 作业会重新索引所有无效馈送。 这是标准的Adobe Commerce cron作业。
   - 此 `saas_data_exporter` 作业适用于旧版导出源。
   - 此 `sales_data_exporter` 作业特定于销售数据导出信息源。

这些作业每分钟运行一次。

为了使部分同步正常工作，Commerce应用程序需要以下配置：

- [通过cron作业启用任务计划](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- 所有SaaS数据导出索引器均配置于 `Update by Schedule` 模式。

  在SaaS数据导出版本103.1.0及更高版本中， `Update by Schedule` 默认情况下，模式处于启用状态。 您可以使用Commerce CLI命令验证服务器上的索引配置， `bin/magento indexer:show-mode | grep -i feed`

### 重试失败的项目同步

重试失败项目同步使用单独的进程来重新发送由于同步过程中出现的错误（例如应用程序错误、网络中断或SaaS服务错误）而未能同步的项目。 此同步的实施也基于cron作业。

- `resync_failed_feeds_data_exporter` cron组作业：
   - 此 `<feed name>_feed_resend_failed_feeds_items` 例如，作业会重新发送同步失败的项目 `products_feed_resend_failed_items`.

### 查看和管理同步过程

大多数同步活动是根据应用程序配置自动处理的。 但是，SaaS数据导出还提供了用于管理该过程的工具。

- 管理员用户可以查看和跟踪同步进度，并从获取有关数据的信息 [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

- 有权访问Commerce应用程序服务器的开发人员、系统集成商或管理员可以使用Adobe Commerce命令行工具(CLI)管理同步过程和数据馈送。 请参阅 [数据导出命令参考](data-export-cli-commands.md).

### 验证Commerce应用程序配置

仅当Commerce实例配置正确时，“部分同步”和“重试失败的项”同步才能正常工作。 通常，在设置Commerce服务时完成配置。 如果数据导出无法正常工作，请检查以下配置。

- [确认cron作业正在运行](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- 验证索引器是否从 [管理员](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 或使用Commerce CLI命令 `bin/magento indexer:info`.

- 验证以下馈送的索引器是否设置为 `Update by Schedule`：目录属性、产品、产品覆盖和产品变体。 您可以从以下位置检查索引器： [索引管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 在管理员中或使用CLI (`bin/magento indexer:show-mode | grep -i feed`)。
