---
title: 安装 [!DNL Payment Services]
description: 安装Payments Services扩展。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 安装 [!DNL Payment Services]

下载并安装 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 是使用的先决条件步骤 [!DNL Payment Services].

![[!DNL Payment Services] 扩展管理视图](assets/admin-view.png)

## 下载扩展

您必须首先从以下位置下载扩展： [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 安装之前。

1. 导航到 [Commerce Marketplace中的Payment Services扩展](https://marketplace.magento.com/magento-payment-services.html).
1. 要选择版本和版本，请切换 **[!UICONTROL Edition]** 和 **[!UICONTROL Your store version]** 到您的首选内容。
1. 单击 **[!UICONTROL Add to Cart]**.
1. 完成结账并单击 **[!UICONTROL Place Order]**.
1. 检查与您的Marketplace下载关联的电子邮件，以确认订单和获取详细信息。

## 安装扩展

您可以安装 [!DNL Payment Services] 扩展两者 [!DNL Adobe Commerce] 链接到您的Commerce帐户的云基础架构和内部部署实例上 [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 在注册过程中提供。 [!DNL Magento Open Source] 客户使用内部部署说明。

Composer在初始安装期间使用这些密钥 [!DNL Adobe Commerce]，或者在之前未将编辑器键保存到的情况下 `auth.json` 文件。

参见 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 以了解有关获取编辑器键的更多信息。

参见 [安装扩展](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) ，以了解有关下载和安装扩展之前应考虑哪些事项的更多信息。

### [!DNL Adobe Commerce] 在云基础架构上

此方法用于安装 [!DNL Payment Services] Commerce Cloud实例的扩展。

1. 更新您的 `composer.json` 文件：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依赖关系。

1. 提交并推送更改。

### 内部部署和其他配置

此方法用于安装 [!DNL Payment Services] 本地实例的扩展和 [!DNL Magento Open Source] 客户。

1. 要获取该扩展，请运行以下命令：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 更新依赖项并安装扩展：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依赖关系。

1. 升级实例：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 提交更改。
1. 要确保已提交的代码已部署，请更新您的实例。

## 升级扩展

当有新版本的 [!DNL Payment Services] 发布后，您可以轻松升级扩展。

1. 要获取包的最新版本，请执行以下操作：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   使用 `composer update` 命令以更新所有根依赖关系。

1. 提交并推送更改。

## 疑难解答

在尝试安装 [!DNL Payment Services] 扩展。 使用以下故障排除方法来解决错误。

### 不正确的编辑器键

如果您看到以下错误，表明您的编辑器键不正确：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

验证您的编辑器密钥是否有效，以及您是否有权访问其他Magento包。

要查看已配置的编辑器键，请执行以下操作：

1. 查找的位置 `auth.json` 文件：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 文件：

   ```bash
   cat /path/to/auth.json
   ```

1. 参见 [哪些键与您的Commerce帐户关联 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### 内存不足，无法用于PHP

如果看到以下错误，表示您没有足够的内存来使用PHP：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加内存限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 环境上的PHP的 `php.ini`.

或者，也可以使用此命令指定内存限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
