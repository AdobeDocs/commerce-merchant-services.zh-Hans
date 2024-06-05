---
title: 可用数据
description: 使用Financial Reporting数据协调报表与非Commerce系统。
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
feature: Payments, Checkout, Data Import/Export
source-git-commit: 9a933d41bffc2af453eed00caeb941eb18b23852
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 可用数据

您可以获得一些订单和付款数据，以便跨外部系统协调Adobe Commerce Financial Reporting。

## 与ERP系统协调

您可以使用与特定订单关联的增量ID来调整Adobe Commerce Financial Reporting与非Adobe企业资源计划(ERP)系统。

当支付服务将Commerce订单发送至PayPal时，增量ID包含为 `custom_id` _和_ 在 `invoice_id` (也包含随机字符串，位于 `increment_id`)。

在付款的商家活动详细信息和PayPal webhook中均可轻松访问ID。

此 `invoice_id` 和 `custom_id` 显示在付款的商家活动详细信息底部附近：

![`custom_id` 在商家活动详细信息中](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` 和 `invoice_id` 详情请见PayPal的webhook：

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

有关更多信息，请参阅PayPal的REST API文档：

* [`purchase_unit`，其中 `custom_id` 和 `invoice_id` 驻留](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit)
* [显示订单详细信息](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
