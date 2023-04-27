---
title: 将商务数据连接到Adobe Experience Platform
description: 了解如何将您的商务数据连接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform

安装Experience Platform连接器时， **系统** 菜单下 **服务** 在商务中 _管理员_.

- Commerce Services Connector
- Experience Platform连接器

要将Adobe Commerce实例连接到Adobe Experience Platform，您必须配置两个连接器，从Commerce Services连接器开始，然后使用Experience Platform连接器完成。

## 更新Commerce Services连接器

如果您之前安装了Adobe Commerce服务，则可能已配置了Commerce Services连接器。 如果没有，则必须在 [Commerce Services连接器](../landing/saas.md) 页面：

1. 登录到您的Commerce帐户以 [检索生产和沙盒API密钥](../landing/saas.md#credentials).
1. 选择 [SaaS数据空间](../landing/saas.md#saas-configuration).
1. 登录到您的Adobe帐户以 [检索您的组织ID](../landing/saas.md#ims-organization-optional).

配置Commerce Services连接器后，即可配置Experience Platform连接器。

## 更新Experience Platform连接器

在此部分中，您可以使用您的组织ID将Adobe Commerce实例连接到Adobe Experience Platform。 然后，您可以指定要发送到Experience Platform边缘的数据类型（存储前端或后台）。

![Experience Platform连接器配置](assets/epc-config-dc.png)

## 常规

1. 登录到您的Adobe帐户(位于 [Commerce Services Connector](../landing/saas.md#organizationid) ，然后选择您的组织ID。

   >[!NOTE]
   >
   >如果您之前配置了Commerce Services连接器，则可以跳过此步骤，因为您的组织ID已被选择。

1. 在管理员中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表中，将上下文设置为 **网站**.

1. 在 **组织ID** 字段中，根据 [Commerce Services Connector](../landing/saas.md#organizationid). 组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. （可选）如果您已经 [AEP Web SDK（合金）](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署到您的网站后，启用复选框并添加AEP Web SDK的名称。 否则，请将这些字段留空，Experience Platform连接器会为您部署一个字段。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK，Experience Platform连接器将使用与该SDK关联的数据流ID，而不是此页面上指定的数据流ID（如果有）。

## 数据收集

在 **数据收集** 部分，选择要发送到Experience Platform边缘的storefront和/或back office data。 要确保Adobe Commerce实例可以开始数据收集，请查看 [先决条件](overview.md#prerequisites).

请参阅事件主题以了解有关 [店面](events.md#storefront-events) 和 [后台办公室](events.md#back-office-events) 事件。

>[!NOTE]
>
>中的所有字段 **数据收集** 部分 **网站** 范围或更高。

1. 选择 **店面事件** 要发送店面行为数据。

   >[!NOTE]
   >
   >的 **店面事件** 复选框会在AEP Web SDK和组织ID有效时自动启用。

1. 选择 **后台活动** 如果要发送订单状态信息，例如订单已下达、取消、退还或已发运。

   >[!NOTE]
   >
   >如果您选择 **后台活动**，则所有后台数据都会发送到Experience Platform边缘。 如果购物者选择退出数据收集，则必须在Experience Platform中明确设置购物者的隐私首选项。 这与店面事件不同，在店面事件中，收集者已根据购物者偏好处理同意事件。 [了解更多](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 关于在Experience Platform中设置购物者的隐私首选项。

1. 确保后台事件数据根据 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 工作，你必须改变 `Sales Orders Feed` 索引到 `Update by Schedule`.

   1. 在 _管理员_ 侧栏，转到 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 选中 `Sales Orders Feed` 索引器。

   1. 已设置 **[!UICONTROL Actions]** to `Update by Schedule`.

   1. 如果您是首次启用后台数据，请运行以下命令以重新编入索引并触发重新同步。 只要 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 作业设置正确。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

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

## 验证数据是否被发送到Experience Platform

入门后，店面数据开始流向Experience Platform边缘。 后台数据在载入后大约需要5分钟才能显示在边缘。 随后的更新将根据cron计划显示在边缘。

将商务数据发送到Experience Platform边缘时，您可以构建如下报表：

![Adobe Experience Platform中的商务数据](assets/aem-data-1.png)
_Adobe Experience Platform中的商务数据_
