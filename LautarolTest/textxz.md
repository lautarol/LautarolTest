---

Description: 'Windows Setup Command-Line Options'
ms.assetid: 16001d04-db9f-4953-abc7-37903ef47fd1
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'Windows Setup Command-Line Options'

ms.date: 05/02/2017
ms.topic: article
---

# Windows Setup Command-Line Options


The following command-line options are available for Windows Setup. Beginning with Windows 10, version 1607, you can use a setupconfig file as an alternative to passing paramters to Windows Setup on a command line. For more information, see [Windows Setup Automation Overview](windows-setup-automation-overview.md).

<b>setup.exe</b> 

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

The following table lists Setup command-line options:

<table>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><p><span id="1"></span><b>/1394Debug:</b><i>&lt;channel&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate&gt;</i>]</p></td>
<td><p>Enables kernel debugging over an IEEE 1394 (FireWire) port while Windows is running and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.<br />
&lt;channel&gt; specifies the debugging channel. The default value for <b>&lt;channel&gt;</b> is <b>1</b>.<br />
[<b>baudrate:</b><i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging. The default setting is <b>19200</b>. You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>. For example:<br />  

<font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></p></td>

</tr>
<tr>
<td><p><span id="2"></span><b>/AddBootMgrLast</b></font></p></td>
<td><p>Instructs Windows Setup to add the Windows Boot Manager as the last entry in the UEFI firmware boot order. This option is only supported on UEFI PCs running Windows PE 4.0 or later.</p></td>
</tr>
<tr>
<td><p><span id="3"></span><b>/Auto</b> <b>{Clean | DataOnly | Upgrade}</font></p></td>
<td><p>Performs an automated upgrade to Windows 10 or Windows 8.1 volume license editions only.<br />
When /auto is used, an unattend file cannot be used.<br />
When /auto is used, Windows Setup consumes ei.cfg, and checks compatibility issues before starting the installation. If ei.cfg is malformed, setup exits silently and logs an exit code.<br />
<b>Clean</b>: Performs an clean install of Windows.<br />
<b>DataOnly</b>: Performs an upgrade of Windows, saving only data (and not apps.) If the data-only installation option is not available due to compatibility checks, Windows Setup will exit silently and log an exit code.<br />
<b>Upgrade</b>: Performs an upgrade of Windows saving apps and data. If the upgrade installation option is not available, or the user needs to resolve an app compatibility issue, Windows Setup will exit silently and log an exit code.<br />
<b>Setup.exe exit codes</b>: See <a href="#setup_exe_exit_codes">table below</a>.<br />
<b>/noautoexit</b>: Not used in Windows 10. In Windows 8.1, if an error is found, Windows Setup does not exit, but instead stops and stays on the setup screen until the user addresses the issue. The installation from that point on is attended.<br />
<b>/performDU</b>: Not used in Windows 10. In Windows 8.1, Windows Setup checks for Dynamic Updates for Windows Setup.<br />
Examples:<br />
<font face="courier" color="red">Setup /auto clean</font><br />
<font face="courier" color="red">Setup /auto dataonly</font><br />
<font face="courier" color="red">Setup /auto upgrade </font></p></td>
</tr>
<tr>
<td><p><span id="33"></span><b>/BitLocker<b> <b>{AlwaysSuspend | TryKeepActive | ForceKeepActive}</b></p></td>
<td><p>Specifies the BitLocker status during upgrades.<br />
<b>AlwaysSuspend</b>: BitLocker is always suspended during an upgrade. This is the default behavior if the <b>/bitlocker</b> option is not specified.<br />
<b>TryKeepActive</b>: Attempts an upgrade without suspending BitLocker. If the upgrade fails, Windows Setup will suspend BitLocker and complete the upgrade.<br />
<b>ForceKeepActive</b>: Enables upgrading without suspending BitLocker. If the upgrade can't be completed because BitLocker is active, the upgrade will fail. </p></td>
</tr>
<tr>
<td><p><span id="4"></span><b>/BusParams</b>:<i>&lt;bus.device.function&gt;</i></p></td>
<td><p>Specifies the PCI address of a 1394, USB, or NET debug port. The bus, device, and function numbers must be in decimal format. Example:<p><font face="courier" color="red">Setup /busparams:0.29.7 </font><p>For more info, see <a href="https://go.microsoft.com/fwlink/?LinkId=317360">Setting Up Kernel Debugging with USB 2.0</a>.</p></td>
</tr>
<tr>
<td><p><span id="5"></span><b>/CompactOS</b> {<b>Enable</b> / <b>Disable</b>}</p></td>
<td><p>Specifies whether to use the Compact OS feature to save hard drive space. By default, Windows Setup determines whether to use this feature automatically.<br />
<b>Enable</b>: Setup installs Windows using compressed system files.<br />
<b>Disable</b>: Setup installs Windows using uncompressed system files<br />
To learn more about Compact OS, see <a href="compact-os.md">Compact OS, single-instancing, and image optimization</a>.<br />
<font face="courier" color="red">Setup /compactos enable</font></p></td>
</tr>
<tr>
<td><p><span id="6"></span><b>/Compat</b> {<b>IgnoreWarning</b> / <b>ScanOnly</b>} </p></td>
<td><p><b>IgnoreWarning</b>: Setup completes installation, ignoring any dismissible compatibility messages.<br />
<b>ScanOnly</b>: Windows Setup runs through compatibility scans, and then exits (without completing the installation) with an exit code to indicate if any compatibility concerns are present. Setup will return 0xC1900210 if no concerns are found. Setup will return 0xC1900208 if compatibility concerns are found.<br />
Example:<br />
<font face="courier" color="red">Setup /compat IgnoreWarning</font><br />
If you launch Setup with <font face="courier" color="red">/Compat ScanOnly</font>:<br />
<ul><li>If it does not find any compat issue, it will return MOSETUP_E_COMPAT_SCANONLY (0xC1900210)</li>
<li>If it finds Actionable compat issues, like Apps, it will return MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)</li>
<li>If it finds that the Mig-Choice selected is not available, it will return MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)</li>
<li>If it finds that machine is not eligible for Windows 10, it will return MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)</li>
<li>If it finds that machine does not have enough free space to install, it will return MOSETUP_E_INSTALLDISKSPACE_BLOCK (0xC190020E)</li>
</ul>This command works with other switches. For example, to run Setup in the background without any UI:<br />
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly</font><br />
To ignore common disclaimers in the UI, for example, language changes:<br />
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning</font><br />
Most of the time, an Admin would like to look at the compat XML if Setup found compat issues. For that the admin can even use copy logs flag to collect Setup logs:<br />
<font face="courier" color="red">Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning /CopyLogs C:\Temp\Logfiles.log </font><br />
This setting is new for Windows 10.</p></td>
</tr>
<tr>
<td><p><span id="7"></span><b>/CopyLogs</b><i>&lt;location&gt;</i></p></td>
<td><p>Setup will copy or upload logs(compressed) upon failure to the specified location (assuming machine/user has permission and network access to location).<br />
Accepted parameters are local file paths and UNC network paths.<br />
Note: This runs in the system context, so it may not have permissions to copy to locations that require user permissions.<br />
Example:<br />
<font face="courier" color="red">Setup /copylogs \\server\share\</font></p></td>
</tr>
<tr>
<td><p><span id="8"></span><b>/Debug:</b><i>&lt;port&gt;</i> [<b>BaudRate:</b><i>&lt;baudrate></i>]</p></td>
<td><p>Enables kernel debugging over a communications (COM) port when Windows is running, and during the <a href="windowspe.md">windowsPE</a> configuration pass of Windows Setup.<br />
&lt;port&gt; specifies the debugging port. The default value for &lt;port&gt; is 1.<br />
[<b>baudrate</b>:&lt;baudrate&gt;] specifies the baud to use when Windows transfers data during debugging. The default setting is <b>19200</b>. You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>. For example:<br />
<font face="courier" color="red">Setup /1394debug:1 /baudrate:115200</font></p></td>
</tr>
<tr>
<td><p><span id="9"></span>/<b>DiagnosticPrompt</b> {<b>enable</b> | <b>disable</b>}</p></td>
<td><p>Specifies that the Command Prompt is available during Windows Setup.<br />
<b>Enable</b>: The Command Prompt can be accessed by pressing Shift+F10 during Windows setup.<br />
<b>Disable</b>: The Command Prompt is not available during Windows setup. The Command Prompt wil not be available while offline and OOBE phases are running. This is the default setting.<br>Example:<br />
<font face="courier" color="red">setup /DiagnosticPrompt enable</font><br />
This setting is new for Windows 10, Version 1703.</p></td>
</tr>
<tr>
<td><p><span id="10"></span><b>/DynamicUpdate</b> {<b>enable</b> | <b>disable</b>}</p></td>
<td><p>Specifies whether setup will perform Dynamic Update operations (search, download, and install updates). Example:<br />
<font face="courier" color="red">setup /auto upgrade /DynamicUpdate disable </font></p></td>
</tr>
<tr>
<td><p><span id="11"></span><b>/EMSPort</b>: {<b>COM1</b> | <b>COM2</b> | <b>off</b>} [<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>]</p></td>
<td><p>Enables or disables Emergency Management Services (EMS) during Windows Setup and after the server operating system has been installed. The following arguments are used to specify the behavior of EMS during Windows Setup.<br />
<b>COM1</b> enables EMS over COM1. Supported for x86 systems only.<br />
<b>COM2</b> enables EMS over COM2. Supported for x86 systems only.<br />
<b>usebiossettings</b> uses the setting that the BIOS specifies. For x86 systems, Windows uses the value from the Serial Port Console Redirection (SPCR) table. If no SPCR table or EFI console device path is specified in the BIOS, Windows disables <b>usebiossettings.usebiossettings</b><br />
<b>off</b> disables EMS. If EMS is disabled in Windows Setup, you can later enable EMS by modifying the boot settings.<br />
[<b>/emsbaudrate</b>:<i>&lt;baudrate&gt;</i>] specifies the baud to use when Windows transfers data during debugging. The default is <b>19200</b>. You can also set the &lt;baudrate&gt; setting to <b>57600</b> or <b>115200</b>. For example:<br />
<font face="courier" color="red">Setup /emsport:COM1 /emsbaudrate:115200</font></p></td>
</tr>
<tr>
<td><p><span id="12"></span><b>/InstallDrivers</b><i>&lt;location&gt;</i></p></td>
<td><p>Adds .inf-style drivers to the new Windows 10 installation. The driver .inf can be in a folder within the specified location. The command will recurse through the specified location.<br />
Accepted parameters are a local file path or UNC network path to a folder that contains .inf files. Example:<br />
<font face="courier" color="red">setup.exe /auto upgrade /installdrivers C:\Fabrikam\drivers /noreboot </font><br />
This setting is new for Windows 10.</p></td>
</tr>
<tr>
<td><p><span id="13"></span><b>/InstallFrom</b><i>&lt;path&gt;</i></p></td>
<td><p>Specifies a different Install.wim file to use during Windows Setup. This enables you to use a single preinstallation environment to install multiple versions of Windows images. For example, you can use a 32-bit version of Windows Setup to deploy a 64-bit Windows image. You can also use an answer file for cross-platform deployments. For more information, see “Creating a WIM for Multiple Architecture Types” in <a href="windows-setup-supported-platforms-and-cross-platform-deployments.md#creating_wimfile">Windows Setup Supported Platforms and Cross-Platform Deployments</a>.<br />
&lt;path&gt; specifies the path of the .wim file to install. For example:<br />
<font face="courier" color="red">Setup /installfrom D:\custom.wim</font><br />
Can also be used with split image files (.swm). Select the first split image file in the series, for example:<br />
<font face="courier" color="red">Setup /installfrom D:\install.swm</font></p></td>
</tr>
<tr>
<td><p><span id="14"></span><b>/InstallLangPacks</b><i>&lt;location&gt;</i></p></td>
<td><p>Adds language packs (lp.cab) to the new Windows 10 installation.<br />
The language packs can be in a folder within the specified location. The command installs all lp.cab files and language capabilities such as text-to-speech recognition, in the folder and subfolders at the specified location.<br />
Accepted parameters are a local file path or UNC network path to a folder that contains .inf files.<br />
<font face="courier" color="red">setup /auto upgrade /installlangpacks C:\Fabrikam\Languages\French /noreboot</font><br />
This setting is new for Windows 10. </p></td>
</tr>
<tr>
<td><p><span id="15"></span><b>/m</b>:<i>&lt;folder_name&gt;</i></p></td>
<td><p>Instructs Setup to copy alternate files from an alternate location. This option instructs Setup to look in the alternate location first, and, if files are present, to use them instead of the files from the default location.<br />
<i>&lt;folder_name&gt;</i> specifies the name and the location of the folder that contains the replacement files and can be any local drive location. UNC paths are not supported.<br />
You must know where the files will be installed on the Windows installation. All the additional files must be copied to an $OEM$ folder in your installation sources or in the <i>&lt;folder_name&gt;</i>. The $OEM$ structure provides a representation of the destination installation disk. For example:<br />
<font face="courier" color="red">$OEM$\$1</font><br />
maps to %SYSTEMDRIVE%, which could be drive C.<br />
<font face="courier" color="red">$OEM$\$$</font><br />
maps to %WINDIR%, which could be C:\windows.<br />
<font face="courier" color="red">$OEM$\$progs</font><br />
maps to the program files directory.<br />
<font face="courier" color="red">$OEM$\$docs</font><br />
maps to the user's My Documents folder.<br />
For example, to copy an updated C:\Program Files\Messenger\Msmsgs.exe file into the Windows installation, create the following folder structure on the Pro\Sources\$OEM$\$Progs\Messenger\Msmsgs.exe installation source by using the <b>Setup</b> command:<br />
<font face="courier" color="red">Pro\sources\setup.exe /m</font><br />
If you replace a file that Windows file protection protects, you must also copy the updated file to the local sources to be installed with Windows. For example, you may copy the file to the C:\Windows\i386 folder. The file name must be the same as the name that is used in Windows Setup. For example, add the following file and folder structure to your $OEM$ directory:<br />
<font face="courier" color="red">Pro\sources\$OEM$\$$\i386\msmsgs.ex_</font><br />
If you use files that are not on an installation share, you must specify the folder name. In this example the &lt;folder_name&gt; is C:\additional_files:<br />
<font face="courier" color="red">Setup /m:C:\additional_files</font><br />
where C:\additional_files is your customized $OEM$ directory. For example:<br />
<font face="courier" color="red">C:\additional_files\$$\i386\msmsgs.ex_</font><br />
If you change resources in your replacement files, you must add the updated Multilanguage User Interface (MUI) files to the installation. </p></td>
</tr>
<tr>
<td><p><span id="36"></span><b>/MigNEO Disable</b></p></td>
<td><p>Tells Windows Setup to perform an upgrade of Windows without additional offline phase optimizations. This option is available in Windows 10, version 1803 and later. </p></td>
</tr>
<tr>
<td><p><span id="16"></span><b>/MigrateDrivers</b> {<b>all</b> | <b>none</b>}</p></td>
<td><p> Instructs Setup whether to migrate the drivers from the existing installation during the upgrade. You can specify <b>All</b> or <b>None</b>. By default, Setup decides which is best for each individual driver based on the install choice.<br />
You can use this switch with <b>/installdrivers</b>, though it's not required.<br />
<font face="courier" color="red">Setup /auto upgrade /migratedrivers all</font><br />
<font face="courier" color="red">Setup /auto upgrade /migratedrivers none /installdrivers N:\NewDrivers</font></p></td>
</tr>
<tr>
<td><p><span id="17"></span><b>/NetDebug</b>:hostip=<i>&lt;w.x.y.z&gt;</i>,port=<i>&lt;n&gt;</i>,key= <i>&lt;q.r.s.t&gt;</i>[,nodhcp][,busparams=<i>n.o.p</i>]</p></td>
<td><p>Enables kernel debugging over the network.<br />
Use hostip to identify the IP address of the host computer.<br />
Use port to identify the port. The default start port is 49152, and the default end port is 65535.<br />
Use key to provide a password to set up a secure connection.<br />
Use nodhcp to avoid using a DHCP connection. (optional)<br />
Use busparams to select the bus number, device number, and function number of an adapter for a specific PCI bus device. (optional)<br />
Examples:<br />
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000,key=0.0.0.0</font><br />
<font face="courier" color="red">setup /netdebug:hostip=10.125.4.86,port=50000, key=abcdefg.123.hijklmnop.456,nodhcp</font><br />
<font face="courier" color="red">setup /netdebug:hostip=10.1.4.8,port=50000, key=dont.use.previous.keys,busparams=1.5.0</font><br />
For details, see <a href="https://go.microsoft.com/fwlink/p/?linkid=317384">Setting Up Kernel-Mode Debugging over a Network Cable Manually</a>.</p></td>
</tr>
<tr>
<td><p><span id="18"></span><b>/NoReboot</b></p></td>
<td><p>Instructs Windows Setup not to restart the computer after the down-level phase of Windows Setup completes. The <b>/noreboot</b> option enables you to execute additional commands before Windows restarts. This option suppresses only the first reboot. The option does not suppress subsequent reboots. For example:<br />
<font face="courier" color="red">Setup /noreboot</font></p></td>
</tr>
<tr>
<td><p><span id="19"></span><b>/PKey</b><i>&lt;product key&gt;</i></p></td>
<td><p> Supplies Setup with the specific product key. Example:<br />
<font face="courier" color="red">setup.exe /auto upgrade /pkey xxxxx-xxxxx-xxxxx-xxxxx-xxxxx</font><br />
This setting is new for Windows 10. </p></td>
</tr>
<tr>
<td><p><span id="35"></span><b>/Priority Normal</b></p></td>
<td><p>Tells Windows Setup to increase the thread priority from low to high for feature updates through Windows Update. This option is available in Windows 10, version 1709 and later <b>Note</b>: Media based installations already run at normal priority. </p></td>
</tr>
<tr>
<td><p><span id="20"></span><b>/PostOOBE</b><i>&lt;location&gt;</i> [<b>\setupcomplete.cmd</b>]</p></td>
<td><p>After Setup is complete, run a script.<br />
Accepted parameters are a local file path or UNC network path to a file named setupcomplete.cmd or to a folder that contains setupcomplete.cmd.<br />
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam\setupcomplete.cmd</font><br />
Path to folder that contains a script with the name: <b>setupcomplete.cmd</b>: Copies setupcomplete.cmd to $Windows.~BT to be run after OOBE.<br />
<font face="courier" color="red">setup.exe /auto upgrade /postoobe c:\Fabrikam</font><br />
This setting is new for Windows 10. </p></td>
</tr>
<tr>
<td><p><span id="21"></span><b>/PostRollback</b><i>&lt;location&gt;</i> [<b>\setuprollback.cmd</b>] [<b>/postrollbackcontext {system / user}]</b></p></td>
<td><p>If the feature update fails to install and rolls back the changes, or if the user chooses to uninstall the feature update and go back to a previous version of Windows, run a script.<br />
Accepted parameters are a local file path or UNC network path to a file named setuprollback.cmd, or to a folder that contains setuprollback.cmd.<br />
By default, updates from media run <font face="courier" color="red">setuprollback.cmd</font> in <b>user</b> context, which requires the first user who logs in post-upgrade to have administrator rights. For updates from Windows Update, <font face="courier" color="red">setuprollback.cmd</font> runs in <b>system</b> context, regardless of the rights of the first logged-in user.  The <b>postrollbackcontext</b> option allows you to specify whether the script runs in the context of the System account or the account of the signed in user.<br />
<font face="courier" color="red">setup.exe /auto upgrade /postrollback c:\Fabrikam\setuprollback.cmd</font><br />
Path to folder that contains a script with the name: <b>setuprollback.cmd</b>: Copies setuprollback.cmd to $Windows.~BT to be run after OOBE.<br />
<font face="courier" color="red">setup.exe /auto upgrade /postrollback \server\share</font><br />
<font face="courier" color="red">setup.exe /postrollback C:\Fabrikamsetuprollback.cmd /postrollbackcontext user</font><br />
<font face="courier" color="red">/postrollbackcontext</font> is new for Windows 10, version 1803. </p></td>
</tr>
<tr>
<td><p><span id="22"></span><b>/Quiet</b></p></td>
<td><p>This will suppress any Setup user experience including the rollback user experience. Example:<br />
<font face="courier" color="red">setup /auto upgrade /quiet</font><br />
This setting is new for Windows 10. </p></td>
</tr>
<tr>
<td><p><span id="23"></span><b>/ReflectDrivers</b><i>&lt;location&gt;</i></p></td>
<td><p>Specifies the path to a folder that contains encryption drivers for a computer that has third-party encryption enabled.<br />
<font face="courier" color="red">Setup /ReflectDrivers <folder_path></font><br />
This setting is new for Windows 10, version 1607.<br />
Make sure that <i>&lt;folder_path&gt;</i> contains only a minimal set of encryption drivers. Having more drivers than necessary in <i>&lt;folder_path&gt;</i> can negatively impact upgrade scenarios. </p></td>
</tr>
<tr>
<td><p><span id="24"></span><b>/ResizeRecoveryPartition</b> {<b>Enable</b> / <b>Disable</b>}</p></td>
<td><p>Specifies whether it's OK to resize the existing Windows Recovery Environment (Windows RE) partition or create a new one during installation.<br />
<b>Enable</b>: During installation, Windows can resize the existing Windows RE tools partition or create a new one if needed.<br />
<b>Disable</b>: Windows does not resize the existing Windows RE tools partition or create a new one during installation.<br />
To learn more about Windows RE partitions, see <a href="configure-uefigpt-based-hard-drive-partitions.md">UEFI/GPT-based hard drive partitions</a> and <a href="configure-biosmbr-based-hard-drive-partitions.md">BIOS/MBR-based hard drive partitions</a>.<br />
<font face="courier" color="red">Setup /resizerecoverypartition disable</font></p></td>
</tr>
<tr>
<td><p><span id="25"></span><b>/ShowOOBE</b> {<b>full</b> / <b>none</b>}</p></td>
<td><p><b>full</b>: Requires the user to interactively complete the out of box experience (OOBE).<br />
<b>none</b>: Skips OOBE and selects the default settings.<br />
Example:<br />
<font face="courier" color="red">setup.exe /auto upgrade /showoobe full</font><br />
This setting is new for Windows 10.</p></td>
</tr>
<tr>
<td><p><span id="26"></span><b>/Telemetry</b> {<b>Enable</b> / <b>Disable</b>}</p></td>
<td><p>Specifies whether Windows Setup should capture and report installation data.<br />
<b>Enable</b>: Setup captures and reports installation data.<br />
<b>Disable</b>: Setup does not capture and report installation data.<br />
<font face="courier" color="red">Setup /telemetry disable</font></p></td>
</tr>
<tr>
<td><p><span id="27"></span><b>/TempDrive</b> <i>&lt;drive_letter&gt;</i></p></td>
<td><p>Instructs Windows Setup to put temporary installation files on the specified partition. For an upgrade, the <b>/tempdrive</b> option affects only the placement of temporary files. The operating system is upgraded in the partition from which you run the Setup.exe file.<br />
The <b>/tempdrive</b> parameter is available in Windows 10, version 1607, but it is not available in earlier versions of Windows 10.<br />
<i>&lt;drive_letter&gt;</i> specifies the partition to copy installation files to during Windows Setup. For example:<br />
<font face="courier" color="red">Setup /tempdrive H</font></p></td>
</tr>
<tr>
<td><p><span id="28"></span><b>/Unattend</b>:<i>&lt;answer_file&gt;</i></p></td>
<td><p> Enables you to use an answer file with Windows Setup. This is known as an unattended installation. You must specify a value for <i>&lt;answer_file&gt;</i>. Windows Setup applies the values in the answer file during installation.<br />
<i>&lt;answer_file&gt;</i> specifies the file path and file name of the unattended Windows Setup answer file.<br />
<font face="courier" color="red">When /Unattend is used, /Auto cannot be used.</font><br />
<font face="courier" color="red">Setup /unattend:\server\share\unattend.xml</font></p></td>
</tr>
<tr>
<td><p><span id="29"></span><b>/Uninstall</b> {<b>enable</b> / <b>disable</b>}</p></td>
<td><p>Determines whether Windows will include controls that allow the user to go back to the previous operating system.<br />
This setting is new for Windows 10.<br />
<font face="courier" color="red">Setup /uninstall disable</font></p></td>
</tr>
<tr>
<td><p><span id="30"></span><b>/USBDebug</b>:<i>&lt;hostname&gt;</i> </p></td>
<td><p>Sets up debugging on a USB port. Debug data is effective on the next reboot.<br />
&lt;hostname&gt; specifies the name of the computer to debug. For example:<br />
<font face="courier" color="red">Setup /usbdebug:testmachine01</font> </p></td>
</tr>
<tr>
<td><p><span id="31"></span><b>/WDSDiscover</b></p></td>
<td><p>Specifies that the Windows Deployment Services (WDS) client should be in discover mode.<br />
If you do not specify <b>/wdsserver</b> with this option, WDS searches for a server. For example, to start the WDS client in this dynamic discover mode, run the following command:<br />
<font face="courier" color="red">Setup /wds /wdsdiscover</font></p></td>
</tr>
<tr>
<td><p><span id="32"></span><b>/WDSServer</b>:<i>&lt;servername&gt;</i></p></td>
<td><p>Specifies the name of the Windows Deployment Services server that the client should connect to.<br />
To use this setting, you must also use the <font face="courier" color="red">/wdsdiscover</font> option.<br />
<i>&lt;servername&gt;</i> can be an IP address, a NetBIOS name, or a fully qualified domain name (FQDN). For example, to start the Windows Deployment Services client in this static discover mode, run the following command:<br />
<font face="courier" color="red">Setup /wds /wdsdiscover /wdsserver:MyWDSServer</font></p></td>
</tr>
<tr>
</table>


<span id="setup_exe_exit_codes"></span>**Setup.exe exit codes**

| Exit code name | Exit code | Cause |
| --- | --- | --- |
| CONX_SETUP_EXITCODE_CONTINUE_REBOOT | 0x3 | This upgrade was successful. |
| CONX_SETUP_EXITCODE_RESUME_AT_COMPAT_REPORT | 0x5 | The compatibility check detected issues that require resolution before the upgrade can continue. |
| CONX_SETUP_EXITCODE_AUTO_INSTALL_FAIL | 0x7 | The installation option (upgrade or data only) was not available. |

<b>Related topics</b>

[Windows Setup States](windows-setup-states.md)

[Windows Setup Edition Configuration and Product ID Files (EI.cfg and PID.txt)](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[Windows Setup Log Files and Event Logs](windows-setup-log-files-and-event-logs.md)
