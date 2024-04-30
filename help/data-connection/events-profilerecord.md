---
title: 配置文件记录
description: 了解配置文件记录捕获的数据。
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] 配置文件记录(Beta)

以下介绍了在安装时可用的Commerce配置文件记录数据 [!DNL Data Connection] 扩展。 配置文件记录中的数据将发送到Adobe Experience Platform。

## 个人资料记录

在创建、更新或删除新配置文件时，可在Experience Platform中使用配置文件记录更新。

### 从个人资料记录收集的数据

下面描述了为用户档案记录捕获的数据。

| 字段 | 描述 |
|---|---|
| `channel` | 包含有关数据源的信息。 两者 `_id` 和 `_type` contain [命名空间值](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | 渠道的唯一标识符，如 `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | 标识渠道数据的来源，例如 `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | 包含有关客户的信息。 |
| `person.name` | 包含有关客户名称的信息。 |
| `person.name.firstName` | 包含客户的名字。 |
| `person.name.lastName` | 包含客户的姓氏。 |
| `person.birthDate` | 购物者的出生日期。 |
| `personalEmail` | 个人电子邮件地址。 |
| `personalEmail.address` | 技术地址，例如， `name@domain.com` 如RFC2822和后续标准中通常定义。 |
| `billingAddress` | 帐单邮寄地址。 |
| `billingAddress.street1` | 主要街道级别信息、公寓号、街道号和街道名称。 |
| `billingAddress.street2` | 可选街道信息第二行。 |
| `billingAddress.city` | 城市的名称。 |
| `billingAddress.state` | 省/市/自治区名称。 这是自由格式字段。 |
| `billingAddress.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `billingAddressPhone` | 与帐单地址关联的电话号码。 |
| `billingAddressPhone.number` | 电话号码。 请注意，电话号码是一个字符串，并且可能包含有意义的字符，例如圆括号 `()`，连字符 `-`或字符来指示子拨号标识符，如扩展 `x` 例如，  `1-353(0)18391111` 或 `+613 9403600x1234`. |
| `shippingAddress` | 装运邮政地址。 |
| `shippingAddress.street1` | 主要街道级别信息、公寓号、街道号和街道名称。 |
| `shippingAddress.street2` | 可选街道信息第二行。 |
| `shippingAddress.city` | 城市的名称。 |
| `shippingAddress.state` | 省/市/自治区名称。 这是自由格式字段。 |
| `shippingAddress.country` | 政府管辖地区的名称。 除 `xdm:countryCode`，这是一个自由格式的字段，可以包含任何语言的国家/地区名称。 |
| `shippingAddressPhone` | 与送货地址关联的电话号码。 |
| `shippingAddressPhone.number` | 电话号码。 请注意，电话号码是一个字符串，并且可能包含有意义的字符，例如圆括号 `()`，连字符 `-`或字符来指示子拨号标识符，如扩展 `x` 例如，  `1-353(0)18391111` 或 `+613 9403600x1234`. |
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.startDate` | 首次创建用户档案的日期。 |

>[!NOTE]
>
>每个配置文件记录还包含 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，其中包含系统生成的Commerce客户ID作为用户档案的主要标识符，以及用作次要标识符的电子邮件ID。

了解如何 [创建特定于配置文件记录的架构](profile-data.md) 可以从您的个人资料记录中摄取数据。
