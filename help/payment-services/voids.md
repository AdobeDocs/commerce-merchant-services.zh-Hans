---
title: 空隙
description: 通过空格，您可以释放信用卡或借记卡帐户中的资金，这些资金被阻止或被授权存放以购买金额。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 空隙

使用 [!DNL Payment Services]，则可以使用现有商务功能来撤消事务。 通过空格，您可以释放信用卡或借记卡帐户中的资金，这些资金被阻止或被授权存放以购买金额。

>[!NOTE]
>
>只有在尚未捕获付款时，才能撤消事务处理。

如果您的商店是 [已配置](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;}仅授权（而非捕获）销售点的资金，从您的商店购买会导致订购 `Processing` 状态。

您还可以 [取消订单](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order)未开票的{target=&quot;_blank&quot;}。 任何未捕获的授权也作为取消过程的一部分被撤消。

>[!NOTE]
>
>取消订单也会产生撤消，但撤消订单不会触发取消。

要详细了解订单执行的基本步骤，请参阅 [订单工作流](https://docs.magento.com/user-guide/sales/order-workflow.html)核心用户指南中的{target=&quot;_blank&quot;}主题。

要了解撤消功能以及如何撤消订单交易，请参阅 [处理订单](https://docs.magento.com/user-guide/sales/order-processing.html)核心用户指南中的{target=&quot;_blank&quot;}。
