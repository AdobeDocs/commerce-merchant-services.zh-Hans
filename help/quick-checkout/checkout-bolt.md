---
title: “Bolt用户在Adobe Commerce中的结帐流程”
description: 概述 [!DNL Quick Checkout] 在Adobe Commerce中为Bolt用户流量。
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 来宾用户

来宾结账体验与Adobe用户体验不同。 当购物者输入进入结账的电子邮件地址时， [!DNL Quick Checkout] 验证并查找现有 [!DNL Bolt] 帐户。

>[!WARNING]
>
> 的 [!DNL In-Store Pickup] 当 [!DNL Quick Checkout] 启用。

## 已注册 [!DNL Bolt] 帐户

如果 [!DNL Bolt] 帐户，购物者将继续其 [!DNL Quick Checkout] 无缝结账体验：

1. 输入发送到该密码的一次性密码(OTP) [!DNL Bolt] 帐户的电子邮件地址或移动设备，具体取决于 [中的用户首选项 [!DNL Bolt] 帐户](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP弹出窗口](assets/pop-up.png)

1. 登录后 [!DNL Bolt] 帐户，详细信息会自动添加：

   - 装运信息
   - 付款方法

1. 下订单。

>[!TIP]
>
> 来宾用户下单，他们可以选择在Adobe Commerce中注册。

## 新建 [!DNL Bolt] 帐户

如果否 [!DNL Bolt] 找到帐户后，购物者会继续其默认的现成Adobe Commerce结账，并且购物者会提供所有必需的详细信息以下订单：

- 运输和账单信息
- 装运方法
- 复核付款方法
- 此时会出现一个复选框以注册 [!DNL Bolt] 以便在下订单前更快地结帐。 购物者可以同意创建其 [!DNL Bolt] 帐户。

   ![记住 [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- 来宾用户下单，他们可以选择在Adobe Commerce中注册。
