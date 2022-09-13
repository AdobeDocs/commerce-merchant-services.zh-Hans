---
title: 订单付款状态报表
description: 使用“订单付款状态”报表可查看订单的付款状态并确定任何潜在问题。
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: ac1d0a4e64f358da44796edb0138b3656a907440
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 订单付款状态报表

[!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的报表，以便您能够清楚地了解商店的订单和付款情况。

![财务报表视图](assets/reports-view-new.png)

“订单付款状态”报表可帮助您轻松了解特定订单在订单中的现金流程流中的位置。 此报表允许您快速查看订单的付款状态并识别任何潜在问题。

您不必打开多个视图，即可人工交叉引用订单和付款。 [!DNL Payment Services] 表示 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 使您能够从“订单付款状态”报表中全面查看订单和付款。

请在“管理员”中查看此报表中的付款状态、开票和发运状态、退款状态、争议状态等。

您可以下载.csv文件格式的订单付款状态事务处理，以便在现有的会计或订单管理软件中使用。

>[!NOTE]
>
>如果没有 [已载入和已激活的实时模式](production.md#enable-live-payments) 表示 [!DNL Payment Services].

## 报表中使用的数据

的 [!DNL Payment Services] 模块使用订单数据，并将其与其他来源（包括PayPal）的汇总付款数据合并，以提供有意义且非常有用的报表。

订单数据将导出并保留在付款服务中。 当您 [更改或添加订单状态](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;}或 [编辑商店视图](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [商店](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}或网站名称，该数据与付款数据相结合，并且订单付款状态报表填充了组合信息。

此过程中有两个步骤：

1. 索引已更改数据 `ON SAVE` （每次订单信息或商店信息发生更改时）或 `BY SCHEDULE` （根据预配置的cron计划），具体取决于 [索引管理](https://docs.magento.com/user-guide/system/index-management.html)管理员中的{target=&quot;_blank&quot;}。

   默认情况下，会进行数据索引 `ON SAVE`，这意味着每当某些内容在顺序、顺序状态、存储视图、存储区或网站中发生更改时，都会立即进行重新索引过程。

1. 索引数据将发送到付款服务，然后将其填充到订单付款状态报表中。

出于报告目的导出和整理的唯一数据是订单付款状态报表使用的数据。

>[!NOTE]
>
>此表中显示的数据按降序排序(`DESC`) `ORDER DATE`. 的 `ORDER DATE` 是创建订单的日期时间戳。

### 配置数据导出

尽管默认情况下，在 `ON SAVE` 模式，建议在 `BY SCHEDULE` 模式。 的 `BY SCHEDULE` 索引在cron计划下运行1分钟，任何更改的数据都会在任何数据更改后的两分钟内显示在“订单状态”报表中。 此计划的重新索引有助于您减少存储上的任何压力，特别是当您有大量传入订单时，因为它是按计划进行的（不是在每个订单下达时）。

可以更改索引模式 — `ON SAVE` 或 `BY SCHEDULE`—[在管理员中](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}。

要了解如何配置数据导出，请参阅 [命令行配置](configure-cli.md#configure-data-export).

## 可用性

在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** 查看订单的付款状态。

![管理员中的订单付款状态](assets/order-payment-status-report.png)

## 选择数据源

在“订单付款状态”报表视图中，您可以选择数据源 — _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_ — 要查看其报表结果。

![数据源选择](assets/datasource.png)

如果 _[!UICONTROL Live]_是选定的数据源，则可以查看使用 [!DNL Payment Services] in_[!UICONTROL Live]_ 模式。 如果 [!UICONTROL Sandbox]_是选定的数据源，您可以看到沙盒环境的报表信息。

数据源选择的工作方式如下：

* 如果您没有使用 [!DNL Payment Services] 在实时模式下，数据源选择默认为 _[!UICONTROL Sandbox]_.
* 如果您有任何商店（一个或多个）使用 [!DNL Payment Services] 在实时模式下，数据源选择默认为 _[!UICONTROL Live]_.
* 报表导出始终遵循数据源选择。

为 [!UICONTROL Order Payment Status] 报表：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 单击 **[!UICONTROL Data source]** 选择 _[!UICONTROL Live]_或_[!UICONTROL Sandbox]_.

   报表结果会根据所选的数据源重新生成。

## 自定义日期时间范围

从“订单付款状态”报表视图中，您可以通过选择特定日期来自定义要查看的状态的时间范围。 默认情况下，网格中会显示30天的订单付款状态。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 单击 **[!UICONTROL Order dates]** 日历选择器过滤器。
1. 选择适用的日期范围。
1. 在网格中查看指定日期的订单付款状态。

## 显示和隐藏列

默认情况下，“订单付款状态”报表显示所有可用的信息列。 但是，您可以自定义在报表中看到的列。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 单击 _列设置_ 图标(![列设置图标](assets/column-settings.png))。
1. 要自定义在报表中看到的列，请勾选或取消选中列表中的列。

   订单付款状态报表将立即显示您在列设置菜单中所做的任何更改。 列首选项将会保存，并且在您离开报表视图时保持有效。

## 查看状态

“订单付款状态”报表视图显示每个付款服务订单的全面事务处理状态和付款状态信息。

### 交易状态

默认情况下，网格中会显示30天的订单付款状态。

向左和向右滚动以查看 [订单付款状态信息](#column-descriptions)，包括订单日期、授权日期、开票、发运、付款状态等。

在搜索中返回或在默认的30天订单付款状态下显示的行数显示在“订单付款状态”视图网格的上方，并与“订单日期日历选择器”筛选器一起显示。

### 付款状态

“付款状态”列显示任何付款的当前状态。 A `Capture failed` 付款显示红色警报状态和 `Voided` 付款显示灰色警报状态。

### 退款状态

“退款状态”列显示任何退款的当前状态。 A `Capture failed` 付款显示红色警报状态和 `Voided` 付款显示灰色警报状态。

## 更新报表数据

“订单付款状态”报表视图显示 _[!UICONTROL Last updated]_显示上次更新报表信息的时间戳。 默认情况下，订单付款状态报表数据每三小时自动刷新一次。

您还可以手动强制刷新订单付款状态报表数据以查看最新的报表信息。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 单击 _刷新_ 图标(![刷新图标](assets/refresh-button-med.png))。

   订单付款状态报表数据将刷新， *[!UICONTROL Update complete]* 确认出现，并且网格中存在最新信息。

## 查看争议

您可以查看商店订单上的任何争议，并从“订单付款状态”报表中定位至PayPal解决中心以对它们采取措施。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 导航到 **[!UICONTROL Disputes column]**.
1. 查看特定订单的任何争议并查看 [争议状况](#order-payment-status-information).
1. 单击争议ID链接(以 _PP-D-_)转到 [PayPal解决中心](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. 根据需要对争端采取适当行动。

   要按状态对订单争议进行排序，请单击“争议”列标题。

## 下载订单付款状态

无论您是查看默认的30天状态还是自定义的时间范围，您都可以下载一个.csv文件，其中的所有状态都显示在“订单付款状态”视图网格中。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 如果要查看过去30天以外的某个时间范围的状态，请 [自定义状态的日期范围时间范围](#customize-dates-timeframe).
1. 单击 _下载_ (![下载图标](assets/icon-download.png))图标。

您的订单付款状态将以.csv格式下载。

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## 订单付款状态信息

“订单付款状态”视图显示网格中显示的每个状态的广泛信息。

### 列描述

订单付款状态报表包括以下信息。

| 列 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商务订单ID<br> <br>查看相关 [订购信息](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}，单击ID。 |
| [!UICONTROL Order Date] | 订单日期时间戳 |
| [!UICONTROL Authorized Date] | 付款授权的日期时间戳 |
| [!UICONTROL Order Status] | 当前商务 [订单状态](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | 订单的发票状态 — *[!UICONTROL No]*, *[!UICONTROL Partial]*&#x200B;或 *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | 订单的发运状态 — *[!UICONTROL No]*, *[!UICONTROL Partial]*&#x200B;或 *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | 订单总金额 |
| [!UICONTROL Cur] | 订单的货币类型 |
| [!UICONTROL Pay Status] | 特定订单的付款状态 |
| [!UICONTROL Paid Amt] | 订单上支付的金额 |
| [!UICONTROL Cur] | 订单支付金额的币种类型 |
| [!UICONTROL Refund Status] | 订单退款的状态（例如退货、RMA和贷项通知单中的信息） —    *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*&#x200B;或 *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | 订单的退还金额总计 |
| [!UICONTROL Cur] | 订单退还金额的货币类型 |
| [!UICONTROL Disputes] | 对订单的任何争议状况（来自争议和拖欠的信息） — *[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]*&#x200B;或 *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | 在订单的商务交易中使用的付款方法 |
| [!UICONTROL Website] | 下订单的网站 |
| [!UICONTROL Store] | 下订单的商店 |
| [!UICONTROL Store View] | 从中下达订单的存储视图 |
