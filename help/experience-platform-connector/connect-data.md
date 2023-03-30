---
title: 将商务数据连接到Adobe Experience Platform
description: 了解如何将您的商务数据连接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform {#connectaep}

要将Adobe Commerce实例连接到Adobe Experience Platform，您必须提供组织ID和数据流ID。

![Experience Platform连接器配置](assets/epc-config-sf.png)

## 常规

1. 登录到您的Adobe帐户(位于 [Commerce Services Connector](../landing/saas.md#organizationid) ，然后选择您的组织ID。

1. 在管理员中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表中，将上下文设置为 **网站**.

1. 在 **组织ID** 字段中，您将看到与Adobe Experience Platform帐户关联的ID，该ID在 [Commerce Services Connector](../landing/saas.md#organizationid). 组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. （可选）如果您已经 [AEP Web SDK（合金）](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署到您的网站后，启用复选框并添加AEP Web SDK的名称。 否则，请将这些字段留空，Experience Platform连接器会为您部署一个字段。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK，Experience Platform连接器将使用与该SDK关联的数据流ID，而不是此页面上指定的数据流ID（如果有）。

## 数据收集

在 **数据收集** 部分，可指定要收集和发送到Experience Platform边缘的数据类型。 默认情况下，只要AEP Web SDK和组织ID有效，就会自动发送店面事件。 请参阅事件主题以了解有关 [店面](events.md#storefront-events) 和 [后台办公室](events.md#back-office-events) 事件。

![Experience Platform连接器配置](assets/epc-config-dc.png)

>[!NOTE]
>
>中的所有字段 **数据收集** 部分 **网站** 范围或更高。

1. 选择 **后台活动** 如果要发送订单状态信息，例如订单已下达、取消、退还或已发运。

   >[!NOTE]
   >
   >默认情况下，所有后台数据都会发送到Experience Platform边缘。 如果购物者选择退出数据收集，则必须在Experience Platform中明确设置购物者的隐私首选项。 这与店面事件不同，在店面事件中，收集者已根据购物者偏好处理同意事件。 [了解更多](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 关于在Experience Platform中设置购物者的隐私首选项。

1. （如果您使用的是自己的AEP Web SDK，请跳过此步骤。） [创建](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的数据流，或选择要用于收集的现有数据流。

1. （如果您使用的是自己的AEP Web SDK，请跳过此步骤。） 在 **数据流ID** 字段中，粘贴该新数据流或现有数据流的ID。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 范围 | 您希望应用配置设置的特定网站。 |
| 组织ID（全局） | 属于购买AdobeDX产品的组织的ID。 此ID可将您的Adobe Commerce实例链接到Adobe Experience Platform。 |
| AEP Web SDK是否已部署到您的站点 | 如果您已将自己的AEP Web SDK部署到您的网站，请选中此复选框 |
| AEP Web SDK名称（全局） | 如果您已经将Experience PlatformWeb SDK部署到您的站点，请在此字段中指定该SDK的名称。 这允许Storefront事件收集器和Storefront事件SDK使用您的Experience PlatformWeb SDK，而不是Experience Platform连接器部署的版本。 如果您尚未将Experience PlatformWeb SDK部署到您的站点，请将此字段留空，Experience Platform连接器将为您部署一个。 |
| 店面事件 | 默认情况下，只要组织ID和数据流ID有效，就会选中此选项。 Storefront事件在购物者浏览您的网站时收集匿名化行为数据。 |
| 后台事件 | 如果选中，则事件有效负载包含匿名化的订单状态信息，例如，订单是否被下达、取消、退还或发运。 |
| 数据流ID（网站） | 允许数据从Adobe Experience Platform流到其他AdobeDX产品的ID。 此ID必须与您特定Adobe Commerce实例中的特定网站关联。 如果您指定自己的Experience PlatformWeb SDK，请不要在此字段中指定数据流ID。 Experience Platform连接器使用与该SDK关联的数据流ID，并忽略此字段中指定的任何数据流ID（如果有）。 |

安装了Experience Platform连接器扩展、创建了Adobe Commerce和Adobe Experience Platform之间的链接，并指定了数据流ID后，商务数据开始流向Adobe Experience Platform边缘和其他AdobeDX产品。

>[!NOTE]
>
> 数据从边缘流向其他AdobeDX产品所花费的时间可能会有所不同。

## 验证数据是否被发送到Experience Platform

将商务数据发送到Adobe Experience Platform边缘时，您可以构建如下报表：

![Adobe Experience Manager中的商务数据](assets/aem-data-1.png)
_Adobe Experience Manager中的商务数据_
