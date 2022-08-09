---
title: 指南概述
description: Adobe Experience Platform connector for Adobe Commerce可将您的Commerce实例连接到其他Adobe Experience Cloud产品。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Experience Platform连接器概述

Experience Platform连接器扩展允许Adobe Commerce商户将数据发送到Adobe Experience Platform边缘，以便其他Adobe Experience Cloud产品(如Adobe Analytics和Adobe Target)可以使用该商务数据。 通过将您的商务数据连接到Adobe Experience Cloud中的其他产品，您可以执行各种任务，例如分析网站上的用户行为、执行AB测试，以及创建个性化的营销活动。

Storefront事件捕获购物者交互，例如 `View Page`, `View Product`, `Add to Cart`，等等。 捕获的数据不包括个人身份信息(PII)。 所有用户标识符（如Cookie ID和IP地址）都严格匿名化。 [了解更多](https://www.adobe.com/privacy/experience-cloud.html). 请参阅 [storefront事件](events.md).

## 使用Experience Platform连接器的先决条件 {#prereqs}

要使用Experience Platform连接器，必须首先：

- 填写以下内容 [表单](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) 和Adobe将为您配置对数据流和Adobe Experience Platform（如果需要）的访问权限。

授予访问权限时：

1. [登录](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe帐户。
1. 看您的 [组织](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 组织ID是与您配置的Experience Cloud公司关联的ID。 此ID是由24个字符组成的字母数字字符串，其后跟（且必须包括） `@AdobeOrg`.
1. 创建或更新 [XDM架构](update-xdm.md) 具有特定于商务的字段组。
1. [创建数据流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) ，然后选择包含特定于商务的 **字段组**.

>[!NOTE]
>
> 组织ID和数据流用于将您的Adobe Commerce实例连接到Adobe Experience Platform。

## 后续步骤

- 安装 [Experience Platform连接器扩展](install.md).

   Experience Platform连接器扩展从服务器的命令行安装，并作为 [服务](../landing/saas.md). 过程完成后，Experience Platform连接器将显示在 **系统** 菜单下 **服务** 在商务中 _管理员_.
- [上传购物者配置文件](profile.md) 店面数据可归因于特定购物者以提升其购物体验。

## 受众

本指南专为必须将其Adobe Commerce店面数据与其他AdobeDX产品连接的Adobe Commerce商家而设计。

### PWA Studio支持

请参阅 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) 文档，以了解有关如何在PWA Studio店面中使用Experience Platform连接器的信息。

## 已知问题

目前，Experience Platform连接器存在以下已知问题：

- 安装了B2B模块的Adobe Commerce Enterprise Edition不支持搜索事件。
- 连接到Adobe Commerce边缘后，Storefront数据需要大约一小时才能从Adobe Experience Platform转到各种目标。

如果您需要信息或遇到本指南未涵盖的问题，请使用以下资源：

- [帮助中心](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [支持票证](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — 提交票证以接收其他帮助。
- Slack: `#beacon-ama`
