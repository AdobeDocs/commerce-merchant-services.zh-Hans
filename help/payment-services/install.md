---
title: 安装 [!DNL Payment Services]
description: 安装Payments Services扩展。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 647848c58213ea7f85d8a2c025146aa065042433
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# 安装 [!DNL Payment Services]

安装 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 是使用的先决步骤 [!DNL Payment Services].

![[!DNL Payment Services] 扩展管理员视图](assets/admin-view.png)

的 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以使用编辑器键进行安装，这些键链接到MagentoID([马吉德](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在注册过程中提供。 在初始安装时，编辑器会使用这些键 [!DNL Adobe Commerce]，或者在以前未将编辑器键保存到 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 有关获取编辑器键的更多信息。

有两种方法可安装此扩展 — 对于 [[!DNL Adobe Commerce] 云基础架构](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 安装。 这些方法要求您使用命令行界面(CLI)。

## 安装扩展

您可以安装 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 云基础架构和本地实例上。

### [!DNL Adobe Commerce] 云基础架构

此方法用于安装 [!DNL Payment Services] 扩展。

1. 更新 `composer.json` 文件：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer require magento/payment-services`.

1. 提交并推送更改。

### 本地

此方法用于安装 [!DNL Payment Services] 内部部署实例的扩展。

1. 要获取该扩展，请运行以下命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer require magento/payment-services`.

1. 升级 [!DNL Adobe Commerce]:

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 要确保部署已提交的代码，请更新您的内部部署实例。

## 升级扩展

当的 [!DNL Payment Services] 发布后，您可以轻松升级扩展。

1. 要获取包的最新版本，请执行以下操作：

   ```bash
   composer update
   ```

   的 `composer update` 命令会更新所有依赖项。 如果不想同时更新所有依赖项，请改用以下命令： `composer update magento/payment-services`.

1. 提交并推送更改。

## 疑难解答

尝试安装 [!DNL Payment Services] 扩展。 请使用以下故障诊断方法来解决错误。

### 编辑器键不正确

如果您看到以下错误，表示您的编辑器键不正确：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

验证您的编辑器键是否已链接到在 [!DNL Payment Services] 注册。

要查看配置了哪些编辑器键：

1. 查找 `auth.json` 文件：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 文件：

   ```bash
   cat /path/to/auth.json
   ```

1. 请参阅 [哪些键与您的MagentoID关联](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### 内存不足，PHP不能使用

如果您看到以下错误，表示没有足够的内存用于PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[提高内存限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) ，用于 `php.ini`.

或者，您也可以使用以下命令指定内存限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
