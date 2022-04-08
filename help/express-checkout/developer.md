---
title: '''[!DNL Express Checkout] (针对Adobe Commerce开发人员信息)'
description: '''[!DNL Express Checkout] 开发人员信息。'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 46d5cae4e55a2983a2dc8c442cf5530803be65af
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# [!DNL Express Checkout] 开发人员信息

>[!IMPORTANT]
>
> 该功能仅面向提前采纳者计划(EAP)用户，并且尚未可供所有客户访问。 目前仅限于美国客户。 如需帮助和问题，请联系Adobe Commerce支持。

本主题包含的信息适用于与Adobe Commerce和Magento Open Source代码密切合作，并希望了解有关 [!DNL Express Checkout] 扩展。

## 扩展点

使用扩展点自定义 [!DNL Express Checkout].

通过使用扩展点，您可以进行自定义，而无需实际更改应用程序代码中的核心组件。

## 发运详细信息步骤

使用登录后，可以使用扩展点自定义自动步骤导航 [!DNL Bolt].

购物者登录时使用 [!DNL Bolt]，则会预填所有有效信息，并将其重定向到付款详细信息步骤以下订单。 请参阅 [结账流程](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) 主题以了解更多信息。

此扩展点允许阻止导航到付款步骤，并且当有扩展要求购物者对送货步骤执行其他操作时，此扩展点非常有用。 请参阅下面的示例，了解如何将扩展点与混合使用在一起：

1. 在 `require-config.js` 位于 `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. 在 `can-navigate-to-payment.js` 位于 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> 对于德国(DE)中希望继续执行“送货详细信息”步骤的购物者，此示例为一个示例。

检查 [[!DNL Bolt] 开发人员帮助](https://help.bolt.com/developers/) 有关 [!DNL Bolt] 适用于开发人员。
