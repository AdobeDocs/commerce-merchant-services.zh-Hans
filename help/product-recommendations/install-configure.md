---
title: 安装和配置
description: 了解如何安装、更新和卸载 [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 安装和配置

部署 [!DNL Product Recommendations] 管理员要求您安装模块并配置 [商务服务连接器](../landing/saas.md). 发布更新后，您可以轻松地将安装更新为最新版本。

- [安装](#install)
- [配置](#configure)
- [更新](#update)
- [卸载](#uninstall)

## 安装 [!DNL Product Recommendations] {#install}

因为 [!DNL Product Recommendations] 模块是一个独立的中继组件，比Adobe Commerce更频繁地发布更新。 要确保您及时了解最新的错误修复和功能，请参阅 [发行说明](release-notes.md).

安装 `magento/product-recommendations` 使用编辑器的模块：

```bash
composer require magento/product-recommendations
```

### 添加页面生成器支持 {#pbsupport}

[!DNL Product Recommendations] for Page Builder是一个可选模块，需单独安装。 使用 [!DNL Product Recommendations] 使用页面生成器，通过运行以下命令来安装模块：

```bash
composer require magento/module-page-builder-product-recommendations
```

通过启用 [!DNL Product Recommendations] 在Page Builder中，您可以添加现有的活动 [推荐单位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 添加到在页面生成器中创建的任何内容，例如页面、块和动态块。

参见 [使用 [!DNL Product Recommendations] 包含页面生成器内容](page-builder.md) 以获取进一步说明。

### 添加视觉相似性推荐类型 {#vissimsupport}

此 _视觉相似度_ 推荐类型允许您将推荐单元部署到显示以下产品的产品详细信息页面 [视觉相似](type.md#visualsim) 到正在查看的产品。 当产品的图像和视觉方面是购物体验的重要部分时，此推荐类型最有用。 安装 _视觉相似度_ 通过运行以下命令可获取建议类型：

```bash
composer require magento/module-visual-product-recommendations
```

## 配置 [!DNL Product Recommendations] {#configure}

安装之后 `magento/product-recommendations` 模块，您必须配置 [商务服务连接器](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 通过指定API密钥并选择SaaS数据空间。

要确保目录导出正常运行，请确认 [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 作业和 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 正在运行，并且 `Product Feed` 索引器设置为 `Update by Schedule`.

当您通过API密钥成功链接到Commerce Services并指定SaaS数据空间时，目录同步将开始。 然后，您可以 [验证](verify.md) 行为数据将被发送到您的店面。

## 更新您的 [!DNL Product Recommendations] 安装 {#update}

和所有Adobe Commerce一样， [!DNL Product Recommendations] 使用Composer进行安装和更新。 要更新 `magento/product-recommendations` 模块，运行以下命令：

```bash
composer update magento/product-recommendations --with-dependencies
```

要更新到主要版本（例如从3.0到4.0），您必须编辑根 `composer.json` 文件。 (请参阅 [发行说明](release-notes.md) 有关最新版本的信息。) 例如，让我们打开 `composer.json` 文件并搜索 `magento/product-recommendations` 模块：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

让我们从以下位置浏览主要版本： `3.0` 到 `4.0`：

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

保存 `composer.json` 文件并运行：

```bash
composer update magento/product-recommendations --with-dependencies
```

或者，如果您已安装 `magento/module-visual-product-recommendations` 和 `magento/module-page-builder-product-recommendations` 模块：

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> 在版本3.x.x的产品Recommendations中，您只需要一个API密钥。 在版本4.x.x及更高版本中，您必须提供生产公共API密钥和专用API密钥以及沙盒公共API密钥和专用API密钥。 如果您没有提供这两对API密钥，则无法在管理员中访问产品Recommendations功能。 但是，您的店面将继续收集数据，现有推荐将继续向您的购物者显示。

## 卸载 [!DNL Product Recommendations] {#uninstall}

如有必要，您可以 [卸载](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) product-recommendations模块。
