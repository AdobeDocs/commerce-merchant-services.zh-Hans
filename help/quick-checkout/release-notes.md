---
title: ’[!DNL Quick Checkout] 发行说明
description: 查看发行说明，了解所有 [!DNL Quick Checkout] 版本发布。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
feature: Release Notes, Services, Checkout
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# 发行说明

以下发行说明介绍了的初始版本 [!DNL Quick Checkout] 并包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

请参阅 [即将发布的版本](https://devdocs.magento.com/release/) 了解发布计划和支持。

请参阅 [可用性](https://devdocs.magento.com/release/availability.html) ，了解有关产品兼容性的信息。

## 管理面板更新

这些发行说明描述了发生的功能更改和修复，这些更改和修复是在管理员面板的常规版本控制功能发布之外发布的。

+++管理面板更新

2023年5月23日_

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-489 --> 现在， **新帐户** 中的组件 [!DNL Quick Checkout] 报告页面包含频谱 [工作流图标](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_2023年4月25日_

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-452 --> 此 [!DNL Quick Checkout] **进行导览** 现在，按钮将鼠标悬停在其上方时，会显示可单击的手光标。

_2023年4月19日_

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-596 --> 此 [!DNL Quick Checkout] 在解析ISO 8601格式的日期时，“报告”页面现在可正确显示“新帐户”图表。

_2022年12月14日_

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-524 --> 此 [!DNL Quick Checkout] “管理员”面板现在可显示正确的总订单数和更新的报表信息。

_2022年11月30日_

![新建](../assets/new.svg)<!-- Issue BOLT-502 --> 现在， [报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tab具有新的“去年”预设。

![新建](../assets/new.svg)<!-- Issue BOLT-471 --> 中的用户体验改进 [!DNL Quick Checkout] 管理面板显示详细信息，请参阅 [工具提示](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-514 --> 中的用户体验改进 [!DNL Quick Checkout] 管理面板为所有图表显示正确的总订单数、颜色一致性和正确图例。

_2022年11月2_

![新建](../assets/new.svg)<!-- Issue BOLT-293 --> 现在， [报告](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 选项卡 [!DNL Quick Checkout] 管理面板可显示商店的结账体验统计信息的图表和报告信息。

![新建](../assets/new.svg)<!-- Issue BOLT-422 --> 此 [_概述_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 报表主题部分的部分显示有关商店结账性能的详细信息，包括平均结账时间、结账期间创建的新帐户以及结账放弃。

![新建](../assets/new.svg)<!-- Issue BOLT-423 --> 此 [_趋势_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) “报表”选项卡的部分显示按帐户类型过滤的签出体验趋势以及在签出期间创建的新帐户。

![新建](../assets/new.svg)<!-- Issue BOLT-439 --> 此 **报表** 选项卡显示 [默认筛选预设](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 区域来显示特定数据范围。

![新建](../assets/new.svg)<!-- Issue BOLT-433 --> 您现在可以看到 _无可用数据_ 请求未返回数据时图表出现警告。

![新建](../assets/new.svg)<!-- Issue BOLT-473 --> 用户体验改进，来自 [!DNL Quick Checkout] 管理面板包括启用 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 设置，允许Adobe Commerce与Bolt共享报表信息。

_2022年10月5_

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> 现在，当新商家访问 [!DNL Quick Checkout] 首次使用管理面板 [功能导览，由Gainsight提供支持](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 显示。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **报表** 选项卡 [!DNL Quick Checkout] “管理”面板可显示图表和报告分析。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 此 **报表** 选项卡 [!DNL Quick Checkout] “管理”面板显示图表和报告分析的日期范围和过滤器预设。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> 现在， [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 在页脚中显示应用程序版本。

+++

## v1.8.0

_2023年2月24日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-520 --> 正式发布版 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 现已在Adobe Commerce Cloud版本2.4.6及更高版本中预安装。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-592 --> 在中下订单时的用户体验改进 [管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) 使用 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 作为支付方式。 此功能允许客户在结账时以Braintree作为付款方式下订单 [!DNL Quick Checkout] 已启用。

## v1.7.0

_2023年2月22日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复的问题](../assets/fix.svg)<!-- Issue AC-8002 --> 使用下达订单时的用户体验改进 [多运输](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) 方法。 此功能支持在结账时显示支付方式 [!DNL Quick Checkout] 已启用。

## v1.6.0

_2023年2月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-567 --> 在以下情况下改善用户体验： [下订单](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 使用 [店内投放](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 具有的方法 [!DNL Quick Checkout] 已禁用。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-569 --> 改进了注销功能，允许购物者 [从螺栓网络注销](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023年1月18日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-522 --> 可以启用/禁用新配置以检测 [购物者](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 可自动登录Bolt。

![新建](../assets/new.svg)<!-- Issue BOLT-523 --> 可以启用/禁用新的配置，该配置允许商家指定购物者是否可以自动登录到两个网络，或者仅登录Bolt网络。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-542 --> 在以下情况下改善用户体验： [将卡或地址保存到Bolt帐户](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 购物者提供电子邮件时。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-550 --> 中的用户体验改进 [自动登录](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) 当Bolt用户提供电子邮件时。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-544 --> 的兼容性改进 [回调URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 替换为 [多站点](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 在Bolt。

## v1.4.0

_2022年11月30日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-513 --> 现在，当Adobe Commerce客户在结帐过程中登录到应用商店，并且具有Bolt帐户时，将会显示用于登录到购物者的Bolt帐户的选项。

![新建](../assets/new.svg)<!-- Issue BOLT-512 --> 新配置会自动检测已登录的购物者是否也可以在Bolt中登录。

![新建](../assets/new.svg)<!-- Issue BOLT-480 --> 中的新配置 [!DNL Quick Checkout] 管理员面板允许您将默认导航流更改为 **配送** 一旦Bolt客户登录就翻页。 默认情况下，它被配置为 **支付** 页面。

## v1.3.0

_2022年11月2_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-293 --> 现在， [!DNL Quick Checkout] 包括启用 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 设置，允许Adobe Commerce与Bolt共享报表信息。

![新建](../assets/new.svg)<!-- Issue BOLT-461 --> 您现在可以在以下位置看到警告消息： [!DNL Quick Checkout] 管理面板，如果 [结账跟踪](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 配置已禁用。

## v1.2.0

_2022年9月8日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布版 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.5兼容。

![新建](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] 对于Adobe Commerce，Magento Open Source提供 [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 以及设置和使用扩展所需的所有信息。

![新建](../assets/new.svg)<!-- Issue BOLT-364 --> 管理员用户 [可以设置用户角色和权限](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允许其他用户查看 [!DNL Quick Checkout] 管理面板。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 管理面板现在包含一个页面标题，其中包含特定部分，例如 **概述**， **报表**、和 **设置**.

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> 当新商家访问 [!DNL Quick Checkout] 首次显示欢迎小组件的“管理”面板，其中提供了功能导览。

![新建](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包含一个 **配置** 未在中提供API和可发布密钥时显示的步骤 [设置](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 视图。

![新建](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包含一个 **资源** 根据载入阶段而变化的部分。

![新建](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包括 **帮助与支持** 部分。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> 此 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在在页脚中显示扩展版本。

## v1.1.0

_2022年8月12日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的用户体验改进 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在，仅包含在启用扩展时可见并验证的参数。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-349 --> 改进了现有送货地址与Bolt Wallet的兼容性。

## v1.0.0

_2022年8月9日_

[!BADGE 兼容性]{type=Informative tooltip="兼容性"}

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布版 — [[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.1到2.4.4兼容。

![新建](../assets/new.svg)<!-- Issue BOLT-340 --> 此 [!DNL Quick Checkout] for Adobe Commerce可以为Adobe Commerce安装 [在云基础架构上](install.md#adobe-commerce-on-cloud-infrastructure) 或 [内部部署](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce提供优化的店面，允许 [一键式结账体验](overview.md) 不需要使用者填写字段。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] for Adobe Commerce会自动识别其网络中的每个购物者，以便 [一键式购买](checkout-flow.md) 直接在您的网站上。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 此 [!DNL Quick Checkout] (适用于Adobe Commerce)允许购物者同时 [已登录Adobe Commerce和Bolt网络](checkout-flow.md/#quick-checkout-use-cases) 提供更好的 `one-click checkout` 体验。

![新建](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] for Adobe Commerce支持 [沙盒帐户](testing.md#testing-in-sandbox) 这允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue BOLT-780 --> 您的购物者可以通过 [[!DNL Quick Checkout]](checkout-page.md) 扩展或通过 [人工创建订单](create-order-admin.md).

![新建](../assets/new.svg)<!-- Issue BOLT-666 --> 商家可以配置 [!DNL Quick Checkout] 具有基本支付操作，例如 [`Authorize and Capture` 或 `Authorize`](onboarding.md#complete-admin-configuration)，或在沙盒环境和生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue BOLT-288 --> 自定义 [用户会话生命周期](user-session-lifetime.md) 对象 [!DNL Quick Checkout] 用于Adobe Commerce。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 中的用户体验改进 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 允许您在提供了所有必需的参数时保存配置。

![已知问题](../assets/bug.svg)<!-- Issue BOLT-342 --> 公共 [故障排除](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 安装期间的问题 [!DNL Quick Checkout].
