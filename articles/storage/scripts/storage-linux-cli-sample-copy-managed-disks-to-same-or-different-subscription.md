---
title: "Azure CLI 脚本示例 - 将托管磁盘复制（移动）到相同或不同订阅 | Microsoft Docs"
description: "Azure CLI 脚本示例 - 将托管磁盘复制（移动）到相同或不同订阅"
services: virtual-machines-linux
documentationcenter: storage
author: ramankumarlive
manager: kavithag
editor: tysonn
tags: azure-service-management
ms.assetid: 
ms.service: virtual-machines-linux
ms.devlang: azurecli
ms.topic: sample
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 05/19/2017
ms.author: ramankum
ms.translationtype: Human Translation
ms.sourcegitcommit: be747170a0d8a7a6defd790a3f8a122c4d397671
ms.openlocfilehash: 90228d66150cf961557b6dbeed11308932677d83
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017

---

# <a name="copy-managed-disks-to-same-or-different-subscription-with-cli"></a>使用 CLI 将托管磁盘复制（移动）到相同或不同订阅

此脚本会将托管磁盘复制到相同订阅或相同区域中的不同订阅。 


[!INCLUDE [sample-cli-install](../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>示例脚本

[!code-azurecli[main](../../../cli_scripts/storage/copy-managed-disks-to-same-or-different-subscription/copy-managed-disks-to-same-or-different-subscription.sh "复制托管磁盘")]


## <a name="script-explanation"></a>脚本说明

此脚本使用以下命令并使用源托管磁盘的 Id 在目标订阅中创建新托管磁盘。 表中的每条命令均链接到特定于命令的文档。

| 命令 | 说明 |
|---|---|
| [az disk show](https://docs.microsoft.com/cli/azure/disk#show) | 使用托管磁盘的名称和资源组属性获取托管磁盘的所有属性。 Id 属性用于将托管磁盘复制到其他订阅。  |
| [az disk create](https://docs.microsoft.com/cli/azure/disk#create) | 使用父托管磁盘的 ID 和名称在其他订阅中新建托管磁盘，从而复制托管磁盘。  |

## <a name="next-steps"></a>后续步骤

[基于托管磁盘创建虚拟机](./../../virtual-machines/scripts/virtual-machines-linux-cli-sample-create-vm-from-managed-os-disks.md?toc=%2fpowershell%2fmodule%2ftoc.json)

有关 Azure CLI 的详细信息，请参阅 [Azure CLI 文档](https://docs.microsoft.com/cli/azure/overview)。

可以在 [Azure Linux VM 文档](../../virtual-machines/linux/cli-samples.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)中找到其他虚拟机和托管磁盘 CLI 脚本示例。

