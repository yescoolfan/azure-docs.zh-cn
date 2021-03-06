---
title: "使用 Azure CLI 创建和管理 Linux VM | Microsoft Docs"
description: "教程 - 使用 Azure CLI 创建和管理 Linux VM"
services: virtual-machines-linux
documentationcenter: virtual-machines
author: neilpeterson
manager: timlt
editor: tysonn
tags: azure-service-management
ms.assetid: 
ms.service: virtual-machines-linux
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 05/02/2017
ms.author: nepeters
ms.custom: mvc
ms.translationtype: Human Translation
ms.sourcegitcommit: 7948c99b7b60d77a927743c7869d74147634ddbf
ms.openlocfilehash: 1063807ac83d2f63229f397da7ecc01f4072efd5
ms.contentlocale: zh-cn
ms.lasthandoff: 06/20/2017

---

# 使用 Azure CLI 创建和管理 Linux VM
<a id="create-and-manage-linux-vms-with-the-azure-cli" class="xliff"></a>

Azure 虚拟机提供完全可配置的灵活计算环境。 本教程介绍 Azure 虚拟机的基本部署项目，例如选择 VM 大小、选择 VM 映像和部署 VM。 你将学习如何：

> [!div class="checklist"]
> * 创建并连接到 VM
> * 选择并使用 VM 映像
> * 查看和使用特定 VM 大小
> * 调整 VM 的大小
> * 查看并了解 VM 状态


[!INCLUDE [cloud-shell-try-it.md](../../../includes/cloud-shell-try-it.md)]

如果选择在本地安装并使用 CLI，本教程要求运行 Azure CLI 2.0.4 或更高版本。 运行 `az --version` 即可查找版本。 如果需要进行安装或升级，请参阅[安装 Azure CLI 2.0]( /cli/azure/install-azure-cli)。 

## 创建资源组
<a id="create-resource-group" class="xliff"></a>

使用 [az group create](https://docs.microsoft.com/cli/azure/group#create) 命令创建资源组。 

Azure 资源组是在其中部署和管理 Azure 资源的逻辑容器。 必须在创建虚拟机前创建资源组。 在此示例中，在“eastus”区域中创建了名为“myResourceGroupVM”的资源组。 

```azurecli-interactive 
az group create --name myResourceGroupVM --location eastus
```

创建或修改 VM 时指定资源组，本教程会对此进行演示。

## 创建虚拟机
<a id="create-virtual-machine" class="xliff"></a>

使用 [az vm create](https://docs.microsoft.com/cli/azure/vm#create) 命令创建虚拟机。 

创建虚拟机时，可使用多个选项，例如操作系统映像、磁盘大小调整和管理凭据。 在此示例中，创建了一个名为“myVM”的运行 Ubuntu Server 的虚拟机。 

```azurecli-interactive 
az vm create --resource-group myResourceGroupVM --name myVM --image UbuntuLTS --generate-ssh-keys
```

创建 VM 后，Azure CLI 会输出有关 VM 的信息。 请记下 `publicIpAddress`，可以使用此地址访问虚拟机。 

```azurecli-interactive 
{
  "fqdns": "",
  "id": "/subscriptions/d5b9d4b7-6fc1-0000-0000-000000000000/resourceGroups/myResourceGroupVM/providers/Microsoft.Compute/virtualMachines/myVM",
  "location": "eastus",
  "macAddress": "00-0D-3A-23-9A-49",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.4",
  "publicIpAddress": "52.174.34.95",
  "resourceGroup": "myResourceGroupVM"
}
```

## 连接到 VM
<a id="connect-to-vm" class="xliff"></a>

现在可以使用 SSH 连接到 VM。 将示例 IP 地址替换为上一步骤中记下的 `publicIpAddress`。

```bash
ssh 52.174.34.95
```

使用完 VM 后，请关闭 SSH 会话。 

```bash
exit
```

## 了解 VM 映像
<a id="understand-vm-images" class="xliff"></a>

Azure 应用商店包括许多可用于创建 VM 的映像。 在之前的步骤中，使用 Ubuntu 映像创建了虚拟机。 在此步骤中，Azure CLI 用于在应用商店中搜索 CentOS 映像，此映像稍后将用于部署第二个虚拟机。  

若要查看最常用的映像列表，请使用 [az vm image list](/cli/azure/vm/image#list) 命令。

```azurecli-interactive 
az vm image list --output table
```

命令输出返回 Azure 上最常用的 VM 映像。

```bash
Offer          Publisher               Sku                 Urn                                                             UrnAlias             Version
-------------  ----------------------  ------------------  --------------------------------------------------------------  -------------------  ---------
WindowsServer  MicrosoftWindowsServer  2016-Datacenter     MicrosoftWindowsServer:WindowsServer:2016-Datacenter:latest     Win2016Datacenter    latest
WindowsServer  MicrosoftWindowsServer  2012-R2-Datacenter  MicrosoftWindowsServer:WindowsServer:2012-R2-Datacenter:latest  Win2012R2Datacenter  latest
WindowsServer  MicrosoftWindowsServer  2008-R2-SP1         MicrosoftWindowsServer:WindowsServer:2008-R2-SP1:latest         Win2008R2SP1         latest
WindowsServer  MicrosoftWindowsServer  2012-Datacenter     MicrosoftWindowsServer:WindowsServer:2012-Datacenter:latest     Win2012Datacenter    latest
UbuntuServer   Canonical               16.04-LTS           Canonical:UbuntuServer:16.04-LTS:latest                         UbuntuLTS            latest
CentOS         OpenLogic               7.3                 OpenLogic:CentOS:7.3:latest                                     CentOS               latest
openSUSE-Leap  SUSE                    42.2                SUSE:openSUSE-Leap:42.2:latest                                  openSUSE-Leap        latest
RHEL           RedHat                  7.3                 RedHat:RHEL:7.3:latest                                          RHEL                 latest
SLES           SUSE                    12-SP2              SUSE:SLES:12-SP2:latest                                         SLES                 latest
Debian         credativ                8                   credativ:Debian:8:latest                                        Debian               latest
CoreOS         CoreOS                  Stable              CoreOS:CoreOS:Stable:latest                                     CoreOS               latest
```

可以通过添加 `--all` 参数查看完整列表。 还可以按 `--publisher` 或 `–-offer` 筛选映像列表。 在此示例中，已在列表中筛选出其产品与“CentOS”匹配的所有映像。 

```azurecli-interactive 
az vm image list --offer CentOS --all --output table
```

部分输出：

```azurecli-interactive 
Offer             Publisher         Sku   Urn                                     Version
----------------  ----------------  ----  --------------------------------------  -----------
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.201501         6.5.201501
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.201503         6.5.201503
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.201506         6.5.201506
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.20150904       6.5.20150904
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.20160309       6.5.20160309
CentOS            OpenLogic         6.5   OpenLogic:CentOS:6.5:6.5.20170207       6.5.20170207
```

若要使用特定映像部署 VM，请记下“Urn”列中的值。 指定映像时，可将映像版本号替换为“latest”，这会选择最新的发行版。 在此示例中，`--image` 参数用于指定最新版本的 CentOS 6.5 映像。  

```azurecli-interactive 
az vm create --resource-group myResourceGroupVM --name myVM2 --image OpenLogic:CentOS:6.5:latest --generate-ssh-keys
```

## 了解 VM 大小
<a id="understand-vm-sizes" class="xliff"></a>

虚拟机大小决定虚拟机可用计算资源（如 CPU、GPU 和内存）的数量。 需要根据预期的工作负载适当调整虚拟机的大小。 如果工作负荷增加，则可调整现有虚拟机的大小。

### VM 大小
<a id="vm-sizes" class="xliff"></a>

下表将大小分类成了多个用例。  

| 类型                     | 大小           |    说明       |
|--------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------|
| [常规用途](sizes-general.md)         |DSv2、Dv2、DS、D、Av2、A0-7| CPU 与内存之比均衡。 适用于开发/测试、小到中型应用程序和数据解决方案。  |
| [计算优化](sizes-compute.md)   | Fs, F             | 高 CPU 与内存之比。 适用于中等流量的应用程序、网络设备和批处理。        |
| [内存优化](../virtual-machines-windows-sizes-memory.md)    | GS, G, DSv2, DS, Dv2, D   | 较高的内存核心比。 适用于关系数据库、中到大型缓存和内存中分析。                 |
| [存储优化](../virtual-machines-windows-sizes-storage.md)      | LS                | 高磁盘吞吐量和 IO。 适用于大数据、SQL 和 NoSQL 数据库。                                                         |
| [GPU](sizes-gpu.md)          | NV, NC            | 专门针对大量图形绘制和视频编辑的 VM。       |
| [高性能](sizes-hpc.md) | H, A8-11          | 功能极其强大的 CPU VM 具有可选的高吞吐量网络接口 (RDMA)。 


### 查找可用的 VM 大小
<a id="find-available-vm-sizes" class="xliff"></a>

若要查看在特定区域可用的 VM 大小的列表，请使用 [az vm list-sizes](/cli/azure/vm#list-sizes) 命令。 

```azurecli-interactive 
az vm list-sizes --location eastus --output table
```

部分输出：

```azurecli-interactive 
  MaxDataDiskCount    MemoryInMb  Name                      NumberOfCores    OsDiskSizeInMb    ResourceDiskSizeInMb
------------------  ------------  ----------------------  ---------------  ----------------  ----------------------
                 2          3584  Standard_DS1                          1           1047552                    7168
                 4          7168  Standard_DS2                          2           1047552                   14336
                 8         14336  Standard_DS3                          4           1047552                   28672
                16         28672  Standard_DS4                          8           1047552                   57344
                 4         14336  Standard_DS11                         2           1047552                   28672
                 8         28672  Standard_DS12                         4           1047552                   57344
                16         57344  Standard_DS13                         8           1047552                  114688
                32        114688  Standard_DS14                        16           1047552                  229376
                 1           768  Standard_A0                           1           1047552                   20480
                 2          1792  Standard_A1                           1           1047552                   71680
                 4          3584  Standard_A2                           2           1047552                  138240
                 8          7168  Standard_A3                           4           1047552                  291840
                 4         14336  Standard_A5                           2           1047552                  138240
                16         14336  Standard_A4                           8           1047552                  619520
                 8         28672  Standard_A6                           4           1047552                  291840
                16         57344  Standard_A7                           8           1047552                  619520
```

### 创建具有特定大小的 VM
<a id="create-vm-with-specific-size" class="xliff"></a>

在前面的 VM 创建示例中未提供大小，因此会使用默认大小。 可以在创建时使用 [az vm create](/cli/azure/vm#create) 和 `--size` 参数选择 VM 大小。 

```azurecli-interactive 
az vm create \
    --resource-group myResourceGroupVM \
    --name myVM3 \
    --image UbuntuLTS \
    --size Standard_F4s \
    --generate-ssh-keys
```

### 调整 VM 的大小
<a id="resize-a-vm" class="xliff"></a>

部署 VM 后，可调整其大小以增加或减少资源分配。

调整 VM 大小之前，请检查所需的大小在当前 Azure 群集上是否可用。 [az vm list-vm-resize-options](/cli/azure/vm#list-vm-resize-options) 命令返回大小列表。 

```azurecli-interactive 
az vm list-vm-resize-options --resource-group myResourceGroupVM --name myVM --query [].name
```
如果所需大小可用，则可从开机状态调整 VM 大小，但需在此操作期间重启 VM。 使用 [az vm resize]( /cli/azure/vm#resize) 命令执行大小调整。

```azurecli-interactive 
az vm resize --resource-group myResourceGroupVM --name myVM --size Standard_DS4_v2
```

如果所需大小在当前群集上不可用，则需解除分配 VM，然后才能执行调整大小操作。 使用 [az vm deallocate]( /cli/azure/vm#deallocate) 命令停止和解除分配 VM。 请注意，重新打开 VM 的电源时，可能会删除临时磁盘上的所有数据。 除非使用静态 IP 地址，否则公共 IP 地址也会更改。 

```azurecli-interactive 
az vm deallocate --resource-group myResourceGroupVM --name myVM
```

解除分配 VM 后，可能会发生大小调整。 

```azurecli-interactive 
az vm resize --resource-group myResourceGroupVM --name myVM --size Standard_GS1
```

调整大小后，可以启动 VM。

```azurecli-interactive 
az vm start --resource-group myResourceGroupVM --name myVM
```

## VM 电源状态
<a id="vm-power-states" class="xliff"></a>

Azure VM 可能会处于多种电源状态之一。 从虚拟机监控程序的角度来看，此状态表示 VM 的当前状态。 

### 电源状态
<a id="power-states" class="xliff"></a>

| 电源状态 | 说明
|----|----|
| 正在启动 | 指示正在启动虚拟机。 |
| 正在运行 | 指示虚拟机正在运行。 |
| 正在停止 | 指示正在停止虚拟机。 | 
| 已停止 | 指示虚拟机已停止。 虚拟机处于停止状态时仍会产生计算费用。  |
| 正在解除分配 | 指示正在解除分配虚拟机。 |
| 已解除分配 | 指示虚拟机已从监控程序中删除，但仍可在控制面板中使用。 处于“已解除分配”状态的虚拟机不会产生计算费用。 |
| - | 指示虚拟机的电源状态未知。 |

### 查找电源状态
<a id="find-power-state" class="xliff"></a>

若要检索特定 VM 的状态，请使用 [az vm get instance-view](/cli/azure/vm#get-instance-view) 命令。 请确保为虚拟机和资源组指定有效的名称。 

```azurecli-interactive 
az vm get-instance-view \
    --name myVM \
    --resource-group myResourceGroupVM \
    --query instanceView.statuses[1] --output table
```

输出：

```azurecli-interactive 
ode                DisplayStatus    Level
------------------  ---------------  -------
PowerState/running  VM running       Info
```

## 管理任务
<a id="management-tasks" class="xliff"></a>

在虚拟机生命周期中，你可能需要运行管理任务，例如启动、停止或删除虚拟机。 此外，可能还需要创建脚本来自动执行重复或复杂的任务。 使用 Azure CLI，可从命令行或脚本运行许多常见的管理任务。 

### 获取 IP 地址
<a id="get-ip-address" class="xliff"></a>

此命令返回虚拟机的私有 IP 地址和公共 IP 地址。  

```azurecli-interactive 
az vm list-ip-addresses --resource-group myResourceGroupVM --name myVM --output table
```

### 停止虚拟机
<a id="stop-virtual-machine" class="xliff"></a>

```azurecli-interactive 
az vm stop --resource-group myResourceGroupVM --name myVM
```

### 启动虚拟机
<a id="start-virtual-machine" class="xliff"></a>

```azurecli-interactive 
az vm start --resource-group myResourceGroupVM --name myVM
```

### 删除资源组
<a id="delete-resource-group" class="xliff"></a>

删除资源组会删除其包含的所有资源。

```azurecli-interactive 
az group delete --name myResourceGroupVM --no-wait --yes
```

## 后续步骤
<a id="next-steps" class="xliff"></a>

在本教程中，已学习 VM 创建和管理的基本知识，例如如何：

> [!div class="checklist"]
> * 创建并连接到 VM
> * 选择并使用 VM 映像
> * 查看和使用特定 VM 大小
> * 调整 VM 的大小
> * 查看并了解 VM 状态

请转到下一教程，了解 VM 磁盘。  

> [!div class="nextstepaction"]
> [创建和管理 VM 磁盘](./tutorial-manage-disks.md)

