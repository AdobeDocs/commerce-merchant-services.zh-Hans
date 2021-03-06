---
title: '"[!DNL Payment Services] 发行说明"'
description: 查看发行说明，了解有关 [!DNL Payment Services] 版本。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 78f17e82a820a8be73c6abc0ef25d1bb240ea238
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了 [!DNL Payment Services] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

有关在常规版本控制的功能版本之外发布的功能更改和修复，请参阅托管服务更新部分。

请参阅 [即将发行的版本](https://devdocs.magento.com/release/) 了解发行计划和支持。

请参阅 [可用性](https://devdocs.magento.com/release/availability.html) ，以了解有关产品兼容性的信息。

## v1.2.0

_2022年6月29日_

![已知问题](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay与移动设备和桌面设备上的Safari浏览器v15.5不兼容。 使用Safari版本15.5时，您无法使用Apple Pay完成结帐。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前，当登录用户选择与其帐户的默认地址不同的帐单/送货地址时，结帐失败。 我们修复了此问题，现在已发送选定的帐单/送货地址（而不是默认的保存地址），并且结帐已成功完成。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3314 --> 如果禁用PayPal智能按钮进行结帐，则不会显示任何错误。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3330 --> 当来宾用户输入包含短划线的电话号码时，付款在结账期间不再失败。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> 当商务服务凭据无效时， [!DNL Payment Services] 现在，主页将显示在管理员中。 出现凭据错误，提醒您凭据无效。

![已知问题](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 当前与不兼容 [`commerce-data-export` v101.20及更高版本](https://github.com/magento-commerce/commerce-data-export/releases/tag/v101.2.0)，这会使其与不兼容 [[!DNL Channel manager] 扩展](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

### 托管服务更新

这些发行说明描述了在当前v1.2.0版本与托管服务的先前1.1.0版本之间，在常规版本控制功能发布之外发生的功能更改和修复。

![新建](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay现已作为PayPal智能按钮提供。 此 [付款选项](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 允许客户在其设备上使用触屏ID来使用Apple Pay，它使用存储在其iOS或macOS设备上的信用卡和借记卡付款凭据。

![新建](../assets/new.svg)<!-- Issue PAY-1720 --> 现在，商店订单争议可在 [订单付款状态报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). 您可以从直接导航到PayPal Resolution Center [!DNL Payment Services] 就纠纷采取行动。

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 改进了 [!DNL Payment Services] 主页包括在当前继承级别修改配置的功能，以及改进标题和导航的显示。

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 现在，当您从沙盒模式切换到生产模式，以及尝试从视图导航到尚未保存的更新时，您会看到警告。

![新建](../assets/new.svg)<!-- Issue PAY-2761 --> 您现在可以自定义 [订单付款状态报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 和 [派息报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 显示或隐藏列时，会显示或隐藏列。

## v1.1.0

_2022年3月31日_

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布 — [!DNL Payment Services] 现在 [兼容 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0至2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 的 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 现在可供加拿大商人使用。 商户可以在以下任一位置查看付款配置 [法语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) 或 [英语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支持 [加元(CAD)](overview.md#accepted-credit-cards-and-currencies) 信用卡和PayPal交易。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板载 [!DNL Payment Services]](onboard.md) 英语或法语扩展。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商户现在可以查看 [订单付款状态](order-payment-status.md) 和 [派息报告](payouts.md)，以加元(CAD)表示。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 现在与 [8.1菲律宾比索](https://www.php.net/releases/8.1/en.php).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3017 --> 改进了沙盒模式警报，可通过多个存储区显示正确的警报。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2742 --> 您现在可以在商店视图级别启用和禁用可用的付款方法，如Venmo。 以前，您只能为每个网站配置付款方法。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2277 --> 您现在可以选择性地 [启用或禁用单个PayPal智能按钮](settings.md#payment-buttons).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前删除的产品不会显示在 _审阅顺序_ 页面。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2842 --> 测试信用卡交易记录 [可能因PayPal而失败](https://support.magento.com/hc/en-us/articles/5201041963917) 在沙盒环境中处理付款时。

## v1.0.0

_2021年11月29日_

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布 — [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 现在与 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.3-p1。

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 的 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以为 [[!DNL Adobe Commerce] 云基础架构](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支持 [沙盒帐户](sandbox.md) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置Payment Services](settings.md) 扩展，例如利用 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙盒或生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 您的购物者可以 [!DNL Payment Services] 或通过 [手动订单创建](create-order.md).

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> 通过 [订单付款状态](order-payment-status.md) 和 [派息报告](payouts.md)，可用于 [!DNL Payment Services] 让您清楚地了解商店的订单和相关付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支持基于总处理量的灵活分层定价，适用于任何商家。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以轻松 [自定义外观](payments-options.md) 的PayPal智能按钮和信用卡字段 [!DNL Payment Services] 扩展。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [编辑器键不正确](https://support.magento.com/hc/en-us/articles/4406603542541) 在安装扩展期间，会阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 报告 [不能立即同步](https://support.magento.com/hc/en-us/articles/4406114741517).

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> 您的 [PayPal沙盒帐户](https://support.magento.com/hc/en-us/articles/4406954952461) 表示 [!DNL Payment Services] 如果您在载入过程中创建该帐户，则无法验证。
