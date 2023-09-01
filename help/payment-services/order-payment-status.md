---
title: 订单付款状态报表
description: 使用“订单付款状态”报表可以查看订单的付款状态，并确定任何潜在问题。
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 9242e8eea078a00445c7f24ffc998b7d978a9775
workflow-type: tm+mt
source-wordcount: '1868'
ht-degree: 0%

---

# 订单付款状态报表

[!DNL Payment Services] 对象 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 提供全面的报表，以便您清楚地了解商店的 [交易](transactions.md)、订单和支付。

有两个可用的“订单付款状态”报告视图，使您可以快速查看订单的付款状态：

* **[订单付款状态可视化图表视图](#order-payment-status-data-visualization-view)** — 付款服务主页上的图表，它直观地显示订单付款状态报表视图中的每日汇总付款状态
* **[订单付款状态报表视图](#order-payment-status-report-view)** — 以订单付款状态报告可用，显示所有事务处理的详细付款、已开票、已发运、退款和争议状态

订单付款状态视图帮助您轻松了解特定订单在订单到现金流程中的位置。 这些报告允许您根据订单的付款状态和付款日期快速查看订单，并识别任何潜在问题。

您可以 [下载订单付款状态](#download-order-payment-statuses) CSV文件格式，用于现有会计或订单管理软件。

>[!NOTE]
>
>如果没有，则无法查看财务报表 [已载入和激活的实时模式](production.md#enable-live-payments) 对象 [!DNL Payment Services].

## 订单支付状态数据可视化视图

可在Payment Services主页中找到订单付款状态数据可视化视图。 这是详细表格中每天汇总支付状态的可视表示形式 [订单付款状态报表视图](#order-payment-status-report-view).

在 _管理员_ 侧栏，转到 **销售** > **支付服务** > _订购_ 查看数据可视化图表 [付款状态表](#statuses-information).

![管理员中的支付数据可视化图表](assets/orderpayment-dataviz.png){zoomable=yes}

单击 **[!UICONTROL View Report]** 导航到详细表格 [订单付款状态报表视图](#order-payment-status-report-view).

### 自定义状态时间范围

默认情况下，将显示30天的付款状态。

从“订单付款状态”可视化图表视图中，您可以通过选择日期范围来自定义要查看的付款状态的时间范围：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. 订单支付状态数据可视化图表视图在以下位置可见： _订购_ 部分。
1. 单击 **[!UICONTROL Range]** 选择器过滤器。
1. 选择适用的日期范围 — 30天、15天或7天。
1. 查看指定日期的状态信息。

### 状态信息

选定日期范围的付款状态显示在“订单付款状态”数据可视化视图的左侧。 所选日期范围的日期显示在视图底部。 如果特定日期没有订单，则不会显示该日期。

订单支付状态数据可视化视图包含以下信息。

| 数据 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL Orders] | 指定时间范围内的订单金额范围；Y轴上的数据（左） |
| 日期范围 | 指定时间范围的日期范围；X轴（底部）上的数据 |
| 已授权 | 订单已授权 |
| 已请求捕获 | 订单捕获请求 |
| 捕获已确认 | 订单捕获已完成 |
| 部分捕获 | 部分捕获的订单 |
| 捕获失败 | 订单捕获失败 |
| 已失效 | 订单已失效 |

## 订单付款状态报表视图

在Payment Services的“主页”视图中可以使用“订单付款状态”报表视图。 它包括所有交易的详细状态 — 付款、已开票、已发运、退款、争议等。

在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**要查看详细的表格形式订单付款状态报表视图，请执行以下操作：

![管理员中的订单付款状态交易记录](assets/orders-report-data.png)

您可以根据本主题中的部分对此视图进行配置，以便最好地呈现您希望查看的数据。

您可以 [下载支付交易记录](#download-order-payment-statuses) CSV文件格式，用于现有会计或订单管理软件。

>[!NOTE]
>
>此表中显示的数据按降序排序(`DESC`)默认情况下，使用 `TRANS DATE`. 此 `TRANS DATE` 是启动交易的日期和时间。

### 报表中使用的数据

此 [!DNL Payment Services] 模块使用订单数据，并将其与其他来源（包括PayPal）的汇总付款数据相结合，以提供有意义且非常有用的报表。

订单数据将导出并保留在支付服务中。 当您 [更改或添加订单状态](https://docs.magento.com/user-guide/sales/order-status-custom.html) 或 [编辑商店视图](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html)， [存储](https://docs.magento.com/user-guide/stores/store-information.html)或网站名称)时，该数据将与付款数据相结合，并且订单付款状态报表中会填充合并的信息。

此过程包括两个步骤：

1. 索引是更改的数据 `ON SAVE` （每次更改订单信息或商店信息时）或 `BY SCHEDULE` （按照预配置的cron计划），具体取决于在中如何进行配置 [索引管理](https://docs.magento.com/user-guide/system/index-management.html) 在“管理员”中。

   默认情况下，进行数据索引 `ON SAVE`，这意味着每当订单中的某些内容、订单状态、商店视图、商店或网站发生更改时，索引过程都会立即发生。

1. 系统会将索引数据发送到付款服务，然后付款服务将填充到订单付款状态报表中。

为报告目的而导出和整理的唯一数据是“订单付款状态”报表使用的数据。

>[!NOTE]
>
>此表中显示的数据按降序排序(`DESC`)默认情况下，使用 `ORDER DATE`. 此 `ORDER DATE` 是创建订单的日期时间戳。

#### 配置数据导出

即使默认情况下，重新索引也会在 `ON SAVE` 模式，建议您在 `BY SCHEDULE` 模式。 此 `BY SCHEDULE` 索引以1分钟的cron时间表运行，任何更改的数据将在任何数据更改后的2分钟内显示在订单状态报表中。 此计划的重新索引可帮助您减少存储空间上的任何压力，尤其是在您有大量传入订单的情况下，因为它按计划进行（而不是在每次下订单时）。

您可以更改索引模式 — `ON SAVE` 或 `BY SCHEDULE`—[在管理员中](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

要了解如何配置数据导出，请参阅 [命令行配置](configure-cli.md#configure-data-export).

### 选择数据源

在“订单付款状态”报表视图中，您可以选择数据源 — **[!UICONTROL Live]** _或 **[!UICONTROL Sandbox]** — 要查看其报告结果。

![数据源选择](assets/datasource.png){width=400px}

如果 _[!UICONTROL Live]_是选定的数据源，则可以查看使用的商店的报表信息 [!DNL Payment Services] 在生产模式下。 如果_[!UICONTROL Sandbox]_ 是选定的数据源，您可以看到沙盒模式的报表信息。

数据源选择的工作方式如下所示：

* 如果您没有任何使用 [!DNL Payment Services] 在实时模式下，数据源选项默认为 _[!UICONTROL Sandbox]_.
* 如果您有任何商店（一个或多个）使用 [!DNL Payment Services] 在实时模式下，数据源选项默认为 _[!UICONTROL Live]_.
* 报表导出始终遵循数据源选择。

要为选择数据源，请执行以下操作 [!UICONTROL Order Payment Status] 报告：

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. 单击 _[!UICONTROL Data source]_选择器筛选并选择&#x200B;**[!UICONTROL Live]**或&#x200B;**[!UICONTROL Sandbox]**.

   报表结果会根据所选数据源重新生成。

### 自定义日期时间范围

从“订单付款状态”报表视图中，您可以通过选择特定日期来自定义要查看的状态的时间范围。 默认情况下，网格中显示30天的订单付款状态。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 单击 _[!UICONTROL Order dates]_日历选择器过滤器。
1. 选择适用的日期范围。
1. 在网格中查看指定日期的订单付款状态。

### 筛选报表信息

从“订单付款状态”报表视图中，您可以通过选择筛选条件来筛选要查看的状态结果。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 单击 **[!UICONTROL Filter]** 选择器。
1. 切换 _付款状态_ 选项，用于仅查看选定订单付款状态的报表结果。
1. 输入 _最小订单金额_ 或 _最大订单金额_ 以便在该订单金额范围内查看报表结果。
1. 单击 **[!UICONTROL Hide filters]** 以隐藏筛选器。

### 显示和隐藏列

默认情况下，“订单付款状态”报表会显示所有可用的信息列。 但是，您可以自定义您在报表中看到的列。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 单击 _列设置_ 图标(![列设置图标](assets/column-settings.png))。
1. 要自定义您在报表中看到的列，请选中或取消选中列表中的列。

   订单付款状态报表将立即显示您在“列设置”菜单中所做的任何更改。 列首选项将进行保存，如果您离开报表视图，这些首选项将保持有效。

### 查看状态

“订单付款状态”报表视图显示每个订单的综合付款状态信息。

默认情况下，网格中显示30天的订单付款状态。

向左和向右滚动以查看 [订单付款状态信息](#column-descriptions)，包括订单日期、授权日期、开票、发运、付款状态等。

在搜索中返回的行数，或默认显示的30天订单付款状态的行数，显示在“订单付款”状态视图网格的上方，与“订单日期”日历选择器过滤器一起显示。

#### 付款状态

“支付状态”列显示任何付款的当前状态。 A `Capture failed` 付款显示红色警报状态和 `Voided` 付款显示灰色警报状态。

#### 退款状态

退款状态列显示任何退款的当前状态。 A `Capture failed` 付款显示红色警报状态和 `Voided` 付款显示灰色警报状态。

### 更新报表数据

订单付款状态报表视图显示 _[!UICONTROL Last updated]_显示上次更新报告信息的时间戳。 默认情况下，订单付款状态报表数据每三小时自动刷新一次。

您也可以手动强制刷新订单付款状态报表数据，以查看最新的报表信息。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 单击 _刷新_ 图标(![刷新图标](assets/refresh-button-med.png))。

   订单付款状态报表数据已刷新，并且 *[!UICONTROL Update complete]* 确认即会出现，网格中会显示最新信息。

### 查看争议

您可以在订单付款状态报表中查看商店订单上的任何争议，然后定位至PayPal解决中心对其执行操作。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 导航至 **[!UICONTROL Disputes column]**.
1. 查看特定订单的任何争议并查看 [争议状态](#order-payment-status-information).
1. 单击争议ID链接(以 _PP-D-_)以转到 [PayPal解决中心](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. 根据需要，对争议采取适当行动。

   要按状态对订单争议进行排序，请单击“争议”列标题。

### 下载订单付款状态

您可以下载.csv文件，该文件的所有状态均显示在“订单付款”状态视图网格中，无论您查看的是默认的30天状态还是自定义的时间范围。

1. 在 _管理员_ 侧栏，转到 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. 如果您希望查看过去30天以外的其他时间范围的状态， [自定义状态的日期范围时间范围](#customize-dates-timeframe).
1. 单击 _下载_ (![下载图标](assets/icon-download.png))图标。

您的订单付款状态将以.csv格式下载。

### 列描述

订单付款状态报表包括以下信息。

| 列 | 描述 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | 商业订单ID<br> <br>查看相关内容 [订单信息](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}中，单击ID。 |
| [!UICONTROL Order Date] | 订单日期时间戳 |
| [!UICONTROL Authorized Date] | 付款授权的日期时间戳 |
| [!UICONTROL Order Status] | 当前商务 [订单状态](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | 订单的发票状态 — *[!UICONTROL No]*， *[!UICONTROL Partial]*，或 *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | 订单的装运状态 — *[!UICONTROL No]*， *[!UICONTROL Partial]*，或 *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | 订单的总金额 |
| [!UICONTROL Cur] | 订单的货币类型 |
| [!UICONTROL Pay Status] | 特定订单的付款状态 |
| [!UICONTROL Paid Amt] | 订单已付金额 |
| [!UICONTROL Cur] | 订单上已付金额的货币类型 |
| [!UICONTROL Refund Status] | 订单上的退款状态（如退货、RMA和贷项通知单中的信息） —    *[!UICONTROL Requires refund]*， *[!UICONTROL Refund requested]*， *[!UICONTROL Refunded]*， *[!UICONTROL Refund failed]*，或 *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | 订单的已退款总额 |
| [!UICONTROL Cur] | 订单退款金额的币种类型 |
| [!UICONTROL Disputes] | 订单上的任何争议状态（争议信息和退款） — *[!UICONTROL Open]*， *[!UICONTROL Waiting for buyer response]*， *[!UICONTROL Waiting for seller response]*， *[!UICONTROL Under review]*， *[!UICONTROL Resolved]*，或 *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | 在订单的商务交易记录中使用的付款方法 |
| [!UICONTROL Website] | 从中下达订单的网站 |
| [!UICONTROL Store] | 下订单的商店 |
| [!UICONTROL Store View] | 从中下达订单的存储区视图 |
