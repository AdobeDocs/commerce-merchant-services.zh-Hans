---
title: 安装
description: '"安装 [!DNL Store Fulfillment solution] 用于使用PHP编辑器的Adobe Commerce店面。”'
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 66c4ca972004c43fa55795006b1511820ca9b514
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# 安装

完成 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 扩展，其中队列管理器运行和缓存配置为允许异常处理。 确保您的开发环境包含开发工具，以确保在操作和维护Adobe Commerce实例方面采用最佳实践。

## 先决条件

查看 [要求](solution-requirements.md) ，并在安装 [!DNL Store Fulfillment] 扩展的Adobe Commerce。

如果您已安装了Store Fullment for Adobe Commerce扩展的预发行版或测试版版本，请在安装当前版本之前使用以下命令将其删除。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 安装要求

- **通过Walmart Commerce Technologies软件存档（.zip文件）访问商店履行** — 在载入和启用过程中，请与您的客户经理合作，以访问商店履行扩展的安装文件。

- **Adobe Commerce帐户信息** — 安装 [!DNL Store Fulfillment] 解决方案需要 [商务帐户](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}。 您需要具有以下权限的帐户ID和凭据：拥有 [!DNL Adobe Commerce] 项目。

- 对于 [!DNL Adobe Commerce] 在云基础架构项目上，软件安装程序必须拥有对云项目的管理员访问权限。 请参阅 [管理用户访问权限](https://devdocs.magento.com/cloud/project/user-admin.html).

- **使用编辑器和[!DNL Commerce CLI]** — 请参阅 [常规CLI安装](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;}以了解有关使用这些工具在上安装和管理扩展的信息 [!DNL Adobe Commerce] 平台。

- **在Adobe Commerce上安装第三方扩展的体验** — 有关参考，请参阅Adobe Commerce文档。

   - [在云基础架构实例上安装Adobe Commerce的扩展](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [安装Adobe Commerce本地实例的扩展](https://devdocs.magento.com/extensions/install/).

### 步骤1:下载扩展包

按照您的帐户代表提供的说明下载包含用于安装商店履行服务扩展的编辑器包的存档文件。

### 步骤2:将扩展工件提取到应用程序

提取包含集成包的存档文件，以安装Store Fulfillment Services扩展。

1. 为提取的文件创建目标目录。

   - 从命令行中，转到Web服务器文档根目录。

   - 创建 `artifacts` 目录访问Advertising Cloud的帮助。

1. 将存档文件解压到新目录。

1. 通过查看文件列表来验证已提取的文件。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 步骤3:使用编辑器配置您的应用程序

使用编辑器配置安装的源目录并安装Store Fulfillment Services扩展。

1. 为编辑器安装配置源存储库。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. 将Store Fulfillment Services扩展添加到 `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>为了在Adobe Commerce内部实例上获得更好的性能，您可以 [更新自动加载配置](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### 步骤4:升级数据库模式和数据

使用 `bin/magento setup:upgrade` 用更改更新数据库模式和数据，以支持“存储履行”解决方案。

>注意：
>对于云基础架构项目上的Adobe Commerce，您无需注册扩展。 相反，应提交上一步中的代码更改，并将它们推送到环境分支。 在云构建和部署过程中，将自动运行更新数据库架构和数据的命令。

### 步骤5:完成安装

1. 使用 `setup:upgrade` MagentoCLI命令。

   ```terminal
   bin/magento setup:upgrade
   ```

1. 如果出现提示，请重新编译 [!DNL Commerce] 项目。

   ```bash
   bin/magento setup:di:compile
   ```

1. 清除缓存。

   ```bash
   bin/magento cache:clean
   ```

1. 禁用维护模式。

   ```bash
   bin/magento maintenance:disable
   ```

### 步骤6:验证安装

从Adobe Commerce服务器中，验证是否已安装并启用“商店履行服务”扩展的模块。

1. 登录到服务器。

   对于云基础架构上的Adobe Commerce安装， [使用SSH登录到远程环境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. 验证是否已启用“商店履行服务”模块。

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   输出应包括以下模块：

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### 其他步骤

如果需要，请使用 `[setup:static-content: deploy](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy)` CLI命令将静态视图文件部署到生产环境。

```terminal
php bin/magento setup:static-content:deploy -f
```

的 `-f` 选项。

>[!NOTE]
>
>有关更多信息，请参阅 [静态内容在Adobe Commerce中部署最佳实践](https://support.magento.com/hc/en-us/articles/360031624091) 在Adobe Commerce帮助中心。
