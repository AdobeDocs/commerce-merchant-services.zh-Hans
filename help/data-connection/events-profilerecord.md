---
title: 配置文件记录
description: 了解配置文件记录捕获的数据。
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# [!DNL Data Connection] 配置文件记录

以下内容介绍安装Commerce配置文件时可用的记录数据 [!DNL Data Connection] 扩展。 配置文件记录中的数据将发送到Adobe Experience Platform。

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
| `userAccount` | 指示任何忠诚度详细信息、偏好设置、登录流程和其他帐户偏好设置。 |
| `userAccount.startDate` | 首次创建用户档案的日期。 |

>[!NOTE]
>
>每个配置文件记录还包含 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 字段，其中包括购物者的电子邮件地址（如果可用）和ECID。

了解如何 [创建特定于配置文件记录的架构](profile-data.md) 可以从您的个人资料记录中摄取数据。
