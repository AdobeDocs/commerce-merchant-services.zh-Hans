---
title: 载入和安装
description: 了解如何安装 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8bac6f053cddd3d47c3aa279abf7c96c79ffcd81
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# 载入和安装

查看以下内容的演练： [!DNL Catalog Service] 进程。

第1部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

第2部分：

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## 先决条件

的新用户引导流程 [!DNL Catalog Service] 需要访问服务器的命令行。 如果您不熟悉如何使用命令行，请向开发人员或系统集成商寻求帮助。

### 软件要求

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- Composer： 2.x

### 支持的平台

- 云基础架构上的Adobe Commerce：2.4.4+
- Adobe Commerce内部部署：2.4.4+

## 端点

[!DNL Catalog Service] 有两个端点可供载入：

- 沙盒(https://catalog-service-sandbox.adobe.io/graphql) — 用于在上线之前进行测试和验证
- 生产(https://catalog-service.adobe.io/graphql)-用于Commerce商家和网站的实时流量

Commerce的所有测试实例都应使用沙盒端点。

只应对沙盒端点执行负载测试。 建议 [支持服务单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 在加载测试时打开，以便服务团队可以预见额外的服务器流量。

## 安装和配置

开始使用 [!DNL Catalog Service] 对于Adobe Commerce，需要执行以下步骤：

- 安装数据导出扩展
- 配置服务和数据导出
- 访问服务

### 安装数据导出扩展

的新用户引导流程 [!DNL Catalog Service] 需要访问服务器的命令行。

此 [!DNL Catalog Service] 扩展可以安装在Adobe Commerce云基础架构和内部部署实例上。

此 [!DNL Catalog Service] 随编辑器密钥一起安装，这些密钥链接到Commerce帐户 [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 在注册过程中提供。 Composer在Adobe Commerce的初始安装期间或之前未将Composer键保存到外部的情况下使用这些键 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 以了解有关获取编辑器键的更多信息。

#### 云基础架构上的Adobe Commerce

使用此方法安装 [!DNL Catalog Service] Commerce Cloud实例的扩展。

1. 打开 `<Commerce_root>/composer.json` 在文本编辑器中生成文件并更新所需部分，如下所示：

```json
"require": {
  "magento/catalog-service": "^3.0.1"
}
```

1. 在本地测试新配置并更新依赖关系：

```bash
composer update
```

该命令会更新所有依赖项。

1. 提交并推送您的更改 `composer.json` 和 `composer.lock`.

#### 内部部署

使用此方法安装 [!DNL Catalog Service] 内部部署实例的扩展。

1. 打开 `<Commerce_root>/composer.json` 在文本编辑器中生成文件并更新所需部分，如下所示：

```json
"require": {
    "magento/catalog-service": "^3.0.1"
}
```

1. 更新依赖项并安装扩展：

```bash
composer update
```

该命令会更新所有依赖项。

1. 升级Adobe Commerce：

```bash
bin/magento setup:upgrade
```

1. 清除缓存：

```bash
bin/magento cache:clean
```

### 配置服务和数据导出

安装之后 [!DNL Catalog Service]，您必须配置 [Commerce服务连接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) 通过指定API密钥并选择SaaS数据空间。

SaaS配置完成后，按照以下步骤执行初始数据同步 [目录同步](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 指南。

要确保正确运行目录导出，请执行以下操作：

- 确认cron作业正在运行。
- 验证索引器是否正在运行。
- 确保 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、和 `Product Variant Feed` 索引器设置为“按计划更新”。

初始同步可能需要几分钟到几小时，具体取决于目录大小。 初始同步后，目录会持续将产品数据从Commerce服务器导出到Commerce服务，以使服务保持最新。

### 访问服务

此 [!DNL Catalog Service] 可通过HTTPS使用POST命令访问API。

要获取API密钥，请转到管理员中的Commerce Service Connector区域并复制公共API密钥。

阅读 [GraphQL文档](https://developer.adobe.com/commerce/services/graphql/) 了解如何查询和发送生成API请求所需的标头。

允许 [!DNL Catalog Service] 通过防火墙，添加 `commerce.adobe.io` 给允许列表。

## 目录服务和API网格

此 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用AdobeIO将专用或第三方API以及其他界面与Adobe产品集成。

请参阅  [[!DNL Catalog Service] 和API Mesh](mesh.md) 有关安装和配置详细信息的主题。
