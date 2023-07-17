---
title: 结账
description: 根据客户的需求自定义结账。
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# 结账

您可以为Adobe Commerce配置签出 [!DNL Payment Services] 最适合您的购物者。 功能，例如 [订单自动失效](#order-auto-voided-if-error) 和 [信用卡保险存储](#credit-card-vaulting) 确保您的购物者拥有流畅的用户体验。

## 出错时订单自动失效

如果在结账时出现错误， [!DNL Payment Services] 自动撤消/取消订单。

购物者的结帐页面上会显示一条错误消息。 消息可能有所不同。

![检查时出错](assets/user-checkout-error.png "签出时出错")

有关已取消订单的注释也会显示在特定 [订购](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en).

![已取消订单管理员中的订单评论](assets/admin-checkout-error.png "已取消订单管理员中的订单评论")

如果购物者获得订单授权，但订单未创建并转换为 `Capture`，则订单会自动失效。 此过程可确保购物者的信用卡上不会预留任何信用，并避免在标准29天期限结束时授权失效时产生的支付提供商费用。

>[!NOTE]
>
>仅当客户使用的付款方式设置为时，才会发生订单自动作废 `Authorize` 模式，非 `Authorize and Capture` 模式。

## 从产品页面中结帐

客户使用PayPal或 [!DNL Pay Later] 按钮时，只会购买当前产品页面上显示的项目。 已存在于客户购物车中的商品不会添加到结账流程中，也不会被购买。

此功能允许客户快速购买他们当前正在查看的项目，同时保留之前添加到购物车的项目。
如果客户取消订单，则当前产品页面中的项目将添加到客户的购物车中。

当客户从产品页面进入结帐流程时，结帐页面得到简化，视图仅显示与订单相关的数据和选项。

## 信用卡保险存储

购物者可以将其信用卡信息保存或“保存”，以便将来在网站级别（同一商家帐户内的任何商店）进行购买。

参见 [信用卡保险存储](vaulting.md) 了解更多信息
