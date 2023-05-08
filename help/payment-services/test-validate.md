---
title: 测试和验证
description: 测试和验证有助于确保 [!DNL Payment Services] 功能可按预期工作，并为客户提供最佳付款选项
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 0324c2d8e34fee0872d5f52ed3a246094b482aa2
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 测试和验证

在公开之前 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 对于购物者而言，最好在沙盒环境中进行测试 _和_ 在生产中。 测试和验证有助于确保 [!DNL Payment Services] 功能可按预期工作，为您的商店和客户提供最佳付款选项。

## 在沙盒环境中测试

测试 [!DNL Payment Services] 沙盒环境中是一个重要的验证步骤，尽管它是仅与PayPal沙盒连接的模拟环境，而不是与真实银行和商户连接。

1. 通过 [信用卡字段](payments-options.md#credit-card-fields) 或 [PayPal智能按钮](payments-options.md#paypal-smart-buttons). 请参阅 [测试凭据](#testing-credentials) 有关使用假信用卡进行测试的更多信息。
1. 捕获(当您的付款操作为 [设置为 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method))、 [退款](refunds.md)或 [void](voids.md) 刚刚完成的订单。 您还可以 [创建发票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 如果您的付款活动设置为 `Authorize` 而不是 `Authorize and Capture`.
1. 在24-48小时内，查看 [派息报告](payouts.md).
1. 请参阅 [订单付款状态报表](order-payment-status.md).

### 测试凭据

在测试和验证沙盒时，您必须使用假信用卡号，这样您就不会对现有信用卡帐户产生实际费用。

使用PayPal的信用卡生成器 [生成随机信用卡信息](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 用于测试。

要在沙盒模式下测试Apple Pay，请执行以下操作：

* 创建 [Apple沙盒测试员帐户](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)，以及假信用卡和账单信息。
* [注册沙盒域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal的沙盒支付处理有时会很慢，服务有时可能会停止。 这种情况并不表示实时产品支付处理的速度和效率。

## 在生产中测试

强烈建议您测试 [!DNL Payment Services] 在生产中，使用真实信用卡和银行，然后向购物者公开此功能。 即使测试 [!DNL Payment Services] 在沙盒中测试很重要，在生产中测试是确保 [!DNL Payment Services] 工作正常。

您可以测试 [!DNL Payment Services] 在生产中采用两种方式之一：

* 选择您知道购物者不会下订单的时间。
* 使用网店，该商店暂时无法访问购物者，但您可以访问该网店进行测试。

使用真实信用卡和PayPal帐户完成生产测试，测试付款的整个生命周期，包括捕获和退款。 在测试期间完成整个结账和付款流程，可以最清晰地了解您的 [!DNL Payment Services] 实时购物者使用此功能时，该功能将起作用。

您还应验证在银行对帐单中显示的有关您在生产测试中使用的付款方法的信息是否正确且符合预期（包括业务说明）。

要在生产模式下测试Apple Pay，您必须 [注册生产域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
