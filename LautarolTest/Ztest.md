---
title: When and how should I file a bug report?
ms.topic: article
ms.prod: xamarin
ms.assetid: 8AD9CFBF-282A-4C1F-95E9-25F21141B052
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
---

| <span data-ttu-id="7e440-101">Format specifier</span><span class="sxs-lookup"><span data-stu-id="7e440-101">Format specifier</span></span> | <span data-ttu-id="7e440-102">Description</span><span class="sxs-lookup"><span data-stu-id="7e440-102">Description</span></span> | <span data-ttu-id="7e440-103">Examples</span><span class="sxs-lookup"><span data-stu-id="7e440-103">Examples</span></span> |
| ---------------------- | ----------------- | -------------- |
|%|<span data-ttu-id="7e440-104">Defines the following character as a custom format specifier.</span><span class="sxs-lookup"><span data-stu-id="7e440-104">Defines the following character as a custom format specifier.</span></span><br /><br /> <span data-ttu-id="7e440-105">More information:[Using Single Custom Format Specifiers](#UsingSingleSpecifiers).</span><span class="sxs-lookup"><span data-stu-id="7e440-105">More information:[Using Single Custom Format Specifiers](#UsingSingleSpecifiers).</span></span>|<span data-ttu-id="7e440-106">2009-06-15T13:45:30 (%h) -> 1</span><span class="sxs-lookup"><span data-stu-id="7e440-106">2009-06-15T13:45:30 (%h) -> 1</span></span>|
|<span data-ttu-id="7e440-107">\\|The escape character.</span><span class="sxs-lookup"><span data-stu-id="7e440-107">\\|The escape character.</span></span><br /><br /> <span data-ttu-id="7e440-108">More information: [Character literals](#Literals) and [Using the Escape Character](#escape).</span><span class="sxs-lookup"><span data-stu-id="7e440-108">More information: [Character literals](#Literals) and [Using the Escape Character](#escape).</span></span>|<span data-ttu-id="7e440-109">2009-06-15T13:45:30 (h \h) -> 1 h</span><span class="sxs-lookup"><span data-stu-id="7e440-109">2009-06-15T13:45:30 (h \h) -> 1 h</span></span>|
|<span data-ttu-id="7e440-110">Any other character</span><span class="sxs-lookup"><span data-stu-id="7e440-110">Any other character</span></span>|<span data-ttu-id="7e440-111">The character is copied to the result string unchanged.</span><span class="sxs-lookup"><span data-stu-id="7e440-111">The character is copied to the result string unchanged.</span></span><br /><br /> <span data-ttu-id="7e440-112">More information: [Character literals](#Literals).</span><span class="sxs-lookup"><span data-stu-id="7e440-112">More information: [Character literals](#Literals).</span></span>|<span data-ttu-id="7e440-113">2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A</span><span class="sxs-lookup"><span data-stu-id="7e440-113">2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A</span></span>|


1. <span data-ttu-id="1baab-102">File an [issue](https://github.com/dotnet/docs/issues) or add a comment "[!INCLUDE[at](../LautarolTest/includes/at.md)]" to an [issue](https://github.com/dotnet/docs/issues) existing one that you are working on it.</span><span class="sxs-lookup"><span data-stu-id="1baab-102">File an [issue](https://github.com/dotnet/docs/issues) or add a comment "[!INCLUDE[at](../LautarolTest/includes/at.md)]" to an [issue](https://github.com/dotnet/docs/issues) existing one that you are working on it.</span></span>
2. <span data-ttu-id="1baab-103">Write the topic that explains the concepts demonstrated in your sample (example: `docs/standard/linq/where-clause.md`).</span><span class="sxs-lookup"><span data-stu-id="1baab-103">Write the topic that explains the concepts demonstrated in your sample (example: `docs/standard/linq/where-clause.md`).</span></span>


| <span data-ttu-id="1dc58-101">Format specifier</span><span class="sxs-lookup"><span data-stu-id="1dc58-101">Format specifier</span></span> | <span data-ttu-id="1dc58-102">Description</span><span class="sxs-lookup"><span data-stu-id="1dc58-102">Description</span></span> | <span data-ttu-id="1dc58-103">Examples</span><span class="sxs-lookup"><span data-stu-id="1dc58-103">Examples</span></span> |
| ---------------------- | ----------------- | -------------- |
|%|<span data-ttu-id="1dc58-104">Defines the following character as a custom format specifier.</span><span class="sxs-lookup"><span data-stu-id="1dc58-104">Defines the following character as a custom format specifier.</span></span><br /><br /> <span data-ttu-id="1dc58-105">More information:[Using Single Custom Format Specifiers](#UsingSingleSpecifiers).</span><span class="sxs-lookup"><span data-stu-id="1dc58-105">More information:[Using Single Custom Format Specifiers](#UsingSingleSpecifiers).</span></span>|<span data-ttu-id="1dc58-106">2009-06-15T13:45:30 (%h) -> 1</span><span class="sxs-lookup"><span data-stu-id="1dc58-106">2009-06-15T13:45:30 (%h) -> 1</span></span>|
|<span data-ttu-id="1dc58-107">&#92;</span><span class="sxs-lookup"><span data-stu-id="1dc58-107">&#92;</span></span>|<span data-ttu-id="1dc58-108">The escape character.</span><span class="sxs-lookup"><span data-stu-id="1dc58-108">The escape character.</span></span><br /><br /> <span data-ttu-id="1dc58-109">More information: [Character literals](#Literals) and [Using the Escape Character](#escape).</span><span class="sxs-lookup"><span data-stu-id="1dc58-109">More information: [Character literals](#Literals) and [Using the Escape Character](#escape).</span></span>|<span data-ttu-id="1dc58-110">2009-06-15T13:45:30 (h \h) -> 1 h</span><span class="sxs-lookup"><span data-stu-id="1dc58-110">2009-06-15T13:45:30 (h \h) -> 1 h</span></span>|
|<span data-ttu-id="1dc58-111">Any other character</span><span class="sxs-lookup"><span data-stu-id="1dc58-111">Any other character</span></span>|<span data-ttu-id="1dc58-112">The character is copied to the result string unchanged.</span><span class="sxs-lookup"><span data-stu-id="1dc58-112">The character is copied to the result string unchanged.</span></span><br /><br /> <span data-ttu-id="1dc58-113">More information: [Character literals](#Literals).</span><span class="sxs-lookup"><span data-stu-id="1dc58-113">More information: [Character literals](#Literals).</span></span>|<span data-ttu-id="1dc58-114">2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A</span><span class="sxs-lookup"><span data-stu-id="1dc58-114">2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A</span></span>|

1. <span data-ttu-id="1baab-102">File an or add a comment "@" to an  existing one that you are working on it.</span><span class="sxs-lookup"><span data-stu-id="1baab-102">File an  or add a comment "@" to an existing one that you are working on it.</span></span>

    ```csharp
    public class Program
    {
        public void Main(string[] args)
        {
            WhereClause1.QuerySyntaxExample();

            // Add the method syntax as an example.
            WhereClause1.MethodSyntaxExample();
        }
    }
    ```
    
<span data-ttu-id="1baab-107">You build any .NET Core snippet or sample using the .NET Core CLI, which can be installed with [the .NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="1baab-107">You build any .NET Core snippet or sample using the .NET Core CLI, which can be installed with [the .NET Core SDK](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="1baab-108">To build and run your sample:</span><span class="sxs-lookup"><span data-stu-id="1baab-108">To build and run your sample:</span></span>

1. <span data-ttu-id="1baab-109">Go to the sample folder and build to check for errors:</span><span class="sxs-lookup"><span data-stu-id="1baab-109">Go to the sample folder and build to check for errors:</span></span>

    ```console
    dotnet build
    ```
2. <span data-ttu-id="1baab-110">Run your sample:</span><span class="sxs-lookup"><span data-stu-id="1baab-110">Run your sample:</span></span>

    ```console
    dotnet run
    ```

3. <span data-ttu-id="1baab-111">Add a readme.md to the root directory of your sample.</span><span class="sxs-lookup"><span data-stu-id="1baab-111">Add a readme.md to the root directory of your sample.</span></span> 

   <span data-ttu-id="1baab-112">This should include a brief description of the code, and refer people to the article that references the sample.</span><span class="sxs-lookup"><span data-stu-id="1baab-112">This should include a brief description of the code, and refer people to the article that references the sample.</span></span>



>[!NOTE]
><span data-ttu-id="6a529-106">[!INCLUDE[SQL2016](../LautarolTest/includes/ztest2.md)] Service Pack 2 und höher stellt die vollständige Unterstützung für verteilte Transaktionen in Verfügbarkeitsgruppen bereit.</span>

> [!NOTE]
> <span data-ttu-id="6a529-106">[!INCLUDE[SQL2016](../LautarolTest/includes/ztest2.md)] Service Pack 2 und höher stellt die vollständige Unterstützung für verteilte Transaktionen in Verfügbarkeitsgruppen bereit.</span>

## How to integrate Azure ATP with Windows Defender ATP

1. Set the [!INCLUDE[SQL2016]](../LautarolTest/includes/ztest2.md)] workspace you want to integrate as **Primary**. Only one workspace can be the Primary workspace and only a primary workspace can integrate with other services. If, at some point in the future, you should want to make this workspace no longer the primary workspace, you will first have to remove the integration before you can set it as non-primary.

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
