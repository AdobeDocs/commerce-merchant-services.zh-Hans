---
title: 载入和安装
description: “了解如何安装 [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c33ec5a10f9f2570e971e968efd1524e0d384ecd
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 载入和安装

安装目录服务，以使用从Commerce实例请求和接收产品数据 [目录服务GraphQL API](https://developer.adobe.com/commerce/services/graphql/catalog-service/).

>[!NOTE]
>
>如果您的Commerce实例使用Live Search或Product Recommendations，则当您载入或升级这些服务时，会自动安装或更新目录服务。 有关详细信息，请参阅 [实时搜索](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) 和 [产品Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).

>[!BEGINSHADEBOX]

## 先决条件

的新用户引导流程 [!DNL Catalog Service] 需要访问服务器的命令行。 如果您不熟悉如何使用命令行，请向开发人员或系统集成商寻求帮助。

**软件要求**

- Adobe Commerce 2.4.4+
- PHP 8.1、8.2
- Composer： 2.x

**支持的平台**

- 云基础架构上的Adobe Commerce：2.4.4+
- Adobe Commerce内部部署：2.4.4+

>[!ENDSHADEBOX]

## 端点

[!DNL Catalog Service] 有两个端点可供载入：

- 沙盒(`https://catalog-service-sandbox.adobe.io/graphql`) — 用于在上线之前进行测试和验证
- 生产(`https://catalog-service.adobe.io/graphql`) — 用于Commerce商家和网站的实时流量

所有Commerce测试实例都使用沙盒端点。

对沙盒端点执行所有加载测试。 在开始加载测试之前，请提交 [支持服务单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 以便服务团队能够预见额外的服务器流量。

## 安装和配置

开始使用 [!DNL Catalog Service] 对于Adobe Commerce，需要执行以下步骤：

- 安装数据导出扩展
- 配置服务和数据导出
- 访问服务

### 安装数据导出扩展

您必须具有服务器的命令行访问权限，才能完成 [!DNL Catalog Service] 载入流程。

此 [!DNL Catalog Service] 随链接到Commerce帐户的编辑器键一起安装 [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 在注册过程中提供。 Composer在Adobe Commerce的初始安装期间或之前未将Composer键保存到外部的情况下使用这些键 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 以了解有关获取编辑器键的更多信息。

此 [!DNL Catalog Service] 扩展可以安装在Adobe Commerce云基础架构和内部部署实例上。

>[!BEGINTABS]

>[!TAB 云基础架构]

使用此方法安装 [!DNL Catalog Service] Commerce Cloud实例的扩展。

1. 在本地工作站上，转到云基础架构项目上Adobe Commerce的项目目录。

   >[!NOTE]
   >
   >有关在本地管理Commerce项目环境的信息，请参阅 [使用CLI管理分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) 在 _《云基础架构上的Adobe Commerce用户指南》_.

1. 请查看环境分支，以使用Adobe Commerce Cloud CLI进行更新。

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. 添加目录服务模块。

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. 更新包依赖关系。

   ```bash
   composer update "magento/catalog-service"
   ```

1. 提交和推送对的代码更改 `composer.json` 和 `composer.lock` 文件。

1. 添加、提交和推送的代码更改 `composer.json` 和 `composer.lock` 文件到云环境。

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   推送更新会启动 [Commerce云部署流程](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 以应用更改。 从检查部署状态 [部署日志](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB 内部部署]

使用此方法安装 [!DNL Catalog Service] 内部部署实例的扩展。

1. 使用Composer将Catalog Service模块添加到您的项目中：

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update  "magento/catalog-service"
   ```

1. 升级Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >在某些情况下，特别是在部署到生产环境时，您可能希望避免清除编译的代码，因为这样可能需要一些时间。 在进行任何更改之前，请确保备份系统。

>[!ENDTABS]

### 配置服务和数据导出

安装之后 [!DNL Catalog Service]，完成以下任务以将目录服务与您的Adobe Commerce实例集成。 此集成支持数据同步以及Commerce实例、目录服务和其他支持服务之间的通信。

1. 设置 [Commerce服务连接器](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) 通过指定API密钥并选择SaaS数据空间。

   Commerce服务连接器设置是使用Adobe Commerce服务(如目录服务、实时搜索和产品Recommendations)所需的一次性过程。 如果已为其他服务配置了连接器，请跳过此步骤。

1. 从执行初始数据同步 [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   初始同步可能需要几分钟到几小时，具体取决于目录大小。 您可以从“数据管理”仪表板监视同步状态。 初始同步后，目录会持续导出产品数据以使服务保持最新。

要确保正确运行目录导出，请执行以下操作：

- [确认cron作业正在运行](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- 验证索引器是否从 [管理员](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 或使用Commerce CLI命令 `bin/magento indexer:info`.
- 验证 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、和 `Product Variant Feed` 索引器设置为 `Update by Schedule`.

### 访问服务

此 [!DNL Catalog Service] 可从访问GraphQL API。 ` https://catalog-service.adobe.io/graphql` 端点通过HTTPS使用POST命令。

在GraphQL查询中，必须指定多个HTTP标头，包括您在“管理员”中添加到Adobe Commerce Services Connector配置的公共API密钥。 有关详细信息，请参见 [Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) 文档。

### 防火墙配置

允许 [!DNL Catalog Service] 通过防火墙，添加 `commerce.adobe.io` 给允许列表。

## 目录服务和API网格

此 [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 使开发人员能够使用AdobeIO将专用或第三方API以及其他界面与Adobe产品集成。

请参阅 [[!DNL Catalog Service] 和API Mesh](mesh.md) 有关安装和配置详细信息的主题。

## 数据管理功能板

有关详情 [!DNL Catalog Service] 数据同步，请参见 [数据管理功能板](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
