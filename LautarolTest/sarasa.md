---
title: How do I downgrade a NuGet package?
ms.topic: article
ms.prod: xamarin
ms.assetid: 2375F833-A630-471E-B8E9-5AD2CB81F264
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
---

# <a name="how-do-i-downgrade-a-nuget-package"></a><span data-ttu-id="f30fa-102">How do I downgrade a NuGet package?</span><span class="sxs-lookup"><span data-stu-id="f30fa-102">How do I downgrade a NuGet package?</span></span>

<span data-ttu-id="f30fa-103">Visual Studio for Mac & Visual Studio both have features for selecting older versions of packages and installing them automatically; similar to how updating packages works.</span><span class="sxs-lookup"><span data-stu-id="f30fa-103">Visual Studio for Mac & Visual Studio both have features for selecting older versions of packages and installing them automatically; similar to how updating packages works.</span></span> <span data-ttu-id="f30fa-104">These steps are described below.</span><span class="sxs-lookup"><span data-stu-id="f30fa-104">These steps are described below.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="f30fa-105">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f30fa-105">Visual Studio</span></span>
1. <span data-ttu-id="f30fa-106">Go to **Tools > NuGet Package Manager > Package Manager Console**</span><span class="sxs-lookup"><span data-stu-id="f30fa-106">Go to **Tools > NuGet Package Manager > Package Manager Console**</span></span>
2. <span data-ttu-id="f30fa-107">Set the project under **Default Project**</span><span class="sxs-lookup"><span data-stu-id="f30fa-107">Set the project under **Default Project**</span></span>
3. <span data-ttu-id="f30fa-108">Use this syntax:</span><span class="sxs-lookup"><span data-stu-id="f30fa-108">Use this syntax:</span></span>

    > <span data-ttu-id="f30fa-109">Install-Package [PackageName] -Version [tab for version menu]</span><span class="sxs-lookup"><span data-stu-id="f30fa-109">Install-Package [PackageName] -Version [tab for version menu]</span></span>

<span data-ttu-id="f30fa-110">You can also copy/paste the exact command from the package's NuGet page.</span><span class="sxs-lookup"><span data-stu-id="f30fa-110">You can also copy/paste the exact command from the package's NuGet page.</span></span> <span data-ttu-id="f30fa-111">Example for Xamarin.Forms: [https://www.nuget.org/packages/Xamarin.Forms/](https://www.nuget.org/packages/Xamarin.Forms/)</span><span class="sxs-lookup"><span data-stu-id="f30fa-111">Example for Xamarin.Forms: [https://www.nuget.org/packages/Xamarin.Forms/](https://www.nuget.org/packages/Xamarin.Forms/)</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="f30fa-112">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f30fa-112">Visual Studio for Mac</span></span>
1. <span data-ttu-id="f30fa-113">In your project, right-click the packages folder & select **Add Packages**</span><span class="sxs-lookup"><span data-stu-id="f30fa-113">In your project, right-click the packages folder & select **Add Packages**</span></span>
2. <span data-ttu-id="f30fa-114">In the searchbar, you can use the following syntax to search for your required packages:</span><span class="sxs-lookup"><span data-stu-id="f30fa-114">In the searchbar, you can use the following syntax to search for your required packages:</span></span>

    `[PackageName] version:*`

### <a name="examples"></a><span data-ttu-id="f30fa-115">Examples</span><span class="sxs-lookup"><span data-stu-id="f30fa-115">Examples</span></span> 
- <span data-ttu-id="f30fa-116">Lists all Xamarin.Forms packages:</span><span class="sxs-lookup"><span data-stu-id="f30fa-116">Lists all Xamarin.Forms packages:</span></span> 

    `Xamarin.Forms version:`
- <span data-ttu-id="f30fa-117">Lists all Xamarin.Forms 1.4.x packages:</span><span class="sxs-lookup"><span data-stu-id="f30fa-117">Lists all Xamarin.Forms 1.4.x packages:</span></span> 

    `Xamarin.Forms version:1.4`

<span data-ttu-id="f30fa-118">*Note: If you add a space between `version:` & the version number, the search will behave as though no version was specified.*</span><span class="sxs-lookup"><span data-stu-id="f30fa-118">*Note: If you add a space between `version:` & the version number, the search will behave as though no version was specified.*</span></span>
