---
title: 信用卡保险存储
description: 购物者可以保存（保存）其信用卡详细信息，以便将来购买。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡保险存储

通过信用卡保险存储，将一次性客户转化为忠诚的购物者。 购物者可在结帐期间保存（或“保管库”）其信用卡凭据，以供以后购买相同或另一商户帐户的商品时使用。

![保管信用卡供以后使用](assets/save-card-for-later.png)

购物者使用存储的令牌，使用其保存的信用卡信息完成将来的结账。

![将存储的凭据用于将来的购买](assets/use-stored-card.png)

他们还可以轻松地从 [存储的付款方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在他们的账户里。

![我的帐户中存储的付款方法](assets/stored-payment-methods.png)

## 启用保险存储

您可以为客户启用信用卡保险存储 _和_ 管理员中的商户 — 用于 [!DNL Payment Services] [设置](settings.md#card-vaulting).

## 在管理员中使用保险存储

如果客户拥有以前保险存卡，则商家可以在管理员中使用其保险存付方式为该客户创建后续订单。

仅当客户通过之前完成的付款在系统中存储了现有帐户和有效令牌时，才能在管理员中使用拱形卡。

要在管理员中为使用保险卡的客户创建订单，请执行以下操作：

1. [创建订单并添加产品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. 在 _[!UICONTROL Payment & Shipping Information]_，选择&#x200B;**[!UICONTROL Stored Cards]**付款方式。
1. 选择所需的拱形信用卡付款方法。
1. 完成订单的任何其他必要步骤后， [提交](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![在“管理员”中为客户使用拱形信用卡](assets/admin-vaultedcard.png)

## 安全性

与购物者共享的信用卡信息最少；他们只能看到其保险卡的最后四位数字、过期日期和品牌。 信用卡信息与支付提供商一起存储以满足 [PCI](security.md#PCI-compliance) 合规标准。
