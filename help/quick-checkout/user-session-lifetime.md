---
title: 用户会话生命周期
description: 管理员提供为 [!DNL Quick Checkout] 扩展。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 用户会话生命周期

购物者会话的生命周期由多个因素决定，这些因素可以在您的Adobe Commerce管理员中进行配置。 请参阅 [配置Cookie生命周期](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 以了解更多信息。

Cookie的已配置生命周期可能会影响您的 [!DNL Quick Checkout] 如果：

1. 由于不活动，购物者被注销Adobe Commerce。
1. 的 [!DNL Bolt] 会话过期。

如果购物者在 [!DNL Bolt] 会话过期后，会成功下达订单，但用户会从两个网络注销。

如果用户在成功结帐后仍处于活动状态，则他们不会从Adobe Commerce和 [!DNL Bolt].
