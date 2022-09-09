---
title: 可用数据
description: 使用财务报告数据与非商务系统协调报告。
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 可用数据

您可以获得一些订单和付款数据，以便跨外部系统协调Adobe Commerce财务报告。

## 与ERP系统协调

您可以使用与特定订单关联的增量ID，将Adobe Commerce Financial Reporting与非Adobe企业资源计划(ERP)系统进行协调。

当Payment Services将商务订单发送至PayPal时，递增ID将作为 `custom_id`. 的 `custom_id` 在商户活动详细信息中可看到付款和PayPal Webhook中。

`custom_id` 在商户活动详情的底部，进行付款：

![`custom_id` 在商户活动详细信息中](assets/merchant-activity.png)

`custom_id` 在PayPal的Webhook中，有关细节：

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

有关更多信息，请参阅PayPal的REST API文档：

* [`purchase_unit` 在 `custom_id` 驻留](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit， — 折叠)
* [显示订单详细信息](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
