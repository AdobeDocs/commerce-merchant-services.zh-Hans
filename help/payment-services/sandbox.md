---
title: 设置测试沙盒
description: 使用PayPal沙盒帐户 [!DNL Payment Services] 在测试模式下。
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 设置测试沙盒

在开始沙盒载入之前，您必须注册一个免费的PayPal开发人员帐户，并创建商家（用于载入）和购物者帐户（用于测试结账）。 您可以根据需要创建多个开发人员帐户。

PayPal沙盒帐户允许您使用 [!DNL Payment Services] 在测试模式下。 PayPal要求您使用PayPal开发人员门户生成的商业沙盒测试帐户、电子邮件和密码进行沙盒载入。 *在沙盒载入过程中，请勿创建其他帐户。*

## 沙盒载入

要完成沙盒载入，请执行以下操作：

1. 导航到 [PayPal开发人员帐户页面](https://developer.paypal.com/developer/accounts/).
1. 单击 **[!UICONTROL Log in to Dashboard]** 并使用您现有的PayPal开发人员门户生成的商业沙盒测试帐户登录，或单击 **注册** 创建帐户。
1. 创建PayPal沙盒帐户：
   1. 转到 _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. 单击 **[!UICONTROL Create account]**.

      如果您在沙盒PayPal载入过程中创建了一个PayPal沙盒帐户，则必须 [重置载入沙盒](#reset-your-sandbox-account) 因为或您无法验证电子邮件。

   1. 选择 **[!UICONTROL Business]** 作为“帐户类型”，然后单击 **[!UICONTROL Create]**.
   1. 在 _[!UICONTROL Sandbox Accounts]_中，单击_[!UICONTROL Manage accounts]_ 列。
   1. 单击 **[!UICONTROL View/edit account]**.

      ![PayPal — 查看/编辑沙盒帐户](assets/onboarding-viewedit-sandbox.png)

   1. 复制并保存电子邮件ID和系统生成的密码，供将来使用。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Sandbox onboarding]**.

   如果尚未完成的沙盒载入，则会显示此选项 [!DNL Payment Services].

   沙盒商户ID是自动生成并填充到 [设置](settings.md). 请勿更改或更改此ID。

   您将看到一个PayPal窗口，用于连接PayPal帐户以开始接受付款。

1. 输入您在步骤3中生成的PayPal沙盒帐户（而非您的PayPal业务帐户信息）以及您所在国家或地区的电子邮件和密码。
1. 单击 **[!UICONTROL Next]**.

   ![PayPal — 用于支付的Connect PayPal帐户](assets/paypal-connectacct.png)

1. 使用您之前保存的沙盒帐户凭据，继续遵循PayPal流程。
1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   的 **[!UICONTROL Sandbox onboarding]** 按钮将不再可见，并且您会看到“沙盒付款待决”文本。

当您的PayPal沙盒载入获得批准后，您应会看到一则通知，指出您的支付系统当前处于沙盒模式，且不处理实时支付。

>[!IMPORTANT]
>
>如果您撤消对 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 处理付款时（在您的PayPal帐户设置中），您商店中的订单无法由 [!DNL Payment Services]. 在您的Payment Services主页上，会显示有关已吊销同意的警报。 要关闭警报，请单击 **[!UICONTROL Do not show again]**.

### 重置沙盒帐户

如果您在沙盒PayPal载入过程中创建了一个PayPal沙盒帐户，则必须重置载入沙盒，因为或者您无法验证电子邮件。

要重置沙盒帐户，请执行以下操作：

1. 单击 **[!UICONTROL Reset sandbox]**. [创建PayPal业务沙盒帐户](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. 单击 **[!UICONTROL Sandbox onboarding]** 并完成下一组步骤。

## 启用联系电话号码

联系电话号码允许您获取PayPal从您的客户那里收集的联系电话号码。 PayPal始终从PayPal帐户持有者那里收集联系电话，以帮助确认其身份并联系他们以解决帐户问题或完成其履行流程。 但是，PayPal不建议直接从商家使用联系电话号码，因为这可能对销售产生负面影响。 请参阅 [PayPal获取联系电话号码](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) 文档以了解更多信息。

此功能为 `off` 默认情况下。 启用该功能后，当客户在结帐页面外完成品牌结帐流程时，商店管理员可以看到电话号码。

>[!IMPORTANT]
>
>此设置不适用于其他结帐流。

## 在沙盒环境中测试

请参阅 [测试和验证](test-validate.md) 以了解更多信息。
