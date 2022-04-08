---
title: 对 [!DNL Express Checkout]
description: 对错误进行故障诊断，在使用 [!DNL Express Checkout] (对于Adobe Commerce扩展)。
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 故障诊断 [!DNL Express Checkout] 对于Adobe Commerce

>[!IMPORTANT]
>
> 该功能仅面向提前采纳者计划(EAP)用户，并且尚未可供所有客户访问。 目前仅限于美国客户。 如需帮助和问题，请联系Adobe Commerce支持。

使用以下故障诊断方法来解决这些特定问题。

## 编辑器键不正确

如果您看到以下错误，表示您的编辑器键不正确：

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

确认您的编辑器键已链接到快速结帐注册期间使用的MagentoID。

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

## 在 `composer.json` 设置为稳定

如果您看到以下错误，表示您的编辑器键不正确：

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

将最小稳定性设置为 `RC` 在 `composer.json` 文件。

## 内存不足，PHP不能使用

如果您看到以下错误，表示没有足够的内存用于PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[提高内存限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) ，用于 `php.ini`.

或者，您也可以使用以下命令指定内存限制： `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## 无效的发运地址

有一个已知问题，即 [!DNL Express Checkout].

当默认发运地址无效时，客户将被重定向到发运地址步骤。 Storefront仅显示有效的送货地址。

>[!WARNING]
>
> 如果没有有效的发运地址，则客户看不到任何可用的发运地址。

请参阅 [装运详细信息](../express-checkout/shipping-details.md) 主题以了解更多信息。

## 添加具有新送货地址的街道地址行

有一个已知问题，即 [!DNL Express Checkout].

当您 [使用Bolt帐户登录](https://help.bolt.com/shoppers/guides/checkout/log-in/) 您可以添加新的送货地址，每个街道地址的行数限制为4行。

Adobe Commerce通常可配置为支持多达20条街道地址线。

## 复选框 `enable terms and conditions` 未正确显示

有一个已知问题，即 [!DNL Express Checkout].

当您启用 `Enable terms and conditions` 复选框，并使用 [!DNL Bolt] 帐户， `Enable terms and conditions` 复选框。 请参阅 [登录](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] 页面以了解更多信息。

请参阅 [条款和条件](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) 主题，以了解有关管理员配置的更多信息。

## 当 `Display Billing Address On` 设置为 `payment page`

有一个已知问题，即 [!DNL Express Checkout].

如果您将 `Display Billing Address On` 参数 `payment page` 和 [使用Bolt帐户登录](https://help.bolt.com/shoppers/guides/checkout/log-in/) 当您检查 `My billing and shipping address are the same` 复选框：

![同一地址](assets/checked-address.png)

单选按钮显示 `use existing card`.

请参阅 [结帐](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主题，以了解有关 `Display Billing Address On` 参数。

## 翻译 [!DNL Express Checkout] 扩展

Adobe Commerce使您能够将您的商店本地化到多个地区和市场。 您甚至可以在“管理员”视图中将错误消息本地化。

请参阅 [翻译和本地化](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) 主题以了解更多信息。

## 获取帮助

请联系Adobe Commerce支持部门以获取任何帮助。
