---
title: 入门和安装
description: 了解如何安装 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 55c35e7775505ab9f6a61a458b6cd6fa4c7f1702
workflow-type: tm+mt
source-wordcount: '574'
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

## 环境

目录服务有两个可用于入门的环境：

- 沙盒(https://catalog-service-sandbox.adobe.io/graphql) — 用于上线前进行测试和验证
- 生产(https://catalog-service.adobe.io/graphql)-用于商务商家和网站的实时流量)

## 安装和配置

要开始使用Adobe Commerce的目录服务，需要执行以下步骤：

- 安装数据导出扩展
- 配置服务和数据导出
- 访问服务

### 安装数据导出扩展

目录服务的载入过程需要访问服务器的命令行。

目录服务扩展可以同时安装在Adobe Commerce云基础架构和本地实例上。

目录服务随编辑器密钥一起安装，这些密钥已链接到商务帐户 [马吉德](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 在注册过程中提供。 在初始安装Adobe Commerce时，或在以前未将编辑器键保存到外部时，编辑器会使用这些键 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 有关获取编辑器键的更多信息。

#### Adobe Commerce云基础架构

使用此方法为Commerce Cloud实例安装目录服务扩展。

1. 打开 `<Commerce_root>/composer.json` 文件，并按如下方式更新“需要”部分：

   ```json
   "require": {
     "magento/module-saas-catalog": "^101.4.0",
     "magento/module-saas-product-override": "^101.4.0",
     "magento/module-saas-product-variant": "^101.4.0",
     "magento/module-bundle-product-data-exporter": "^101.3.1",
     "magento/module-catalog-data-exporter": "^101.3.1",
     "magento/module-catalog-inventory-data-exporter": "^101.3.1",
     "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
     "magento/module-configurable-product-data-exporter": "^101.3.1",
     "magento/module-data-exporter": "^101.3.1",
     "magento/module-parent-product-data-exporter": "^101.3.1",
     "magento/module-product-override-data-exporter": "^101.3.1",
     "magento/data-services": "^7.0.11",
     "magento/services-id": "^3.0.1",
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. 在本地测试新配置并更新依赖项：

```bash
composer update
```

命令会更新所有依赖项。

1. 提交并推送更改，以便 `composer.json` 和 `composer.lock`.

#### 本地

使用此方法为本地实例安装目录服务扩展。

1. 打开 `<Commerce_root>/composer.json` 文件，并按如下方式更新“需要”部分：

```json
"require": {
 "magento/module-saas-catalog": "^101.4.0",
 "magento/module-saas-product-override": "^101.4.0",
 "magento/module-saas-product-variant": "^101.4.0",
 "magento/module-bundle-product-data-exporter": "^101.3.1",
 "magento/module-catalog-data-exporter": "^101.3.1",
 "magento/module-catalog-inventory-data-exporter": "^101.3.1",
 "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
 "magento/module-configurable-product-data-exporter": "^101.3.1",
 "magento/module-data-exporter": "^101.3.1",
 "magento/module-parent-product-data-exporter": "^101.3.1",
 "magento/module-product-override-data-exporter": "^101.3.1",
 "magento/data-services": "^7.0.11",
 "magento/services-id": "^3.0.1",
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
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

### 配置服务和数据导出

安装目录服务后，必须配置 [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) 指定API密钥并选择SaaS数据空间。

完成SaaS配置后，按照“目录同步”指南执行初始数据同步。

要确保目录导出正常运行，请执行以下操作：

- 确认cron作业正在运行。
- 验证索引器是否正在运行。
- 确保 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`和 `Product Variant Feed` 索引器被设置为“按计划更新”。

初始同步可能需要几分钟到几小时，具体取决于目录大小。 初始同步后，目录会持续将产品数据从商务服务器导出到商务服务，以使服务保持为最新。

### 访问服务

可通过HTTPS使用POST命令访问目录服务API。

要获取api密钥，请转到管理员中的Commerce Service Connector区域，并复制公共API密钥。

阅读 [GraphQL文档](https://developer.adobe.com/commerce/webapi/graphql/) 了解如何查询和发送生成API请求所需的标头。

## 目录服务和API网格

的 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用AdobeIO将专用或第三方API及其他界面与Adobe产品集成。

请参阅  [目录服务和API网格](mesh.md) 安装和配置详细信息主题。
