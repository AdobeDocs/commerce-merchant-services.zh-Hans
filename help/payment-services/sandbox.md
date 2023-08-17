---
title: 设置测试沙盒
description: 使用PayPal沙盒帐户以使用 [!DNL Payment Services] 处于测试模式。
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# 设置测试沙盒

在开始沙盒载入之前，您必须注册一个免费的PayPal开发人员帐户，并创建商家（用于入门）和购物者帐户（用于测试您的结帐）。 如果需要，您可以创建多个开发人员帐户。

PayPal沙盒帐户允许您使用 [!DNL Payment Services] 处于测试模式。 PayPal要求您使用PayPal Developer Portal生成的业务沙盒测试帐户、电子邮件和密码进行沙盒载入。 *在沙盒载入过程中不要创建其他帐户。*

## 沙盒载入

要完成沙盒载入，请执行以下操作：

1. 导航至 [PayPal开发人员帐户页面](https://developer.paypal.com/developer/accounts/).
1. 单击 **[!UICONTROL Log in to Dashboard]** 并使用您现有的PayPal开发人员门户生成的业务沙盒测试帐户登录，或单击 **注册** 以创建帐户。
1. 创建PayPal沙盒帐户：
   1. 转到 _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. 单击 **[!UICONTROL Create account]**.

      如果您在沙盒PayPal载入过程中创建了PayPal沙盒帐户，则必须 [重置载入沙盒](#reset-your-sandbox-account) 因为或者您无法验证电子邮件。

   1. 选择 **[!UICONTROL Business]** 作为帐户类型，然后单击 **[!UICONTROL Create]**.
   1. 在 _[!UICONTROL Sandbox Accounts]_部分中，单击_[!UICONTROL Manage accounts]_ 您创建的沙盒帐户的列。
   1. 单击 **[!UICONTROL View/edit account]**.

      ![PayPal — 查看/编辑沙盒帐户](assets/onboarding-viewedit-sandbox.png)

   1. 复制并保存电子邮件ID和系统生成的密码以供将来使用。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 单击 **[!UICONTROL Sandbox onboarding]**.

   如果您尚未完成的沙盒载入，则可以看到此选项 [!DNL Payment Services].

   沙盒商家ID会自动生成并填充到 [设置](settings.md). 请勿更改或更改此ID。

   您会看到一个PayPal窗口，用于连接PayPal帐户以开始接受付款。

1. 输入您在步骤3中生成的PayPal沙盒帐户的电子邮件和密码（不是您的PayPal商业帐户信息）以及您所在国家或地区。
1. 单击 **[!UICONTROL Next]**.

   ![PayPal — 连接PayPal帐户以进行支付](assets/paypal-connectacct.png)

1. 使用您之前保存的沙盒帐户凭据继续遵循PayPal流程。
1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   此 **[!UICONTROL Sandbox onboarding]** 按钮不再可见，并且您看到“沙盒支付待处理”文本。

当您的PayPal沙盒载入获得批准时，您应该看到一条通知，表明您的支付系统当前处于沙盒模式并且不处理实时支付。

>[!IMPORTANT]
>
>如果您撤销对 [!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 为了处理您的付款（在您的PayPal帐户设置中），您商店中的订单不能由处理 [!DNL Payment Services]. 在您的Payment Services主页上，会显示有关撤销同意的警报。 要解除警报，请单击 **[!UICONTROL Do not show again]**.

### 重置沙盒帐户

如果您在沙盒PayPal新用户引导过程中创建了PayPal沙盒帐户，则必须重置新用户引导沙盒，因为或者您无法验证电子邮件。

要重置沙盒帐户：

1. 单击 **[!UICONTROL Reset sandbox]**. [创建PayPal商业沙盒帐户](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. 单击 **[!UICONTROL Sandbox onboarding]** 并完成下一组步骤。

## 启用联系人电话号码

联系电话号码允许您获取PayPal从客户那里收集的联系电话号码。 PayPal始终从PayPal帐户持有人那里收集联系电话号码，以帮助确认其身份并联系他们以解决其帐户上的问题或完成其履行流程。 但是，PayPal不鼓励直接从商家使用联系电话号码，因为它可能会对销售产生负面影响。 请参阅 [PayPal获取联系电话号码](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) 文档，以了解更多信息。

此功能是 `off` 默认情况下。 启用后，当客户在结账页面之外完成品牌认证结账流程时，商店管理员可以看到电话号码。

>[!IMPORTANT]
>
>此设置不适用于其他签出流。

## 在沙盒环境中测试

请参阅 [测试和验证](test-validate.md) 以了解更多信息。
