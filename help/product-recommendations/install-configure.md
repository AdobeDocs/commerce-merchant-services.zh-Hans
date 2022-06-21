---
title: 安装和配置
description: 了解如何安装、更新和卸载 [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: cfeb8b4f8e2dc1e9d2d4c0be7a7bc522488418bc
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# 安装和配置

部署 [!DNL Product Recommendations] 要求您安装模块并配置 [Commerce Services Connector](../landing/saas.md). 随着更新的发布，您可以轻松地使用最新版本更新安装。

- [安装](#install)
- [配置](#configure)
- [更新](#update)
- [卸载](#uninstall)

## 安装 [!DNL Product Recommendations] {#install}

因为 [!DNL Product Recommendations] 模块是独立的元数据包，更新的发布频率高于Adobe Commerce。 要确保您是最新的错误修复和功能，请参阅 [发行说明](release-notes.md).

安装 `magento/product-recommendations` 具有编辑器的模块：

```bash
composer require magento/product-recommendations
```

### 添加页面生成器支持 {#pbsupport}

[!DNL Product Recommendations] for Page Builder是一个可选模块，单独安装。 使用 [!DNL Product Recommendations] 在页面生成器中，通过运行以下命令来安装模块：

```bash
composer require magento/module-page-builder-product-recommendations
```

启用 [!DNL Product Recommendations] 在页面生成器中，您可以添加一个现有的活动 [推荐单元](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) 到在页面生成器中创建的任何内容，如页面、块和动态块。

### 添加可视相似度推荐类型 {#vissimsupport}

的 _视觉相似度_ 推荐类型允许您将推荐单元部署到产品详细信息页面，该页面显示的产品 [视觉相似](type.md#visualsim) 到要查看的产品。 当产品的图像和视觉方面是购物体验的重要部分时，此推荐类型非常有用。 安装 _视觉相似度_ 通过运行以下命令键入推荐类型：

```bash
composer require magento/module-visual-product-recommendations
```

## 配置 [!DNL Product Recommendations] {#configure}

安装 `magento/product-recommendations` 模块中，必须配置 [Commerce Services Connector](https://docs.magento.com/user-guide/configuration/services/saas.html) 指定API密钥并选择SaaS数据空间。

要确保目录导出正常运行，请确认 [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 工作和 [索引器](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 正在运行， `Product Feed` 索引器设置为 `Update by Schedule`.

当您通过API密钥成功链接到Commerce Services并指定SaaS数据空间时，将开始目录同步。 然后，您可以 [验证](verify.md) 行为数据被发送到您的店面。

## 更新 [!DNL Product Recommendations] 安装 {#update}

和Adobe Commerce一样， [!DNL Product Recommendations] 使用编辑器进行安装和更新。 要更新 `magento/product-recommendations` 模块，运行以下命令：

```bash
composer update magento/product-recommendations --with-dependencies
```

要更新到主版本（如从3.0更新到4.0），必须编辑根 `composer.json` 文件。 (请参阅 [发行说明](release-notes.md) ) 例如，让我们打开主 `composer.json` 文件和搜索 `magento/product-recommendations` 模块：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

让我们从 `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

保存 `composer.json` 文件和运行：

```bash
composer update magento/product-recommendations --with-dependencies
```

>[!NOTE]
>
> 在产品Recommendations的3.x.x版本中，您只需要一个API密钥。 在4.x.x及更高版本中，您必须提供生产公共和专用API密钥，以及沙盒公共和专用API密钥。 如果不提供两对API密钥，您将无法在管理员中访问产品Recommendations功能。 但是，数据收集将继续在您的店面中，现有推荐将继续显示给您的购物者。

## 卸载 [!DNL Product Recommendations] {#uninstall}

如有必要，您可以 [卸载](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) 产品 — 推荐模块。
