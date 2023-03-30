---
title: 从Adobe Commerce安装和配置Adobe Experience Platform Connector
description: 了解如何从Adobe Commerce安装、配置、更新和卸载Adobe Experience Platform Connector。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# 安装和配置Experience Platform连接器

安装该扩展之前， [查看先决条件](overview.md#prereqs).

## 安装扩展

Experience Platform连接器扩展从服务器的命令行安装，并作为 [服务](../landing/saas.md). 完成该过程后， **Experience Platform连接器** 在 **系统** 菜单下 **服务** 在商务中 _管理员_.

Experience Platform连接器作为 [Adobe市场](https://marketplace.magento.com/magento-experience-platform-connector.html).

![B2B for Adobe Commerce](../assets/b2b.svg) 对于B2B商户，您必须安装一个单独的扩展。 此扩展添加了对B2B特定事件的支持。 [了解更多](#install-the-b2b-extension).

1. 要下载 `experience-platform-connector` 包中，从命令行中运行以下命令：

   ```bash
   composer require magento/experience-platform-connector
   ```

   此元包包含以下模块和扩展：

   * `module-experience-connector-admin`  — 更新管理员UI，以便您能够为特定Adobe Commerce实例选择数据流ID
   * `module-experience-connector`  — 设置 `Organization ID` 和 `datastreamId` 在Storefront Events SDK中
   * `data-services`  — 为店面事件提供属性上下文。 例如，发生结帐事件时，将包含有关购物车中有多少个项目的信息以及这些项目的产品属性数据。
   * `services-id`  — 将Adobe Commerce实例连接到 [Adobe Commerce SaaS](../landing/saas.md) 使用沙盒和生产API密钥和Adobe Experience Platform来检索IMS组织ID

1. （可选）要包含 [!DNL Live Search] 数据，包括搜索事件，安装 [[!DNL Live Search]](../live-search/install.md) 扩展。

### 安装B2B扩展

对于B2B商户，请安装以下扩展以包含 [申请列表](events.md#b2b-events) 事件数据。

下载 `magento/experience-platform-connector-b2b` 扩展：从命令行中运行以下内容：

```bash
composer require magento/experience-platform-connector-b2b
```

## 更新Experience Platform连接器 {#update}

要更新Experience Platform连接器，请从命令行运行以下命令：

```bash
composer update magento/experience-platform-connector --with-dependencies
```

或者，对于B2B商户：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
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

或者，对于B2B商户：

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

## 卸载Experience Platform连接器 {#uninstall}

要卸载Experience Platform连接器，请参阅 [卸载模块](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
