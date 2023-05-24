---
title: 信用卡保险存储
description: 购物者可以保存（保存）信用卡信息以便将来购买。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 信用卡保险存储

通过信用卡保险存储将一次性客户转化为忠诚的购物者。 购物者可以在结账时保存（或“保管库”）他们的信用卡凭据，以便稍后为同一商家帐户内的相同或其他商店购买这些凭据。

![保存他们的信用卡以供将来使用](assets/save-card-for-later.png)

购物者使用存储的令牌在未来的结账中填写他们保存的信用卡信息。

![使用存储的凭据进行将来购买](assets/use-stored-card.png)

他们还可以轻松地从中删除其电子仓库的信用卡 [存储的支付方式](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 在我的账户里。

![我的帐户中存储的付款方法](assets/stored-payment-methods.png)

## 启用保险存储

您可以为客户启用信用卡保险存储 _和_ 管理员中的商家 — 适用于您位于以下位置的商店： [!DNL Payment Services] [设置](settings.md#card-vaulting).

## 在管理员中使用保险存储

如果客户具有以前存储的信用卡，则商家可以使用其存储的付款方法在“管理员”中为该客户创建后续订单。

如果客户同时具有现有帐户，并且系统中存储了来自之前完成付款的有效令牌，则您只能在管理员中使用电子仓库卡。

要在“管理员”中使用客户的保险存储信用卡为其创建订单，请执行以下操作：

1. [创建订单并添加产品](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. In _[!UICONTROL Payment & Shipping Information]_，选择&#x200B;**[!UICONTROL Stored Cards]**作为付款方式。
1. 选择所需的保险存储信用卡支付方式。
1. 完成订单的任何其它必要步骤后， [提交](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![在管理员中为客户使用保险存储信用卡](assets/admin-vaultedcard.png)

## 安全性

与购物者共享的信用卡信息最少；他们只能看到其保险存储信用卡的最后4位数、过期日期和品牌。 信用卡信息将与支付方存储在一起以满足 [PCI](security.md#PCI-compliance) 合规性标准。
