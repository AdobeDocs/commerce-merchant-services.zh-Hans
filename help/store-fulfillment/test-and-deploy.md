---
title: 测试和部署存储履行
description: 测试计划，以验证Store Fulfillment功能。 测试包括“库存同步API”、已取消订单的端到端履行工作流、“商店履行”应用程序用户管理和客户登记体验。
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '2660'
ht-degree: 0%

---

# 测试和部署Adobe Commerce商店履行

在开发环境中完成载入流程后，您可以启动该流程以测试存储履行解决方案，并将其部署到生产环境。

**先决条件**

在测试或同步任何信息、商店或订单之前，请确认您已完成以下任务：

- 已完成 [常规配置](enable-general.md) 用于Store Fulfillment服务。

- [添加并验证沙盒和生产环境的帐户凭据和连接详细信息](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 确认 [Adobe Commerce集成](connect-set-up-service.md#configure-store-fulfillment-account-credentials) Store Fulfillment解决方案现已推出并获得授权。

## 准备测试

必须先完成连接配置，然后才能创建任何测试订单或执行集成测试。 在测试之前，还必须验证存储区数据是否已同步。

1. 同步存储履行来源。

   - 转到 **[!UICONTROL Stores > Sources]**.

   - 选择 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. 从商店网格中，验证是否已将商店标记为 `Synced` 创建测试订单之前。

## 示例测试计划

零售商在部署的配置和测试阶段验证Store Fulfillment解决方案的基本功能。 此示例测试计划提供了测试的起点。 根据您的要求添加其他方案。

>[!NOTE]
>
>在完成Store Fulfillment解决方案的初始载入或更新现有安装后，始终在部署到生产环境之前在非生产环境中测试应用程序。

此测试计划示例涵盖以下功能区域：

| 功能区域 | 函数 | 角色 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 库存和订单同步 | 清单API同步 | Adobe Commerce管理员 |
| 端到端 | 订单取消工作流 | 客户、管理员、商店关联 |
| 管理员 | 应用商店履行应用程序权限 | 管理员 |
| Adobe Commerce前端 | 产品类型 | 客户、管理员 |
| 前端结帐</br>签入表单 | 签入体验 | 客户、管理员 |
| 商店协助应用程序 | 订购</br>选取</br>暂存</br>和移交 | 商店关联 |

### 清单API同步

测试计划的此部分涵盖库存和订单同步，以验证提货来源和库存的更新是否在Adobe Commerce和“商店履行”解决方案之间正确同步。

**功能区域**：库存和订单同步</br>
**角色：** 管理员</br>
**测试类型：** 全部为正数

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
<td><strong>添加提货库存来源</strong></td>
<td>保存新的提货库存来源。</td>
<td>该实时同步程序会在5分钟内将源详细信息发送到沃尔玛GIF服务。</td>
</tr>
<tr>
<td><strong>更新现有的提货库存来源</strong></td>
<td>将更新保存到现有的提货库存来源。</td>
<td>实时同步操作会在5分钟内将详细信息发送给沃尔玛GIF</td>
</tr>
<tr>
<td><strong>提货库存来源</br><code>Is Synced</code> 状态</strong></td>
<td>将更新保存到现有的提货库存来源。</td>
<td>成功操作后， <code>Is Synced</code> “管理源”页更新所在的列 <code>No</code> 到 <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>已修改的库存预留流程</strong></td>
<td>为产品创建并提交新订单。</td>
<td>产品的可销售数量会相应减少。</td>
</tr>
<tr>
<td><strong>新订单推送、API同步 — 客户订单</strong></td>
<td>客户提交商店取货单。</td>
<td><ul><li>在“管理订单”视图中， <strong>Adobe Commerce管理员用户</strong> 订单同步状态更新为 <code>Sent</code></li><li>订单详细信息日志包含消息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新订单推送、API同步 — 管理员提交订单</strong></td>
<td>Adobe Commerce <strong>管理员</strong> 提交装货订单。</td>
<td><ul><li>在“管理订单”视图中，“订单同步”状态将更新为 <code>Sent</code>.</li><li>订单详细信息日志包含消息 <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新订单推送，例外队列<strong></td>
<td>确定Adobe Commerce管理员中的多种虚拟和可下载产品，这些产品可以通过Adobe Commerce完成，而无需与履行服务(FaaS)交互。</td>
<td>这些产品在导出时被适当删除或标记，以防止下游与FaaS冲突。</td>
</tr>
</tbody>
</table>

### 订单取消工作流

测试计划的此部分包含一些场景，用于测试通过Adobe Commerce取消的订单的端到端工作流。

**功能区域：** Adobe Commerce管理员</br>
**角色：** 端到端（管理员、商店助理、客户）</br>
**测试结果类型：** 对于所有方案为正

<table style="table-layout:fixed">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>全部订单取消</strong></td>
<td><ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>验证发票创建（如果授权并捕获）是否收到发票电子邮件。</li>
<li>从“发票”视图中使用所有订购的产品创建贷项通知单。</li>
</ol>
</td>
<td>
<ul>
<li>订单历史记录已更新 <code>We refunded $X online. Transaction ID: transactionID</code> 和 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>订单状态为 <code>Closed</code>. （我们现在已设置“付款复核”。）</li>
<li>在Adobe Commerce中创建的贷项通知单。 （等待cron正常工作。）</li>
<li>如果所有物料都已挑库，则准备好接收电子邮件 <code>DISPLAY COMMENT HISTORY</code> 显示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 标志为 <code>true</code>.)</li>
<li>如果所有物料均未挑库，则取消电子邮件和显示备注历史记录将显示 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 标志为 <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>部分订单取消<strong></td>
<td>
<ol>
<li>订购至少两件产品。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>等待两个小时进行交易结算。</li>
<li>从“发票”视图创建仅含部分订购产品的贷项通知单。</li>
</td>
<td>
<ul>
<li>订单历史记录更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>订单历史记录更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>订单退款接收电子邮件： <code>$x amount was refunded</code></li>
<li>订单状态为 <code>Processing</code>.</li>
<li>在Adobe Commerce中创建的贷项通知单（等待cron正常工作）。</li>
<li>如果某些物料未领料，请确认 [!UICONTROL Ready for Pickup] 将显示带有nil pick或refust节的电子邮件。 <code>DISPLAY COMMENT HISTORY</code> 显示 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> 标志为 <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>准备取车</br></br>完全取消</br>（所有产品均设置为0数量的“已挑库”）</strong></td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>转到Postman并运行准备好取货请求，将所有产品设置为 <code>picked</code> 替换为 <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>已更新订单历史记录： <code>We refunded $X offline</code></li>
<li>订单状态为 <code>CLOSED</code>.
<li>创建贷项通知单。 （等待cron正常工作。）</li>
<li>收到的退款电子邮件： <code>$x amount was refunded</code></li>
<li>已发送订单取消电子邮件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>准备提货 — 部分取消</strong></br></br><strong>(有些产品被挑库，有些产品被挑库 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>转到Postman并运行准备提货请求，其中部分产品设置为0数量且其余产品已挑库。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> 替换为 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>订单状态为“准备提货”。 </li>
<li>已更新订单历史记录： <code>We refunded $X offline.</code>
<li>已更新订单历史记录： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到的退款电子邮件： <code>$x amount was refunded</code>
<li>创建贷项通知单。 （等待cron正常工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>准备提货 — 部分取消</br></br>有些产品被挑库，有些产品被挑库 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>转到Postman并运行准备提货请求，其中部分产品设置为0数量且其余产品已挑库。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> 替换为 [!UICONTROL Ready for Pickup Items] 和 [!UICONTROL Canceled Items] 表格。 </li>
<li>订单状态为“准备提货”。 </li>
<li>已更新订单历史记录： <code>We refunded $X offline.</code>
<li>已更新订单历史记录： <code>Order notified as partly canceled at: Date and hour</code>
<li>收到的退款电子邮件： <code>$x amount was refunded</code>
<li>创建贷项通知单。 （等待cron正常工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期间） </br></br>完全取消（将所有产品都设置为已拒绝）</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>转到Postman并运行准备提货请求，将所有产品设置为已提货。</li>
<li>打开邮箱，找到“准备好取货”电子邮件。 然后，单击**[!UICONTROL Confirm Arrival]**。</li>
<li>签入。</li>
<li>转到Postman并运行Dispended请求，将所有产品设置为已拒绝。</li>
</ol>
<td><ul>
<li>已更新订单历史记录： <code>We refunded $X offline.</code></li>
<li>收到的退款电子邮件： <code>$x amount was refunded</code></li>
<li>状态设置为 <code>CLOSED</code>.</li>
<li>已创建贷项通知单。 （等待cron正常工作。）</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分配（分配期间）</br></br>部分取消</br>（某些产品已分发；某些产品被拒绝。）</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>转到Postman，运行准备提货请求，并将所有产品设置为已提货。</li>
<li>打开您的邮箱。 找到“准备好取车”电子邮件，然后选择 <code>Confirm Arrival</code>.</li>
<li>签入。</li>
<li>转到Postman，然后运行Dispensed请求，其中某些产品设置为dispensed，而某些产品设置为rejected</li>
</ol>
</td>
<td>
<li>已更新订单历史记录： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>收到的退款电子邮件： <code>$x amount was refunded</code>
<li>订单状态设置为 <code>Ready for pickup Dispensed</code>
<li>已创建贷项通知单。 （等待cron正常工作。）</li>
</td>
</tr>
<tr>
<td> <strong>返回后的新RMA（完整）</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>如果已配置授权和捕获选项，请验证发票是否已创建，以及客户是否已收到发票电子邮件。</li>
<li>用Postman选择所有产品。</li>
<li>签入。</li>
<li>做一个分配。</li>
<li>转到订单，然后选择<strong>[!UICONTROL Create returns]=
<li>创建RMA。</li>
</ol>
</td>
<td>
<ul>
<li>RMA已创建，并显示在 <strong>[!UICONTROL Returns]</b> 选项卡。</li>
<li>客户收到了RMA确认电子邮件。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>返回后的新RMA — 部分</strong>
</td>
<td>
<ol>
<li>下订单。</li>
<li>等待订单同步。</li>
<li>检查是否已创建发票（如果授权并捕获）以及是否收到发票电子邮件。</li>
<li>用Postman选择所有产品。</li>
<li>签入。</li>
<li>做一个分配。</li>
<li>转到订单，然后选择  <strong>[!UICONTROL Create returns]</strong></li>
<li>使用部分订购的产品创建RMA。</li>
</ol>
<td>
<ul>
<li>RMA已创建并显示在下面 <strong>[!UICONTROL Returns]</strong> 选项卡。</li>
<li>客户收到了RMA确认电子邮件。</li>
<li>创建RMA后，获取RMA授权：从管理员转到 <strong>[!UICONTROL Sales > Returns]</strong>. 选择您创建的RMA并为其授权。</li>
<li>验证客户是否收到了RMA授权确认电子邮件。</li>
<li>检查退款是否已添加至交易和订单历史记录。</li>
</ul>
</td>
</tr>
</table>


### 应用商店履行应用程序权限

测试计划的这一部分涵盖了商店履行应用程序用户的帐户管理。

- 确认应用商店关联可以使用从Adobe Commerce管理员创建的新用户帐户进行身份验证。
- 确认已成功应用对现有帐户的更新。

**功能区域：** Adobe Commerce管理员</br>
**角色：** 管理员、商店关联</br>
**测试类型：** 全部为正数

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
<li>已成功创建帐户。</li>
<li>新用户帐户将显示在 [!UICONTROL Store Fulfillment Users] 仪表板。</li>
<li><strong>商店关联</strong> 使用新用户帐户登录“商店助手”应用程序。</li>
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
<li>在“用户帐户”列表中，通过选择以打开现有的活动用户帐户 <strong>[!UICONTROL Edit]</strong>.
<li>通过更改禁用帐户 <strong>[!UICONTROL Is Active]</strong> 到 <strong>否</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>在 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 仪表板，已更新帐户的状态已更改为 <strong>[!UICONTROL Inactive]</strong>.</li>
<li>应用商店关联无法使用非活动帐户凭据登录到“应用商店助手”应用程序。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce产品类型

Adobe Commerce产品类型的测试方案将验证客户是否可以看到不同产品类型的正确产品、库存和交付方法信息：

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] 在Adobe Commerce店面。

**功能区域：** Adobe Commerce前端</br>
**角色：** 商店协助应用用户（商店关联）</br>
**测试类型：** 全部为正数

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>注释</th>
</tr>
<tr>
<td><strong>可配置产品</strong>
</td>
<td>
<ul>
<li>验证用户是否只能看到这些可配置选项（哪个来源已启用、库存已分配以及库存中有某些项目），并检查子产品。</li>
<li>验证在选择其他存储时，不可用的选项是否显示为已划出。</li>
<li>验证如果用户选择不同的商店，可配置的选项是否未选中。</li>
<li>验证如果可配置产品已在购物车中，并且用户选择其他商店，则产品将显示为缺货。</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>分组的产品</strong>
</td>
<td>
<ul>
<li>验证投放方法和 [!UICONTROL Add to cart] 当所有子产品都具有
<code>qty</code> 设置为 <code>0</code>.</li>
<li>验证是否为客户启用了交货方法，前提是至少有一个子产品具有 <code>qty</code> 设置为 <code>0.</code></li>
<li>验证 [!UICONTROL Store Pickup Delivery] 方法仅对具有以下特性的产品可见和有效： [!UICONTROL Available for Store Pickup] 已启用。 （检查子产品。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>虚拟产品</strong>
</td>
<td>
验证虚拟产品是否不提供  [!UICONTROL In-store Pickup] 投放方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>捆绑产品</strong>
</td>
<td>
<ul>
<li>验证是否至少有一个子产品具有 [!UICONTROL Available for Store Pickup] 禁用，客户无法使用“商店取货”交货选项。</li>
<li>验证是否至少有一个子产品具有 [!UICONTROL Available for Home Delivery] 禁用，Home Delivery选项不适用于客户。</li>
<li>验证捆绑包中是否至少有一个子产品缺货，捆绑包（父产品）也显示为 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 签入体验

测试计划的此部分介绍了以下功能的商店提货订单登记体验：

- 备用提货联系人 — 验证用于添加 [!UICONTROL Alternate Pickup Contact] 并选择一个 [!UICONTROL Preferred Contact] 在商店提货单上。

- 签入表单 — 验证用于提交商店装货订单的签入请求的工作流。

**功能领域：** 购物车结帐、商店取货订单的登记表</br>
**角色：** 管理员、客户、商店关联</br>
**测试类型：** 全部为正数

### 备用取车联系人


**功能区域：** 购物车结帐</br>
**角色：** 客户</br>
**测试类型：** 全部为正数

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>备用取车联系人</br>
签入<strong>
</td>
<td>
客户提交带有“店内提货”选项的订单。</td>
<td>在结账过程中，客户会看到 [!UICONTROL Alternate Pickup Contact] “配送”步骤上的选项。
</td>
</tr>
<tr>
<td><strong>备用代答首选联系人，登记入住</strong>
<td>
客户提交带有“店内提货”选项的订单。 在结账过程中，客户添加 [!UICONTROL Alternate Pickup Contact].</td>
<td>在结账过程中，客户会看到 [!UICONTROL Preferred Contact] 配送步骤中的选项。</td>
</td>
</tr>
<tr>
<td><strong>备用取车联系人详细信息，登记入住</strong>
</td>
<td>
客户提交带有“店内提货”选项的订单。 在结账过程中，客户选择 [!UICONTROL Alternate Pickup Contact] 在送货步骤中。
</td>
<td>客户会看到输入选项以输入联系人详细信息： [!UICONTROL First name]， [!UICONTROL Last name]， [!UICONTROL Phone]、和 [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>备用接送、登记电子邮件</strong>
</td>
<td>客户提交带有“店内提货”选项的订单。 在结账过程中，客户选择 [!UICONTROL Alternate Pickup Contact] 在配送步骤中，添加联系人详细信息并提交订单。</td>
<td>客户和备用联系人都会收到订单的登记电子邮件。</td>
</tr>
<td><strong>替代提货，订单详细信息</strong></td>
<td>客户提交带有“店内提货”选项的订单。 在结账过程中，客户选择 [!UICONTROL Alternate Pickup Contact] 在配送步骤中，添加联系人详细信息并提交订单。</td>
<td>管理员会看到已保存订单上的其他联系信息。</td>
</tr>
<tr>
<td><strong>替代提货联系人、“商店关联”订单视图</strong>
</td>
<td>客户提交带有“店内提货”选项的订单。 在结账过程中，客户选择 [!UICONTROL Alternate Pickup Contact] 在配送步骤中，添加联系人详细信息并提交订单。</td>
<td>“商店关联”可以在FaaS/ChaaS中查看订单上的其他联系信息。</td>
</td>
</tr>
</tbody>
</table>

### 签入表单


**功能区域：** 签入表单</br>
**角色：** 客户</br>
**测试类型：** 全部为正数

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td><strong>签入操作 — 提交请求</strong>
</td>
<td>在签到表单中，客户填写所有必填字段，并提交请求。</td>
<td>客户收到成功响应。</td>
</tr>
<tr>
<td><strong>签入操作 — 查看请求详细信息</strong></td>
<td>客户已成功提交签入请求。</td>
<td>订单状态会在FaaS系统中更新，且“商店关联”可以在FaaS中查看签入请求详细信息。
</td>
</tr>
<tr>
<td><strong>签入操作 — 仅提交请求一次</strong></td>
<td>在提交订单的登记请求后，客户会选择链接以再次登记。</td>
<td>在“检入”表单上，客户看不到用于编辑或重新提交表单的选项。</td>
</tr>
<tr>
<td><strong>签入操作 — 确认到达</strong></td>
<td>店内取货订单已标记为可在FaaS中取货。 客户收到“准备好取货”电子邮件，并选择 [!UICONTROL Confirm Arrival].</td>
<td>客户看到订单的“登记”表格。</td>
</tr>
</tbody>
</table>

## 商店助手应用程序

测试计划的此部分介绍了应用商店助手应用程序中测试订单、挑选和移交工作流的场景。

**功能区域：** 商店协助应用程序</br>
**角色：** 商店关联</br>
**测试类型：** 全部为正数

<table style="table-layout:auto">
<tr>
<th>函数</th>
<th>方案</th>
<th>预期结果</th>
</tr>
<tr>
<td>
<strong>单订单提货 — 路线愉快，路边提货</strong></td>
<td>挑选单个和多数量物料。 无零挑选，路边提货（带暂存设备）。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>多订单挑库 — 快乐路径、路边挑库</strong></td>
<td>单个和多数量物料。 无nil pick和路边取车（带暂存）</td>
<td></td>
</tr>
<tr>
<td><strong>单订单提货 — 店内提货的快乐路径</strong></td>
<td>单个和多数量物料。 无nil pick和店内提货（带暂存）</td>
<td>
</td>
</tr>
<tr>
<td><strong>多订单领料 — 快乐路径、店内领料</strong></td>
<td>挑选单个和多数量物料。 无零挑选，路边提货（带暂存设备）。</td>
<td></td>
</tr>
<tr>
<td><strong>单次捡料 — 路径不愉快，店内捡料</strong></td>
<td>挑选单个和多数量物料，包括部分挑库和零挑库以及店内提货（含暂存）</td>
</td>
<td></td>
</tr>
<td><strong>多订单领料 — 不满意路边领料</strong></td>
<td>挑选单个和多数量物料，包括部分挑库和零挑库以及店内提货（含暂存）</td>
<td></td>
</tr>
<td><strong>单订单提货 — 路径不愉快，路边提货</strong></td>
<td>挑选单个和多数量物料，包括部分挑库和分段挑库（含暂存）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>下订单 — 领料前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下单 — 移交前已取消</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>下订单 — 按订单搜索模块</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>下订单 — 搜索和手动签入以进行移交</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>订单已下达 — 挑库器未挑库或标记不可用的所有物料</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>使用捆绑项目下达的订单 — 领料和移交</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>已下达订单 — 已下达但被拒绝</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>下达的订单 — 已下达但拒绝所有物料</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## 部署

在验证解决方案已配置并且已按照您的规范测试后，您便可以从暂存部署到生产。

部署和测试因您的基础架构和功能而异。

>[!TIP]
>
>有关Adobe Commerce在云基础架构项目中的部署准则、核对清单和最佳实践，请参阅 [部署您的商店](https://devdocs.magento.com/cloud/live/stage-prod-live.html) 在Adobe Commerce开发人员文档中。
