---
title: Azure Monitor 中的 Azure Active Directory 活动日志（预览版）| Microsoft Docs
description: Azure Monitor 中的 Azure Active Directory 活动日志（预览版）简介
services: active-directory
documentationcenter: ''
author: priyamohanram
manager: daveba
editor: ''
ms.assetid: 4b18127b-d1d0-4bdc-8f9c-6a4c991c5f75
ms.service: active-directory
ms.devlang: na
ms.topic: concept
ms.tgt_pltfrm: na
ms.workload: identity
ms.subservice: report-monitor
ms.date: 11/13/2018
ms.author: priyamo
ms.reviewer: dhanyahk
ms.openlocfilehash: 4bbe436632b2fac91658292f33ce391eea090412
ms.sourcegitcommit: d3200828266321847643f06c65a0698c4d6234da
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2019
ms.locfileid: "55169716"
---
# <a name="azure-ad-activity-logs-in-azure-monitor-preview"></a><span data-ttu-id="1e19a-103">Azure Monitor 中的 Azure AD 活动日志（预览版）</span><span class="sxs-lookup"><span data-stu-id="1e19a-103">Azure AD activity logs in Azure Monitor (preview)</span></span>

<span data-ttu-id="1e19a-104">现在可以将 Azure Active Directory (Azure AD) 活动日志路由到多个终结点以便长期保留以及获取数据见解。</span><span class="sxs-lookup"><span data-stu-id="1e19a-104">You can now route Azure Active Directory (Azure AD) activity logs to several endpoints for long term retention and data insights.</span></span> <span data-ttu-id="1e19a-105">使用 Azure Monitor 中的 Azure AD 日志公共预览版可以：</span><span class="sxs-lookup"><span data-stu-id="1e19a-105">The public preview of Azure AD logs in Azure Monitor allows you to:</span></span>

* <span data-ttu-id="1e19a-106">将 Azure AD 活动日志存档到 Azure 存储帐户，以便长期保留数据</span><span class="sxs-lookup"><span data-stu-id="1e19a-106">Archive Azure AD activity logs to an Azure storage account, to retain the data for a long time.</span></span>
* <span data-ttu-id="1e19a-107">使用常用的安全信息和事件管理 (SIEM) 工具（例如 Splunk 和 QRadar）将 Azure AD 活动日志流式传输到 Azure 事件中心进行分析。</span><span class="sxs-lookup"><span data-stu-id="1e19a-107">Stream Azure AD activity logs to an Azure event hub for analytics, using popular Security Information and Event Management (SIEM) tools, such as Splunk and QRadar.</span></span>
* <span data-ttu-id="1e19a-108">将 Azure AD 活动日志流式传输到事件中心，以便与自定义日志解决方案集成。</span><span class="sxs-lookup"><span data-stu-id="1e19a-108">Integrate Azure AD activity logs with your own custom log solutions by streaming them to an event hub.</span></span>
* <span data-ttu-id="1e19a-109">将 Azure AD 活动日志发送到 Log Analytics，以启用丰富的可视化效果以及对连接数据的监视和警报。</span><span class="sxs-lookup"><span data-stu-id="1e19a-109">Send Azure AD activity logs to Log Analytics to enable rich visualizations, monitoring and alerting on the connected data.</span></span>

> [!VIDEO https://www.youtube.com/embed/syT-9KNfug8]

## <a name="supported-reports"></a><span data-ttu-id="1e19a-110">支持的报表</span><span class="sxs-lookup"><span data-stu-id="1e19a-110">Supported reports</span></span>

<span data-ttu-id="1e19a-111">可以使用此功能将 Azure AD 活动日志和登录日志路由到 Azure 存储帐户、事件中心、Log Analytics 或自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="1e19a-111">You can route Azure AD audit logs and sign-in logs to your Azure storage account, event hub, Log Analytics or custom solution by using this feature.</span></span> 

* <span data-ttu-id="1e19a-112">**审核日志**：可通过[审核日志活动报表](concept-audit-logs.md)访问在租户中执行的每个任务的历史记录。</span><span class="sxs-lookup"><span data-stu-id="1e19a-112">**Audit logs**: The [audit logs activity report](concept-audit-logs.md) gives you access to the history of every task that's performed in your tenant.</span></span>
* <span data-ttu-id="1e19a-113">**登录日志**：可通过[登录活动报表](concept-sign-ins.md)来确定谁执行了审核日志中报告的任务。</span><span class="sxs-lookup"><span data-stu-id="1e19a-113">**Sign-in logs**: With the [sign-in activity report](concept-sign-ins.md), you can determine who performed the tasks that are reported in the audit logs.</span></span>

> [!NOTE]
> <span data-ttu-id="1e19a-114">目前不支持 B2C 相关的审核和登录活动日志。</span><span class="sxs-lookup"><span data-stu-id="1e19a-114">B2C-related audit and sign-in activity logs are not supported at this time.</span></span>
>

## <a name="prerequisites"></a><span data-ttu-id="1e19a-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="1e19a-115">Prerequisites</span></span>

<span data-ttu-id="1e19a-116">若要使用此功能，需满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="1e19a-116">To use this feature, you need:</span></span>

* <span data-ttu-id="1e19a-117">Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="1e19a-117">An Azure subscription.</span></span> <span data-ttu-id="1e19a-118">如果没有 Azure 订阅，可以[注册免费试用版](https://azure.microsoft.com/free/)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-118">If you don't have an Azure subscription, you can [sign up for a free trial](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="1e19a-119">在 Azure 门户中访问 Azure AD 审核日志所需的 Azure AD Free、Basic、Premium 1 或 Premium 2 [许可证](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-119">Azure AD Free, Basic, Premium 1, or Premium 2 [license](https://azure.microsoft.com/pricing/details/active-directory/), to access the Azure AD audit logs in the Azure portal.</span></span> 
* <span data-ttu-id="1e19a-120">Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="1e19a-120">An Azure AD tenant.</span></span>
* <span data-ttu-id="1e19a-121">一个是 Azure AD 租户的全局管理员或安全管理员的用户。</span><span class="sxs-lookup"><span data-stu-id="1e19a-121">A user who's a **global administrator** or **security administrator** for the Azure AD tenant.</span></span>
* <span data-ttu-id="1e19a-122">在 Azure 门户中访问 Azure AD 登录日志所需的 Azure AD Premium 1 或 Premium 2 [许可证](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-122">Azure AD Premium 1, or Premium 2 [license](https://azure.microsoft.com/pricing/details/active-directory/), to access the Azure AD sign-in logs in the Azure portal.</span></span> 

<span data-ttu-id="1e19a-123">根据审核日志数据要路由到的位置，需满足以下条件之一:</span><span class="sxs-lookup"><span data-stu-id="1e19a-123">Depending on where you want to route the audit log data, you need either of the following:</span></span>

* <span data-ttu-id="1e19a-124">你对其拥有 *ListKeys* 权限的 Azure 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="1e19a-124">An Azure storage account that you have *ListKeys* permissions for.</span></span> <span data-ttu-id="1e19a-125">建议使用常规存储帐户而非 Blob 存储帐户。</span><span class="sxs-lookup"><span data-stu-id="1e19a-125">We recommend that you use a general storage account and not a Blob storage account.</span></span> <span data-ttu-id="1e19a-126">有关存储定价信息，请查看 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/calculator/?service=storage)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-126">For storage pricing information, see the [Azure Storage pricing calculator](https://azure.microsoft.com/pricing/calculator/?service=storage).</span></span> 
* <span data-ttu-id="1e19a-127">用于与第三方解决方案集成的 Azure 事件中心命名空间。</span><span class="sxs-lookup"><span data-stu-id="1e19a-127">An Azure Event Hubs namespace to integrate with third-party solutions.</span></span>
* <span data-ttu-id="1e19a-128">用于将日志发送到 Log Analytics 的 Azure Log Analytics 工作区。</span><span class="sxs-lookup"><span data-stu-id="1e19a-128">An Azure Log Analytics workspace to send logs to Log Analytics.</span></span>

## <a name="cost-considerations"></a><span data-ttu-id="1e19a-129">成本注意事项</span><span class="sxs-lookup"><span data-stu-id="1e19a-129">Cost considerations</span></span>

<span data-ttu-id="1e19a-130">如果已经有 Azure AD 许可证，则还需要一个 Azure 订阅才能设置存储帐户和事件中心。</span><span class="sxs-lookup"><span data-stu-id="1e19a-130">If you already have an Azure AD license, you need an Azure subscription to set up the storage account and event hub.</span></span> <span data-ttu-id="1e19a-131">Azure 订阅可以免费获取，但若要使用 Azure 资源（包括用于存档的存储帐户以及用于流式处理的事件中心），则需付费。</span><span class="sxs-lookup"><span data-stu-id="1e19a-131">The Azure subscription comes at no cost, but you have to pay to utilize Azure resources, including the storage account that you use for archival and the event hub that you use for streaming.</span></span> <span data-ttu-id="1e19a-132">数据量以及因此引发的费用可能因租户大小的不同而差异很大。</span><span class="sxs-lookup"><span data-stu-id="1e19a-132">The amount of data and, thus, the cost incurred, can vary significantly depending on the tenant size.</span></span> 

### <a name="storage-size-for-activity-logs"></a><span data-ttu-id="1e19a-133">用于活动日志的存储大小</span><span class="sxs-lookup"><span data-stu-id="1e19a-133">Storage size for activity logs</span></span>

<span data-ttu-id="1e19a-134">每个审核日志事件使用大约 2 KB 的数据存储。</span><span class="sxs-lookup"><span data-stu-id="1e19a-134">Every audit log event uses about 2 KB of data storage.</span></span> <span data-ttu-id="1e19a-135">如果一个租户有 100,000 个用户，每天会引发大约 150 万个事件，则每天需要大约 3 GB 的数据存储。</span><span class="sxs-lookup"><span data-stu-id="1e19a-135">For a tenant with 100,000 users, which would incur about 1.5 million events per day, you would need about 3 GB of data storage per day.</span></span> <span data-ttu-id="1e19a-136">由于写入时每批需要大约五分钟的时间，则可预计每月大约有 9,000 次写入操作。</span><span class="sxs-lookup"><span data-stu-id="1e19a-136">Because writes occur in approximately five-minute batches, you can anticipate approximately 9,000 write operations per month.</span></span> 

<span data-ttu-id="1e19a-137">下表包含的内容是根据租户大小进行的成本估算。这是一个常规用途的 v2 存储帐户，位于“美国西部”区域，保留期至少为一年。</span><span class="sxs-lookup"><span data-stu-id="1e19a-137">The following table contains a cost estimate of, depending on the size of the tenant, a general-purpose v2 storage account in West US for at least one year of retention.</span></span> <span data-ttu-id="1e19a-138">若要针对应用程序的预期数据量进行更准确的估算，请使用 [Azure 存储定价计算器](https://azure.microsoft.com/pricing/details/storage/blobs/)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-138">To create a more accurate estimate for the data volume that you anticipate for your application, use the [Azure storage pricing calculator](https://azure.microsoft.com/pricing/details/storage/blobs/).</span></span> 

| <span data-ttu-id="1e19a-139">日志类别</span><span class="sxs-lookup"><span data-stu-id="1e19a-139">Log category</span></span> | <span data-ttu-id="1e19a-140">用户数</span><span class="sxs-lookup"><span data-stu-id="1e19a-140">Number of users</span></span> | <span data-ttu-id="1e19a-141">每日事件数</span><span class="sxs-lookup"><span data-stu-id="1e19a-141">Events per day</span></span> | <span data-ttu-id="1e19a-142">每月数据量（估算）</span><span class="sxs-lookup"><span data-stu-id="1e19a-142">Volume of data per month (est.)</span></span> | <span data-ttu-id="1e19a-143">每月成本（估算）</span><span class="sxs-lookup"><span data-stu-id="1e19a-143">Cost per month (est.)</span></span> | <span data-ttu-id="1e19a-144">每年成本（估算）</span><span class="sxs-lookup"><span data-stu-id="1e19a-144">Cost per year (est.)</span></span> |
|--------------|-----------------|----------------------|--------------------------------------|----------------------------|---------------------------|
| <span data-ttu-id="1e19a-145">审核</span><span class="sxs-lookup"><span data-stu-id="1e19a-145">Audit</span></span> | <span data-ttu-id="1e19a-146">100,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-146">100,000</span></span> | <span data-ttu-id="1e19a-147">150&nbsp;万</span><span class="sxs-lookup"><span data-stu-id="1e19a-147">1.5&nbsp;million</span></span> | <span data-ttu-id="1e19a-148">90 GB</span><span class="sxs-lookup"><span data-stu-id="1e19a-148">90 GB</span></span> | <span data-ttu-id="1e19a-149">$1.93</span><span class="sxs-lookup"><span data-stu-id="1e19a-149">$1.93</span></span> | <span data-ttu-id="1e19a-150">$23.12</span><span class="sxs-lookup"><span data-stu-id="1e19a-150">$23.12</span></span> |
| <span data-ttu-id="1e19a-151">审核</span><span class="sxs-lookup"><span data-stu-id="1e19a-151">Audit</span></span> | <span data-ttu-id="1e19a-152">1,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-152">1,000</span></span> | <span data-ttu-id="1e19a-153">15,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-153">15,000</span></span> | <span data-ttu-id="1e19a-154">900 MB</span><span class="sxs-lookup"><span data-stu-id="1e19a-154">900 MB</span></span> | <span data-ttu-id="1e19a-155">$0.02</span><span class="sxs-lookup"><span data-stu-id="1e19a-155">$0.02</span></span> | <span data-ttu-id="1e19a-156">$0.24</span><span class="sxs-lookup"><span data-stu-id="1e19a-156">$0.24</span></span> |
| <span data-ttu-id="1e19a-157">登录</span><span class="sxs-lookup"><span data-stu-id="1e19a-157">Sign-ins</span></span> | <span data-ttu-id="1e19a-158">1,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-158">1,000</span></span> | <span data-ttu-id="1e19a-159">34,800</span><span class="sxs-lookup"><span data-stu-id="1e19a-159">34,800</span></span> | <span data-ttu-id="1e19a-160">4 GB</span><span class="sxs-lookup"><span data-stu-id="1e19a-160">4 GB</span></span> | <span data-ttu-id="1e19a-161">$0.13</span><span class="sxs-lookup"><span data-stu-id="1e19a-161">$0.13</span></span> | <span data-ttu-id="1e19a-162">$1.56</span><span class="sxs-lookup"><span data-stu-id="1e19a-162">$1.56</span></span> |
| <span data-ttu-id="1e19a-163">登录</span><span class="sxs-lookup"><span data-stu-id="1e19a-163">Sign-ins</span></span> | <span data-ttu-id="1e19a-164">100,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-164">100,000</span></span> | <span data-ttu-id="1e19a-165">1,500&nbsp;万</span><span class="sxs-lookup"><span data-stu-id="1e19a-165">15&nbsp;million</span></span> | <span data-ttu-id="1e19a-166">1.7 TB</span><span class="sxs-lookup"><span data-stu-id="1e19a-166">1.7 TB</span></span> | <span data-ttu-id="1e19a-167">$35.41</span><span class="sxs-lookup"><span data-stu-id="1e19a-167">$35.41</span></span> | <span data-ttu-id="1e19a-168">$424.92</span><span class="sxs-lookup"><span data-stu-id="1e19a-168">$424.92</span></span> | 


### <a name="event-hub-messages-for-activity-logs"></a><span data-ttu-id="1e19a-169">活动日志的事件中心消息</span><span class="sxs-lookup"><span data-stu-id="1e19a-169">Event hub messages for activity logs</span></span>

<span data-ttu-id="1e19a-170">事件按大约五分钟的时间间隔进行批处理，并以单条消息的形式发送，每条包含该时间范围内的所有事件。</span><span class="sxs-lookup"><span data-stu-id="1e19a-170">Events are batched into approximately five-minute intervals and sent as a single message that contains all the events within that timeframe.</span></span> <span data-ttu-id="1e19a-171">事件中心的消息的最大大小为 256 KB，如果该时间范围内所有消息的总大小超出该大小，则会发送多条消息。</span><span class="sxs-lookup"><span data-stu-id="1e19a-171">A message in the event hub has a maximum size of 256 KB, and if the total size of all the messages within the timeframe exceeds that volume, multiple messages are sent.</span></span> 

<span data-ttu-id="1e19a-172">例如，对于用户数超出 100,000 的大型租户来说，通常情况下每秒大约有 18 个事件，该频率相当于每五分钟 5,400 个事件。</span><span class="sxs-lookup"><span data-stu-id="1e19a-172">For example, about 18 events per second ordinarily occur for a large tenant of more than 100,000 users, a rate that equates to 5,400 events every five minutes.</span></span> <span data-ttu-id="1e19a-173">由于审核日志大约每个事件 2 KB，上述事件相当于 10.8 MB 的数据，</span><span class="sxs-lookup"><span data-stu-id="1e19a-173">Because audit logs are about 2 KB per event, this equates to 10.8 MB of data.</span></span> <span data-ttu-id="1e19a-174">因此会在五分钟的时间间隔内向事件中心发送 43 条消息。</span><span class="sxs-lookup"><span data-stu-id="1e19a-174">Therefore, 43 messages are sent to the event hub in that five-minute interval.</span></span> 

<span data-ttu-id="1e19a-175">下表包含的内容是根据事件数据的量对“美国西部”区域一个基本事件中心进行的每月成本估算。</span><span class="sxs-lookup"><span data-stu-id="1e19a-175">The following table contains estimated costs per month for a basic event hub in West US, depending on the volume of event data.</span></span> <span data-ttu-id="1e19a-176">若要针对应用程序的预期数据量进行准确的估算，请使用[事件中心定价计算器](https://azure.microsoft.com/pricing/details/event-hubs/)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-176">To calculate an accurate estimate of the data volume that you anticipate for your application, use the [Event Hubs pricing calculator](https://azure.microsoft.com/pricing/details/event-hubs/).</span></span>

| <span data-ttu-id="1e19a-177">日志类别</span><span class="sxs-lookup"><span data-stu-id="1e19a-177">Log category</span></span> | <span data-ttu-id="1e19a-178">用户数</span><span class="sxs-lookup"><span data-stu-id="1e19a-178">Number of users</span></span> | <span data-ttu-id="1e19a-179">每秒事件数</span><span class="sxs-lookup"><span data-stu-id="1e19a-179">Events per second</span></span> | <span data-ttu-id="1e19a-180">每五分钟时间间隔的事件数</span><span class="sxs-lookup"><span data-stu-id="1e19a-180">Events per five-minute interval</span></span> | <span data-ttu-id="1e19a-181">每个时间间隔的数据量</span><span class="sxs-lookup"><span data-stu-id="1e19a-181">Volume per interval</span></span> | <span data-ttu-id="1e19a-182">每个时间间隔的消息数</span><span class="sxs-lookup"><span data-stu-id="1e19a-182">Messages per interval</span></span> | <span data-ttu-id="1e19a-183">每月消息数</span><span class="sxs-lookup"><span data-stu-id="1e19a-183">Messages per month</span></span> | <span data-ttu-id="1e19a-184">每月成本（估算）</span><span class="sxs-lookup"><span data-stu-id="1e19a-184">Cost per month (est.)</span></span> |
|--------------|-----------------|-------------------------|----------------------------------------|---------------------|---------------------------------|------------------------------|----------------------------|
| <span data-ttu-id="1e19a-185">审核</span><span class="sxs-lookup"><span data-stu-id="1e19a-185">Audit</span></span> | <span data-ttu-id="1e19a-186">100,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-186">100,000</span></span> | <span data-ttu-id="1e19a-187">18</span><span class="sxs-lookup"><span data-stu-id="1e19a-187">18</span></span> | <span data-ttu-id="1e19a-188">5,400</span><span class="sxs-lookup"><span data-stu-id="1e19a-188">5,400</span></span> | <span data-ttu-id="1e19a-189">10.8 MB</span><span class="sxs-lookup"><span data-stu-id="1e19a-189">10.8 MB</span></span> | <span data-ttu-id="1e19a-190">43</span><span class="sxs-lookup"><span data-stu-id="1e19a-190">43</span></span> | <span data-ttu-id="1e19a-191">371,520</span><span class="sxs-lookup"><span data-stu-id="1e19a-191">371,520</span></span> | <span data-ttu-id="1e19a-192">$10.83</span><span class="sxs-lookup"><span data-stu-id="1e19a-192">$10.83</span></span> |
| <span data-ttu-id="1e19a-193">审核</span><span class="sxs-lookup"><span data-stu-id="1e19a-193">Audit</span></span> | <span data-ttu-id="1e19a-194">1,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-194">1,000</span></span> | <span data-ttu-id="1e19a-195">0.1</span><span class="sxs-lookup"><span data-stu-id="1e19a-195">0.1</span></span> | <span data-ttu-id="1e19a-196">52</span><span class="sxs-lookup"><span data-stu-id="1e19a-196">52</span></span> | <span data-ttu-id="1e19a-197">104 KB</span><span class="sxs-lookup"><span data-stu-id="1e19a-197">104 KB</span></span> | <span data-ttu-id="1e19a-198">1</span><span class="sxs-lookup"><span data-stu-id="1e19a-198">1</span></span> | <span data-ttu-id="1e19a-199">8,640</span><span class="sxs-lookup"><span data-stu-id="1e19a-199">8,640</span></span> | <span data-ttu-id="1e19a-200">$10.80</span><span class="sxs-lookup"><span data-stu-id="1e19a-200">$10.80</span></span> |
| <span data-ttu-id="1e19a-201">登录</span><span class="sxs-lookup"><span data-stu-id="1e19a-201">Sign-ins</span></span> | <span data-ttu-id="1e19a-202">1,000</span><span class="sxs-lookup"><span data-stu-id="1e19a-202">1,000</span></span> | <span data-ttu-id="1e19a-203">178</span><span class="sxs-lookup"><span data-stu-id="1e19a-203">178</span></span> | <span data-ttu-id="1e19a-204">53,400</span><span class="sxs-lookup"><span data-stu-id="1e19a-204">53,400</span></span> | <span data-ttu-id="1e19a-205">106.8&nbsp;MB</span><span class="sxs-lookup"><span data-stu-id="1e19a-205">106.8&nbsp;MB</span></span> | <span data-ttu-id="1e19a-206">418</span><span class="sxs-lookup"><span data-stu-id="1e19a-206">418</span></span> | <span data-ttu-id="1e19a-207">3,611,520</span><span class="sxs-lookup"><span data-stu-id="1e19a-207">3,611,520</span></span> | <span data-ttu-id="1e19a-208">$11.06</span><span class="sxs-lookup"><span data-stu-id="1e19a-208">$11.06</span></span> |  

### <a name="log-analytics-cost-considerations"></a><span data-ttu-id="1e19a-209">Log Analytics 成本注意事项</span><span class="sxs-lookup"><span data-stu-id="1e19a-209">Log Analytics cost considerations</span></span>

<span data-ttu-id="1e19a-210">若要查看与管理 Log Analytics 工作区相关的成本，请参阅[通过在 Log Analytics 中控制数据量和保留期管理成本](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-210">To review costs related to managing the Log Analytics workspace, see [Manage cost by controlling data volume and retention in Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="1e19a-211">常见问题</span><span class="sxs-lookup"><span data-stu-id="1e19a-211">Frequently asked questions</span></span>

<span data-ttu-id="1e19a-212">此部分回答 Azure Monitor 中 Azure AD 日志的常见问题并讨论已知问题。</span><span class="sxs-lookup"><span data-stu-id="1e19a-212">This section answers frequently asked questions and discusses known issues with Azure AD logs in Azure Monitor.</span></span>

<span data-ttu-id="1e19a-213">**问：哪些日志包括在其中？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-213">**Q: Which logs are included?**</span></span>

<span data-ttu-id="1e19a-214">**答**：登录活动日志和审核日志均可通过此功能进行路由，但与 B2C 相关的审核事件目前未包括在其中。</span><span class="sxs-lookup"><span data-stu-id="1e19a-214">**A**: The sign-in activity logs and audit logs are both available for routing through this feature, although B2C-related audit events are currently not included.</span></span> <span data-ttu-id="1e19a-215">若要了解目前支持哪些类型的日志和哪些基于功能的日志，请参阅[审核日志架构](reference-azure-monitor-audit-log-schema.md)和[登录日志架构](reference-azure-monitor-sign-ins-log-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-215">To find out which types of logs and which feature-based logs are currently supported, see [Audit log schema](reference-azure-monitor-audit-log-schema.md) and [Sign-in log schema](reference-azure-monitor-sign-ins-log-schema.md).</span></span> 

---

<span data-ttu-id="1e19a-216">**问：执行某项操作之后，相应的日志多快会在事件中心内显示？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-216">**Q: How soon after an action will the corresponding logs show up in my event hub?**</span></span>

<span data-ttu-id="1e19a-217">**答**：日志会在执行操作后两到五分钟内在事件中心显示。</span><span class="sxs-lookup"><span data-stu-id="1e19a-217">**A**: The logs should show up in your event hub within two to five minutes after the action is performed.</span></span> <span data-ttu-id="1e19a-218">有关事件中心的详细信息，请参阅[什么是 Azure 事件中心？](../../event-hubs/event-hubs-about.md)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-218">For more information about Event Hubs, see [What is Azure Event Hubs?](../../event-hubs/event-hubs-about.md).</span></span>

---

<span data-ttu-id="1e19a-219">**问：执行某项操作之后，相应的日志多快会在存储帐户中显示？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-219">**Q: How soon after an action will the corresponding logs show up in my storage account?**</span></span>

<span data-ttu-id="1e19a-220">**答**：就 Azure 存储帐户而言，执行操作之后，日志的显示会有 5-15 分钟的延迟。</span><span class="sxs-lookup"><span data-stu-id="1e19a-220">**A**: For Azure storage accounts, the latency is anywhere from 5 to 15 minutes after the action is performed.</span></span>

---

<span data-ttu-id="1e19a-221">**问：如果管理员更改诊断设置的保持期，会发生什么情况？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-221">**Q: What happens if an Adminstrator changes the retention period of a diagnostic setting?**</span></span>

<span data-ttu-id="1e19a-222">**答**：新的保留策略将应用于更改后收集的日志。</span><span class="sxs-lookup"><span data-stu-id="1e19a-222">**A**: The new retention policy will be applied to logs collected after the change.</span></span> <span data-ttu-id="1e19a-223">策略更改前收集的日志将不会受到影响。</span><span class="sxs-lookup"><span data-stu-id="1e19a-223">Logs collected before the policy change will be unaffected.</span></span>

---

<span data-ttu-id="1e19a-224">**问：存储数据的费用是多少？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-224">**Q: How much will it cost to store my data?**</span></span>

<span data-ttu-id="1e19a-225">**答**：存储费用取决于日志大小以及所选保留期。</span><span class="sxs-lookup"><span data-stu-id="1e19a-225">**A**: The storage costs depend on both the size of your logs and the retention period you choose.</span></span> <span data-ttu-id="1e19a-226">如需租户估算费用（取决于生成的日志量）的列表，请参阅[活动日志的存储大小](#storage-size-for-activity-logs)部分。</span><span class="sxs-lookup"><span data-stu-id="1e19a-226">For a list of the estimated costs for tenants, which depend on the volume of logs generated, see the [Storage size for activity logs](#storage-size-for-activity-logs) section.</span></span>

---

<span data-ttu-id="1e19a-227">**问：将数据流式传输到事件中心的费用是多少？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-227">**Q: How much will it cost to stream my data to an event hub?**</span></span>

<span data-ttu-id="1e19a-228">**答**：流式传输费用取决于每分钟收到的消息数。</span><span class="sxs-lookup"><span data-stu-id="1e19a-228">**A**: The streaming costs depend on the number of messages you receive per minute.</span></span> <span data-ttu-id="1e19a-229">本文介绍了费用计算方法并列出了根据消息数估算的费用。</span><span class="sxs-lookup"><span data-stu-id="1e19a-229">This article discusses how the costs are calculated and lists cost estimates, which are based on the number of messages.</span></span> 

---

<span data-ttu-id="1e19a-230">**问：如何将 Azure AD 活动日志与 SIEM 系统集成？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-230">**Q: How do I integrate Azure AD activity logs with my SIEM system?**</span></span>

<span data-ttu-id="1e19a-231">**答**：可通过两种方式实现此目的：</span><span class="sxs-lookup"><span data-stu-id="1e19a-231">**A**: You can do this in two ways:</span></span>

- <span data-ttu-id="1e19a-232">将 Azure Monitor 与事件中心配合使用，以将日志流式传输到 SIEM 系统。</span><span class="sxs-lookup"><span data-stu-id="1e19a-232">Use Azure Monitor with Event Hubs to stream logs to your SIEM system.</span></span> <span data-ttu-id="1e19a-233">首先，[将日志流式传输到事件中心](tutorial-azure-monitor-stream-logs-to-event-hub.md)，然后使用配置的事件中心[设置 SIEM 工具](tutorial-azure-monitor-stream-logs-to-event-hub.md#access-data-from-your-event-hub)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-233">First, [stream the logs to an event hub](tutorial-azure-monitor-stream-logs-to-event-hub.md) and then [set up your SIEM tool](tutorial-azure-monitor-stream-logs-to-event-hub.md#access-data-from-your-event-hub) with the configured event hub.</span></span> 

- <span data-ttu-id="1e19a-234">使用[报告图形 API](concept-reporting-api.md) 访问数据，并使用自己的脚本将其推送到 SIEM 系统。</span><span class="sxs-lookup"><span data-stu-id="1e19a-234">Use the [Reporting Graph API](concept-reporting-api.md) to access the data, and push it into the SIEM system using your own scripts.</span></span>

---

<span data-ttu-id="1e19a-235">**问：目前支持哪些 SIEM 工具？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-235">**Q: What SIEM tools are currently supported?**</span></span> 

<span data-ttu-id="1e19a-236">**答**：目前，[Splunk](tutorial-integrate-activity-logs-with-splunk.md)、QRadar 和 [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) 支持 Azure Monitor。</span><span class="sxs-lookup"><span data-stu-id="1e19a-236">**A**: Currently, Azure Monitor is supported by [Splunk](tutorial-integrate-activity-logs-with-splunk.md), QRadar, and [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory).</span></span> <span data-ttu-id="1e19a-237">若要详细了解连接器的工作方式，请参阅[将 Azure 监视数据流式传输到事件中心供外部工具使用](../../azure-monitor/platform/stream-monitoring-data-event-hubs.md)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-237">For more information about how the connectors work, see [Stream Azure monitoring data to an event hub for consumption by an external tool](../../azure-monitor/platform/stream-monitoring-data-event-hubs.md).</span></span>

---

<span data-ttu-id="1e19a-238">**问：如何将 Azure AD 活动日志与 Splunk 实例集成？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-238">**Q: How do I integrate Azure AD activity logs with my Splunk instance?**</span></span>

<span data-ttu-id="1e19a-239">**答**：首先，[将 Azure AD 活动日志路由到事件中心](quickstart-azure-monitor-stream-logs-to-event-hub.md)，然后按照相关步骤[将活动日志与 Splunk 集成](tutorial-integrate-activity-logs-with-splunk.md)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-239">**A**: First, [route the Azure AD activity logs to an event hub](quickstart-azure-monitor-stream-logs-to-event-hub.md), then follow the steps to [Integrate activity logs with Splunk](tutorial-integrate-activity-logs-with-splunk.md).</span></span>

---

<span data-ttu-id="1e19a-240">**问：如何将 Azure AD 活动日志与 Sumo Logic 集成？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-240">**Q: How do I integrate Azure AD activity logs with Sumo Logic?**</span></span> 

<span data-ttu-id="1e19a-241">**答**：首先，[将 Azure AD 活动日志路由到事件中心](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Collect_Logs_for_Azure_Active_Directory)，然后按照相关步骤[安装 Azure AD 应用程序并查看 SumoLogic 中的仪表板](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Install_the_Azure_Active_Directory_App_and_View_the_Dashboards)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-241">**A**: First, [route the Azure AD activity logs to an event hub](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Collect_Logs_for_Azure_Active_Directory), then follow the steps to [Install the Azure AD application and view the dashboards in SumoLogic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory/Install_the_Azure_Active_Directory_App_and_View_the_Dashboards).</span></span>

---

<span data-ttu-id="1e19a-242">**问：是否可以在不使用外部 SIEM 工具的情况下，从事件中心访问数据？**</span><span class="sxs-lookup"><span data-stu-id="1e19a-242">**Q: Can I access the data from an event hub without using an external SIEM tool?**</span></span> 

<span data-ttu-id="1e19a-243">**答**：是的。</span><span class="sxs-lookup"><span data-stu-id="1e19a-243">**A**: Yes.</span></span> <span data-ttu-id="1e19a-244">若要通过自定义应用程序来访问日志，可以使用[事件中心 API](../../event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph.md)。</span><span class="sxs-lookup"><span data-stu-id="1e19a-244">To access the logs from your custom application, you can use the [Event Hubs API](../../event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph.md).</span></span> 

---


## <a name="next-steps"></a><span data-ttu-id="1e19a-245">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1e19a-245">Next steps</span></span>

* [<span data-ttu-id="1e19a-246">将活动日志存档到存储帐户</span><span class="sxs-lookup"><span data-stu-id="1e19a-246">Archive activity logs to a storage account</span></span>](quickstart-azure-monitor-route-logs-to-storage-account.md)
* [<span data-ttu-id="1e19a-247">将活动日志路由到事件中心</span><span class="sxs-lookup"><span data-stu-id="1e19a-247">Route activity logs to an event hub</span></span>](quickstart-azure-monitor-stream-logs-to-event-hub.md)
* [<span data-ttu-id="1e19a-248">将活动日志与 Log Analytics 集成</span><span class="sxs-lookup"><span data-stu-id="1e19a-248">Integrate activity logs with Log Analytics</span></span>](howto-integrate-activity-logs-with-log-analytics.md)
