---
title: 'Tutorial: Simulate a failure in accessing read access redundant storage in Azure | Microsoft Docs'
description: Simulate an error in accessing read access geo-redundant storage
services: storage
author: tamram
ms.service: storage
ms.topic: tutorial
ms.date: 01/03/2019
ms.author: tamram
---  

# <a name="tutorial-simulate-a-failure-in-accessing-read-access-redundant-storage"></a><span data-ttu-id="21699-103">Tutorial: Simulate a failure in accessing read-access redundant storage</span><span class="sxs-lookup"><span data-stu-id="21699-103">Tutorial: Simulate a failure in accessing read-access redundant storage</span></span>

<span data-ttu-id="21699-104">This tutorial is part two of a series.</span><span class="sxs-lookup"><span data-stu-id="21699-104">This tutorial is part two of a series.</span></span> <span data-ttu-id="21699-105">In it, you learn about the benefits of a [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) by simulating a failure.</span><span class="sxs-lookup"><span data-stu-id="21699-105">In it, you learn about the benefits of a [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) by simulating a failure.</span></span>

<span data-ttu-id="21699-106">In order to simulate a failure, you can use either [Fiddler](#simulate-a-failure-with-fiddler) or [Static Routing](#simulate-a-failure-with-an-invalid-static-route).</span><span class="sxs-lookup"><span data-stu-id="21699-106">In order to simulate a failure, you can use either [Fiddler](#simulate-a-failure-with-fiddler) or [Static Routing](#simulate-a-failure-with-an-invalid-static-route).</span></span> <span data-ttu-id="21699-107">Either method will allow you to simulate failure for requests to the primary endpoint of your [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) storage account, causing the application read from the secondary endpoint instead.</span><span class="sxs-lookup"><span data-stu-id="21699-107">Either method will allow you to simulate failure for requests to the primary endpoint of your [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) storage account, causing the application read from the secondary endpoint instead.</span></span>

<span data-ttu-id="21699-108">If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/free/) before you begin.</span><span class="sxs-lookup"><span data-stu-id="21699-108">If you don't have an Azure subscription, [create a free account](https://azure.microsoft.com/free/) before you begin.</span></span>

<span data-ttu-id="21699-109">In part two of the series, you learn how to:</span><span class="sxs-lookup"><span data-stu-id="21699-109">In part two of the series, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="21699-110">Run and pause the application</span><span class="sxs-lookup"><span data-stu-id="21699-110">Run and pause the application</span></span>
> * <span data-ttu-id="21699-111">Simulate a failure with [fiddler](#simulate-a-failure-with-fiddler) or [an invalid static route](#simulate-a-failure-with-an-invalid-static-route)</span><span class="sxs-lookup"><span data-stu-id="21699-111">Simulate a failure with [fiddler](#simulate-a-failure-with-fiddler) or [an invalid static route](#simulate-a-failure-with-an-invalid-static-route)</span></span> 
> * <span data-ttu-id="21699-112">Simulate primary endpoint restoration</span><span class="sxs-lookup"><span data-stu-id="21699-112">Simulate primary endpoint restoration</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21699-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="21699-113">Prerequisites</span></span>

<span data-ttu-id="21699-114">Before you begin this tutorial, complete the previous tutorial: [Make your application data highly available with Azure storage][previous-tutorial].</span><span class="sxs-lookup"><span data-stu-id="21699-114">Before you begin this tutorial, complete the previous tutorial: [Make your application data highly available with Azure storage][previous-tutorial].</span></span>

<span data-ttu-id="21699-115">To simulate a failure using Fiddler:</span><span class="sxs-lookup"><span data-stu-id="21699-115">To simulate a failure using Fiddler:</span></span> 

* <span data-ttu-id="21699-116">Download and [install Fiddler](https://www.telerik.com/download/fiddler)</span><span class="sxs-lookup"><span data-stu-id="21699-116">Download and [install Fiddler](https://www.telerik.com/download/fiddler)</span></span>

## <a name="simulate-a-failure-with-fiddler"></a><span data-ttu-id="21699-117">Simulate a failure with Fiddler</span><span class="sxs-lookup"><span data-stu-id="21699-117">Simulate a failure with Fiddler</span></span>

<span data-ttu-id="21699-118">To simulate failure with Fiddler, you inject a failed response for requests to the primary endpoint of your RA-GRS storage account.</span><span class="sxs-lookup"><span data-stu-id="21699-118">To simulate failure with Fiddler, you inject a failed response for requests to the primary endpoint of your RA-GRS storage account.</span></span>

<span data-ttu-id="21699-119">The following sections depict how to simulate a failure and primary endpoint restoration with fiddler.</span><span class="sxs-lookup"><span data-stu-id="21699-119">The following sections depict how to simulate a failure and primary endpoint restoration with fiddler.</span></span>

### <a name="launch-fiddler"></a><span data-ttu-id="21699-120">Launch fiddler</span><span class="sxs-lookup"><span data-stu-id="21699-120">Launch fiddler</span></span>

<span data-ttu-id="21699-121">Open Fiddler, select **Rules** and **Customize Rules**.</span><span class="sxs-lookup"><span data-stu-id="21699-121">Open Fiddler, select **Rules** and **Customize Rules**.</span></span>

![Customize Fiddler rules](media/storage-simulate-failure-ragrs-account-app/figure1.png)

<span data-ttu-id="21699-123">The Fiddler ScriptEditor launches and displays the **SampleRules.js** file.</span><span class="sxs-lookup"><span data-stu-id="21699-123">The Fiddler ScriptEditor launches and displays the **SampleRules.js** file.</span></span> <span data-ttu-id="21699-124">This file is used to customize Fiddler.</span><span class="sxs-lookup"><span data-stu-id="21699-124">This file is used to customize Fiddler.</span></span>

<span data-ttu-id="21699-125">Paste the following code sample in the `OnBeforeResponse` function.</span><span class="sxs-lookup"><span data-stu-id="21699-125">Paste the following code sample in the `OnBeforeResponse` function.</span></span> <span data-ttu-id="21699-126">The new code is commented out to ensure that the logic it creates is not implemented immediately.</span><span class="sxs-lookup"><span data-stu-id="21699-126">The new code is commented out to ensure that the logic it creates is not implemented immediately.</span></span>

<span data-ttu-id="21699-127">Once complete, select **File** and **Save** to save your changes.</span><span class="sxs-lookup"><span data-stu-id="21699-127">Once complete, select **File** and **Save** to save your changes.</span></span>

```javascript
    /*
        // Simulate data center failure
        // After it is successfully downloading the blob, pause the code in the sample,
        // uncomment these lines of script, and save the script.
        // It will intercept the (probably successful) responses and send back a 503 error. 
        // When you're ready to stop sending back errors, comment these lines of script out again 
        //     and save the changes.

        if ((oSession.hostname == "contosoragrs.blob.core.windows.net") 
            && (oSession.PathAndQuery.Contains("HelloWorld"))) {
            oSession.responseCode = 503;  
        }
    */
```

![Paste customized rule](media/storage-simulate-failure-ragrs-account-app/figure2.png)

### <a name="interrupting-the-application"></a><span data-ttu-id="21699-129">Interrupting the application</span><span class="sxs-lookup"><span data-stu-id="21699-129">Interrupting the application</span></span>

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-130">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-130">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-131">Run the application in your IDE or shell.</span><span class="sxs-lookup"><span data-stu-id="21699-131">Run the application in your IDE or shell.</span></span>

<span data-ttu-id="21699-132">Once the application begins reading from the primary endpoint, press **any key** in the console window to pause the application.</span><span class="sxs-lookup"><span data-stu-id="21699-132">Once the application begins reading from the primary endpoint, press **any key** in the console window to pause the application.</span></span>

![Scenario app](media/storage-simulate-failure-ragrs-account-app/scenario.png)

# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-134">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-134">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-135">Run the application in your IDE or shell.</span><span class="sxs-lookup"><span data-stu-id="21699-135">Run the application in your IDE or shell.</span></span>

<span data-ttu-id="21699-136">Since you control the sample, you do not need to interrupt it in order to simulate a failure.</span><span class="sxs-lookup"><span data-stu-id="21699-136">Since you control the sample, you do not need to interrupt it in order to simulate a failure.</span></span> <span data-ttu-id="21699-137">Just make sure that the file has been uploaded to your storage account by running the sample and entering **P**.</span><span class="sxs-lookup"><span data-stu-id="21699-137">Just make sure that the file has been uploaded to your storage account by running the sample and entering **P**.</span></span>

![Scenario app](media/storage-simulate-failure-ragrs-account-app/Java-put-list-output.png)

---

### <a name="simulate-failure"></a><span data-ttu-id="21699-139">Simulate failure</span><span class="sxs-lookup"><span data-stu-id="21699-139">Simulate failure</span></span>

<span data-ttu-id="21699-140">While the application is paused, uncomment the custom rule we saved in Fiddler.</span><span class="sxs-lookup"><span data-stu-id="21699-140">While the application is paused, uncomment the custom rule we saved in Fiddler.</span></span>

<span data-ttu-id="21699-141">The code sample looks for requests to the RA-GRS storage account and, if the path contains the name of the file `HelloWorld`, returns a response code of `503 - Service Unavailable`.</span><span class="sxs-lookup"><span data-stu-id="21699-141">The code sample looks for requests to the RA-GRS storage account and, if the path contains the name of the file `HelloWorld`, returns a response code of `503 - Service Unavailable`.</span></span>

<span data-ttu-id="21699-142">Navigate to Fiddler and select **Rules** -> **Customize Rules...**.</span><span class="sxs-lookup"><span data-stu-id="21699-142">Navigate to Fiddler and select **Rules** -> **Customize Rules...**.</span></span>

<span data-ttu-id="21699-143">Uncomment the following lines, replace `STORAGEACCOUNTNAME` with the name of your storage account.</span><span class="sxs-lookup"><span data-stu-id="21699-143">Uncomment the following lines, replace `STORAGEACCOUNTNAME` with the name of your storage account.</span></span> <span data-ttu-id="21699-144">Select **File** -> **Save** to save your changes.</span><span class="sxs-lookup"><span data-stu-id="21699-144">Select **File** -> **Save** to save your changes.</span></span> 

> [!NOTE]
> <span data-ttu-id="21699-145">If you are running the sample application on Linux, you need to restart Fiddler whenever you edit the **CustomRule.js** file, in order for Fiddler to install the custom logic.</span><span class="sxs-lookup"><span data-stu-id="21699-145">If you are running the sample application on Linux, you need to restart Fiddler whenever you edit the **CustomRule.js** file, in order for Fiddler to install the custom logic.</span></span>

```javascript
         if ((oSession.hostname == "STORAGEACCOUNTNAME.blob.core.windows.net")
         && (oSession.PathAndQuery.Contains("HelloWorld"))) {
         oSession.responseCode = 503;
         }
```

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-146">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-146">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-147">To resume the application, press **any key**.</span><span class="sxs-lookup"><span data-stu-id="21699-147">To resume the application, press **any key**.</span></span>

<span data-ttu-id="21699-148">Once the application starts running again, the requests to the primary endpoint begin to fail.</span><span class="sxs-lookup"><span data-stu-id="21699-148">Once the application starts running again, the requests to the primary endpoint begin to fail.</span></span> <span data-ttu-id="21699-149">The application attempts to reconnect to the primary endpoint 5 times.</span><span class="sxs-lookup"><span data-stu-id="21699-149">The application attempts to reconnect to the primary endpoint 5 times.</span></span> <span data-ttu-id="21699-150">After the failure threshold of five attempts, it requests the image from the secondary read-only endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-150">After the failure threshold of five attempts, it requests the image from the secondary read-only endpoint.</span></span> <span data-ttu-id="21699-151">When the application successfully retrieves the image 20 times from the secondary endpoint it will attempt to connect to the primary endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-151">When the application successfully retrieves the image 20 times from the secondary endpoint it will attempt to connect to the primary endpoint.</span></span> <span data-ttu-id="21699-152">If the primary endpoint is still unreachable, the application resumes reading from the secondary endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-152">If the primary endpoint is still unreachable, the application resumes reading from the secondary endpoint.</span></span>

<span data-ttu-id="21699-153">This pattern is the [Circuit Breaker](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) pattern described in the previous tutorial.</span><span class="sxs-lookup"><span data-stu-id="21699-153">This pattern is the [Circuit Breaker](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) pattern described in the previous tutorial.</span></span>

![Paste customized rule](media/storage-simulate-failure-ragrs-account-app/figure3.png)

# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-155">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-155">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-156">Now that you've introduced the failure, enter **G** to test the failure.</span><span class="sxs-lookup"><span data-stu-id="21699-156">Now that you've introduced the failure, enter **G** to test the failure.</span></span>

<span data-ttu-id="21699-157">It will inform you that it is using the secondary pipeline as opposed to the primary pipeline.</span><span class="sxs-lookup"><span data-stu-id="21699-157">It will inform you that it is using the secondary pipeline as opposed to the primary pipeline.</span></span>

---

### <a name="simulate-primary-endpoint-restoration"></a><span data-ttu-id="21699-158">Simulate primary endpoint restoration</span><span class="sxs-lookup"><span data-stu-id="21699-158">Simulate primary endpoint restoration</span></span>

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-159">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-159">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-160">With the Fiddler custom rule set in the preceding step, requests to the primary endpoint fail.</span><span class="sxs-lookup"><span data-stu-id="21699-160">With the Fiddler custom rule set in the preceding step, requests to the primary endpoint fail.</span></span>

<span data-ttu-id="21699-161">In order to simulate the primary endpoint functioning again, you remove the logic to inject the `503` error.</span><span class="sxs-lookup"><span data-stu-id="21699-161">In order to simulate the primary endpoint functioning again, you remove the logic to inject the `503` error.</span></span>

<span data-ttu-id="21699-162">To pause the application, press **any key**.</span><span class="sxs-lookup"><span data-stu-id="21699-162">To pause the application, press **any key**.</span></span>

<span data-ttu-id="21699-163">Navigate to Fiddler and select **Rules** and **Customize Rules...**.</span><span class="sxs-lookup"><span data-stu-id="21699-163">Navigate to Fiddler and select **Rules** and **Customize Rules...**.</span></span> 

<span data-ttu-id="21699-164">Comment or remove the custom logic in the `OnBeforeResponse` function, leaving the default function.</span><span class="sxs-lookup"><span data-stu-id="21699-164">Comment or remove the custom logic in the `OnBeforeResponse` function, leaving the default function.</span></span>

<span data-ttu-id="21699-165">Select **File** and **Save** to save the changes.</span><span class="sxs-lookup"><span data-stu-id="21699-165">Select **File** and **Save** to save the changes.</span></span>

![Remove customized rule](media/storage-simulate-failure-ragrs-account-app/figure5.png)

<span data-ttu-id="21699-167">When complete, press **any key** to resume the application.</span><span class="sxs-lookup"><span data-stu-id="21699-167">When complete, press **any key** to resume the application.</span></span> <span data-ttu-id="21699-168">The application continues reading from the primary endpoint until it hits 999 reads.</span><span class="sxs-lookup"><span data-stu-id="21699-168">The application continues reading from the primary endpoint until it hits 999 reads.</span></span>

![Resume application](media/storage-simulate-failure-ragrs-account-app/figure4.png)

# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-170">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-170">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-171">With the Fiddler custom rule set in the preceding step, requests to the primary endpoint fail.</span><span class="sxs-lookup"><span data-stu-id="21699-171">With the Fiddler custom rule set in the preceding step, requests to the primary endpoint fail.</span></span>

<span data-ttu-id="21699-172">In order to simulate the primary endpoint functioning again, you remove the logic to inject the `503` error.</span><span class="sxs-lookup"><span data-stu-id="21699-172">In order to simulate the primary endpoint functioning again, you remove the logic to inject the `503` error.</span></span>

<span data-ttu-id="21699-173">Navigate to Fiddler and select **Rules** and **Customize Rules...**.  Comment or remove the custom logic in the `OnBeforeResponse` function, leaving the default function.</span><span class="sxs-lookup"><span data-stu-id="21699-173">Navigate to Fiddler and select **Rules** and **Customize Rules...**.  Comment or remove the custom logic in the `OnBeforeResponse` function, leaving the default function.</span></span>

<span data-ttu-id="21699-174">Select **File** and **Save** to save the changes.</span><span class="sxs-lookup"><span data-stu-id="21699-174">Select **File** and **Save** to save the changes.</span></span>

<span data-ttu-id="21699-175">When complete, enter **G** to test the download.</span><span class="sxs-lookup"><span data-stu-id="21699-175">When complete, enter **G** to test the download.</span></span> <span data-ttu-id="21699-176">The application will report that it is now using the primary pipeline again.</span><span class="sxs-lookup"><span data-stu-id="21699-176">The application will report that it is now using the primary pipeline again.</span></span>

---

## <a name="simulate-a-failure-with-an-invalid-static-route"></a><span data-ttu-id="21699-177">Simulate a failure with an invalid static route</span><span class="sxs-lookup"><span data-stu-id="21699-177">Simulate a failure with an invalid static route</span></span>

<span data-ttu-id="21699-178">You can create an invalid static route for all requests to the primary endpoint of your [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) storage account.</span><span class="sxs-lookup"><span data-stu-id="21699-178">You can create an invalid static route for all requests to the primary endpoint of your [read-access geo-redundant](../common/storage-redundancy-grs.md#read-access-geo-redundant-storage) (RA-GRS) storage account.</span></span> <span data-ttu-id="21699-179">In this tutorial, the local host is used as the gateway for routing requests to the storage account.</span><span class="sxs-lookup"><span data-stu-id="21699-179">In this tutorial, the local host is used as the gateway for routing requests to the storage account.</span></span> <span data-ttu-id="21699-180">Using the local host as the gateway causes all requests to your storage account primary endpoint to loop back inside the host, which subsequently leads to failure.</span><span class="sxs-lookup"><span data-stu-id="21699-180">Using the local host as the gateway causes all requests to your storage account primary endpoint to loop back inside the host, which subsequently leads to failure.</span></span> <span data-ttu-id="21699-181">Follow the following steps to simulate a failure, and primary endpoint restoration with an invalid static route.</span><span class="sxs-lookup"><span data-stu-id="21699-181">Follow the following steps to simulate a failure, and primary endpoint restoration with an invalid static route.</span></span> 

### <a name="start-and-pause-the-application"></a><span data-ttu-id="21699-182">Start and pause the application</span><span class="sxs-lookup"><span data-stu-id="21699-182">Start and pause the application</span></span>

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-183">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-183">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-184">Run the application in your IDE or shell.</span><span class="sxs-lookup"><span data-stu-id="21699-184">Run the application in your IDE or shell.</span></span> <span data-ttu-id="21699-185">Once the application begins reading from the primary endpoint, press **any key** in the console window to pause the application.</span><span class="sxs-lookup"><span data-stu-id="21699-185">Once the application begins reading from the primary endpoint, press **any key** in the console window to pause the application.</span></span>

# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-186">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-186">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-187">Since you control the sample, you do not need to interrupt it in order to test failure.</span><span class="sxs-lookup"><span data-stu-id="21699-187">Since you control the sample, you do not need to interrupt it in order to test failure.</span></span>

<span data-ttu-id="21699-188">Make sure that the file has been uploaded to your storage account by running the sample and entering **P**.</span><span class="sxs-lookup"><span data-stu-id="21699-188">Make sure that the file has been uploaded to your storage account by running the sample and entering **P**.</span></span>

---

### <a name="simulate-failure"></a><span data-ttu-id="21699-189">Simulate failure</span><span class="sxs-lookup"><span data-stu-id="21699-189">Simulate failure</span></span>

<span data-ttu-id="21699-190">With the application paused, start command prompt on Windows as an administrator or run terminal as root on Linux.</span><span class="sxs-lookup"><span data-stu-id="21699-190">With the application paused, start command prompt on Windows as an administrator or run terminal as root on Linux.</span></span>

<span data-ttu-id="21699-191">Get information about the storage account primary endpoint domain by entering the following command on a command prompt or terminal.</span><span class="sxs-lookup"><span data-stu-id="21699-191">Get information about the storage account primary endpoint domain by entering the following command on a command prompt or terminal.</span></span>

```
nslookup STORAGEACCOUNTNAME.blob.core.windows.net
``` 
 <span data-ttu-id="21699-192">Replace `STORAGEACCOUNTNAME` with the name of your storage account.</span><span class="sxs-lookup"><span data-stu-id="21699-192">Replace `STORAGEACCOUNTNAME` with the name of your storage account.</span></span> <span data-ttu-id="21699-193">Copy to the IP address of your storage account to a text editor for later use.</span><span class="sxs-lookup"><span data-stu-id="21699-193">Copy to the IP address of your storage account to a text editor for later use.</span></span>

<span data-ttu-id="21699-194">To get the IP address of your local host, type `ipconfig` on the Windows command prompt, or `ifconfig` on the Linux terminal.</span><span class="sxs-lookup"><span data-stu-id="21699-194">To get the IP address of your local host, type `ipconfig` on the Windows command prompt, or `ifconfig` on the Linux terminal.</span></span> 

<span data-ttu-id="21699-195">To add a static route for a destination host, type the following command on a Windows command prompt or Linux terminal.</span><span class="sxs-lookup"><span data-stu-id="21699-195">To add a static route for a destination host, type the following command on a Windows command prompt or Linux terminal.</span></span> 

#### <a name="linux"></a><span data-ttu-id="21699-196">Linux</span><span class="sxs-lookup"><span data-stu-id="21699-196">Linux</span></span>

`route add <destination_ip> gw <gateway_ip>`

#### <a name="windows"></a><span data-ttu-id="21699-197">Windows</span><span class="sxs-lookup"><span data-stu-id="21699-197">Windows</span></span>

`route add <destination_ip> <gateway_ip>`

<span data-ttu-id="21699-198">Replace  `<destination_ip>` with your storage account IP address, and `<gateway_ip>` with your local host IP address.</span><span class="sxs-lookup"><span data-stu-id="21699-198">Replace  `<destination_ip>` with your storage account IP address, and `<gateway_ip>` with your local host IP address.</span></span>

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-199">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-199">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-200">To resume the application, press **any key**.</span><span class="sxs-lookup"><span data-stu-id="21699-200">To resume the application, press **any key**.</span></span>

<span data-ttu-id="21699-201">Once the application starts running again, the requests to the primary endpoint begin to fail.</span><span class="sxs-lookup"><span data-stu-id="21699-201">Once the application starts running again, the requests to the primary endpoint begin to fail.</span></span> <span data-ttu-id="21699-202">The application attempts to reconnect to the primary endpoint five times.</span><span class="sxs-lookup"><span data-stu-id="21699-202">The application attempts to reconnect to the primary endpoint five times.</span></span> <span data-ttu-id="21699-203">After the failure threshold of five attempts, it requests the image from the secondary read-only endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-203">After the failure threshold of five attempts, it requests the image from the secondary read-only endpoint.</span></span> <span data-ttu-id="21699-204">After the application successfully retrieves the image 20 times from the secondary endpoint, the application attempts to connect to the primary endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-204">After the application successfully retrieves the image 20 times from the secondary endpoint, the application attempts to connect to the primary endpoint.</span></span> <span data-ttu-id="21699-205">If the primary endpoint is still unreachable, the application resumes reading from the secondary endpoint.</span><span class="sxs-lookup"><span data-stu-id="21699-205">If the primary endpoint is still unreachable, the application resumes reading from the secondary endpoint.</span></span> <span data-ttu-id="21699-206">This pattern is the [Circuit Breaker](/azure/architecture/patterns/circuit-breaker) pattern described in the previous tutorial.</span><span class="sxs-lookup"><span data-stu-id="21699-206">This pattern is the [Circuit Breaker](/azure/architecture/patterns/circuit-breaker) pattern described in the previous tutorial.</span></span>

# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-207">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-207">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-208">Now that you've introduced the failure, enter **G** to test the failure.</span><span class="sxs-lookup"><span data-stu-id="21699-208">Now that you've introduced the failure, enter **G** to test the failure.</span></span> <span data-ttu-id="21699-209">It will inform you that it is using the secondary pipeline as opposed to the primary pipeline.</span><span class="sxs-lookup"><span data-stu-id="21699-209">It will inform you that it is using the secondary pipeline as opposed to the primary pipeline.</span></span>

---

### <a name="simulate-primary-endpoint-restoration"></a><span data-ttu-id="21699-210">Simulate primary endpoint restoration</span><span class="sxs-lookup"><span data-stu-id="21699-210">Simulate primary endpoint restoration</span></span>

<span data-ttu-id="21699-211">To simulate the primary endpoint functioning again, delete the static route of the primary endpoint from the routing table.</span><span class="sxs-lookup"><span data-stu-id="21699-211">To simulate the primary endpoint functioning again, delete the static route of the primary endpoint from the routing table.</span></span> <span data-ttu-id="21699-212">This allows all requests to the primary endpoint to be routed through the default gateway.</span><span class="sxs-lookup"><span data-stu-id="21699-212">This allows all requests to the primary endpoint to be routed through the default gateway.</span></span>

<span data-ttu-id="21699-213">To delete the static route of a destination host, the storage account, type the following command on a Windows command prompt or linux terminal.</span><span class="sxs-lookup"><span data-stu-id="21699-213">To delete the static route of a destination host, the storage account, type the following command on a Windows command prompt or linux terminal.</span></span>

#### <a name="linux"></a><span data-ttu-id="21699-214">Linux</span><span class="sxs-lookup"><span data-stu-id="21699-214">Linux</span></span>

`route del <destination_ip> gw <gateway_ip>`

#### <a name="windows"></a><span data-ttu-id="21699-215">Windows</span><span class="sxs-lookup"><span data-stu-id="21699-215">Windows</span></span>

`route delete <destination_ip>`

# <a name="net-python-and-java-v7-tabdotnet-python-java-v7"></a><span data-ttu-id="21699-216">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span><span class="sxs-lookup"><span data-stu-id="21699-216">[.NET, Python, and Java v7] (#tab/dotnet-python-java-v7)</span></span>

<span data-ttu-id="21699-217">Press **any key** to resume the application.</span><span class="sxs-lookup"><span data-stu-id="21699-217">Press **any key** to resume the application.</span></span> <span data-ttu-id="21699-218">The application continues reading from the primary endpoint until it hits 999 reads.</span><span class="sxs-lookup"><span data-stu-id="21699-218">The application continues reading from the primary endpoint until it hits 999 reads.</span></span>

![Resume application](media/storage-simulate-failure-ragrs-account-app/figure4.png)


# <a name="java-v10-tabjava-v10"></a><span data-ttu-id="21699-220">[Java v10] (#tab/Java-v10)</span><span class="sxs-lookup"><span data-stu-id="21699-220">[Java v10] (#tab/Java-v10)</span></span>

<span data-ttu-id="21699-221">Enter **G** to test the download.</span><span class="sxs-lookup"><span data-stu-id="21699-221">Enter **G** to test the download.</span></span> <span data-ttu-id="21699-222">The application will report that it is now using the primary pipeline again.</span><span class="sxs-lookup"><span data-stu-id="21699-222">The application will report that it is now using the primary pipeline again.</span></span>

![Resume application](media/storage-simulate-failure-ragrs-account-app/java-get-pipeline-example-v10.png)

---

## <a name="next-steps"></a><span data-ttu-id="21699-224">Next steps</span><span class="sxs-lookup"><span data-stu-id="21699-224">Next steps</span></span>

<span data-ttu-id="21699-225">In part two of the series, you learned about simulating a failure to test read access geo-redundant storage.</span><span class="sxs-lookup"><span data-stu-id="21699-225">In part two of the series, you learned about simulating a failure to test read access geo-redundant storage.</span></span>

<span data-ttu-id="21699-226">To learn more about how RA-GRS storage works, as well as its associated risks, read the following article:</span><span class="sxs-lookup"><span data-stu-id="21699-226">To learn more about how RA-GRS storage works, as well as its associated risks, read the following article:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21699-227">Designing HA apps with RA-GRS</span><span class="sxs-lookup"><span data-stu-id="21699-227">Designing HA apps with RA-GRS</span></span>](../common/storage-designing-ha-apps-with-ragrs.md)

[previous-tutorial]: storage-create-geo-redundant-storage.md
