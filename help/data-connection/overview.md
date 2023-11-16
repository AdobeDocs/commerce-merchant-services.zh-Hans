---
title: 指南概述
description: 了解如何使用将Adobe Commerce数据与Adobe Experience Platform集成 [!DNL Data Connection] 扩展。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# [!DNL Data Connection] 概述

>[!IMPORTANT]
>
>Experience Platform连接器已重命名为 [!DNL Data Connection].

此 [!DNL Data Connection] 扩展允许Adobe Commerce商家发送 [店面](events.md#storefront-events) 和 [后台](events.md#back-office-events) 将数据发送到Adobe Experience Platform Edge，以便其他Adobe Experience Cloud产品(如Adobe Analytics和Adobe Journey Optimizer)可以使用该Commerce数据。 通过将Commerce数据连接到Adobe Experience Cloud中的其他产品，您可以执行分析网站上的用户行为、执行AB测试以及创建个性化营销活动等任务。

[店面活动](events.md#storefront-events) 捕获购物者交互，例如 `View Page`， `View Product`， `Add to Cart`、和 [申请列表](events.md#b2b-events) 信息（对于B2B商家）。 [后台](events.md#back-office-events) 事件会捕获有关订单状态的信息，例如，订单是否已下达、已取消、已退款、已发运或已完成。 捕获的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都经过严格匿名处理。 [了解详情](https://www.adobe.com/privacy/experience-cloud.html).

此 [!DNL Data Connection] 扩展显示在Commerce管理员的下 **系统** >服务> **[!DNL Data Connection]**.

![[!DNL Data Connection] 扩展管理员视图](assets/epc-adminui.png)

## 先决条件 {#prereqs}

要使用 [!DNL Data Connection] 扩展上，您必须具备以下条件：

- Adobe Commerce 2.4.3或更高版本
- Adobe ID和组织ID
- [Adobe客户端数据层(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). 需要ACDL才能收集店面事件数据。
- 对其他AdobeDX产品的权利

## 载入步骤

1. [安装](install.md) 该 [!DNL Data Connection] 扩展。
1. [登录](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 到您的Adobe帐户和 [查看以确认](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的组织ID。 组织ID是与您配置的Experience Cloud公司关联的ID。 此ID是由24个字符组成的字母数字字符串，其后跟（且必须包括） `@AdobeOrg`.
1. [创建或更新](update-xdm.md) 您的XDM架构和特定于商务的字段组。
1. [创建数据集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 基于您创建或更新的架构。 此数据集包含您发送的商务数据。
1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 并选择包含特定于Commerce的字段组的XDM架构。
1. [连接到Commerce Services](../landing/saas.md).
1. [连接到Adobe Experience Platform](connect-data.md).

## 受众

本指南专为希望将其Adobe Commerce数据连接到其他AdobeDX产品的Adobe Commerce商家设计。

### PWA Studio支持

请参阅 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 有关如何使用的信息，请参阅文档 [!DNL Data Connection] 扩展名放在PWA Studio店面。

### AEM支持 {#aem-support}

请参阅 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) 文档，以了解如何使用CIF将storefront事件数据从AEM渲染的产品页面发送到Experience Platform- [!DNL Data Connection] 扩展。

如果您需要本指南中未涉及的信息或问题，请使用以下资源：

- [帮助中心](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 提交票证以接收其他帮助。
