<properties 
	pageTitle="管理对容器和 blob 的匿名访问 | Microsoft Azure" 
	description="了解如何使容器和 blob 可供匿名访问。" 
	services="storage" 
	documentationCenter="" 
	authors="tamram" 
	manager="jdial" 
	editor=""/>

<tags 
	ms.service="storage" 
	ms.date="09/28/2015" 
	wacn.date=""/>

# 管理对 Azure 存储资源的访问

## 概述

默认情况下，只有存储帐户的所有者可访问该帐户中的存储资源。如果服务或应用程序需要向其他客户端提供这些资源但不共享访问密钥，则有以下选项可允许访问：

- 可设置容器的权限以允许匿名读取该容器及其 Blob。匿名读取访问仅供用于容器和 Blob。 

- 可通过共享访问签名公开资源，这样即可通过指定提供资源的间隔以及客户端对于容器、Blob、表、队列、文件共享或文件将拥有的权限，允许对这些资源进行有限的访问。

- 可使用存储访问策略管理容器或其 Blob、队列、表或文件共享或其文件的共享访问签名。存储访问策略对于共享访问签名提供了另一种控制措施，并提供了一种简单明了的撤消这些签名的方法。

## 授予对容器和 blob 的匿名用户权限

默认情况下，仅存储帐户的所有者能够访问容器以及其中的所有 Blob。要授予匿名用户对容器及其 Blob 的读取权限，你可以设置容器权限以允许公共访问。匿名用户可以读取可公开访问的容器中的 Blob，而无需对请求进行身份验证。

容器提供了下列用于管理容器访问的选项：

- **完全公共读取访问：**可通过匿名请求读取容器和 Blob 数据。客户端可以通过匿名请求枚举容器中的 Blob，但无法枚举存储帐户中的容器。

- **仅针对 Blob 的公共读取访问：**可以通过匿名请求读取此容器中的 Blob 数据，但容器数据不可用。客户端无法通过匿名请求枚举容器中的 Blob。

- **无公共读取访问：**仅帐户所有者可读取容器和 Blob 数据。

>[AZURE.NOTE]如果服务要求你对 Blob 资源进行更精确的控制，或者你希望提供针对读取操作以外的其他操作的权限，则可以使用“共享访问签名”来使资源对用户可访问。

## 对匿名用户可用的功能

下表显示了在将容器的 ACL 设置为允许公共访问时匿名用户可调用的操作。

| REST 操作 | 具有完全公共读取访问权限 | 具有仅针对 Blob 的公共读取访问权限 |
|--------------------------------------------------------|-----------------------------------------|---------------------------------------------------|
| 列出容器 | 仅所有者 | 仅所有者 |
| 创建容器 | 仅所有者 | 仅所有者 |
| 获取容器属性 | 全部 | 仅所有者 |
| 获取容器元数据 | 全部 | 仅所有者 |
| 设置容器元数据 | 仅所有者 | 仅所有者 |
| 获取容器 ACL | 仅所有者 | 仅所有者 |
| 设置容器 ACL | 仅所有者 | 仅所有者 |
| 删除容器 | 仅所有者 | 仅所有者 |
| 列出 Blob | 全部 | 仅所有者 |
| 放置 Blob | 仅所有者 | 仅所有者 |
| 获取 Blob | 全部 | 全部 |
| 获取 Blob 属性 | 全部 | 全部 |
| 设置 Blob 属性 | 仅所有者 | 仅所有者 |
| 获取 Blob 元数据 | 全部 | 全部 |
| 设置 Blob 元数据 | 仅所有者 | 仅所有者 |
| 放置块 | 仅所有者 | 仅所有者 |
| 获取块列表（仅提交的块） | 全部 | 全部 |
| 获取块列表（未提交的块或所有块） | 仅所有者 | 仅所有者 |
| 放置块列表 | 仅所有者 | 仅所有者 |
| 删除 Blob | 仅所有者 | 仅所有者 |
| 复制 Blob | 仅所有者 | 仅所有者 |
| 快照 Blob | 仅所有者 | 仅所有者 |
| 租赁 Blob | 仅所有者 | 仅所有者 |
| 放置页面 | 仅所有者 | 仅所有者 |
| 获取页面范围 | 全部 | 全部 |


## 另请参阅

- [Azure 存储空间服务的身份验证](https://msdn.microsoft.com/zh-cn/library/azure/dd179428.aspx)
- [共享访问签名：了解 SAS 模型](/documentation/articles/storage-dotnet-shared-access-signature-part-1)
- [使用共享的访问签名委托访问](https://msdn.microsoft.com/zh-cn/library/azure/ee395415.aspx) 

<!---HONumber=79-->