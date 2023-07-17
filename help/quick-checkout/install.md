---
title: '"安装 [!DNL Quick Checkout] for Adobe Commerce扩展”'
description: “按照以下步骤安装 [!DNL Quick Checkout] 在您的Adobe Commerce项目中。”
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 安装 [!DNL Quick Checkout]

此 [!DNL Quick Checkout] Adobe Commerce的扩展和 [!DNL Magento Open Source] 可以安装 [!DNL Composer keys]，这些帐户链接到Commerce帐户 [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} 在注册过程中提供。 Composer在Adobe Commerce的初始安装期间或以下情况下使用这些密钥： [!DNL Composer keys] 之前未保存到 `auth.json` 文件。

参见 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} 有关获取的详细信息，请参阅主题 [!DNL Composer keys].

有两种方法可安装此扩展 — for [云基础架构上的Adobe Commerce](#magento-commerce-cloud) 或 [内部部署](#on-premises) 安装。 这些方法要求您使用命令行界面(command-line interface， CLI)。

## 更新最低稳定性设置

在安装扩展之前，请确保 `minimum-stability` 中的字段 `composer.json` 文件设置为 `"stable"`：

`"minimum-stability": "stable"`

## 安装扩展

您可以安装 [!DNL Quick Checkout] 适用于Adobe Commerce在云基础架构和内部部署实例的扩展。

### 云基础架构上的Adobe Commerce

此方法用于安装 [!DNL Quick Checkout] Commerce Cloud实例的扩展。

1. 在本地工作站上，更改为云项目根目录。

1. 更新您的 `composer.json` 文件：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依赖项。 如果不希望同时更新所有依赖项，请改用此命令： `composer update magento/quick-checkout`.

1. 提交并推送更改。

### 内部部署

此方法用于安装 [!DNL Quick Checkout] 内部部署实例的扩展。

1. 将“快速签出”模块添加到 `require` 部分 `composer.json` 文件：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依赖项。 如果不希望同时更新所有依赖项，请改用此命令： `composer update magento/quick-checkout`.

1. 升级Adobe Commerce：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 更新您的内部部署实例以确保部署提交的代码。

## 升级扩展

当我们发布新版本的 [!DNL Quick Checkout]，您可以轻松升级扩展。

1. 要获取包的最新版本，请执行以下操作：

   ```bash
   composer update
   ```

   此 `composer update` 命令更新所有依赖项。 如果不希望同时更新所有依赖项，请改用此命令： `composer update magento/quick-checkout`.

1. 提交并推送更改。

## 疑难解答

在尝试安装 [!DNL Quick Checkout] 扩展。

如果您在 [!DNL Quick Checkout] 安装过程，请参见 [快速签出问题疑难解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 在Adobe Commerce帮助中心。

## 先决条件

请参阅 [先决条件](../quick-checkout/prerequisites.md) 主题以了解更多信息。
