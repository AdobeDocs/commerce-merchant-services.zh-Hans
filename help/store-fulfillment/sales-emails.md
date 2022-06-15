---
title: 销售电子邮件
description: 配置事务型电子邮件模板，以便在“商店提货单”的履行过程中与客户和商店管理员通信。
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# 销售电子邮件

存储履行提供了一组扩展的事务型电子邮件模板，用于支持订单和履行工作流。 它们提供跨渠道的一致、自动通信和消息传送 — 通知客户和商店管理员订单状态更改、店内提货单的说明等。

商店履行电子邮件模板配置了默认消息和设置。 Adobe Commerce中的商户管理员可以管理和修改配置，并选择电子邮件模板以在不同情况下与客户通信。 管理员还可以配置和自定义模板。

从管理员配置销售电子邮件模板： **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## 电子邮件 — 常规设置

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>异步发送</strong></td>
<td>禁用此功能。 不支持异步电子邮件发送。 为获得存储拾取的最快通信和响应时间，请立即发送电子邮件，而不是对其进行批量处理。 </td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>

## 准备在商店中取货

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已启用</strong></td>
<td>当商店关联完成领料订单时，此电子邮件会发送给客户。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止商店关联人员选取订单。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订购准备接收电子邮件发件人</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>准备接收电子邮件模板的订单</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>为来宾准备接收电子邮件模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>为替代提货联系人准备提货电子邮件模板</strong></td>
<td>用于通知订单中名为的其他联系人的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单以准备接收电子邮件副本至</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单以准备接收电子邮件复制方法</strong></td>
<td>电子邮件“Carbon Copy”的方法发送给使用。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>


## 已在商店中提取订单

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已启用</strong></td>
<td>当客户确认已从商店取得订单时，系统会向客户发送此电子邮件。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止客户提取订单。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单已接收电子邮件发件人</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已提取订单电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成提供了默认模板</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>已为来宾接收“电子邮件”模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>“发送”已接收电子邮件副本，请</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>“发送”已被接收电子邮件复制方法</strong></td>
<td>发送给使用的电子邮件“Carbon Copy”的方法。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>

## 订单延迟

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已启用</strong></td>
<td>此电子邮件会发送给客户，以告知客户在商家商店处理或领取订单时出现延迟。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则功能不会阻止订单延迟。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订购延迟的电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订购延迟的电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>为来宾订购延迟的电子邮件模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将订单延迟的电子邮件副本发送到</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单延迟复制方法</strong></td>
<td>发送给使用的电子邮件“Carbon Copy”的方法。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>



## 已取消订单

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已启用</strong></td>
<td>此电子邮件将发送给客户，以通知他们在商店的订单已取消。 设置为 <code>No</code> 禁用电子邮件通知。 如果禁用了电子邮件模板，则该功能不会阻止取消订单。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单已取消电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消订单的电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>已取消来宾订单</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将已取消的订单电子邮件副本发送到</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单取消复制方法</strong></td>
<td>发送给使用的电子邮件“Carbon Copy”的方法。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>


## 部分取消订单

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>已启用</strong></td>
<td>此电子邮件将发送给客户，以通知客户其部分订单已在商店取消。 设置为 <code>No</code> 禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止订单被部分取消。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订购部分取消的电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的订单电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<td><strong>订购部分取消的替代提货联系人电子邮件模板</strong></td>
<td>用于通知订单中名为的其他联系人的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已部分取消对来宾的订购</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将部分取消的订单电子邮件副本发送到</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单部分取消的复制方法</strong></td>
<td>发送给使用的电子邮件“Carbon Copy”的方法。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>

## 收货商店

<table>
<thead>
<tr>
<th><strong>字段</strong></th>
<th><strong>描述</strong></th>
<th><strong>范围</strong></th>
<th><strong>必需</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>订单有收货商店产品电子邮件发件人</strong></td>
<td>发送给指定商家人员的电子邮件作为所有未结订单的汇总报表，在商家商店中，这些订单在库存可用之前无法被挑选。 </br></br> 商户可以使用此报表来启动和管理商店到商店的库存转移或补充。 </br></br>此通知仅在 [!DNL Ship-to-Store] 功能。
</br></br>此标签不影响所选装运承运人或其可用的装运方法标签。</br></br></td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>收货商店电子邮件收件人</strong></td>
<td>用于发送每个通知副本的电子邮件地址列表（以逗号分隔）。</td>
<td>存储视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>电子邮件模板</strong></td>
<td>用于通知收件人的电子邮件模板。 随集成提供了默认模板。</td>
<td>存储视图</td>
<td>否</td>
</tr>
</tbody></table>

>[!NOTE]
>
>如果允许延交订单，则必须提供管理员电子邮件地址以接收有关这些订单的通知。 将地址添加到以下配置设置： **[!UICONTROL Send Order Delayed Email Copy To]** 在 [订单延迟](#order-delayed) 模板和 [!UICONTROL Ship To Store Email Recipients] 在 [收货商店](#ship-to-store) 模板。



