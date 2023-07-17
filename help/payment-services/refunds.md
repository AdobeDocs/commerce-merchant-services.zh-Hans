---
title: 退款
description: 创建退款 [!DNL Payment Services] 管理中的订单，作为贷项通知单流程的一部分。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# 退款

退款 [!DNL Payment Services] 订单是在管理员中创建的，作为贷项通知单流程的一部分。 贷项通知单是一种文档，它显示应向客户支付的全部或部分退款的金额，可用于购买或直接向客户退款。 只能为以下订单发放贷项通知单： [已开发票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

参见 [贷项通知单](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} 请参阅我们的核心用户指南，以获取更多信息并了解如何发放和打印贷项通知单。

对于使用PayPal或信用卡处理的订单，您可以：

* 退回订单的全部金额
* 退回订单的部分金额（或多个部分金额）
* 退款金额小于特定订单项目的值

参见 [发放贷项通知单](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} ，以了解更多信息。

>[!NOTE]
>
>如果您尝试对超过剩余订单金额（原始金额减去现有退款总额）的订单进行部分退款，或者如果您发出的退款金额大于全部订单金额，则PayPal或信用卡处理的订单会发生错误。

此 [!UICONTROL Payment Action] 在中设置 [!UICONTROL Payment Settings] 配置 —  `Authorize` 或 `Authorize and Capture` — 确定 [基本退款工作流](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} 订购单。

请参阅 [付款活动设置部分](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} 之 _发放贷项通知单_ 了解更多信息。
