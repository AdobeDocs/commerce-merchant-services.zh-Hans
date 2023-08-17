---
title: “Adobe Commerce用户的结账流程”
description: “概述 [!DNL Quick Checkout] 流量中指定哪些流量适合使用Adobe Commerce用户。”
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 现有Adobe Commerce用户：其工作方式

在使用以下方式下订单时，现有Adobe Commerce用户可以选择已保存的送货和付款详细信息 [!DNL Quick Checkout] 以获得更快的结账体验。

当购物者在结帐时输入电子邮件地址时， [!DNL Quick Checkout] 验证它并找到现有的 [!DNL Bolt] 帐户。

## Adobe Commerce和中的注册用户 [!DNL Bolt]

当购物者同时是Adobe Commerce和中的注册用户时 [!DNL Bolt] 网络，这两个网络都提供了存储的装运和付款详细信息。

如果 [!DNL Bolt] 在结账期间找到帐户，购物者可以继续其 [!DNL Quick Checkout] 无缝结账体验：

1. 输入发送给该用户的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或手机，具体取决于 [用户在 [!DNL Bolt] 帐户](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP弹出窗口](assets/new-logo-otp-email.png)

1. 使用登录后 [!DNL Bolt] 帐户，则将自动添加详细信息：

   - 配送信息
   - 付款方式

1. 下订单。

>[!NOTE]
>
> 仅当购物者位于结帐页面上时，才会出现“螺栓OTP”弹出窗口。 购物者可以通过关闭该弹出窗口来选择退出登录Bolt。

如果购物者在结帐前登录到Adobe Commerce，则 [!DNL Bolt] 结帐期间不会出现OTP弹出窗口，但会显示一条消息，建议购物者登录以访问其Bolt Wallet。

如果您在以现有Adobe Commerce用户身份下达订单时遇到问题，请参阅 [快速签出问题疑难解答](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Adobe Commerce帮助中心中的文章。

## 自动登录

自动登录组件可检测购物者何时具有活动的Bolt会话，并自动将购物者登录。 这会跳过帐户检测和一次性密码(OTP)步骤，因为购物者在上一个会话中完成了它们。

可以配置自动登录 [!DNL Quick Checkout] 用户。 您可以启用配置以在签出期间自动登录用户。

1. 在 _管理员_ 侧栏，导航到 **商店** > **配置** > **结帐** 以访问常规签出管理配置页面。
1. 在 _服务设置_ 部分 [!DNL Quick Checkout]，并提供设置自动登录所需的所有详细信息。

请参阅 [[!DNL Quick Checkout] 配置服务设置](../quick-checkout/onboarding.md#configure-service-settings) 主题以了解更多信息。

>[!NOTE]
>
> 首次登录时间 **自动登录** 要启用，需要用户同意并接受弹出窗口以对其进行授权。

## 新建 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 找到帐户后，购物者继续其默认的现成Adobe Commerce结账，并且购物者会从其保存的信息中选择所有必要的详细信息来下达订单：

- 配送和帐单信息
- 配送方式
- 审核付款方式
- 注册选项 [!DNL Bolt] 此时会出现以下提示：在下订单前结账速度更快。 购物者可以同意条款和条件以创建其 [!DNL Bolt] 帐户。

  ![记住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
