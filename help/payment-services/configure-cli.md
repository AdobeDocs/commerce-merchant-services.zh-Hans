---
title: 命令行配置
description: 安装后，您可以配置 [!DNL Payment Services] 使用命令行界面(CLI)。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# 命令行配置

安装之后 [!DNL Payment Services]，您可以从中轻松配置它 [在家中](payments-home.md) 或通过命令行界面(CLI)。

## 配置数据导出

[!DNL Payment Services] 组合从导出的订单数据 [!DNL Magento Open Source] 和 [!DNL Adobe Commerce] 使用来自付款提供商的汇总付款数据创建有用的报表。 此 [!DNL Payment Services] 扩展使用索引器高效地收集报告的所有必要数据。

要了解中使用的数据 [!DNL Payment Services] 报表，请参阅 [订单付款状态报表](order-payment-status.md#data-used-in-the-report).

### 配置cron [!DNL Magento Open Source]

如果您要使用 `BY SCHEDULE` 索引模式开启 [!DNL Magento Open Source]，您必须配置cron。 请参阅 [配置和运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 设置索引器

使用以下两种索引模式之一，在支付服务中导出并保留订单数据：`ON SAVE` （默认）或 `BY SCHEDULE` （推荐）。

以下索引用于 [!DNL Payment Services]：

| 代码 | 名称 | 描述 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 销售订单信息源 | 生成订单数据的索引 |
| `sales_order_status_data_exporter` | 销售订单状态信息源 | 生成销售订单状态数据的索引 |
| `store_data_exporter` | 商店信息源 | 生成存储数据的索引 |

要更改所有三个索引器的索引模式，请运行：

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>如果未在命令中指定任何索引器，则所有索引器都会更新为相同的值。 如果要更改特定索引器，必须在命令中列出该索引器。

要了解有关手动更改索引器模式的更多信息，请参阅 [配置索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} 在开发人员文档中。 要了解如何在管理员中更改它，请参阅 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} （在核心用户指南中）。

### 手动重新索引数据

您可以手动重新索引数据，而不是等待数据自动生成。 请参阅 [重新索引](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} 在 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} 以了解更多信息。

时间 `BY SCHEDULE` 模式被设置，系统跟踪被改变的实体，并且cron作业根据设置的计划更新它们的索引。 请参阅 [从命令行运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) 在 [配置和运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html))，了解如何使用cron作业手动触发索引。

### 将重新索引的数据发送到付款服务

为数据编制索引后，该数据将自动发送到 [!DNL Payment Services]. 您还可以使用此命令手动触发发送索引数据的过程：

```bash
bin/magento saas:resync --feed [feedName]
```

使用以下命令选项：

| 命令 | 描述 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 执行指定馈送的重新索引并将其发送到相应的服务 |
| `bin/magento saas:resync --no-reindex` | 跳过索引并发送来自索引的未同步数据 |

此 `--feed` 参数允许您指定要发送的信息源：

| 信息源 | 描述 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 生产模式下的订单馈送 |
| `paymentServicesOrdersSandbox` | 沙盒模式下的订单馈送 |
| `paymentServicesOrderStatusesProduction` | 生产模式下的订单状态 |
| `paymentServicesOrderStatusesSandbox` | 沙盒模式中的订单状态 |
| `paymentServicesStoresProduction` | 在生产模式下存储 |
| `paymentServicesStoresSandbox` | 以沙盒模式存储 |

报告所需的所有数据都会发送至 [!DNL Payment Services] 如果配置和安装了cron，则会自动进行配置。 您还可以手动触发将cron数据发送到的过程 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

要了解有关重新索引和索引器的更多信息，请参阅 [管理索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 开发人员文档中的主题。

## 配置L2/L3处理

[!DNL Payment Services] 可以处理来自卡支付交易的级别2和级别3数据，以便为商家提供附加信息。

>[!WARNING]
>
> 通过PayPal与2级和3级处理集成仅适用于美国商家。 请参阅 [支付处理](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} 有关更多信息，请参阅PayPal开发人员文档。

如果要使用L2/L3处理数据 [!DNL Payment Services]，或者，如果您有任何问题，请联系您的 [!DNL Payment Services] 客户经理。

了解中使用的第2层和第3层处理 [!DNL Payment Services]，请参见 [2级和3级处理](levels-card-payment-transactions.md).
