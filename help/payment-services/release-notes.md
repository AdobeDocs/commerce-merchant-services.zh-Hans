---
title: '"[!DNL Payment Services] 发行说明”'
description: 查看发行说明，了解所有 [!DNL Payment Services] 版本发布。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 9f0381546a98a8a5d72394adbd3ddd49daf539cb
workflow-type: tm+mt
source-wordcount: '2547'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了的初始版本 [!DNL Payment Services] 并包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

有关在常规功能发布版本之外发布的功能更改和修复，请查看 _托管服务更新_ 部分。

详细了解即将发行的版本、产品支持以及Adobe Commerce的哪些版本支持 [!DNL Payment Services] 扩展，请参阅Adobe Commerce [发布计划](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) 和 [产品可用性](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) 主题。

## 托管服务更新

这些发行说明描述了所发生以及发行的功能更改和修复，这些更改和修复超出了托管服务的常规功能发行版本。

+++托管服务更新

_2024年7月9日_

![新建问题](../assets/new.svg)<!-- Issue PAY-5488 --> Commerce现在，商家可以在 [交易报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 帮助识别特定客户已进行的交易。 此外，商家还可以按此Commerce客户ID筛选关联订单的交易报表。

_2024年3月5日_

![修复的问题](../assets/fix.svg)<!-- Issue PAY-5252 --> 现在，商家可以通过选择单个单元格的内容，从功能板网格中复制数据。

_2023年10月10日_

![新建问题](../assets/fix.svg)<!-- Issue PAY-4888 --> 现在，商家可以根据以下位置中卡号的最后4位数过滤信用卡和借记卡交易： [交易报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_2023年7月12日_

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4587 --> 中引入了一个问题 [!DNL Payment Services] 2.1.0版本防止了由以前的扩展版本设置的授权void，现在该版本已得到解决。 商家使用任何版本的 [!DNL Payment Services] 可能会使授权失效。

_2023年6月9日_

![新建](../assets/new.svg)<!-- Issue PAY-4288 --> 现在，商家可以 [配置 _仅限_ PayPal付款按钮](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) — 和 _非_ 使用PayPal信用卡支付选项。 这允许商家提供各种支付选项，包括Venmo和PayPal支付按钮，并使用现有的信用卡提供商而不是PayPal信用卡支付选项。

![新建](../assets/new.svg)<!-- Issue PAY-4050 --> 添加了 [数据可视化视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view)，显示在付款服务主页上，用于订单付款状态报表。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4486--> 以前，PayPal PayLater按钮不会出现在英国商家的结账单中。 该问题已得到解决。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4485--> 报表数据可视化视图现在显示于 [!DNL Payment Services] 主页时间[!DNL Payment Services] 已禁用。

_2023年1月25日_

![已知问题](../assets/bug.svg)<!-- Issue PAY-4102 --> 的新安装 [!DNL Payment Services] 无法配置Commerce服务，正在呈现 [!DNL Payment Services] 无法操作。 要解决此问题，请更新您的 [!DNL Payment Services] 扩展至版本1.5.3。

_2022年9月12日_

![新建](../assets/new.svg)<!-- Issue PAY-3705 --> 此 `increment_id` 现在可用于调节外部ERP系统中的付款。 它会传播到 [`custom_id` _和_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)，在PayPal webhook和付款的商家活动详细信息中均可见。

_2022年8月31日_

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3629 --> 当新商家访问 [!DNL Payment Services] 首页，页面现在会立即加载以显示内容，而不是需要页面刷新。

_2021年8月9日_

![新建](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay现已作为PayPal智能按钮提供。 此 [付款选项](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 允许客户在其iOS或macOS设备上使用Touch ID功能来选择Apple Pay。 Apple Pay使用存储在设备上的信用卡和借记卡支付凭据处理支付。

_2021年6月28日_

![新建](../assets/new.svg)<!-- Issue PAY-1720 --> 有关商店订单的争议现已可在 [订单付款状态报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). 您可以直接从导航到PayPal解决中心来解决争议 [!DNL Payment Services].

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 来自的用户体验改进 [!DNL Payment Services] 主页包含在当前继承级别修改配置的功能，并改进了标题和导航的显示方式。

![新建](../assets/new.svg)<!-- Issue PAY-2854 --> 现在，当您从沙盒模式切换到生产模式时，以及当您尝试离开包含尚未保存的更新的视图时，您会看到警告。

![新建](../assets/new.svg)<!-- Issue PAY-2761 --> 您现在可以自定义以下位置显示的数据： [订单付款状态报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 和 [支付报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 通过使用“列设置”控件显示或隐藏列。

+++

## v2.6.0

_2024年6月4日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-4877 --> 现在， [!DNL Payment Services] 支持 [L2/L3定价功能](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). 此功能仅适用于 [!DNL Payment Services] 启用了IC++定价的客户。 如果要使用L2/L3处理数据 [!DNL Payment Services]，请联系 [!DNL Payment Services] 客户经理。

![修复](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] 允许您直接从扩展启用Apple Pay，而无需下载和托管 [域关联文件](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_2024年4月23日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] 现在支持 [Adobe Commerce准则 `--db-prefix` 参数](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) 适用于Adobe Commerce版本2.4.7及更高版本。

## v2.4.3

_2024年4月16日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- Issue PAY-5106 --> 修复了在PayPal和Adobe Commerce之间结账时错误填充订单金额合计的问题。 现在，商家可以在下订单时确保订单金额合计正确。

## v2.4.2

_2024年4月11日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue xxx --> 添加了对Adobe Commerce 2.4.7的支持。

## v2.4.1

_2024年4月4日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- PAY-5322 --> 修复了较新的Adobe Commerce版本存在的PCI兼容性问题。 现在， [!DNL Payment Services] 适用于作为付款选项的Adobe Commerce中的结账要求。

![修复](../assets/fix.svg)<!-- PAY-5323 --> PayLater和Venmo在Adobe Commerce中正确显示。 修复了导致管理员无法显示PayLater和Venmo切换选项的错误。

## v2.4.0

_2024年3月20日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-4868 --> 商家可以成功 [在购买过程中配置Google Pay](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html)，类似于中的其他付款按钮[!DNL Payment Services] 通过管理员。

![新建](../assets/new.svg)<!-- PAY-4381 --> [Payment Services支持通过GraphQL使用Google Pay](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) 允许商家在Google Pay支付方法方面享有Headless Commerce体验。

![新建](../assets/new.svg)<!-- PAY-4878 --> 现在， [!DNL Payment Services] 为Adobe Commerce和Magento Open Source商家捆绑了基本结账功能。[!DNL Payment Services] 现在可支持在全球200个地理区域内开展业务的商家。[!DNL Payment Services] 基本结账功能在自助式入门培训中提供借记/贷记、PayPal、Venmo（如果可用）和PayLater（如果可用）选项。

![修复](../assets/fix.svg)<!-- PAY-5291 --> 接收某些交易记录的付款确认可能会延迟。 在这种情况下，商家现在可以获得订单的更新付款状态。 [付款服务检测付款交易记录的待处理状态](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) 通过检测待定事务并主动监视这些事务并在已捕获待定状态时进行更新，按顺序执行操作。

## v2.3.4

_2024年3月1日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-5244 --> 修复了异步签出兼容性。

![修复](../assets/fix.svg)<!-- PAY-5253 --> 修复了保险库令牌不属于 [!DNL Payment Services] 无法删除。

## v2.3.3

_2024年2月14日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-5048 --> 添加了对PHP 8.3的支持

![修复](../assets/fix.svg)<!-- PAY-5048 --> 修复了错误 `is_deleted` 标志。 现在，订单不会由于 `Rejected` 从扩展发送的状态。

## v2.3.2

_2024年1月26日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- PAY-5183 --> 修复了REST/GraphQL性能问题。 现在，通过API获取时，信用卡按钮呈现。

## v2.3.1

_2023年12月7日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-5047 --> 信用卡/借记卡品牌或支付方式类型现在可从以下位置获得：

- 店面的客户订单页面
- 发送给购物者的订单确认电子邮件
- 从 [订单详细信息视图](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) 在Commerce Admin中。

## v2.3.0

_2023年12月1日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-4381 --> [Payment Services现在支持GraphQL集成](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). GraphQL支持PayPal支付按钮、托管字段和Apple Pay，[!DNL Payment Services] 现在支持headless Commerce设置。

## v2.2.1

_2023年9月27日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4870 --> 修复了在使用最新版本发送扩展版本时，Storefront中正确填充新标题属性的问题。 以前，使用 `1.3.0` 发布Commerce服务连接器，您无法扩展 `User-Agent header` 从 [!DNL Payment Services] 扩展。

## v2.2.0

_2023年8月30日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- PAY-4638 --> 添加了 [与Signifyd集成](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html)，可提供自动化的欺诈保护服务。

![新建](../assets/new.svg)<!-- PAY-3981 --> [已将Apple Pay提升为单独的付款选项](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)，以提升付款选项的购物者可见性，并允许商家控制Apple Pay的版面和样式。

![新建](../assets/new.svg)<!-- PAY-4002 --> 改进了信用卡字段结账的用户体验，包括样式改进，例如添加付款图标，以降低购物者的认知负载并提高转化率。

![新建](../assets/new.svg)<!-- PAY-4002 --> 添加的功能允许商家执行以下操作 [排序其付款选项的顺序](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) 确定某些支付选项的优先级。 此功能可提高结帐对话率。

![新建](../assets/new.svg)<!-- PAY-4035 --> 商家现在可以有效地监控店铺的健康状况，并使用新的识别任何交易问题 [交易报表](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 可从以下位置获取：[!DNL Payment Services] 管理主页。 此报表还会提供有关交易授权率和负交易趋势的数据。

## v2.1.0

_2023年6月9日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue xxx --> 添加了对Adobe Commerce 2.4.7-beta1的支持。

![新建](../assets/new.svg)<!-- Issue xxx --> 已添加 [在下列国家/地区和相关货币中的可用性](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability)：澳大利亚、法国、英国。

![新建](../assets/new.svg)<!-- Issue PAY-4296 --> 已添加 [扩展了管理员角色的资源](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) 以确保管理员用户可以创建和管理客户的订单，并且可以[!DNL Payment Services] 在Sales菜单中。

![新建](../assets/new.svg)<!-- Issue PAY-4236 --> 已添加 [在结帐期间发生错误的订单的自动作废](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![新建](../assets/new.svg)<!-- Issue PAY-4183 --> 创建的功能 [显示信用卡/借记卡付款选项按钮](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) 在结帐页面上。

## v2.0.0

_2023年3月10日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-4152 --> 添加了对PHP 8.2和Adobe Commerce 2.4.6的支持。与PHP 7.x不兼容。

## v1.6.1

_2023年3月10日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- Issue PAY-4226 --> 修复了阻止新建的问题 [!DNL Payment Services] 商户在管理员中使用结帐。[!DNL Payment Services] 之前使用的是Commerce客户ID，而新客户不存在该ID。

![修复](../assets/fix.svg)<!-- Issue PAY-4205 --> 修复了在使用结帐时，导致指定的送货地址状态被默认税务设置中的状态替换的问题 [PayPal选项](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). 现在，客户可以将他们的订单发往商户税务设置中配置为默认状态的状态以外的其他状态。

![修复](../assets/fix.svg)<!-- Issue PAY-4202 --> 修复了导致客户无法使用卡保险存储完成购买或删除商店的保险存储付款方法的问题 [使用 `Authorize and Capture` 付款操作](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). 以前，当客户尝试使用或修改其保险存储信用卡时，会出现“Provider Vault ID未找到”错误。

## v1.6.0

_2023年2月17日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-3540 --> 已添加 [PCI 3DS合规性功能，适用于在欧盟(EU)和英国进行交易的商家](security.md#3ds). 这一额外的安全层要求购买者使用其信用卡发行商进行身份验证，有助于防止在线欺诈，并且是欧盟(EU)合规条例的必备要求。

![新建](../assets/new.svg)<!-- Issue PAY-3609 --> 添加了以下功能 [在管理员中启用信息卡保险存储](vaulting.md#use-vaulting-in-the-admin). 这允许商家使用他们存储的支付方式在管理员中为客户创建订单。

## v1.5.4

_2023年1月29日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4110 --> 修复了导致购买者无法使用产品页面、迷你购物车和购物车上的付款按钮下达订单的问题。 买家现在可以成功完成订单。

## v1.5.3

_2023年1月25日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复的问题](../assets/fix.svg)<!-- Issue PAY-4102 --> 发布了对向后不兼容的已知问题的修复。 此发行版本将服务ID扩展版本锁定到最新稳定版本，从而重新启用新版本 [!DNL Payment Services] 安装以配置Commerce服务。

## v1.5.2

_2022年12月22日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3992 --> 改进了中的开票 [!DNL Payment Services] 当付款方式被拒绝时。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] 现在可以使用为商家正确显示PayPal付款按钮 [触发签出](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} 签出页面的自定义模板。 以前，微型画间歇性地显示按钮。

## v1.5.1

_2022年11月23日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] 现在，用户代理标头中包含版本号，以便请求可以跟踪、过滤或弃用未使用的端点。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] 现在，当使用付款按钮从产品页面下达订单时，可以正确显示订单数据。

## v1.5.0

_2022年11月18日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-3880 --> 购物者现在可以 [在结账时保存其信用卡信息](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 在以后为同一商店或同一商家帐户内的其他商店购买时使用。

![新建](../assets/new.svg)<!-- Issue PAY-3950 --> 商家现在可以启用 [即时购买Commerce功能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 以便顾客能够(使用 [保险存储信用卡信息](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html))以加快结帐速度。

## v1.4.1

_2022年10月14_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复](../assets/fix.svg)<!-- Issue PAY-3766 --> 当客户的支付方式被拒绝时，显示的错误消息更具描述性。 它建议客户重新输入付款信息，然后重试，尝试其他付款方式，或就拒绝的交易联系其银行。

## v1.4.0

_2022年9月30日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] 现在包括设置商家帐户以 [使用多个PayPal企业帐户](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). 这使商家能够使用不同的货币在多个国家/地区经营您的商店，或者将Adobe Commerce用于您的部分业务。

![新建](../assets/new.svg)<!-- Issue PAY-3231 --> 商家可以 [添加 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 对于客户交易银行对帐单上显示的网站或单个商店视图配置，以描述品牌、商店或产品线。

![新建](../assets/new.svg)<!-- Issue PAY-3707 --> [启用或禁用信用卡字段和PayPal付款按钮](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) 用于签入[!DNL Payment Services] 设置。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3546 --> 客户点击时 **[!UICONTROL Edit cart]**，页面将重定向到购物车页面，并显示更新的项目，而不是显示空购物车。

## v1.3.1

_2022年9月6日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3663 --> 现在，当商家的商店捕获授权使用非全局货币的订单时，捕获进程将完成，并且不显示错误。

## v1.3.0

_2022年8月9日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-XX --> 正式发布版 — [!DNL Payment Services] 为现在 [支持方 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay现在与移动和桌面上的Safari浏览器v15.5兼容。

## v1.2.0

_2022年6月29日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![已知问题](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay与移动和桌面上的Safari浏览器v15.5不兼容。 使用Safari版本15.5时，无法使用Apple Pay完成签出。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前，当登录用户为其帐户选择默认地址以外的账单/运送地址时，签出失败。 现在，将发送选定的账单/运送地址（而不是默认的保存地址），并成功完成结账。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3314 --> 如果禁用PayPal付款按钮以进行结帐，则不会显示错误。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3330 --> 当访客用户输入包含短划线的电话号码时，在结账期间付款不再失败。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> 当Commerce服务凭据无效时，[!DNL Payment Services] 现在，通过显示凭据错误，提醒您 [!DNL Payment Services] 在Admin中主页。

![已知问题](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 与不兼容 `commerce-data-export` v101.20及更高版本，这使得它与 [[!DNL Channel manager] 扩展](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022年3月31日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布版 — [!DNL Payment Services] 为现在 [支持方 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新建](../assets/new.svg)<!-- Issue PAY-2682 --> 此 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 现在向加拿大商家提供。 商家可以在以下任意位置查看支付配置： [法语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) 或 [英语](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![新建](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 支持 [加元(CAD)](overview.md#accepted-credit-cards-and-currencies) 用于信用卡和PayPal交易。

![新建](../assets/new.svg)<!-- Issue PAY-2680 --> 商家可以 [板载 [!DNL Payment Services]](onboard.md) 英语或法语的扩展。

![新建](../assets/new.svg)<!-- Issue PAY-2678 --> 商家现在可以查看财务报表，包括 [订单付款状态](order-payment-status.md) 和 [支付报表](payouts.md)，加元(CAD)。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] 现在与 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-3017 --> 改进了沙盒模式警报，以显示具有多个存储的正确警报。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2742 --> 您现在可以在商店视图级别启用和禁用可用的付款方法，例如Venmo。 以前，您只能为每个网站配置支付方式。

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2277 --> 您现在可以选择 [启用或禁用单个PayPal付款按钮](settings.md#payment-buttons).

![修复的问题](../assets/fix.svg)<!-- Issue PAY-2561 --> 之前删除的产品不会出现在的购物车中 _审阅订单_ 页面。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2842 --> 测试信用卡交易记录 [可能无法通过PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) 在沙盒环境中处理付款时。

## v1.0.0

_2021年11月29日_

[!BADGE 支持]{type=Informative tooltip="支持"}

![新建](../assets/new.svg)<!-- Issue PAY-2127 --> 正式发布版 — [[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) 现在受支持 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 版本2.4.0到2.4.3 - p1.

![新建](../assets/new.svg)<!-- Issue PAY-124 --> 此 [!DNL Payment Services] 扩展 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 可以安装用于 [[!DNL Adobe Commerce] 在云基础架构上](install.md#adobe-commerce-on-cloud-infrastructure) 或 [内部部署](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 支持 [沙盒帐户](sandbox.md) 这允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue PAY-666 --> 商家可以 [配置支付服务](settings.md) 扩展与基本支付行为，例如利用 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 在沙盒或生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue PAY-780 --> 您的购物者可以使用 [!DNL Payment Services] 或通过 [人工创建订单](create-order.md).

![新建](../assets/new.svg)<!-- Issue PAY-1856 --> 全面的报告功能，通过 [订单付款状态](order-payment-status.md) 和 [支付报表](payouts.md)，可用于 [!DNL Payment Services] 以便您清楚地了解商店的订单和相关付款。

![新建](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 支持基于总处理量的灵活的分层定价，适用于任何商家。

![新建](../assets/new.svg)<!-- Issue PAY-1443 --> 您可以轻松地 [自定义外观](payments-options.md) 的PayPal付款按钮和信用卡字段 [!DNL Payment Services] 扩展。

![已知问题](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [不正确的编辑器键](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 在安装扩展期间，阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 带正确的 `MAGEID`.

![已知问题](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 报表 [不能立即同步](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![已知问题](../assets/bug.svg)<!-- Issue PAY-2475 --> 您的 [PayPal沙盒帐户](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) 对象 [!DNL Payment Services] 如果您在新用户引导期间创建该帐户，则无法验证。
