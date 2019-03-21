---
Description: Windows Setup Command-Line Options
ms.assetid: 16001d04-db9f-4953-abc7-37903ef47fd1
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Windows Setup Command-Line Options
ms.date: 05/02/2017
ms.topic: article
---

# <a name="windows-setup-command-line-options"></a><span data-ttu-id="89cd7-103">Windows Setup Command-Line Options</span><span class="sxs-lookup"><span data-stu-id="89cd7-103">Windows Setup Command-Line Options</span></span>


<span data-ttu-id="89cd7-104">The following command-line options are available for Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-104">The following command-line options are available for Windows Setup.</span></span> <span data-ttu-id="89cd7-105">Beginning with Windows 10, version 1607, you can use a setupconfig file as an alternative to passing paramters to Windows Setup on a command line.</span><span class="sxs-lookup"><span data-stu-id="89cd7-105">Beginning with Windows 10, version 1607, you can use a setupconfig file as an alternative to passing paramters to Windows Setup on a command line.</span></span> <span data-ttu-id="89cd7-106">For more information, see [Windows Setup Automation Overview](windows-setup-automation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89cd7-106">For more information, see [Windows Setup Automation Overview](windows-setup-automation-overview.md).</span></span>

<span data-ttu-id="89cd7-107"><b>setup.exe</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-107"><b>setup.exe</b></span></span> 

> [!div class="op_single_selector"]
> - [1394Debug:&lt;channel&gt; baudrate:&lt;baudrate&gt;](#1)
> - [AddBootMgrLast](#2)
> - [Auto {Clean | DataOnly | Upgrade}](#3)
> - [BitLocker {AlwaysSuspend | TryKeepActive  | ForceKeepActive }](#33)
> - [BusParams:&lt;bus.device.function&gt;](#4)
> - [CompactOS {Enable / Disable}](#5)
> - [Compat {IgnoreWarning / ScanOnly}](#6)
> - [CopyLogs&lt;location&gt;](#7)
> - [Debug:&lt;port&gt; {BaudRate:&lt;baudrate&gt;}](#8)
> - [DiagnosticPrompt {enable | disable}](#9)
> - [DynamicUpdate {enable | disable}](#10)
> - [EMSPort: {COM1 | COM2 | usebiossettings | off} /emsbaudrate:&lt;baudrate&gt;](#11)
> - [InstallDrivers&lt;location>:](#12)
> - [InstallFrom&lt;path&gt;](#13)
> - [InstallLangPacks&lt;location&gt;](#14)
> - [m:&lt;folder_name&gt; /noreboot](#15)
> - [MigNEO disable](#36)
> - [MigrateDrivers {all | none}](#16)
> - [NetDebug](#17)
> - [NoReboot](#18)
> - [PKey&lt;product key&gt;](#19)
> - [Priority normal](#35)
> - [PostOOBE&lt;location&gt; \\setupcomplete.cmd](#20)
> - [PostRollback&lt;location&gt; \\setuprollback.cmd](#21)
> - [Quiet](#22)
> - [ReflectDrivers&lt;location&gt;](#23)
> - [ResizeRecoveryPartition {Enable / Disable}](#24)
> - [ShowOOBE {full / none}](#25)
> - [Telemetry {Enable / Disable}](#26)
> - [TempDrive &lt;drive_letter&gt;](#27)
> - [Unattend:&lt;answer_file&gt;](#28)
> - [Uninstall {enable / disable}](#29)
> - [USBDebug:&lt;hostname&gt;](#30)
> - [WDSDiscover](#31)
> - [WDSServer:&lt;servername&gt;](#32)

<span data-ttu-id="89cd7-143">The following table lists Setup command-line options:</span><span class="sxs-lookup"><span data-stu-id="89cd7-143">The following table lists Setup command-line options:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="89cd7-144">Option</span><span class="sxs-lookup"><span data-stu-id="89cd7-144">Option</span></span></th>
<th align="left"><span data-ttu-id="89cd7-145">Description</span><span class="sxs-lookup"><span data-stu-id="89cd7-145">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><p><span data-ttu-id="89cd7-146"><span id="1"></span><b>/1394Debug:</b><i>&lt;channel&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate&gt;</i>]</span><span class="sxs-lookup"><span data-stu-id="89cd7-146"><span id="1"></span><b>/1394Debug:</b><i>&lt;channel&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate&gt;</i>]</span></span></p></td>
<td><p><span data-ttu-id="89cd7-147">Enables kernel debugging over an IEEE 1394 (FireWire) port while Windows is running and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-147">Enables kernel debugging over an IEEE 1394 (FireWire) port while Windows is running and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.</span></span><br />
<span data-ttu-id="89cd7-148">&lt;channel&gt; specifies the debugging channel.</span><span class="sxs-lookup"><span data-stu-id="89cd7-148">&lt;channel&gt; specifies the debugging channel.</span></span> <span data-ttu-id="89cd7-149">The default value for <b>&lt;channel&gt;</b> is <b>1</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-149">The default value for <b>&lt;channel&gt;</b> is <b>1</b>.</span></span><br />
<span data-ttu-id="89cd7-150">[<b>baudrate:</b><i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging.</span><span class="sxs-lookup"><span data-stu-id="89cd7-150">[<b>baudrate:</b><i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging.</span></span> <span data-ttu-id="89cd7-151">The default setting is <b>19200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-151">The default setting is <b>19200</b>.</span></span> <span data-ttu-id="89cd7-152">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-152">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span></span> <span data-ttu-id="89cd7-153">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-153">For example:</span></span><br />  

<span data-ttu-id="89cd7-154"><font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-154"><font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></span></span></p></td>

</tr>
<tr>
<td><p><span data-ttu-id="89cd7-155"><span id="2"></span><b>/AddBootMgrLast</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-155"><span id="2"></span><b>/AddBootMgrLast</b></span></span></font></p></td>
<td><p><span data-ttu-id="89cd7-156">Instructs Windows Setup to add the Windows Boot Manager as the last entry in the UEFI firmware boot order.</span><span class="sxs-lookup"><span data-stu-id="89cd7-156">Instructs Windows Setup to add the Windows Boot Manager as the last entry in the UEFI firmware boot order.</span></span> <span data-ttu-id="89cd7-157">This option is only supported on UEFI PCs running Windows PE 4.0 or later.</span><span class="sxs-lookup"><span data-stu-id="89cd7-157">This option is only supported on UEFI PCs running Windows PE 4.0 or later.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-158"><span id="3"></span><b>/Auto</b> <b>{Clean | DataOnly | Upgrade}</span><span class="sxs-lookup"><span data-stu-id="89cd7-158"><span id="3"></span><b>/Auto</b> <b>{Clean | DataOnly | Upgrade}</span></span></font></p></td>
<td><p><span data-ttu-id="89cd7-159">Performs an automated upgrade to Windows 10 or Windows 8.1 volume license editions only.</span><span class="sxs-lookup"><span data-stu-id="89cd7-159">Performs an automated upgrade to Windows 10 or Windows 8.1 volume license editions only.</span></span><br />
<span data-ttu-id="89cd7-160">When /auto is used, an unattend file cannot be used.</span><span class="sxs-lookup"><span data-stu-id="89cd7-160">When /auto is used, an unattend file cannot be used.</span></span><br />
<span data-ttu-id="89cd7-161">When /auto is used, Windows Setup consumes ei.cfg, and checks compatibility issues before starting the installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-161">When /auto is used, Windows Setup consumes ei.cfg, and checks compatibility issues before starting the installation.</span></span> <span data-ttu-id="89cd7-162">If ei.cfg is malformed, setup exits silently and logs an exit code.</span><span class="sxs-lookup"><span data-stu-id="89cd7-162">If ei.cfg is malformed, setup exits silently and logs an exit code.</span></span><br /><span data-ttu-id="89cd7-163">
<b>Clean</b>: Performs an clean install of Windows.</span><span class="sxs-lookup"><span data-stu-id="89cd7-163">
<b>Clean</b>: Performs an clean install of Windows.</span></span><br /><span data-ttu-id="89cd7-164">
<b>DataOnly</b>: Performs an upgrade of Windows, saving only data (and not apps.) If the data-only installation option is not available due to compatibility checks, Windows Setup will exit silently and log an exit code.</span><span class="sxs-lookup"><span data-stu-id="89cd7-164">
<b>DataOnly</b>: Performs an upgrade of Windows, saving only data (and not apps.) If the data-only installation option is not available due to compatibility checks, Windows Setup will exit silently and log an exit code.</span></span><br /><span data-ttu-id="89cd7-165">
<b>Upgrade</b>: Performs an upgrade of Windows saving apps and data.</span><span class="sxs-lookup"><span data-stu-id="89cd7-165">
<b>Upgrade</b>: Performs an upgrade of Windows saving apps and data.</span></span> <span data-ttu-id="89cd7-166">If the upgrade installation option is not available, or the user needs to resolve an app compatibility issue, Windows Setup will exit silently and log an exit code.</span><span class="sxs-lookup"><span data-stu-id="89cd7-166">If the upgrade installation option is not available, or the user needs to resolve an app compatibility issue, Windows Setup will exit silently and log an exit code.</span></span><br /><span data-ttu-id="89cd7-167">
<b>Setup.exe exit codes</b>: See <a href="#setup_exe_exit_codes">table below</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-167">
<b>Setup.exe exit codes</b>: See <a href="#setup_exe_exit_codes">table below</a>.</span></span><br /><span data-ttu-id="89cd7-168">
<b>/noautoexit</b>: Not used in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-168">
<b>/noautoexit</b>: Not used in Windows 10.</span></span> <span data-ttu-id="89cd7-169">In Windows 8.1, if an error is found, Windows Setup does not exit, but instead stops and stays on the setup screen until the user addresses the issue.</span><span class="sxs-lookup"><span data-stu-id="89cd7-169">In Windows 8.1, if an error is found, Windows Setup does not exit, but instead stops and stays on the setup screen until the user addresses the issue.</span></span> <span data-ttu-id="89cd7-170">The installation from that point on is attended.</span><span class="sxs-lookup"><span data-stu-id="89cd7-170">The installation from that point on is attended.</span></span><br /><span data-ttu-id="89cd7-171">
<b>/performDU</b>: Not used in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-171">
<b>/performDU</b>: Not used in Windows 10.</span></span> <span data-ttu-id="89cd7-172">In Windows 8.1, Windows Setup checks for Dynamic Updates for Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-172">In Windows 8.1, Windows Setup checks for Dynamic Updates for Windows Setup.</span></span><br />
<span data-ttu-id="89cd7-173">Examples:</span><span class="sxs-lookup"><span data-stu-id="89cd7-173">Examples:</span></span><br /><span data-ttu-id="89cd7-174">
<font face="courier" color="red">Setup /auto clean</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-174">
<font face="courier" color="red">Setup /auto clean</font></span></span><br /><span data-ttu-id="89cd7-175">
<font face="courier" color="red">Setup /auto dataonly</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-175">
<font face="courier" color="red">Setup /auto dataonly</font></span></span><br /><span data-ttu-id="89cd7-176">
<font face="courier" color="red">Setup /auto upgrade </font></span><span class="sxs-lookup"><span data-stu-id="89cd7-176">
<font face="courier" color="red">Setup /auto upgrade </font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-177"><span id="33"></span><b>/BitLocker<b> <b>{AlwaysSuspend | TryKeepActive | ForceKeepActive}</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-177"><span id="33"></span><b>/BitLocker<b> <b>{AlwaysSuspend | TryKeepActive | ForceKeepActive}</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-178">Specifies the BitLocker status during upgrades.</span><span class="sxs-lookup"><span data-stu-id="89cd7-178">Specifies the BitLocker status during upgrades.</span></span><br /><span data-ttu-id="89cd7-179">
<b>AlwaysSuspend</b>: BitLocker is always suspended during an upgrade.</span><span class="sxs-lookup"><span data-stu-id="89cd7-179">
<b>AlwaysSuspend</b>: BitLocker is always suspended during an upgrade.</span></span> <span data-ttu-id="89cd7-180">This is the default behavior if the <b>/bitlocker</b> option is not specified.</span><span class="sxs-lookup"><span data-stu-id="89cd7-180">This is the default behavior if the <b>/bitlocker</b> option is not specified.</span></span><br /><span data-ttu-id="89cd7-181">
<b>TryKeepActive</b>: Attempts an upgrade without suspending BitLocker.</span><span class="sxs-lookup"><span data-stu-id="89cd7-181">
<b>TryKeepActive</b>: Attempts an upgrade without suspending BitLocker.</span></span> <span data-ttu-id="89cd7-182">If the upgrade fails, Windows Setup will suspend BitLocker and complete the upgrade.</span><span class="sxs-lookup"><span data-stu-id="89cd7-182">If the upgrade fails, Windows Setup will suspend BitLocker and complete the upgrade.</span></span><br /><span data-ttu-id="89cd7-183">
<b>ForceKeepActive</b>: Enables upgrading without suspending BitLocker.</span><span class="sxs-lookup"><span data-stu-id="89cd7-183">
<b>ForceKeepActive</b>: Enables upgrading without suspending BitLocker.</span></span> <span data-ttu-id="89cd7-184">If the upgrade can't be completed because BitLocker is active, the upgrade will fail.</span><span class="sxs-lookup"><span data-stu-id="89cd7-184">If the upgrade can't be completed because BitLocker is active, the upgrade will fail.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-185"><span id="4"></span><b>/BusParams</b>:<i>&lt;bus.device.function&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-185"><span id="4"></span><b>/BusParams</b>:<i>&lt;bus.device.function&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-186">Specifies the PCI address of a 1394, USB, or NET debug port.</span><span class="sxs-lookup"><span data-stu-id="89cd7-186">Specifies the PCI address of a 1394, USB, or NET debug port.</span></span> <span data-ttu-id="89cd7-187">The bus, device, and function numbers must be in decimal format.</span><span class="sxs-lookup"><span data-stu-id="89cd7-187">The bus, device, and function numbers must be in decimal format.</span></span> <span data-ttu-id="89cd7-188">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-188">Example:</span></span><p><span data-ttu-id="89cd7-189"><font face="courier" color="red">Setup /busparams:0.29.7 </font></span><span class="sxs-lookup"><span data-stu-id="89cd7-189"><font face="courier" color="red">Setup /busparams:0.29.7 </font></span></span><p><span data-ttu-id="89cd7-190">For more info, see <a href="https://go.microsoft.com/fwlink/?LinkId=317360">Setting Up Kernel Debugging with USB 2.0</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-190">For more info, see <a href="https://go.microsoft.com/fwlink/?LinkId=317360">Setting Up Kernel Debugging with USB 2.0</a>.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-191"><span id="5"></span><b>/CompactOS</b> {<b>Enable</b> / <b>Disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-191"><span id="5"></span><b>/CompactOS</b> {<b>Enable</b> / <b>Disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-192">Specifies whether to use the Compact OS feature to save hard drive space.</span><span class="sxs-lookup"><span data-stu-id="89cd7-192">Specifies whether to use the Compact OS feature to save hard drive space.</span></span> <span data-ttu-id="89cd7-193">By default, Windows Setup determines whether to use this feature automatically.</span><span class="sxs-lookup"><span data-stu-id="89cd7-193">By default, Windows Setup determines whether to use this feature automatically.</span></span><br /><span data-ttu-id="89cd7-194">
<b>Enable</b>: Setup installs Windows using compressed system files.</span><span class="sxs-lookup"><span data-stu-id="89cd7-194">
<b>Enable</b>: Setup installs Windows using compressed system files.</span></span><br /><span data-ttu-id="89cd7-195">
<b>Disable</b>: Setup installs Windows using uncompressed system files</span><span class="sxs-lookup"><span data-stu-id="89cd7-195">
<b>Disable</b>: Setup installs Windows using uncompressed system files</span></span><br />
<span data-ttu-id="89cd7-196">To learn more about Compact OS, see <a href="compact-os.md">Compact OS, single-instancing, and image optimization</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-196">To learn more about Compact OS, see <a href="compact-os.md">Compact OS, single-instancing, and image optimization</a>.</span></span><br /><span data-ttu-id="89cd7-197">
<font face="courier" color="red">Setup /compactos enable</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-197">
<font face="courier" color="red">Setup /compactos enable</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-198"><span id="6"></span><b>/Compat</b> {<b>IgnoreWarning</b> / <b>ScanOnly</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-198"><span id="6"></span><b>/Compat</b> {<b>IgnoreWarning</b> / <b>ScanOnly</b>}</span></span> </p></td>
<td><p><span data-ttu-id="89cd7-199"><b>IgnoreWarning</b>: Setup completes installation, ignoring any dismissible compatibility messages.</span><span class="sxs-lookup"><span data-stu-id="89cd7-199"><b>IgnoreWarning</b>: Setup completes installation, ignoring any dismissible compatibility messages.</span></span><br /><span data-ttu-id="89cd7-200">
<b>ScanOnly</b>: Windows Setup runs through compatibility scans, and then exits (without completing the installation) with an exit code to indicate if any compatibility concerns are present.</span><span class="sxs-lookup"><span data-stu-id="89cd7-200">
<b>ScanOnly</b>: Windows Setup runs through compatibility scans, and then exits (without completing the installation) with an exit code to indicate if any compatibility concerns are present.</span></span> <span data-ttu-id="89cd7-201">Setup will return 0xC1900210 if no concerns are found.</span><span class="sxs-lookup"><span data-stu-id="89cd7-201">Setup will return 0xC1900210 if no concerns are found.</span></span> <span data-ttu-id="89cd7-202">Setup will return 0xC1900208 if compatibility concerns are found.</span><span class="sxs-lookup"><span data-stu-id="89cd7-202">Setup will return 0xC1900208 if compatibility concerns are found.</span></span><br />
<span data-ttu-id="89cd7-203">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-203">Example:</span></span><br /><span data-ttu-id="89cd7-204">
<font face="courier" color="red">Setup /compat IgnoreWarning</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-204">
<font face="courier" color="red">Setup /compat IgnoreWarning</font></span></span><br />
<span data-ttu-id="89cd7-205">If you launch Setup with <font face="courier" color="red">/Compat ScanOnly</font>:</span><span class="sxs-lookup"><span data-stu-id="89cd7-205">If you launch Setup with <font face="courier" color="red">/Compat ScanOnly</font>:</span></span><br />
<ul><li><span data-ttu-id="89cd7-206">If it does not find any compat issue, it will return MOSETUP_E_COMPAT_SCANONLY (0xC1900210)</span><span class="sxs-lookup"><span data-stu-id="89cd7-206">If it does not find any compat issue, it will return MOSETUP_E_COMPAT_SCANONLY (0xC1900210)</span></span></li>
<li><span data-ttu-id="89cd7-207">If it finds Actionable compat issues, like Apps, it will return MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)</span><span class="sxs-lookup"><span data-stu-id="89cd7-207">If it finds Actionable compat issues, like Apps, it will return MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)</span></span></li>
<li><span data-ttu-id="89cd7-208">If it finds that the Mig-Choice selected is not available, it will return MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)</span><span class="sxs-lookup"><span data-stu-id="89cd7-208">If it finds that the Mig-Choice selected is not available, it will return MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)</span></span></li>
<li><span data-ttu-id="89cd7-209">If it finds that machine is not eligible for Windows 10, it will return MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)</span><span class="sxs-lookup"><span data-stu-id="89cd7-209">If it finds that machine is not eligible for Windows 10, it will return MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)</span></span></li>
<li><span data-ttu-id="89cd7-210">If it finds that machine does not have enough free space to install, it will return MOSETUP_E_INSTALLDISKSPACE_BLOCK (0xC190020E)</span><span class="sxs-lookup"><span data-stu-id="89cd7-210">If it finds that machine does not have enough free space to install, it will return MOSETUP_E_INSTALLDISKSPACE_BLOCK (0xC190020E)</span></span></li>
</ul><span data-ttu-id="89cd7-211">This command works with other switches.</span><span class="sxs-lookup"><span data-stu-id="89cd7-211">This command works with other switches.</span></span> <span data-ttu-id="89cd7-212">For example, to run Setup in the background without any UI:</span><span class="sxs-lookup"><span data-stu-id="89cd7-212">For example, to run Setup in the background without any UI:</span></span><br /><span data-ttu-id="89cd7-213">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-213">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly</font></span></span><br />
<span data-ttu-id="89cd7-214">To ignore common disclaimers in the UI, for example, language changes:</span><span class="sxs-lookup"><span data-stu-id="89cd7-214">To ignore common disclaimers in the UI, for example, language changes:</span></span><br /><span data-ttu-id="89cd7-215">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-215">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning</font></span></span><br />
<span data-ttu-id="89cd7-216">Most of the time, an Admin would like to look at the compat XML if Setup found compat issues.</span><span class="sxs-lookup"><span data-stu-id="89cd7-216">Most of the time, an Admin would like to look at the compat XML if Setup found compat issues.</span></span> <span data-ttu-id="89cd7-217">For that the admin can even use copy logs flag to collect Setup logs:</span><span class="sxs-lookup"><span data-stu-id="89cd7-217">For that the admin can even use copy logs flag to collect Setup logs:</span></span><br /><span data-ttu-id="89cd7-218">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning /CopyLogs C:\Temp\Logfiles.log </font></span><span class="sxs-lookup"><span data-stu-id="89cd7-218">
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning /CopyLogs C:\Temp\Logfiles.log </font></span></span><br />
<span data-ttu-id="89cd7-219">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-219">This setting is new for Windows 10.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-220"><span id="7"></span><b>/CopyLogs</b><i>&lt;location&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-220"><span id="7"></span><b>/CopyLogs</b><i>&lt;location&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-221">Setup will copy or upload logs(compressed) upon failure to the specified location (assuming machine/user has permission and network access to location).</span><span class="sxs-lookup"><span data-stu-id="89cd7-221">Setup will copy or upload logs(compressed) upon failure to the specified location (assuming machine/user has permission and network access to location).</span></span><br />
<span data-ttu-id="89cd7-222">Accepted parameters are local file paths and UNC network paths.</span><span class="sxs-lookup"><span data-stu-id="89cd7-222">Accepted parameters are local file paths and UNC network paths.</span></span><br />
<span data-ttu-id="89cd7-223">Note: This runs in the system context, so it may not have permissions to copy to locations that require user permissions.</span><span class="sxs-lookup"><span data-stu-id="89cd7-223">Note: This runs in the system context, so it may not have permissions to copy to locations that require user permissions.</span></span><br />
<span data-ttu-id="89cd7-224">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-224">Example:</span></span><br /><span data-ttu-id="89cd7-225">
<font face="courier" color="red">Setup /copylogs \\server\share\</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-225">
<font face="courier" color="red">Setup /copylogs \\server\share\</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-226"><span id="8"></span><b>/Debug:</b><i>&lt;port&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate></i>]</span><span class="sxs-lookup"><span data-stu-id="89cd7-226"><span id="8"></span><b>/Debug:</b><i>&lt;port&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate></i>]</span></span></p></td>
<td><p><span data-ttu-id="89cd7-227">Enables kernel debugging over a communications (COM) port when Windows is running, and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-227">Enables kernel debugging over a communications (COM) port when Windows is running, and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.</span></span><br />
<span data-ttu-id="89cd7-228">&lt;port&gt; specifies the debugging port.</span><span class="sxs-lookup"><span data-stu-id="89cd7-228">&lt;port&gt; specifies the debugging port.</span></span> <span data-ttu-id="89cd7-229">The default value for &lt;port&gt; is 1.</span><span class="sxs-lookup"><span data-stu-id="89cd7-229">The default value for &lt;port&gt; is 1.</span></span><br />
<span data-ttu-id="89cd7-230">[<b>baudrate</b>:&lt;baudrate&gt;] specifies the baud to use when Windows transfers data during debugging.</span><span class="sxs-lookup"><span data-stu-id="89cd7-230">[<b>baudrate</b>:&lt;baudrate&gt;] specifies the baud to use when Windows transfers data during debugging.</span></span> <span data-ttu-id="89cd7-231">The default setting is <b>19200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-231">The default setting is <b>19200</b>.</span></span> <span data-ttu-id="89cd7-232">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-232">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span></span> <span data-ttu-id="89cd7-233">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-233">For example:</span></span><br /><span data-ttu-id="89cd7-234">
<font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-234">
<font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-235"><span id="9"></span>/<b>DiagnosticPrompt</b> {<b>enable</b> | <b>disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-235"><span id="9"></span>/<b>DiagnosticPrompt</b> {<b>enable</b> | <b>disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-236">Specifies that the Command Prompt is available during Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-236">Specifies that the Command Prompt is available during Windows Setup.</span></span><br /><span data-ttu-id="89cd7-237">
<b>Enable</b>: The Command Prompt can be accessed by pressing Shift+F10 during Windows setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-237">
<b>Enable</b>: The Command Prompt can be accessed by pressing Shift+F10 during Windows setup.</span></span><br /><span data-ttu-id="89cd7-238">
<b>Disable</b>: The Command Prompt is not available during Windows setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-238">
<b>Disable</b>: The Command Prompt is not available during Windows setup.</span></span> <span data-ttu-id="89cd7-239">The Command Prompt wil not be available while offline and OOBE phases are running.</span><span class="sxs-lookup"><span data-stu-id="89cd7-239">The Command Prompt wil not be available while offline and OOBE phases are running.</span></span> <span data-ttu-id="89cd7-240">This is the default setting.</span><span class="sxs-lookup"><span data-stu-id="89cd7-240">This is the default setting.</span></span><br><span data-ttu-id="89cd7-241">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-241">Example:</span></span><br /><span data-ttu-id="89cd7-242">
<font face="courier" color="red">setup /DiagnosticPrompt enable</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-242">
<font face="courier" color="red">setup /DiagnosticPrompt enable</font></span></span><br />
<span data-ttu-id="89cd7-243">This setting is new for Windows 10, Version 1703.</span><span class="sxs-lookup"><span data-stu-id="89cd7-243">This setting is new for Windows 10, Version 1703.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-244"><span id="10"></span><b>/DynamicUpdate</b> {<b>enable</b> | <b>disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-244"><span id="10"></span><b>/DynamicUpdate</b> {<b>enable</b> | <b>disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-245">Specifies whether setup will perform Dynamic Update operations (search, download, and install updates).</span><span class="sxs-lookup"><span data-stu-id="89cd7-245">Specifies whether setup will perform Dynamic Update operations (search, download, and install updates).</span></span> <span data-ttu-id="89cd7-246">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-246">Example:</span></span><br /><span data-ttu-id="89cd7-247">
<font face="courier" color="red">setup /auto upgrade /DynamicUpdate disable </font></span><span class="sxs-lookup"><span data-stu-id="89cd7-247">
<font face="courier" color="red">setup /auto upgrade /DynamicUpdate disable </font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-248"><span id="11"></span><b>/EMSPort</b>: {<b>COM1</b> | <b>COM2</b> | <b>off</b>} [<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>]</span><span class="sxs-lookup"><span data-stu-id="89cd7-248"><span id="11"></span><b>/EMSPort</b>: {<b>COM1</b> | <b>COM2</b> | <b>off</b>} [<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>]</span></span></p></td>
<td><p><span data-ttu-id="89cd7-249">Enables or disables Emergency Management Services (EMS) during Windows Setup and after the server operating system has been installed.</span><span class="sxs-lookup"><span data-stu-id="89cd7-249">Enables or disables Emergency Management Services (EMS) during Windows Setup and after the server operating system has been installed.</span></span> <span data-ttu-id="89cd7-250">The following arguments are used to specify the behavior of EMS during Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-250">The following arguments are used to specify the behavior of EMS during Windows Setup.</span></span><br /><span data-ttu-id="89cd7-251">
<b>COM1</b> enables EMS over COM1.</span><span class="sxs-lookup"><span data-stu-id="89cd7-251">
<b>COM1</b> enables EMS over COM1.</span></span> <span data-ttu-id="89cd7-252">Supported for x86 systems only.</span><span class="sxs-lookup"><span data-stu-id="89cd7-252">Supported for x86 systems only.</span></span><br /><span data-ttu-id="89cd7-253">
<b>COM2</b> enables EMS over COM2.</span><span class="sxs-lookup"><span data-stu-id="89cd7-253">
<b>COM2</b> enables EMS over COM2.</span></span> <span data-ttu-id="89cd7-254">Supported for x86 systems only.</span><span class="sxs-lookup"><span data-stu-id="89cd7-254">Supported for x86 systems only.</span></span><br /><span data-ttu-id="89cd7-255">
<b>usebiossettings</b> uses the setting that the BIOS specifies.</span><span class="sxs-lookup"><span data-stu-id="89cd7-255">
<b>usebiossettings</b> uses the setting that the BIOS specifies.</span></span> <span data-ttu-id="89cd7-256">For x86 systems, Windows uses the value from the Serial Port Console Redirection (SPCR) table.</span><span class="sxs-lookup"><span data-stu-id="89cd7-256">For x86 systems, Windows uses the value from the Serial Port Console Redirection (SPCR) table.</span></span> <span data-ttu-id="89cd7-257">If no SPCR table or EFI console device path is specified in the BIOS, Windows disables <b>usebiossettings.usebiossettings</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-257">If no SPCR table or EFI console device path is specified in the BIOS, Windows disables <b>usebiossettings.usebiossettings</b></span></span><br /><span data-ttu-id="89cd7-258">
<b>off</b> disables EMS.</span><span class="sxs-lookup"><span data-stu-id="89cd7-258">
<b>off</b> disables EMS.</span></span> <span data-ttu-id="89cd7-259">If EMS is disabled in Windows Setup, you can later enable EMS by modifying the boot settings.</span><span class="sxs-lookup"><span data-stu-id="89cd7-259">If EMS is disabled in Windows Setup, you can later enable EMS by modifying the boot settings.</span></span><br />
<span data-ttu-id="89cd7-260">[<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging.</span><span class="sxs-lookup"><span data-stu-id="89cd7-260">[<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging.</span></span> <span data-ttu-id="89cd7-261">The default is <b>19200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-261">The default is <b>19200</b>.</span></span> <span data-ttu-id="89cd7-262">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-262">You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>.</span></span> <span data-ttu-id="89cd7-263">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-263">For example:</span></span><br /><span data-ttu-id="89cd7-264">
<font face="courier" color="red">Setup /emsport:COM1 /emsbaudrate:115200</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-264">
<font face="courier" color="red">Setup /emsport:COM1 /emsbaudrate:115200</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-265"><span id="12"></span><b>/InstallDrivers</b><i>&lt;location&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-265"><span id="12"></span><b>/InstallDrivers</b><i>&lt;location&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-266">Adds .inf-style drivers to the new Windows 10 installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-266">Adds .inf-style drivers to the new Windows 10 installation.</span></span> <span data-ttu-id="89cd7-267">The driver .inf can be in a folder within the specified location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-267">The driver .inf can be in a folder within the specified location.</span></span> <span data-ttu-id="89cd7-268">The command will recurse through the specified location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-268">The command will recurse through the specified location.</span></span><br />
<span data-ttu-id="89cd7-269">Accepted parameters are a local file path or UNC network path to a folder that contains .inf files.</span><span class="sxs-lookup"><span data-stu-id="89cd7-269">Accepted parameters are a local file path or UNC network path to a folder that contains .inf files.</span></span> <span data-ttu-id="89cd7-270">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-270">Example:</span></span><br /><span data-ttu-id="89cd7-271">
<font face="courier" color="red">setup.exe /auto upgrade /installdrivers C:\Fabrikam\drivers /noreboot </font></span><span class="sxs-lookup"><span data-stu-id="89cd7-271">
<font face="courier" color="red">setup.exe /auto upgrade /installdrivers C:\Fabrikam\drivers /noreboot </font></span></span><br />
<span data-ttu-id="89cd7-272">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-272">This setting is new for Windows 10.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-273"><span id="13"></span><b>/InstallFrom</b><i>&lt;path&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-273"><span id="13"></span><b>/InstallFrom</b><i>&lt;path&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-274">Specifies a different Install.wim file to use during Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-274">Specifies a different Install.wim file to use during Windows Setup.</span></span> <span data-ttu-id="89cd7-275">This enables you to use a single preinstallation environment to install multiple versions of Windows images.</span><span class="sxs-lookup"><span data-stu-id="89cd7-275">This enables you to use a single preinstallation environment to install multiple versions of Windows images.</span></span> <span data-ttu-id="89cd7-276">For example, you can use a 32-bit version of Windows Setup to deploy a 64-bit Windows image.</span><span class="sxs-lookup"><span data-stu-id="89cd7-276">For example, you can use a 32-bit version of Windows Setup to deploy a 64-bit Windows image.</span></span> <span data-ttu-id="89cd7-277">You can also use an answer file for cross-platform deployments.</span><span class="sxs-lookup"><span data-stu-id="89cd7-277">You can also use an answer file for cross-platform deployments.</span></span> <span data-ttu-id="89cd7-278">For more information, see “Creating a WIM for Multiple Architecture Types” in <a href="windows-setup-supported-platforms-and-cross-platform-deployments.md#creating_wimfile">Windows Setup Supported Platforms and Cross-Platform Deployments</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-278">For more information, see “Creating a WIM for Multiple Architecture Types” in <a href="windows-setup-supported-platforms-and-cross-platform-deployments.md#creating_wimfile">Windows Setup Supported Platforms and Cross-Platform Deployments</a>.</span></span><br />
<span data-ttu-id="89cd7-279">&lt;path&gt; specifies the path of the .wim file to install.</span><span class="sxs-lookup"><span data-stu-id="89cd7-279">&lt;path&gt; specifies the path of the .wim file to install.</span></span> <span data-ttu-id="89cd7-280">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-280">For example:</span></span><br /><span data-ttu-id="89cd7-281">
<font face="courier" color="red">Setup /installfrom D:\custom.wim</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-281">
<font face="courier" color="red">Setup /installfrom D:\custom.wim</font></span></span><br />
<span data-ttu-id="89cd7-282">Can also be used with split image files (.swm).</span><span class="sxs-lookup"><span data-stu-id="89cd7-282">Can also be used with split image files (.swm).</span></span> <span data-ttu-id="89cd7-283">Select the first split image file in the series, for example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-283">Select the first split image file in the series, for example:</span></span><br /><span data-ttu-id="89cd7-284">
<font face="courier" color="red">Setup /installfrom D:\install.swm</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-284">
<font face="courier" color="red">Setup /installfrom D:\install.swm</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-285"><span id="14"></span><b>/InstallLangPacks</b><i>&lt;location&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-285"><span id="14"></span><b>/InstallLangPacks</b><i>&lt;location&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-286">Adds language packs (lp.cab) to the new Windows 10 installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-286">Adds language packs (lp.cab) to the new Windows 10 installation.</span></span><br />
<span data-ttu-id="89cd7-287">The language packs can be in a folder within the specified location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-287">The language packs can be in a folder within the specified location.</span></span> <span data-ttu-id="89cd7-288">The command installs all lp.cab files and language capabilities such as text-to-speech recognition, in the folder and subfolders at the specified location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-288">The command installs all lp.cab files and language capabilities such as text-to-speech recognition, in the folder and subfolders at the specified location.</span></span><br />
<span data-ttu-id="89cd7-289">Accepted parameters are a local file path or UNC network path to a folder that contains .inf files.</span><span class="sxs-lookup"><span data-stu-id="89cd7-289">Accepted parameters are a local file path or UNC network path to a folder that contains .inf files.</span></span><br /><span data-ttu-id="89cd7-290">
<font face="courier" color="red">setup /auto upgrade /installlangpacks C:\Fabrikam\Languages\French /noreboot</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-290">
<font face="courier" color="red">setup /auto upgrade /installlangpacks C:\Fabrikam\Languages\French /noreboot</font></span></span><br />
<span data-ttu-id="89cd7-291">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-291">This setting is new for Windows 10.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-292"><span id="15"></span><b>/m</b>:<i>&lt;folder_name&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-292"><span id="15"></span><b>/m</b>:<i>&lt;folder_name&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-293">Instructs Setup to copy alternate files from an alternate location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-293">Instructs Setup to copy alternate files from an alternate location.</span></span> <span data-ttu-id="89cd7-294">This option instructs Setup to look in the alternate location first, and, if files are present, to use them instead of the files from the default location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-294">This option instructs Setup to look in the alternate location first, and, if files are present, to use them instead of the files from the default location.</span></span><br /><span data-ttu-id="89cd7-295">
<i>&lt;folder_name&gt;</i> specifies the name and the location of the folder that contains the replacement files and can be any local drive location.</span><span class="sxs-lookup"><span data-stu-id="89cd7-295">
<i>&lt;folder_name&gt;</i> specifies the name and the location of the folder that contains the replacement files and can be any local drive location.</span></span> <span data-ttu-id="89cd7-296">UNC paths are not supported.</span><span class="sxs-lookup"><span data-stu-id="89cd7-296">UNC paths are not supported.</span></span><br />
<span data-ttu-id="89cd7-297">You must know where the files will be installed on the Windows installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-297">You must know where the files will be installed on the Windows installation.</span></span> <span data-ttu-id="89cd7-298">All the additional files must be copied to an $OEM$ folder in your installation sources or in the <i>&lt;folder_name&gt;</i>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-298">All the additional files must be copied to an $OEM$ folder in your installation sources or in the <i>&lt;folder_name&gt;</i>.</span></span> <span data-ttu-id="89cd7-299">The $OEM$ structure provides a representation of the destination installation disk.</span><span class="sxs-lookup"><span data-stu-id="89cd7-299">The $OEM$ structure provides a representation of the destination installation disk.</span></span> <span data-ttu-id="89cd7-300">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-300">For example:</span></span><br /><span data-ttu-id="89cd7-301">
<font face="courier" color="red">$OEM$\$1</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-301">
<font face="courier" color="red">$OEM$\$1</font></span></span><br />
<span data-ttu-id="89cd7-302">maps to %SYSTEMDRIVE%, which could be drive C.</span><span class="sxs-lookup"><span data-stu-id="89cd7-302">maps to %SYSTEMDRIVE%, which could be drive C.</span></span><br /><span data-ttu-id="89cd7-303">
<font face="courier" color="red">$OEM$\$$</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-303">
<font face="courier" color="red">$OEM$\$$</font></span></span><br />
<span data-ttu-id="89cd7-304">maps to %WINDIR%, which could be C:\windows.</span><span class="sxs-lookup"><span data-stu-id="89cd7-304">maps to %WINDIR%, which could be C:\windows.</span></span><br /><span data-ttu-id="89cd7-305">
<font face="courier" color="red">$OEM$\$progs</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-305">
<font face="courier" color="red">$OEM$\$progs</font></span></span><br />
<span data-ttu-id="89cd7-306">maps to the program files directory.</span><span class="sxs-lookup"><span data-stu-id="89cd7-306">maps to the program files directory.</span></span><br /><span data-ttu-id="89cd7-307">
<font face="courier" color="red">$OEM$\$docs</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-307">
<font face="courier" color="red">$OEM$\$docs</font></span></span><br />
<span data-ttu-id="89cd7-308">maps to the user's My Documents folder.</span><span class="sxs-lookup"><span data-stu-id="89cd7-308">maps to the user's My Documents folder.</span></span><br />
<span data-ttu-id="89cd7-309">For example, to copy an updated C:\Program Files\Messenger\Msmsgs.exe file into the Windows installation, create the following folder structure on the Pro\Sources\$OEM$\$Progs\Messenger\Msmsgs.exe installation source by using the <b>Setup</b> command:</span><span class="sxs-lookup"><span data-stu-id="89cd7-309">For example, to copy an updated C:\Program Files\Messenger\Msmsgs.exe file into the Windows installation, create the following folder structure on the Pro\Sources\$OEM$\$Progs\Messenger\Msmsgs.exe installation source by using the <b>Setup</b> command:</span></span><br /><span data-ttu-id="89cd7-310">
<font face="courier" color="red">Pro\sources\setup.exe /m</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-310">
<font face="courier" color="red">Pro\sources\setup.exe /m</font></span></span><br />
<span data-ttu-id="89cd7-311">If you replace a file that Windows file protection protects, you must also copy the updated file to the local sources to be installed with Windows.</span><span class="sxs-lookup"><span data-stu-id="89cd7-311">If you replace a file that Windows file protection protects, you must also copy the updated file to the local sources to be installed with Windows.</span></span> <span data-ttu-id="89cd7-312">For example, you may copy the file to the C:\Windows\i386 folder.</span><span class="sxs-lookup"><span data-stu-id="89cd7-312">For example, you may copy the file to the C:\Windows\i386 folder.</span></span> <span data-ttu-id="89cd7-313">The file name must be the same as the name that is used in Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-313">The file name must be the same as the name that is used in Windows Setup.</span></span> <span data-ttu-id="89cd7-314">For example, add the following file and folder structure to your $OEM$ directory:</span><span class="sxs-lookup"><span data-stu-id="89cd7-314">For example, add the following file and folder structure to your $OEM$ directory:</span></span><br /><span data-ttu-id="89cd7-315">
<font face="courier" color="red">Pro\sources\$OEM$\$$\i386\msmsgs.ex_</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-315">
<font face="courier" color="red">Pro\sources\$OEM$\$$\i386\msmsgs.ex_</font></span></span><br />
<span data-ttu-id="89cd7-316">If you use files that are not on an installation share, you must specify the folder name.</span><span class="sxs-lookup"><span data-stu-id="89cd7-316">If you use files that are not on an installation share, you must specify the folder name.</span></span> <span data-ttu-id="89cd7-317">In this example the &lt;folder_name&gt; is C:\additional_files:</span><span class="sxs-lookup"><span data-stu-id="89cd7-317">In this example the &lt;folder_name&gt; is C:\additional_files:</span></span><br /><span data-ttu-id="89cd7-318">
<font face="courier" color="red">Setup /m:C:\additional_files</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-318">
<font face="courier" color="red">Setup /m:C:\additional_files</font></span></span><br />
<span data-ttu-id="89cd7-319">where C:\additional_files is your customized $OEM$ directory.</span><span class="sxs-lookup"><span data-stu-id="89cd7-319">where C:\additional_files is your customized $OEM$ directory.</span></span> <span data-ttu-id="89cd7-320">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-320">For example:</span></span><br /><span data-ttu-id="89cd7-321">
<font face="courier" color="red">C:\additional_files\$$\i386\msmsgs.ex_</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-321">
<font face="courier" color="red">C:\additional_files\$$\i386\msmsgs.ex_</font></span></span><br />
<span data-ttu-id="89cd7-322">If you change resources in your replacement files, you must add the updated Multilanguage User Interface (MUI) files to the installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-322">If you change resources in your replacement files, you must add the updated Multilanguage User Interface (MUI) files to the installation.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-323"><span id="36"></span><b>/MigNEO Disable</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-323"><span id="36"></span><b>/MigNEO Disable</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-324">Tells Windows Setup to perform an upgrade of Windows without additional offline phase optimizations.</span><span class="sxs-lookup"><span data-stu-id="89cd7-324">Tells Windows Setup to perform an upgrade of Windows without additional offline phase optimizations.</span></span> <span data-ttu-id="89cd7-325">This option is available in Windows 10, version 1803 and later.</span><span class="sxs-lookup"><span data-stu-id="89cd7-325">This option is available in Windows 10, version 1803 and later.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-326"><span id="16"></span><b>/MigrateDrivers</b> {<b>all</b> | <b>none</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-326"><span id="16"></span><b>/MigrateDrivers</b> {<b>all</b> | <b>none</b>}</span></span></p></td>
<td><p> <span data-ttu-id="89cd7-327">Instructs Setup whether to migrate the drivers from the existing installation during the upgrade.</span><span class="sxs-lookup"><span data-stu-id="89cd7-327">Instructs Setup whether to migrate the drivers from the existing installation during the upgrade.</span></span> <span data-ttu-id="89cd7-328">You can specify <b>All</b> or <b>None</b>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-328">You can specify <b>All</b> or <b>None</b>.</span></span> <span data-ttu-id="89cd7-329">By default, Setup decides which is best for each individual driver based on the install choice.</span><span class="sxs-lookup"><span data-stu-id="89cd7-329">By default, Setup decides which is best for each individual driver based on the install choice.</span></span><br />
<span data-ttu-id="89cd7-330">You can use this switch with <b>/installdrivers</b>, though it's not required.</span><span class="sxs-lookup"><span data-stu-id="89cd7-330">You can use this switch with <b>/installdrivers</b>, though it's not required.</span></span><br /><span data-ttu-id="89cd7-331">
<font face="courier" color="red">Setup /auto upgrade /migratedrivers all</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-331">
<font face="courier" color="red">Setup /auto upgrade /migratedrivers all</font></span></span><br /><span data-ttu-id="89cd7-332">
<font face="courier" color="red">Setup /auto upgrade /migratedrivers none /installdrivers N:\NewDrivers</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-332">
<font face="courier" color="red">Setup /auto upgrade /migratedrivers none /installdrivers N:\NewDrivers</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-333"><span id="17"></span><b>/NetDebug</b>:hostip=<i>&lt;w.x.y.z&gt;</i>,port=<i>&lt;n&gt;</i>,key= <i>&lt;q.r.s.t&gt;</i>[,nodhcp][,busparams=<i>n.o.p</i>]</span><span class="sxs-lookup"><span data-stu-id="89cd7-333"><span id="17"></span><b>/NetDebug</b>:hostip=<i>&lt;w.x.y.z&gt;</i>,port=<i>&lt;n&gt;</i>,key= <i>&lt;q.r.s.t&gt;</i>[,nodhcp][,busparams=<i>n.o.p</i>]</span></span></p></td>
<td><p><span data-ttu-id="89cd7-334">Enables kernel debugging over the network.</span><span class="sxs-lookup"><span data-stu-id="89cd7-334">Enables kernel debugging over the network.</span></span><br />
<span data-ttu-id="89cd7-335">Use hostip to identify the IP address of the host computer.</span><span class="sxs-lookup"><span data-stu-id="89cd7-335">Use hostip to identify the IP address of the host computer.</span></span><br />
<span data-ttu-id="89cd7-336">Use port to identify the port.</span><span class="sxs-lookup"><span data-stu-id="89cd7-336">Use port to identify the port.</span></span> <span data-ttu-id="89cd7-337">The default start port is 49152, and the default end port is 65535.</span><span class="sxs-lookup"><span data-stu-id="89cd7-337">The default start port is 49152, and the default end port is 65535.</span></span><br />
<span data-ttu-id="89cd7-338">Use key to provide a password to set up a secure connection.</span><span class="sxs-lookup"><span data-stu-id="89cd7-338">Use key to provide a password to set up a secure connection.</span></span><br />
<span data-ttu-id="89cd7-339">Use nodhcp to avoid using a DHCP connection.</span><span class="sxs-lookup"><span data-stu-id="89cd7-339">Use nodhcp to avoid using a DHCP connection.</span></span> <span data-ttu-id="89cd7-340">(optional)</span><span class="sxs-lookup"><span data-stu-id="89cd7-340">(optional)</span></span><br />
<span data-ttu-id="89cd7-341">Use busparams to select the bus number, device number, and function number of an adapter for a specific PCI bus device.</span><span class="sxs-lookup"><span data-stu-id="89cd7-341">Use busparams to select the bus number, device number, and function number of an adapter for a specific PCI bus device.</span></span> <span data-ttu-id="89cd7-342">(optional)</span><span class="sxs-lookup"><span data-stu-id="89cd7-342">(optional)</span></span><br />
<span data-ttu-id="89cd7-343">Examples:</span><span class="sxs-lookup"><span data-stu-id="89cd7-343">Examples:</span></span><br /><span data-ttu-id="89cd7-344">
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000,key=0.0.0.0</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-344">
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000,key=0.0.0.0</font></span></span><br /><span data-ttu-id="89cd7-345">
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000, key=abcdefg.123.hijklmnop.456,nodhcp</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-345">
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000, key=abcdefg.123.hijklmnop.456,nodhcp</font></span></span><br /><span data-ttu-id="89cd7-346">
<font face="courier" color="red">setup /netdebug:hostip=10.1.4.8,port=50000, key=dont.use.previous.keys,busparams=1.5.0</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-346">
<font face="courier" color="red">setup /netdebug:hostip=10.1.4.8,port=50000, key=dont.use.previous.keys,busparams=1.5.0</font></span></span><br />
<span data-ttu-id="89cd7-347">For details, see <a href="https://go.microsoft.com/fwlink/p/?linkid=317384">Setting Up Kernel-Mode Debugging over a Network Cable Manually</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-347">For details, see <a href="https://go.microsoft.com/fwlink/p/?linkid=317384">Setting Up Kernel-Mode Debugging over a Network Cable Manually</a>.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-348"><span id="18"></span><b>/NoReboot</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-348"><span id="18"></span><b>/NoReboot</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-349">Instructs Windows Setup not to restart the computer after the down-level phase of Windows Setup completes.</span><span class="sxs-lookup"><span data-stu-id="89cd7-349">Instructs Windows Setup not to restart the computer after the down-level phase of Windows Setup completes.</span></span> <span data-ttu-id="89cd7-350">The <b>/noreboot</b> option enables you to execute additional commands before Windows restarts.</span><span class="sxs-lookup"><span data-stu-id="89cd7-350">The <b>/noreboot</b> option enables you to execute additional commands before Windows restarts.</span></span> <span data-ttu-id="89cd7-351">This option suppresses only the first reboot.</span><span class="sxs-lookup"><span data-stu-id="89cd7-351">This option suppresses only the first reboot.</span></span> <span data-ttu-id="89cd7-352">The option does not suppress subsequent reboots.</span><span class="sxs-lookup"><span data-stu-id="89cd7-352">The option does not suppress subsequent reboots.</span></span> <span data-ttu-id="89cd7-353">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-353">For example:</span></span><br /><span data-ttu-id="89cd7-354">
<font face="courier" color="red">Setup /noreboot</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-354">
<font face="courier" color="red">Setup /noreboot</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-355"><span id="19"></span><b>/PKey</b><i>&lt;product key&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-355"><span id="19"></span><b>/PKey</b><i>&lt;product key&gt;</i></span></span></p></td>
<td><p> <span data-ttu-id="89cd7-356">Supplies Setup with the specific product key.</span><span class="sxs-lookup"><span data-stu-id="89cd7-356">Supplies Setup with the specific product key.</span></span> <span data-ttu-id="89cd7-357">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-357">Example:</span></span><br /><span data-ttu-id="89cd7-358">
<font face="courier" color="red">setup.exe /auto upgrade /pkey xxxxx-xxxxx-xxxxx-xxxxx-xxxxx</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-358">
<font face="courier" color="red">setup.exe /auto upgrade /pkey xxxxx-xxxxx-xxxxx-xxxxx-xxxxx</font></span></span><br />
<span data-ttu-id="89cd7-359">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-359">This setting is new for Windows 10.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-360"><span id="35"></span><b>/Priority Normal</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-360"><span id="35"></span><b>/Priority Normal</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-361">Tells Windows Setup to increase the thread priority from low to high for feature updates through Windows Update.</span><span class="sxs-lookup"><span data-stu-id="89cd7-361">Tells Windows Setup to increase the thread priority from low to high for feature updates through Windows Update.</span></span> <span data-ttu-id="89cd7-362">This option is available in Windows 10, version 1709 and later <b>Note</b>: Media based installations already run at normal priority.</span><span class="sxs-lookup"><span data-stu-id="89cd7-362">This option is available in Windows 10, version 1709 and later <b>Note</b>: Media based installations already run at normal priority.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-363"><span id="20"></span><b>/PostOOBE</b><i>&lt;location&gt;</i> [<b>\setupcomplete.cmd</b>]</span><span class="sxs-lookup"><span data-stu-id="89cd7-363"><span id="20"></span><b>/PostOOBE</b><i>&lt;location&gt;</i> [<b>\setupcomplete.cmd</b>]</span></span></p></td>
<td><p><span data-ttu-id="89cd7-364">After Setup is complete, run a script.</span><span class="sxs-lookup"><span data-stu-id="89cd7-364">After Setup is complete, run a script.</span></span><br />
<span data-ttu-id="89cd7-365">Accepted parameters are a local file path or UNC network path to a file named setupcomplete.cmd or to a folder that contains setupcomplete.cmd.</span><span class="sxs-lookup"><span data-stu-id="89cd7-365">Accepted parameters are a local file path or UNC network path to a file named setupcomplete.cmd or to a folder that contains setupcomplete.cmd.</span></span><br /><span data-ttu-id="89cd7-366">
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam\setupcomplete.cmd</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-366">
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam\setupcomplete.cmd</font></span></span><br />
<span data-ttu-id="89cd7-367">Path to folder that contains a script with the name: <b>setupcomplete.cmd</b>: Copies setupcomplete.cmd to $Windows.~BT to be run after OOBE.</span><span class="sxs-lookup"><span data-stu-id="89cd7-367">Path to folder that contains a script with the name: <b>setupcomplete.cmd</b>: Copies setupcomplete.cmd to $Windows.~BT to be run after OOBE.</span></span><br /><span data-ttu-id="89cd7-368">
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-368">
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam</font></span></span><br />
<span data-ttu-id="89cd7-369">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-369">This setting is new for Windows 10.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-370"><span id="21"></span><b>/PostRollback</b><i>&lt;location&gt;</i> [<b>\setuprollback.cmd</b>] [<b>/postrollbackcontext {system / user}]</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-370"><span id="21"></span><b>/PostRollback</b><i>&lt;location&gt;</i> [<b>\setuprollback.cmd</b>] [<b>/postrollbackcontext {system / user}]</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-371">If the feature update fails to install and rolls back the changes, or if the user chooses to uninstall the feature update and go back to a previous version of Windows, run a script.</span><span class="sxs-lookup"><span data-stu-id="89cd7-371">If the feature update fails to install and rolls back the changes, or if the user chooses to uninstall the feature update and go back to a previous version of Windows, run a script.</span></span><br />
<span data-ttu-id="89cd7-372">Accepted parameters are a local file path or UNC network path to a file named setuprollback.cmd, or to a folder that contains setuprollback.cmd.</span><span class="sxs-lookup"><span data-stu-id="89cd7-372">Accepted parameters are a local file path or UNC network path to a file named setuprollback.cmd, or to a folder that contains setuprollback.cmd.</span></span><br />
<span data-ttu-id="89cd7-373">By default, updates from media run <font face="courier" color="red">setuprollback.cmd</font> in <b>user</b> context, which requires the first user who logs in post-upgrade to have administrator rights.</span><span class="sxs-lookup"><span data-stu-id="89cd7-373">By default, updates from media run <font face="courier" color="red">setuprollback.cmd</font> in <b>user</b> context, which requires the first user who logs in post-upgrade to have administrator rights.</span></span> <span data-ttu-id="89cd7-374">For updates from Windows Update, <font face="courier" color="red">setuprollback.cmd</font> runs in <b>system</b> context, regardless of the rights of the first logged-in user.</span><span class="sxs-lookup"><span data-stu-id="89cd7-374">For updates from Windows Update, <font face="courier" color="red">setuprollback.cmd</font> runs in <b>system</b> context, regardless of the rights of the first logged-in user.</span></span>  <span data-ttu-id="89cd7-375">The <b>postrollbackcontext</b> option allows you to specify whether the script runs in the context of the System account or the account of the signed in user.</span><span class="sxs-lookup"><span data-stu-id="89cd7-375">The <b>postrollbackcontext</b> option allows you to specify whether the script runs in the context of the System account or the account of the signed in user.</span></span><br /><span data-ttu-id="89cd7-376">
<font face="courier" color="red">setup.exe /auto upgrade /postrollback c:\Fabrikam\setuprollback.cmd</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-376">
<font face="courier" color="red">setup.exe /auto upgrade /postrollback c:\Fabrikam\setuprollback.cmd</font></span></span><br />
<span data-ttu-id="89cd7-377">Path to folder that contains a script with the name: <b>setuprollback.cmd</b>: Copies setuprollback.cmd to $Windows.~BT to be run after OOBE.</span><span class="sxs-lookup"><span data-stu-id="89cd7-377">Path to folder that contains a script with the name: <b>setuprollback.cmd</b>: Copies setuprollback.cmd to $Windows.~BT to be run after OOBE.</span></span><br /><span data-ttu-id="89cd7-378">
<font face="courier" color="red">setup.exe /auto upgrade /postrollback \server\share</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-378">
<font face="courier" color="red">setup.exe /auto upgrade /postrollback \server\share</font></span></span><br /><span data-ttu-id="89cd7-379">
<font face="courier" color="red">setup.exe /postrollback C:\Fabrikamsetuprollback.cmd /postrollbackcontext user</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-379">
<font face="courier" color="red">setup.exe /postrollback C:\Fabrikamsetuprollback.cmd /postrollbackcontext user</font></span></span><br /><span data-ttu-id="89cd7-380">
<font face="courier" color="red">/postrollbackcontext</font> is new for Windows 10, version 1803.</span><span class="sxs-lookup"><span data-stu-id="89cd7-380">
<font face="courier" color="red">/postrollbackcontext</font> is new for Windows 10, version 1803.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-381"><span id="22"></span><b>/Quiet</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-381"><span id="22"></span><b>/Quiet</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-382">This will suppress any Setup user experience including the rollback user experience.</span><span class="sxs-lookup"><span data-stu-id="89cd7-382">This will suppress any Setup user experience including the rollback user experience.</span></span> <span data-ttu-id="89cd7-383">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-383">Example:</span></span><br /><span data-ttu-id="89cd7-384">
<font face="courier" color="red">setup /auto upgrade /quiet</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-384">
<font face="courier" color="red">setup /auto upgrade /quiet</font></span></span><br />
<span data-ttu-id="89cd7-385">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-385">This setting is new for Windows 10.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-386"><span id="23"></span><b>/ReflectDrivers</b><i>&lt;location&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-386"><span id="23"></span><b>/ReflectDrivers</b><i>&lt;location&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-387">Specifies the path to a folder that contains encryption drivers for a computer that has third-party encryption enabled.</span><span class="sxs-lookup"><span data-stu-id="89cd7-387">Specifies the path to a folder that contains encryption drivers for a computer that has third-party encryption enabled.</span></span><br /><span data-ttu-id="89cd7-388">
<font face="courier" color="red">Setup /ReflectDrivers <folder_path></font></span><span class="sxs-lookup"><span data-stu-id="89cd7-388">
<font face="courier" color="red">Setup /ReflectDrivers <folder_path></font></span></span><br />
<span data-ttu-id="89cd7-389">This setting is new for Windows 10, version 1607.</span><span class="sxs-lookup"><span data-stu-id="89cd7-389">This setting is new for Windows 10, version 1607.</span></span><br />
<span data-ttu-id="89cd7-390">Make sure that <i>&lt;folder_path&gt;</i> contains only a minimal set of encryption drivers.</span><span class="sxs-lookup"><span data-stu-id="89cd7-390">Make sure that <i>&lt;folder_path&gt;</i> contains only a minimal set of encryption drivers.</span></span> <span data-ttu-id="89cd7-391">Having more drivers than necessary in <i>&lt;folder_path&gt;</i> can negatively impact upgrade scenarios.</span><span class="sxs-lookup"><span data-stu-id="89cd7-391">Having more drivers than necessary in <i>&lt;folder_path&gt;</i> can negatively impact upgrade scenarios.</span></span> </p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-392"><span id="24"></span><b>/ResizeRecoveryPartition</b> {<b>Enable</b> / <b>Disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-392"><span id="24"></span><b>/ResizeRecoveryPartition</b> {<b>Enable</b> / <b>Disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-393">Specifies whether it's OK to resize the existing Windows Recovery Environment (Windows RE) partition or create a new one during installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-393">Specifies whether it's OK to resize the existing Windows Recovery Environment (Windows RE) partition or create a new one during installation.</span></span><br /><span data-ttu-id="89cd7-394">
<b>Enable</b>: During installation, Windows can resize the existing Windows RE tools partition or create a new one if needed.</span><span class="sxs-lookup"><span data-stu-id="89cd7-394">
<b>Enable</b>: During installation, Windows can resize the existing Windows RE tools partition or create a new one if needed.</span></span><br /><span data-ttu-id="89cd7-395">
<b>Disable</b>: Windows does not resize the existing Windows RE tools partition or create a new one during installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-395">
<b>Disable</b>: Windows does not resize the existing Windows RE tools partition or create a new one during installation.</span></span><br />
<span data-ttu-id="89cd7-396">To learn more about Windows RE partitions, see <a href="configure-uefigpt-based-hard-drive-partitions.md">UEFI/GPT-based hard drive partitions</a> and <a href="configure-biosmbr-based-hard-drive-partitions.md">BIOS/MBR-based hard drive partitions</a>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-396">To learn more about Windows RE partitions, see <a href="configure-uefigpt-based-hard-drive-partitions.md">UEFI/GPT-based hard drive partitions</a> and <a href="configure-biosmbr-based-hard-drive-partitions.md">BIOS/MBR-based hard drive partitions</a>.</span></span><br /><span data-ttu-id="89cd7-397">
<font face="courier" color="red">Setup /resizerecoverypartition disable</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-397">
<font face="courier" color="red">Setup /resizerecoverypartition disable</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-398"><span id="25"></span><b>/ShowOOBE</b> {<b>full</b> / <b>none</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-398"><span id="25"></span><b>/ShowOOBE</b> {<b>full</b> / <b>none</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-399"><b>full</b>: Requires the user to interactively complete the out of box experience (OOBE).</span><span class="sxs-lookup"><span data-stu-id="89cd7-399"><b>full</b>: Requires the user to interactively complete the out of box experience (OOBE).</span></span><br /><span data-ttu-id="89cd7-400">
<b>none</b>: Skips OOBE and selects the default settings.</span><span class="sxs-lookup"><span data-stu-id="89cd7-400">
<b>none</b>: Skips OOBE and selects the default settings.</span></span><br />
<span data-ttu-id="89cd7-401">Example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-401">Example:</span></span><br /><span data-ttu-id="89cd7-402">
<font face="courier" color="red">setup.exe /auto upgrade /showoobe full</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-402">
<font face="courier" color="red">setup.exe /auto upgrade /showoobe full</font></span></span><br />
<span data-ttu-id="89cd7-403">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-403">This setting is new for Windows 10.</span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-404"><span id="26"></span><b>/Telemetry</b> {<b>Enable</b> / <b>Disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-404"><span id="26"></span><b>/Telemetry</b> {<b>Enable</b> / <b>Disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-405">Specifies whether Windows Setup should capture and report installation data.</span><span class="sxs-lookup"><span data-stu-id="89cd7-405">Specifies whether Windows Setup should capture and report installation data.</span></span><br /><span data-ttu-id="89cd7-406">
<b>Enable</b>: Setup captures and reports installation data.</span><span class="sxs-lookup"><span data-stu-id="89cd7-406">
<b>Enable</b>: Setup captures and reports installation data.</span></span><br /><span data-ttu-id="89cd7-407">
<b>Disable</b>: Setup does not capture and report installation data.</span><span class="sxs-lookup"><span data-stu-id="89cd7-407">
<b>Disable</b>: Setup does not capture and report installation data.</span></span><br /><span data-ttu-id="89cd7-408">
<font face="courier" color="red">Setup /telemetry disable</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-408">
<font face="courier" color="red">Setup /telemetry disable</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-409"><span id="27"></span><b>/TempDrive</b> <i>&lt;drive_letter&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-409"><span id="27"></span><b>/TempDrive</b> <i>&lt;drive_letter&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-410">Instructs Windows Setup to put temporary installation files on the specified partition.</span><span class="sxs-lookup"><span data-stu-id="89cd7-410">Instructs Windows Setup to put temporary installation files on the specified partition.</span></span> <span data-ttu-id="89cd7-411">For an upgrade, the <b>/tempdrive</b> option affects only the placement of temporary files.</span><span class="sxs-lookup"><span data-stu-id="89cd7-411">For an upgrade, the <b>/tempdrive</b> option affects only the placement of temporary files.</span></span> <span data-ttu-id="89cd7-412">The operating system is upgraded in the partition from which you run the Setup.exe file.</span><span class="sxs-lookup"><span data-stu-id="89cd7-412">The operating system is upgraded in the partition from which you run the Setup.exe file.</span></span><br />
<span data-ttu-id="89cd7-413">The <b>/tempdrive</b> parameter is available in Windows 10, version 1607, but it is not available in earlier versions of Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-413">The <b>/tempdrive</b> parameter is available in Windows 10, version 1607, but it is not available in earlier versions of Windows 10.</span></span><br /><span data-ttu-id="89cd7-414">
<i>&lt;drive_letter&gt;</i> specifies the partition to copy installation files to during Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-414">
<i>&lt;drive_letter&gt;</i> specifies the partition to copy installation files to during Windows Setup.</span></span> <span data-ttu-id="89cd7-415">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-415">For example:</span></span><br /><span data-ttu-id="89cd7-416">
<font face="courier" color="red">Setup /tempdrive H</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-416">
<font face="courier" color="red">Setup /tempdrive H</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-417"><span id="28"></span><b>/Unattend</b>:<i>&lt;answer_file&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-417"><span id="28"></span><b>/Unattend</b>:<i>&lt;answer_file&gt;</i></span></span></p></td>
<td><p> <span data-ttu-id="89cd7-418">Enables you to use an answer file with Windows Setup.</span><span class="sxs-lookup"><span data-stu-id="89cd7-418">Enables you to use an answer file with Windows Setup.</span></span> <span data-ttu-id="89cd7-419">This is known as an unattended installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-419">This is known as an unattended installation.</span></span> <span data-ttu-id="89cd7-420">You must specify a value for <i>&lt;answer_file&gt;</i>.</span><span class="sxs-lookup"><span data-stu-id="89cd7-420">You must specify a value for <i>&lt;answer_file&gt;</i>.</span></span> <span data-ttu-id="89cd7-421">Windows Setup applies the values in the answer file during installation.</span><span class="sxs-lookup"><span data-stu-id="89cd7-421">Windows Setup applies the values in the answer file during installation.</span></span><br /><span data-ttu-id="89cd7-422">
<i>&lt;answer_file&gt;</i> specifies the file path and file name of the unattended Windows Setup answer file.</span><span class="sxs-lookup"><span data-stu-id="89cd7-422">
<i>&lt;answer_file&gt;</i> specifies the file path and file name of the unattended Windows Setup answer file.</span></span><br /><span data-ttu-id="89cd7-423">
<font face="courier" color="red">When /Unattend is used, /Auto cannot be used.</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-423">
<font face="courier" color="red">When /Unattend is used, /Auto cannot be used.</font></span></span><br /><span data-ttu-id="89cd7-424">
<font face="courier" color="red">Setup /unattend:\server\share\unattend.xml</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-424">
<font face="courier" color="red">Setup /unattend:\server\share\unattend.xml</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-425"><span id="29"></span><b>/Uninstall</b> {<b>enable</b> / <b>disable</b>}</span><span class="sxs-lookup"><span data-stu-id="89cd7-425"><span id="29"></span><b>/Uninstall</b> {<b>enable</b> / <b>disable</b>}</span></span></p></td>
<td><p><span data-ttu-id="89cd7-426">Determines whether Windows will include controls that allow the user to go back to the previous operating system.</span><span class="sxs-lookup"><span data-stu-id="89cd7-426">Determines whether Windows will include controls that allow the user to go back to the previous operating system.</span></span><br />
<span data-ttu-id="89cd7-427">This setting is new for Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89cd7-427">This setting is new for Windows 10.</span></span><br /><span data-ttu-id="89cd7-428">
<font face="courier" color="red">Setup /uninstall disable</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-428">
<font face="courier" color="red">Setup /uninstall disable</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-429"><span id="30"></span><b>/USBDebug</b>:<i>&lt;hostname&gt;</i> </span><span class="sxs-lookup"><span data-stu-id="89cd7-429"><span id="30"></span><b>/USBDebug</b>:<i>&lt;hostname&gt;</i> </span></span></p></td>
<td><p><span data-ttu-id="89cd7-430">Sets up debugging on a USB port.</span><span class="sxs-lookup"><span data-stu-id="89cd7-430">Sets up debugging on a USB port.</span></span> <span data-ttu-id="89cd7-431">Debug data is effective on the next reboot.</span><span class="sxs-lookup"><span data-stu-id="89cd7-431">Debug data is effective on the next reboot.</span></span><br />
<span data-ttu-id="89cd7-432">&lt;hostname&gt; specifies the name of the computer to debug.</span><span class="sxs-lookup"><span data-stu-id="89cd7-432">&lt;hostname&gt; specifies the name of the computer to debug.</span></span> <span data-ttu-id="89cd7-433">For example:</span><span class="sxs-lookup"><span data-stu-id="89cd7-433">For example:</span></span><br /><span data-ttu-id="89cd7-434">
<font face="courier" color="red">Setup /usbdebug:testmachine01</font> </span><span class="sxs-lookup"><span data-stu-id="89cd7-434">
<font face="courier" color="red">Setup /usbdebug:testmachine01</font> </span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-435"><span id="31"></span><b>/WDSDiscover</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-435"><span id="31"></span><b>/WDSDiscover</b></span></span></p></td>
<td><p><span data-ttu-id="89cd7-436">Specifies that the Windows Deployment Services (WDS) client should be in discover mode.</span><span class="sxs-lookup"><span data-stu-id="89cd7-436">Specifies that the Windows Deployment Services (WDS) client should be in discover mode.</span></span><br />
<span data-ttu-id="89cd7-437">If you do not specify <b>/wdsserver</b> with this option, WDS searches for a server.</span><span class="sxs-lookup"><span data-stu-id="89cd7-437">If you do not specify <b>/wdsserver</b> with this option, WDS searches for a server.</span></span> <span data-ttu-id="89cd7-438">For example, to start the WDS client in this dynamic discover mode, run the following command:</span><span class="sxs-lookup"><span data-stu-id="89cd7-438">For example, to start the WDS client in this dynamic discover mode, run the following command:</span></span><br /><span data-ttu-id="89cd7-439">
<font face="courier" color="red">Setup /wds /wdsdiscover</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-439">
<font face="courier" color="red">Setup /wds /wdsdiscover</font></span></span></p></td>
</tr>
<tr>
<td><p><span data-ttu-id="89cd7-440"><span id="32"></span><b>/WDSServer</b>:<i>&lt;servername&gt;</i></span><span class="sxs-lookup"><span data-stu-id="89cd7-440"><span id="32"></span><b>/WDSServer</b>:<i>&lt;servername&gt;</i></span></span></p></td>
<td><p><span data-ttu-id="89cd7-441">Specifies the name of the Windows Deployment Services server that the client should connect to.</span><span class="sxs-lookup"><span data-stu-id="89cd7-441">Specifies the name of the Windows Deployment Services server that the client should connect to.</span></span><br />
<span data-ttu-id="89cd7-442">To use this setting, you must also use the <font face="courier" color="red">/wdsdiscover</font> option.</span><span class="sxs-lookup"><span data-stu-id="89cd7-442">To use this setting, you must also use the <font face="courier" color="red">/wdsdiscover</font> option.</span></span><br /><span data-ttu-id="89cd7-443">
<i>&lt;servername&gt;</i> can be an IP address, a NetBIOS name, or a fully qualified domain name (FQDN).</span><span class="sxs-lookup"><span data-stu-id="89cd7-443">
<i>&lt;servername&gt;</i> can be an IP address, a NetBIOS name, or a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="89cd7-444">For example, to start the Windows Deployment Services client in this static discover mode, run the following command:</span><span class="sxs-lookup"><span data-stu-id="89cd7-444">For example, to start the Windows Deployment Services client in this static discover mode, run the following command:</span></span><br /><span data-ttu-id="89cd7-445">
<font face="courier" color="red">Setup /wds /wdsdiscover /wdsserver:MyWDSServer</font></span><span class="sxs-lookup"><span data-stu-id="89cd7-445">
<font face="courier" color="red">Setup /wds /wdsdiscover /wdsserver:MyWDSServer</font></span></span></p></td>
</tr>
<tr>
</table>


<span data-ttu-id="89cd7-446"><span id="setup_exe_exit_codes"></span>**Setup.exe exit codes**</span><span class="sxs-lookup"><span data-stu-id="89cd7-446"><span id="setup_exe_exit_codes"></span>**Setup.exe exit codes**</span></span>

| <span data-ttu-id="89cd7-447">Exit code name</span><span class="sxs-lookup"><span data-stu-id="89cd7-447">Exit code name</span></span> | <span data-ttu-id="89cd7-448">Exit code</span><span class="sxs-lookup"><span data-stu-id="89cd7-448">Exit code</span></span> | <span data-ttu-id="89cd7-449">Cause</span><span class="sxs-lookup"><span data-stu-id="89cd7-449">Cause</span></span> |
| --- | --- | --- |
| <span data-ttu-id="89cd7-450">CONX_SETUP_EXITCODE_CONTINUE_REBOOT</span><span class="sxs-lookup"><span data-stu-id="89cd7-450">CONX_SETUP_EXITCODE_CONTINUE_REBOOT</span></span> | <span data-ttu-id="89cd7-451">0x3</span><span class="sxs-lookup"><span data-stu-id="89cd7-451">0x3</span></span> | <span data-ttu-id="89cd7-452">This upgrade was successful.</span><span class="sxs-lookup"><span data-stu-id="89cd7-452">This upgrade was successful.</span></span> |
| <span data-ttu-id="89cd7-453">CONX_SETUP_EXITCODE_RESUME_AT_COMPAT_REPORT</span><span class="sxs-lookup"><span data-stu-id="89cd7-453">CONX_SETUP_EXITCODE_RESUME_AT_COMPAT_REPORT</span></span> | <span data-ttu-id="89cd7-454">0x5</span><span class="sxs-lookup"><span data-stu-id="89cd7-454">0x5</span></span> | <span data-ttu-id="89cd7-455">The compatibility check detected issues that require resolution before the upgrade can continue.</span><span class="sxs-lookup"><span data-stu-id="89cd7-455">The compatibility check detected issues that require resolution before the upgrade can continue.</span></span> |
| <span data-ttu-id="89cd7-456">CONX_SETUP_EXITCODE_AUTO_INSTALL_FAIL</span><span class="sxs-lookup"><span data-stu-id="89cd7-456">CONX_SETUP_EXITCODE_AUTO_INSTALL_FAIL</span></span> | <span data-ttu-id="89cd7-457">0x7</span><span class="sxs-lookup"><span data-stu-id="89cd7-457">0x7</span></span> | <span data-ttu-id="89cd7-458">The installation option (upgrade or data only) was not available.</span><span class="sxs-lookup"><span data-stu-id="89cd7-458">The installation option (upgrade or data only) was not available.</span></span> |

<span data-ttu-id="89cd7-459"><b>Related topics</b></span><span class="sxs-lookup"><span data-stu-id="89cd7-459"><b>Related topics</b></span></span>

[<span data-ttu-id="89cd7-460">Windows Setup States</span><span class="sxs-lookup"><span data-stu-id="89cd7-460">Windows Setup States</span></span>](windows-setup-states.md)

[<span data-ttu-id="89cd7-461">Windows Setup Edition Configuration and Product ID Files (EI.cfg and PID.txt)</span><span class="sxs-lookup"><span data-stu-id="89cd7-461">Windows Setup Edition Configuration and Product ID Files (EI.cfg and PID.txt)</span></span>](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[<span data-ttu-id="89cd7-462">Windows Setup Log Files and Event Logs</span><span class="sxs-lookup"><span data-stu-id="89cd7-462">Windows Setup Log Files and Event Logs</span></span>](windows-setup-log-files-and-event-logs.md)
