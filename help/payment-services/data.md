---
title: 可用数据
description: 使用财务报表数据使报表与非商务系统相协调。
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 可用数据

您可以获得一些订单和付款数据，以便协调外部系统之间的Adobe Commerce Financial Reporting。

## 与ERP系统协调

您可以使用与特定订单关联的增量ID来调节Adobe Commerce Financial Reporting与非AdobeEnterprise Resource Planning (ERP)系统。

当支付服务将商业订单发送至PayPal时，增量ID被包含为 `custom_id` _和_ 在 `invoice_id` (其中还包含 `increment_id`)。

在付款的商家活动详细信息和PayPal webhook中均可轻松访问ID。

此 `invoice_id` 和 `custom_id` 在付款的商家活动详细信息底部附近显示：

![`custom_id` 在商家活动详细信息中](assets/merchant-activity-ids.png)

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

* [`purchase_unit`，其中 `custom_id` 和 `invoice_id` 驻留](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-，purchase_unit， — 折叠)
* [显示订单详细信息](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
