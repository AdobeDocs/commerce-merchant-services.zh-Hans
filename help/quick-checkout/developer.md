---
title: '"[!DNL Quick Checkout] (适用于Adobe Commerce开发人员信息)'
description: '"[!DNL Quick Checkout] 开发人员信息。”'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
feature: Checkout, Services
role: Developer
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 开发人员信息

本主题包含面向与Adobe Commerce紧密合作的开发人员的信息，包括 [!DNL Magento Open Source] 代码并想要了解有关 [!DNL Quick Checkout] 扩展。

## 扩展点

使用扩展点自定义 [!DNL Quick Checkout].

通过使用扩展点，您可以进行自定义，而无需实际更改应用程序代码中的核心组件。

## 配送详细资料步骤

扩展点可用于在使用登录后自定义自动步骤导航 [!DNL Bolt].

一旦购物者登录使用 [!DNL Bolt]，则所有有效信息都将预先填写并重定向到支付详情步骤以下订单。 请参阅 [结账流程](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 主题以了解更多信息。

此扩展点允许阻止导航到付款步骤，并且在存在需要购物者对配送步骤执行其他操作的扩展时可能很有用。 请参阅以下示例，了解如何将扩展点与mixin结合使用：

1. 在中注册新的mixin `require-config.js` 文件位于 `app/code/Vendor/ModuleName/view/frontend/`.

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

1. 在中扩展模型 `can-navigate-to-payment.js` 文件位于 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> 这是一个德国购物者(DE)希望停留在“配送详细信息”步骤的示例。

Check [[!DNL Bolt] 开发人员帮助](https://help.bolt.com/developers/) 有关的详细信息 [!DNL Bolt] 适用于开发人员。
