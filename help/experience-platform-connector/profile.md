---
title: 将购物者配置文件上传到Adobe Experience Platform
description: 了解如何将购物者配置文件上传到Adobe Experience Platform。
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 将购物者配置文件上传到Adobe Experience Platform

Adobe Commerce商户可以将客户用户档案数据上传到 [实时客户资料](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)，是Adobe Experience Platform的一部分。 利用用户档案，可将客户数据整合到统一视图中，为每次客户互动提供一个加盖时间戳的可操作帐户。

>[!NOTE]
>
> 用户档案数据必须包含电子邮件地址，因为这是购物者与其店面行为数据之间链接的创建方式。

在您上传购物者的配置文件后，与购物者在您的网站上进行的任何交互关联的事件数据将通过Experience Platform连接器发送到配置文件，并链接到该购物者的配置文件。

>[!NOTE]
>
> 的 `createAccount` [storefront事件](events.md) 不会在“配置文件”中自动创建客户配置文件。 出于安全原因，这是有意为之的。

在本主题中，您将了解如何在Experience Platform中将Adobe Commerce客户用户档案上传到实时客户用户档案。

1. 确定客户数据的存储位置。 对于某些商户，此数据存储在Adobe Commerce中，可以 [导出](https://docs.magento.com/user-guide/system/data-export.html) 文件。 对于其他客户，它可能位于单独的客户关系管理(CRM)系统中。

1. 在确定客户数据的存储位置后，找到相应的 [源连接器](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en) 基于客户数据的存储位置。 如果看不到相应的源连接器，请使用 [本地文件上传](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) 连接器和从CSV文件导入购物者配置文件。

   >[!NOTE]
   >
   > 如果使用本地文件上传连接器，则必须启用 **配置文件数据集** 选项时 [定义数据集](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). 这会将数据集标识为用户档案数据。

在用户档案中创建购物者配置文件后，与该购物者关联的所有店面数据都将链接到其配置文件。

## 经常上传用户档案

为确保增强的购物者体验，您应定期导入用户档案数据。 某些源连接器允许您按计划导入配置文件数据。
