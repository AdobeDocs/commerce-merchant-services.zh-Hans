---
title: 设置
description: 了解如何更改源 [!DNL Product Recommendations] 数据和如何启用可视化推荐。
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 48e350167611a2737d79bf5decccd7f6f24c714c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# 设置

当您 [配置SaaS数据空间](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 对于Recommendations，SaaS数据空间收集目录数据和店面行为数据。 [Adobe Sensei](https://www.adobe.com/sensei.html) 分析这些数据并计算用于提供Product Recommendations的产品关联。

用于测试或暂存的非生产环境通常不具备店面行为数据的数量或质量，因而无法提供切实可行的产品推荐。 实际购物者行为只能在生产环境中捕获。 要解决此问题，Adobe Commerce允许您将生产环境中的产品推荐与其他非生产SaaS数据空间结合使用。 通过在非生产环境中使用实际的店面数据，您可以预览购物者看到的推荐，并尝试使用不同的推荐类型和放置位置。 其他SaaS数据空间中的Recommendations可供购物者预览，但无法单击。

>[!NOTE]
>
>通过REST使用产品Recommendations时， `alternateEnvironmentId` 参数可用于指定其他数据空间。 通过GraphQL使用产品Recommendations时，此参数不可用。

## 选择推荐源

要更改产品推荐数据的来源，请选择包含要使用的行为数据的SaaS数据空间。 在开始之前，请确保：

- 店面数据收集必须为 [已配置并启用](install-configure.md) 生产环境和 [已验证](verify.md) 行为数据将被发送到Adobe Commerce。
- 您的非生产环境目录应该与生产目录基本相同。 使用类似的目录可确保产品推荐单元的返回与生产中的单元非常相似。

1. 登录到非生产Adobe Commerce环境的管理员。

1. 在 _管理员_ 侧栏，转到 **营销** > _促销活动_ > **产品Recommendations**.

1. 单击 **设置**.

   ![产品推荐设置](assets/settings.png)
   _设置_

1. 在 _Recommendations源_ 部分，启用 **从其他SaaS数据空间获取推荐** 选项。 此 _Recommendations源_ 部分仅在非生产环境中显示。

   列表 _可用的SaaS数据空间_ 显示。

   ![产品推荐设置](assets/settings-select-saas.png)
   _设置_

1. 选择具有要使用的购物者数据的SaaS数据空间。

1. 单击 **保存更改**.

   Adobe Commerce现在会从所选数据空间获取推荐。

   >[!NOTE]
   >
   > 虽然您可以查看从非生产店面的其他SaaS数据空间获取的推荐，但无法单击这些推荐。

### 配置新的SaaS数据空间

1. 在Recommendations源部分中，单击 **编辑配置**.

1. 按照说明配置新的 [[!DNL Commerce] 服务](/help/landing/saas.md).

## 启用可视化推荐

如果 [可视化产品Recommendations](install-configure.md) 模块已安装，您必须启用Visual Recommendations才能使用 [视觉相似度](type.md#visualsim) 推荐类型。

在 _可视化Recommendations_ 部分，设置 **启用可视Recommendations** 到活动位置。
