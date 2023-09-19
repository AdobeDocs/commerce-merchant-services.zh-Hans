---
title: 测试和验证
description: 测试和验证有助于确保 [!DNL Payment Services] 功能按预期工作，并为客户提供最佳支付选项
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 测试和验证

在你公开之前 [!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 对于您的购物者，最好在沙盒环境中进行测试 _和_ 正在生产。 测试和验证有助于确保 [!DNL Payment Services] 功能按预期工作，并为您的商店和客户提供最佳支付选项。

## 在沙盒环境中测试

测试 [!DNL Payment Services] 在沙盒环境中是一个重要的验证步骤，即使它是一个仅连接到PayPal沙盒而非真实银行和商家的模拟环境。

1. 使用以下任一方式从您的商店成功结帐： [信用卡字段](payments-options.md#credit-card-fields) 或任何 [PayPal智能按钮](payments-options.md#paypal-smart-buttons). 请参阅 [测试凭据](#testing-credentials) 了解更多有关使用假信用卡进行测试的信息。
1. 捕获(当您的付款活动为 [设置为 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method))， [退款](refunds.md)，或 [空白](voids.md) 刚刚完成的订单。 您也可以 [创建发票](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 对于订单，如果您的付款活动设置为 `Authorize` 而不是 `Authorize and Capture`.
1. 在24-48小时内，查看以下文件中的交易和其它信息： [支付报表](payouts.md).
1. 欲知订单详情，请参见 [订单付款状态报表](order-payment-status.md).

### 测试凭据

在测试和验证沙盒时，您必须使用虚假信用卡号，这样您就不会对现有信用卡帐户产生真正的费用。

使用PayPal的信用卡生成器 [生成随机信用卡信息](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 以进行测试。

要在沙盒模式下测试Apple Pay，请执行以下操作：

* 创建 [Apple沙盒测试程序帐户](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)，并提供虚假信用卡和账单信息。
* [注册沙盒域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal的沙盒支付处理有时很慢，该服务偶尔可能会停用。 这种情况不能表明实时产品支付处理的速度和效率。

## 在生产环境中测试

强烈建议您测试 [!DNL Payment Services] 在投入生产之前，使用真正的信用卡和银行，然后将此功能公开给购物者。 即使测试 [!DNL Payment Services] 在沙盒中测试很重要，在生产环境中测试是确保 [!DNL Payment Services] 按预期工作。

您可以测试 [!DNL Payment Services] 在生产环境中，可通过以下两种方式之一：

* 选择您知道购物者不会下订单的时间。
* 使用购物者暂时无法访问但可供您访问以进行测试的网络商店。

使用真实的信用卡和PayPal帐户完成您的生产测试，测试付款的整个生命周期，包括捕获和退款。 在测试期间完成整个结账和支付流程，可让您清楚地了解 [!DNL Payment Services] 功能将在实时购物者使用它时正常工作。

您还应该验证银行对帐单上显示的用于生产测试的支付方式的信息是否正确和符合预期（包括业务描述）。

要在生产模式下测试Apple Pay，您必须 [注册生产域](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
