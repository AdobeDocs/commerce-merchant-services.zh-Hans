---
title: 命令行配置
description: 安装后，您可以配置 [!DNL Payment Services] 使用命令行界面(CLI)。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 命令行配置

安装后 [!DNL Payment Services]，则可以轻松地通过 [管理员内部](configure-admin.md) 或通过命令行界面(CLI)。

## 配置数据导出

[!DNL Payment Services] 将从Magento Open Source和Adobe Commerce导出的订单数据与支付提供商的汇总付款数据合并，以创建有用的报表。 的 [!DNL Payment Services] 扩展使用索引器来有效地收集报表的所有必需数据。

了解 [!DNL Payment Services] 报表，请参阅 [订单付款状态报表](order-payment-status.md#data-used-in-the-report).

### 在Magento Open Source上配置CRON

如果您想使用 `BY SCHEDULE` Magento Open Source时，必须配置cron。 请参阅 [配置并运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 设置索引器

订单数据在支付服务中使用两种索引模式之一导出并保留。`ON SAVE` （默认）或 `BY SCHEDULE` （推荐）。

以下索引适用于 [!DNL Payment Services]:

| 代码 | 名称 | 描述 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 销售订单馈送 | 构建订单数据索引 |
| `sales_order_status_data_exporter` | 销售订单状态信息源 | 生成销售订单状态数据索引 |
| `store_data_exporter` | 存储馈送 | 生成存储数据索引 |

要更改所有三个索引器的索引模式，请运行：

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>如果您未在命令中指定任何索引器，则所有索引器都将更新为相同的值。 如果要更改特定索引器，必须在命令中列出该索引器。

要了解有关手动更改索引器模式的更多信息，请参阅 [配置索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)开发人员文档中的{target=&quot;_blank&quot;}。 要了解如何在管理员中更改它，请参阅 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode)核心用户指南中的{target=&quot;_blank&quot;}。

### 手动重新编入数据索引

您可以手动重新编入数据索引，而无需等待数据自动发生。 请参阅 [重新索引](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot;}(位于 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;}以了解详细信息。

When `BY SCHEDULE` 模式时，系统会跟踪已更改的实体，而cron作业会根据设置的计划更新这些实体的索引。 请参阅 [从命令行中运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [配置并运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html))，以了解如何使用cron作业手动触发索引。

### 将重新索引的数据发送到支付服务

在数据编入索引后，该数据将自动发送到 [!DNL Payment Services]. 您还可以使用以下命令手动触发发送索引数据的过程：

```bash
bin/magento saas:resync --feed [feedName]
```

使用以下命令选项：

| 命令 | 描述 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 执行指定馈送的重新索引，并将其发送到相应的服务 |
| `bin/magento saas:resync --no-reindex` | 跳过索引并从索引发送未同步的数据 |

的 `--feed` 参数允许您指定要发送的馈送：

| 信息源 | 描述 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 生产模式下的订单馈送 |
| `paymentServicesOrdersSandbox` | 沙盒模式下的订单馈送 |
| `paymentServicesOrderStatusesProduction` | 生产模式下的订单状态 |
| `paymentServicesOrderStatusesSandbox` | 在沙盒模式下对状态进行排序 |
| `paymentServicesStoresProduction` | 在生产模式下存储 |
| `paymentServicesStoresSandbox` | 在沙盒模式下存储 |

报表所需的所有数据都会发送到 [!DNL Payment Services] 自动。 您还可以手动触发向发送CRON数据的过程 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

要了解有关重新索引和索引器的更多信息，请参阅 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 开发人员文档中的主题。
