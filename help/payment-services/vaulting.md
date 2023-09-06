---
title: 信用卡保险存储
description: 购物者可以保存（保存）自己的信用卡信息以便将来购买。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡保险存储

通过信用卡保险存储将一次性客户转化为忠诚的购物者。 购物者可以在结账时保存（或“保险库”）他们的信用卡凭据，以便稍后在同一商家帐户内为同一商店或其他商店购买时使用。

![保存他们的信用卡以供将来使用](assets/save-card-for-later.png){width="400" zoomable="yes"}

购物者使用存储的令牌以其保存的信用卡信息完成未来的结账。

![使用存储的凭据供将来购买](assets/use-stored-card.png){width="400" zoomable="yes"}

他们还可以轻松地从中删除其保险存储的信用卡 [存储的支付方式](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在我的帐户中。

![我的帐户中存储的支付方式](assets/stored-payment-methods.png){width="400" zoomable="yes"}

## 启用保险存储

您可以为客户启用信用卡保险存储 _和_ Admin中的商家 — 适用于您的商店 [!DNL Payment Services] [设置](settings.md#card-vaulting).

## 在管理员中使用保险存储

如果客户具有以前存储的信用卡，则商家可以使用其存储的付款方法在“管理员”中为该客户创建后续订单。

如果客户具有现有帐户，并且系统中存储了先前完成的付款的有效令牌，则您只能在管理员中使用保管卡。

要在“管理员”中使用保险存储信用卡为客户创建订单，请执行以下操作：

1. [创建订单并添加产品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. 在 _[!UICONTROL Payment & Shipping Information]_，选择&#x200B;**[!UICONTROL Stored Cards]**作为付款方式。
1. 选择所需的保险存储信用卡支付方式。
1. 完成订单的任何其它必要步骤后， [提交它](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![在管理员中为客户使用保险存储信用卡](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## 安全性

与购物者共享最少信用卡信息；他们只能看到其保险存储信用卡的最后四位数字、过期日期和品牌。 信用卡信息将与付款提供商一起存储以满足 [PCI](security.md#PCI-compliance) 合规性标准。
