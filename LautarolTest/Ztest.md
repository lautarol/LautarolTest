---
ms.assetid: c3c34c0d-4f06-489a-aaba-0a96b9d8eaf9
title: Include 檔案
description: 包含提供 System Center 2016 - Orchestrator 系統需求的檔案，其中也包含設計規劃 Orchestrator 部署時所要考量的一般效能和延展性指導。
author: rayne-wiselman
manager: carmon
ms.date: 05/17/2018
ms.prod: system-center-threshold
ms.technology: Orchestrator
ms.topic: include
ms-author: raynew
ms.openlocfilehash: f95664efbef0fc34c977026abad68c7e0333f598
ms.sourcegitcommit: e9ab1b68e1dce67c533d69ca3eaefb1b719a3500
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58395544"
---
## <a name="system-requirements-for-system-center-2016---orchestrator"></a><span data-ttu-id="990a0-103">System Center 2016 - Orchestrator 的系統需求</span><span class="sxs-lookup"><span data-stu-id="990a0-103">System requirements for System Center 2016 - Orchestrator</span></span>

<span data-ttu-id="990a0-104">下列各節描述適用於 System Center 2016 - Orchestrator 的一般效能與延展性指導，並針對各種不同的工作負載建議硬體設定。</span><span class="sxs-lookup"><span data-stu-id="990a0-104">The following sections describe general performance and scalability guidance for System Center 2016 - Orchestrator, and recommends hardware configurations for a variety of workloads.</span></span> <span data-ttu-id="990a0-105">由於 System Center 2016 的設計理念是保障靈活性與可調整性，因此特定案例的實際硬體需求可能不同於此處所提供指導方針。</span><span class="sxs-lookup"><span data-stu-id="990a0-105">As System Center 2016 is built to be flexible and scalable, the actual hardware requirements for specific scenarios may differ from the guidelines that are presented here.</span></span>

## <a name="hardware"></a><span data-ttu-id="990a0-106">硬體</span><span class="sxs-lookup"><span data-stu-id="990a0-106">Hardware</span></span>

| <span data-ttu-id="990a0-107">Orchestrator 伺服器角色</span><span class="sxs-lookup"><span data-stu-id="990a0-107">Orchestrator Server Role</span></span> | <span data-ttu-id="990a0-108">x64 處理器 (最低)</span><span class="sxs-lookup"><span data-stu-id="990a0-108">x64 Processor (min)</span></span> | <span data-ttu-id="990a0-109">記憶體 (最低)</span><span class="sxs-lookup"><span data-stu-id="990a0-109">Memory (min)</span></span> | <span data-ttu-id="990a0-110">磁碟空間 (最低)</span><span class="sxs-lookup"><span data-stu-id="990a0-110">Disk space (min)</span></span> |
|:-----|:----|:---- |:---- |
|<span data-ttu-id="990a0-111">所有伺服器角色</span><span class="sxs-lookup"><span data-stu-id="990a0-111">All server roles</span></span>|<span data-ttu-id="990a0-112">2.1 GHz，雙核心 CPU</span><span class="sxs-lookup"><span data-stu-id="990a0-112">2.1 GHz, dual-core CPU</span></span> |<span data-ttu-id="990a0-113">2 GB</span><span class="sxs-lookup"><span data-stu-id="990a0-113">2 GB</span></span>|<span data-ttu-id="990a0-114">200 MB</span><span class="sxs-lookup"><span data-stu-id="990a0-114">200 MB</span></span>

## <a name="server-operating-system"></a><span data-ttu-id="990a0-115">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="990a0-115">Server operating system</span></span>

<span data-ttu-id="990a0-116">支援下列 Windows Server 作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="990a0-116">The following versions of Windows Server operating system are supported.</span></span>

| <span data-ttu-id="990a0-117">元件</span><span class="sxs-lookup"><span data-stu-id="990a0-117">Component</span></span> | <span data-ttu-id="990a0-118">Windows Server 2012 R2 Standard、Datacenter</span><span class="sxs-lookup"><span data-stu-id="990a0-118">Windows Server 2012 R2 Standard, Datacenter</span></span> | <span data-ttu-id="990a0-119">Windows Server 2016 Standard、Datacenter (含桌面體驗)</span><span class="sxs-lookup"><span data-stu-id="990a0-119">Windows Server 2016 Standard, Datacenter with Desktop Experience</span></span> | <span data-ttu-id="990a0-120">Windows Server Core 2016</span><span class="sxs-lookup"><span data-stu-id="990a0-120">Windows Server Core 2016</span></span> |
|:--- |:---|:--- |:--- |
|<span data-ttu-id="990a0-121">所有伺服器角色</span><span class="sxs-lookup"><span data-stu-id="990a0-121">All server roles</span></span>|<span data-ttu-id="990a0-122">支援</span><span class="sxs-lookup"><span data-stu-id="990a0-122">Supported</span></span>|<span data-ttu-id="990a0-123">支援</span><span class="sxs-lookup"><span data-stu-id="990a0-123">Supported</span></span>|<span data-ttu-id="990a0-124">不支援</span><span class="sxs-lookup"><span data-stu-id="990a0-124">Not Supported</span></span>


## <a name="client-operating-system"></a><span data-ttu-id="990a0-125">用戶端作業系統</span><span class="sxs-lookup"><span data-stu-id="990a0-125">Client operating system</span></span>

<span data-ttu-id="990a0-126">Orchestrator 支援下列 Windows 用戶端作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="990a0-126">The following versions of Windows client operating system are supported for the Orchestrator.</span></span>

|<span data-ttu-id="990a0-127">元件</span><span class="sxs-lookup"><span data-stu-id="990a0-127">Component</span></span>| <span data-ttu-id="990a0-128">Windows 7</span><span class="sxs-lookup"><span data-stu-id="990a0-128">Windows 7</span></span> | <span data-ttu-id="990a0-129">Windows 8</span><span class="sxs-lookup"><span data-stu-id="990a0-129">Windows 8</span></span> | <span data-ttu-id="990a0-130">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="990a0-130">Windows 8.1</span></span> | <span data-ttu-id="990a0-131">Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="990a0-131">Windows 10 Enterprise</span></span> |
|:--- |:---|:--- |:--- |:---|
|<span data-ttu-id="990a0-132">Runbook Designer</span><span class="sxs-lookup"><span data-stu-id="990a0-132">Runbook Designer</span></span>|<span data-ttu-id="990a0-133">不支援</span><span class="sxs-lookup"><span data-stu-id="990a0-133">Not supported</span></span>|<span data-ttu-id="990a0-134">不支援</span><span class="sxs-lookup"><span data-stu-id="990a0-134">Not Supported</span></span>|<span data-ttu-id="990a0-135">不支援</span><span class="sxs-lookup"><span data-stu-id="990a0-135">Not Supported</span></span>|<span data-ttu-id="990a0-136">支援</span><span class="sxs-lookup"><span data-stu-id="990a0-136">Supported</span></span>

## <a name="software"></a><span data-ttu-id="990a0-137">軟體</span><span class="sxs-lookup"><span data-stu-id="990a0-137">Software</span></span>

<span data-ttu-id="990a0-138">若要將 Orchestrator 完整地安裝在單一電腦上，則需下列軟體：</span><span class="sxs-lookup"><span data-stu-id="990a0-138">The following software is required for a full installation of Orchestrator on a single computer:</span></span>

* <span data-ttu-id="990a0-139">Microsoft SQL Server 2012、2014 或 2016 – Orchestrator 只需要 Database Engine 服務中的基本 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="990a0-139">Microsoft SQL Server 2012, 2014, or 2016 – Orchestrator requires only the basic SQL Server features found in the Database Engine Service.</span></span> <span data-ttu-id="990a0-140">不需要額外的功能。</span><span class="sxs-lookup"><span data-stu-id="990a0-140">No additional features are required.</span></span> <span data-ttu-id="990a0-141">Orchestrator 支援將 SQL_Latin1_General_CP1_CI_AS 作為定序。</span><span class="sxs-lookup"><span data-stu-id="990a0-141">Orchestrator supports SQL_Latin1_General_CP1_CI_AS for collation.</span></span> <span data-ttu-id="990a0-142">安裝精靈會使用 SQL_Latin1_General_CP1_CI_AS 作為預設定序來建立 Orchestrator 資料庫。</span><span class="sxs-lookup"><span data-stu-id="990a0-142">The installation wizard uses SQL_Latin1_General_CP1_CI_AS as the default collation to create the orchestration database.</span></span> <span data-ttu-id="990a0-143">如需詳細資訊，請參閱[＜SQL Server＞](#sql-server)一節。</span><span class="sxs-lookup"><span data-stu-id="990a0-143">For more information, see the section on [SQL Server](#sql-server).</span></span>

> [!NOTE]
> <span data-ttu-id="990a0-144">安裝在同一部電腦上的 Management 伺服器和 Runbook 伺服器必須使用相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="990a0-144">Management servers and runbook servers installed on the same computer must use the same database.</span></span> <span data-ttu-id="990a0-145">Management 伺服器必須以 32 位元應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="990a0-145">The management server must run as a 32-bit application.</span></span>

* <span data-ttu-id="990a0-146">Microsoft Internet Information Services (IIS) – Orchestrator 安裝程式會啟用 IIS (如果尚未啟用)。</span><span class="sxs-lookup"><span data-stu-id="990a0-146">Microsoft Internet Information Services (IIS) – Orchestrator Setup enables IIS if it is not enabled.</span></span>

* <span data-ttu-id="990a0-147">Microsoft .NET Framework 3.5 Service Pack 1 - Orchestrator 安裝程式會安裝及啟用 .NET Framework 3.5 SP1 (如果尚未安裝及啟用)。</span><span class="sxs-lookup"><span data-stu-id="990a0-147">Microsoft .NET Framework 3.5 Service Pack 1 - Orchestrator Setup installs and enables .NET Framework 3.5 SP1 if it is not installed and enabled.</span></span>

* <span data-ttu-id="990a0-148">Microsoft .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="990a0-148">Microsoft .NET Framework 4</span></span>
* [<span data-ttu-id="990a0-149">Microsoft SQL Server 2012 Native Client - QFE (適用於 SQL 2012/2014/2016)</span><span class="sxs-lookup"><span data-stu-id="990a0-149">Microsoft SQL Server 2012 Native Client - QFE   (applies to SQL 2012/2014/2016)</span></span>](https://www.microsoft.com/download/details.aspx?id=50402)

<span data-ttu-id="990a0-150">將 Orchestrator 完整安裝在單一電腦上時，建議您採用下列軟體：</span><span class="sxs-lookup"><span data-stu-id="990a0-150">We recommend the following software for a full installation of Orchestrator on a single computer:</span></span>

* <span data-ttu-id="990a0-151">將電腦加入 Active Directory 網域。</span><span class="sxs-lookup"><span data-stu-id="990a0-151">Join the computer to an Active Directory domain.</span></span>

> [!NOTE]
> <span data-ttu-id="990a0-152">第一次使用 Orchestration 主控台時，如果尚未在電腦上安裝 Microsoft Silverlight 4，則會跳出提示提醒安裝。</span><span class="sxs-lookup"><span data-stu-id="990a0-152">On first use of the Orchestration console, you are prompted to install Microsoft Silverlight 4 on the computer if it is not already installed.</span></span>

## <a name="sql-server"></a><span data-ttu-id="990a0-153">SQL Server</span><span class="sxs-lookup"><span data-stu-id="990a0-153">SQL Server</span></span>

> [!NOTE]
> <span data-ttu-id="990a0-154">針對支援的 SQL 版本，請使用 Microsoft 目前支援的 Service Pack。</span><span class="sxs-lookup"><span data-stu-id="990a0-154">For the supported versions of SQL, use the service packs that are currently in support by Microsoft.</span></span>

<span data-ttu-id="990a0-155">**SQL 版本**</span><span class="sxs-lookup"><span data-stu-id="990a0-155">**SQL version**</span></span> | <span data-ttu-id="990a0-156">**支援**</span><span class="sxs-lookup"><span data-stu-id="990a0-156">**Supported**</span></span>
--- | ---
<span data-ttu-id="990a0-157">**SQL Server 2008**</span><span class="sxs-lookup"><span data-stu-id="990a0-157">**SQL Server 2008**</span></span>| <span data-ttu-id="990a0-158">N</span><span class="sxs-lookup"><span data-stu-id="990a0-158">N</span></span>
<span data-ttu-id="990a0-159">**[這裡](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202012%20service%20pack)提供 SQL Server 2012 和 SP 的詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="990a0-159">**SQL Server 2012 and SPs as detailed [here](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202012%20service%20pack)**</span></span> | <span data-ttu-id="990a0-160">Y</span><span class="sxs-lookup"><span data-stu-id="990a0-160">Y</span></span>
<span data-ttu-id="990a0-161">**[這裡](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202014%20service%20pack)提供 SQL Server 2014 和 SP 的詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="990a0-161">**SQL Server 2014 and SPs as detailed [here](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202014%20service%20pack)**</span></span> | <span data-ttu-id="990a0-162">Y</span><span class="sxs-lookup"><span data-stu-id="990a0-162">Y</span></span>
<span data-ttu-id="990a0-163">**[這裡](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202016%20service%20pack)提供 SQL Server 2016 和 SP 的詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="990a0-163">**SQL Server 2016 and SPs as detailed [here](https://support.microsoft.com/en-in/lifecycle/search?alpha=SQL%20server%202016%20service%20pack)**</span></span> | <span data-ttu-id="990a0-164">Y</span><span class="sxs-lookup"><span data-stu-id="990a0-164">Y</span></span>

## <a name="net-requirements"></a><span data-ttu-id="990a0-165">.NET 需求</span><span class="sxs-lookup"><span data-stu-id="990a0-165">.Net requirements</span></span>

<span data-ttu-id="990a0-166">所有 Orchestrator 伺服器角色都需要 .NET 3.5 SP1 才能執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="990a0-166">All Orchestrator server roles require .Net 3.5 SP1 in order to run the setup program.</span></span> <span data-ttu-id="990a0-167">Orchestrator Web 服務需要 .NET 4.5 和 WCF 啟動。</span><span class="sxs-lookup"><span data-stu-id="990a0-167">The Orchestrator Web Service requires .Net 4.5 with WCF Activation.</span></span>

<span data-ttu-id="990a0-168">您可以下載在.Net 3.5 SP1:</span><span class="sxs-lookup"><span data-stu-id="990a0-168">You can download .Net 3.5 SP1 at:</span></span>  

### <a name="to-turn-on-wcf-activation"></a><span data-ttu-id="990a0-169">開啟 WCF 啟動</span><span class="sxs-lookup"><span data-stu-id="990a0-169">To turn on WCF activation</span></span>

1. <span data-ttu-id="990a0-170">在 Windows [開始] 畫面中，按一下 [伺服器管理員] 磚。</span><span class="sxs-lookup"><span data-stu-id="990a0-170">On the Windows Start screen, click the **Server Manager** tile.</span></span>
2.  <span data-ttu-id="990a0-171">在伺服器管理員主控台的 [管理]  功能表中按一下 [新增角色及功能] 。</span><span class="sxs-lookup"><span data-stu-id="990a0-171">On the **Manage** menu in the Server Manager console, click **Add Roles and Features**.</span></span>
3.  <span data-ttu-id="990a0-172">逐一完成精靈中的作業，直到進入 [功能]  頁面。</span><span class="sxs-lookup"><span data-stu-id="990a0-172">Go through the wizard until you reach the **Features** page.</span></span>
4.  <span data-ttu-id="990a0-173">展開 [.NET Framework 4.5 功能] 。</span><span class="sxs-lookup"><span data-stu-id="990a0-173">Expand **.NET Framework 4.5 Features**.</span></span>
5.  <span data-ttu-id="990a0-174">如果尚未選取 [.NET Framework 4.5]  ，請選取。</span><span class="sxs-lookup"><span data-stu-id="990a0-174">Select **.NET Framework 4.5** if it isn’t already selected.</span></span>
6.  <span data-ttu-id="990a0-175">展開 [WCF 服務] 。</span><span class="sxs-lookup"><span data-stu-id="990a0-175">Expand **WCF Services**.</span></span>
7.  <span data-ttu-id="990a0-176">選取 [HTTP 啟用]  \(如果尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="990a0-176">Select **HTTP Activation** if it isn’t already selected.</span></span>
8.  <span data-ttu-id="990a0-177">按 [下一步]  ，並遵照提示完成安裝。</span><span class="sxs-lookup"><span data-stu-id="990a0-177">Click **Next** and follow the prompts to finish the installation.</span></span> <span data-ttu-id="990a0-178">如果您有任何問題，請查閱 [Troubleshoot Your Orchestrator Installation](https://technet.microsoft.com/library/hh546549.aspx)中涵蓋的問題。</span><span class="sxs-lookup"><span data-stu-id="990a0-178">If you have problems, check the issues covered in [Troubleshoot Your Orchestrator Installation](https://technet.microsoft.com/library/hh546549.aspx).</span></span>


## <a name="virtualization"></a><span data-ttu-id="990a0-179">虛擬化</span><span class="sxs-lookup"><span data-stu-id="990a0-179">Virtualization</span></span>

<span data-ttu-id="990a0-180">完整支援在虛擬化作業系統上部署及執行 Orchestrator。</span><span class="sxs-lookup"><span data-stu-id="990a0-180">Deploying and running Orchestrator on a virtualized operating system is fully supported.</span></span> <span data-ttu-id="990a0-181">其軟體需求與上述需求相同。</span><span class="sxs-lookup"><span data-stu-id="990a0-181">The software requirements are the same as those listed above.</span></span> <span data-ttu-id="990a0-182">在 Microsoft Azure 中執行的虛擬化伺服器上也可以執行任何 Orchestrator 角色。</span><span class="sxs-lookup"><span data-stu-id="990a0-182">Any of the Orchestrator roles can also be run on a virtualized server running in Microsoft Azure.</span></span>
