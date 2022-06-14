---
title: '"[!DNL Payment Services] 发行说明"'
description: 查看发行说明，了解有关 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# 发行说明

以下发行说明介绍了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

请参阅 [即将发行的版本](https://devdocs.magento.com/release/) 了解发行计划和支持。

请参阅 [可用性](https://devdocs.magento.com/release/availability.html) ，以了解有关产品兼容性的信息。

## v1.1.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布 — [!DNL Payment Services] 现在 [兼容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 的 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 现在可供加拿大商人使用。 商户可以在以下任一位置查看付款配置 [法语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) 或 [英语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支持 [加元(CAD)](overview.md#accepted-credit-cards-and-currencies) 信用卡和PayPal交易。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板载 [!DNL Payment Services]](onboard.md) 英语或法语扩展。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商户现在可以查看 [订单付款状态](order-payment-status.md) 和 [派息报告](payouts.md)，以加元(CAD)表示。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 现在与 [8.1菲律宾比索](https://www.php.net/releases/8.1/en.php).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3017 --> 改进了沙盒模式警报，可通过多个存储区显示正确的警报。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2742 --> 您现在可以在商店视图级别启用和禁用可用的付款方法，如Venmo。 以前，您只能为每个网站配置付款方法。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2277 --> 您现在可以选择性地 [启用或禁用单个PayPal智能按钮](settings.md#paypal-smart-buttons).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前删除的产品不会显示在 _审阅顺序_ 页面。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2842 --> 测试信用卡交易记录 [可能因PayPal而失败](https://support.magento.com/hc/en-us/articles/5201041963917) 在沙盒环境中处理付款时。

## v1.0.0

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布 — [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 现在与 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.3-p1。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以为 [[!DNL Adobe Commerce] 云基础架构](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支持 [沙盒帐户](sandbox.md) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](settings.md) 扩展，例如利用 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙盒或生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 您的购物者可以 [!DNL Payment Services] 或通过 [手动订单创建](create-order.md).

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> 通过 [订单付款状态](order-payment-status.md) 和 [派息报告](payouts.md)，可用于 [!DNL Payment Services] 让您清楚地了解商店的订单和相关付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支持基于总处理量的灵活分层定价，适用于任何商家。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以轻松 [自定义外观](payments-options.md) Payment Services扩展的PayPal智能按钮和信用卡字段的数量。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [编辑器键不正确](https://support.magento.com/hc/en-us/articles/4406603542541) 在安装扩展期间，会阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 报告 [不能立即同步](https://support.magento.com/hc/en-us/articles/4406114741517).

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> 您的 [PayPal沙盒帐户](https://support.magento.com/hc/en-us/articles/4406954952461) 表示 [!DNL Payment Services] 如果您在载入过程中创建该帐户，则无法验证。
