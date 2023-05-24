---
title: ‘[!DNL Quick Checkout] 发行说明
description: 查看发行说明，了解关于 [!DNL Quick Checkout] 版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 169b3e365d7f4c0c4cef19fa1941dfa0a95ea58b
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了 [!DNL Quick Checkout] 并包括：

![新](../assets/new.svg) 新增功能
![已修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

参见 [即将发行的版本](https://devdocs.magento.com/release/) 了解发布时间表和支持。

参见 [可用性](https://devdocs.magento.com/release/availability.html) ，了解有关产品兼容性的信息。

## 管理面板更新

这些发行说明描述了发生的功能更改和修复，这些更改和修复是在管理员面板的常规版本化功能发行之外发布的。

+++管理面板更新

2023年5月23日_

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-489 --> 现在， **新帐户** 中的组件 [!DNL Quick Checkout] 报告页面包含频谱 [工作流图标](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_2023年4月25日_

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-452 --> 此 [!DNL Quick Checkout] **进行导览** 现在，按钮将鼠标悬停在其上方时，会显示可单击的手光标。

_2023年4月19日_

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-596 --> 此 [!DNL Quick Checkout] 现在，当将日期解析为ISO 8601格式时，“报告”页面可正确显示“新帐户”图表。

_2022年12月14日_

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-524 --> 此 [!DNL Quick Checkout] “管理”面板现在可显示正确的总订单数和更新的报表信息。

_2022年11月30日_

![新](../assets/new.svg)<!-- Issue BOLT-502 --> 现在， [报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tab具有新的“去年”预设。

![新](../assets/new.svg)<!-- Issue BOLT-471 --> 中的用户体验改进 [!DNL Quick Checkout] “管理”面板显示详细信息，请参阅 [工具提示](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-514 --> 中的用户体验改进 [!DNL Quick Checkout] 管理面板为所有图表显示正确的总订单数、颜色一致性和正确图例。

_2022年11月2_

![新](../assets/new.svg)<!-- Issue BOLT-293 --> 现在， [报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 在中选项卡 [!DNL Quick Checkout] “管理员”面板可显示商店的结账体验统计信息的图表和报告信息。

![新](../assets/new.svg)<!-- Issue BOLT-422 --> 此 [_概述_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 报表主题部分的一部分显示有关商店结账性能的详细信息，包括平均结账时间、结账期间创建的新帐户以及结账放弃情况。

![新](../assets/new.svg)<!-- Issue BOLT-423 --> 此 [_趋势_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) “报表”选项卡的部分显示按帐户类型过滤的签出体验趋势以及在签出期间创建的新帐户。

![新](../assets/new.svg)<!-- Issue BOLT-439 --> 此 **报告** 选项卡显示 [默认筛选条件预设](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 用于显示特定数据范围。

![新](../assets/new.svg)<!-- Issue BOLT-433 --> 您现在可以看到 _无可用数据_ 请求未返回数据时图表出现警告。

![新](../assets/new.svg)<!-- Issue BOLT-473 --> 用户体验改进 [!DNL Quick Checkout] “管理”面板包括启用 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 设置以允许Adobe Commerce与Bolt共享报表信息。

_2022年10月5日_

![新](../assets/new.svg)<!-- Issue BOLT-379 --> 现在，当新商家访问 [!DNL Quick Checkout] 首次使用“管理”面板 [功能导览，由Gainsight提供支持](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 显示。

![新](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **报告** 在中选项卡 [!DNL Quick Checkout] “管理”面板可显示图表和报告分析。

![新](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **报告** 在中选项卡 [!DNL Quick Checkout] “管理”面板显示图表和报告分析的日期范围和过滤器预设。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> 现在， [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 在页脚中显示应用程序版本。

+++

## v1.8.0

_2023年2月24日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-520 --> 正式发布版 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现已预安装在Adobe Commerce Cloud版本2.4.6及更高版本中。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-592 --> 在中下订单时的用户体验改进 [管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) 使用 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 作为支付方式。 此功能允许客户在结帐期间以Braintree作为付款方式下订单 [!DNL Quick Checkout] 已启用。

## v1.7.0

_2023年2月22日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![已修复的问题](../assets/fix.svg)<!-- Issue AC-8002 --> 使用下达订单时的用户体验改进 [多发运输](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) 方法。 在结账时，此功能可显示付款方式 [!DNL Quick Checkout] 已启用。

## v1.6.0

_2023年2月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-567 --> 在以下情况下改善用户体验： [下订单](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 使用 [店内投放](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 方法 [!DNL Quick Checkout] 已禁用。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-569 --> 改进了注销功能，使购物者能够 [从螺栓网络注销](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023年1月18日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-522 --> 可以启用/禁用新配置以检测 [购物者](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 可自动登录Bolt。

![新](../assets/new.svg)<!-- Issue BOLT-523 --> 可以启用/禁用新的配置，该配置允许商家指定购物者是否可以自动登录到两个网络，或者仅登录Bolt网络。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-542 --> 在以下情况下改善用户体验： [将卡或地址保存到Bolt帐户](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 购物者提供电子邮件时。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-550 --> 中的用户体验改进 [自动登录](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) 当Bolt用户提供电子邮件时。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-544 --> 的兼容性改进 [回调URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 替换为 [多站点](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 在Bolt。

## v1.4.0

_2022年11月30日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-513 --> 现在，当Adobe Commerce客户在结帐过程中登录到应用商店，并且具有Bolt帐户时，将显示用于登录到购物者的Bolt帐户的选项。

![新](../assets/new.svg)<!-- Issue BOLT-512 --> 新配置会自动检测已登录的购物者是否也可以在Bolt中登录。

![新](../assets/new.svg)<!-- Issue BOLT-480 --> 中的新配置 [!DNL Quick Checkout] 管理面板允许您将默认导航流更改为 **配送** 一旦Bolt客户登录就翻页。 默认情况下，它被配置为 **支付** 页面。

## v1.3.0

_2022年11月2_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-293 --> 现在， [!DNL Quick Checkout] 包括启用 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 设置以允许Adobe Commerce与Bolt共享报表信息。

![新](../assets/new.svg)<!-- Issue BOLT-461 --> 您现在可以在以下位置看到警告消息： [!DNL Quick Checkout] 管理面板，如果 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 配置已禁用。

## v1.2.0

_2022年9月8日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布版 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.5兼容。

![新](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] for Adobe Commerce和Magento Open Source提供 [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 以及设置和使用扩展所需的所有信息。

![新](../assets/new.svg)<!-- Issue BOLT-364 --> 管理员用户 [可以设置用户角色和权限](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允许其他用户查看 [!DNL Quick Checkout] 管理面板。

![新](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] “管理”面板现在包含一个页眉，其中包含了特定部分，例如 **概述**， **报告**、和 **设置**.

![新](../assets/new.svg)<!-- Issue BOLT-379 --> 当新商家访问 [!DNL Quick Checkout] 首次显示欢迎小组件的“管理”面板，其中提供了功能导览。

![新](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包含一个 **配置** 未在中提供API和可发布密钥时显示的步骤 [设置](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 视图。

![新](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包含一个 **资源** 根据载入阶段而变化的部分。

![新](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包括 **帮助与支持** 部分。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> 此 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在在页脚中显示扩展版本。

## v1.1.0

_2022年8月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的用户体验改进 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在，仅包含启用该扩展时可见并验证的参数。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-349 --> 改进了现有送货地址与Bolt Wallet的兼容性。

## v1.0.0

_2022年8月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布版 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.1到2.4.4兼容。

![新](../assets/new.svg)<!-- Issue BOLT-340 --> 此 [!DNL Quick Checkout] 适用于Adobe Commerce的既可以安装，也可以安装Adobe Commerce [在云基础架构上](install.md#adobe-commerce-on-cloud-infrastructure) 或 [内部部署](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce提供优化的店面，允许 [一键式结账体验](overview.md) 不需要使用者填写字段。

![新](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce自动识别其网络中的每个购物者，以便 [一键购买](checkout-flow.md) 直接在您的网站上。

![新](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce允许购物者同时 [已登录Adobe Commerce和Bolt网络](checkout-flow.md/#quick-checkout-use-cases) 提供更好的 `one-click checkout` 体验。

![新](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] for Adobe Commerce支持 [沙盒帐户](testing.md#testing-in-sandbox) 这允许商家在测试模式下评估扩展。

![新](../assets/new.svg)<!-- Issue BOLT-780 --> 您的购物者可以通过 [[!DNL Quick Checkout]](checkout-page.md) 扩展或通过 [手动订单创建](create-order-admin.md).

![新](../assets/new.svg)<!-- Issue BOLT-666 --> 商家可以配置 [!DNL Quick Checkout] 具有基本支付操作，例如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)，或在沙盒环境和生产环境之间切换。

![新](../assets/new.svg)<!-- Issue BOLT-288 --> 自定义 [用户会话生命周期](user-session-lifetime.md) 对象 [!DNL Quick Checkout] 适用于Adobe Commerce的。

![已修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的用户体验改进 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 允许您在提供了所有必需的参数时保存配置。

![已知问题](../assets/bug.svg)<!-- Issue BOLT-342 --> 公共 [故障排除](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 安装过程中出现的问题 [!DNL Quick Checkout].
