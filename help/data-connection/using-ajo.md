---
title: 使用Adobe Journey Optimizer发送放弃的购物车电子邮件
description: 了解如何使用Adobe Journey Optimizer发送放弃的购物车电子邮件。
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: ee84525a9146123d80c303e40acdc6baba098cdd
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 0%

---

# 使用Adobe Journey Optimizer发送放弃的购物车电子邮件

了解如何在购物车或浏览器会话已被放弃时发送个性化的重新参与电子邮件或通知。 在本篇文章中，您将使用从查看过许多产品和类别、参与过某个产品或在一个页面上花费时间的客户那里生成的数据。

## 应考虑使用哪些数据？

使用店面和后台事件的数据构建放弃的购物车、浏览电子邮件或通知。

| 数据类型 | 店面数据（行为事件） | 后台数据（服务器端事件） |
|---|---|---|
| **定义** | 客户在您的网站上采取的点击或操作。 | 关于生命周期的信息和每个订单的详细信息（过去和当前）。 |
| **Adobe Commerce捕获的事件** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlaced](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[订单历史记录](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### 我能用Adobe Commerce做什么？

使用Adobe [!DNL Commerce] 以设置基于规则的电子邮件提醒，此类提醒可用作购物车或浏览放弃电子邮件。 在此处了解详情。

### 我能用Adobe做什么 [!DNL Commerce] 和Experience Cloud？

- **Adobe [!DNL Commerce] 使用Adobe Journey Optimizer**  — 使用Adobe [!DNL Commerce] 通过Adobe Journey Optimizer，您可以使用 [!DNL Commerce] 数据作为全渠道放弃历程的触发器。 您可以根据客户属性、他们放弃的项目、其他购物行为和过去的购买行为，个性化该历程。

- **Adobe Commerce、Adobe Journey Optimizer和Adobe Real-Time CDP**  — 添加Real-Time CDP允许您根据统一的客户配置文件和集中管理的基于规则或由AI支持的受众，进一步优化放弃促销活动。 例如，您可以创建：

   - 弃用率较低的“转化率较高”受众
   - 多次重新访问某些类别的“高关注度”受众
   - 一个“高潜能”受众，拥有高支出和高忠诚度，但最近放弃了

### 其他客户取得了哪些成就？

Adobe [!DNL Commerce] 客户通过使用Adobe实施个性化的放弃促销活动，实现了显着的业务影响 [!DNL Commerce]，Adobe [!DNL Journey Optimizer]、和Adobe [!DNL Real-Time CDP].

一家全球多品牌服装零售商实现了：

- 来自新营销活动的1.9倍点击转化率
- 来自全渠道弃用之旅的收入增加57%
- 重新参与活动的转化率提高41%
- 每周有1000多名新购物者参与

一家全球饮料公司实现了：

- 36%的重新参与电子邮件打开率
- 点进率提高21%
- 转化率提升了8.5%
- 89%的重新参与放弃者改变了

## 让我们开始吧

此特定用例侧重于使用来自以下对象的数据创建放弃的购物车电子邮件 [!DNL Commerce] 实例并将它发送到Adobe [!DNL Journey Optimizer].

### 什么是Adobe Journey Optimizer？

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) 帮助您为购物者打造个性化的商业体验。 例如，您可以使用Journey Optimizer创建和投放计划的营销活动，如零售商店的每周促销活动，或者，如果客户将产品添加到购物车，但未完成结账过程，则生成放弃的购物车电子邮件。

在本主题中，您将学习通过收听 `checkout` 事件生成自 [!DNL Commerce] 实例并响应该Journey Optimizer事件。

>[!IMPORTANT]
>
>出于演示目的，请使用 [!DNL Commerce] 沙盒环境，这样您就不会用发送到Experience Platform的店面和后台事件数据稀释生产事件数据。

### 先决条件

在开始这些步骤之前，请确保：

- 您已配置为使用Adobe [!DNL Journey Optimizer]. 如果您不确定，请咨询您的系统集成商或管理项目和环境的开发团队。
- 您 [已安装](install.md) 和 [已配置](connect-data.md) 该 [!DNL Data Connection] 中的扩展 [!DNL Commerce].
- 您 [已确认](connect-data.md#confirm-that-event-data-is-collected) 您的 [!DNL Commerce] 事件数据将到达Experience Platform边缘。

## 步骤1：在中创建用户 [!DNL Commerce] 沙盒环境

在您的沙盒环境中创建一个用户，并确认用户帐户信息显示在Experience Platform中。 请确保您指定的电子邮件有效，因为稍后在此部分中会使用该电子邮件发送放弃的购物车电子邮件。

1. 登录或在您的帐户中创建帐户 [!DNL Commerce] 沙盒环境。

   ![登录到您的测试帐户](assets/sign-in-account.png){width="700" zoomable="yes"}

   使用 [!DNL Data Connection] 安装并配置的扩展后，此帐户信息将作为配置文件发送到Experience Platform。

1. 确认您的用户帐户信息显示在 **[!UICONTROL Profile]** 部分Experience Platform。

   转到 **[!UICONTROL Profiles]** 在Adobe Experience Platform中。 单击 **[!UICONTROL Detail]** ，查看您创建的配置文件。

   ![确认配置文件](assets/check-event-profile.png){width="700" zoomable="yes"}

## 步骤2：在Journey Optimizer中查看事件

在您的 [!DNL Commerce] 沙盒环境，通过查看产品页面、将项目添加到购物车以及完成购物者可以执行的各种其他活动来触发店面上的事件。 然后，确认这些事件正在流入Journey Optimizer。

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. 选择 **[!UICONTROL Profiles]**.
1. 设置 **[!UICONTROL Identity namespace]** 到 `Email`.
1. 设置 **[!UICONTROL Identity value]** 到您的电子邮件地址。
1. 选择您的个人资料，然后选择 **[!UICONTROL Events]** 选项卡。

   ![检查事件详细信息](assets/check-event-details.png){width="700" zoomable="yes"}

   查找 `commerce.checkouts` 事件并检查事件有效负载：

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   如您所见，完整的事件有效负载包含丰富的事件数据。 在下一部分中，您将配置Journey Optimizer中的事件以侦听和响应 `commerce.checkouts` 事件生成自 [!DNL Commerce] 店面。

## 步骤3：在Journey Optimizer中配置事件

在Journey Optimizer中配置两个事件：一个事件监听 `commerce.checkouts` Commerce事件，另一个是基本超时事件，需要等待一段时间才能触发放弃的购物车电子邮件。

### 创建监听程序事件

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. 单击 **[!UICONTROL Configurations]** 在 **[!UICONTROL Administration]** 部分。

1. 在 **[!UICONTROL Events]** 图块，单击 **[!UICONTROL Manage]**.

   ![Journey Optimizer事件配置](assets/ajo-config.png){width="700" zoomable="yes"}

1. 在 **[!UICONTROL Events]** 页面，单击 **[!UICONTROL Create Event]**.

1. 在右侧导航中，按如下方式设置您的事件：

   1. 设置 **[!UICONTROL Name]** 至： `firstname_lastname_checkout`.
   1. 设置 **[!UICONTROL Type]** 到 **[!UICONTROL Unitary]**.
   1. 设置 **[!UICONTROL Event id typ]e** 到 **[!UICONTROL Rule based]**.
   1. 设置 **[!UICONTROL Schema]** 敬您的 [!DNL Commerce] [架构](update-xdm.md).
   1. 选择 **[!UICONTROL Fields]** 以打开 **[!UICONTROL Fields]** 页面。 然后，选择对此事件有用的字段。 例如，选择 **[!UICONTROL Product list items]**， **[!UICONTROL Commerce]**， **[!UICONTROL eventType]**、和 **[!UICONTROL Web]**.
   1. 单击 **[!UICONTROL OK]** 以保存选定的字段。
   1. 在 **[!UICONTROL Event id condition]** 字段。 然后，创建一个条件： `eventType` 等于 `commerce.checkouts` 和 `personalEmail.address` 等于在上一部分中创建用户档案时使用的电子邮件地址。

      ![Journey Optimizer设置条件](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. 单击 **[!UICONTROL OK]**.
   1. 单击 **[!UICONTROL Save]** 以保存您的事件。

### 创建超时事件

1. 像之前一样在Journey Optimizer中创建事件。

1. 在右侧导航中，按如下方式设置您的事件：

   1. 设置 **[!UICONTROL Name]** 至： `firstname_lastname_timeout`.
   1. 设置 **[!UICONTROL Type]** 到 **[!UICONTROL Unitary]**.
   1. 设置 **[!UICONTROL Event id type]** 到 **[!UICONTROL Rule based]**.
   1. 设置 **[!UICONTROL Schema]** 敬您的 [!DNL Commerce] [架构](update-xdm.md).
   1. 设置 **[!UICONTROL Schema]**， **[!UICONTROL Fields]**、和 **[!UICONTROL Event id condition]** 与上面相同。
   1. 单击 **[!UICONTROL Save]** 以保存您的事件。

配置这两个事件后，创建一个历程，以发送放弃的购物车电子邮件。

## 步骤4：构建结账历程

创建监听 `commerce.checkouts` 事件，然后在过了指定的时间后发送放弃的购物车电子邮件。

1. 在Journey Optimizer中，选择 **[!UICONTROL Journeys]** 下 **J[!UICONTROL OURNEY MANAGEMENT]**.
1. 单击 **[!UICONTROL Create Journey]**.
1. 指定历程的名称。
1. 单击 **[!UICONTROL OK]** 以保存历程。
1. 在左侧导航中的 **[!UICONTROL EVENTS]** 部分，搜索您之前创建的签出事件： `firstname_lastname_checkout` 然后将其拖放到画布上。

   >[!TIP]
   >
   >双击事件会自动将其添加到画布。

1. 搜索超时事件并将其添加到画布。
1. 双击超时事件。

   1. 在 **[!UICONTROL Timeout]** 部分，选择 **[!UICONTROL Define the event time]** 复选框。
   1. 在 **[!UICONTROL Wait for]** 字段输入 `1` 和 `Minute`.
   1. 选择 **[!UICONTROL Set a timeout path]** 复选框。

   使用此超时配置，执行结账但未在一分钟内完成订单的购物者将触发此超时分支。 在实际生产环境中，您需要设置更长的时间段，如24小时。

1. 在左侧导航中，位于 **[!UICONTROL ACTIONS]**，添加 **[!UICONTROL Email]** 超时分支的操作。 您的历程应如下所示：

   ![Journey Optimizer画布](assets/ajo-canvas.png){width="700" zoomable="yes"}

### 创建放弃的购物车电子邮件

创建在检测到放弃的购物车时发送的放弃的购物车电子邮件。

1. 在上面创建的历程中，双击 **[!UICONTROL Email]** 图标。

1. 请遵循 [步骤](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) Journey Optimizer ，以创建放弃的购物车电子邮件。

现在，您有一个在Journey Optimizer中收听 `commerce.checkouts` 来自您的的事件 [!DNL Commerce] 存储以及在一段时间后发送的放弃的购物车电子邮件。 下一部分将向您展示如何测试旅程。

## 步骤5：实时触发签出事件

在此部分中，您将实时测试事件。

1. 在Journey Optimizer中，切换测试模式。

   ![启用测试模式](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. 要实时测试此历程，请打开另一个浏览器选项卡，然后转到 [!DNL Commerce] 沙盒环境中的网站。

   1. 将产品添加到购物车。
   1. 转到结帐页面。
   1. 在结账页面中，通过返回主页或关闭选项卡来放弃购物车。

      旅程现在会触发。 要进行确认，请在Journey Optimizer中打开包含您的旅程的选项卡。 您应该会看到一个绿色箭头，其中显示用户经历的路径。

1. 检查收件箱中的电子邮件。
