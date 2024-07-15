---
title: 空洞
description: 通过撤消，您可以释放信用卡或借记卡账户中的资金，该账户已通过授权被阻止或保留，金额为购买金额。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# 空洞

通过[!DNL Payment Services]，您可以使用现有的Commerce功能使事务失效。 通过撤消，您可以释放信用卡或借记卡账户中的资金，该账户已通过授权被阻止或保留，金额为购买金额。

>[!NOTE]
>
>只有在尚未获取付款的情况下，您才能撤消事务处理。

如果您的商店[配置为](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"}，则在销售点仅授权（不捕获）资金，则从您的商店购买会导致订单在Commerce管理中具有`Processing`状态。

您也可以[取消未开票的订单](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"}。 作为取消过程的一部分，任何未捕获的授权也会失效。

>[!NOTE]
>
>取消订单也会产生作废，但撤消订单不会触发取消。

要了解有关订单所经历的基本步骤的更多信息，请参阅核心用户指南中的[订单工作流](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"}主题。

要了解void功能以及如何使订单交易无效，请参阅核心用户指南中的[处理订单](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"}。
