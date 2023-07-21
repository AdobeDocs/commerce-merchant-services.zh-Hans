---
title: 销售电子邮件模板
description: 配置事务型电子邮件模板，以便在完成商店提货订单的过程中与客户和商店管理员进行通信。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# 销售电子邮件模板

存储履行提供一组扩展的事务性电子邮件模板，以支持订单和履行工作流。 它们跨渠道提供一致的自动化通信和消息传递 — 通知客户和商店管理员订单状态更改、店内接单指令等。

使用默认消息传递和设置配置商店履行电子邮件模板。 Adobe Commerce中的商家管理员可以管理和修改配置，并选择电子邮件模板以在不同场景中与客户通信。 管理员还可以配置和自定义模板。

从管理员处配置销售电子邮件模板： **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

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
<td>禁用此功能。 不支持异步电子邮件发送。 为了使“商店提货”的通信速度和响应速度最快，请立即发送电子邮件，而不是成批发送。 </td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>

## 订单已准备好在商店中提货

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
<td>当店员完成挑选订单后，会向客户发送此电子邮件。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止商店关联人员选择订单。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单已准备好接收电子邮件发件人</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单准备取货电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<td><strong>来宾的订单准备取货电子邮件模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>备用取货联系人的订单准备取货电子邮件模板</strong></td>
<td>用于通知订单中列出的其他联系人的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将订单准备取货电子邮件副本发送至</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单准备取货电子邮件复制方法</strong></td>
<td>要使用的电子邮件复制方法（抄送）。</td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>


## 订单已在商店中领取

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
<td>当客户确认他们已从商店中取回订单时，会向客户发送此电子邮件。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止客户提取订单。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单已提取电子邮件发件人</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单已提取电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 默认模板随集成一起提供</td>
<td>商店视图</td>
<td>否</td>
</tr>
<td><strong>已提取访客的订单电子邮件模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送已提取电子邮件副本至</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送已选取电子邮件复制方法</strong></td>
<td>要使用的电子邮件复制方法（抄送）。</td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>

## 订单已延迟

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
<td>此电子邮件将发送给客户，以通知他们在商户商店处理或领取订单时出现延迟。 设置为“否”可禁用电子邮件通知。 如果禁用了电子邮件模板，则功能不会阻止订单延迟。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单延迟的电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>订单延迟电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<td><strong>来宾的订单延迟电子邮件模板</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将订单延迟电子邮件副本发送至</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送订单延迟复制方法</strong></td>
<td>要使用的电子邮件复制方法（抄送）。</td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>



## 订单已取消

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
<td>此电子邮件将发送给客户，以通知他们在商户商店的订单已被取消。 设置为 <code>No</code> 禁用电子邮件通知。 如果禁用了电子邮件模板，则此功能不会阻止取消订单。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消订单的电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已取消订单的电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<td><strong>已取消访客的订单</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将已取消订单的电子邮件副本发送至</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送已取消订单的复制方法</strong></td>
<td>要使用的电子邮件复制方法（抄送）。</td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>


## 部分取消的订单

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
<td>此电子邮件将发送给客户，以通知他们在商户商店取消了部分订单。 设置为 <code>No</code> 禁用电子邮件通知。 如果禁用了电子邮件模板，则不会阻止部分取消订单。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的订单电子邮件发件人
</strong></td>
<td>发送电子邮件通知时使用的发件人身份。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>部分取消的订单电子邮件模板</strong></td>
<td>用于通知注册客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<td><strong>备用提货联系人的订单部分取消的电子邮件模板</strong></td>
<td>用于通知订单中列出的其他联系人的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>已部分取消访客的订单</strong></td>
<td>用于通知来宾客户的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>将部分取消的订单电子邮件副本发送至</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>发送部分取消的订单复制方法</strong></td>
<td>要使用的电子邮件复制方法（抄送）。</td>
<td>商店视图</td>
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
<td><strong>订单具有收货商店产品电子邮件发件人</strong></td>
<td>将发送给指定商家人员的电子邮件作为所有未结订单的汇总报表，这些订单在商家商店的库存可用之前无法挑库。 </br></br> 商家可以使用此报表来起动和管理商店到商店的库存转移或补充。 </br></br>此通知仅在 [!DNL Ship-to-Store] 功能已启用。
</br></br>此标签不会影响所选的装运承运人或其可用的装运方法标签。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>收货方存储电子邮件收件人</strong></td>
<td>以逗号分隔的电子邮件地址列表，用于发送每个通知的副本。</td>
<td>商店视图</td>
<td>否</td>
</tr>
<tr>
<td><strong>电子邮件模板</strong></td>
<td>用于通知收件人的电子邮件模板。 随集成一起提供了一个默认模板。</td>
<td>商店视图</td>
<td>否</td>
</tr>
</tbody></table>

>[!NOTE]
>
>如果您允许延交订单，则必须提供管理员电子邮件地址来接收有关这些订单的通知。 将地址添加到以下配置设置： **[!UICONTROL Send Order Delayed Email Copy To]** 在 [订单延迟](#order-delayed) 模板，和 [!UICONTROL Ship To Store Email Recipients] 在 [收货商店](#ship-to-store) 模板。



