---
title: When and how should I file a bug report?
ms.topic: article
ms.prod: xamarin
ms.assetid: 8AD9CFBF-282A-4C1F-95E9-25F21141B052
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
---

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