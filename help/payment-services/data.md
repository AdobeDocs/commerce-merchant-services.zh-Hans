---
title: 可用数据
description: 使用财务报告数据与非商务系统协调报告。
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 可用数据

您可以获得一些订单和付款数据，以便跨外部系统协调Adobe Commerce财务报告。

## 与ERP系统协调

您可以使用与特定订单关联的增量ID，将Adobe Commerce Financial Reporting与非Adobe企业资源计划(ERP)系统进行协调。

当Payment Services将商务订单发送至PayPal时，递增ID将作为 `custom_id` _和_ 在 `invoice_id` (其中还包含一个随机字符串 `increment_id`)。

ID在商家活动细节中和在PayPal网络挂接中都容易访问。

的 `invoice_id` 和 `custom_id` 显示在商家活动详细信息底部附近，用于支付：

![`custom_id` 在商户活动详细信息中](assets/merchant-activity-ids.png)

`custom_id` 和 `invoice_id` 在PayPal的Webhook中，有关细节：

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

* [`purchase_unit`，其中 `custom_id` 和 `invoice_id` resid](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit， — 折叠)
* [显示订单详细信息](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
