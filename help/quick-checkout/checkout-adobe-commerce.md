---
title: 结帐流程
description: 概述 [!DNL Quick Checkout] 流量。Adobe Commerce用户。
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# 现有Adobe Commerce用户：工作原理

现有的Adobe Commerce用户在使用 [!DNL Quick Checkout] 更快的结帐体验。

当购物者在结账时输入其电子邮件地址时， [!DNL Quick Checkout] 验证并查找现有 [!DNL Bolt] 帐户。

## 在Adobe Commerce和 [!DNL Bolt]

当购物者是Adobe Commerce和 [!DNL Bolt] 网络中，两个网络都被提供存储的运输和付款详细信息。

如果 [!DNL Bolt] 帐户在结帐期间找到，购物者可以继续其 [!DNL Quick Checkout] 无缝结账体验：

1. 输入发送到该密码的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或移动设备，具体取决于 [中的用户首选项 [!DNL Bolt] 帐户](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}。

![OTP弹出窗口](assets/pop-up.png)

1. 登录后 [!DNL Bolt] 帐户，详细信息会自动添加：

   - 装运信息
   - 付款方法

1. 下订单。

>[!NOTE]
>
> 仅当购物者位于结账页面时，才会显示“Bolt OTP”弹出窗口。 购物者可以通过关闭该弹出窗口来选择退出登录到Bolt。

如果购物者在结账前已登录Adobe Commerce，则 [!DNL Bolt] 在结账期间，OTP弹出窗口将不显示。

如果您在以现有Adobe Commerce用户身份下订单时遇到问题，请参阅 [快速结帐问题疑难解答](https://support.magento.com/hc/en-us/articles/6909450342541) Adobe Commerce帮助中心中的文章。

## 新建 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 找到帐户后，购物者会继续其默认的现成Adobe Commerce结账，购物者会从其保存的信息中选择所有必需的详细信息以下订单：

- 运输和账单信息
- 装运方法
- 复核付款方法
- 可选择在 [!DNL Bolt] 以便在下订单之前更快地结帐。 购物者可以同意创建其 [!DNL Bolt] 帐户。

   ![记住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
