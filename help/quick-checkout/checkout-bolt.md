---
title: “Adobe Commerce中Bolt用户的结账流程”
description: 概述 [!DNL Quick Checkout] Bolt用户在Adobe Commerce中的流程。
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 来宾用户

来宾签出体验与Adobe用户体验不同。 当购物者输入电子邮件地址进行结账时， [!DNL Quick Checkout] 验证它并找到现有的 [!DNL Bolt] 帐户。

>[!WARNING]
>
> 此 [!DNL In-Store Pickup] (ISPU)功能在以下情况下不受支持： [!DNL Quick Checkout] 已启用。

## 已注册 [!DNL Bolt] 帐户

如果 [!DNL Bolt] 账户被发现，购物者继续购买他们的 [!DNL Quick Checkout] 无缝结账体验：

1. 输入发送给该用户的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或手机，具体取决于 [用户在 [!DNL Bolt] 帐户](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP弹出窗口](assets/new-logo-otp-email.png)

1. 使用登录后 [!DNL Bolt] 帐户，则将自动添加详细信息：

   - 配送信息
   - 付款方式

1. 下订单。

>[!TIP]
>
> 访客用户下订单，并且可以选择在Adobe Commerce中注册。

## 新 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 账户后，购物者可以继续使用默认的开箱即用Adobe Commerce结账，购物者提供下单所需的所有详细信息：

- 配送和帐单信息
- 配送方式
- 审核付款方式
- 此时会显示一个复选框，以注册 [!DNL Bolt] ，以便在下订单前更快结账。 购物者可以同意条款和条件以创建其 [!DNL Bolt] 帐户。
- 访客用户下订单，并且可以选择在Adobe Commerce中注册。
