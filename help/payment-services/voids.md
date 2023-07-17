---
title: 空洞
description: 通过撤消，您可以释放信用卡或借记卡帐户中的资金，这些帐户已被阻止或根据授权保留在购买金额中。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# 空洞

替换为 [!DNL Payment Services]，则可以使用现有Commerce功能使交易失效。 通过撤消，您可以释放信用卡或借记卡帐户中的资金，这些帐户已被阻止或根据授权保留在购买金额中。

>[!NOTE]
>
>只有在尚未获取付款的情况下，您才能撤消事务处理。

如果您的商店为 [已配置](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 要在销售点仅授权（而不是捕获）资金，从您的商店购买会导致订单包含 `Processing` 商务管理员中的状态。

您还可以 [取消订单](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} 未开具发票。 在该取消过程中，任何未捕获的授权也会失效。

>[!NOTE]
>
>取消订单也会产生作废，但撤消订单不会触发取消。

要了解有关订单所经历的基本步骤的更多信息，请参阅 [订单工作流](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} 主题。

要了解撤消功能以及如何撤消订单事务处理，请参阅 [处理订单](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} （在核心用户指南中）。
