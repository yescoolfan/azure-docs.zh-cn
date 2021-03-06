---
title: "Azure Database for PostgreSQL 中的服务器概念 | Microsoft Docs"
description: "本主题提供使用 Azure Database for PostgreSQL 服务器的注意事项和指南。"
services: postgresql
author: SaloniSonpal
ms.author: salonis
manager: jhubbard
editor: jasonwhowell
ms.service: postgresql-database
ms.topic: article
ms.date: 05/10/2017
ms.translationtype: Human Translation
ms.sourcegitcommit: ff2fb126905d2a68c5888514262212010e108a3d
ms.openlocfilehash: 5197a3f44a085d25d964f355154d92b08e65560b
ms.contentlocale: zh-cn
ms.lasthandoff: 06/17/2017

---
# <a name="azure-database-for-postgresql-servers"></a>Azure Database for PostgreSQL 服务器

本主题提供使用 Azure Database for PostgreSQL 服务器的注意事项和指南。

## <a name="what-is-an-azure-database-for-postgresql-server"></a>什么是 Azure Database for PostgreSQL 服务器？

Azure Database for PostgreSQL 服务器是多个数据库的中心管理点。 它的 PostgreSQL 服务器构造与本地环境中用户可能比较熟悉的构造相同。 具体而言，PostgreSQL 服务是托管的服务，它提供性能保证、公开服务器级访问权限和功能。

Azure Database for PostgreSQL 服务器：

- 在 Azure 订阅中创建。
- 是数据库的父资源。
- 为数据库提供了一个命名空间。
- 是具有强生存期语义的容器 - 删除服务器时将删除所包含的数据库。
- 并置区域中的资源。
- 提供用于服务器和数据库访问的连接终结点 (.postgresql.database.azure.com)。
- 提供应用于其数据库的管理策略的作用域：登录名、防火墙、用户、角色、配置等。
- 在多个版本内可用。 有关详细信息，请参阅[支持的 PostgreSQL 数据库版本](concepts-supported-versions.md)。
- 用户可将其进行扩展。 有关详细信息，请参阅 [PostgreSQL 扩展](concepts-extensions.md)。

## <a name="how-do-i-connect-and-authenticate-to-an-azure-database-for-postgresql-server"></a>如何连接到 Azure Database for PostgreSQL 服务器并向其进行身份验证？

以下元素有助于确保安全地访问数据库。

|||
| :-- | :-- |
| **身份验证和授权** | Azure Database for PostgreSQL 服务器支持本机 PostgreSQL 身份验证。 可使用服务器的管理员登录名连接到服务器并进行身份验证。 |
| **协议** | 该服务支持 PostgreSQL 使用的基于消息的协议。 |
| TCP/IP | 通过 TCP/IP 和 Unix 域套接字支持该协议。 |
| **防火墙** | 为了帮助保护数据，在用户指定具有访问权限的计算机之前，防火墙规则将禁止所有对数据库服务器或其数据库的访问。 请参阅 [Azure Database for PostgreSQL 服务器防火墙规则](concepts-firewall-rules.md)。 |
|||

## <a name="how-do-i-manage-a-server"></a>如何管理服务器？

可通过使用 Azure 门户或 [Azure CLI](/cli/azure/postgres).来管理 Azure Database for PostgreSQL 服务器。

## <a name="next-steps"></a>后续步骤

- 有关该服务的概述，请参阅 [Azure Database for PostgreSQL 概述](overview.md)
- 有关基于服务层的具体资源配额和限制的信息，请参阅[服务层](concepts-service-tiers.md)
- 有关连接到服务的信息，请参阅 [Azure Database for PostgreSQL 的连接库](concepts-connection-libraries.md)。

