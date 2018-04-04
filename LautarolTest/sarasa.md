---
title: Walkthrough - Working with WCF
description: This walkthrough covers how a mobile application built with Xamarin can consume a WCF web service using the BasicHttpBinding class.
ms.prod: xamarin
ms.assetid: D0E83342-2E79-4D25-BD57-43718F5628C4
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
ms.date: 02/17/2018
---

# <a name="walkthrough---working-with-wcf"></a><span data-ttu-id="d3122-103">Walkthrough - Working with WCF</span><span class="sxs-lookup"><span data-stu-id="d3122-103">Walkthrough - Working with WCF</span></span>

<span data-ttu-id="d3122-104">_This walkthrough covers how a mobile application built with Xamarin can consume a WCF web service using the BasicHttpBinding class._</span><span class="sxs-lookup"><span data-stu-id="d3122-104">_This walkthrough covers how a mobile application built with Xamarin can consume a WCF web service using the BasicHttpBinding class._</span></span>


<span data-ttu-id="d3122-105">It is a common requirement for mobile applications to be able to communicate with backend systems.</span><span class="sxs-lookup"><span data-stu-id="d3122-105">It is a common requirement for mobile applications to be able to communicate with backend systems.</span></span> <span data-ttu-id="d3122-106">There are many choices and options for backend frameworks, one of which is [Windows Communication Foundation](http://msdn.microsoft.com/en-us/library/ms731082.aspx) (WCF).</span><span class="sxs-lookup"><span data-stu-id="d3122-106">There are many choices and options for backend frameworks, one of which is [Windows Communication Foundation](http://msdn.microsoft.com/en-us/library/ms731082.aspx) (WCF).</span></span> <span data-ttu-id="d3122-107">This walkthrough will provide an example of how a Xamarin mobile application can consume a WCF service using the `BasicHttpBinding` class.</span><span class="sxs-lookup"><span data-stu-id="d3122-107">This walkthrough will provide an example of how a Xamarin mobile application can consume a WCF service using the `BasicHttpBinding` class.</span></span> <span data-ttu-id="d3122-108">The walkthrough includes the following topics:</span><span class="sxs-lookup"><span data-stu-id="d3122-108">The walkthrough includes the following topics:</span></span>

1.  <span data-ttu-id="d3122-109">**Create a WCF Service** - In this section we will create a very basic WCF service having two methods.</span><span class="sxs-lookup"><span data-stu-id="d3122-109">**Create a WCF Service** - In this section we will create a very basic WCF service having two methods.</span></span> <span data-ttu-id="d3122-110">The first method will take a string parameter, while the other method will take a C# object.</span><span class="sxs-lookup"><span data-stu-id="d3122-110">The first method will take a string parameter, while the other method will take a C# object.</span></span> <span data-ttu-id="d3122-111">This section will also discuss how to configure a developer's workstation to allow remote access to the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-111">This section will also discuss how to configure a developer's workstation to allow remote access to the WCF service.</span></span>
1.  <span data-ttu-id="d3122-112">**Create a Xamarin.Android Application** - Once the WCF service has been created, we will create a simple Xamarin.Android application that will use the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-112">**Create a Xamarin.Android Application** - Once the WCF service has been created, we will create a simple Xamarin.Android application that will use the WCF service.</span></span> <span data-ttu-id="d3122-113">This section will cover how to create a WCF service proxy class to facilitate communication with the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-113">This section will cover how to create a WCF service proxy class to facilitate communication with the WCF service.</span></span>
1.  <span data-ttu-id="d3122-114">**Create a Xamarin.iOS Application** - The final part of this tutorial involves creating a simple Xamarin.iOS application that will use the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-114">**Create a Xamarin.iOS Application** - The final part of this tutorial involves creating a simple Xamarin.iOS application that will use the WCF service.</span></span>

<a name="Requirements" />

## <a name="requirements"></a><span data-ttu-id="d3122-115">Requirements</span><span class="sxs-lookup"><span data-stu-id="d3122-115">Requirements</span></span>

<span data-ttu-id="d3122-116">This walkthrough assumes that you have some familiarity with creating and using WCF services.</span><span class="sxs-lookup"><span data-stu-id="d3122-116">This walkthrough assumes that you have some familiarity with creating and using WCF services.</span></span>

<a name="Creating_a_WCF_Service" />

## <a name="creating-a-wcf-service"></a><span data-ttu-id="d3122-117">Creating a WCF Service</span><span class="sxs-lookup"><span data-stu-id="d3122-117">Creating a WCF Service</span></span>

<span data-ttu-id="d3122-118">The first task before us is to create a WCF service for a mobile applications to communicate with.</span><span class="sxs-lookup"><span data-stu-id="d3122-118">The first task before us is to create a WCF service for a mobile applications to communicate with.</span></span>

1. <span data-ttu-id="d3122-119">Launch Visual Studio 2017, and create a new project.</span><span class="sxs-lookup"><span data-stu-id="d3122-119">Launch Visual Studio 2017, and create a new project.</span></span>
1. <span data-ttu-id="d3122-120">In the **New Project** dialog, select the **WCF > WCF Service Library** template, and name the solution `HelloWorldService`:</span><span class="sxs-lookup"><span data-stu-id="d3122-120">In the **New Project** dialog, select the **WCF > WCF Service Library** template, and name the solution `HelloWorldService`:</span></span>

    <span data-ttu-id="d3122-121">![](walkthrough-working-with-wcf-images/new-wcf-service.png "Create a new WCF service library")</span><span class="sxs-lookup"><span data-stu-id="d3122-121">![](walkthrough-working-with-wcf-images/new-wcf-service.png "Create a new WCF service library")</span></span>

1. <span data-ttu-id="d3122-122">In **Solution Explorer**, add a new class named `HelloWorldData` to the project:</span><span class="sxs-lookup"><span data-stu-id="d3122-122">In **Solution Explorer**, add a new class named `HelloWorldData` to the project:</span></span>

    ```csharp
        using System.Runtime.Serialization;

        namespace HelloWorldService
        {
            [DataContract]
            public class HelloWorldData
            {
                [DataMember]
                public bool SayHello { get; set; }

                [DataMember]
                public string Name { get; set; }

                public HelloWorldData()
                {
                    Name = "Hello ";
                    SayHello = false;
                }
            }
        }
    ```


1. <span data-ttu-id="d3122-123">In **Solution Explorer**, rename `IService1.cs` to `IHelloWorldService.cs`, and rename `Service1.cs` to `HelloWorldService.cs`.</span><span class="sxs-lookup"><span data-stu-id="d3122-123">In **Solution Explorer**, rename `IService1.cs` to `IHelloWorldService.cs`, and rename `Service1.cs` to `HelloWorldService.cs`.</span></span>
1. <span data-ttu-id="d3122-124">In **Solution Explorer**, open `IHelloWorldService.cs` and replace the code with the following code:</span><span class="sxs-lookup"><span data-stu-id="d3122-124">In **Solution Explorer**, open `IHelloWorldService.cs` and replace the code with the following code:</span></span>

    ```csharp
        using System.ServiceModel;

        namespace HelloWorldService
        {
            [ServiceContract]
            public interface IHelloWorldService
            {
                [OperationContract]
                string SayHelloTo(string name);

                [OperationContract]
                HelloWorldData GetHelloData(HelloWorldData helloWorldData);
            }
        }
    ```
  
    <span data-ttu-id="d3122-125">This service provides two methods – one that takes a string for a parameter and another that takes a .NET object.</span><span class="sxs-lookup"><span data-stu-id="d3122-125">This service provides two methods – one that takes a string for a parameter and another that takes a .NET object.</span></span>

1. <span data-ttu-id="d3122-126">In **Solution Explorer**, open `HelloWorldService.cs` and replace the code with the following code:</span><span class="sxs-lookup"><span data-stu-id="d3122-126">In **Solution Explorer**, open `HelloWorldService.cs` and replace the code with the following code:</span></span>

    ```csharp
        using System;

        namespace HelloWorldService
        {
            public class HelloWorldService : IHelloWorldService
            {
                public HelloWorldData GetHelloData(HelloWorldData helloWorldData)
                {
                    if (helloWorldData == null)
                        throw new ArgumentException("helloWorldData");

                    if (helloWorldData.SayHello)
                        helloWorldData.Name = "Hello World to {helloWorldData.Name}";

                    return helloWorldData;
                }

                public string SayHelloTo(string name)
                {
                    return "Hello World to you, {name}";
                }
            }
        }
    ```

1. <span data-ttu-id="d3122-127">In **Solution Explorer**, open `App.config`, update the `name` attribute of the `<service>` node, the `contract` attribute of the `<endpoint>` node, and the `baseAddress` attribute of the `<add>` node:</span><span class="sxs-lookup"><span data-stu-id="d3122-127">In **Solution Explorer**, open `App.config`, update the `name` attribute of the `<service>` node, the `contract` attribute of the `<endpoint>` node, and the `baseAddress` attribute of the `<add>` node:</span></span>

    ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <configuration>
            ...
            <services>
              <service name="HelloWorldService.HelloWorldService">
                <endpoint address="" binding="basicHttpBinding" contract="HelloWorldService.IHelloWorldService">
                  <identity>
                    <dns value="localhost" />
                  </identity>
                </endpoint>
                <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange" />
                <host>
                  <baseAddresses>
                    <add baseAddress="http://localhost:8733/Design_Time_Addresses/HelloWorldService/" />
                  </baseAddresses>
                </host>
              </service>
            </services>
            ...
        </configuration>
    ```

1. <span data-ttu-id="d3122-128">Build and run the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-128">Build and run the WCF service.</span></span> <span data-ttu-id="d3122-129">The service will be hosted by the WCF test client:</span><span class="sxs-lookup"><span data-stu-id="d3122-129">The service will be hosted by the WCF test client:</span></span>

    <span data-ttu-id="d3122-130">![](walkthrough-working-with-wcf-images/hosted-wcf-service.png "WCF service running in test client")</span><span class="sxs-lookup"><span data-stu-id="d3122-130">![](walkthrough-working-with-wcf-images/hosted-wcf-service.png "WCF service running in test client")</span></span>

1. <span data-ttu-id="d3122-131">With the WCF test client running, launch a browser and navigate to the endpoint for the WCF service:</span><span class="sxs-lookup"><span data-stu-id="d3122-131">With the WCF test client running, launch a browser and navigate to the endpoint for the WCF service:</span></span>

    <span data-ttu-id="d3122-132">![](walkthrough-working-with-wcf-images/wcf-service-browser.png "WCF service browser information page")</span><span class="sxs-lookup"><span data-stu-id="d3122-132">![](walkthrough-working-with-wcf-images/wcf-service-browser.png "WCF service browser information page")</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3122-133">The following section is only necessary if you need to accept remote connections on a Windows 10 workstation.</span><span class="sxs-lookup"><span data-stu-id="d3122-133">The following section is only necessary if you need to accept remote connections on a Windows 10 workstation.</span></span> <span data-ttu-id="d3122-134">The section can be ignored if you have an alternate platform on which to deploy the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-134">The section can be ignored if you have an alternate platform on which to deploy the WCF service.</span></span>

<a name="Allow_Remote_Access_to_IIS_Express" />

## <a name="configuring-remote-access-to-iis-express"></a><span data-ttu-id="d3122-135">Configuring Remote Access to IIS Express</span><span class="sxs-lookup"><span data-stu-id="d3122-135">Configuring Remote Access to IIS Express</span></span>

<span data-ttu-id="d3122-136">Hosting a WCF locally is adequate when connections only come from the local machine.</span><span class="sxs-lookup"><span data-stu-id="d3122-136">Hosting a WCF locally is adequate when connections only come from the local machine.</span></span> <span data-ttu-id="d3122-137">However, remote devices (such as an Android device or an iPhone) will not have any access to a local WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-137">However, remote devices (such as an Android device or an iPhone) will not have any access to a local WCF service.</span></span> <span data-ttu-id="d3122-138">Therefore, this section explains how to configure Windows 10 and IIS Express to accept remote connections:</span><span class="sxs-lookup"><span data-stu-id="d3122-138">Therefore, this section explains how to configure Windows 10 and IIS Express to accept remote connections:</span></span>

1.  <span data-ttu-id="d3122-139">**Configure IIS Express to Accept Remote connections** - This step involves editing the config file for IIS Express to accept remote connections on a specific port and then setting up a rule for IIS Express to accept the incoming traffic.</span><span class="sxs-lookup"><span data-stu-id="d3122-139">**Configure IIS Express to Accept Remote connections** - This step involves editing the config file for IIS Express to accept remote connections on a specific port and then setting up a rule for IIS Express to accept the incoming traffic.</span></span>
1.  <span data-ttu-id="d3122-140">**Add an Exception to Windows Firewall** - You must open up a port through Windows Firewall that remote applications can use to communicate with the WCF service.</span><span class="sxs-lookup"><span data-stu-id="d3122-140">**Add an Exception to Windows Firewall** - You must open up a port through Windows Firewall that remote applications can use to communicate with the WCF service.</span></span>

    <span data-ttu-id="d3122-141">You will need to know the IP address of your workstation.</span><span class="sxs-lookup"><span data-stu-id="d3122-141">You will need to know the IP address of your workstation.</span></span> <span data-ttu-id="d3122-142">For the purposes of this example we'll assume that our workstation has the IP address 192.168.1.143.</span><span class="sxs-lookup"><span data-stu-id="d3122-142">For the purposes of this example we'll assume that our workstation has the IP address 192.168.1.143.</span></span>

1. <span data-ttu-id="d3122-143">Let's begin by configuring IIS Express to listen for external requests.</span><span class="sxs-lookup"><span data-stu-id="d3122-143">Let's begin by configuring IIS Express to listen for external requests.</span></span> <span data-ttu-id="d3122-144">We can do this by editing the configuration file for IIS Express at `[solutiondirectory]\.vs\config\applicationhost.config`, as shown in the following screenshot:</span><span class="sxs-lookup"><span data-stu-id="d3122-144">We can do this by editing the configuration file for IIS Express at `[solutiondirectory]\.vs\config\applicationhost.config`, as shown in the following screenshot:</span></span>

    <span data-ttu-id="d3122-145">[![](walkthrough-working-with-wcf-images/image05.png "We can do this by editing the configuration file for IIS Express at solutiondirectory.vsconfigapplicationhost.config, as shown in this screenshot")](walkthrough-working-with-wcf-images/image05.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3122-145">[![](walkthrough-working-with-wcf-images/image05.png "We can do this by editing the configuration file for IIS Express at solutiondirectory.vsconfigapplicationhost.config, as shown in this screenshot")](walkthrough-working-with-wcf-images/image05.png#lightbox)</span></span>

    <span data-ttu-id="d3122-146">Locate the `site` element with the name `HelloWorldWcfHost`.</span><span class="sxs-lookup"><span data-stu-id="d3122-146">Locate the `site` element with the name `HelloWorldWcfHost`.</span></span> <span data-ttu-id="d3122-147">It should look something like the following XML snippet:</span><span class="sxs-lookup"><span data-stu-id="d3122-147">It should look something like the following XML snippet:</span></span>

    ```xml
        <site name="HelloWorldWcfHost" id="2">
            <application path="/" applicationPool="Clr4IntegratedAppPool">
                <virtualDirectory path="/" physicalPath="\\vmware-host\Shared Folders\tom\work\xamarin\code\private-samples\webservices\HelloWorld\HelloWorldWcfHost" />
            </application>
            <bindings>
                <binding protocol="http" bindingInformation="*:8733:localhost" />
            </bindings>
        </site>
    ```
 
    <span data-ttu-id="d3122-148">We will need to add another `binding` to open up port 8734 to outside traffic.</span><span class="sxs-lookup"><span data-stu-id="d3122-148">We will need to add another `binding` to open up port 8734 to outside traffic.</span></span> <span data-ttu-id="d3122-149">Add the following XML to the `bindings` element, replacing the IP address with your own IP address:</span><span class="sxs-lookup"><span data-stu-id="d3122-149">Add the following XML to the `bindings` element, replacing the IP address with your own IP address:</span></span>

    ```xml
    <binding protocol="http" bindingInformation="*:8734:192.168.1.143" />
    ```
    
    <span data-ttu-id="d3122-150">This will configure IIS Express to accept HTTP traffic from any remote IP address on port 8734 on the external IP address of the computer.</span><span class="sxs-lookup"><span data-stu-id="d3122-150">This will configure IIS Express to accept HTTP traffic from any remote IP address on port 8734 on the external IP address of the computer.</span></span> <span data-ttu-id="d3122-151">This above snippet assumes the IP address of the computer running IIS Express is 192.168.1.143.</span><span class="sxs-lookup"><span data-stu-id="d3122-151">This above snippet assumes the IP address of the computer running IIS Express is 192.168.1.143.</span></span> <span data-ttu-id="d3122-152">After the changes, the `bindings` element should look like the following:</span><span class="sxs-lookup"><span data-stu-id="d3122-152">After the changes, the `bindings` element should look like the following:</span></span>

    ```xml
        <site name="HelloWorldWcfHost" id="2">
            <application path="/" applicationPool="Clr4IntegratedAppPool">
                <virtualDirectory path="/" physicalPath="\\vmware-host\Shared Folders\tom\work\xamarin\code\private-samples\webservices\HelloWorld\HelloWorldWcfHost" />
            </application>
            <bindings>
                <binding protocol="http" bindingInformation="*:8733:localhost" />
                <binding protocol="http" bindingInformation="*:8734:192.168.1.143" />
            </bindings>
        </site>
    ```

1. <span data-ttu-id="d3122-153">Next, we need to configure IIS Express accept incoming connections on port 8734.</span><span class="sxs-lookup"><span data-stu-id="d3122-153">Next, we need to configure IIS Express accept incoming connections on port 8734.</span></span> <span data-ttu-id="d3122-154">Startup up an administrative command prompt, and run this command:</span><span class="sxs-lookup"><span data-stu-id="d3122-154">Startup up an administrative command prompt, and run this command:</span></span>

    `> netsh http add urlacl url=http://192.168.1.143:9608/ user=everyone`

1. <span data-ttu-id="d3122-155">The final step is to configure Windows Firewall to permit external traffic on port 8734.</span><span class="sxs-lookup"><span data-stu-id="d3122-155">The final step is to configure Windows Firewall to permit external traffic on port 8734.</span></span> <span data-ttu-id="d3122-156">From an administrative command prompt, run the following command:</span><span class="sxs-lookup"><span data-stu-id="d3122-156">From an administrative command prompt, run the following command:</span></span>

    `> netsh advfirewall firewall add rule name="IISExpressXamarin" dir=in protocol=tcp localport=8734 profile=private remoteip=localsubnet action=allow`

    <span data-ttu-id="d3122-157">This command will allow incoming traffic on port 8734 from all devices on the same subnet as the Windows 10 workstation.</span><span class="sxs-lookup"><span data-stu-id="d3122-157">This command will allow incoming traffic on port 8734 from all devices on the same subnet as the Windows 10 workstation.</span></span>

<span data-ttu-id="d3122-158">You have created a very basic WCF service hosted in IIS Express that will accept incoming connections from other devices or computers on our subnet.</span><span class="sxs-lookup"><span data-stu-id="d3122-158">You have created a very basic WCF service hosted in IIS Express that will accept incoming connections from other devices or computers on our subnet.</span></span> <span data-ttu-id="d3122-159">You can test this out by running your application and visiting `http://localhost:8733/Design_Time_Addresses/HelloWorldService/` on your workstation and `http://192.168.1.143:8734/Design_Time_Addresses/HelloWorldService/` from another computer on your subnet.</span><span class="sxs-lookup"><span data-stu-id="d3122-159">You can test this out by running your application and visiting `http://localhost:8733/Design_Time_Addresses/HelloWorldService/` on your workstation and `http://192.168.1.143:8734/Design_Time_Addresses/HelloWorldService/` from another computer on your subnet.</span></span>

<span data-ttu-id="d3122-160">To allow IIS Express to keep running and serving the service, turn off the **Edit and Continue** option in *Project Properties > Web >Debuggers*.</span><span class="sxs-lookup"><span data-stu-id="d3122-160">To allow IIS Express to keep running and serving the service, turn off the **Edit and Continue** option in *Project Properties > Web >Debuggers*.</span></span>

## <a name="creating-a-proxy-for-the-web-service"></a><span data-ttu-id="d3122-161">Creating a Proxy for the Web Service</span><span class="sxs-lookup"><span data-stu-id="d3122-161">Creating a Proxy for the Web Service</span></span>

<span data-ttu-id="d3122-162">A web service proxy must be created for the WCF service, before an application can consume the service.</span><span class="sxs-lookup"><span data-stu-id="d3122-162">A web service proxy must be created for the WCF service, before an application can consume the service.</span></span> <span data-ttu-id="d3122-163">This can be accomplished as follows:</span><span class="sxs-lookup"><span data-stu-id="d3122-163">This can be accomplished as follows:</span></span>

1. <span data-ttu-id="d3122-164">Add a .NET Standard Class Library named `HelloWorldServiceProxy`, and delete any classes in the project.</span><span class="sxs-lookup"><span data-stu-id="d3122-164">Add a .NET Standard Class Library named `HelloWorldServiceProxy`, and delete any classes in the project.</span></span>
1. <span data-ttu-id="d3122-165">Run the `HelloWorldService` project.</span><span class="sxs-lookup"><span data-stu-id="d3122-165">Run the `HelloWorldService` project.</span></span>
1. <span data-ttu-id="d3122-166">With the `HelloWorldService` project running, add a new **Connected Service** to the project, using the **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="d3122-166">With the `HelloWorldService` project running, add a new **Connected Service** to the project, using the **Microsoft WCF Web Service Reference Provider**.</span></span>
1. <span data-ttu-id="d3122-167">In the **Service Endpoint** tab of the **Configure WCF Web Service Reference** dialog, click the **Discover** button, delete `mex` from the end of the detected endpoint in the **URI** drop-down, enter `HelloWorldServiceProxy` as the **Namespace**, and click the **Next** button.</span><span class="sxs-lookup"><span data-stu-id="d3122-167">In the **Service Endpoint** tab of the **Configure WCF Web Service Reference** dialog, click the **Discover** button, delete `mex` from the end of the detected endpoint in the **URI** drop-down, enter `HelloWorldServiceProxy` as the **Namespace**, and click the **Next** button.</span></span>
1. <span data-ttu-id="d3122-168">In the **Data Type Options** tab of the **Configure WCF Web Service Reference** dialog, accept the defaults by clicking the **Next** button.</span><span class="sxs-lookup"><span data-stu-id="d3122-168">In the **Data Type Options** tab of the **Configure WCF Web Service Reference** dialog, accept the defaults by clicking the **Next** button.</span></span>
1. <span data-ttu-id="d3122-169">In the **Client Options** tab of the **Configure WCF Web Service Reference** dialog, ensure that the **Public** checkbox is selected, and click the **Finish** button.</span><span class="sxs-lookup"><span data-stu-id="d3122-169">In the **Client Options** tab of the **Configure WCF Web Service Reference** dialog, ensure that the **Public** checkbox is selected, and click the **Finish** button.</span></span>
1. <span data-ttu-id="d3122-170">Build the `HelloWorldServiceProxy` project.</span><span class="sxs-lookup"><span data-stu-id="d3122-170">Build the `HelloWorldServiceProxy` project.</span></span>

> [!NOTE]
> <span data-ttu-id="d3122-171">An alternative to creating the proxy using the Microsoft WCF Web Service Reference Provider in Visual Studio 2017 is to use the ServiceModel Metadata Utility Tool (svcutil.exe).</span><span class="sxs-lookup"><span data-stu-id="d3122-171">An alternative to creating the proxy using the Microsoft WCF Web Service Reference Provider in Visual Studio 2017 is to use the ServiceModel Metadata Utility Tool (svcutil.exe).</span></span> <span data-ttu-id="d3122-172">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://docs.microsoft.com/en-us/dotnet/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe).</span><span class="sxs-lookup"><span data-stu-id="d3122-172">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://docs.microsoft.com/en-us/dotnet/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe).</span></span>

<a name="Creating_a_Xamarin_Android_Application" />

## <a name="creating-a-xamarinandroid-application"></a><span data-ttu-id="d3122-173">Creating a Xamarin.Android Application</span><span class="sxs-lookup"><span data-stu-id="d3122-173">Creating a Xamarin.Android Application</span></span>

<span data-ttu-id="d3122-174">The WCF service proxy can be consumed by a Xamarin.Android application, as follows:</span><span class="sxs-lookup"><span data-stu-id="d3122-174">The WCF service proxy can be consumed by a Xamarin.Android application, as follows:</span></span>

1. <span data-ttu-id="d3122-175">In Visual Studio, add a new blank Android project to the solution and name it `HelloWorld.Android`.</span><span class="sxs-lookup"><span data-stu-id="d3122-175">In Visual Studio, add a new blank Android project to the solution and name it `HelloWorld.Android`.</span></span>
1. <span data-ttu-id="d3122-176">In the `HelloWorld.Android` project, add a reference to the `HelloWorldServiceProxy` project, and a reference to the `System.ServiceModel` namespace.</span><span class="sxs-lookup"><span data-stu-id="d3122-176">In the `HelloWorld.Android` project, add a reference to the `HelloWorldServiceProxy` project, and a reference to the `System.ServiceModel` namespace.</span></span>
1. <span data-ttu-id="d3122-177">In **Solution Explorer**, open `Resources/layout/main.axml` and replace the existing XML with the following XML:</span><span class="sxs-lookup"><span data-stu-id="d3122-177">In **Solution Explorer**, open `Resources/layout/main.axml` and replace the existing XML with the following XML:</span></span>

    ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
                  android:orientation="vertical"
                  android:layout_width="fill_parent"
                  android:layout_height="fill_parent">
            <LinearLayout
                    android:orientation="vertical"
                    android:layout_width="fill_parent"
                    android:layout_height="0px"
                    android:layout_weight="1">
                <Button
                        android:id="@+id/sayHelloWorldButton"
                        android:layout_width="fill_parent"
                        android:layout_height="wrap_content"
                        android:text="@string/say_hello_world" />
                <TextView
                        android:text="Large Text"
                        android:textAppearance="?android:attr/textAppearanceLarge"
                        android:layout_width="fill_parent"
                        android:layout_height="wrap_content"
                        android:id="@+id/sayHelloWorldTextView" />
            </LinearLayout>
            <LinearLayout
                    android:orientation="vertical"
                    android:layout_width="fill_parent"
                    android:layout_height="0px"
                    android:layout_weight="1">
                <Button
                        android:id="@+id/getHelloWorldDataButton"
                        android:layout_width="fill_parent"
                        android:layout_height="wrap_content"
                        android:text="@string/get_hello_world_data" />
                <TextView
                        android:text="Large Text"
                        android:textAppearance="?android:attr/textAppearanceLarge"
                        android:layout_width="fill_parent"
                        android:layout_height="wrap_content"
                        android:id="@+id/getHelloWorldDataTextView" />
            </LinearLayout>
        </LinearLayout>
    ```
    
    <span data-ttu-id="d3122-178">The following screenshots shows the UI in the designer:</span><span class="sxs-lookup"><span data-stu-id="d3122-178">The following screenshots shows the UI in the designer:</span></span>

    <span data-ttu-id="d3122-179">[![](walkthrough-working-with-wcf-images/image09.png "This is a screenshot of what this UI looks like in the designer")](walkthrough-working-with-wcf-images/image09.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3122-179">[![](walkthrough-working-with-wcf-images/image09.png "This is a screenshot of what this UI looks like in the designer")](walkthrough-working-with-wcf-images/image09.png#lightbox)</span></span>
    
1. <span data-ttu-id="d3122-180">In **Solution Explorer**, open `Resources/values/Strings.xml` and add the following XML:</span><span class="sxs-lookup"><span data-stu-id="d3122-180">In **Solution Explorer**, open `Resources/values/Strings.xml` and add the following XML:</span></span>

    ```xml
    <string name="say_hello_world">Say Hello World</string>
    <string name="get_hello_world_data">Get Hello World data</string>
    ```
    
1. <span data-ttu-id="d3122-181">In **Solution Explorer**, open `MainActivity.cs` and replace existing code with the following code:</span><span class="sxs-lookup"><span data-stu-id="d3122-181">In **Solution Explorer**, open `MainActivity.cs` and replace existing code with the following code:</span></span>

    ```csharp
        [Activity(Label = "HelloWorld.Android", MainLauncher = true)]
        public class MainActivity : Activity
        {
            static readonly EndpointAddress Endpoint = new EndpointAddress("<insert_WCF_service_endpoint_here>");

            HelloWorldServiceClient _client;
            Button _getHelloWorldDataButton;
            TextView _getHelloWorldDataTextView;
            Button _sayHelloWorldButton;
            TextView _sayHelloWorldTextView;
            ...
        }
    ```

    <span data-ttu-id="d3122-182">Replace `<insert_WCF_service_endpoint_here>` with the address of your WCF endpoint.</span><span class="sxs-lookup"><span data-stu-id="d3122-182">Replace `<insert_WCF_service_endpoint_here>` with the address of your WCF endpoint.</span></span>

1. <span data-ttu-id="d3122-183">In `MainActivity.cs`, modify the `OnCreate` method so that it contains the following code:</span><span class="sxs-lookup"><span data-stu-id="d3122-183">In `MainActivity.cs`, modify the `OnCreate` method so that it contains the following code:</span></span>

    ```csharp
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(bundle);

            SetContentView(Resource.Layout.Main);

            InitializeHelloWorldServiceClient();

            // This button will invoke the GetHelloWorldData - the method that takes a C# object as a parameter.
            _getHelloWorldDataButton = FindViewById<Button>(Resource.Id.getHelloWorldDataButton);
            _getHelloWorldDataButton.Click += GetHelloWorldDataButtonOnClick;
            _getHelloWorldDataTextView = FindViewById<TextView>(Resource.Id.getHelloWorldDataTextView);

            // This button will invoke SayHelloWorld - this method takes a simple string as a parameter.
            _sayHelloWorldButton = FindViewById<Button>(Resource.Id.sayHelloWorldButton);
            _sayHelloWorldButton.Click += SayHelloWorldButtonOnClick;
            _sayHelloWorldTextView = FindViewById<TextView>(Resource.Id.sayHelloWorldTextView);
        }
    ```
    
    <span data-ttu-id="d3122-184">The code above initializes the instance variables for the class and wires up some event handlers.</span><span class="sxs-lookup"><span data-stu-id="d3122-184">The code above initializes the instance variables for the class and wires up some event handlers.</span></span>

1. <span data-ttu-id="d3122-185">In `MainActivity.cs`, instantiate the client proxy class by adding the following two methods:</span><span class="sxs-lookup"><span data-stu-id="d3122-185">In `MainActivity.cs`, instantiate the client proxy class by adding the following two methods:</span></span>

    ```csharp
        void InitializeHelloWorldServiceClient()
        {
            BasicHttpBinding binding = CreateBasicHttpBinding();
            _client = new HelloWorldServiceClient(binding, Endpoint);
        }

        static BasicHttpBinding CreateBasicHttpBinding()
        {
            BasicHttpBinding binding = new BasicHttpBinding
            {
                Name = "basicHttpBinding",
                MaxBufferSize = 2147483647,
                MaxReceivedMessageSize = 2147483647
            };

            TimeSpan timeout = new TimeSpan(0, 0, 30);
            binding.SendTimeout = timeout;
            binding.OpenTimeout = timeout;
            binding.ReceiveTimeout = timeout;
            return binding;
        }
    ```
    
    <span data-ttu-id="d3122-186">The code above instantiates and initializes a `HelloWorldServiceClient` object.</span><span class="sxs-lookup"><span data-stu-id="d3122-186">The code above instantiates and initializes a `HelloWorldServiceClient` object.</span></span>

1. <span data-ttu-id="d3122-187">In `MainActivity.cs`, add even handlers for the two buttons in the `Activity`:</span><span class="sxs-lookup"><span data-stu-id="d3122-187">In `MainActivity.cs`, add even handlers for the two buttons in the `Activity`:</span></span>

    ```csharp
        async void GetHelloWorldDataButtonOnClick(object sender, EventArgs e)
        {
            var data = new HelloWorldData
            {
                Name = "Mr. Chad",
                SayHello = true
            };

            _getHelloWorldDataTextView.Text = "Waiting for WCF...";
            HelloWorldData result;
            try
            {
                result = await _client.GetHelloDataAsync(data);
                _getHelloWorldDataTextView.Text = result.Name;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }

        async void SayHelloWorldButtonOnClick(object sender, EventArgs e)
        {
            _sayHelloWorldTextView.Text = "Waiting for WCF...";
            try
            {
                var result = await _client.SayHelloToAsync("Kilroy");
                _sayHelloWorldTextView.Text = result;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    ```
  
1. <span data-ttu-id="d3122-188">Run the application, ensure that the WCF service is running, and click on the two buttons.</span><span class="sxs-lookup"><span data-stu-id="d3122-188">Run the application, ensure that the WCF service is running, and click on the two buttons.</span></span> <span data-ttu-id="d3122-189">The application will call the WCF asynchronously, provided that the `Endpoint` field is correctly set:</span><span class="sxs-lookup"><span data-stu-id="d3122-189">The application will call the WCF asynchronously, provided that the `Endpoint` field is correctly set:</span></span>

    <span data-ttu-id="d3122-190">[![](walkthrough-working-with-wcf-images/image08.png "Within 30 seconds a response should be received from each WCF method, and our application should look something like this screenshot")](walkthrough-working-with-wcf-images/image08.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3122-190">[![](walkthrough-working-with-wcf-images/image08.png "Within 30 seconds a response should be received from each WCF method, and our application should look something like this screenshot")](walkthrough-working-with-wcf-images/image08.png#lightbox)</span></span>

<a name="Creating_a_Xamarin_iOS_Application" />

## <a name="creating-a-xamarinios-application"></a><span data-ttu-id="d3122-191">Creating a Xamarin.iOS Application</span><span class="sxs-lookup"><span data-stu-id="d3122-191">Creating a Xamarin.iOS Application</span></span>

<span data-ttu-id="d3122-192">The WCF service proxy can be consumed by a Xamarin.iOS application, as follows:</span><span class="sxs-lookup"><span data-stu-id="d3122-192">The WCF service proxy can be consumed by a Xamarin.iOS application, as follows:</span></span>

1. <span data-ttu-id="d3122-193">In Visual Studio, add a new iPhone **Single View Application** project to the solution and name it `HelloWorld.iOS`.</span><span class="sxs-lookup"><span data-stu-id="d3122-193">In Visual Studio, add a new iPhone **Single View Application** project to the solution and name it `HelloWorld.iOS`.</span></span>
1. <span data-ttu-id="d3122-194">In the `HelloWorld.iOS` project, add a reference to the `HelloWorldServiceProxy` project, and a reference to the `System.ServiceModel` namespace.</span><span class="sxs-lookup"><span data-stu-id="d3122-194">In the `HelloWorld.iOS` project, add a reference to the `HelloWorldServiceProxy` project, and a reference to the `System.ServiceModel` namespace.</span></span>
1. <span data-ttu-id="d3122-195">In **Solution Explorer**, double-click on `Main.storyboard` to open the file in the iOS designer.</span><span class="sxs-lookup"><span data-stu-id="d3122-195">In **Solution Explorer**, double-click on `Main.storyboard` to open the file in the iOS designer.</span></span> <span data-ttu-id="d3122-196">Then, add the following `UIButton` and `UITextView` controls:</span><span class="sxs-lookup"><span data-stu-id="d3122-196">Then, add the following `UIButton` and `UITextView` controls:</span></span>

    ||<span data-ttu-id="d3122-197">Name</span><span class="sxs-lookup"><span data-stu-id="d3122-197">Name</span></span>|<span data-ttu-id="d3122-198">Title</span><span class="sxs-lookup"><span data-stu-id="d3122-198">Title</span></span>|
    |--- |--- |--- |
    |`UIButton`|`sayHelloWorldButton`|<span data-ttu-id="d3122-199">Say "Hello, World"</span><span class="sxs-lookup"><span data-stu-id="d3122-199">Say "Hello, World"</span></span>|
    |`UITextView`|`sayHelloWorldText`||
    |`UIButton`|`getHelloWorldDataButton`|<span data-ttu-id="d3122-200">Get "Hello, World" Data</span><span class="sxs-lookup"><span data-stu-id="d3122-200">Get "Hello, World" Data</span></span>|
    |`UITextView`|`getHelloWorldDataText`||

    <span data-ttu-id="d3122-201">After adding the controls, the UI should resemble the following screenshot:</span><span class="sxs-lookup"><span data-stu-id="d3122-201">After adding the controls, the UI should resemble the following screenshot:</span></span>

    <span data-ttu-id="d3122-202">[![](walkthrough-working-with-wcf-images/image12.png "After adding the controls, the UI should resemble this screenshot")](walkthrough-working-with-wcf-images/image12.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3122-202">[![](walkthrough-working-with-wcf-images/image12.png "After adding the controls, the UI should resemble this screenshot")](walkthrough-working-with-wcf-images/image12.png#lightbox)</span></span>

1. <span data-ttu-id="d3122-203">In **Solution Explorer**, open `ViewController.cs` and add the following code:</span><span class="sxs-lookup"><span data-stu-id="d3122-203">In **Solution Explorer**, open `ViewController.cs` and add the following code:</span></span>

    ```xml
        public partial class ViewController : UIViewController
        {
            static readonly EndpointAddress Endpoint = new EndpointAddress("<insert_WCF_service_endpoint_here>");
            HelloWorldServiceClient _client;
            ...
        }
    ```
  
    <span data-ttu-id="d3122-204">Replace `<insert_WCF_service_endpoint_here>` with the address of your WCF endpoint.</span><span class="sxs-lookup"><span data-stu-id="d3122-204">Replace `<insert_WCF_service_endpoint_here>` with the address of your WCF endpoint.</span></span>

1. <span data-ttu-id="d3122-205">In `ViewController.cs`, update the `ViewDidLoad` method so that it resembles the following:</span><span class="sxs-lookup"><span data-stu-id="d3122-205">In `ViewController.cs`, update the `ViewDidLoad` method so that it resembles the following:</span></span>

    ```csharp
        public override void ViewDidLoad()
        {
            base.ViewDidLoad();
            InitializeHelloWorldServiceClient();

            getHelloWorldDataButton.TouchUpInside += GetHelloWorldDataButton_TouchUpInside;
            sayHelloWorldButton.TouchUpInside += SayHelloWorldButton_TouchUpInside;
        }
    ```
  
1. <span data-ttu-id="d3122-206">In `ViewController.cs`, add the `InitializeHelloWorldServiceClient` and `CreateBasicHttpBinding` methods:</span><span class="sxs-lookup"><span data-stu-id="d3122-206">In `ViewController.cs`, add the `InitializeHelloWorldServiceClient` and `CreateBasicHttpBinding` methods:</span></span>

    ```csharp
        void InitializeHelloWorldServiceClient()
        {
            BasicHttpBinding binding = CreateBasicHttpBinding();
            _client = new HelloWorldServiceClient(binding, Endpoint);
        }

        static BasicHttpBinding CreateBasicHttpBinding()
        {
            BasicHttpBinding binding = new BasicHttpBinding
            {
                Name = "basicHttpBinding",
                MaxBufferSize = 2147483647,
                MaxReceivedMessageSize = 2147483647
            };

            TimeSpan timeout = new TimeSpan(0, 0, 30);
            binding.SendTimeout = timeout;
            binding.OpenTimeout = timeout;
            binding.ReceiveTimeout = timeout;
            return binding;
        }
    ```
  
1. <span data-ttu-id="d3122-207">In `ViewController.cs`, add event handlers for the `TouchUpInside` events on the two `UIButton` instances:</span><span class="sxs-lookup"><span data-stu-id="d3122-207">In `ViewController.cs`, add event handlers for the `TouchUpInside` events on the two `UIButton` instances:</span></span>

    ```csharp
        async void GetHelloWorldDataButton_TouchUpInside(object sender, EventArgs e)
        {
            getHelloWorldDataText.Text = "Waiting for WCF...";
            var data = new HelloWorldData
            {
                Name = "Mr. Chad",
                SayHello = true
            };

            HelloWorldData result;
            try
            {
                result = await _client.GetHelloDataAsync(data);
                getHelloWorldDataText.Text = result.Name;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }

        async void SayHelloWorldButton_TouchUpInside(object sender, EventArgs e)
        {
            sayHelloWorldText.Text = "Waiting for WCF...";
            try
            {
                var result = await _client.SayHelloToAsync("Kilroy");
                sayHelloWorldText.Text = result;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    ```

1. <span data-ttu-id="d3122-208">Run the application, ensure that the WCF service is running, and click on the two buttons.</span><span class="sxs-lookup"><span data-stu-id="d3122-208">Run the application, ensure that the WCF service is running, and click on the two buttons.</span></span> <span data-ttu-id="d3122-209">The application will call the WCF asynchronously, provided that the `Endpoint` field is correctly set:</span><span class="sxs-lookup"><span data-stu-id="d3122-209">The application will call the WCF asynchronously, provided that the `Endpoint` field is correctly set:</span></span>

    <span data-ttu-id="d3122-210">[![](walkthrough-working-with-wcf-images/image10.png "Within 30 seconds a response should be received from each WCF method, and our application should look like this screenshot")](walkthrough-working-with-wcf-images/image10.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3122-210">[![](walkthrough-working-with-wcf-images/image10.png "Within 30 seconds a response should be received from each WCF method, and our application should look like this screenshot")](walkthrough-working-with-wcf-images/image10.png#lightbox)</span></span>

<a name="Summary" />

## <a name="summary"></a><span data-ttu-id="d3122-211">Summary</span><span class="sxs-lookup"><span data-stu-id="d3122-211">Summary</span></span>

<span data-ttu-id="d3122-212">This tutorial covered how to work with a WCF service in a mobile application using Xamarin.Android and Xamarin.iOS.</span><span class="sxs-lookup"><span data-stu-id="d3122-212">This tutorial covered how to work with a WCF service in a mobile application using Xamarin.Android and Xamarin.iOS.</span></span> <span data-ttu-id="d3122-213">It showed how to create a WCF service and explained how to configure Windows 10 and IIS Express to accept connections from remote devices.</span><span class="sxs-lookup"><span data-stu-id="d3122-213">It showed how to create a WCF service and explained how to configure Windows 10 and IIS Express to accept connections from remote devices.</span></span> <span data-ttu-id="d3122-214">It then explained how to generate a WCF proxy client and demonstrated how to use the proxy client in both Xamarin.Android and Xamarin.iOS applications.</span><span class="sxs-lookup"><span data-stu-id="d3122-214">It then explained how to generate a WCF proxy client and demonstrated how to use the proxy client in both Xamarin.Android and Xamarin.iOS applications.</span></span>


## <a name="related-links"></a><span data-ttu-id="d3122-215">Related Links</span><span class="sxs-lookup"><span data-stu-id="d3122-215">Related Links</span></span>

- [<span data-ttu-id="d3122-216">HelloWorld (sample)</span><span class="sxs-lookup"><span data-stu-id="d3122-216">HelloWorld (sample)</span></span>](https://developer.xamarin.com/samples/mobile/WCF-Walkthrough/)
- [<span data-ttu-id="d3122-217">Developing Service-Oriented Applications with WCF</span><span class="sxs-lookup"><span data-stu-id="d3122-217">Developing Service-Oriented Applications with WCF</span></span>](https://docs.microsoft.com/en-us/dotnet/framework/wcf/index)
- [<span data-ttu-id="d3122-218">How to: Create a Windows Communication Foundation Client</span><span class="sxs-lookup"><span data-stu-id="d3122-218">How to: Create a Windows Communication Foundation Client</span></span>](https://docs.microsoft.com/en-us/dotnet/framework/wcf/how-to-create-a-wcf-client)
- [<span data-ttu-id="d3122-219">ServiceModel Metadata Utility Tool (svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d3122-219">ServiceModel Metadata Utility Tool (svcutil.exe)</span></span>](https://docs.microsoft.com/en-us/dotnet/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe)
