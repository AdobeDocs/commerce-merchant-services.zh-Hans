---
title: 将Commerce数据连接到Adobe Experience Platform
description: 了解如何将Commerce数据连接到Adobe Experience Platform。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# 将Commerce数据连接到Adobe Experience Platform

安装Experience Platform连接器时， **系统** 下的菜单 **服务** 在商业中 _管理员_.

- 商务服务连接器
- Experience Platform连接器

要将Adobe Commerce实例连接到Adobe Experience Platform，您必须配置这两个连接器，从Commerce Services连接器开始，然后使用Experience Platform连接器完成。

## 更新Commerce服务连接器

如果您以前安装过Adobe Commerce服务，则您可能已经配置了Commerce Services连接器。 如果没有，则必须在 [商务服务连接器](../landing/saas.md) 页面：

1. 登录到您的Commerce帐户以 [检索您的生产和沙盒API密钥](../landing/saas.md#credentials).
1. 选择 [SaaS数据空间](../landing/saas.md#saas-configuration).
1. 登录到您的Adobe帐户以 [检索您的组织ID](../landing/saas.md#ims-organization-optional).

配置Commerce Services连接器后，再配置Experience Platform连接器。

## 更新Experience Platform连接器

在本节中，您将使用组织ID将Adobe Commerce实例连接到Adobe Experience Platform。 然后，您可以指定要发送到Experience Platform边缘的数据类型（店面或后台）。

![Experience Platform连接器配置](assets/epc-config-dc.png)

## 常规

1. 在中登录到您的Adobe帐户 [商务服务连接器](../landing/saas.md#organizationid) 并选择您的组织ID。

   >[!NOTE]
   >
   >如果您之前配置了Commerce Services连接器，则可以跳过此步骤，因为已选择您的组织ID。

1. 在“管理员”中，转到 **系统** >服务> **Experience Platform连接器**.

1. 在 **范围** 下拉列表，将上下文设置为 **网站**.

1. 在 **组织ID** 字段中，验证与您的Adobe Experience Platform帐户关联的ID，如中配置 [商务服务连接器](../landing/saas.md#organizationid). 组织ID是全局的。 每个Adobe Commerce实例只能关联一个组织ID。

1. （可选）如果您已经拥有 [AEP Web SDK（合金）](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 部署到您的站点时，启用复选框并添加AEP Web SDK的名称。 否则，请将这些字段留空，Experience Platform连接器将为您部署一个字段。

   >[!NOTE]
   >
   >如果您指定自己的AEP Web SDK，Experience Platform连接器将使用与该SDK关联的数据流ID，而不是此页中指定的数据流ID（如果有）。

## 数据收集

在此部分中，您可以指定要发送到Experience Platform边缘的数据类型。 有两种类型的数据：客户端和服务器端。

客户端数据是在店面中捕获的数据。 这包括购物者交互，例如 `View Page`， `View Product`， `Add to Cart`、和 [申请列表](events.md#b2b-events) 信息（对于B2B商家）。 服务器端数据（或后台数据）是在Commerce服务器中捕获的数据。 这包括有关订单状态的信息，例如订单是否已下达、取消、退款、已发运或已完成。

在 **数据收集** 部分，选择要发送到Experience Platform边缘的数据类型。 要确保Adobe Commerce实例可以开始数据收集，请查看 [先决条件](overview.md#prerequisites).

请参阅事件主题以了解有关 [店面](events.md#storefront-events) 和 [后台](events.md#back-office-events) 事件。

>[!NOTE]
>
>中的所有字段 **数据收集** 部分适用于 **网站** 范围或更高。

1. 选择 **店面活动** 如果您要发送店面行为数据。

   >[!NOTE]
   >
   >此 **店面活动** 如果AEP Web SDK和组织ID有效，则会自动启用此复选框。

1. 选择 **后台活动** 如果您要发送订单状态信息（例如，订单是否已下达、取消、已退款或已发运）。

   >[!NOTE]
   >
   >如果您选择 **后台活动**，则所有后台数据都会发送到Experience Platform边缘。 如果购物者选择退出数据收集，您必须在Experience Platform中明确设置购物者的隐私偏好设置。 这与店面事件不同，店面事件收集器已根据购物者的偏好处理同意。 [了解详情](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) 关于在Experience Platform中设置购物者的隐私首选项。

1. 确保后台事件数据根据计划更新 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 作业，您必须更改 `Sales Orders Feed` 索引目标 `Update by Schedule`.

   1. 在 _管理员_ 侧栏，转到 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 选中复选框 `Sales Orders Feed` 索引器。

   1. 设置 **[!UICONTROL Actions]** 到 `Update by Schedule`.

   1. 如果您是首次启用后台数据，请运行以下命令来重新索引并触发重新同步。 后续的重新同步只要 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 作业设置正确。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. （如果您使用自己的AEP Web SDK，请跳过此步骤。） [创建](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform中的数据流，或者选择要用于收集的现有数据流。

1. （如果您使用自己的AEP Web SDK，请跳过此步骤。） 在 **数据流ID** 字段中，粘贴新数据流或现有数据流的ID。

## 字段描述

| 字段 | 描述 |
|--- |--- |
| 范围 | 您希望应用配置设置的特定网站。 |
| 组织ID（全局） | 属于购买AdobeDX产品的组织的ID。 此ID可将您的Adobe Commerce实例链接到Adobe Experience Platform。 |
| AEP Web SDK是否已部署到您的站点 | 如果您已将自己的AEP Web SDK部署到站点，请选中此复选框 |
| AEP Web SDK名称（全局） | 如果您已将一个Experience PlatformWeb SDK部署到站点，请在此字段中指定该SDK的名称。 这允许Storefront事件收集器和店面事件SDK使用您的Experience PlatformWeb SDK，而不是Experience Platform连接器部署的版本。 如果您没有将Experience PlatformWeb SDK部署到网站，请将此字段留空，Experience Platform连接器会为您部署一个。 |
| 店面活动 | 只要组织ID和数据流ID有效，就会默认选中。 店面活动在购物者浏览您的网站时收集他们的匿名行为数据。 |
| 后台活动 | 如果选中，则事件有效负荷包含匿名的订单状态信息，例如订单是否已下达、取消、退款或装运。 |
| 数据流ID（网站） | 允许数据从Adobe Experience Platform流向其他AdobeDX产品的ID。 此ID必须关联到您的特定Adobe Commerce实例中的特定网站。 如果您指定自己的Experience PlatformWeb SDK，请不要在此字段中指定数据流ID。 Experience Platform连接器使用与该SDK关联的数据流ID，并忽略此字段中指定的任何数据流ID（如果有）。 |

>[!NOTE]
>
>上线后，店面数据开始流入Experience Platform边缘。 后台数据需要大约5分钟才能显示在边缘。 根据cron计划，后续更新在Edge上可见。

## 确认已收集事件数据

要确认正在从Commerce商店收集数据，请使用 [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 检查您的Commerce网站。 确认正在收集数据后，您可以通过运行查询来验证您的店面和后台事件数据是否显示在边缘，该查询会从返回数据。 [您创建的数据集](overview.md#prerequisites).

1. 选择 **查询** 在Experience Platform的左侧导航中，然后单击 [!UICONTROL Create Query].

   ![查询编辑器](assets/query-editor.png)

1. 打开查询编辑器后，输入从数据集中选择数据的查询。

   ![创建查询](assets/create-query.png)

   例如，您的查询可能如下所示：

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 查询运行后，结果将显示在 **结果** 选项卡，在 **控制台** 选项卡。 此视图显示查询的表格输出。

   ![查询编辑器](assets/query-results.png)

在此示例中，您会看到以下源自 [`commerce.productListAdds`](events.md#addtocart)， [`commerce.productViews`](events.md#productpageview)， [`web.webpagedetails.pageViews`](events.md#pageview)，等等。 利用此视图，可验证您的Commerce数据是否已到达边缘。

如果结果不符合预期，请打开数据集并查找任何失败的批次导入。 详细了解 [批量导入疑难解答](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
