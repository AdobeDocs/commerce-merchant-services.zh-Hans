---
title: 测试和部署存储实现
description: 测试计划以验证“商店完成”功能。 测试涵盖库存同步API、取消订单的端到端履行工作流、商店履行应用程序用户管理以及客户签入体验。
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2652'
ht-degree: 0%

---


# 测试和部署用于Adobe Commerce的商店实施

在开发环境中完成载入过程后，您可以启动该过程以测试并将商店履行解决方案部署到生产环境。

**先决条件**

在测试或同步任何信息、存储或订购之前，请确认您已完成以下任务：

- 已完成 [常规配置](enable-general.md) ，用于商店履行服务。

- [添加并验证沙盒和生产环境的帐户凭据和连接详细信息](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 确认 [Adobe Commerce集成](connect-set-up-service.md#configure-store-fulfillment-account-credentials) “商店履行”解决方案可用且已授权。

## 准备测试

必须先完成连接配置，然后才能创建任何测试订单或执行集成测试。 在测试之前，还必须验证存储数据是否已同步。

1. 同步存储履行源。

   - 转到 **[!UICONTROL Stores > Sources]**.

   - 选择 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. 在存储网格中，验证存储是否标记为 `Synced` 在创建测试订单之前。

## 示例测试计划

零售商在部署的配置和测试阶段期间验证商店完成解决方案的基本功能。 此示例测试计划为测试提供了一个起点。 根据您的要求添加其他方案。

>[!NOTE]
>
>完成“商店完成”解决方案的初始入门或更新现有安装后，在部署到生产之前，请始终在非生产环境中测试应用程序。

此示例测试计划涵盖以下功能区域：

| 功能区 | 函数 | 角色 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 库存和订单同步 | 库存API同步 | Adobe Commerce管理员 |
| 端到端 | 订单取消工作流 | 客户、管理员、商店关联 |
| 管理员 | 商店履行应用程序权限 | 管理员 |
| Adobe Commerce弗朗滕 | 产品类型 | 客户，管理员 |
| 前端结账</br>签入表单 | 签入体验 | 客户，管理员 |
| 商店辅助应用程序 | 订购</br>挑选</br>阶段</br>和切换 | 存储关联 |




### 库存API同步

测试计划的此部分涵盖库存和订单同步，以验证在Adobe Commerce和商店履行解决方案之间是否正确同步了对挑库来源和库存的更新。

**功能区**:库存和订单同步</br>
**角色：** 管理员</br>
**测试类型：** 全部积极

<table>
<thead>
<tr>
<th>函数</th>
<th>测试方案</th>
<th>预期结果</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>添加装货货源</strong></td>
<td>保存新的装货库存来源。</td>
<td>实时同步会在5分钟内将源详细信息发送到WalmartGIF服务。</td>
</tr>
<tr>
<td><strong>更新现有的装箱库存来源</strong></td>
<td>保存对现有装货库存来源的更新。</td>
<td>实时同步操作会在5分钟内将详细信息发送到WalmartGIF</td>
</tr>
<tr>
<td><strong>装货货源</br><code>Is Synced</code> 状态</br><code>Is Synced</code></strong></td>
<td>保存对现有装货库存来源的更新。</td>
<td>成功操作后， <code>Is Synced</code> “管理源”页面的列从 <code>No</code> to <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>修改的库存预订流程</strong></td>
<td>为产品创建并提交新订单。</td>
<td>产品的可售量相应地减少。</td>
</tr>
<tr>
<td><strong>新订单推送、API同步 — 客户订单</strong></td>
<td>客户提交商店提货单。</td>
<td><ul><li>在“管理员订单”视图中， <strong>Adobe Commerce管理员用户</strong> 看到“订单同步”状态更新为 <code>Sent</code></li><li>订单详细信息日志包含该消息 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新订单推送、API同步 — 管理员提交订单</strong></td>
<td>安Adobe Commerce <strong>管理员</strong> 提交提货单。</td>
<td><ul><li>在“管理员订单”视图中，订单同步状态将更新为 <code>Sent</code>.</li><li>订单详细信息日志包含该消息 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新订单推送、例外队列<strong></td>
<td>在Adobe Commerce管理员中确定一些虚拟和可下载的产品，这些产品可通过Adobe Commerce完成，而无需与履行服务(FaaS)进行交互。</td>
<td>这些产品在导出中会被正确删除或标记，以防止与FaaS发生下游冲突。</td>
</tr>
</tbody>
</table>

### 订单取消工作流

测试计划的此部分包含用于测试通过Adobe Commerce取消的订单的端到端工作流的方案。

**功能区域：** Adobe Commerce管理员</br>
**角色：** 端到端（管理员、商店关联、客户）</br>
**测试结果类型：** 所有情况均为正数

<table style="table-layout:fixed">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>完全取消订单</strong></td>
<td><ol>
<li>下单。</li>
<li>等待顺序同步。</li>
<li>验证发票电子邮件的发票创建（如果授权并捕获）接收。</li>
<li>使用“发票”视图中的所有已订购产品创建贷项通知单。</li>
</ol>
</td>
<td>
<ul>
<td>
<li>订单历史记录更新为 <code>We refunded $X online. Transaction ID: transactionID</code> 和 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>订单状态为 <code>Closed</code>. （我们已设置PAYMENT REVIEW。）</li>
<li>在Adobe Commerce创建的贷项通知单。 （等到cron工作。）</li>
<li>如果已选取所有项目，则准备接收电子邮件 <code>DISPLAY COMMENT HISTORY</code> 显示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 标志 <code>true</code>.)</li>
<li>如果未选取所有项目，则会显示取消电子邮件和显示评论历史记录 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 标志 <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>部分订单取消<strong></td>
<td>
<ol>
<li>订购至少两个产品。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>等待两小时进行交易结算。</li>
<li>从“发票”视图中创建仅包含部分已订购产品的贷项通知单。</li>
</td>
<td>
<ul>
<li>订单历史记录更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>订单历史记录更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>收到订单退款电子邮件： <code>$x amount was refunded</code></li>
<li>订单状态为 <code>Processing</code>.</li>
<li>在Adobe Commerce中创建的贷项通知单（等到cron工作完成时再执行）。</li>
<li>如果未选取某些项目，请确认 [!UICONTROL Ready for Pickup] 将显示包含“nilpick or refund”部分的电子邮件。 <code>DISPLAY COMMENT HISTORY</code> 显示 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> 标志 <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>准备接收</br></br>完全取消</br>（所有产品均设置为已挑库，数量为0）</br></strong></td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>转到Postman，并在所有产品均设置为的情况下运行“准备提货”请求 <code>picked</code> with <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>订单历史记录已更新： <code>We refunded $X offline</code></li>
<li>订单状态为 <code>CLOSED</code>.
<li>将创建贷项通知单。 （等到cron工作。）</li>
<li>收到退款电子邮件： <code>$x amount was refunded</code></li>
<li>已发送订单取消电子邮件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>准备提货 — 部分取消</strong></br></br><strong>(有些产品被挑选，有些产品被挑选 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>转到Postman并运行“准备装货”请求，其中部分产品设置为已挑库，其中0个数量，其余部分已挑库。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>订单状态为“准备装货”。 </li>
<li>订单历史记录已更新： <code>We refunded $X offline.</code>
<li>订单历史记录已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到退款电子邮件： <code>$x amount was refunded</code>
<li>将创建贷项通知单。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>准备提货 — 部分取消</br></br>有些产品被挑选，有些产品被挑选 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>转到Postman并运行“准备装货”请求，其中部分产品设置为已挑库，其中0个数量，其余部分已挑库。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>订单状态为“准备装货”。 </li>
<li>订单历史记录已更新： <code>We refunded $X offline.</code>
<li>订单历史记录已更新： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到退款电子邮件： <code>$x amount was refunded</code>
<li>将创建贷项通知单。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期间） </br></br>完全取消（所有产品均设置为拒绝）</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>转到Postman并运行“准备提货”请求，并将所有产品都设置为已挑库。</li>
<li>打开您的邮箱，找到准备接收电子邮件。 然后，单击**[!UICONTROL Confirm Arrival]**。</li>
<li>签到。</li>
<li>转到Postman，并运行Sprifated请求以将所有产品设置为已拒绝。</li>
</ol>
<td><ul>
<li>订单历史记录已更新： <code>We refunded $X offline.</code></li>
<li>收到退款电子邮件： <code>$x amount was refunded</code></li>
<li>状态设置为 <code>CLOSED</code>.</li>
<li>已创建贷项通知单。 （等到cron工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期间）</br></br>部分取消</br>(一些产品分发；有些会被拒绝。)</strong>
</br></td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>转到Postman，并在所有产品均设置为已选中的情况下运行“准备提货”请求。</li>
<li>打开您的邮箱。 查找准备接收电子邮件，然后选择 <code>Confirm Arrival</code>.</li>
<li>签到。</li>
<li>转到Postman，并运行“已分配”请求，其中一些产品设置为已分配，另一些设置为已拒绝</li>
</ol>
</td>
<td>
<li>订单历史记录已更新： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>收到退款电子邮件： <code>$x amount was refunded</code>
<li>订单状态设置为 <code>Ready for pickup Dispensed</code>
<li>已创建贷项通知单。 （等到cron工作。）</li>
</td>
</tr>
<tr>
<td> <strong>退回后的新RMA（完整）</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>确认已创建发票（如果授权并捕获），并收到发票电子邮件。</li>
<li>选择所有带Postman的产品。</li>
<li>签到。</li>
<li>下药。</li>
<li>转到订单，然后选择<strong>[!UICONTROL Create returns]=
<li>创建RMA。</li>
</ol>
</td>
<td>
<ul>
<li>RMA已创建，显示在 <strong>[!UICONTROL Returns]</b> 选项卡。</li>
<li>客户收到RMA确认电子邮件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>退回后新RMA — 部分</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待顺序同步。</li>
<li>检查发票是否已创建（如果授权并捕获），并收到发票电子邮件。</li>
<li>选择所有带Postman的产品。</li>
<li>签到。</li>
<li>下药。</li>
<li>按顺序，然后选择  <strong>[!UICONTROL Create returns]</strong></li>
<li>使用部分订购产品创建RMA。</li>
</ol>
<td>
<ul>
<li>RMA创建并显示在 <strong>[!UICONTROL Returns]</strong> 选项卡。</li>
<li>客户收到了RMA确认电子邮件。</li>
<li>创建RMA后，获取RMA授权：从管理员中，转到 <strong>[!UICONTROL Sales > Returns]</strong>. 选择您创建并授权的RMA。</li>
<li>确认客户收到RMA授权确认电子邮件。</li>
<li>检查退款是否已添加到交易记录和订单历史记录中。</li>
</ul>
</td>
</tr>
</table>


### 商店履行应用程序权限

测试计划的此部分涵盖商店实施应用程序用户的帐户管理。

- 确认存储关联可以使用从Adobe Commerce管理员创建的新用户帐户进行身份验证。
- 确认已成功应用对现有帐户的更新。

**功能区域：** Adobe Commerce管理员</br>
**角色：** 管理员、商店关联</br>
**测试类型：** 全部积极

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>用户帐户管理 — 创建帐户</strong></br></br>
</td>
<td>
<ol>
<li><strong>管理员</strong>  — 登录Adobe Commerce管理员</li>
<li>转到 <strong>[!UICONTROL System] &gt;商店履行应用程序权限&gt;所有商店履行应用程序用户</strong></li>
<li><strong>添加新用户。</strong></li>
</ol>
<td>
<ul>
<li>帐户已成功创建。</li>
<li>新用户帐户显示在 [!UICONTROL Store Fulfillment Users] 功能板。</li>
<li><strong>存储关联</strong> 使用新的用户帐户登录到Store Assist应用程序。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>用户帐户管理 — 更新现有用户帐户</strong>
</td>
<td>
<ol>
<li>使用管理员用户帐户登录Adobe Commerce管理员。</li>
<li>转到 <strong>[!UICONTROL System] &gt;商店履行应用程序权限&gt;所有商店履行应用程序用户</strong>.</li>
<li>在用户帐户列表中，通过选择 <strong>[!UICONTROL Edit]</strong>.
<li>通过更改 <strong>[!UICONTROL Is Active]</strong> to <strong>否</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>在 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 功能板中，已更新帐户的状态更改为 <strong>[!UICONTROL Inactive]</strong>.</li>
<li>存储关联无法使用不活动的帐户凭据登录到存储协助应用程序。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce产品类型

Adobe Commerce产品类型的测试方案可验证客户是否看到不同产品类型的正确产品、库存和交付方法信息：

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] 在Adobe Commerce店。

**功能区域：** Adobe Commerce弗朗滕</br>
**角色：** 应用商店辅助用户（商店关联）</br>
**测试类型：** 全部积极

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>评论</th>
</tr>
<tr>
<td><strong>可配置产品</strong>
</td>
<td>
<ul>
<li>确认用户只能看到那些可配置的选项（已启用源、已分配库存以及存货中有某些物料），请检查子产品。</li>
<li>确认在选择其他商店时，不可用的选项显示为交叉。</li>
<li>确认如果用户选择不同的存储区，则可配置选项将被取消选中。</li>
<li>确认如果可配置产品已在购物车中，并且用户选择了不同的商店，则产品显示为无现货。</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>分组产品</strong>
</td>
<td>
<ul>
<li>验证投放方法和 [!UICONTROL Add to cart] 按钮，则当所有子产品都具有
<code>qty</code> 设置为 <code>0</code>.</li>
<li>确认在至少有一个子产品具有 <code>qty</code> 设置为 <code>0.</code></li>
<li>验证 [!UICONTROL Store Pickup Delivery] 方法仅对具有 [!UICONTROL Available for Store Pickup] 已启用。 （检查子产品。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>虚拟产品</strong>
</td>
<td>
验证虚拟产品是否未提供  [!UICONTROL In-store Pickup] 投放方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>捆绑产品</strong>
</td>
<td>
<ul>
<li>验证是否至少有一个子产品具有 [!UICONTROL Available for Store Pickup] 禁用后，客户无法使用“商店提货”交付选项。</li>
<li>验证是否至少有一个子产品具有 [!UICONTROL Available for Home Delivery] 禁用后，“主页交付”选项将不可用于客户。</li>
<li>验证捆绑包中至少有一个子产品无现货，该捆绑包（父产品）还显示为 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 签入体验

测试计划的此部分涵盖下列功能的“商店代理货位的签入体验”订单：

- 替代拾取联系人 — 验证添加 [!UICONTROL Alternate Pickup Contact] 和选择 [!UICONTROL Preferred Contact] 在商店提货单上。

- 签入表单 — 验证提交存货提货单签入请求的工作流。

**功能区：** 购物车结帐、存货提货单的签入表</br>
**角色：** 管理员、客户、商店关联</br>
**测试类型：** 全部积极

### 替代装货联系人


**功能区域：** 购物车结账</br>
**角色：** 客户</br>
**测试类型：** 全部积极

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>替代装货联系人</br>
签入</br><strong>
</td>
<td>
客户使用店内装货选项提交订单。</td>
<td>在结账过程中，客户会看到 [!UICONTROL Alternate Pickup Contact] 发运步骤中的选项。
</td>
</tr>
<tr>
<td><strong>备用装货首选联系人，签到</strong>
<td>
客户使用店内装货选项提交订单。 在结帐期间，客户会添加 [!UICONTROL Alternate Pickup Contact].</td>
<td>在结账过程中，客户会看到 [!UICONTROL Preferred Contact] 选项。</td>
</td>
</tr>
<tr>
<td><strong>备用提货联系人详细信息，签入</strong>
</td>
<td>
客户使用店内装货选项提交订单。 在结帐期间，客户会选择 [!UICONTROL Alternate Pickup Contact] 中，单击“Target Workbench”。
</td>
<td>客户将看到用于输入联系人详细信息的输入选项： [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]和 [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>备用提货，签到电子邮件</strong>
</td>
<td>客户使用店内装货选项提交订单。 在结帐期间，客户会选择 [!UICONTROL Alternate Pickup Contact] 在发运步骤中，添加联系人详细信息并提交订单。</td>
<td>客户和备用联系人都会收到订单的签到电子邮件。</td>
</tr>
<td><strong>备用装货、订单详细信息</strong></td>
<td>客户使用店内装货选项提交订单。 在结帐期间，客户会选择 [!UICONTROL Alternate Pickup Contact] 在发运步骤中，添加联系人详细信息并提交订单。</td>
<td>管理员会看到有关已保存订单的其他联系信息。</td>
</tr>
<tr>
<td><strong>替代装货联系人、存储关联订单视图</strong>
</td>
<td>客户使用店内装货选项提交订单。 在结帐期间，客户会选择 [!UICONTROL Alternate Pickup Contact] 在发运步骤中，添加联系人详细信息并提交订单。</td>
<td>Store Associate可以在FaaS/ChaaS中查看有关订单的其他联系信息。</td>
</td>
</tr>
</tbody>
</table>

### 签入表单


**功能区域：** 签入表单</br>
**角色：** 客户</br>
**测试类型：** 全部积极

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>签入操作 — 提交请求</strong>
</td>
<td>在签入表单中，客户填写所有必填字段并提交请求。</td>
<td>客户会收到成功响应。</td>
</tr>
<tr>
<td><strong>签入操作 — 查看请求详细信息</strong></td>
<td>客户成功提交签入请求。</td>
<td>订单状态在FaaS系统中更新，并且商店关联可以在FaaS中查看签入请求详细信息。
</td>
</tr>
<tr>
<td><strong>签入操作 — 仅提交一次请求</strong></td>
<td>在提交订单的签入请求后，客户将再次选择要签入的链接。</td>
<td>在“签入”窗体中，客户看不到用于编辑或重新提交表单的选项。</td>
</tr>
<tr>
<td><strong>签入操作 — 确认到达</strong></td>
<td>在FaaS中标记了店内取货订单，准备取货。 客户收到“准备提货”电子邮件，并选择 [!UICONTROL Confirm Arrival].</td>
<td>客户将看到订单的签入表单。</td>
</tr>
</tbody>
</table>

## 商店辅助应用程序

测试计划的此部分涵盖应用商店辅助应用程序中测试顺序、选择和切换工作流的方案。

**功能区域：** 商店辅助应用程序</br>
**角色：** 存储关联</br>
**测试类型：** 全部积极

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td>
<strong>单次领料快乐路径，卷边提货</strong></td>
<td>挑选单个和多数量的物料。 不吃尼尔鱼，也吃冰糖（有暂存）。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>多顺序挑选 — 快乐路径、曲边拾取</strong></td>
<td>单个和多数量项目。 不吃牛奶，吃牛奶（有暂存）</td>
<td></td>
</tr>
<tr>
<td><strong>单笔订单领料 — 店内快捷路径领料</strong></td>
<td>单个和多数量项目。 不吃牛，不吃牛，不吃牛（带暂存）</td>
<td>
</td>
</tr>
<tr>
<td><strong>多订单挑库 — 快乐路径、店内提货</strong></td>
<td>挑选单个和多数量的物料。 不吃尼尔鱼，也吃冰糖（有暂存）。</td>
<td></td>
</tr>
<tr>
<td><strong>单笔订单挑库 — 不快乐路径，店内提货</strong></td>
<td>挑选具有部分和零件的单个和多数量物料，然后在库内挑库（带暂存）</td>
</td>
<td></td>
</tr>
<td><strong>多订单挑库 — 不快乐的路径曲边拾取</strong></td>
<td>挑选具有部分和零件的单个和多数量物料，然后在库内挑库（带暂存）</td>
<td></td>
</tr>
<td><strong>单笔订单挑库 — 不快乐的路径，弯边提货</strong></td>
<td>挑选具有部分和零件的单件和多件物料，并进行边挑边（带暂存）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>已下订单 — 挑库前取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下单 — 切换前取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下订单 — 在订单模块中搜索</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>下单 — 搜索和手动签入以进行切换</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>已下订单 — 所有项目均未选取或未由选取器标记</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>通过捆绑项目下单 — 挑库和切换</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>下单 — 提交拒绝</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>下单 — 将所有物品拒绝交出</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>



## 部署

在验证解决方案已配置并测试到您的规范后，您便可以从暂存环境部署到生产环境。

部署和测试因您的基础架构和功能而异。

>[!TIP]
>
>有关云基础架构项目的Adobe Commerce部署准则、检查列表和最佳实践，请参阅 [部署您的商店](https://devdocs.magento.com/cloud/live/stage-prod-live.html) ，位于Adobe Commerce开发人员文档中。




















