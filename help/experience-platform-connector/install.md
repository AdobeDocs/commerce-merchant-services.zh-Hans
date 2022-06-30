---
title: 从Adobe Commerce安装和配置Adobe Experience Platform Connector
description: 了解如何从Adobe Commerce安装、配置、更新和卸载Adobe Experience Platform Connector。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: b503c369f12696a2a791af77055a7b53000b827f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 安装和配置Experience Platform连接器

安装该扩展之前， [查看先决条件](overview.md#prereqs).

## 安装扩展

1. 安装Experience Platform连接器元包。

   ```bash
   composer require magento/experience-platform-connector
   ```

   此元包包含以下模块和扩展：

   * `module-platform-connector-admin`  — 更新管理员UI，以便您能够配置数据流ID
   * `module-platform-connector`  — 设置 `ImsOrgId` 和 `datastreamId` 在Adobe Commerce Storefront Event SDK中
   * `data-services`  — 为店面事件提供属性上下文。 例如，发生结帐事件时，将包含有关购物车中有多少个项目的信息以及这些项目的产品属性数据。
   * `commerce-services`  — 将Adobe Commerce实例连接到 [Adobe Commerce SaaS](../landing/saas.md) 使用沙盒和生产API密钥，以及使用IMS组织ID传送到Adobe Experience Platform

1. （可选）要包含 [!DNL Live Search] 数据，包括搜索事件，安装 [[!DNL Live Search]](../live-search/install.md) 扩展。

## 更新Experience Platform连接器 {#update}

要更新Experience Platform连接器，请从命令行运行以下命令：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

要从1.0.0更新到主版本（如从1.0.0更新到2.0.0），请编辑项目的根 [!DNL Composer] `.json` 文件如下：

1. 打开根 `composer.json` 文件和搜索 `magento/platform-connector`.

1. 在 `require` 部分更新版本号，如下所示：

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 然后，从命令行中运行以下命令：

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

## 卸载Experience Platform连接器 {#uninstall}

要卸载Experience Platform连接器，请参阅 [卸载模块](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
