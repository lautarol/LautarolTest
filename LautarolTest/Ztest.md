---
title: When and how should I file a bug report?
ms.topic: article
ms.prod: xamarin
ms.assetid: 8AD9CFBF-282A-4C1F-95E9-25F21141B052
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
---

10. blalflasdlasldasldsald

11. blalflasdlasldasldsald

12. blalflasdlasldasldsald
    
    - blalflasdlasldasldsald 
    
    - blalflasdlasldasldsald
    
    - blalflasdlasldasldsald 

7. If you selected **Set permissions** for **Azure (cloud key)**, this option lets you configure the same settings that you can configure in a template. 
    
    Select **Add permissions**, and on the **Add permissions** blade, select the first set of users and groups who will have rights to use the content that will be protected by the selected label:
    
    - Choose **Select from the list** where you can then add all users from your organization by selecting **Add \<organization name> - All members**. This setting excludes guest accounts. Or, you can select **Add any authenticated users**, or browse the directory.
        
        When you choose all members or browse the directory, the users or groups must have an email address. In a production environment, users and groups nearly always have an email address, but in a simple testing environment, you might need to add email addresses to user accounts or groups.
        
        ###### More information about **Add any authenticated users** 
        This setting doesn't restrict who can access the content that the label protects, while still encrypting the content and providing you with options to restrict how the content can be used (permissions), and accessed (expiry and offline access). However, the application opening the protected content must be able to support the authentication being used. For this reason, federated social providers such as Google, and onetime passcode authentication should be used for email only, and only when you use Exchange Online and the new capabilities from Office 365 Message Encryption. Microsoft accounts can be used with the Azure Information Protection viewer and Office 2016 Click-to-Run. 
          
        Some typical scenarios for the any authenticated users setting:
            - You don't mind who views the content, but you want to restrict how it is used. For example, you do not want the content to be edited, copied, or printed.  
            - You don't need to restrict who accesses the content, but you want to be able to track who opens it and potentially, revoke it.  
            - You have a requirement that the content must be encrypted at rest and in transit, but it doesn't require access controls.
        
    - Choose **Enter details** to manually specify email addresses for individual users or groups (internal or external). Or, use this option to specify all users in another organization by entering any domain name from that organization. You can also use this option for social providers, by entering their domain name such as **gmail.com**, **hotmail.com**, or **outlook.com**.

-   <span data-ttu-id="cc05c-167">각 ATA 센터는 Active Directory 포리스트 하나를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc05c-167">One ATA Center can monitor a single Active Directory forest.</span></span> <span data-ttu-id="cc05c-168">Active Directory 포리스트가 둘 이상인 경우에는 Active Directory 포리스트당 최소 하나의 ATA 센터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cc05c-168">If you have more than one Active Directory forest, you need a minimum of one ATA Center per Active Directory forest.</span></span>

-    <span data-ttu-id="cc05c-169">대규모 Active Directory 배포에서는 ATA 센터 하나가 모든 도메인 컨트롤러의 트래픽을 모두 처리하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc05c-169">In large Active Directory deployments, a single ATA Center might not be able to handle all the traffic of all your domain controllers.</span></span> <span data-ttu-id="cc05c-170">이 경우 ATA 센터가 여러 개 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc05c-170">In this case, multiple ATA Centers are required.</span></span> <span data-ttu-id="cc05c-171">ATA 센터의 수는 [ATA 용량 계획](ata-capacity-planning.md)에 따라 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc05c-171">The number of ATA Centers should be dictated by [ATA capacity planning](ata-capacity-planning.md).</span></span>






|<span data-ttu-id="5d6ca-101">Part</span><span class="sxs-lookup"><span data-stu-id="5d6ca-101">Part</span></span>|<span data-ttu-id="5d6ca-102">Description</span><span class="sxs-lookup"><span data-stu-id="5d6ca-102">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="5d6ca-103">Required.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-103">Required.</span></span> <span data-ttu-id="5d6ca-104">Terminates the definition of the programming element.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-104">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="5d6ca-105">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-105">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="5d6ca-106">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-106">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="5d6ca-107">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-107">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="5d6ca-108">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-108">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="5d6ca-109">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-109">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="5d6ca-110">If execution encounters an `End Function` statement, control returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-110">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="5d6ca-111">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-111">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="5d6ca-112">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-112">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="5d6ca-113">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-113">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="5d6ca-114">See [If...Then...Else Statement](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-114">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="5d6ca-115">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-115">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="5d6ca-116">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-116">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="5d6ca-117">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-117">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="5d6ca-118">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-118">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="5d6ca-119">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-119">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="5d6ca-120">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-120">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="5d6ca-121">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-121">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="5d6ca-122">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-122">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="5d6ca-123">See [Select...Case Statement](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-123">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="5d6ca-124">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-124">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="5d6ca-125">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-125">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="5d6ca-126">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-126">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="5d6ca-127">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-127">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="5d6ca-128">If execution encounters an `End Sub` statement, control returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-128">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="5d6ca-129">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-129">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="5d6ca-130">See [SyncLock Statement](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-130">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="5d6ca-131">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-131">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="5d6ca-132">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-132">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="5d6ca-133">Required to terminate a `While` loop definition begun by a matching `While` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-133">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="5d6ca-134">See [While...End While Statement](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-134">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="5d6ca-135">Required to terminate a `With` block definition begun by a matching `With` statement.</span><span class="sxs-lookup"><span data-stu-id="5d6ca-135">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="5d6ca-136">See [With...End With Statement](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ca-136">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  






## How to integrate Azure ATP with Windows Defender ATP

1. Set the workspace you want to integrate as **Primary**. Only one workspace can be the Primary workspace and only a primary workspace can integrate with other services. If, at some point in the future, you should want to make this workspace no longer the primary workspace, you will first have to remove the integration before you can set it as non-primary.

 ![primary workspace](./media/primary-workspace.png)

2. Click **Configuration**, and under **Data sources** select **Windows Defender ATP**. Then click the link to **Workspace management**. This is only available if you have a license for Windows Defender ATP and you already performed the on-boarding process for Windows Defender ATP. 

3. In your primary workspace, click the settings cog.

 ![workspace integration](./media/edit-workspace.png)
 
3. Set the integration to **On**. 

 ![enable integration](./media/enable-integration.png)

4. In the [Windows Defender ATP portal](https://beta.securitycenter.windows.com/preferences/advanced), go to **Settings**, **Advanced features** and set **Azure ATP integration** to **ON**. 

 ![Windows Defender ATP enable integration](./media/wd-atp-enable.png)

5. To check the status of the integration, in the Azure ATP workspace portal, go to **Settings** and then **Windows Defender ATP integration**. You can see the status of the integration; if something is wrong you see an error. You can also see which workspace is integrated with Windows Defender ATP.


test test 




## How to integrate Azure ATP with Windows Defender ATP

1. Set the workspace you want to integrate as **Primary**. Only one workspace can be the Primary workspace and only a primary workspace can integrate with other services. If, at some point in the future, you should want to make this workspace no longer the primary workspace, you will first have to remove the integration before you can set it as non-primary.

 ![primary workspace](./media/primary-workspace.png)

2. Click **Configuration**, and under **Data sources** select **Windows Defender ATP**. Then click the link to **Workspace management**. This is only available if you have a license for Windows Defender ATP and you already performed the on-boarding process for Windows Defender ATP. 

3. In your primary workspace, click the settings cog.

 ![workspace integration](./media/edit-workspace.png)

3. Set the integration to **On**. 

 ![enable integration](./media/enable-integration.png)

4. In the [Windows Defender ATP portal](https://beta.securitycenter.windows.com/preferences/advanced), go to **Settings**, **Advanced features** and set **Azure ATP integration** to **ON**. 

 ![Windows Defender ATP enable integration](./media/wd-atp-enable.png)

5. To check the status of the integration, in the Azure ATP workspace portal, go to **Settings** and then **Windows Defender ATP integration**. You can see the status of the integration; if something is wrong you see an error. You can also see which workspace is integrated with Windows Defender ATP.


## Instructions to Create a Remoting Endpoint

PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.
For more information, see:

- [SSH Remoting in PowerShell Core][ssh-remoting]
- [WSMan Remoting in PowerShell Core][wsman-remoting]

## Artifact Installation Instructions

We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].

To install PowerShell Core from the CoreCLR Artifact:

1. Download ZIP package from *artifacts* tab of the particular build.
2. Unblock ZIP file: right-click in File Explorer -> Properties ->
   check 'Unblock' box -> apply
3. Extract zip file to `bin` directory
4. `./bin/pwsh.exe`



<span data-ttu-id="5902f-108">Protokoly ATA Gateway jsou umístěné v podsložce s názvem **Protokoly** v místě, kde je služba ATA nainstalovaná. Výchozí umístění je **C:\Program Files\Microsoft Advanced Threat Analytics\** .</span><span class="sxs-lookup"><span data-stu-id="5902f-108">The ATA Gateway logs are located in a subfolder called **Logs** where ATA is installed; the default location is: **C:\Program Files\Microsoft Advanced Threat Analytics\**.</span></span> <span data-ttu-id="5902f-109">Ve výchozí instalaci ji najdete tady: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.</span><span class="sxs-lookup"><span data-stu-id="5902f-109">In the default installation location, it can be found at: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.</span></span>

<span data-ttu-id="5902f-108">Protokoly ATA Gateway jsou umístěné v podsložce s názvem **Protokoly** v místě, kde je služba ATA nainstalovaná. Výchozí umístění je **C:\Program Files\Microsoft Advanced Threat Analytics\**.</span><span class="sxs-lookup"><span data-stu-id="5902f-108">The ATA Gateway logs are located in a subfolder called **Logs** where ATA is installed; the default location is: **C:\Program Files\Microsoft Advanced Threat Analytics\**.</span></span> <span data-ttu-id="5902f-109">Ve výchozí instalaci ji najdete tady: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.</span><span class="sxs-lookup"><span data-stu-id="5902f-109">In the default installation location, it can be found at: **C:\Program Files\Microsoft Advanced Threat Analytics\Gateway\Logs**.</span></span>









|Azure ATP standalone sensor|Domain Controller|Considerations|
|---------------|---------------------|------------------|
|Virtual|Virtual on same host|The virtual switch needs to support port mirroring.<br /><br />Moving one of the virtual machines to another host by itself may break the port mirroring.|
|Virtual|Virtual on different hosts|Make sure your virtual switch supports this scenario.|
|Virtual|Physical|Requires a dedicated network adapter otherwise Azure ATP sees all of the traffic coming in and out of the host, even the traffic it sends to the Azure ATP cloud service.|

|Physical|Virtual|Make sure your virtual switch supports this scenario - and port mirroring configuration on your physical switches based on the scenario:<br /><br />If the virtual host is on the same physical switch, you need to configure a switch level span.<br /><br />If the virtual host is on a different switch, you need to configure RSPAN or ERSPAN&#42;.|
|Physical|Physical on the same switch|Physical switch must support SPAN/Port Mirroring.|
|Physical|Physical on a different switch|Requires physical switches to support RSPAN or ERSPAN&#42;.|
&#42; ERSPAN is only supported when decapsulation is performed before the traffic is analyzed by ATP.


|<span data-ttu-id="d440a-132">Azure ATP 獨立感應器</span><span class="sxs-lookup"><span data-stu-id="d440a-132">Azure ATP standalone sensor</span></span>|<span data-ttu-id="d440a-133">網域控制站</span><span class="sxs-lookup"><span data-stu-id="d440a-133">Domain Controller</span></span>|<span data-ttu-id="d440a-134">考量</span><span class="sxs-lookup"><span data-stu-id="d440a-134">Considerations</span></span>|
|---------------|---------------------|------------------|
|<span data-ttu-id="d440a-135">網路</span><span class="sxs-lookup"><span data-stu-id="d440a-135">Virtual</span></span>|<span data-ttu-id="d440a-136">相同主機上的虛擬</span><span class="sxs-lookup"><span data-stu-id="d440a-136">Virtual on same host</span></span>|<span data-ttu-id="d440a-137">虛擬交換器需要支援連接埠鏡像。</span><span class="sxs-lookup"><span data-stu-id="d440a-137">The virtual switch needs to support port mirroring.</span></span><br /><br /><span data-ttu-id="d440a-138">將其中一部虛擬機器本身單獨移至另一個主機，可能會中斷連接埠鏡像。</span><span class="sxs-lookup"><span data-stu-id="d440a-138">Moving one of the virtual machines to another host by itself may break the port mirroring.</span></span>|
|<span data-ttu-id="d440a-139">網路</span><span class="sxs-lookup"><span data-stu-id="d440a-139">Virtual</span></span>|<span data-ttu-id="d440a-140">不同主機上的虛擬</span><span class="sxs-lookup"><span data-stu-id="d440a-140">Virtual on different hosts</span></span>|<span data-ttu-id="d440a-141">請確定您的虛擬交換器支援這種案例。</span><span class="sxs-lookup"><span data-stu-id="d440a-141">Make sure your virtual switch supports this scenario.</span></span>|
|<span data-ttu-id="d440a-142">網路</span><span class="sxs-lookup"><span data-stu-id="d440a-142">Virtual</span></span>|<span data-ttu-id="d440a-143">實體</span><span class="sxs-lookup"><span data-stu-id="d440a-143">Physical</span></span>|<span data-ttu-id="d440a-144">需要專用的網路介面卡，否則 Azure ATP 會看到所有進出主機的流量，甚至是由它傳送至 Azure ATP 雲端服務的流量。</span><span class="sxs-lookup"><span data-stu-id="d440a-144">Requires a dedicated network adapter otherwise Azure ATP sees all of the traffic coming in and out of the host, even the traffic it sends to the Azure ATP cloud service.</span></span>|
|<span data-ttu-id="d440a-145">實體</span><span class="sxs-lookup"><span data-stu-id="d440a-145">Physical</span></span>|<span data-ttu-id="d440a-146">網路</span><span class="sxs-lookup"><span data-stu-id="d440a-146">Virtual</span></span>|<span data-ttu-id="d440a-147">請確定您的虛擬交換器支援這種案例 - 且實體交換器上的連接埠鏡像設定是根據此案例︰</span><span class="sxs-lookup"><span data-stu-id="d440a-147">Make sure your virtual switch supports this scenario - and port mirroring configuration on your physical switches based on the scenario:</span></span><br /><br /><span data-ttu-id="d440a-148">如果虛擬主機位於相同的實體交換器上，您必須設定交換器層級的 SPAN。</span><span class="sxs-lookup"><span data-stu-id="d440a-148">If the virtual host is on the same physical switch, you need to configure a switch level span.</span></span><br /><br /><span data-ttu-id="d440a-149">如果虛擬主機位於不同的交換器上，您必須設定 RSPAN 或 ERSPAN&#42;。</span><span class="sxs-lookup"><span data-stu-id="d440a-149">If the virtual host is on a different switch, you need to configure RSPAN or ERSPAN&#42;.</span></span>|
|<span data-ttu-id="d440a-150">實體</span><span class="sxs-lookup"><span data-stu-id="d440a-150">Physical</span></span>|<span data-ttu-id="d440a-151">相同交換器上的實體</span><span class="sxs-lookup"><span data-stu-id="d440a-151">Physical on the same switch</span></span>|<span data-ttu-id="d440a-152">實體交換器必須支援 SPAN/連接埠鏡像。</span><span class="sxs-lookup"><span data-stu-id="d440a-152">Physical switch must support SPAN/Port Mirroring.</span></span>|
|<span data-ttu-id="d440a-153">實體</span><span class="sxs-lookup"><span data-stu-id="d440a-153">Physical</span></span>|<span data-ttu-id="d440a-154">不同交換器上的實體</span><span class="sxs-lookup"><span data-stu-id="d440a-154">Physical on a different switch</span></span>|<span data-ttu-id="d440a-155">實體交換器需要支援 RSPAN 或 ERSPAN &#42;。</span><span class="sxs-lookup"><span data-stu-id="d440a-155">Requires physical switches to support RSPAN or ERSPAN&#42;.</span></span>|

<span data-ttu-id="d440a-156">&#42; 只有在 ATP 分析流量之前先解除除封裝的前提下，才支援 ERSPAN。</span><span class="sxs-lookup"><span data-stu-id="d440a-156">&#42; ERSPAN is only supported when decapsulation is performed before the traffic is analyzed by ATP.</span></span>

|||
|-|-|
<span data-ttu-id="8c3ea-101">C4000</span><span class="sxs-lookup"><span data-stu-id="8c3ea-101">C4000</span></span>|<span data-ttu-id="8c3ea-102">UNKNOWN WARNING    Please choose the Technical Support command on the Visual C++     Help menu, or open the Technical Support help file for more information</span><span class="sxs-lookup"><span data-stu-id="8c3ea-102">UNKNOWN WARNING    Please choose the Technical Support command on the Visual C++     Help menu, or open the Technical Support help file for more information</span></span>
<span data-ttu-id="8c3ea-103">C4272</span><span class="sxs-lookup"><span data-stu-id="8c3ea-103">C4272</span></span>|<span data-ttu-id="8c3ea-104">'*type*': is marked __declspec(dllimport); must specify native calling convention when importing a function.</span><span class="sxs-lookup"><span data-stu-id="8c3ea-104">'*type*': is marked __declspec(dllimport); must specify native calling convention when importing a function.</span></span>
<span data-ttu-id="8c3ea-105">C4333</span><span class="sxs-lookup"><span data-stu-id="8c3ea-105">C4333</span></span>|<span data-ttu-id="8c3ea-106">'*expression*': right shift by too large amount, data loss</span><span class="sxs-lookup"><span data-stu-id="8c3ea-106">'*expression*': right shift by too large amount, data loss</span></span>
<span data-ttu-id="8c3ea-107">C4334</span><span class="sxs-lookup"><span data-stu-id="8c3ea-107">C4334</span></span>|<span data-ttu-id="8c3ea-108">'*expression*': result of 32-bit shift implicitly converted to 64 bits (was 64-bit shift intended?)</span><span class="sxs-lookup"><span data-stu-id="8c3ea-108">'*expression*': result of 32-bit shift implicitly converted to 64 bits (was 64-bit shift intended?)</span></span>
<span data-ttu-id="8c3ea-109">C4335</span><span class="sxs-lookup"><span data-stu-id="8c3ea-109">C4335</span></span>|<span data-ttu-id="8c3ea-110">Mac file format detected: please convert the source file to either DOS or UNIX format</span><span class="sxs-lookup"><span data-stu-id="8c3ea-110">Mac file format detected: please convert the source file to either DOS or UNIX format</span></span>
<span data-ttu-id="8c3ea-111">C4342</span><span class="sxs-lookup"><span data-stu-id="8c3ea-111">C4342</span></span>|<span data-ttu-id="8c3ea-112">behavior change: '*type*' called, but a member operator was called in previous versions</span><span class="sxs-lookup"><span data-stu-id="8c3ea-112">behavior change: '*type*' called, but a member operator was called in previous versions</span></span>
<span data-ttu-id="8c3ea-113">C4350</span><span class="sxs-lookup"><span data-stu-id="8c3ea-113">C4350</span></span>|<span data-ttu-id="8c3ea-114">behavior change: '*declaration*' called instead of '*declaration*'</span><span class="sxs-lookup"><span data-stu-id="8c3ea-114">behavior change: '*declaration*' called instead of '*declaration*'</span></span>
<span data-ttu-id="8c3ea-115">C4688</span><span class="sxs-lookup"><span data-stu-id="8c3ea-115">C4688</span></span>|<span data-ttu-id="8c3ea-116">'*name*': constraint list contains assembly private type '*declaration*'</span><span class="sxs-lookup"><span data-stu-id="8c3ea-116">'*name*': constraint list contains assembly private type '*declaration*'</span></span>
<span data-ttu-id="8c3ea-117">C4690</span><span class="sxs-lookup"><span data-stu-id="8c3ea-117">C4690</span></span>|[ emitidl(pop) ]: more pops than pushes
<span data-ttu-id="8c3ea-119">C4691</span><span class="sxs-lookup"><span data-stu-id="8c3ea-119">C4691</span></span>|<span data-ttu-id="8c3ea-120">'*type*': type referenced was expected in unreferenced *module* '*description*', type defined in current translation unit used instead</span><span class="sxs-lookup"><span data-stu-id="8c3ea-120">'*type*': type referenced was expected in unreferenced *module* '*description*', type defined in current translation unit used instead</span></span>


|||
|-|-|
<span data-ttu-id="0994b-101">C4000</span><span class="sxs-lookup"><span data-stu-id="0994b-101">C4000</span></span>|<span data-ttu-id="0994b-102">UNKNOWN WARNING    Please choose the Technical Support command on the Visual C++     Help menu, or open the Technical Support help file for more information</span><span class="sxs-lookup"><span data-stu-id="0994b-102">UNKNOWN WARNING    Please choose the Technical Support command on the Visual C++     Help menu, or open the Technical Support help file for more information</span></span>
<span data-ttu-id="0994b-103">C4272</span><span class="sxs-lookup"><span data-stu-id="0994b-103">C4272</span></span>|<span data-ttu-id="0994b-104">'*type*': is marked __declspec(dllimport); must specify native calling convention when importing a function.</span><span class="sxs-lookup"><span data-stu-id="0994b-104">'*type*': is marked __declspec(dllimport); must specify native calling convention when importing a function.</span></span>
<span data-ttu-id="0994b-105">C4333</span><span class="sxs-lookup"><span data-stu-id="0994b-105">C4333</span></span>|<span data-ttu-id="0994b-106">'*expression*': right shift by too large amount, data loss</span><span class="sxs-lookup"><span data-stu-id="0994b-106">'*expression*': right shift by too large amount, data loss</span></span>
<span data-ttu-id="0994b-107">C4334</span><span class="sxs-lookup"><span data-stu-id="0994b-107">C4334</span></span>|<span data-ttu-id="0994b-108">'*expression*': result of 32-bit shift implicitly converted to 64 bits (was 64-bit shift intended?)</span><span class="sxs-lookup"><span data-stu-id="0994b-108">'*expression*': result of 32-bit shift implicitly converted to 64 bits (was 64-bit shift intended?)</span></span>
<span data-ttu-id="0994b-109">C4335</span><span class="sxs-lookup"><span data-stu-id="0994b-109">C4335</span></span>|<span data-ttu-id="0994b-110">Mac file format detected: please convert the source file to either DOS or UNIX format</span><span class="sxs-lookup"><span data-stu-id="0994b-110">Mac file format detected: please convert the source file to either DOS or UNIX format</span></span>
<span data-ttu-id="0994b-111">C4342</span><span class="sxs-lookup"><span data-stu-id="0994b-111">C4342</span></span>|<span data-ttu-id="0994b-112">behavior change: '*type*' called, but a member operator was called in previous versions</span><span class="sxs-lookup"><span data-stu-id="0994b-112">behavior change: '*type*' called, but a member operator was called in previous versions</span></span>
<span data-ttu-id="0994b-113">C4350</span><span class="sxs-lookup"><span data-stu-id="0994b-113">C4350</span></span>|<span data-ttu-id="0994b-114">behavior change: '*declaration*' called instead of '*declaration*'</span><span class="sxs-lookup"><span data-stu-id="0994b-114">behavior change: '*declaration*' called instead of '*declaration*'</span></span>
<span data-ttu-id="0994b-115">C4688</span><span class="sxs-lookup"><span data-stu-id="0994b-115">C4688</span></span>|<span data-ttu-id="0994b-116">'*name*': constraint list contains assembly private type '*declaration*'</span><span class="sxs-lookup"><span data-stu-id="0994b-116">'*name*': constraint list contains assembly private type '*declaration*'</span></span>
<span data-ttu-id="0994b-117">C4690</span><span class="sxs-lookup"><span data-stu-id="0994b-117">C4690</span></span>|<span data-ttu-id="0994b-118">\[ emitidl(pop) ]: more pops than pushes</span><span class="sxs-lookup"><span data-stu-id="0994b-118">\[ emitidl(pop) ]: more pops than pushes</span></span>
<span data-ttu-id="0994b-119">C4691</span><span class="sxs-lookup"><span data-stu-id="0994b-119">C4691</span></span>|<span data-ttu-id="0994b-120">'*type*': type referenced was expected in unreferenced *module* '*description*', type defined in current translation unit used instead</span><span class="sxs-lookup"><span data-stu-id="0994b-120">'*type*': type referenced was expected in unreferenced *module* '*description*', type defined in current translation unit used instead</span></span>

<span data-ttu-id="3a550-101">bla bla</span><span class="sxs-lookup"><span data-stu-id="3a550-101">bla bla</span></span>

<span data-ttu-id="3a550-102"><!-- [download-center]: TODO --> [releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span><span class="sxs-lookup"><span data-stu-id="3a550-102"><!-- [download-center]: TODO --> [releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span></span>

<!--Marketplace Links -->
<!----Not available[idera_marketplace]:https://azure.microsoft.com/en-us/marketplace/--> 

[click2cloud_marketplace]:https://marketplace.visualstudio.com/items?itemName=Click2CloudInc.Click2CloudDockerExtensionforVisualStudio 
