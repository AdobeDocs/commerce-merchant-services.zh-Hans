---
title: '"[!DNL Payment Services] 发行说明"'
description: 查看发行说明，了解有关 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 93a10d91a2dc92db530074d7fc2dfd4f31a9488d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

## v1.1.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 现在与Adobe Commerce和Magento Open Source版本2.4.0到2.4.4兼容。

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 的 [!DNL Payment Services] Adobe Commerce和Magento Open Source的扩展适用于加拿大商户。 商户可以在以下任一位置查看付款配置 [法语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) 或 [英语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支持 [加元(CAD)](overview.md#accepted-credit-cards-and-currencies) 信用卡和Paypal。 购物者可以使用其首选语言获得购物体验，具体取决于他们所在商店的区域设置。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板载 [!DNL Payment Services]](onboard.md) 扩展。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商户现在可以查看 [财务报告](order-payment-status.md) 加元。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 现在与 [8.1菲律宾比索](https://www.php.net/releases/8.1/en.php).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3035 --> 改进了 [!DNL Payment Services] 扩展。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3017 --> 改进了沙盒模式警报，可通过多个存储区显示正确的警报。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] 允许在存储视图级别启用/禁用可用的付款方法，如Venmo。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2277 --> 改进了管理员中商家有选择地禁用/启用PayPal智能按钮的功能。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前删除的产品不会显示在 _审阅顺序_ 页面。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] 改进了管理员中的付款方法标签。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2907 --> 改进了交易数据收集，以便最好地利用欺诈规则和按存储容量使用计费保护。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [编辑器键值不正确](https://support.magento.com/hc/en-us/articles/4406603542541) 在安装扩展期间，会阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [报告](https://support.magento.com/hc/en-us/articles/4406114741517) 付款和订单付款状态可能无法立即同步。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal沙盒帐户](https://support.magento.com/hc/en-us/articles/4406954952461) 表示 [!DNL Payment Services] 如果在载入期间创建了帐户，则无法验证。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2842 --> [测试信用卡失败](https://support.magento.com/hc/en-us/articles/5201041963917) 在沙盒环境中处理付款时使用PayPal。

## v1.0.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布。 [支付服务](https://marketplace.magento.com/magento-payment-services.html) 现在与Adobe Commerce和Magento Open Source版本2.4.0到2.4.3-p1兼容。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] Adobe Commerce和Magento Open Source的扩展可以安装 [Adobe Commerce云基础架构](install.md#magento-commerce-cloud) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支持 [沙盒帐户](onboard.md#enable-sandbox-testing) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](configure-admin.md) 扩展，具有基本付款行为（例如将身份验证捕获一起，以及在沙盒或生产环境之间切换）。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 购物者可以 [!DNL Payment Services] 或者你通过电话接下命令 [创建整个订单](create-order.md) 在管理员中。

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] 为商户提供全面的报表，以便您能够清楚地了解商店订单和付款情况。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支持适合任何商户的分层定价（基于TPV）。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 可以自定义PayPal按钮的外观以及 [支付服务](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) 扩展。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [编辑器键值不正确](https://support.magento.com/hc/en-us/articles/4406603542541) 在安装扩展期间，会阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [报告](https://support.magento.com/hc/en-us/articles/4406114741517) 付款和订单付款状态可能无法立即同步。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal沙盒帐户](https://support.magento.com/hc/en-us/articles/4406954952461) 表示 [!DNL Payment Services] 无法验证。
