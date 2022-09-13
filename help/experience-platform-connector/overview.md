---
title: 指南概述
description: 了解如何使用Adobe Commerce连接器将Adobe Experience Platform数据与Experience Platform集成。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Experience Platform连接器概述

Experience Platform连接器扩展允许Adobe Commerce商户将数据发送到Adobe Experience Platform边缘，以便其他Adobe Experience Cloud产品(如Adobe Analytics和Adobe Target)可以使用该商务数据。 通过将您的商务数据连接到Adobe Experience Cloud中的其他产品，您可以执行各种任务，例如分析网站上的用户行为、执行AB测试，以及创建个性化的营销活动。

[店面事件](events.md) 捕获购物者交互，例如 `View Page`, `View Product`, `Add to Cart`，等等。 捕获的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都严格匿名化。 [了解更多](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platform连接器显示在“商务管理员”下的 **系统** >服务> **Experience Platform连接器**.

![Experience Platform连接器扩展管理视图](assets/epc-adminui.png)

## 先决条件 {#prereqs}

要使用Experience Platform连接器，您必须具有以下内容：

- Adobe Commerce 2.4.3或更高版本
- Adobe ID和组织ID
- 其他AdobeDX产品的授权

## 入门步骤

1. [安装](install.md) Experience Platform连接器扩展。
1. [登录](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe帐户和 [视图](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 您的组织ID。 组织ID是与您配置的Experience Cloud公司关联的ID。 此ID是由24个字符组成的字母数字字符串，其后跟（且必须包括） `@AdobeOrg`.
1. [连接](connect-data.md) 您的Adobe Commerce实例到Adobe Experience Platform。
1. [创建或更新](update-xdm.md) 您的XDM架构，其中包含特定于商务的字段组。
1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 并选择包含特定于商务的字段组的XDM架构。
1. （可选） [上传购物者配置文件](profile.md) 店面数据可归因于特定购物者以提升其购物体验。

## 受众

本指南专为希望将其Adobe Commerce店面数据与其他AdobeDX产品连接的Adobe Commerce商家而设计。

### PWA Studio支持

请参阅 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 文档，以了解有关如何在PWA Studio店面中使用Experience Platform连接器的信息。

如果您需要信息或遇到本指南未涵盖的问题，请使用以下资源：

- [帮助中心](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [支持票证](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — 提交票证以接收其他帮助。
