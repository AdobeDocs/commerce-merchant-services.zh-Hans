---
title: 退款
description: 为 [!DNL Payment Services] 在贷项通知单流程中对管理员中的订单执行操作。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 退款

退款 [!DNL Payment Services] 在“管理员”中创建订单，作为贷项通知单流程的一部分。 贷项通知单是一份单据，用于显示应付给客户的全额或部分退款金额，这些退款可用于购买或直接退还给客户。 贷项通知单只能为 [已开票](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}。

请参阅 [贷项通知单](https://docs.magento.com/user-guide/sales/credit-memos.html)我们的核心用户指南中的{target=&quot;_blank&quot;}，以了解更多信息以及如何签发和打印贷项通知单。

对于通过PayPal或信用卡处理的订单，您可以：

* 退还订单的全部金额
* 退回部分订单金额（或多个部分金额）
* 退款金额小于特定订单项目的价值

请参阅 [发出贷项通知单](https://docs.magento.com/user-guide/sales/credit-memo-create.html)有关详细信息，请参阅核心用户指南中的{target=&quot;_blank&quot;}。

>[!NOTE]
>
>如果您尝试为订单部分退款的金额超过剩余订单金额（原始金额减去现有退款总额），或者您为金额大于完整订单金额的金额发出退款，则PayPal或信用卡处理订单会出错。

的 [!UICONTROL Payment Action] 在 [!UICONTROL Payment Settings] 配置 —  `Authorize` 或 `Authorize and Capture` — 确定 [基本退款工作流](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target=&quot;_blank&quot;}。

请参阅 [付款活动设置部分](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;}，共 _发出贷项通知单_ 以了解更多信息。
