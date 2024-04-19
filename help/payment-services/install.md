---
title: 安装 [!DNL Payment Services]
description: 安装Payments Services扩展。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 安装 [!DNL Payment Services]

要开始使用的付款服务，请执行以下操作： [!DNL Adobe Commerce] 和 [!DNL Magento Open Source]，您必须完成一些入门培训步骤。

>[!INFO]
>
> 查看我们的 [配置 [!DNL Payment Services] 适用于Adobe Commerce的](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) 视频，以了解其他信息。

下载并安装 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 是使用的先决步骤 [!DNL Payment Services].

![[!DNL Payment Services] 扩展管理员视图](assets/admin-view.png){width="300" zoomable="yes"}

## 下载扩展

必须首先从以下位置下载扩展 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 安装之前。

1. 导航至 [Commerce Marketplace中的支付服务扩展](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. 要选择版本和版本，请切换 **[!UICONTROL Edition]** 和 **[!UICONTROL Your store version]** 到您的首选内容。
1. 单击 **[!UICONTROL Add to Cart]**.
1. 完成结账并单击 **[!UICONTROL Place Order]**.
1. 检查与您的Marketplace下载关联的电子邮件，以查看订单确认和详细信息。

## 安装扩展

您可以安装 [!DNL Payment Services] 两者的扩展 [!DNL Adobe Commerce] 链接到您的Commerce帐户的云基础架构和本地实例 [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 在注册过程中提供。
[!DNL Magento Open Source] 客户使用内部部署说明。

Composer在初始安装期间使用这些密钥 [!DNL Adobe Commerce]，或者在之前未将编辑器键保存到的情况下 `auth.json` 文件。

请参阅 [获取您的身份验证密钥](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 以了解有关获取编辑器键的更多信息。

请参阅 [安装扩展](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 有关下载和安装扩展之前需要考虑的事项的更多信息。

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

   使用 `composer update` 用于更新所有根依赖项的命令。

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

   使用 `composer update` 用于更新所有根依赖项的命令。

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

   使用 `composer update` 用于更新所有根依赖项的命令。

1. 提交并推送更改。

## 故障排除

尝试安装 [!DNL Payment Services] 扩展。 使用以下故障排除方法解决错误。

### 不正确的编辑器键

如果您看到以下错误，表明您的编辑器键不正确：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

验证您的编辑器密钥是否有效，以及您是否有权访问其他Magento包。

要查看已配置的编辑器键：

1. 查找的位置 `auth.json` 文件：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 文件：

   ```bash
   cat /path/to/auth.json
   ```

1. 请参阅 [哪些键与您的Commerce帐户关联 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### 内存不足，无法用于PHP

如果看到以下错误，表示您没有足够的内存来安装PHP：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[增加内存限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 环境上的PHP的 `php.ini`.

或者，也可以使用此命令指定内存限制： `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
