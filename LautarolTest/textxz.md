<properties
pageTitle="NvaDiagnostic"
description="NvaDiagnostic"
infoBubbleText="检测到网络流量路由有问题。 请参阅右侧的详细信息。"
service="microsoft.network"
resource="virtualnetworks"
authors="chadmath"
ms.author="chadmat"
displayOrder=""
articleId="NvaDiagnosticsInsight"
diagnosticScenario="NvaDiagnosticsInsight"
selfHelpType="Diagnostics"
supportTopicIds="32584252, 32584251, 32584250, 32584249, 32547215"
resourceTags="windows"
productPesIds="15526"
cloudEnvironments="Public"
/>
# <a name="we-found-an-issue-related-to-a-network-virtual-appliance-used-in-this-connectivity-path"></a>我们发现了一个与此连接路径中使用的网络虚拟设备相关的问题 
<!--issueDescription--> 我们评估了从源 VM **'[SourceVM]'** 到 IP 为 **[DestinationIP]** 的目标资源的路由，发现有一个名为 **'[NvaVmName]'** 的用于管理流量的网络虚拟设备 (NVA)。 我们在检测的方案上运行了一些诊断，有了以下发现： 

- 检查了源虚拟运行状况：**<!--$SourceVmHealthStatus-->[SourceVmHealthStatus]<!--/$SourceVmHealthStatus-->** 
- 检查了网络虚拟设备运行状况：**<!--$NvaHealthStatus-->[NvaHealthStatus]<!--/$NvaHealthStatus-->**
- 检查了目标 VM 运行状况（如果适用）：**<!--$DestVmHealthStatus-->[DestVmHealthStatus]<!--/$DestVmHealthStatus-->**
- 检查了 NVA 上的 IP 转发：**<!--$IpFwdStatus-->[IpFwdStatus]<!--/$IpFwdStatus-->**
- 检查是否存在阻止流量从源发往 NVA 的网络安全组 (NSG)：**<!--$SourceToNvaNsgStatus-->[SourceToNvaNsgStatus]<!--/$SourceToNvaNsgStatus-->** 
- 检查是否存在阻止流量从目标 IP (**<!--$DestinationIP-->[DestinationIP]<!--/$DestinationIP-->**) 发往源 **<!--$DestinationToSourceNsgStatus-->[DestinationToSourceNsgStatus]<!--/$DestinationToSourceNsgStatus-->** 的网络安全组 (NSG) <br><br>
请参阅下面的内容，了解解决检测到的问题的详细步骤。
<!--/issueDescription-->
## <a name="steps-to-resolve-detected-issues"></a>解决检测到的问题的步骤：
<!--$ResolutionSteps-->[ResolutionSteps]<!--/$ResolutionSteps-->
