---
title: '[!DNL Quick Checkout] 发行说明'
description: 查看发行说明，了解有关 [!DNL Quick Checkout] 版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 7c99f1aa4bed9878625d855509448494d5547d56
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 1%

---

# 发行说明

以下发行说明介绍了 [!DNL Quick Checkout] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

请参阅 [即将发行的版本](https://devdocs.magento.com/release/) 了解发行计划和支持。

请参阅 [可用性](https://devdocs.magento.com/release/availability.html) ，以了解有关产品兼容性的信息。

## 管理面板更新

这些发行说明描述了在管理面板的常规版本控制功能版本之外发生和发布的功能更改和修复。

+++管理面板更新

_2022年10月5日_

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> [!DNL Quick Checkout] 管理面板集成了 [由Gainsight提供支持的功能导览](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html).

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 的 **报表** 选项卡 [!DNL Quick Checkout] 管理面板包含即将提供的图表和报告信息的概要。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> 的 **报表** 选项卡 [!DNL Quick Checkout] “管理员”面板显示即将提供的图表和报表信息的过滤器日期范围。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在，在页脚中显示react应用程序版本。

+++

## v1.2.0

_2022年9月8日_

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.5兼容。

![新建](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] 对于Adobe Commerce和Magento Open Source，提供了 [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 以及设置和使用扩展所需的所有必要信息。

![新建](../assets/new.svg)<!-- Issue BOLT-364 --> 管理员用户 [可以设置用户角色和权限](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 允许其他用户查看 [!DNL Quick Checkout] 管理面板。

![新建](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 管理员面板现在包含包含特定部分(如 **概述**, **报表**&#x200B;和 **设置**.

![新建](../assets/new.svg)<!-- Issue BOLT-379 --> [!DNL Quick Checkout] “管理员面板”添加了一个欢迎用小组件，该小组件提供了由Gainsight提供支持的功能导览。

![新建](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 合并 **配置** 步骤，当API和可发布密钥未在 [设置](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 中。

![新建](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 合并 **资源** 部分进行更改。

![新建](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理面板视图](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 包括 **帮助和支持** 中。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-369 --> 的 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在在页脚中显示扩展版本。

## v1.1.0

_2022年8月12日_

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 改进了 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 现在，仅包含启用扩展后可见和已验证的参数。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-349 --> 改进了Bolt Wallet现有送货地址的兼容性。

## v1.0.0

_2022年8月9日_

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.1到2.4.4兼容。

![新建](../assets/new.svg)<!-- Issue BOLT-340 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，可以为Adobe Commerce安装 [云基础架构](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，为 [一键式结账体验](overview.md) ，用户无需填写字段。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] for Adobe Commerce自动识别其网络中的每位购物者 [一键式购买](checkout-flow.md) 直接访问您的网站。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，允许购物者同时 [已登录Adobe Commerce和Bolt网络](checkout-flow.md/#quick-checkout-use-cases) 更好 `one-click checkout` 体验。

![新建](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] 对于Adobe Commerce支持 [沙盒帐户](testing.md#testing-in-sandbox) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue BOLT-780 --> 购物者可通过 [[!DNL Quick Checkout]](checkout-page.md) 扩展或通过 [手动订单创建](create-order-admin.md).

![新建](../assets/new.svg)<!-- Issue BOLT-666 --> 商户可以配置 [!DNL Quick Checkout] 基本付款操作(例如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)，或在沙盒和生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue BOLT-288 --> 自定义 [用户会话生命周期](user-session-lifetime.md) 表示 [!DNL Quick Checkout] Adobe Commerce。

![修复的问题](../assets/fix.svg)<!-- Issue BOLT-375 --> 改进了 [[!DNL Quick Checkout] 管理面板](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 允许您在提供所有必需参数时保存配置。

![已知问题](../assets/bug.svg)<!-- Issue BOLT-342 --> 常用 [疑难解答](https://support.magento.com/hc/en-us/articles/6909450342541) 安装过程中出现的问题 [!DNL Quick Checkout].
