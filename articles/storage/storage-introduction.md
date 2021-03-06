---
title: "Azure 存储简介 | Microsoft 文档"
description: "Microsoft 的云中在线数据存储 - Azure 存储的概述。 了解如何在应用程序中使用最佳的云存储解决方案。"
services: storage
documentationcenter: 
author: mmacy
manager: timlt
editor: tysonn
ms.assetid: a4a1bc58-ea14-4bf5-b040-f85114edc1f1
ms.service: storage
ms.workload: storage
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 07/26/2017
ms.author: marsma
ms.translationtype: HT
ms.sourcegitcommit: 54774252780bd4c7627681d805f498909f171857
ms.openlocfilehash: 98670b60daca7091e09ce2ab03cf2eaff015070e
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="introduction-to-microsoft-azure-storage"></a>Microsoft Azure 存储简介

## <a name="overview"></a>概述
Azure 存储是依赖于持续性、可用性和伸缩性来满足客户需求的现代应用程序的云存储解决方案。 通过阅读本文章，开发人员、IT 专业人员和业务决策人员可以了解：

* 什么是 Azure 存储，以及如何在云、移动、服务器和桌面应用程序中利用它
* 使用 Azure 存储服务可以存储哪种数据：Blob（对象）数据、NoSQL 表数据、队列消息和文件共享。
* 在 Azure 存储中如何管理对数据的访问
* 如何通过冗余和复制确保 Azure 存储数据的持久性
* 接下来要到何处去构建第一个 Azure 存储应用程序

<!-- after our quick starts are available, replace this link with a link to one of those. 
Had to remove this article, it refers to the VS quickstarts, and they've stopped publishing them. Robin --> 
<!-- To get up and running with Azure Storage quickly, see [Get started with Azure Storage in five minutes](storage-getting-started-guide.md). -->

有关可配合 Azure 存储使用的工具、库和其他资源的详细信息，请参阅下面的 [后续步骤](#next-steps) 。

## <a name="what-is-azure-storage"></a>什么是 Azure 存储空间？
对于需要为其数据使用可伸缩的、持久的且具有高可用性的存储的应用程序，云计算使其有了新的方案可供选择，这正是 Microsoft 开发 Azure 存储的原因。 除了使开发人员可以构建大型应用程序来支持新方案之外，Azure 存储还为 Azure 虚拟机提供了存储基础，进一步证明其可靠性。

Azure 存储可以大规模伸缩，因此可以存储和处理数百 TB 的数据来支持科学、财务分析和媒体应用程序所需的大数据方案。 也可以存储小型商业网站所需的少量数据。 当需求降低时，只需为当前存储的数据支付费用。 Azure 存储当前存储了数十万亿个唯一的客户对象，平均每秒处理数百万个请求。

Azure 存储是弹性的，因此可以针对大量的全球受众设计应用程序，并根据需要伸缩这些应用程序 - 在存储的数据量和针对它发出的请求数两个方面。 只需要为使用的内容付费，并且只需要在使用它时付费。

Azure 存储使用了一个自动分区系统，它可以根据流量自动对数据进行负载均衡。 这意味着当应用程序上的需求增长时，Azure 存储会自动分配合适的资源来满足这些需求。

可以从世界上的任何位置从任何类型的应用程序访问 Azure 存储，无论该应用程序是在云中、在桌面上、在本地服务器上运行还是在移动设备或平板电脑设备上运行。 可以将 Azure 存储用于移动方案，在这类方案中，应用程序在设备上存储一部分数据，并将其与存储在云中的完整数据集进行同步。

Azure 存储支持使用各种操作系统（包括 Windows 和 Linux）及各种编程语言（包括 .NET、Java、Node.js、Python、Ruby、PHP、C++ 和移动编程语言）的客户端以方便开发。 Azure 存储还通过简单的 REST API 公开数据资源，这些 REST API 可供能够通过 HTTP/HTTPS 发送和接收数据的任何客户端使用。

Azure 高级存储提供高性能、低延迟的磁盘支持，适合在 Azure 虚拟机上运行的 I/O 密集型工作负载。 有了 Azure 高级存储，便可以将多个持久性数据磁盘附加到虚拟机，并根据性能要求对其进行配置。 每个数据磁盘在 Azure 高级存储中都有一个后备 SSD 磁盘，以确保最高的 I/O 性能。 有关详细信息，请参阅 [高级存储：适用于 Azure 虚拟机工作负荷的高性能存储](storage-premium-storage.md) 。

## <a name="introducing-the-azure-storage-services"></a>Azure 存储服务简介
Azure 存储提供以下四种服务：Blob 存储、表存储、队列存储和文件存储。

* Blob 存储用于存储非结构化对象数据。 Blob 可以是任何类型的文本或二进制数据，例如文档、媒体文件或应用程序安装程序。 Blob 存储也称为对象存储。
* 表存储用于存储结构化数据集。 表存储是一个 NoSQL“键-属性”数据存储，可以用于实现快速开发以及快速访问大量数据。
* 队列存储为云服务的各个组件之间的工作流处理和通信提供可靠的消息传送。
* 文件存储使用标准 SMB 协议为旧版应用程序提供共享存储。 Azure 虚拟机和云服务可通过装载的共享在应用程序组件之间共享文件数据，本地应用程序可通过文件服务 REST API 来访问共享中的文件数据。

Azure 存储帐户是一个安全的帐户，用于访问 Azure 存储中的服务。 存储帐户为存储资源提供唯一的命名空间。 下图显示了存储帐户中各种 Azure 存储资源之间的关系：

![Azure 存储资源](./media/storage-introduction/storage-concepts.png)

[!INCLUDE [storage-account-types-include](../../includes/storage-account-types-include.md)]

[!INCLUDE [storage-versions-include](../../includes/storage-versions-include.md)]

## <a name="blob-storage"></a>Blob 存储
对于有大量非结构化对象数据要存储在云中的用户，Blob 存储提供了一种经济高效且可伸缩的解决方案。 可以使用 Blob 存储来存储如下内容：

* 文档
* 社交数据，例如照片、视频、音乐和博客
* 文件、计算机、数据库和设备的备份
* Web 应用程序的图像和文本
* 云应用程序的配置数据
* 大数据，例如日志和其他大型数据集

每个 Blob 都组织到一个容器中。 容器还提供了一种有用的方式来向对象组分配安全策略。 一个存储帐户可以包含任意数目的容器，一个容器可以包含任意数目的 Blob，直至达到存储帐户的容量限制 500 TB。

Blob 存储提供三种类型的 Blob：块 Blob、追加 Blob 和页 Blob（磁盘）。

* 块 Blob 进行了相应的优化来流化和存储云对象，并且是用于存储文档、介质文件和备份等对象的不错选择。
* 追加 Blob 类似于块 Blob，但针对追加追加操作进行了优化。 追加 Blob 仅可以通过将新的块添加到末尾来进行更新。 对于需要新数据只能写入到 Blob 结尾的情况，例如日志记录，追加 Blob 是一个不错的选择 。
* 页 Blob 进行了相应的优化来表示 IaaS 磁盘和支持随机写入，并且最大可以为 1 TB。 Azure 虚拟机网络连接的 IaaS 磁盘是一个 VHD，存储为页 Blob。

对于网络限制使得通过线缆向 Blob 存储上传或从其下载数据不可行的每个大型数据集，可以将硬盘驱动器发送到 Microsoft 以直接通过数据中心导入或导出数据。 请参阅[使用 Microsoft Azure 导入/导出服务将数据传输到 Blob 存储中](storage-import-export-service.md)。

## <a name="table-storage"></a>表存储

[!INCLUDE [storage-table-cosmos-db-tip-include](../../includes/storage-table-cosmos-db-tip-include.md)]

与前几代的必需软件相比，现代应用程序通常要求数据存储具有更高的可伸缩性和灵活性。 表存储提供了具有高可用性且可大规模伸缩的存储，因此应用程序可以自动伸缩以满足用户需求。 表存储是 Microsoft 的 NoSQL 键/属性存储 - 它具有无模式的设计，使其不同于传统的关系数据库。 采用无模式的数据存储，可以很容易地随着应用程序需求的发展使数据适应存储。 表存储易于使用，因此开发人员可以快速创建应用程序。 对于所有类型的应用程序，都可以快速并经济高效地访问数据。  对于相似的数据量，表存储的成本通常显著低于传统的 SQL。

表存储是一种“键-属性”存储，这意味着表中的每个值都是随所键入的一个属性名称存储的。 属性名称可以用来筛选和指定选择条件。 属性集合及其值构成了实体。 因为表存储是无模式的，因此同一表中的两个实体可以包含不同的属性集合，并且这些属性可以属于不同的类型。

可以使用表存储来存储灵活的数据集，例如 Web 应用程序的用户数据、通讯簿、设备信息，以及服务需要的任何其他类型的元数据。  可以在表中存储任意数量的实体，并且一个存储帐户可以包含任意数量的表，直至达到存储帐户的容量极限。

像 Blob 和队列一样，开发人员可以使用标准 REST 协议来管理和访问表存储，不过，表存储还支持 OData 协议的一个子集，这简化了高级查询功能并支持 JSON 和 AtomPub（基于 XML）格式。

对于当前的基于 Internet 的应用程序，NoSQL 数据库（例如表存储）提供了一种用于替代传统的关系数据库的主流方式。

## <a name="queue-storage"></a>队列存储
在设计应用程序以实现伸缩性时，通常要将各个应用程序组件分离，使其可以独立地进行伸缩。 队列存储为在应用程序组件之间进行异步通信提供了一种可靠的消息传送解决方案，无论这些应用程序组件是在云中、在桌面上、在本地服务器上运行还是在移动设备上运行。 队列存储还支持管理异步任务以及构建过程工作流。

一个存储帐户可以包含任意数目的队列。 队列可以包含任意数量的消息，直至达到存储帐户的容量极限。 每条消息最大可以为 64 KB。

## <a name="file-storage"></a>文件存储
可以通过 Azure 文件服务设置可用性高的网络文件共享，以便使用标准的服务器消息块 (SMB) 协议对其进行访问。 这意味着，多个 VM 可以共享启用了读取和写入访问权限的相同文件。 也可使用 REST 接口或存储客户端库来读取文件。

Azure 文件存储不同于公司文件共享的一点是，可以在全球任何地方使用 URL 来访问文件，只要该 URL 指向文件且包含共享访问签名 (SAS) 令牌即可。 可以生成 SAS 令牌，用于在指定时间内对私有资产进行特定访问。

文件共享适用于许多常用方案：

* 许多本地应用程序使用文件共享。 此功能可以更方便地迁移那些将数据共享到 Azure 的应用程序。 如果将文件共享装载到本地应用程序所使用的驱动器号，则应用程序中访问文件共享的那部分应尽量少做更改（如果必须进行更改的话）。

* 配置文件可以在一个文件共享上存储，从多个 VM 进行访问。 可以将一个组中多个开发人员使用的工具和实用程序存储到文件共享中，确保每个人都能找到它们并使用同一版本。

* 例如，诊断日志、指标和故障转储是三种可以写入到文件共享中供以后处理或分析的数据。

目前不支持基于 Active Directory 的身份验证和访问控制列表 (ACL)，但将来的某个时候会提供此方面的支持。 存储帐户凭据用于提供访问文件共享所需的身份验证。 这意味着，任何人只要装载了共享都具有该共享的完整读/写访问权限。

## <a name="access-to-blob-table-queue-and-file-resources"></a>访问 Blob、表、队列和文件资源
默认情况下，只有存储帐户所有者可以访问存储帐户中的资源。 为保证数据的安全性，对你帐户中的资源发出的每个请求都必须进行身份验证。 身份验证依赖于一个共享密钥模型。 还可以将 Blob 配置为支持异步身份验证。

在创建存储帐户时为其分配了两个用于身份验证的私有访问密钥。 设置两个密钥可以确保应用程序在定期重新生成密钥（这是一种常用的安全密钥管理做法）时仍然保持可用。

如果不需要为存储资源实施用户受控访问，则可以创建一个共享访问签名。 共享访问签名是一个可以附加到 URL 的令牌，可以实现对存储资源的委托访问。 持有令牌的任何人都可以在令牌有效期间使用它指定的权限访问它指向的资源。 从 2015-04-05 版开始，Azure 存储支持两种类型的共享访问签名：服务 SAS 和帐户 SAS。

服务 SAS 只能委派对以下一个存储服务中的资源的访问权限：Blob、队列、表或文件服务。

帐户 SAS 可委派对一个或多个存储服务中的资源的访问权限。 可以委派对服务级别操作的访问权限，而这是服务 SAS 所无法提供的。 还可以委派对 blob 容器、表、队列和文件共享执行读取、写入和删除操作的访问权限，而这是服务 SAS 所不允许的。

最后，可以指定一个容器及其 Blob 或某个特定的 Blob 可供公开访问。 指定某个容器或 Blob 为公用的时，任何人都可以匿名读取它，不需要进行身份验证。  公用容器和 Blob 非常适用于公开在网站上托管的资源，例如媒体和文档。  要降低全球受众的网络延迟，可以通过 Azure CDN 来缓存网站使用的 Blob 数据。

有关共享访问签名的详细信息，请参阅 [使用共享访问签名 (SAS)](storage-dotnet-shared-access-signature-part-1.md) 。 有关安全访问存储帐户的详细信息，请参阅[管理对容器和 Blob 的匿名读取访问](storage-manage-access-to-resources.md)和 [Authentication for the Azure Storage Services](https://msdn.microsoft.com/library/azure/dd179428.aspx)（Azure 存储服务身份验证）。

## <a name="replication-for-durability-and-high-availability"></a>用于实现持久性和高可用性的复制
始终复制 Microsoft Azure 存储帐户中的数据以确保持久性和高可用性。 复制可在同一数据中心内或向第二个数据中心复制数据，具体取决于所选的复制选项。 复制可保护数据，并在发生暂时性硬件故障时保留应用程序正常运行时间。 如果数据复制到第二个数据中心，它还可以保护数据，以免主要位置发送灾难性故障。

即使面临故障时，复制也可确保存储帐户满足[存储的服务级别协议 (SLA)](https://azure.microsoft.com/support/legal/sla/storage/)的要求。 请参阅 SLA，了解有关 Azure 存储确保持续性和可用性的信息。

创建存储帐户时，可以选择以下复制选项之一：

* **本地冗余存储 (LRS)。** 本地冗余存储保留数据的三个副本。 LRS 会在单个区域中的单个数据中心内复制三次。 LRS 可以保护数据免受普通的硬件故障损害，但无法保护数据免受单个数据中心故障的损害。

    LRS 以折扣价格提供。 为获得最大持久性，我们建议使用下文所述的地域冗余存储。
* **区域冗余存储 (ZRS)。** 区域冗余存储保留数据的三个副本。 ZRS 在两到三个设施之间复制三次（在单个区域内或两个区域之间），提供比 LRS 更高的持久性。 ZRS 在单个区域内确保数据持久保存。

    ZRS 提供比 LRS 更高级别的持久性；不过，为获得最大持久性，我们建议使用下文所述的地域冗余存储。

  > [!NOTE]
  > ZRS 当前仅适用于块 blob，并且仅支持版本 2014-02-14 和更高版本。
  >
  > 在创建存储帐户并选择 ZRS 后，无法将其转换为使用任何其他类型的复制，反之亦然。
  >
  >
* **异地冗余存储 (GRS)**。 GRS 维护数据的六个副本。 使用 GRS 时，数据会在主区域内复制三次，并且还在离主区域数百英里的辅助区域中复制三次，从而提供最高级别的持久性。 当主区域中发生故障时，Azure 存储将故障转移到辅助区域。 GRS 在两个不同的区域中确保数据持久保存。

    有关主配对和辅助配对（按区域）的详细信息，请参阅 [Azure 区域](https://azure.microsoft.com/regions/)。
* **读取访问异地冗余存储 (RA-GRS)**。 读取访问异地冗余存储将数据复制到一个辅助地理位置，同时提供对你在辅助位置中的数据的读取访问权限。 读取访问地域冗余存储允许从主位置或辅助位置访问数据，以防其中一个位置不可用。 默认情况下，从创建存储帐户开始，读取访问异地冗余存储即是存储帐户的默认选项。

  > [!IMPORTANT]
  > 创建存储帐户后，可以更改复制数据的方式，除非在创建该帐户时指定了 ZRS。 但请注意，如果从 LRS 切换到 GRS 或 RA-GRS，可能会产生额外的一次性数据传输费用。
  >
  >

有关存储复制选项的其他详细信息，请参阅 [Azure 存储复制](storage-redundancy.md) 。

有关存储帐户复制的定价信息，请参阅 [Azure 存储定价](https://azure.microsoft.com/pricing/details/storage/)。 有关每个区域中提供了哪些服务的详细信息，请参阅 [Azure 区域](https://azure.microsoft.com/regions/#services) 。

有关 Azure 存储持久性的体系结构详细信息，请参阅 [SOSP Paper - Azure Storage: A Highly Available Cloud Storage Service with Strong Consistency](http://blogs.msdn.com/b/windowsazurestorage/archive/2011/11/20/windows-azure-storage-a-highly-available-cloud-storage-service-with-strong-consistency.aspx)（SOSP 论文 - Azure 存储空间：具有高度一致性的高可用云存储服务）。

## <a name="transferring-data-to-and-from-azure-storage"></a>将数据传输到和移出 Azure 存储
可以使用 AzCopy 命令行实用程序复制存储帐户内或跨存储帐户的 blob、文件和表数据。 有关详细信息，请参阅 [使用 AzCopy 命令行实用程序传输数据](storage-use-azcopy.md) 。

AzCopy 在 [Azure 数据移动库](https://www.nuget.org/packages/Microsoft.Azure.Storage.DataMovement/)的基础上构建，当前以预览版提供。

利用 Azure 导入/导出服务提供的方法，通过邮寄给 Azure 数据中心的硬盘，将 Blob 数据导入到存储帐户中或从存储帐户中导出。 有关导入/导出服务的详细信息，请参阅[使用 Microsoft Azure 导入/导出服务将数据传输到 Blob 存储中](storage-import-export-service.md)。

## <a name="pricing"></a>定价
[!INCLUDE [storage-account-billing-include](../../includes/storage-account-billing-include.md)]

## <a name="storage-apis-libraries-and-tools"></a>存储 API、库和工具
Azure 存储资源可以通过任何发出 HTTP/HTTPS 请求的语言来进行访问。 另外，Azure 存储还为多种主流语言提供了编程库。 这些库通过对细节进行处理简化了使用 Azure 存储的许多方面，这些细节包括同步和异步调用、操作的批处理、异常管理、自动重试、操作行为，等等。 这些库当前可供下列语言和平台以及正在筹备的其他语言和平台使用：

### <a name="azure-storage-data-services"></a>Azure 存储数据服务
* [存储服务 REST API](http://msdn.microsoft.com/library/azure/dd179355.aspx)
* [适用于 .NET、Windows Phone 和 Windows 运行时的存储空间客户端库](https://www.nuget.org/packages/WindowsAzure.Storage/)
* [适用于 C++ 的存储客户端库](https://github.com/Azure/azure-storage-cpp)
* [适用于 Java/Android 的存储空间客户端库](https://azure.microsoft.com/develop/java/)
* [适用于 Node.js 的存储空间客户端库](http://dl.windowsazure.com/nodestoragedocs/index.html)
* [适用于 PHP 的存储空间客户端库](https://azure.microsoft.com/develop/php/)
* [适用于 Ruby 的存储空间客户端库](https://azure.microsoft.com/develop/ruby/)
* [适用于 Python 的存储空间客户端库](https://azure.microsoft.com/develop/python/)
* [适用于 PowerShell 1.0 的存储空间 Cmdlet](/powershell/module/azurerm.storage/#storage)

### <a name="azure-storage-management-services"></a>Azure 存储管理服务
* [存储资源提供程序 REST API 参考](/rest/api/storagerp/)
* [适用于 .NET 的存储资源提供程序客户端库](/dotnet/api/microsoft.azure.management.storage)
* [适用于 PowerShell 1.0 的存储资源提供程序 Cmdlet](/powershell/module/azure.storage)
* [存储服务管理 REST API (Classic)](https://msdn.microsoft.com/library/azure/ee460790.aspx)

### <a name="azure-storage-data-movement-services"></a>Azure 存储数据移动服务
* [存储导入/导出服务 REST API](storage-import-export-service.md)
* [适用于 .NET 的存储数据移动客户端库](https://www.nuget.org/packages/Microsoft.Azure.Storage.DataMovement/)

### <a name="tools-and-utilities"></a>工具和实用程序
* [Microsoft Azure 存储资源管理器](../vs-azure-tools-storage-manage-with-storage-explorer.md)是 Microsoft 免费提供的独立应用，适用于在 Windows、macOS 和 Linux 上以可视方式处理 Azure 存储数据。
* [Azure 存储客户端工具](storage-explorers.md)
* [Azure SDK 和工具](https://azure.microsoft.com/tools/)
* [Azure 存储模拟器](http://www.microsoft.com/download/details.aspx?id=43709)
* [Azure PowerShell](/powershell/azure/overview)
* [AzCopy 命令行实用程序](http://aka.ms/downloadazcopy)

## <a name="next-steps"></a>后续步骤
若要了解有关 Azure 存储的详细信息，请参阅以下资源：

### <a name="documentation"></a>文档
* [Azure 存档文档](https://azure.microsoft.com/documentation/services/storage/)
* [创建存储帐户](storage-create-storage-account.md)

<!-- after our quick starts are available, replace this link with a link to one of those. 
Had to remove this article, it refers to the VS quickstarts, and they've stopped publishing them. Robin --> 
<!--* [Get started with Azure Storage in five minutes](storage-getting-started-guide.md)
-->

### <a name="for-administrators"></a>面向管理员
* [对 Azure 存储空间使用 Azure PowerShell](storage-powershell-guide-full.md)
* [将 Azure CLI 用于 Azure 存储](storage-azure-cli.md)

### <a name="for-net-developers"></a>面向 .NET 开发人员
* [通过 .NET 开始使用 Azure Blob 存储](storage-dotnet-how-to-use-blobs.md)
* [通过 .NET 开始使用 Azure 表存储](storage-dotnet-how-to-use-tables.md)
* [通过 .NET 开始使用 Azure 队列存储](storage-dotnet-how-to-use-queues.md)
* [在 Windows 上开始使用 Azure 文件存储](storage-dotnet-how-to-use-files.md)

### <a name="for-javaandroid-developers"></a>面向 Java/Android 开发人员
* [如何通过 Java 使用 Blob 存储](storage-java-how-to-use-blob-storage.md)
* [如何通过 Java 使用表存储](storage-java-how-to-use-table-storage.md)
* [如何通过 Java 使用队列存储](storage-java-how-to-use-queue-storage.md)
* [如何通过 Java 使用文件存储](storage-java-how-to-use-file-storage.md)

### <a name="for-nodejs-developers"></a>面向 Node.js 开发人员
* [如何通过 Node.js 使用 Blob 存储](storage-nodejs-how-to-use-blob-storage.md)
* [如何通过 Node.js 使用表存储](storage-nodejs-how-to-use-table-storage.md)
* [如何通过 Node.js 使用队列存储](storage-nodejs-how-to-use-queues.md)

### <a name="for-php-developers"></a>面向 PHP 开发人员
* [如何通过 PHP 使用 Blob 存储](storage-php-how-to-use-blobs.md)
* [如何通过 PHP 使用表存储](storage-php-how-to-use-table-storage.md)
* [如何通过 PHP 使用队列存储](storage-php-how-to-use-queues.md)

### <a name="for-ruby-developers"></a>面向 Ruby 开发人员
* [如何通过 Ruby 使用 Blob 存储](storage-ruby-how-to-use-blob-storage.md)
* [如何通过 Ruby 使用表存储](storage-ruby-how-to-use-table-storage.md)
* [如何通过 Ruby 使用队列存储](storage-ruby-how-to-use-queue-storage.md)

### <a name="for-python-developers"></a>面向 Python 开发人员
* [如何通过 Python 使用 Blob 存储](storage-python-how-to-use-blob-storage.md)
* [如何通过 Python 使用表存储](storage-python-how-to-use-table-storage.md)
* [如何通过 Python 使用队列存储](storage-python-how-to-use-queue-storage.md)
* [如何通过 Python 使用文件存储](storage-python-how-to-use-file-storage.md)

