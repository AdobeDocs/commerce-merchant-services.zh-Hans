---
title: 从Adobe Commerce安装和配置Adobe Experience Platform连接器
description: 了解如何从Adobe Commerce安装、配置、更新和卸载Adobe Experience Platform连接器。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 572df7558e825a7a7c442e47af787c209dbe4ee3
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# 安装和配置Experience Platform连接器

在安装扩展之前， [查看先决条件](overview.md#prereqs).

## 安装扩展

Experience Platform连接器扩展可从 [Adobe市场](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). 从服务器的命令行安装此扩展时，它将作为以下对象连接到Adobe Commerce安装 [服务](../landing/saas.md). 当这个过程完成时， **Experience Platform连接器** 和 **Commerce服务连接器** 显示在 **系统** 下的菜单 **服务** 在商业中 _管理员_.

>[!NOTE]
>
>![适用于Adobe Commerce的B2B](../assets/b2b.svg) 对于B2B商家，您必须安装单独的扩展。 此扩展添加了对B2B特定事件的支持。 [了解详情](#install-the-b2b-extension).

1. 要下载 `experience-platform-connector` 包，从命令行运行以下命令：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此元包包含以下模块和扩展：

   * `module-experience-connector-admin`  — 更新管理员UI，以便您能够为特定Adobe Commerce实例选择数据流ID。
   * `module-experience-connector`  — 设置 `Organization ID` 和 `datastreamId` 在Storefront Events SDK中。
   * `data-services`  — 提供店面事件的属性上下文。 例如，发生结帐事件时，将包含有关购物车中有多少商品的信息以及这些商品的产品属性数据。
   * `services-id`  — 将您的Adobe Commerce实例连接到 [Adobe Commerce SaaS](../landing/saas.md) 使用沙盒和生产API密钥并发送到Adobe Experience Platform以检索IMS组织ID。
   * `orders-connector`  — 将订单状态服务连接到您的Adobe Commerce实例。

1. （可选）要包含 [!DNL Live Search] 数据，包括 [搜索事件](events.md#search-events)，安装 [[!DNL Live Search]](../live-search/install.md) 扩展。

### 配置订单连接器

安装之后 `experience-platform-connector`，您必须最终安装 `orders-connector` 基于部署类型的模块：内部部署或Adobe Commerce on Cloud基础架构。

#### 内部部署

在内部部署环境中，您需要手动启用代码生成和Adobe Commerce事件：

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### 在云基础架构上

在Adobe Commerce on Cloud基础架构中，启用 `ENABLE_EVENTING` 中的全局变量 `.magento.env.yaml`. [了解详情](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

提交更新的文件并将其推送到云环境。 部署完成后，使用以下命令启用发送事件：

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### 安装B2B扩展

对于B2B商家，请安装以下扩展以包含 [申请列表](events.md#b2b-events) 事件数据。

下载 `magento/experience-platform-connector-b2b` 通过从命令行运行以下命令来扩展：

```bash
composer require magento/experience-platform-connector-b2b
```

## 更新Experience Platform连接器 {#update}

要更新Experience Platform连接器，请从命令行运行以下命令：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

或者，对于B2B商家：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

要更新到主要版本，例如从1.0.0到2.0.0，请编辑项目的根 [!DNL Composer] `.json` 文件如下所示：

1. 打开根 `composer.json` 文件和搜索 `magento/experience-platform-connector`.

1. 在 `require` 部分，按如下方式更新版本号：

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 然后，从命令行运行以下命令：

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   或者，对于B2B商家：

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## 卸载Experience Platform连接器 {#uninstall}

要卸载Experience Platform连接器，请参阅 [卸载模块](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
