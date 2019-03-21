---
title: Create and deploy a Windows Defender Application Guard policy
titleSuffix: Configuration Manager
description: Create and deploy Windows Defender Application Guard policy.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 33a6c1d9-4dd8-411c-a748-693a5bd2ea5a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
---


# <a name="create-and-deploy-windows-defender-application-guard-policy"></a><span data-ttu-id="d52ca-103">Create and deploy Windows Defender Application Guard policy</span><span class="sxs-lookup"><span data-stu-id="d52ca-103">Create and deploy Windows Defender Application Guard policy</span></span> 
<span data-ttu-id="d52ca-104">*Applies to: System Center Configuration Manager (Current Branch)*</span><span class="sxs-lookup"><span data-stu-id="d52ca-104">*Applies to: System Center Configuration Manager (Current Branch)*</span></span>
<!-- 1351960 -->  
<span data-ttu-id="d52ca-105">You can create and deploy [Windows Defender Application Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) policies by using the Configuration Manager endpoint protection.</span><span class="sxs-lookup"><span data-stu-id="d52ca-105">You can create and deploy [Windows Defender Application Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) policies by using the Configuration Manager endpoint protection.</span></span> <span data-ttu-id="d52ca-106">These policies help protect your users by opening untrusted web sites in a secure isolated container that is not accessible by other parts of the operating system.</span><span class="sxs-lookup"><span data-stu-id="d52ca-106">These policies help protect your users by opening untrusted web sites in a secure isolated container that is not accessible by other parts of the operating system.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d52ca-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d52ca-107">Prerequisites</span></span>

<span data-ttu-id="d52ca-108">To create and deploy a Windows Defender Application Guard policy, you must use the Windows 10 Fall Creator’s Update (1709).</span><span class="sxs-lookup"><span data-stu-id="d52ca-108">To create and deploy a Windows Defender Application Guard policy, you must use the Windows 10 Fall Creator’s Update (1709).</span></span> <span data-ttu-id="d52ca-109">Also, the Windows 10 devices to which you deploy the policy must be configured with a network isolation policy.</span><span class="sxs-lookup"><span data-stu-id="d52ca-109">Also, the Windows 10 devices to which you deploy the policy must be configured with a network isolation policy.</span></span> <span data-ttu-id="d52ca-110">For more information, see the [Windows Defender Application Guard overview](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview).</span><span class="sxs-lookup"><span data-stu-id="d52ca-110">For more information, see the [Windows Defender Application Guard overview](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview).</span></span> 


## <a name="create-a-policy-and-to-browse-the-available-settings"></a><span data-ttu-id="d52ca-111">Create a policy, and to browse the available settings:</span><span class="sxs-lookup"><span data-stu-id="d52ca-111">Create a policy, and to browse the available settings:</span></span>

1. <span data-ttu-id="d52ca-112">In the Configuration Manager console, choose **Assets and Compliance**.</span><span class="sxs-lookup"><span data-stu-id="d52ca-112">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>
2. <span data-ttu-id="d52ca-113">In the **Assets and Compliance** workspace, choose **Overview** > **Endpoint Protection** > **Windows Defender Application Guard**.</span><span class="sxs-lookup"><span data-stu-id="d52ca-113">In the **Assets and Compliance** workspace, choose **Overview** > **Endpoint Protection** > **Windows Defender Application Guard**.</span></span>
3. <span data-ttu-id="d52ca-114">In the **Home** tab, in the **Create** group, click **Create Windows Defender Application Guard Policy**.</span><span class="sxs-lookup"><span data-stu-id="d52ca-114">In the **Home** tab, in the **Create** group, click **Create Windows Defender Application Guard Policy**.</span></span>
4. <span data-ttu-id="d52ca-115">Using the [article](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard) as a reference, you can browse and configure the available settings.</span><span class="sxs-lookup"><span data-stu-id="d52ca-115">Using the [article](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard) as a reference, you can browse and configure the available settings.</span></span> <span data-ttu-id="d52ca-116">Configuration Manager allows you to set certain policy settings see [host interaction settings](#BKMK_HIS) and [application behavior](#BKMK_AppB).</span><span class="sxs-lookup"><span data-stu-id="d52ca-116">Configuration Manager allows you to set certain policy settings see [host interaction settings](#BKMK_HIS) and [application behavior](#BKMK_AppB).</span></span>
5. <span data-ttu-id="d52ca-117">On the **Network Definition** page, specify the corporate identity, and define your corporate network boundary.</span><span class="sxs-lookup"><span data-stu-id="d52ca-117">On the **Network Definition** page, specify the corporate identity, and define your corporate network boundary.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d52ca-118">Windows 10 PCs store only one network isolation list on the client.</span><span class="sxs-lookup"><span data-stu-id="d52ca-118">Windows 10 PCs store only one network isolation list on the client.</span></span> <span data-ttu-id="d52ca-119">You can create two different kinds of network isolation lists and deploy them to the client:</span><span class="sxs-lookup"><span data-stu-id="d52ca-119">You can create two different kinds of network isolation lists and deploy them to the client:</span></span>
    >
    >  - <span data-ttu-id="d52ca-120">one from Windows Information Protection</span><span class="sxs-lookup"><span data-stu-id="d52ca-120">one from Windows Information Protection</span></span>
    >  - <span data-ttu-id="d52ca-121">one from Windows Defender Application Guard</span><span class="sxs-lookup"><span data-stu-id="d52ca-121">one from Windows Defender Application Guard</span></span>
    >
    > <span data-ttu-id="d52ca-122">If you deploy both policies, these network isolation lists must match.</span><span class="sxs-lookup"><span data-stu-id="d52ca-122">If you deploy both policies, these network isolation lists must match.</span></span> <span data-ttu-id="d52ca-123">If you deploy lists that don’t match to the same client, the deployment will fail.</span><span class="sxs-lookup"><span data-stu-id="d52ca-123">If you deploy lists that don’t match to the same client, the deployment will fail.</span></span> <span data-ttu-id="d52ca-124">For more information, see the [Windows Information Protection documentation](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).</span><span class="sxs-lookup"><span data-stu-id="d52ca-124">For more information, see the [Windows Information Protection documentation](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).</span></span>
    > 
    > 

6. <span data-ttu-id="d52ca-125">When you are finished, complete the wizard, and deploy the policy to one or more Windows 10 1709 devices.</span><span class="sxs-lookup"><span data-stu-id="d52ca-125">When you are finished, complete the wizard, and deploy the policy to one or more Windows 10 1709 devices.</span></span>

### <a name="bkmk_HIS"></a> <span data-ttu-id="d52ca-126">Host interaction settings</span><span class="sxs-lookup"><span data-stu-id="d52ca-126">Host interaction settings</span></span>
<span data-ttu-id="d52ca-127">Configures interactions between host devices and the Application Guard container.</span><span class="sxs-lookup"><span data-stu-id="d52ca-127">Configures interactions between host devices and the Application Guard container.</span></span> <span data-ttu-id="d52ca-128">Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.</span><span class="sxs-lookup"><span data-stu-id="d52ca-128">Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.</span></span>

- <span data-ttu-id="d52ca-129">**Clipboard** - Under settings prior to Configuration Manager 1802</span><span class="sxs-lookup"><span data-stu-id="d52ca-129">**Clipboard** - Under settings prior to Configuration Manager 1802</span></span>
    - <span data-ttu-id="d52ca-130">Permitted content type</span><span class="sxs-lookup"><span data-stu-id="d52ca-130">Permitted content type</span></span>
        - <span data-ttu-id="d52ca-131">Text</span><span class="sxs-lookup"><span data-stu-id="d52ca-131">Text</span></span>
        - <span data-ttu-id="d52ca-132">Images</span><span class="sxs-lookup"><span data-stu-id="d52ca-132">Images</span></span>
- <span data-ttu-id="d52ca-133">**Printing:**</span><span class="sxs-lookup"><span data-stu-id="d52ca-133">**Printing:**</span></span>
    - <span data-ttu-id="d52ca-134">Enable printing to XPS</span><span class="sxs-lookup"><span data-stu-id="d52ca-134">Enable printing to XPS</span></span>
    - <span data-ttu-id="d52ca-135">Enable printing to PDF</span><span class="sxs-lookup"><span data-stu-id="d52ca-135">Enable printing to PDF</span></span>
    - <span data-ttu-id="d52ca-136">Enable printing to local printers</span><span class="sxs-lookup"><span data-stu-id="d52ca-136">Enable printing to local printers</span></span>
    - <span data-ttu-id="d52ca-137">Enable printing to network printers</span><span class="sxs-lookup"><span data-stu-id="d52ca-137">Enable printing to network printers</span></span>
- <span data-ttu-id="d52ca-138">**Graphics:** (starting with Configuration Manager version 1802)</span><span class="sxs-lookup"><span data-stu-id="d52ca-138">**Graphics:** (starting with Configuration Manager version 1802)</span></span>
    - <span data-ttu-id="d52ca-139">Virtual graphics processor access</span><span class="sxs-lookup"><span data-stu-id="d52ca-139">Virtual graphics processor access</span></span>
- <span data-ttu-id="d52ca-140">**Files:** (starting with Configuration Manager version 1802)</span><span class="sxs-lookup"><span data-stu-id="d52ca-140">**Files:** (starting with Configuration Manager version 1802)</span></span>
    - <span data-ttu-id="d52ca-141">Save downloaded files to host</span><span class="sxs-lookup"><span data-stu-id="d52ca-141">Save downloaded files to host</span></span>

### <a name="bkmk_ABS"></a> <span data-ttu-id="d52ca-142">Application behavior settings</span><span class="sxs-lookup"><span data-stu-id="d52ca-142">Application behavior settings</span></span>
<span data-ttu-id="d52ca-143">Configures application behavior inside the Application Guard session.</span><span class="sxs-lookup"><span data-stu-id="d52ca-143">Configures application behavior inside the Application Guard session.</span></span> <span data-ttu-id="d52ca-144">Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.</span><span class="sxs-lookup"><span data-stu-id="d52ca-144">Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.</span></span>

- <span data-ttu-id="d52ca-145">**Content:**</span><span class="sxs-lookup"><span data-stu-id="d52ca-145">**Content:**</span></span>
   - <span data-ttu-id="d52ca-146">Enterprise sites can load non-enterprise content, such as third-party plug-ins.</span><span class="sxs-lookup"><span data-stu-id="d52ca-146">Enterprise sites can load non-enterprise content, such as third-party plug-ins.</span></span>
- <span data-ttu-id="d52ca-147">**Other:**</span><span class="sxs-lookup"><span data-stu-id="d52ca-147">**Other:**</span></span>
    - <span data-ttu-id="d52ca-148">Retain user generated browser data</span><span class="sxs-lookup"><span data-stu-id="d52ca-148">Retain user generated browser data</span></span>
    - <span data-ttu-id="d52ca-149">Audit security events in the isolated application guard session</span><span class="sxs-lookup"><span data-stu-id="d52ca-149">Audit security events in the isolated application guard session</span></span>



## <a name="next-steps"></a><span data-ttu-id="d52ca-150">Next steps</span><span class="sxs-lookup"><span data-stu-id="d52ca-150">Next steps</span></span>
<span data-ttu-id="d52ca-151">To read more about Windows Defender Application Guard: [Windows Defender Application Guard Overview](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview).</span><span class="sxs-lookup"><span data-stu-id="d52ca-151">To read more about Windows Defender Application Guard: [Windows Defender Application Guard Overview](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview).</span></span>
<span data-ttu-id="d52ca-152">[Windows Defender Application Guard FAQ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/faq-wd-app-guard).</span><span class="sxs-lookup"><span data-stu-id="d52ca-152">[Windows Defender Application Guard FAQ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/faq-wd-app-guard).</span></span>
