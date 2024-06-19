---
title: "[!DNL SaaS Data Export Guide]"
description: “了解如何使用 [!DNL data export] Adobe Commerce SaaS服务的扩展，可在Adobe Commerce和连接的Commerce服务之间同步数据。”
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 指南

[!DNL SaaS data export] 通过优化Adobe Commerce实例与连接的Commerce服务之间的数据同步，提高前端性能。 将Live Search、产品Recommendations或目录服务添加到Adobe Commerce安装时， [!DNL Data export] 扩展会自动安装。

SaaS数据导出收集和导出各种类型的数据，称为 _信息源_，用于聚合特定类型的信息。 根据安装的Commerce服务，SaaS数据导出源包括：

- **目录实体信息源** 聚合产品数据。 数据包括产品、产品属性、产品价格、产品变体、类别、类别权限和产品权限。
- 此 **范围馈送** 聚合客户组、网站、商店和商店视图的数据。
- 此 **销售订单信息源** 汇总订单数据，包括其相关实体，如发票、发运、贷项通知单等。
- 此 **多源库存馈送** 汇总有关库存库存状态物料的数据。

数据导出扩展支持多种方法来启动和管理数据同步过程。

- **从Admin或命令行手动同步**

   - 此 [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) 在Commerce中，管理员以图形方式提供了同步状态的视图。 您可以使用功能板执行完全重新同步(_完全同步_)。 但是，Adobe建议仅在首次将Adobe Commerce连接到Commerce服务时执行完全同步。 请参阅 [同步过程](data-synchronization.md).

   - 此 [Adobe Commerce命令行工具](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI)提供用于同步特定馈送的命令，并包含用于自定义馈送处理的其他选项。

- **与cron作业自动同步**

   - [部分数据同步](data-synchronization.md#partial-synchronization-with-cron-jobs) — 当Commerce管理员用户更新实体时，Cron作业会触发部分数据同步。 数据导出过程只将这些更新发送到连接的Commerce服务。 部分同步过程基于MView机制，不需要管理员用户或系统集成商执行任何操作。

   - [自动重试同步错误](data-synchronization.md#failed-items-sync-for-error-recovery) — 当数据同步过程中发生错误时，Cron作业会触发同步过程的自动重试。

- **导出计划和性能**

   - 开发人员和系统集成商可以估算SaaS数据导出所需的时间，以便在Adobe Commerce和连接的服务之间同步数据。 此估计可帮助计划数据导出处理，以防止站点中断。 请参阅 [估计数据量及传输时间](estimate-data-volume-sync-time.md).

   - 在需要更快地执行同步的情况下，SaaS数据导出提供了自定义选项以提高导出处理性能。 请参阅 [提高数据导出性能](customize-export-processing.md).

- **跟踪数据导出活动并排除其故障** — 使用data-export和saas-export日志在同步和索引过程中查看同步状态和馈送负载。 请参阅 [日志记录和疑难解答](troubleshooting-logging.md).



