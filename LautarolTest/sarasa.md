---
title: Connection Troubleshooting
description: 'This guide provides troubleshooting steps for issues that may be encountered using the new connection manager, including connectivity and SSH issues.'
ms.topic: article
ms.prod: xamarin
ms.assetid: A1508A15-1997-4562-B537-E4A9F3DD1F06
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/19/2017
---

# <a name="connection-troubleshooting"></a><span data-ttu-id="200dd-103">Connection Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="200dd-103">Connection Troubleshooting</span></span>

<span data-ttu-id="200dd-104">_This guide provides troubleshooting steps for issues that may be encountered using the new connection manager, including connectivity and SSH issues._</span><span class="sxs-lookup"><span data-stu-id="200dd-104">_This guide provides troubleshooting steps for issues that may be encountered using the new connection manager, including connectivity and SSH issues._</span></span>

## <a name="log-file-location"></a><span data-ttu-id="200dd-105">Log File Location</span><span class="sxs-lookup"><span data-stu-id="200dd-105">Log File Location</span></span>

- <span data-ttu-id="200dd-106">**Mac** – ~/Library/Logs/Xamarin-[MAJOR.MINOR]</span><span class="sxs-lookup"><span data-stu-id="200dd-106">**Mac** – ~/Library/Logs/Xamarin-[MAJOR.MINOR]</span></span>
- <span data-ttu-id="200dd-107">**Windows** – %LOCALAPPDATA%\Xamarin\Logs</span><span class="sxs-lookup"><span data-stu-id="200dd-107">**Windows** – %LOCALAPPDATA%\Xamarin\Logs</span></span>

<span data-ttu-id="200dd-108">The log files can be located by browsing to **Help &gt; Xamarin &gt; Zip Logs** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="200dd-108">The log files can be located by browsing to **Help &gt; Xamarin &gt; Zip Logs** in Visual Studio.</span></span>


## <a name="wheres-the-xamarin-build-host-app"></a><span data-ttu-id="200dd-109">Where's the Xamarin Build Host App?</span><span class="sxs-lookup"><span data-stu-id="200dd-109">Where's the Xamarin Build Host App?</span></span>

<span data-ttu-id="200dd-110">The Xamarin Build Host from older versions of Xamarin.iOS is no longer required.</span><span class="sxs-lookup"><span data-stu-id="200dd-110">The Xamarin Build Host from older versions of Xamarin.iOS is no longer required.</span></span> <span data-ttu-id="200dd-111">Visual Studio now automatically deploys the agent over Remote Login and runs it in the background.</span><span class="sxs-lookup"><span data-stu-id="200dd-111">Visual Studio now automatically deploys the agent over Remote Login and runs it in the background.</span></span> <span data-ttu-id="200dd-112">There is no additional app that will run on either the Mac or Windows machines.</span><span class="sxs-lookup"><span data-stu-id="200dd-112">There is no additional app that will run on either the Mac or Windows machines.</span></span>


## <a name="troubleshooting-remote-login"></a><span data-ttu-id="200dd-113">Troubleshooting Remote Login</span><span class="sxs-lookup"><span data-stu-id="200dd-113">Troubleshooting Remote Login</span></span>

> [!IMPORTANT]
> <span data-ttu-id="200dd-114">These troubleshooting steps are primarily intended for problems that happen during the initial setup on a new system.</span><span class="sxs-lookup"><span data-stu-id="200dd-114">These troubleshooting steps are primarily intended for problems that happen during the initial setup on a new system.</span></span>  <span data-ttu-id="200dd-115">If you had previously been using the connection successfully in a particular environment and then the connection suddenly or intermittently stops working, you can (in most cases) skip straight to checking if any of the following helps:</span><span class="sxs-lookup"><span data-stu-id="200dd-115">If you had previously been using the connection successfully in a particular environment and then the connection suddenly or intermittently stops working, you can (in most cases) skip straight to checking if any of the following helps:</span></span> 
>   * <span data-ttu-id="200dd-116">Kill the leftover processes as described below under [Errors due to existing Build Host Processes](#errors).</span><span class="sxs-lookup"><span data-stu-id="200dd-116">Kill the leftover processes as described below under [Errors due to existing Build Host Processes](#errors).</span></span> 
>   * <span data-ttu-id="200dd-117">Clear the agents as described under [Clearing the Broker, IDB, Build, and Designer Agents](#clearing), and then use a wired internet connection and connect directly via the IP address as described under [Couldn't connect to MacBuildHost.local. Please try again.](#tryagain).</span><span class="sxs-lookup"><span data-stu-id="200dd-117">Clear the agents as described under [Clearing the Broker, IDB, Build, and Designer Agents](#clearing), and then use a wired internet connection and connect directly via the IP address as described under [Couldn't connect to MacBuildHost.local. Please try again.](#tryagain).</span></span>  
> <span data-ttu-id="200dd-118">If none of those options fix the issue, then please follow the instructions in [step 9](#stepnine) to file a new bug report.</span><span class="sxs-lookup"><span data-stu-id="200dd-118">If none of those options fix the issue, then please follow the instructions in [step 9](#stepnine) to file a new bug report.</span></span>

1. <span data-ttu-id="200dd-119">Check that you have compatible Xamarin.iOS versions installed on your Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-119">Check that you have compatible Xamarin.iOS versions installed on your Mac.</span></span> <span data-ttu-id="200dd-120">To do this with Visual Studio 2017 ensure that you are on the **Stable** distribution channel in Visual Studio for Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-120">To do this with Visual Studio 2017 ensure that you are on the **Stable** distribution channel in Visual Studio for Mac.</span></span> <span data-ttu-id="200dd-121">In Visual Studio 2015 and earlier make sure that you are on the same distribution channel on both IDEs.</span><span class="sxs-lookup"><span data-stu-id="200dd-121">In Visual Studio 2015 and earlier make sure that you are on the same distribution channel on both IDEs.</span></span>
    * <span data-ttu-id="200dd-122">In Visual Studio for Mac, go to **Visual Studio for Mac > Check for Updates...** to view or change the **Update channel**.</span><span class="sxs-lookup"><span data-stu-id="200dd-122">In Visual Studio for Mac, go to **Visual Studio for Mac > Check for Updates...** to view or change the **Update channel**.</span></span>
    * <span data-ttu-id="200dd-123">In Visual Studio 2015 and earlier, check the distribution channel under **Tools > Options > Xamarin > Other**.</span><span class="sxs-lookup"><span data-stu-id="200dd-123">In Visual Studio 2015 and earlier, check the distribution channel under **Tools > Options > Xamarin > Other**.</span></span>

2. <span data-ttu-id="200dd-124">Make sure that **Remote Login** is enabled on the Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-124">Make sure that **Remote Login** is enabled on the Mac.</span></span> <span data-ttu-id="200dd-125">Set access for **Only these users**, and make sure your Mac user is included in the list or group:</span><span class="sxs-lookup"><span data-stu-id="200dd-125">Set access for **Only these users**, and make sure your Mac user is included in the list or group:</span></span>

    <span data-ttu-id="200dd-126">[![](troubleshooting-images/troubleshooting-image1.png "Set access for Only these users")](troubleshooting-images/troubleshooting-image1.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-126">[![](troubleshooting-images/troubleshooting-image1.png "Set access for Only these users")](troubleshooting-images/troubleshooting-image1.png#lightbox)</span></span>

3. <span data-ttu-id="200dd-127">Check that your firewall allows incoming connections through port 22 - the default for SSH:</span><span class="sxs-lookup"><span data-stu-id="200dd-127">Check that your firewall allows incoming connections through port 22 - the default for SSH:</span></span>

    <span data-ttu-id="200dd-128">[![](troubleshooting-images/troubleshooting-image2.png "Check that the firewall allows incoming connections through port 22")](troubleshooting-images/troubleshooting-image2.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-128">[![](troubleshooting-images/troubleshooting-image2.png "Check that the firewall allows incoming connections through port 22")](troubleshooting-images/troubleshooting-image2.png#lightbox)</span></span>

    <span data-ttu-id="200dd-129">If you have disabled **Automatically allow signed software to receive incoming connections**, OS X will present a dialog during the pairing process asking to allow `mono-sgen` or `mono-sgen32` to receive incoming connections.</span><span class="sxs-lookup"><span data-stu-id="200dd-129">If you have disabled **Automatically allow signed software to receive incoming connections**, OS X will present a dialog during the pairing process asking to allow `mono-sgen` or `mono-sgen32` to receive incoming connections.</span></span> <span data-ttu-id="200dd-130">Be sure to click **Allow** on this dialog:</span><span class="sxs-lookup"><span data-stu-id="200dd-130">Be sure to click **Allow** on this dialog:</span></span>

    <span data-ttu-id="200dd-131">[![](troubleshooting-images/troubleshooting-image4a.png "Click Allow on this dialog")](troubleshooting-images/troubleshooting-image4a.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-131">[![](troubleshooting-images/troubleshooting-image4a.png "Click Allow on this dialog")](troubleshooting-images/troubleshooting-image4a.png#lightbox)</span></span>

4. <span data-ttu-id="200dd-132">Confirm that you are logged in to the user account on that Mac and have an active GUI session.</span><span class="sxs-lookup"><span data-stu-id="200dd-132">Confirm that you are logged in to the user account on that Mac and have an active GUI session.</span></span>

5. <span data-ttu-id="200dd-133">Make sure you are connecting to the Mac with the _username_ rather than the _Full Name_.</span><span class="sxs-lookup"><span data-stu-id="200dd-133">Make sure you are connecting to the Mac with the _username_ rather than the _Full Name_.</span></span> <span data-ttu-id="200dd-134">This avoids a known limitation for full names that include accented characters.</span><span class="sxs-lookup"><span data-stu-id="200dd-134">This avoids a known limitation for full names that include accented characters.</span></span>

    <span data-ttu-id="200dd-135">You can find your _username_ by running the `whoami` command in **Terminal.app**.</span><span class="sxs-lookup"><span data-stu-id="200dd-135">You can find your _username_ by running the `whoami` command in **Terminal.app**.</span></span>

    <span data-ttu-id="200dd-136">For example, from the screenshot below, the account name will be **amyb** and not **Amy Burns**:</span><span class="sxs-lookup"><span data-stu-id="200dd-136">For example, from the screenshot below, the account name will be **amyb** and not **Amy Burns**:</span></span>

    <span data-ttu-id="200dd-137">[![](troubleshooting-images/troubleshooting-image5a.png "Getting the account name from the Terminal app")](troubleshooting-images/troubleshooting-image5a.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-137">[![](troubleshooting-images/troubleshooting-image5a.png "Getting the account name from the Terminal app")](troubleshooting-images/troubleshooting-image5a.png#lightbox)</span></span>


6. <span data-ttu-id="200dd-138">Check that the IP address you are using for the Mac is correct.</span><span class="sxs-lookup"><span data-stu-id="200dd-138">Check that the IP address you are using for the Mac is correct.</span></span> <span data-ttu-id="200dd-139">You can find the IP address under **System Preferences > Sharing > Remote Login** on the Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-139">You can find the IP address under **System Preferences > Sharing > Remote Login** on the Mac.</span></span>

    <span data-ttu-id="200dd-140">[![](troubleshooting-images/troubleshooting-image17.png "The IP address in the System Preferences app")](troubleshooting-images/troubleshooting-image17.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-140">[![](troubleshooting-images/troubleshooting-image17.png "The IP address in the System Preferences app")](troubleshooting-images/troubleshooting-image17.png#lightbox)</span></span>

7. <span data-ttu-id="200dd-141">Once you have confirmed the IP address of the Mac, try a `ping` to that address in `cmd.exe` on Windows:</span><span class="sxs-lookup"><span data-stu-id="200dd-141">Once you have confirmed the IP address of the Mac, try a `ping` to that address in `cmd.exe` on Windows:</span></span>

        ping 10.1.8.95

    <span data-ttu-id="200dd-142">If the ping fails, then the Mac is not _routable_ from the Windows computer.</span><span class="sxs-lookup"><span data-stu-id="200dd-142">If the ping fails, then the Mac is not _routable_ from the Windows computer.</span></span> <span data-ttu-id="200dd-143">That problem will need to be solved at the level of the local area network configuration between the 2 computers.</span><span class="sxs-lookup"><span data-stu-id="200dd-143">That problem will need to be solved at the level of the local area network configuration between the 2 computers.</span></span> <span data-ttu-id="200dd-144">Ensure that both machines are on the same Local Network.</span><span class="sxs-lookup"><span data-stu-id="200dd-144">Ensure that both machines are on the same Local Network.</span></span>

8. <span data-ttu-id="200dd-145">Next, test if the `ssh` client from OpenSSH can connect successfully to the Mac from Windows.</span><span class="sxs-lookup"><span data-stu-id="200dd-145">Next, test if the `ssh` client from OpenSSH can connect successfully to the Mac from Windows.</span></span> <span data-ttu-id="200dd-146">One way to install this program is to install [Git for Windows](https://git-for-windows.github.io/).</span><span class="sxs-lookup"><span data-stu-id="200dd-146">One way to install this program is to install [Git for Windows](https://git-for-windows.github.io/).</span></span> <span data-ttu-id="200dd-147">You can then start a **Git Bash** command prompt and attempt to `ssh` in to the Mac with your username and IP address:</span><span class="sxs-lookup"><span data-stu-id="200dd-147">You can then start a **Git Bash** command prompt and attempt to `ssh` in to the Mac with your username and IP address:</span></span>

    ```
        ssh amyb@10.1.8.95
    ```
<a name="stepnine" />

9. <span data-ttu-id="200dd-148">If **step 8 succeeds**, you can try running a simple command like `ls` over the connection:</span><span class="sxs-lookup"><span data-stu-id="200dd-148">If **step 8 succeeds**, you can try running a simple command like `ls` over the connection:</span></span>

        ssh amyb@10.1.8.95 'ls'

    <span data-ttu-id="200dd-149">This should list the contents of your home directory on the Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-149">This should list the contents of your home directory on the Mac.</span></span> <span data-ttu-id="200dd-150">If the `ls` command works correctly but the Visual Studio connection still fails, you can check the [Known Issues and Limitations](#knownissues) section about complications specific to Xamarin.</span><span class="sxs-lookup"><span data-stu-id="200dd-150">If the `ls` command works correctly but the Visual Studio connection still fails, you can check the [Known Issues and Limitations](#knownissues) section about complications specific to Xamarin.</span></span> <span data-ttu-id="200dd-151">If none of those match your problem, please [file a new bug report](https://bugzilla.xamarin.com/newbug) and attach the logs described under [Check the Verbose Log Files](#verboselogs).</span><span class="sxs-lookup"><span data-stu-id="200dd-151">If none of those match your problem, please [file a new bug report](https://bugzilla.xamarin.com/newbug) and attach the logs described under [Check the Verbose Log Files](#verboselogs).</span></span>

10. <span data-ttu-id="200dd-152">If **step 8 fails**, you can run the following command in Terminal on the Mac to see if the SSH server is accepting _any_ connections:</span><span class="sxs-lookup"><span data-stu-id="200dd-152">If **step 8 fails**, you can run the following command in Terminal on the Mac to see if the SSH server is accepting _any_ connections:</span></span>

        ssh localhost

11. <span data-ttu-id="200dd-153">If step 8 fails but **step 10 succeeds**, then the problem is most likely that port 22 on the Mac build host is not accessible from Windows due to the network configuration.</span><span class="sxs-lookup"><span data-stu-id="200dd-153">If step 8 fails but **step 10 succeeds**, then the problem is most likely that port 22 on the Mac build host is not accessible from Windows due to the network configuration.</span></span> <span data-ttu-id="200dd-154">Possible configuration issues include:</span><span class="sxs-lookup"><span data-stu-id="200dd-154">Possible configuration issues include:</span></span>

    - <span data-ttu-id="200dd-155">The OS X firewall settings are disallowing the connection.</span><span class="sxs-lookup"><span data-stu-id="200dd-155">The OS X firewall settings are disallowing the connection.</span></span> <span data-ttu-id="200dd-156">Be sure to double-check step 3.</span><span class="sxs-lookup"><span data-stu-id="200dd-156">Be sure to double-check step 3.</span></span>

        <span data-ttu-id="200dd-157">Occasionally the per-app configuration for the OS X firewall can also end up in an invalid state where the settings shown in System Preferences do not reflect the actual behavior.</span><span class="sxs-lookup"><span data-stu-id="200dd-157">Occasionally the per-app configuration for the OS X firewall can also end up in an invalid state where the settings shown in System Preferences do not reflect the actual behavior.</span></span> <span data-ttu-id="200dd-158">Deleting the configuration file (**/Library/Preferences/com.apple.alf.plist**) and rebooting the computer can help restore the default behavior.</span><span class="sxs-lookup"><span data-stu-id="200dd-158">Deleting the configuration file (**/Library/Preferences/com.apple.alf.plist**) and rebooting the computer can help restore the default behavior.</span></span> <span data-ttu-id="200dd-159">One way to delete the file is to enter **/Library/Preferences** under **Go &gt; Go to Folder** in Finder, and then move the **com.apple.alf.plist** file to the Trash.</span><span class="sxs-lookup"><span data-stu-id="200dd-159">One way to delete the file is to enter **/Library/Preferences** under **Go &gt; Go to Folder** in Finder, and then move the **com.apple.alf.plist** file to the Trash.</span></span>

    - <span data-ttu-id="200dd-160">The firewall settings of one of the routers between the Mac and the Windows computer is blocking the connection.</span><span class="sxs-lookup"><span data-stu-id="200dd-160">The firewall settings of one of the routers between the Mac and the Windows computer is blocking the connection.</span></span>

    - <span data-ttu-id="200dd-161">Windows itself is disallowing outbound connections to remote port 22.</span><span class="sxs-lookup"><span data-stu-id="200dd-161">Windows itself is disallowing outbound connections to remote port 22.</span></span> <span data-ttu-id="200dd-162">This would be unusual.</span><span class="sxs-lookup"><span data-stu-id="200dd-162">This would be unusual.</span></span> <span data-ttu-id="200dd-163">It is possible to configure the Windows Firewall to disallow outbound connections, but the default setting is to allow all outbound connections.</span><span class="sxs-lookup"><span data-stu-id="200dd-163">It is possible to configure the Windows Firewall to disallow outbound connections, but the default setting is to allow all outbound connections.</span></span>

    - <span data-ttu-id="200dd-164">The Mac build host is disallowing access to port 22 from all external hosts via a `pfctl` rule.</span><span class="sxs-lookup"><span data-stu-id="200dd-164">The Mac build host is disallowing access to port 22 from all external hosts via a `pfctl` rule.</span></span> <span data-ttu-id="200dd-165">This is unlikely unless you know you have configured `pfctl` in the past.</span><span class="sxs-lookup"><span data-stu-id="200dd-165">This is unlikely unless you know you have configured `pfctl` in the past.</span></span>

12. <span data-ttu-id="200dd-166">If step 8 fails and **step 10 fails**, then the problem is likely that the SSH server process on the Mac is not running or is not configured to allow the current user to log in.</span><span class="sxs-lookup"><span data-stu-id="200dd-166">If step 8 fails and **step 10 fails**, then the problem is likely that the SSH server process on the Mac is not running or is not configured to allow the current user to log in.</span></span> <span data-ttu-id="200dd-167">In this case be sure to double-check the Remote Login settings from step 2 before you investigate any more complicated possibilities.</span><span class="sxs-lookup"><span data-stu-id="200dd-167">In this case be sure to double-check the Remote Login settings from step 2 before you investigate any more complicated possibilities.</span></span>

<a name="knownissues" />

## <a name="known-issues-and-limitations"></a><span data-ttu-id="200dd-168">Known Issues and Limitations</span><span class="sxs-lookup"><span data-stu-id="200dd-168">Known Issues and Limitations</span></span>

> [!NOTE]
> <span data-ttu-id="200dd-169">This section only applies if you have already connected successfully to the Mac build host with your Mac username and password using the OpenSSH SSH client, as discussed in steps 8 and 9 above.</span><span class="sxs-lookup"><span data-stu-id="200dd-169">This section only applies if you have already connected successfully to the Mac build host with your Mac username and password using the OpenSSH SSH client, as discussed in steps 8 and 9 above.</span></span>

### <a name="invalid-credentials-please-try-again"></a><span data-ttu-id="200dd-170">"Invalid credentials.</span><span class="sxs-lookup"><span data-stu-id="200dd-170">"Invalid credentials.</span></span> <span data-ttu-id="200dd-171">Please try again."</span><span class="sxs-lookup"><span data-stu-id="200dd-171">Please try again."</span></span>

<span data-ttu-id="200dd-172">Known causes:</span><span class="sxs-lookup"><span data-stu-id="200dd-172">Known causes:</span></span>

- <span data-ttu-id="200dd-173">**Limitation** – This error can appear when attempting to log in to the build host using the account _Full Name_ if the name includes an accented character.</span><span class="sxs-lookup"><span data-stu-id="200dd-173">**Limitation** – This error can appear when attempting to log in to the build host using the account _Full Name_ if the name includes an accented character.</span></span> <span data-ttu-id="200dd-174">This is a limitation of the [SSH.NET library](https://sshnet.codeplex.com/) that Xamarin uses for the SSH connection.</span><span class="sxs-lookup"><span data-stu-id="200dd-174">This is a limitation of the [SSH.NET library](https://sshnet.codeplex.com/) that Xamarin uses for the SSH connection.</span></span> <span data-ttu-id="200dd-175">**Workaround**: See step 5 above.</span><span class="sxs-lookup"><span data-stu-id="200dd-175">**Workaround**: See step 5 above.</span></span>

### <a name="unable-to-authenticate-with-ssh-keys-please-try-to-log-in-with-credentials-first"></a><span data-ttu-id="200dd-176">"Unable to authenticate with SSH keys.</span><span class="sxs-lookup"><span data-stu-id="200dd-176">"Unable to authenticate with SSH keys.</span></span> <span data-ttu-id="200dd-177">Please try to log in with credentials first"</span><span class="sxs-lookup"><span data-stu-id="200dd-177">Please try to log in with credentials first"</span></span>

<span data-ttu-id="200dd-178">Known cause:</span><span class="sxs-lookup"><span data-stu-id="200dd-178">Known cause:</span></span>

- <span data-ttu-id="200dd-179">**SSH security restriction** – This message most often means that one of the files or directories in the fully qualified path of **$HOME/.ssh/authorized\_keys** on the Mac has write permissions enabled for _other_ or _group_ members.</span><span class="sxs-lookup"><span data-stu-id="200dd-179">**SSH security restriction** – This message most often means that one of the files or directories in the fully qualified path of **$HOME/.ssh/authorized\_keys** on the Mac has write permissions enabled for _other_ or _group_ members.</span></span> <span data-ttu-id="200dd-180">**Common fix**: Run `chmod og-w "$HOME"` in a Terminal command prompt on the Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-180">**Common fix**: Run `chmod og-w "$HOME"` in a Terminal command prompt on the Mac.</span></span> <span data-ttu-id="200dd-181">For details about which particular file or directory is causing the problem, run `grep sshd /var/log/system.log > "$HOME/Desktop/sshd.log"` in Terminal, and then open the **sshd.log** file from your Desktop and look for "Authentication refused: bad ownership or modes".</span><span class="sxs-lookup"><span data-stu-id="200dd-181">For details about which particular file or directory is causing the problem, run `grep sshd /var/log/system.log > "$HOME/Desktop/sshd.log"` in Terminal, and then open the **sshd.log** file from your Desktop and look for "Authentication refused: bad ownership or modes".</span></span>

### <a name="trying-to-connect-never-completes"></a><span data-ttu-id="200dd-182">"Trying to connect..." never completes</span><span class="sxs-lookup"><span data-stu-id="200dd-182">"Trying to connect..." never completes</span></span>

- <span data-ttu-id="200dd-183">**Bug [#52264](https://bugzilla.xamarin.com/show_bug.cgi?id=52264)** – This problem can happen on Xamarin 4.1 if the **Login shell** in the **Advanced Options** context menu for the Mac user in **System Preferences &gt; Users &amp; Groups** is set to a value other than **/bin/bash**.</span><span class="sxs-lookup"><span data-stu-id="200dd-183">**Bug [#52264](https://bugzilla.xamarin.com/show_bug.cgi?id=52264)** – This problem can happen on Xamarin 4.1 if the **Login shell** in the **Advanced Options** context menu for the Mac user in **System Preferences &gt; Users &amp; Groups** is set to a value other than **/bin/bash**.</span></span> <span data-ttu-id="200dd-184">(Starting with Xamarin 4.2, this scenario instead leads to the "Couldn't connect" error message.) **Workaround**: Change the **Login shell** back to the original default of **/bin/bash**.</span><span class="sxs-lookup"><span data-stu-id="200dd-184">(Starting with Xamarin 4.2, this scenario instead leads to the "Couldn't connect" error message.) **Workaround**: Change the **Login shell** back to the original default of **/bin/bash**.</span></span>

<a name="tryagain" />

### <a name="couldnt-connect-to-macbuildhostlocal-please-try-again"></a><span data-ttu-id="200dd-185">"Couldn't connect to MacBuildHost.local.</span><span class="sxs-lookup"><span data-stu-id="200dd-185">"Couldn't connect to MacBuildHost.local.</span></span> <span data-ttu-id="200dd-186">Please try again."</span><span class="sxs-lookup"><span data-stu-id="200dd-186">Please try again."</span></span>

<span data-ttu-id="200dd-187">Reported causes:</span><span class="sxs-lookup"><span data-stu-id="200dd-187">Reported causes:</span></span>

- <span data-ttu-id="200dd-188">**Bug** – A few users have seen this error message along with a more detailed error in the log files "An unexpected error occurred while configuring SSH for the user ... Session operation has timed out" when attempting to log in to the build host using an Active Directory or other directory service domain user account.</span><span class="sxs-lookup"><span data-stu-id="200dd-188">**Bug** – A few users have seen this error message along with a more detailed error in the log files "An unexpected error occurred while configuring SSH for the user ... Session operation has timed out" when attempting to log in to the build host using an Active Directory or other directory service domain user account.</span></span> <span data-ttu-id="200dd-189">**Workaround:** Log in to the build host using a local user account instead.</span><span class="sxs-lookup"><span data-stu-id="200dd-189">**Workaround:** Log in to the build host using a local user account instead.</span></span>

- <span data-ttu-id="200dd-190">**Bug** – Some users have seen this error when attempting to connect to the build host by double-clicking the name of the Mac in the connection dialog.</span><span class="sxs-lookup"><span data-stu-id="200dd-190">**Bug** – Some users have seen this error when attempting to connect to the build host by double-clicking the name of the Mac in the connection dialog.</span></span> <span data-ttu-id="200dd-191">**Possible workaround**: [Manually add the Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md#manual-add) using the IP address.</span><span class="sxs-lookup"><span data-stu-id="200dd-191">**Possible workaround**: [Manually add the Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md#manual-add) using the IP address.</span></span>

- <span data-ttu-id="200dd-192">**Bug [#35971](https://bugzilla.xamarin.com/show_bug.cgi?id=35971)** – Some users have run across this error when using a wireless network connection between the Mac build host and Windows.</span><span class="sxs-lookup"><span data-stu-id="200dd-192">**Bug [#35971](https://bugzilla.xamarin.com/show_bug.cgi?id=35971)** – Some users have run across this error when using a wireless network connection between the Mac build host and Windows.</span></span> <span data-ttu-id="200dd-193">**Possible workaround**: Move both computers to a wired network connection.</span><span class="sxs-lookup"><span data-stu-id="200dd-193">**Possible workaround**: Move both computers to a wired network connection.</span></span>

- <span data-ttu-id="200dd-194">**Bug [#36642](https://bugzilla.xamarin.com/show_bug.cgi?id=36642)** – On Xamarin 4.0, this message will appear anytime the **$HOME/.bashrc** file on the Mac contains an error.</span><span class="sxs-lookup"><span data-stu-id="200dd-194">**Bug [#36642](https://bugzilla.xamarin.com/show_bug.cgi?id=36642)** – On Xamarin 4.0, this message will appear anytime the **$HOME/.bashrc** file on the Mac contains an error.</span></span> <span data-ttu-id="200dd-195">(Starting with Xamarin 4.1, errors in the **.bashrc** file will no longer affect the connection process.) **Workaround**: Move the **.bashrc** file to a backup location (or delete it if you know you don't need it).</span><span class="sxs-lookup"><span data-stu-id="200dd-195">(Starting with Xamarin 4.1, errors in the **.bashrc** file will no longer affect the connection process.) **Workaround**: Move the **.bashrc** file to a backup location (or delete it if you know you don't need it).</span></span>

- <span data-ttu-id="200dd-196">**Bug [#52264](https://bugzilla.xamarin.com/show_bug.cgi?id=52264)** – This error can appear if the **Login shell** in the **Advanced Options** context menu for the Mac user in **System Preferences > Users & Groups** is set to a value other than **/bin/bash**.</span><span class="sxs-lookup"><span data-stu-id="200dd-196">**Bug [#52264](https://bugzilla.xamarin.com/show_bug.cgi?id=52264)** – This error can appear if the **Login shell** in the **Advanced Options** context menu for the Mac user in **System Preferences > Users & Groups** is set to a value other than **/bin/bash**.</span></span> <span data-ttu-id="200dd-197">**Workaround**: Change the **Login shell** back to the original default of **/bin/bash**.</span><span class="sxs-lookup"><span data-stu-id="200dd-197">**Workaround**: Change the **Login shell** back to the original default of **/bin/bash**.</span></span>

- <span data-ttu-id="200dd-198">**Limitation** – This error can appear if the Mac build host is connected to a router that has no access to the internet (or if the Mac is using a DNS server that times out when asked for the reverse-DNS lookup of the Windows computer).</span><span class="sxs-lookup"><span data-stu-id="200dd-198">**Limitation** – This error can appear if the Mac build host is connected to a router that has no access to the internet (or if the Mac is using a DNS server that times out when asked for the reverse-DNS lookup of the Windows computer).</span></span> <span data-ttu-id="200dd-199">Visual Studio will take roughly 30 seconds to retrieve the SSH fingerprint and eventually fail to connect.</span><span class="sxs-lookup"><span data-stu-id="200dd-199">Visual Studio will take roughly 30 seconds to retrieve the SSH fingerprint and eventually fail to connect.</span></span>

    <span data-ttu-id="200dd-200">**Possible workaround**: Add "UseDNS no" to the **sshd\_config** file.</span><span class="sxs-lookup"><span data-stu-id="200dd-200">**Possible workaround**: Add "UseDNS no" to the **sshd\_config** file.</span></span> <span data-ttu-id="200dd-201">Be sure to read about this SSH setting before changing it.</span><span class="sxs-lookup"><span data-stu-id="200dd-201">Be sure to read about this SSH setting before changing it.</span></span> <span data-ttu-id="200dd-202">See for example [unix.stackexchange.com/questions/56941/what-is-the-point-of-sshd-usedns-option](http://unix.stackexchange.com/questions/56941/what-is-the-point-of-sshd-usedns-option).</span><span class="sxs-lookup"><span data-stu-id="200dd-202">See for example [unix.stackexchange.com/questions/56941/what-is-the-point-of-sshd-usedns-option](http://unix.stackexchange.com/questions/56941/what-is-the-point-of-sshd-usedns-option).</span></span>

    <span data-ttu-id="200dd-203">The following steps describe one way to change the setting.</span><span class="sxs-lookup"><span data-stu-id="200dd-203">The following steps describe one way to change the setting.</span></span> <span data-ttu-id="200dd-204">You will need to be logged in to an administrator account on the Mac to complete the steps.</span><span class="sxs-lookup"><span data-stu-id="200dd-204">You will need to be logged in to an administrator account on the Mac to complete the steps.</span></span>

    1. <span data-ttu-id="200dd-205">Confirm the location of the **sshd\_config** file by running `ls /etc/ssh/sshd_config` and `ls /etc/sshd_config` in a Terminal command prompt.</span><span class="sxs-lookup"><span data-stu-id="200dd-205">Confirm the location of the **sshd\_config** file by running `ls /etc/ssh/sshd_config` and `ls /etc/sshd_config` in a Terminal command prompt.</span></span> <span data-ttu-id="200dd-206">For all of the remaining steps, be sure to use the location that does _not_ return "No such file or directory".</span><span class="sxs-lookup"><span data-stu-id="200dd-206">For all of the remaining steps, be sure to use the location that does _not_ return "No such file or directory".</span></span>

        <span data-ttu-id="200dd-207">[![](troubleshooting-images/troubleshooting-image18.png "Running `ls /etc/ssh/sshd_config` and `ls /etc/sshd_config` in the Terminal")](troubleshooting-images/troubleshooting-image18.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-207">[![](troubleshooting-images/troubleshooting-image18.png "Running `ls /etc/ssh/sshd_config` and `ls /etc/sshd_config` in the Terminal")](troubleshooting-images/troubleshooting-image18.png#lightbox)</span></span>

    3. <span data-ttu-id="200dd-208">Run `cp /etc/ssh/sshd_config "$HOME/Desktop/"` in Terminal to copy the file to your desktop.</span><span class="sxs-lookup"><span data-stu-id="200dd-208">Run `cp /etc/ssh/sshd_config "$HOME/Desktop/"` in Terminal to copy the file to your desktop.</span></span>

    4. <span data-ttu-id="200dd-209">Open the file from your Desktop in a text editor.</span><span class="sxs-lookup"><span data-stu-id="200dd-209">Open the file from your Desktop in a text editor.</span></span> <span data-ttu-id="200dd-210">For example you can run `open -a TextEdit "$HOME/Desktop/sshd_config"` in Terminal.</span><span class="sxs-lookup"><span data-stu-id="200dd-210">For example you can run `open -a TextEdit "$HOME/Desktop/sshd_config"` in Terminal.</span></span>

    5. <span data-ttu-id="200dd-211">Add the following line at the bottom of the file:</span><span class="sxs-lookup"><span data-stu-id="200dd-211">Add the following line at the bottom of the file:</span></span>

            UseDNS no

    6. <span data-ttu-id="200dd-212">Remove any lines that say `UseDNS yes` to make sure the new setting takes effect.</span><span class="sxs-lookup"><span data-stu-id="200dd-212">Remove any lines that say `UseDNS yes` to make sure the new setting takes effect.</span></span>

    7. <span data-ttu-id="200dd-213">Save the file.</span><span class="sxs-lookup"><span data-stu-id="200dd-213">Save the file.</span></span>

    8. <span data-ttu-id="200dd-214">Run `sudo cp "$HOME/Desktop/sshd_config" /etc/ssh/sshd_config` in Terminal to copy the edited file back into place.</span><span class="sxs-lookup"><span data-stu-id="200dd-214">Run `sudo cp "$HOME/Desktop/sshd_config" /etc/ssh/sshd_config` in Terminal to copy the edited file back into place.</span></span> <span data-ttu-id="200dd-215">Enter your password if prompted.</span><span class="sxs-lookup"><span data-stu-id="200dd-215">Enter your password if prompted.</span></span>

    9. <span data-ttu-id="200dd-216">Disable and re-enable **Remote Login** under **System Preferences &gt; Sharing &gt; Remote Login** to restart the SSH server.</span><span class="sxs-lookup"><span data-stu-id="200dd-216">Disable and re-enable **Remote Login** under **System Preferences &gt; Sharing &gt; Remote Login** to restart the SSH server.</span></span>

<a name="clearing" />

### <a name="clearing-the-broker-idb-build-and-designer-agents-on-the-mac"></a><span data-ttu-id="200dd-217">Clearing the Broker, IDB, Build, and Designer Agents on the Mac</span><span class="sxs-lookup"><span data-stu-id="200dd-217">Clearing the Broker, IDB, Build, and Designer Agents on the Mac</span></span>

<span data-ttu-id="200dd-218">If your log files show a problem during the "Installing", "Uploading", or "Starting" steps for any of Mac agents, you can try deleting the **XMA** cache folder to force Visual Studio to re-upload them.</span><span class="sxs-lookup"><span data-stu-id="200dd-218">If your log files show a problem during the "Installing", "Uploading", or "Starting" steps for any of Mac agents, you can try deleting the **XMA** cache folder to force Visual Studio to re-upload them.</span></span>

1. <span data-ttu-id="200dd-219">Run the following command in Terminal on the Mac:</span><span class="sxs-lookup"><span data-stu-id="200dd-219">Run the following command in Terminal on the Mac:</span></span>

        open "$HOME/Library/Caches/Xamarin"

2. <span data-ttu-id="200dd-220">Control-click the **XMA** folder and select **Move to Trash**:</span><span class="sxs-lookup"><span data-stu-id="200dd-220">Control-click the **XMA** folder and select **Move to Trash**:</span></span>

    <span data-ttu-id="200dd-221">[![](troubleshooting-images/troubleshooting-image8.png "Move the XMA folder to Trash")](troubleshooting-images/troubleshooting-image8.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-221">[![](troubleshooting-images/troubleshooting-image8.png "Move the XMA folder to Trash")](troubleshooting-images/troubleshooting-image8.png#lightbox)</span></span>

3. <span data-ttu-id="200dd-222">There is a cache on Windows as well that it may help to clear.</span><span class="sxs-lookup"><span data-stu-id="200dd-222">There is a cache on Windows as well that it may help to clear.</span></span> <span data-ttu-id="200dd-223">Open a cmd prompt as Administrator on Windows:</span><span class="sxs-lookup"><span data-stu-id="200dd-223">Open a cmd prompt as Administrator on Windows:</span></span>

        del %localappdata%\Temp\Xamarin\XMA

## <a name="warning-messages"></a><span data-ttu-id="200dd-224">Warning Messages</span><span class="sxs-lookup"><span data-stu-id="200dd-224">Warning Messages</span></span>

<span data-ttu-id="200dd-225">This section discusses a few messages that can appear in the Output windows and logs that you can usually ignore.</span><span class="sxs-lookup"><span data-stu-id="200dd-225">This section discusses a few messages that can appear in the Output windows and logs that you can usually ignore.</span></span>

### <a name="there-is-a-mismatch-between-the-installed-xamarinios--and-the-local-xamarinios"></a><span data-ttu-id="200dd-226">"There is a mismatch between the installed Xamarin.iOS ... and the local Xamarin.iOS"</span><span class="sxs-lookup"><span data-stu-id="200dd-226">"There is a mismatch between the installed Xamarin.iOS ... and the local Xamarin.iOS"</span></span>

<span data-ttu-id="200dd-227">As long as you have confirmed that both Mac and Windows are updated to the same Xamarin distribution channel, this warning is ignorable.</span><span class="sxs-lookup"><span data-stu-id="200dd-227">As long as you have confirmed that both Mac and Windows are updated to the same Xamarin distribution channel, this warning is ignorable.</span></span>

### <a name="failed-to-execute-ls-usrbinmono-exitstatus1"></a><span data-ttu-id="200dd-228">"Failed to execute 'ls /usr/bin/mono': ExitStatus=1"</span><span class="sxs-lookup"><span data-stu-id="200dd-228">"Failed to execute 'ls /usr/bin/mono': ExitStatus=1"</span></span>

<span data-ttu-id="200dd-229">This message is ignorable as long as the Mac is running OS X 10.11 (El Capitan) or newer.</span><span class="sxs-lookup"><span data-stu-id="200dd-229">This message is ignorable as long as the Mac is running OS X 10.11 (El Capitan) or newer.</span></span> <span data-ttu-id="200dd-230">This message is not a problem on OS X 10.11 because Xamarin also checks **/usr/local/bin/mono**, which is the correct expected location for `mono` on OS X 10.11.</span><span class="sxs-lookup"><span data-stu-id="200dd-230">This message is not a problem on OS X 10.11 because Xamarin also checks **/usr/local/bin/mono**, which is the correct expected location for `mono` on OS X 10.11.</span></span>

### <a name="bonjour-service-macbuildhost-did-not-respond-with-its-ip-address"></a><span data-ttu-id="200dd-231">"Bonjour service 'MacBuildHost' did not respond with its IP address."</span><span class="sxs-lookup"><span data-stu-id="200dd-231">"Bonjour service 'MacBuildHost' did not respond with its IP address."</span></span>

<span data-ttu-id="200dd-232">This message is ignorable unless you notice that the connection dialog does not display the IP address of Mac build host.</span><span class="sxs-lookup"><span data-stu-id="200dd-232">This message is ignorable unless you notice that the connection dialog does not display the IP address of Mac build host.</span></span> <span data-ttu-id="200dd-233">If the IP address _is_ missing in that dialog, you can still [manually add the Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md#manual-add).</span><span class="sxs-lookup"><span data-stu-id="200dd-233">If the IP address _is_ missing in that dialog, you can still [manually add the Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md#manual-add).</span></span>

### <a name="invalid-user-a-from-101895-and-inputuserauthrequest-invalid-user-a-preauth"></a><span data-ttu-id="200dd-234">"Invalid user a from 10.1.8.95" and "input\_userauth\_request: invalid user a [preauth]"</span><span class="sxs-lookup"><span data-stu-id="200dd-234">"Invalid user a from 10.1.8.95" and "input\_userauth\_request: invalid user a [preauth]"</span></span>

<span data-ttu-id="200dd-235">You might notice this messages if you look in the **sshd.log**.</span><span class="sxs-lookup"><span data-stu-id="200dd-235">You might notice this messages if you look in the **sshd.log**.</span></span> <span data-ttu-id="200dd-236">These messages are part of the normal connection process.</span><span class="sxs-lookup"><span data-stu-id="200dd-236">These messages are part of the normal connection process.</span></span> <span data-ttu-id="200dd-237">They appear because Xamarin uses the username **a** temporarily when retrieving the _SSH Fingerprint_.</span><span class="sxs-lookup"><span data-stu-id="200dd-237">They appear because Xamarin uses the username **a** temporarily when retrieving the _SSH Fingerprint_.</span></span>

## <a name="output-window-and-log-files"></a><span data-ttu-id="200dd-238">Output Window and Log Files</span><span class="sxs-lookup"><span data-stu-id="200dd-238">Output Window and Log Files</span></span>

<span data-ttu-id="200dd-239">If Visual Studio hits an error when connecting to the build host, there are 2 locations to check for additional messages: the Output window and the log files.</span><span class="sxs-lookup"><span data-stu-id="200dd-239">If Visual Studio hits an error when connecting to the build host, there are 2 locations to check for additional messages: the Output window and the log files.</span></span>

### <a name="output-window"></a><span data-ttu-id="200dd-240">Output Window</span><span class="sxs-lookup"><span data-stu-id="200dd-240">Output Window</span></span>

<span data-ttu-id="200dd-241">The Output window is the best place to start.</span><span class="sxs-lookup"><span data-stu-id="200dd-241">The Output window is the best place to start.</span></span> <span data-ttu-id="200dd-242">It displays messages about the main connection steps and errors.</span><span class="sxs-lookup"><span data-stu-id="200dd-242">It displays messages about the main connection steps and errors.</span></span> <span data-ttu-id="200dd-243">To view the Xamarin messages in the Output window:</span><span class="sxs-lookup"><span data-stu-id="200dd-243">To view the Xamarin messages in the Output window:</span></span>

1. <span data-ttu-id="200dd-244">Select **View > Output** from the menus or click the **Output** tab.</span><span class="sxs-lookup"><span data-stu-id="200dd-244">Select **View > Output** from the menus or click the **Output** tab.</span></span>
2. <span data-ttu-id="200dd-245">Click the **Show output from** drop-down menu.</span><span class="sxs-lookup"><span data-stu-id="200dd-245">Click the **Show output from** drop-down menu.</span></span>
3. <span data-ttu-id="200dd-246">Select **Xamarin**.</span><span class="sxs-lookup"><span data-stu-id="200dd-246">Select **Xamarin**.</span></span>

<span data-ttu-id="200dd-247">[![](troubleshooting-images/troubleshooting-image11.png "Select Xamarin in the Output tab")](troubleshooting-images/troubleshooting-image11.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-247">[![](troubleshooting-images/troubleshooting-image11.png "Select Xamarin in the Output tab")](troubleshooting-images/troubleshooting-image11.png#lightbox)</span></span>

### <a name="log-files"></a><span data-ttu-id="200dd-248">Log Files</span><span class="sxs-lookup"><span data-stu-id="200dd-248">Log Files</span></span>

<span data-ttu-id="200dd-249">If the Output window does not include enough information to diagnose the problem, the log files are the next place to look.</span><span class="sxs-lookup"><span data-stu-id="200dd-249">If the Output window does not include enough information to diagnose the problem, the log files are the next place to look.</span></span> <span data-ttu-id="200dd-250">The log files contain additional diagnostic messages that do not appear in the Output window.</span><span class="sxs-lookup"><span data-stu-id="200dd-250">The log files contain additional diagnostic messages that do not appear in the Output window.</span></span> <span data-ttu-id="200dd-251">To view the log files:</span><span class="sxs-lookup"><span data-stu-id="200dd-251">To view the log files:</span></span>

1. <span data-ttu-id="200dd-252">Start Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="200dd-252">Start Visual Studio.</span></span>

    > [!IMPORTANT]
>  <span data-ttu-id="200dd-253">Note that **.svclogs** are not enabled by default.</span><span class="sxs-lookup"><span data-stu-id="200dd-253">Note that **.svclogs** are not enabled by default.</span></span> <span data-ttu-id="200dd-254">To access them you will need to start Visual Studio with verbose logs as explained in the [Version Logs](~/cross-platform/troubleshooting/questions/version-logs.md#visual-studio-startup-verbose-logs) guide.</span><span class="sxs-lookup"><span data-stu-id="200dd-254">To access them you will need to start Visual Studio with verbose logs as explained in the [Version Logs](~/cross-platform/troubleshooting/questions/version-logs.md#visual-studio-startup-verbose-logs) guide.</span></span> <span data-ttu-id="200dd-255">For more information, refer to the [Troubleshooting Extensions with the Activity Log](https://blogs.msdn.microsoft.com/visualstudio/2010/02/24/troubleshooting-extensions-with-the-activity-log/) blog.</span><span class="sxs-lookup"><span data-stu-id="200dd-255">For more information, refer to the [Troubleshooting Extensions with the Activity Log](https://blogs.msdn.microsoft.com/visualstudio/2010/02/24/troubleshooting-extensions-with-the-activity-log/) blog.</span></span>

2. <span data-ttu-id="200dd-256">Attempt to connect to the build host.</span><span class="sxs-lookup"><span data-stu-id="200dd-256">Attempt to connect to the build host.</span></span>

3. <span data-ttu-id="200dd-257">After Visual Studio hits the connection error, collect the logs from **Help > Xamarin > Zip Logs**:</span><span class="sxs-lookup"><span data-stu-id="200dd-257">After Visual Studio hits the connection error, collect the logs from **Help > Xamarin > Zip Logs**:</span></span>

    <span data-ttu-id="200dd-258">[![](troubleshooting-images/troubleshooting-image12.png "Collect the logs from Help > Xamarin > Zip Logs")](troubleshooting-images/troubleshooting-image12.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-258">[![](troubleshooting-images/troubleshooting-image12.png "Collect the logs from Help > Xamarin > Zip Logs")](troubleshooting-images/troubleshooting-image12.png#lightbox)</span></span>

4. <span data-ttu-id="200dd-259">When you open the .zip file, you will see a list of files similar to the example below.</span><span class="sxs-lookup"><span data-stu-id="200dd-259">When you open the .zip file, you will see a list of files similar to the example below.</span></span> <span data-ttu-id="200dd-260">For connection errors, the most important files are the **\*Ide.log** and **\*Ide.svclog** files.</span><span class="sxs-lookup"><span data-stu-id="200dd-260">For connection errors, the most important files are the **\*Ide.log** and **\*Ide.svclog** files.</span></span> <span data-ttu-id="200dd-261">These files contain the same messages in two slightly different formats.</span><span class="sxs-lookup"><span data-stu-id="200dd-261">These files contain the same messages in two slightly different formats.</span></span> <span data-ttu-id="200dd-262">The **.svclog** is XML and is useful if you want to browse through the messages.</span><span class="sxs-lookup"><span data-stu-id="200dd-262">The **.svclog** is XML and is useful if you want to browse through the messages.</span></span> <span data-ttu-id="200dd-263">The **.log** is plain text and is useful if you want to filter the messages using command line tools.</span><span class="sxs-lookup"><span data-stu-id="200dd-263">The **.log** is plain text and is useful if you want to filter the messages using command line tools.</span></span>

    <span data-ttu-id="200dd-264">To browse through all the messages, select and open the **.svclog** file:</span><span class="sxs-lookup"><span data-stu-id="200dd-264">To browse through all the messages, select and open the **.svclog** file:</span></span>

    <span data-ttu-id="200dd-265">[![](troubleshooting-images/troubleshooting-image13.png "Select the svclog file")](troubleshooting-images/troubleshooting-image13.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-265">[![](troubleshooting-images/troubleshooting-image13.png "Select the svclog file")](troubleshooting-images/troubleshooting-image13.png#lightbox)</span></span>

5. <span data-ttu-id="200dd-266">The **.svclog** file will open in **Microsoft Service Trace Viewer**.</span><span class="sxs-lookup"><span data-stu-id="200dd-266">The **.svclog** file will open in **Microsoft Service Trace Viewer**.</span></span> <span data-ttu-id="200dd-267">You can browse the messages by thread to see related groups of messages.</span><span class="sxs-lookup"><span data-stu-id="200dd-267">You can browse the messages by thread to see related groups of messages.</span></span> <span data-ttu-id="200dd-268">To browse by thread, first select the **Graph** tab, then click the **Layout Mode** drop-down menu and select **Thread**:</span><span class="sxs-lookup"><span data-stu-id="200dd-268">To browse by thread, first select the **Graph** tab, then click the **Layout Mode** drop-down menu and select **Thread**:</span></span>

    <span data-ttu-id="200dd-269">[![](troubleshooting-images/troubleshooting-image14.png "Click the Layout Mode drop-down menu and select Thread")](troubleshooting-images/troubleshooting-image14.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-269">[![](troubleshooting-images/troubleshooting-image14.png "Click the Layout Mode drop-down menu and select Thread")](troubleshooting-images/troubleshooting-image14.png#lightbox)</span></span>

<a name="verboselogs" />

### <a name="verbose-log-files"></a><span data-ttu-id="200dd-270">Verbose Log Files</span><span class="sxs-lookup"><span data-stu-id="200dd-270">Verbose Log Files</span></span>

<span data-ttu-id="200dd-271">If the normal log files still do not provide sufficient information to diagnose the problem, one last technique to try is to enable verbose logging.</span><span class="sxs-lookup"><span data-stu-id="200dd-271">If the normal log files still do not provide sufficient information to diagnose the problem, one last technique to try is to enable verbose logging.</span></span> <span data-ttu-id="200dd-272">The verbose logs are also preferred on bug reports.</span><span class="sxs-lookup"><span data-stu-id="200dd-272">The verbose logs are also preferred on bug reports.</span></span>

1. <span data-ttu-id="200dd-273">Quit Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="200dd-273">Quit Visual Studio.</span></span>

2. <span data-ttu-id="200dd-274">Start a [**Developer Command Prompt**](https://msdn.microsoft.com/en-us/library/ms229859(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="200dd-274">Start a [**Developer Command Prompt**](https://msdn.microsoft.com/en-us/library/ms229859(v=vs.110).aspx).</span></span>

3. <span data-ttu-id="200dd-275">Run the following command in the command prompt to launch Visual Studio with verbose logging:</span><span class="sxs-lookup"><span data-stu-id="200dd-275">Run the following command in the command prompt to launch Visual Studio with verbose logging:</span></span>

    ```bash
    devenv /log
    ```

4. <span data-ttu-id="200dd-276">Attempt to connect to the build host from Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="200dd-276">Attempt to connect to the build host from Visual Studio.</span></span>

5. <span data-ttu-id="200dd-277">After Visual Studio hits the connection error, collect the logs from **Help > Xamarin > Zip Logs**.</span><span class="sxs-lookup"><span data-stu-id="200dd-277">After Visual Studio hits the connection error, collect the logs from **Help > Xamarin > Zip Logs**.</span></span>

6. <span data-ttu-id="200dd-278">Run the following command in Terminal on the Mac to copy any recent log messages from the SSH server into a file on your Desktop:</span><span class="sxs-lookup"><span data-stu-id="200dd-278">Run the following command in Terminal on the Mac to copy any recent log messages from the SSH server into a file on your Desktop:</span></span>

    ```bash
    grep sshd /var/log/system.log > "$HOME/Desktop/sshd.log"
    ```

<span data-ttu-id="200dd-279">If these verbose log files do not provide enough clues to resolve the issue directly, please [file a new bug report](https://bugzilla.xamarin.com/newbug) and attach both the .zip file from step 5 and the .log file from step 6.</span><span class="sxs-lookup"><span data-stu-id="200dd-279">If these verbose log files do not provide enough clues to resolve the issue directly, please [file a new bug report](https://bugzilla.xamarin.com/newbug) and attach both the .zip file from step 5 and the .log file from step 6.</span></span>

## <a name="troubleshooting-build-and-deployment-errors"></a><span data-ttu-id="200dd-280">Troubleshooting Build and Deployment Errors</span><span class="sxs-lookup"><span data-stu-id="200dd-280">Troubleshooting Build and Deployment Errors</span></span>

<span data-ttu-id="200dd-281">This section covers a few problems that can happen after Visual Studio connects successfully to the build host.</span><span class="sxs-lookup"><span data-stu-id="200dd-281">This section covers a few problems that can happen after Visual Studio connects successfully to the build host.</span></span>

### <a name="unable-to-connect-to-address1921681222-with-usermacuser"></a><span data-ttu-id="200dd-282">"Unable to connect to Address='192.168.1.2:22' with User='macuser'"</span><span class="sxs-lookup"><span data-stu-id="200dd-282">"Unable to connect to Address='192.168.1.2:22' with User='macuser'"</span></span>

<span data-ttu-id="200dd-283">Known causes:</span><span class="sxs-lookup"><span data-stu-id="200dd-283">Known causes:</span></span>

- <span data-ttu-id="200dd-284">**Xamarin 4.1 security feature** – This error _will_ happen if you downgrade to Xamarin 4.0 after using Xamarin 4.1 or higher.</span><span class="sxs-lookup"><span data-stu-id="200dd-284">**Xamarin 4.1 security feature** – This error _will_ happen if you downgrade to Xamarin 4.0 after using Xamarin 4.1 or higher.</span></span> <span data-ttu-id="200dd-285">In this case the error will be accompanied by the additional warning "Private key is encrypted but passphrase is empty".</span><span class="sxs-lookup"><span data-stu-id="200dd-285">In this case the error will be accompanied by the additional warning "Private key is encrypted but passphrase is empty".</span></span> <span data-ttu-id="200dd-286">This is an _intentional_ change due to a new security feature in Xamarin 4.1.</span><span class="sxs-lookup"><span data-stu-id="200dd-286">This is an _intentional_ change due to a new security feature in Xamarin 4.1.</span></span> <span data-ttu-id="200dd-287">**Recommended fix**: Delete **id\_rsa** and **id\_rsa.pub** from **%LOCALAPPDATA%\Xamarin\MonoTouch**, and then reconnect to the Mac build host.</span><span class="sxs-lookup"><span data-stu-id="200dd-287">**Recommended fix**: Delete **id\_rsa** and **id\_rsa.pub** from **%LOCALAPPDATA%\Xamarin\MonoTouch**, and then reconnect to the Mac build host.</span></span>

- <span data-ttu-id="200dd-288">**SSH security restriction** – When this message is accompanied by the additional warning "Could not authenticate the user using the existing ssh keys", it most often means one of the files or directories in the fully qualified path of **$HOME/.ssh/authorized\_keys** on the Mac has write permissions enabled for _other_ or _group_ members.</span><span class="sxs-lookup"><span data-stu-id="200dd-288">**SSH security restriction** – When this message is accompanied by the additional warning "Could not authenticate the user using the existing ssh keys", it most often means one of the files or directories in the fully qualified path of **$HOME/.ssh/authorized\_keys** on the Mac has write permissions enabled for _other_ or _group_ members.</span></span> <span data-ttu-id="200dd-289">**Common fix**: Run `chmod og-w "$HOME"` in a Terminal command prompt on the Mac.</span><span class="sxs-lookup"><span data-stu-id="200dd-289">**Common fix**: Run `chmod og-w "$HOME"` in a Terminal command prompt on the Mac.</span></span> <span data-ttu-id="200dd-290">For details about which particular file or directory is causing the problem, run `grep sshd /var/log/system.log > "$HOME/Desktop/sshd.log"` in Terminal, and then open the **sshd.log** file from your Desktop and look for "Authentication refused: bad ownership or modes".</span><span class="sxs-lookup"><span data-stu-id="200dd-290">For details about which particular file or directory is causing the problem, run `grep sshd /var/log/system.log > "$HOME/Desktop/sshd.log"` in Terminal, and then open the **sshd.log** file from your Desktop and look for "Authentication refused: bad ownership or modes".</span></span>

### <a name="solutions-cannot-be-loaded-from-a-network-share"></a><span data-ttu-id="200dd-291">Solutions cannot be loaded from a Network Share</span><span class="sxs-lookup"><span data-stu-id="200dd-291">Solutions cannot be loaded from a Network Share</span></span>

<span data-ttu-id="200dd-292">Solutions will only be compiled if they are on the local Windows file system or a mapped drive.</span><span class="sxs-lookup"><span data-stu-id="200dd-292">Solutions will only be compiled if they are on the local Windows file system or a mapped drive.</span></span>

<span data-ttu-id="200dd-293">Solutions that are saved in a network share might throw errors, or completely refuse to compile.</span><span class="sxs-lookup"><span data-stu-id="200dd-293">Solutions that are saved in a network share might throw errors, or completely refuse to compile.</span></span> <span data-ttu-id="200dd-294">Any **.sln** files used in Visual Studio should be saved on the local Windows file system.</span><span class="sxs-lookup"><span data-stu-id="200dd-294">Any **.sln** files used in Visual Studio should be saved on the local Windows file system.</span></span>

<span data-ttu-id="200dd-295">The following error is thrown because of this problem:</span><span class="sxs-lookup"><span data-stu-id="200dd-295">The following error is thrown because of this problem:</span></span>

```bash
error : Building from a network share path is not supported at the moment. Please map a network drive to '\\SharedSources\HelloWorld\HelloWorld' or copy the source to a local directory.
```

<span data-ttu-id="200dd-296">related bug: [#36195](https://bugzilla.xamarin.com/show_bug.cgi?id=36195)</span><span class="sxs-lookup"><span data-stu-id="200dd-296">related bug: [#36195](https://bugzilla.xamarin.com/show_bug.cgi?id=36195)</span></span>

### <a name="missing-provisioning-profiles-or-failed-to-create-the-a-fat-library-error"></a><span data-ttu-id="200dd-297">Missing Provisioning Profiles or "Failed to create the a fat library" Error</span><span class="sxs-lookup"><span data-stu-id="200dd-297">Missing Provisioning Profiles or "Failed to create the a fat library" Error</span></span>

<span data-ttu-id="200dd-298">Launch Xcode on the Mac and ensure that your Apple developer account is logged in and your iOS Development Profile is downloaded:</span><span class="sxs-lookup"><span data-stu-id="200dd-298">Launch Xcode on the Mac and ensure that your Apple developer account is logged in and your iOS Development Profile is downloaded:</span></span>

<span data-ttu-id="200dd-299">[![](troubleshooting-images/troubleshooting-image7.png "Ensuring that the Apple developer account is logged in and the iOS Development Profile is downloaded")](troubleshooting-images/troubleshooting-image7.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-299">[![](troubleshooting-images/troubleshooting-image7.png "Ensuring that the Apple developer account is logged in and the iOS Development Profile is downloaded")](troubleshooting-images/troubleshooting-image7.png#lightbox)</span></span>

### <a name="a-socket-operation-was-attempted-to-an-unreachable-network"></a><span data-ttu-id="200dd-300">"A socket operation was attempted to an unreachable network"</span><span class="sxs-lookup"><span data-stu-id="200dd-300">"A socket operation was attempted to an unreachable network"</span></span>

<span data-ttu-id="200dd-301">Reported causes:</span><span class="sxs-lookup"><span data-stu-id="200dd-301">Reported causes:</span></span>

- <span data-ttu-id="200dd-302">**Enhancement [#36118](https://bugzilla.xamarin.com/show_bug.cgi?id=36118)** – This error can prevent successful builds when Visual Studio is using an IPv6 address to connect to the build host.</span><span class="sxs-lookup"><span data-stu-id="200dd-302">**Enhancement [#36118](https://bugzilla.xamarin.com/show_bug.cgi?id=36118)** – This error can prevent successful builds when Visual Studio is using an IPv6 address to connect to the build host.</span></span> <span data-ttu-id="200dd-303">(The build host connection does not yet support IPv6 addresses.)</span><span class="sxs-lookup"><span data-stu-id="200dd-303">(The build host connection does not yet support IPv6 addresses.)</span></span>

### <a name="xamarinios-visual-studio-plugin-fails-to-load-after-reinstallation-of-betaalpha-channel"></a><span data-ttu-id="200dd-304">Xamarin.iOS Visual Studio plugin fails to load after reinstallation of beta/alpha channel</span><span class="sxs-lookup"><span data-stu-id="200dd-304">Xamarin.iOS Visual Studio plugin fails to load after reinstallation of beta/alpha channel</span></span>

<span data-ttu-id="200dd-305">Relevant bug [#40781](https://bugzilla.xamarin.com/show_bug.cgi?id=40781).</span><span class="sxs-lookup"><span data-stu-id="200dd-305">Relevant bug [#40781](https://bugzilla.xamarin.com/show_bug.cgi?id=40781).</span></span>

<span data-ttu-id="200dd-306">This issue may happen when Visual Studio fails to refresh the MEF component cache.</span><span class="sxs-lookup"><span data-stu-id="200dd-306">This issue may happen when Visual Studio fails to refresh the MEF component cache.</span></span> <span data-ttu-id="200dd-307">If that's the case, installing this Visual Studio extension may help: [https://visualstudiogallery.msdn.microsoft.com/22b94661-70c7-4a93-9ca3-8b6dd45f47cd](https://visualstudiogallery.msdn.microsoft.com/22b94661-70c7-4a93-9ca3-8b6dd45f47cd)</span><span class="sxs-lookup"><span data-stu-id="200dd-307">If that's the case, installing this Visual Studio extension may help: [https://visualstudiogallery.msdn.microsoft.com/22b94661-70c7-4a93-9ca3-8b6dd45f47cd](https://visualstudiogallery.msdn.microsoft.com/22b94661-70c7-4a93-9ca3-8b6dd45f47cd)</span></span>

<span data-ttu-id="200dd-308">This will clear the Visual Studio MEF component cache to fix issues with cache corruption.</span><span class="sxs-lookup"><span data-stu-id="200dd-308">This will clear the Visual Studio MEF component cache to fix issues with cache corruption.</span></span>

<a name="errors" />

### <a name="errors-due-to-existing-build-host-processes-on-the-mac"></a><span data-ttu-id="200dd-309">Errors due to existing Build Host Processes on the Mac</span><span class="sxs-lookup"><span data-stu-id="200dd-309">Errors due to existing Build Host Processes on the Mac</span></span>

<span data-ttu-id="200dd-310">Processes from previous build host connections can sometimes interfere with the behavior of the current active connection.</span><span class="sxs-lookup"><span data-stu-id="200dd-310">Processes from previous build host connections can sometimes interfere with the behavior of the current active connection.</span></span> <span data-ttu-id="200dd-311">To check for any existing processes, close Visual Studio and then run the following commands in Terminal on the Mac:</span><span class="sxs-lookup"><span data-stu-id="200dd-311">To check for any existing processes, close Visual Studio and then run the following commands in Terminal on the Mac:</span></span>

```bash
ps -A | grep mono
```

<span data-ttu-id="200dd-312">[![](troubleshooting-images/troubleshooting-image10.png "Running commands in Terminal on the Mac")](troubleshooting-images/troubleshooting-image10.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-312">[![](troubleshooting-images/troubleshooting-image10.png "Running commands in Terminal on the Mac")](troubleshooting-images/troubleshooting-image10.png#lightbox)</span></span>

<span data-ttu-id="200dd-313">To kill the existing processes use the following command:</span><span class="sxs-lookup"><span data-stu-id="200dd-313">To kill the existing processes use the following command:</span></span>

```bash
killall mono
```

### <a name="clearing-the-mac-build-cache"></a><span data-ttu-id="200dd-314">Clearing the Mac Build Cache</span><span class="sxs-lookup"><span data-stu-id="200dd-314">Clearing the Mac Build Cache</span></span>

<span data-ttu-id="200dd-315">If you are troubleshooting a build problem and want to make sure the behavior is not related to any of temporary build files stored on the Mac, you can delete the build cache folder.</span><span class="sxs-lookup"><span data-stu-id="200dd-315">If you are troubleshooting a build problem and want to make sure the behavior is not related to any of temporary build files stored on the Mac, you can delete the build cache folder.</span></span>

1. <span data-ttu-id="200dd-316">Run the following command in Terminal on the Mac:</span><span class="sxs-lookup"><span data-stu-id="200dd-316">Run the following command in Terminal on the Mac:</span></span>

    ```bash
    open "$HOME/Library/Caches/Xamarin"
    ```

2. <span data-ttu-id="200dd-317">Control-click the **mtbs** folder and select **Move to Trash**:</span><span class="sxs-lookup"><span data-stu-id="200dd-317">Control-click the **mtbs** folder and select **Move to Trash**:</span></span>

    <span data-ttu-id="200dd-318">[![](troubleshooting-images/troubleshooting-image9.png "Move the mtbs folder to Trash")](troubleshooting-images/troubleshooting-image9.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="200dd-318">[![](troubleshooting-images/troubleshooting-image9.png "Move the mtbs folder to Trash")](troubleshooting-images/troubleshooting-image9.png#lightbox)</span></span>


## <a name="related-links"></a><span data-ttu-id="200dd-319">Related Links</span><span class="sxs-lookup"><span data-stu-id="200dd-319">Related Links</span></span>

- [<span data-ttu-id="200dd-320">Connecting to the Mac</span><span class="sxs-lookup"><span data-stu-id="200dd-320">Connecting to the Mac</span></span>](~/ios/get-started/installation/windows/connecting-to-mac/index.md)
- [<span data-ttu-id="200dd-321">Connecting a Mac to your Visual Studio environment with XMA (video)</span><span class="sxs-lookup"><span data-stu-id="200dd-321">Connecting a Mac to your Visual Studio environment with XMA (video)</span></span>](https://university.xamarin.com/lightninglectures/xamarin-mac-agent)
