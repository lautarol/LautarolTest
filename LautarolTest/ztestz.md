---
title: Use the Always On Availability Group dashboard (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
  - sql13.swb.agdashboard.f1
helpviewer_keywords:
  - 'Availability Groups [SQL Server], policies'
  - 'Availability Groups [SQL Server], dashboard'
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
manager: craigg
---
# <a name="use-the-always-on-availability-group-dashboard-sql-server-management-studio"></a><span data-ttu-id="fbd15-102">Use the Always On Availability Group dashboard (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fbd15-102">Use the Always On Availability Group dashboard (SQL Server Management Studio)</span></span>

  <span data-ttu-id="fbd15-103">Database administrators use the Always On Availability Group dashboard to obtain an at-a-glance view the health of an availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbd15-103">Database administrators use the Always On Availability Group dashboard to obtain an at-a-glance view the health of an availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fbd15-104">Some of the typical uses for the availability group dashboard are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-104">Some of the typical uses for the availability group dashboard are:</span></span>  
  
-   <span data-ttu-id="fbd15-105">Choosing a replica for a manual failover.</span><span class="sxs-lookup"><span data-stu-id="fbd15-105">Choosing a replica for a manual failover.</span></span>    
-   <span data-ttu-id="fbd15-106">Estimating data loss if you force failover.</span><span class="sxs-lookup"><span data-stu-id="fbd15-106">Estimating data loss if you force failover.</span></span>  
-   <span data-ttu-id="fbd15-107">Evaluating data-synchronization performance.</span><span class="sxs-lookup"><span data-stu-id="fbd15-107">Evaluating data-synchronization performance.</span></span>   
-   <span data-ttu-id="fbd15-108">Evaluating the performance impact of a synchronous-commit secondary replica</span><span class="sxs-lookup"><span data-stu-id="fbd15-108">Evaluating the performance impact of a synchronous-commit secondary replica</span></span> 
  -  <span data-ttu-id="fbd15-109">The dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span><span class="sxs-lookup"><span data-stu-id="fbd15-109">The dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span></span>  
-   <span data-ttu-id="fbd15-110">Replica roll-up state</span><span class="sxs-lookup"><span data-stu-id="fbd15-110">Replica roll-up state</span></span>    
-   <span data-ttu-id="fbd15-111">Synchronization mode and state</span><span class="sxs-lookup"><span data-stu-id="fbd15-111">Synchronization mode and state</span></span>   
-   <span data-ttu-id="fbd15-112">Estimate Data Loss</span><span class="sxs-lookup"><span data-stu-id="fbd15-112">Estimate Data Loss</span></span>    
-   <span data-ttu-id="fbd15-113">Estimated Recovery Time (redo catch up)</span><span class="sxs-lookup"><span data-stu-id="fbd15-113">Estimated Recovery Time (redo catch up)</span></span>    
-   <span data-ttu-id="fbd15-114">Database Replica details</span><span class="sxs-lookup"><span data-stu-id="fbd15-114">Database Replica details</span></span>    
-   <span data-ttu-id="fbd15-115">Synchronization mode and state</span><span class="sxs-lookup"><span data-stu-id="fbd15-115">Synchronization mode and state</span></span>    
-   <span data-ttu-id="fbd15-116">Time to restore log</span><span class="sxs-lookup"><span data-stu-id="fbd15-116">Time to restore log</span></span>  
  
  
## <a name="prerequisites"></a><span data-ttu-id="fbd15-117">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fbd15-117">Prerequisites</span></span>  
 <span data-ttu-id="fbd15-118">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-118">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span></span>  
  
 
### <a name="permissions"></a><span data-ttu-id="fbd15-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="fbd15-119">Permissions</span></span>  
 <span data-ttu-id="fbd15-120">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span><span class="sxs-lookup"><span data-stu-id="fbd15-120">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="to-start-the-always-on-dashboard"></a><span data-ttu-id="fbd15-121">To start the Always On dashboard</span><span class="sxs-lookup"><span data-stu-id="fbd15-121">To start the Always On dashboard</span></span>  
  
1.  <span data-ttu-id="fbd15-122">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the Always On Dashboard.</span><span class="sxs-lookup"><span data-stu-id="fbd15-122">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the Always On Dashboard.</span></span>  
  
2.  <span data-ttu-id="fbd15-123">Expand the **Always On High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-123">Expand the **Always On High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span></span>  
  
##  <a name="change-always-on-dashboard-options"></a><span data-ttu-id="fbd15-124">Change Always On Dashboard Options</span><span class="sxs-lookup"><span data-stu-id="fbd15-124">Change Always On Dashboard Options</span></span>  
 <span data-ttu-id="fbd15-125">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Always On Dashboard behavior for automatic refreshing and enabling an auto-defined Always On policy.</span><span class="sxs-lookup"><span data-stu-id="fbd15-125">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Always On Dashboard behavior for automatic refreshing and enabling an auto-defined Always On policy.</span></span>  
  
1.  <span data-ttu-id="fbd15-126">From the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-126">From the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="fbd15-127">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span><span class="sxs-lookup"><span data-stu-id="fbd15-127">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span></span>  
  
3.  <span data-ttu-id="fbd15-128">To enable a user-defined policy, select **Enable user-defined Always On policy**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-128">To enable a user-defined policy, select **Enable user-defined Always On policy**.</span></span>  
  
##  <a name="availability-group-summary"></a><span data-ttu-id="fbd15-129">Availability Group Summary</span><span class="sxs-lookup"><span data-stu-id="fbd15-129">Availability Group Summary</span></span>  
 <span data-ttu-id="fbd15-130">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-130">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="fbd15-131">This pane displays the following columns.</span><span class="sxs-lookup"><span data-stu-id="fbd15-131">This pane displays the following columns.</span></span>  
  
 <span data-ttu-id="fbd15-132">**Availability Group Name**</span><span class="sxs-lookup"><span data-stu-id="fbd15-132">**Availability Group Name**</span></span>  
 <span data-ttu-id="fbd15-133">The name of an availability group for which the connected server instance hosts a replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-133">The name of an availability group for which the connected server instance hosts a replica.</span></span>  
  
 <span data-ttu-id="fbd15-134">**Primary Instance**</span><span class="sxs-lookup"><span data-stu-id="fbd15-134">**Primary Instance**</span></span>  
 <span data-ttu-id="fbd15-135">Name of the server instance that is hosting the primary replica of the availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-135">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="fbd15-136">**Failover Mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-136">**Failover Mode**</span></span>  
 <span data-ttu-id="fbd15-137">Displays the failover mode for which the replica is configured.</span><span class="sxs-lookup"><span data-stu-id="fbd15-137">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="fbd15-138">The possible failover mode values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-138">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="fbd15-139">**Automatic**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-139">**Automatic**.</span></span> <span data-ttu-id="fbd15-140">Indicates that one or more replicas is in automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-140">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="fbd15-141">**Manual**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-141">**Manual**.</span></span> <span data-ttu-id="fbd15-142">Indicates that no replica is automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-142">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="fbd15-143">**Issues**</span><span class="sxs-lookup"><span data-stu-id="fbd15-143">**Issues**</span></span>  
 <span data-ttu-id="fbd15-144">Click the **Issues** link to open troubleshooting documentation for a given issue.</span><span class="sxs-lookup"><span data-stu-id="fbd15-144">Click the **Issues** link to open troubleshooting documentation for a given issue.</span></span> <span data-ttu-id="fbd15-145">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-145">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="fbd15-146">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span><span class="sxs-lookup"><span data-stu-id="fbd15-146">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span></span>  
  
##  <a name="AvGroupDetails"></a> <span data-ttu-id="fbd15-147">Availability Group Details</span><span class="sxs-lookup"><span data-stu-id="fbd15-147">Availability Group Details</span></span>  
 <span data-ttu-id="fbd15-148">The following detail information is displayed for the availability group that you select from the summary screen:</span><span class="sxs-lookup"><span data-stu-id="fbd15-148">The following detail information is displayed for the availability group that you select from the summary screen:</span></span>  
  
 <span data-ttu-id="fbd15-149">**Availability group state**</span><span class="sxs-lookup"><span data-stu-id="fbd15-149">**Availability group state**</span></span>  
 <span data-ttu-id="fbd15-150">Displays the state of health for the availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-150">Displays the state of health for the availability group.</span></span>  
  
 <span data-ttu-id="fbd15-151">**Primary instance**</span><span class="sxs-lookup"><span data-stu-id="fbd15-151">**Primary instance**</span></span>  
 <span data-ttu-id="fbd15-152">Name of the server instance that is hosting the primary replica of the availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-152">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="fbd15-153">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-153">**Failover mode**</span></span>  
 <span data-ttu-id="fbd15-154">Displays the failover mode for which the replica is configured.</span><span class="sxs-lookup"><span data-stu-id="fbd15-154">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="fbd15-155">The possible failover mode values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-155">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="fbd15-156">**Automatic**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-156">**Automatic**.</span></span> <span data-ttu-id="fbd15-157">Indicates that one or more replicas is in automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-157">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="fbd15-158">**Manual**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-158">**Manual**.</span></span> <span data-ttu-id="fbd15-159">Indicates that no replica is automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-159">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="fbd15-160">**Cluster state**</span><span class="sxs-lookup"><span data-stu-id="fbd15-160">**Cluster state**</span></span>  
 <span data-ttu-id="fbd15-161">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span><span class="sxs-lookup"><span data-stu-id="fbd15-161">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span></span>  
  
##  <a name="AvReplicaDetails"></a> <span data-ttu-id="fbd15-162">Availability Replica Details</span><span class="sxs-lookup"><span data-stu-id="fbd15-162">Availability Replica Details</span></span>  

<span data-ttu-id="fbd15-163">When connected to the primary replica, **Availability replica details** shows information from all replicas in the availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-163">When connected to the primary replica, **Availability replica details** shows information from all replicas in the availability group.</span></span> <span data-ttu-id="fbd15-164">When connected to a secondary replica, the display only shows information from the connected replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-164">When connected to a secondary replica, the display only shows information from the connected replica.</span></span>  

<span data-ttu-id="fbd15-165">The **Availability replica** pane displays the following columns:</span><span class="sxs-lookup"><span data-stu-id="fbd15-165">The **Availability replica** pane displays the following columns:</span></span>  
  
 <span data-ttu-id="fbd15-166">**Name**</span><span class="sxs-lookup"><span data-stu-id="fbd15-166">**Name**</span></span>  
 <span data-ttu-id="fbd15-167">The name of the server instance that hosts the availability replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-167">The name of the server instance that hosts the availability replica.</span></span> <span data-ttu-id="fbd15-168">This column is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-168">This column is shown by default.</span></span>  
  
 <span data-ttu-id="fbd15-169">**Role**</span><span class="sxs-lookup"><span data-stu-id="fbd15-169">**Role**</span></span>  
 <span data-ttu-id="fbd15-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="fbd15-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).</span></span> <span data-ttu-id="fbd15-172">This column is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-172">This column is shown by default.</span></span>  
  
 <span data-ttu-id="fbd15-173">**Failover Mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-173">**Failover Mode**</span></span>  
 <span data-ttu-id="fbd15-174">Displays the failover mode for which the replica is configured.</span><span class="sxs-lookup"><span data-stu-id="fbd15-174">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="fbd15-175">The possible failover mode values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-175">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="fbd15-176">**Automatic**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-176">**Automatic**.</span></span> <span data-ttu-id="fbd15-177">Indicates that one or more replicas is in automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-177">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="fbd15-178">**Manual**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-178">**Manual**.</span></span> <span data-ttu-id="fbd15-179">Indicates that no replica is automatic-failover mode.</span><span class="sxs-lookup"><span data-stu-id="fbd15-179">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="fbd15-180">**Synchronization State**</span><span class="sxs-lookup"><span data-stu-id="fbd15-180">**Synchronization State**</span></span>  
 <span data-ttu-id="fbd15-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="fbd15-182">This column is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-182">This column is shown by default.</span></span> <span data-ttu-id="fbd15-183">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-183">The possible values are:</span></span>  
  
-   <span data-ttu-id="fbd15-184">**Not Synchronized**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-184">**Not Synchronized**.</span></span> <span data-ttu-id="fbd15-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span><span class="sxs-lookup"><span data-stu-id="fbd15-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="fbd15-186">**Synchronizing**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-186">**Synchronizing**.</span></span> <span data-ttu-id="fbd15-187">One or more databases in the replica are being synchronized.</span><span class="sxs-lookup"><span data-stu-id="fbd15-187">One or more databases in the replica are being synchronized.</span></span>  
  
-   <span data-ttu-id="fbd15-188">**Synchronized**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-188">**Synchronized**.</span></span> <span data-ttu-id="fbd15-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbd15-190">In performance mode, the database is never in the synchronized state.</span><span class="sxs-lookup"><span data-stu-id="fbd15-190">In performance mode, the database is never in the synchronized state.</span></span>  
  
-   <span data-ttu-id="fbd15-191">**NULL**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-191">**NULL**.</span></span> <span data-ttu-id="fbd15-192">Unknown state.</span><span class="sxs-lookup"><span data-stu-id="fbd15-192">Unknown state.</span></span> <span data-ttu-id="fbd15-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span><span class="sxs-lookup"><span data-stu-id="fbd15-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>  
  
 <span data-ttu-id="fbd15-194">**Issues**</span><span class="sxs-lookup"><span data-stu-id="fbd15-194">**Issues**</span></span>  
 <span data-ttu-id="fbd15-195">Lists the issue name.</span><span class="sxs-lookup"><span data-stu-id="fbd15-195">Lists the issue name.</span></span> <span data-ttu-id="fbd15-196">This value is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-196">This value is shown by default.</span></span> <span data-ttu-id="fbd15-197">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-197">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="fbd15-198">**Availability Mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-198">**Availability Mode**</span></span>  
 <span data-ttu-id="fbd15-199">Indicates the replica property that you set separately for each availability replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-199">Indicates the replica property that you set separately for each availability replica.</span></span> <span data-ttu-id="fbd15-200">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-200">This value is hidden by default.</span></span> <span data-ttu-id="fbd15-201">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-201">The possible values are:</span></span>  
  
-   <span data-ttu-id="fbd15-202">**Asynchronous**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-202">**Asynchronous**.</span></span> <span data-ttu-id="fbd15-203">The secondary replica never becomes synchronized with the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-203">The secondary replica never becomes synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="fbd15-204">**Synchronous**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-204">**Synchronous**.</span></span> <span data-ttu-id="fbd15-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span></span>  
  
 <span data-ttu-id="fbd15-206">**Primary Connection Mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-206">**Primary Connection Mode**</span></span>  
 <span data-ttu-id="fbd15-207">Indicates the mode that is used to connect to the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-207">Indicates the mode that is used to connect to the primary replica.</span></span>  <span data-ttu-id="fbd15-208">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-208">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-209">**Secondary Connection Mode**</span><span class="sxs-lookup"><span data-stu-id="fbd15-209">**Secondary Connection Mode**</span></span>  
 <span data-ttu-id="fbd15-210">Indicates the mode that is used to connect to the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-210">Indicates the mode that is used to connect to the secondary replica.</span></span>  <span data-ttu-id="fbd15-211">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-211">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-212">**Connection State**</span><span class="sxs-lookup"><span data-stu-id="fbd15-212">**Connection State**</span></span>  
 <span data-ttu-id="fbd15-213">Indicates whether a secondary replica is currently connected to the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-213">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="fbd15-214">This column is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-214">This column is hidden by default.</span></span> <span data-ttu-id="fbd15-215">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-215">The possible values are:</span></span>  
  
-   <span data-ttu-id="fbd15-216">**Disconnected**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-216">**Disconnected**.</span></span> <span data-ttu-id="fbd15-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="fbd15-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span><span class="sxs-lookup"><span data-stu-id="fbd15-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span>  
  
    -   <span data-ttu-id="fbd15-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span><span class="sxs-lookup"><span data-stu-id="fbd15-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span>  
  
    -   <span data-ttu-id="fbd15-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>  
  
-   <span data-ttu-id="fbd15-221">**Connected**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-221">**Connected**.</span></span> <span data-ttu-id="fbd15-222">A remote availability replica that is currently connected to the local replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-222">A remote availability replica that is currently connected to the local replica.</span></span>  
  
 <span data-ttu-id="fbd15-223">**Operational State**</span><span class="sxs-lookup"><span data-stu-id="fbd15-223">**Operational State**</span></span>  
 <span data-ttu-id="fbd15-224">Indicates the current operational state of the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-224">Indicates the current operational state of the secondary replica.</span></span> <span data-ttu-id="fbd15-225">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-225">This value is hidden by default.</span></span> <span data-ttu-id="fbd15-226">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-226">The possible values are:</span></span>  
  
 <span data-ttu-id="fbd15-227">**0**. Pending failover</span><span class="sxs-lookup"><span data-stu-id="fbd15-227">**0**. Pending failover</span></span>    
 <span data-ttu-id="fbd15-228">**1**. Pending</span><span class="sxs-lookup"><span data-stu-id="fbd15-228">**1**. Pending</span></span>    
 <span data-ttu-id="fbd15-229">**2**. Online</span><span class="sxs-lookup"><span data-stu-id="fbd15-229">**2**. Online</span></span>    
 <span data-ttu-id="fbd15-230">**3**. Offline</span><span class="sxs-lookup"><span data-stu-id="fbd15-230">**3**. Offline</span></span>   
 <span data-ttu-id="fbd15-231">**4**. Failed</span><span class="sxs-lookup"><span data-stu-id="fbd15-231">**4**. Failed</span></span>    
 <span data-ttu-id="fbd15-232">**5**. Failed, no quorum</span><span class="sxs-lookup"><span data-stu-id="fbd15-232">**5**. Failed, no quorum</span></span>  
  
 <span data-ttu-id="fbd15-233">**NULL**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-233">**NULL**.</span></span> <span data-ttu-id="fbd15-234">Replica is not local</span><span class="sxs-lookup"><span data-stu-id="fbd15-234">Replica is not local</span></span>  
  
 <span data-ttu-id="fbd15-235">**Last Connection Error No.**</span><span class="sxs-lookup"><span data-stu-id="fbd15-235">**Last Connection Error No.**</span></span>  
 <span data-ttu-id="fbd15-236">Number of the last connection error.</span><span class="sxs-lookup"><span data-stu-id="fbd15-236">Number of the last connection error.</span></span>  <span data-ttu-id="fbd15-237">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-237">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-238">**Last Connection Error Description**</span><span class="sxs-lookup"><span data-stu-id="fbd15-238">**Last Connection Error Description**</span></span>  
 <span data-ttu-id="fbd15-239">Description of the last connection error.</span><span class="sxs-lookup"><span data-stu-id="fbd15-239">Description of the last connection error.</span></span>  <span data-ttu-id="fbd15-240">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-240">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-241">**Last Connection Error Timestamp**</span><span class="sxs-lookup"><span data-stu-id="fbd15-241">**Last Connection Error Timestamp**</span></span>  
 <span data-ttu-id="fbd15-242">Timestamp of the last connection error.</span><span class="sxs-lookup"><span data-stu-id="fbd15-242">Timestamp of the last connection error.</span></span> <span data-ttu-id="fbd15-243">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-243">This value is hidden by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbd15-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="group-by-availability-group-information"></a><span data-ttu-id="fbd15-245">Group by Availability Group information</span><span class="sxs-lookup"><span data-stu-id="fbd15-245">Group by Availability Group information</span></span>  
 <span data-ttu-id="fbd15-246">To group the information, click **Group by**, and select one of the following:</span><span class="sxs-lookup"><span data-stu-id="fbd15-246">To group the information, click **Group by**, and select one of the following:</span></span>  
  
-   <span data-ttu-id="fbd15-247">**Availability replicas**</span><span class="sxs-lookup"><span data-stu-id="fbd15-247">**Availability replicas**</span></span>    
-   <span data-ttu-id="fbd15-248">**Availability databases**</span><span class="sxs-lookup"><span data-stu-id="fbd15-248">**Availability databases**</span></span> 
-   <span data-ttu-id="fbd15-249">**Synchronization state**</span><span class="sxs-lookup"><span data-stu-id="fbd15-249">**Synchronization state**</span></span>  
-   <span data-ttu-id="fbd15-250">**Failover readiness**</span><span class="sxs-lookup"><span data-stu-id="fbd15-250">**Failover readiness**</span></span>   
-   <span data-ttu-id="fbd15-251">**Issues**</span><span class="sxs-lookup"><span data-stu-id="fbd15-251">**Issues**</span></span>  
  
 <span data-ttu-id="fbd15-252">The pane that displays the grouped information displays the following columns:</span><span class="sxs-lookup"><span data-stu-id="fbd15-252">The pane that displays the grouped information displays the following columns:</span></span>  
  
 <span data-ttu-id="fbd15-253">**Name**</span><span class="sxs-lookup"><span data-stu-id="fbd15-253">**Name**</span></span>  
 <span data-ttu-id="fbd15-254">The name of the availability database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-254">The name of the availability database.</span></span> <span data-ttu-id="fbd15-255">This value is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-255">This value is shown by default.</span></span>  
  
 <span data-ttu-id="fbd15-256">**Replica**</span><span class="sxs-lookup"><span data-stu-id="fbd15-256">**Replica**</span></span>  
 <span data-ttu-id="fbd15-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span> <span data-ttu-id="fbd15-258">This value is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-258">This value is shown by default.</span></span>  
  
 <span data-ttu-id="fbd15-259">**Synchronization State**</span><span class="sxs-lookup"><span data-stu-id="fbd15-259">**Synchronization State**</span></span>  
 <span data-ttu-id="fbd15-260">Indicates whether the availability database is currently synchronized with primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-260">Indicates whether the availability database is currently synchronized with primary replica.</span></span> <span data-ttu-id="fbd15-261">This value is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-261">This value is shown by default.</span></span> <span data-ttu-id="fbd15-262">The possible synchronization states are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-262">The possible synchronization states are:</span></span>  
  
-   <span data-ttu-id="fbd15-263">**Not synchronizing**:</span><span class="sxs-lookup"><span data-stu-id="fbd15-263">**Not synchronizing**:</span></span>  
-   
    -   <span data-ttu-id="fbd15-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span><span class="sxs-lookup"><span data-stu-id="fbd15-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span></span>   
    -   <span data-ttu-id="fbd15-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span><span class="sxs-lookup"><span data-stu-id="fbd15-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span></span>  
  
-   <span data-ttu-id="fbd15-266">**Synchronizing**:</span><span class="sxs-lookup"><span data-stu-id="fbd15-266">**Synchronizing**:</span></span>
-   
     <span data-ttu-id="fbd15-267">On a primary replica:</span><span class="sxs-lookup"><span data-stu-id="fbd15-267">On a primary replica:</span></span>   
    - <span data-ttu-id="fbd15-268">On a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-268">On a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span></span>  
    - <span data-ttu-id="fbd15-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span></span> 
  
  
-   <span data-ttu-id="fbd15-270">**Synchronized**:</span><span class="sxs-lookup"><span data-stu-id="fbd15-270">**Synchronized**:</span></span> 
  
    - <span data-ttu-id="fbd15-271">For a primary database, indicates that at least one secondary database is synchronized.</span><span class="sxs-lookup"><span data-stu-id="fbd15-271">For a primary database, indicates that at least one secondary database is synchronized.</span></span>
    - <span data-ttu-id="fbd15-272">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-272">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span></span>  
  
-   <span data-ttu-id="fbd15-273">**Reverting**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-273">**Reverting**.</span></span>  
  
     <span data-ttu-id="fbd15-274">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-274">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="fbd15-275">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span><span class="sxs-lookup"><span data-stu-id="fbd15-275">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span></span>  
  
-   <span data-ttu-id="fbd15-276">**Initializing**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-276">**Initializing**.</span></span>  
  
     <span data-ttu-id="fbd15-277">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-277">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="fbd15-278">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span><span class="sxs-lookup"><span data-stu-id="fbd15-278">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span></span>  
  
 <span data-ttu-id="fbd15-279">**Failover Readiness**</span><span class="sxs-lookup"><span data-stu-id="fbd15-279">**Failover Readiness**</span></span>  
 <span data-ttu-id="fbd15-280">Indicates which availability replica can be failed over with or without potential data loss.</span><span class="sxs-lookup"><span data-stu-id="fbd15-280">Indicates which availability replica can be failed over with or without potential data loss.</span></span> <span data-ttu-id="fbd15-281">This column is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-281">This column is shown by default.</span></span> <span data-ttu-id="fbd15-282">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-282">The possible values are:</span></span>  
  
-   <span data-ttu-id="fbd15-283">**Data Loss**</span><span class="sxs-lookup"><span data-stu-id="fbd15-283">**Data Loss**</span></span>   
-   <span data-ttu-id="fbd15-284">**No Data Loss**</span><span class="sxs-lookup"><span data-stu-id="fbd15-284">**No Data Loss**</span></span>  
  
 <span data-ttu-id="fbd15-285">**Issues**</span><span class="sxs-lookup"><span data-stu-id="fbd15-285">**Issues**</span></span>  
 <span data-ttu-id="fbd15-286">Lists the issue name.</span><span class="sxs-lookup"><span data-stu-id="fbd15-286">Lists the issue name.</span></span> <span data-ttu-id="fbd15-287">This column is shown by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-287">This column is shown by default.</span></span> <span data-ttu-id="fbd15-288">The possible values are:</span><span class="sxs-lookup"><span data-stu-id="fbd15-288">The possible values are:</span></span>  
  
-   <span data-ttu-id="fbd15-289">**Warnings**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-289">**Warnings**.</span></span> <span data-ttu-id="fbd15-290">Click to display the thresholds and warnings issues.</span><span class="sxs-lookup"><span data-stu-id="fbd15-290">Click to display the thresholds and warnings issues.</span></span>   
-   <span data-ttu-id="fbd15-291">**Critical**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-291">**Critical**.</span></span> <span data-ttu-id="fbd15-292">Click to display the critical issues.</span><span class="sxs-lookup"><span data-stu-id="fbd15-292">Click to display the critical issues.</span></span>  
  
 <span data-ttu-id="fbd15-293">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-293">For a list of all the Always On policy issues, see [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="fbd15-294">**Suspended**</span><span class="sxs-lookup"><span data-stu-id="fbd15-294">**Suspended**</span></span>  
 <span data-ttu-id="fbd15-295">Indicates whether the database is **Suspended** or has been **Resumed**.</span><span class="sxs-lookup"><span data-stu-id="fbd15-295">Indicates whether the database is **Suspended** or has been **Resumed**.</span></span> <span data-ttu-id="fbd15-296">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-296">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-297">**Suspend Reason**</span><span class="sxs-lookup"><span data-stu-id="fbd15-297">**Suspend Reason**</span></span>  
 <span data-ttu-id="fbd15-298">Indicates the reason for the suspended state.</span><span class="sxs-lookup"><span data-stu-id="fbd15-298">Indicates the reason for the suspended state.</span></span> <span data-ttu-id="fbd15-299">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-299">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-300">**Estimate Data Loss (seconds)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-300">**Estimate Data Loss (seconds)**</span></span>  
 <span data-ttu-id="fbd15-301">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-301">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span></span> <span data-ttu-id="fbd15-302">If the primary replica fails, all transaction log records within the time window will be lost.</span><span class="sxs-lookup"><span data-stu-id="fbd15-302">If the primary replica fails, all transaction log records within the time window will be lost.</span></span> <span data-ttu-id="fbd15-303">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-303">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-304">**Estimated Recovery Time (seconds)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-304">**Estimated Recovery Time (seconds)**</span></span>  
 <span data-ttu-id="fbd15-305">Indicates the time in seconds it takes to redo the catch-up time.</span><span class="sxs-lookup"><span data-stu-id="fbd15-305">Indicates the time in seconds it takes to redo the catch-up time.</span></span> <span data-ttu-id="fbd15-306">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-306">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span></span> <span data-ttu-id="fbd15-307">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-307">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-308">**Synchronization Performance (seconds)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-308">**Synchronization Performance (seconds)**</span></span>  
 <span data-ttu-id="fbd15-309">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span><span class="sxs-lookup"><span data-stu-id="fbd15-309">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span></span> <span data-ttu-id="fbd15-310">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-310">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-311">**Log Send Queue Size (KB)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-311">**Log Send Queue Size (KB)**</span></span>  
 <span data-ttu-id="fbd15-312">Indicates the number of log records in the log files of the primary database that have not been sent to the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-312">Indicates the number of log records in the log files of the primary database that have not been sent to the secondary replica.</span></span> <span data-ttu-id="fbd15-313">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-313">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-314">**Log Send Rate (KB/sec)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-314">**Log Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="fbd15-315">Indicates the rate in KB per second at which log records are being sent to the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-315">Indicates the rate in KB per second at which log records are being sent to the secondary replica.</span></span> <span data-ttu-id="fbd15-316">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-316">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-317">**Redo Queue Size (KB)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-317">**Redo Queue Size (KB)**</span></span>  
 <span data-ttu-id="fbd15-318">Indicates the number of log records in the log files of the secondary replica that have not yet been redone.</span><span class="sxs-lookup"><span data-stu-id="fbd15-318">Indicates the number of log records in the log files of the secondary replica that have not yet been redone.</span></span> <span data-ttu-id="fbd15-319">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-319">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-320">**Redo Rate (KB/sec)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-320">**Redo Rate (KB/sec)**</span></span>  
 <span data-ttu-id="fbd15-321">Indicates the rate in KB per second at which the log records are being redone.</span><span class="sxs-lookup"><span data-stu-id="fbd15-321">Indicates the rate in KB per second at which the log records are being redone.</span></span> <span data-ttu-id="fbd15-322">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-322">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-323">**FileStream Send Rate (KB/sec)**</span><span class="sxs-lookup"><span data-stu-id="fbd15-323">**FileStream Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="fbd15-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span></span> <span data-ttu-id="fbd15-325">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-325">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-326">**End of Log LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-326">**End of Log LSN**</span></span>  
 <span data-ttu-id="fbd15-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span><span class="sxs-lookup"><span data-stu-id="fbd15-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span></span> <span data-ttu-id="fbd15-328">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-328">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-329">**Recovery LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-329">**Recovery LSN**</span></span>  
 <span data-ttu-id="fbd15-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span></span> <span data-ttu-id="fbd15-331">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-331">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-332">**Truncation LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-332">**Truncation LSN**</span></span>  
 <span data-ttu-id="fbd15-333">Indicates the minimum log truncation value for the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-333">Indicates the minimum log truncation value for the primary replica.</span></span> <span data-ttu-id="fbd15-334">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-334">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-335">**Last Commit LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-335">**Last Commit LSN**</span></span>  
 <span data-ttu-id="fbd15-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span><span class="sxs-lookup"><span data-stu-id="fbd15-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span></span> <span data-ttu-id="fbd15-337">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-337">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-338">**Last Commit Time**</span><span class="sxs-lookup"><span data-stu-id="fbd15-338">**Last Commit Time**</span></span>  
 <span data-ttu-id="fbd15-339">Indicates the time corresponding to the last commit record.</span><span class="sxs-lookup"><span data-stu-id="fbd15-339">Indicates the time corresponding to the last commit record.</span></span> <span data-ttu-id="fbd15-340">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-340">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-341">**Last Sent LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-341">**Last Sent LSN**</span></span>  
 <span data-ttu-id="fbd15-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span></span> <span data-ttu-id="fbd15-343">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-343">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-344">**Last Sent Time**</span><span class="sxs-lookup"><span data-stu-id="fbd15-344">**Last Sent Time**</span></span>  
 <span data-ttu-id="fbd15-345">Indicates the time when the last log block was sent.</span><span class="sxs-lookup"><span data-stu-id="fbd15-345">Indicates the time when the last log block was sent.</span></span> <span data-ttu-id="fbd15-346">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-346">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-347">**Last Received LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-347">**Last Received LSN**</span></span>  
 <span data-ttu-id="fbd15-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span></span> <span data-ttu-id="fbd15-349">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-349">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-350">**Last Received Time**</span><span class="sxs-lookup"><span data-stu-id="fbd15-350">**Last Received Time**</span></span>  
 <span data-ttu-id="fbd15-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span></span> <span data-ttu-id="fbd15-352">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-352">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-353">**Last Hardened LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-353">**Last Hardened LSN**</span></span>  
 <span data-ttu-id="fbd15-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span></span> <span data-ttu-id="fbd15-355">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-355">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-356">**Last Hardened Time**</span><span class="sxs-lookup"><span data-stu-id="fbd15-356">**Last Hardened Time**</span></span>  
 <span data-ttu-id="fbd15-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span></span> <span data-ttu-id="fbd15-358">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-358">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-359">**Last Redone LSN**</span><span class="sxs-lookup"><span data-stu-id="fbd15-359">**Last Redone LSN**</span></span>  
 <span data-ttu-id="fbd15-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span><span class="sxs-lookup"><span data-stu-id="fbd15-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span></span> <span data-ttu-id="fbd15-361">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-361">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="fbd15-362">**Last Redone Time**</span><span class="sxs-lookup"><span data-stu-id="fbd15-362">**Last Redone Time**</span></span>  
 <span data-ttu-id="fbd15-363">Indicates the time when the last log record was redone on the secondary database.</span><span class="sxs-lookup"><span data-stu-id="fbd15-363">Indicates the time when the last log record was redone on the secondary database.</span></span> <span data-ttu-id="fbd15-364">This value is hidden by default.</span><span class="sxs-lookup"><span data-stu-id="fbd15-364">This value is hidden by default.</span></span>  
 

   > [!NOTE]  
   >  <span data-ttu-id="fbd15-365">Most data is based on sys.dm_hadr_database_replica_states, so some restriction may apply.</span><span class="sxs-lookup"><span data-stu-id="fbd15-365">Most data is based on sys.dm_hadr_database_replica_states, so some restriction may apply.</span></span> <span data-ttu-id="fbd15-366">For more information, please see [sys.dm_hadr_database_replica_states (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fbd15-366">For more information, please see [sys.dm_hadr_database_replica_states (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md).</span></span>


## <a name="always-on-availability-group-latency-reports"></a><span data-ttu-id="fbd15-367">Always On Availability Group latency reports</span><span class="sxs-lookup"><span data-stu-id="fbd15-367">Always On Availability Group latency reports</span></span>
<span data-ttu-id="fbd15-368">The availability group latency report is a reporting tool built into the availability group dashboard and available in the [SQL Server Management Studio 17.4](../../../ssms/download-sql-server-management-studio-ssms.md) release.</span><span class="sxs-lookup"><span data-stu-id="fbd15-368">The availability group latency report is a reporting tool built into the availability group dashboard and available in the [SQL Server Management Studio 17.4](../../../ssms/download-sql-server-management-studio-ssms.md) release.</span></span> <span data-ttu-id="fbd15-369">This feature provides an easy-to-understand report detailing time spent during various phases of the log transport process.</span><span class="sxs-lookup"><span data-stu-id="fbd15-369">This feature provides an easy-to-understand report detailing time spent during various phases of the log transport process.</span></span> <span data-ttu-id="fbd15-370">This provides a way to narrow down the potential cause of latency during the synchronization process.</span><span class="sxs-lookup"><span data-stu-id="fbd15-370">This provides a way to narrow down the potential cause of latency during the synchronization process.</span></span> 

<span data-ttu-id="fbd15-371">SQL Agent runs the data collection and must be enabled on both the primary replica, and at least one of the secondary replicas.</span><span class="sxs-lookup"><span data-stu-id="fbd15-371">SQL Agent runs the data collection and must be enabled on both the primary replica, and at least one of the secondary replicas.</span></span> <span data-ttu-id="fbd15-372">View the report by right-clicking the availability group > Reports > Standard Reports in **Object Explorer** of SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="fbd15-372">View the report by right-clicking the availability group > Reports > Standard Reports in **Object Explorer** of SQL Server Management Studio.</span></span>  

<span data-ttu-id="fbd15-373">For more information, please see [Always On Availability Group latency reports](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-always-on-availability-group-latency-reports/).</span><span class="sxs-lookup"><span data-stu-id="fbd15-373">For more information, please see [Always On Availability Group latency reports](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-always-on-availability-group-latency-reports/).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="fbd15-374">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fbd15-374">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fbd15-375">Use Always On Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbd15-375">Use Always On Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbd15-376">See Also</span><span class="sxs-lookup"><span data-stu-id="fbd15-376">See Also</span></span>  
 <span data-ttu-id="fbd15-377">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="fbd15-377">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) </span></span>  
 [<span data-ttu-id="fbd15-378">Monitoring of Availability Groups &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbd15-378">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  
