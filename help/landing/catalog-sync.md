---
title: 目录同步
description: 了解如何从 [!DNL Commerce] 服务器到 [!DNL Commerce Services] 不断更新服务。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: 853c55fbae3ccfb7abea8ce074127f2871d55688
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# 目录同步

Adobe Commerce和Magento Open Source使用索引器将目录数据编译为表。 该进程由 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如产品价格或库存水平的更改。

目录同步过程每小时运行一次，以允许 [!DNL Commerce] 服务来使用目录数据。 目录同步从 [!DNL Commerce] 服务器到 [!DNL Commerce] 服务，以使服务保持为最新。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要当前的目录信息，才能准确返回包含正确名称、定价和可用性的推荐。 您可以使用 _目录同步_ 用于观察和管理同步过程的仪表板，或 [命令行界面](#resynccmdline) 触发目录同步并重新索引产品数据以供使用 [!DNL Commerce] 服务。

>[!NOTE]
>
> 使用 _目录同步_ 仪表板或命令行界面中，您必须 [配置了API密钥和SaaS数据空间](saas.md).

## 访问目录同步功能板

>[!NOTE]
>
> 的 _目录同步_ 仅当 _产品Recommendations_ 模块已安装并仅反映与该功能相关的数据预测。 支持其他商务服务，例如 _实时搜索_ 和 _目录服务_ 计划在将来。

要访问“目录同步”功能板，请选择 **系统** > _数据传输_ > **目录同步**.

使用 **目录同步** 功能板，您可以：

- 查看同步状态(**正在进行**, **成功**, **失败**)
- 查看已同步的产品总数（如果成功）
- 搜索同步的产品以查看其当前状态
- 按名称、SKU等搜索商店目录
- 在JSON中查看已同步的产品详细信息，以帮助诊断同步差异
- 重新启动同步过程

### 上次同步

报告同步状态：

- **成功**  — 显示同步成功的日期和时间以及更新的产品数量
- **失败**  — 显示尝试同步的日期和时间
- **正在进行**  — 显示上次成功同步的日期和时间

>[!NOTE]
>
> 目录同步过程每小时自动运行一次。 但是，如果您在店面上看不到产品，或者如果产品未反映您最近所做的更改，则可以解析 [目录同步问题](#resolvesync).

### 已同步的产品

显示从 [!DNL Commerce] 目录。 初始同步后，您应该只希望同步已更改的产品。

## 重新同步 {#resync}

如果必须在每小时计划同步之前启动目录的重新同步，则可以强制执行重新同步。

>[!NOTE]
>
> 强制重新同步会触发整个产品目录的重新同步，这会增加硬件资源的负载。

1. 从 _目录同步_ 功能板，选择 **设置**.

   的 _目录同步设置_ 页面。

1. 在 _重新同步数据_ ，单击 [!UICONTROL Resync].

   [!DNL Commerce] 在下一个计划同步窗口期间同步您的目录。 根据目录的大小，此操作可能需要较长时间。

## 同步的目录产品

的 **同步的目录产品** 表格显示以下信息。

| 字段 | 描述 |
|---|---|
| ID | 产品的唯一标识符 |
| 名称 | 产品的店面名称 |
| 类型 | 标识产品类型，如简单、可配置、可下载等 |
| 上次导出 | 上次从目录成功导出产品的日期 |
| 上次修改时间 | 上次在目录中修改产品的日期 |
| SKU | 显示产品的库存单位 |
| 价格 | 产品的价格 |
| 可见性 | 在 [!DNL Commerce] 目录 |

## 解决目录同步问题 {#resolvesync}

触发数据重新同步时，可能需要长达一小时的时间才能更新数据并反映在UI组件（如推荐单位）中。 但是，如果在等待一小时后，您仍注意到目录与店面上显示的内容之间存在差异，或者如果目录同步失败，请参阅以下内容：

### 数据差异

1. 在搜索结果中显示有关产品的详细视图。
1. 复制JSON输出，并验证内容是否与 [!DNL Commerce] 目录。
1. 如果内容不匹配，请对目录中的产品进行细微更改，例如添加空格或句点。
1. 等待重新同步或 [触发手动重新同步](#resync).

### 同步未运行

如果同步未按计划运行或未同步任何内容，请参阅 [知识库](https://support.magento.com/hc/en-us/articles/360042224851).

### 同步失败

如果目录同步的状态为 **失败**，提交 [支持票证](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket).

## 命令行界面 {#resynccmdline}

的 `saas:resync` 命令是 `magento/saas-export` 包。 您可以使用 [!DNL Commerce Services] 产品，例如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 从命令行触发数据重新同步时，可能需要长达一小时的时间才能更新数据。

命令选项：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

下表描述了 `saas:resync` 参数和描述。

| 参数 | 描述 | 必需？ |
|---| ---| ---|
| `feed` | 指定要重新同步的实体，如 `products` | 是 |
| `no-reindex` | 将现有目录数据重新提交到 [!DNL Commerce Services] 无需重新索引。 未指定此参数时，命令会在同步数据之前运行完全重新索引。 | 否 |

信息源名称可以是以下名称之一：

- `products` — 目录中的产品
- `categories` — 目录中的类别
- `variants` — 可配置产品的产品变体，如颜色和大小
- `productattributes` — 产品属性，例如 `activity`, `gender`, `tops`, `bottoms`，等等
- `productoverrides` — 特定于客户的定价和目录可见性规则，例如那些基于类别权限的规则

### 示例

以下示例重新索引 [!DNL Commerce] 编录并重新同步到商务服务：

```bash
bin/magento saas:resync --feed products
```

如果您不想运行产品的完整重新索引，则可以同步已生成的产品数据：

```bash
bin/magento saas:resync --feed products --no-reindex
```
