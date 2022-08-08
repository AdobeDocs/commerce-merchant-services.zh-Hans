---
title: '''[!DNL Quick Checkout] 发行说明'''
description: 查看发行说明，了解有关 [!DNL Quick Checkout] 版本。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 6162141e1ddf4428126178bd172e8d9bd250c485
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 1%

---

# 发行说明

以下发行说明介绍了 [!DNL Quick Checkout] 包括：

![新建](../assets/new.svg) 新增功能
![修复的问题](../assets/fix.svg) 修复和改进功能
![已知问题](../assets/bug.svg) 已知问题

请参阅 [即将发行的版本](https://devdocs.magento.com/release/) 了解发行计划和支持。

请参阅 [可用性](https://devdocs.magento.com/release/availability.html) ，以了解有关产品兼容性的信息。

## v1.0.0

![新建](../assets/new.svg)<!-- Issue BOLT-341 --> 正式发布 — [[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 现在与Adobe Commerce版本2.4.1到2.4.4兼容。

![新建](../assets/new.svg)<!-- Issue BOLT-340 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，可以为Adobe Commerce安装 [云基础架构](install.md#adobe-commerce-on-cloud-infrastructure) 或 [本地](install.md#on-premises) 实例。 这些方法需要使用命令行接口。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，为 [一键式结账体验](overview.md) ，用户无需填写字段。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] for Adobe Commerce自动识别其网络中的每位购物者 [一键式购买](checkout-flow.md) 直接访问您的网站。

![新建](../assets/new.svg)<!-- Issue BOLT-1 --> 的 [!DNL Quick Checkout] 对于Adobe Commerce，允许购物者同时 [已登录Adobe Commerce和Bolt网络](checkout-flow.md/#quick-checkout-use-cases) 更好 `one-click checkout` 体验。

![新建](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] 对于Adobe Commerce支持 [沙盒帐户](testing.md#testing-in-sandbox) 允许商家在测试模式下评估扩展。

![新建](../assets/new.svg)<!-- Issue BOLT-780 --> 购物者可通过 [[!DNL Quick Checkout]](checkout-page.md) 扩展或通过 [手动订单创建](create-order-admin.md).

![新建](../assets/new.svg)<!-- Issue BOLT-666 --> 商户可以配置 [!DNL Quick Checkout] 基本付款操作(例如 [`Authorize and Capture` 或 `Authorize` ](onboarding.md#complete-admin-configuration)，或在沙盒和生产环境之间切换。

![新建](../assets/new.svg)<!-- Issue BOLT-288 --> 自定义 [用户会话生命周期](user-session-lifetime.md) 表示 [!DNL Quick Checkout] Adobe Commerce。

![已知问题](../assets/bug.svg)<!-- Issue BOLT-342 --> 使用 [编辑器键不正确](https://support.magento.com/hc/en-us/articles/6909450342541) 安装期间 [!DNL Quick Checkout] 阻止用户 [身份验证](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正确 `MAGEID`.
