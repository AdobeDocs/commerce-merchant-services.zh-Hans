---
title: 用户会话生命周期
description: 管理员可以为配置Adobe Commerce用户的Cookie生命周期， [!DNL Quick Checkout] 扩展。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 用户会话生命周期

购物者会话的生命周期取决于多个因素，可以在Adobe Commerce管理员中进行配置。 请参阅 [配置Cookie生命周期](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 以了解更多信息。

配置的Cookie生命周期可能会影响 [!DNL Quick Checkout] 如果：

1. 由于非活动状态，购物者将会从Adobe Commerce中注销。
1. 此 [!DNL Bolt] 会话过期。

如果购物者在以下情况下下单： [!DNL Bolt] 会话过期，订单已成功下达，但用户已从两个网络注销。

如果用户在成功结账后仍处于活动状态，则他们不会同时从Adobe Commerce和注销 [!DNL Bolt].
