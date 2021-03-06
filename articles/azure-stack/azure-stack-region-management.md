---
title: Region management in Azure Stack | Microsoft Docs
description: Overview of region management in Azure Stack.
services: azure-stack
documentationcenter: 
author: efemmano
manager: dsavage
editor: 
ms.assetid: e94775d5-d473-4c03-9f4e-ae2eada67c6c
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/26/2017
ms.author: efemmano
ms.translationtype: HT
ms.sourcegitcommit: 349fe8129b0f98b3ed43da5114b9d8882989c3b2
ms.openlocfilehash: 15a3bc9dce3cc76f98816ba5c88066fdc23cdbe1
ms.contentlocale: zh-cn
ms.lasthandoff: 07/26/2017

---
# <a name="region-management-in-azure-stack"></a>Region management in Azure Stack
Azure Stack has the concept of regions, which are logical entities comprised of the hardware resources that make up the Azure Stack infrastructure. Inside Region management, you can find all resources that are required to successfully operate the Azure Stack infrastructure lifecycle.

The Azure Stack Development Kit is a single-node deployment, and equals one region. If you set up another instance of the Azure Stack Development Kit on separate hardware, this instance is a different region.

## <a name="information-available-through-the-region-management-tile"></a>Information available through the Region Management tile
Azure Stack has a set of region management capabilities available in the **Region management** tile. This tile is available to a cloud administrator on the default dashboard in the administrator portal. Through this tile, you can monitor and update your Azure Stack region and its components, which are region-specific.

 ![The region management tile](media/azure-stack-manage-region/image1.png)

 If you click a region in the Region management tile, you can access the following information:

  ![Description of panes on the Region management blade](media/azure-stack-manage-region/image2.png)

1. **The resource menu**. Here, you can access specific infrastructure management areas, and view and manage tenant resources such as storage accounts and virtual networks.

2. **Alerts**. This tile lists system-wide alerts and provides details on each of those alerts.

3. **Updates**. In this tile, you can view the current version of your Azure Stack infrastructure.

4. **Resource providers**. Resource providers is the place to manage the tenant functionality offered by the components required to run Azure Stack. Each resource provider comes with an administrative experience. This experience can include alerts for the specific provider, metrics, and other management capabilities specific to the resource provider.
 
5. **Infrastructure roles**. Infrastructure roles are the components necessary to run Azure Stack. Only the infrastructure roles that report alerts are listed. By clicking a role, you can view the alerts associated with the specific role and the role instances where this role is running. Although there is the capability to start, restart, or shut down an infrastructure role instance, do **not** do this in a development kit environment. These options are designed only for a multi-node environment, where there is more than one role instance per infrastructure role. Restarting a role instance (especially AzS-Xrp01) in the development kit causes system instability.

## <a name="next-steps"></a>Next steps
[Monitor health and alerts in Azure Stack](azure-stack-monitor-health.md)

[Manage updates in Azure Stack](azure-stack-updates.md)







