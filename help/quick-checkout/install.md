---
title: '"安装 [!DNL Quick Checkout] (对于Adobe Commerce扩展)'
description: “请按照以下步骤安装 [!DNL Quick Checkout] 在您的Adobe Commerce项目中。”
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 安装 [!DNL Quick Checkout]

的 [!DNL Quick Checkout] for Adobe Commerce提供无缝的结账体验，旨在将一次性来宾购物者转化为忠诚的客户持有人。

的 [!DNL Quick Checkout] 扩展适用于Adobe Commerce和 [!DNL Magento Open Source] 可以安装 [!DNL Composer keys]，它们已链接到 [MagentoID(mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)注册过程中提供的{target=&quot;_blank&quot;}。 在初始安装Adobe Commerce时或在 [!DNL Composer keys] 之前未保存到 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;&quot;主题，以了解有关获取的详细信息 [!DNL Composer keys].

有两种方法可安装此扩展 — 对于 [Adobe Commerce云基础架构](#magento-commerce-cloud) 或 [本地](#on-premises) 安装。 这些方法要求您使用命令行界面(CLI)。

## 更新最小稳定性设置

在安装该扩展之前，您可以更改 `minimum-stability` 要求 `RC` （释放候选项） `composer.json` 文件。 您可以使用IDE或您最喜爱的文本编辑器（如Visual Studio代码或Sublime Text）。

在 `composer.json` 文件，更改 `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## 安装扩展

您可以安装 [!DNL Quick Checkout] 扩展，适用于云基础架构和本地实例上的Adobe Commerce。

### Adobe Commerce云基础架构

此方法用于安装 [!DNL Quick Checkout] 扩展。

1. 在您的本地工作站上，更改为云项目根目录。

1. 更新 `composer.json` 文件：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer update magento/quick-checkout`.

1. 提交并推送更改。

### 本地

此方法用于安装 [!DNL Quick Checkout] 内部部署实例的扩展。

1. 将快速结帐模块添加到 `require` 部分 `composer.json` 文件：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer update magento/quick-checkout`.

1. 升级Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 更新您的本地实例，以确保部署已提交的代码。

## 升级扩展

当我们发布 [!DNL Quick Checkout]，则可以轻松升级扩展。

1. 要获取包的最新版本，请执行以下操作：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer update magento/quick-checkout`.

1. 提交并推送更改。

## 疑难解答

尝试安装 [!DNL Quick Checkout] 扩展。

请参阅 [疑难解答](../quick-checkout/troubleshooting.md) 主题。 [!DNL Quick Checkout].

## 先决条件

请参阅 [先决条件](../quick-checkout/prerequisites.md) 主题以了解更多信息。
