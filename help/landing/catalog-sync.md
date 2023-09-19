---
title: 目录同步
description: 了解如何从导出产品数据 [!DNL Commerce] 服务器至 [!DNL Commerce Services] 不断更新服务。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 1fd5f25b88fa129cc136b93fdf88b981624f0678
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# 目录同步

Adobe Commerce和Magento Open Source使用索引器将目录数据编译到表中。 该进程由自动触发 [事件](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 例如产品价格或库存水平改变。

目录同步过程每小时运行以允许 [!DNL Commerce] 服务使用目录数据。 目录同步从导出产品数据 [!DNL Commerce] 服务器至 [!DNL Commerce] 持续提供服务，使服务保持最新。 例如， [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 需要当前的目录信息才能准确地返回具有正确名称、定价和可用性的推荐。 您可以使用 _目录同步_ 仪表板来观察和管理同步过程或 [命令行界面](#resynccmdline) 触发目录同步和重新索引产品数据以供使用： [!DNL Commerce] 服务。

>[!NOTE]
>
> 要使用 _目录同步_ 在仪表板或命令行界面中，必须具有 [已配置API密钥和SaaS数据空间](saas.md).

## 访问目录同步仪表板

>[!NOTE]
>
> 此 _目录同步_ 仅当满足以下条件时，仪表板才可用 _产品Recommendations_ 模块已安装，并且仅反映与该功能相关的数据投影。 支持其他Commerce服务，例如 _实时搜索_ 和 _目录服务_ 是面向未来的。

要访问“目录同步”仪表板，请选择 **系统** > _数据传输_ > **目录同步**.

使用 **目录同步** 功能板您可以：

- 查看同步状态(**进行中**， **成功**， **失败**)
- 查看同步的产品总数（如果成功）
- 搜索同步的产品以查看其当前状态
- 按名称、SKU等搜索存储目录
- 在JSON中查看同步的产品详细信息，以帮助诊断同步差异
- 重新启动同步过程

### 上次同步

报告同步状态：

- **成功**  — 显示同步成功的日期和时间以及更新的产品数
- **失败**  — 显示尝试同步的日期和时间
- **进行中**  — 显示上次成功同步的日期和时间

>[!NOTE]
>
> 目录同步过程每小时自动运行一次。 但是，如果您未在店面中看到产品，或者产品未反映您最近所做的更改，您可以解决 [目录同步问题](#resolvesync).

### 产品已同步

显示从您的 [!DNL Commerce] 目录。 在初始同步之后，您应该只会同步已更改的产品。

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
| 类型 | 标识产品类型，如简单、可配置、可下载等 |
| 上次导出 | 上次成功从目录中导出产品的日期 |
| 上次修改时间 | 上次在目录中修改产品的日期 |
| SKU | 显示产品的库存单位 |
| 价格 | 产品的价格 |
| 可见性 | 产品的可见性设置，如 [!DNL Commerce] 目录 |

## 解决目录同步问题 {#resolvesync}

触发数据重新同步时，最多可能需要一小时才能更新数据并反映在UI组件中，例如推荐单元。 但是，如果在等待一小时后，您仍然发现目录与店面中显示的内容存在差异，或者如果目录同步失败，请参阅以下内容：

### 数据差异

1. 在搜索结果中显示相关产品的详细视图。
1. 复制JSON输出，并验证内容是否与您在 [!DNL Commerce] 目录。
1. 如果内容不匹配，请对目录中的产品进行细微更改，例如添加空格或句点。
1. 等待重新同步或 [触发手动重新同步](#resync).

### 同步未运行

如果同步未按计划运行或未同步任何内容，请参阅 [知识库](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### 同步失败

如果目录同步的状态为 **失败**，提交 [支持服务单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 命令行界面 {#resynccmdline}

此 `saas:resync` 命令是 `magento/saas-export` 包。 您可以使用以下任一方式安装此包： [!DNL Commerce Services] 产品，例如 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 或 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 首次运行数据同步时，请务必运行 `productattributes` 首先馈送，然后馈送 `productoverrides`，然后运行 `products` 信息源。

命令选项：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

下表描述了 `saas:resync` 参数和描述。

| 参数 | 描述 | 必需？ |
|---| ---| ---|
| `feed` | 指定要重新同步的实体，如 `products` | 是 |
| `no-reindex` | 将现有目录数据重新提交到 [!DNL Commerce Services] 而不重新索引。 如果未指定此参数，该命令会在同步数据之前运行完整的重新索引。 | 否 |

馈送名称可以是以下名称之一：

- `categories` — 目录中的类别
- `categoryPermissions`  — 每个类别的权限
- `products` — 目录中的产品
- `productattributes` — 产品属性，例如 `activity`， `gender`， `tops`， `bottoms`，等等
- `productoverrides` — 特定于客户的定价和目录可见性规则，如基于类别权限的那些规则
- `variants` — 可配置产品的产品变体，如颜色和大小

如果从命令行触发数据重新同步，则更新数据可能最多需要1小时。

### 同步SaaS价格索引

如果您使用 [SaaS价格索引](../price-index/index.md) 并需要重新同步，请运行以下命令：

```bash
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
```

### 正在同步目录服务

要重新同步目录服务，请务必按以下顺序运行命令：

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### 示例

以下示例对中的产品数据重新编制索引 [!DNL Commerce] 将其编录并重新同步到Commerce Services：

```bash
bin/magento saas:resync --feed products
```

如果您不想对产品运行完整的重新索引，则可以同步已生成的产品数据：

```bash
bin/magento saas:resync --feed products --no-reindex
```
