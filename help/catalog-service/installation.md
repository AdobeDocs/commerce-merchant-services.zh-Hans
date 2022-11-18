---
title: 入门和安装
description: 了解如何安装 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: ea4b386d7e378b30641e623cb190923dc50563d8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 入门和安装

## 先决条件

的入门流程 [!DNL Catalog Service] 需要访问服务器的命令行。 如果您不熟悉从命令行工作，请咨询开发人员或系统集成商以寻求帮助。

### 软件要求

- Adobe Commerce 2.4.x
- 8.1、7.4、7.3菲律宾比索
- 编辑器：2.x，1.x

### 支持的平台

- Adobe Commerce云基础架构：2.4.x
- Adobe Commerce驻地：2.4.x

## 安装扩展

您可以安装 [!DNL Catalog Service] 扩展，适用于云基础架构和本地实例上的Adobe Commerce。

的 [!DNL Catalog Service] 随编辑器密钥一起安装，这些密钥已链接到商务帐户 [马吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在注册过程中提供。 在初始安装时，编辑器会使用这些键 [!DNL Adobe Commerce]，或者在以前未将编辑器键保存到 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 有关获取编辑器键的更多信息。

### Adobe Commerce云基础架构

使用此方法安装 [!DNL Catalog Service] 扩展。

1. 打开 `<Commerce_root>/composer.json` 文件，并更新 `require` 部分如下：

   ```json
   "require":{
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/magento-cloud-metapackage":">=2.4.5 <2.4.6",
   "magento/catalog-service": "^1.0.0"
      }
   ```

1. 在本地测试新配置并更新依赖项：

   ```bash
   composer update
   ```

   命令会更新所有依赖项。

1. 提交并推送更改，以便 `composer.json` 和 `composer.lock`.

### 本地

使用此方法安装 [!DNL Catalog Service] 内部部署实例的扩展。

1. 打开 `<Commerce_root>/composer.json` 文件，并更新 `require` 部分如下：

   ```json
   "require": {
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/catalog-service": "^1.0.0"
   }
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   命令会更新所有依赖项。

1. 升级Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

## 目录服务和API网格

的 [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用AdobeIO将专用或第三方API及其他界面与Adobe产品集成。

将API Mesh与目录服务结合使用的第一步是将API Mesh连接到实例。 请参阅 [创建网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

要完成设置，您需要 [AdobeIO CLI包](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 已安装。

在AdobeIO上配置Mesh后，运行以下命令以连接新网格。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

where `variables.json` 是存储AdobeIO常用值的单独文件。
例如，API密钥可以保存在文件中：

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

运行此命令后，目录服务应通过API网格运行。

## 配置目录导出

安装后 [!DNL Catalog Service]，则必须配置 [Commerce Services Connector](../landing/saas.md) 指定API密钥并选择SaaS数据空间。

要确保目录导出正常运行，请执行以下操作：

- 确认 [cron作业](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 正在运行。
- 验证 [索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 正在运行。
- 确保 `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`和 `Product Variant Feed` 索引器设置为 `Update by Schedule`.

## [!DNL Catalog Service] 演示

请观看此视频以了解 [!DNL Catalog Service] 安装和测试：

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
