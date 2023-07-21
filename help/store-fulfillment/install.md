---
title: 安装
description: '"安装 [!DNL Store Fulfillment solution] 使用Composer for PHP的Adobe Commerce店面。”'
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---


# 安装

完成初始安装 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 扩展运行队列管理器，并将缓存配置为允许异常处理。 确保您的开发环境包含开发工具，以确保运营和维护您的Adobe Commerce实例的最佳实践。

## 先决条件

查看 [要求](solution-requirements.md) ，并在安装 [!DNL Store Fulfillment] Adobe Commerce的扩展。

如果您已安装预发行版或测试版的Store Fulfillment for Adobe Commerce扩展，请在安装当前版本之前使用以下命令将其删除。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 安装要求

- **访问Walmart Commerce Technologies软件归档的Store Fulfillment （.zip文件）** — 在新用户引导和启用过程中，请与您的客户经理合作，以访问Store Fulfillment扩展的安装文件。

- **Adobe Commerce帐户信息** — 安装 [!DNL Store Fulfillment] 解决方案需要 [[!DNL Commerce] 帐户](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. 您需要具有所有者或管理员访问权限的帐户ID和凭据， [!DNL Adobe Commerce] 项目。

- 对象 [!DNL Adobe Commerce] 在云基础架构项目中，软件安装程序必须具有对云项目的管理员访问权限。 参见 [管理用户访问权限](https://devdocs.magento.com/cloud/project/user-admin.html).

- **使用Composer和[!DNL Commerce CLI]** — 请参阅 [常规CLI安装](https://devdocs.magento.com/extensions/install/){target="_blank"} 有关使用这些工具在上安装和管理扩展的信息 [!DNL Adobe Commerce] 平台。

- **在Adobe Commerce上安装第三方扩展的经验** — 有关参考，请参阅Adobe Commerce文档。

   - [在云基础架构实例上安装Adobe Commerce的扩展](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [为Adobe Commerce内部部署实例安装扩展](https://devdocs.magento.com/extensions/install/).

### 步骤1：下载扩展包

按照您的客户代表提供的说明，下载包含用于安装Store Fulfillment Services扩展的Composer包的存档文件。

### 步骤2：将扩展工件提取到应用程序

提取包含集成捆绑包的存档文件以安装Store Fulfillment Services扩展。

1. 为提取的文件创建目标目录。

   - 从命令行转到Web服务器doc根目录。

   - 创建 `artifacts` 目录。

1. 将存档文件解压缩到新目录。

1. 通过查看文件列表验证是否成功提取了文件。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 步骤3：使用编辑器配置应用程序

使用Composer为安装配置源目录并安装Store Fulfillment Services扩展。

1. 为Composer安装配置源存储库。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. 将Store Fulfillment Services扩展添加到 `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>为了获得更好的Adobe Commerce内部部署实例性能，您可以 [更新自动加载配置](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader)： `composer dump-autoload --optimize`

### 步骤4：升级数据库架构和数据

使用完成安装 `bin/magento setup:upgrade` 使用更改更新数据库架构和数据，以支持Store Fulfillment解决方案。

>[!NOTE]
>
>对于云基础架构项目上的Adobe Commerce，您无需注册扩展。 相反，请提交上一步中的代码更改，并将它们推送到您的环境分支。 在云构建和部署过程中，更新数据库架构和数据的命令会自动运行。

### 步骤5：完成安装

1. 在Adobe Commerce中注册该扩展，方法是使用 `setup:upgrade` CLI命令Magento。

   ```terminal
   bin/magento setup:upgrade
   ```

1. 如果出现提示，请重新编译 [!DNL Commerce] 项目。

   ```bash
   bin/magento setup:di:compile
   ```

1. 清理缓存。

   ```bash
   bin/magento cache:clean
   ```

1. 禁用维护模式。

   ```bash
   bin/magento maintenance:disable
   ```

### 步骤6：验证安装

从Adobe Commerce服务器中，验证是否已安装和启用Store Fulfillment Services扩展的模块。

1. 登录到服务器。

   有关在云基础架构上安装Adobe Commerce的信息， [使用SSH登录到远程环境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

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

如果需要，请使用 [设置:static-content:部署](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} 用于将静态视图文件部署到生产环境的CLI命令。

```terminal
php bin/magento setup:static-content:deploy -f
```

此 `-f` 如果使用空白主题，则必须使用选项。

>[!NOTE]
>
>欲了解更多信息，请参见 [Adobe Commerce中的静态内容部署最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) Adobe Commerce帮助中心中的文章。

