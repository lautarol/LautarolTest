---
title: Manual Test - Verify WLAN connectivity
description: Manual Test - Verify WLAN connectivity
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 56f1306a-98ab-408a-93fe-252ce134c36f


ms.date: 11/05/2018
ms.topic: article


---

# <span id="p_hlk_test.27e4579c-c427-417c-8707-035ba1111b48"></span>Manual Test - Verify WLAN connectivity


This is a manual test & it should be run outside HLK by following the manual instructions provided below. If this test is run as an automated test from HLK studio/controller, the test will pass by default without testing any functionality.

-----

Manual instructions to run this test: Make sure Settings-&gt;cellular-&gt;Data connection is turned off. 1. Ensure device MAC address is provisioned 2. Connect to an open network 3. Open up www.bing.com and search for "otters" 4. Verify search returns results 

-----

Note: This test is associated with an optional feature: System.Client.MobileHardware. It will not appear in the list of tests in HLK studio for a system target by default. Optional: To enable it to show up in the list of tests for system target in HLK studio, run the following steps: 1\] In HLK Studio, select system target 2\] Right click on the selected system target 3\] Click on Add\\Modify Features 4\] A Device Feature List window will open up 5\] Scroll down to select the feature named: System.Client.MobileHardware 6\] Click on the check box to enable this optional feature 7\] This test will now appear in the list of applicable tests for the selected system target in HLK studio

## Test details

|||
|---|---|
| **Specifications**  | <ul><li>System.Client.MobileHardware.BasicFunctionality</li></ul> |  
| **Platforms**   | <ul><li>Windows 10, mobile edition (ARM)</li></ul> |
| **Supported Releases** | <ul><li>Windows 10</li><li>Windows 10, version 1511</li><li>Windows 10, version 1607</li><li>Windows 10, version 1703</li><li>Windows 10, version 1709</li><li>Windows 10, version 1803</li><li>Next update to Windows 10</li></ul> |
|**Expected run time (in minutes)**| 10 |
|**Category**| Development |
|**Timeout (in minutes)**| 15 |
|**Requires reboot**| false |
|**Requires special configuration**| false |
|**Type**| manual |



## <span id="Additional_documentation"></span><span id="additional_documentation"></span><span id="ADDITIONAL_DOCUMENTATION"></span>Additional documentation


Tests in this feature area might have additional documentation, including prerequisites, setup, and troubleshooting information, that can be found in the following topic(s):

-   [System.Client additional documentation](system-client-additional-documentation.md)

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


For generic troubleshooting of HLK test failures, see [Troubleshooting Windows HLK Test Failures](../user/troubleshooting-windows-hlk-test-failures.md).









