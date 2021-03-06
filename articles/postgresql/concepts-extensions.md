---
title: "使用 Azure Database for PostgreSQL 中的 PostgreSQL 扩展 | Microsoft Docs"
description: "介绍有关使用 Azure Database for PostgreSQL 中的扩展来扩展数据库功能的功能。"
services: postgresql
author: SaloniSonpal
ms.author: salonis
manager: jhubbard
editor: jasonwhowell
ms.service: postgresql-database
ms.topic: article
ms.date: 06/29/2017
ms.translationtype: Human Translation
ms.sourcegitcommit: 6dbb88577733d5ec0dc17acf7243b2ba7b829b38
ms.openlocfilehash: 4f85e27d01341d3d9d61d1984add32e72a53b6ac
ms.contentlocale: zh-cn
ms.lasthandoff: 07/04/2017

---
# <a name="postgresql-extensions-in-azure-database-for-postgresql"></a>Azure Database for PostgreSQL 中的 PostgreSQL 扩展
PostgreSQL 支持使用扩展来扩展数据的功能。 扩展允许单个包中的多个相关 SQL 对象捆绑在一起，并且可使用单个命令在数据库中加载或删除扩展。 扩展加载到数据库中后便可像内置功能一样工作。 有关 PostgreSQL 扩展的详细信息，请参阅 [Packaging Related Objects into an Extension](https://www.postgresql.org/docs/9.6/static/extend-extensions.html)（将相关对象打包到扩展中）。

## <a name="how-to-use-postgresql-extensions"></a>如何使用 PostgreSQL 扩展？
需先为数据库安装 PostgreSQL 扩展，才能使用该扩展。 若要安装特定扩展，请通过 psql 工具运行 [CREATE EXTENSION](https://www.postgresql.org/docs/9.6/static/sql-createextension.html) 命令，将打包的对象加载到数据库中。

用于 PostgreSQL 的 Azure 数据库支持本文列出的一部分键扩展。 不支持未列出的其他扩展。 不能使用 Azure Database for PostgreSQL 服务创建自己的扩展。

## <a name="extensions-supported-by-azure-database-for-postgresql"></a>Azure Database for PostgreSQL 支持的扩展
下表列出了用于 PostgreSQL 的 Azure 数据库目前支持的标准 PostgreSQL 扩展。 还可以通过查询 pg\_available\_extensions 获取此信息。 

### <a name="data-types-extensions"></a>数据类型扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [citext](https://www.postgresql.org/docs/9.6/static/citext.html) | 提供不区分大小写的字符串类型 |
| [hstore](https://www.postgresql.org/docs/9.6/static/hstore.html) | 提供用于存储键/值对集的数据类型 |

### <a name="functions-extensions"></a>函数扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [fuzzystrmatch](https://www.postgresql.org/docs/9.6/static/fuzzystrmatch.html) | 提供多个函数，用于确定字符串间的相似性和差异。 |
| [intarray](https://www.postgresql.org/docs/9.6/static/intarray.html) | 提供用于操作无 null 整数数组的函数和运算符。 |
| [pgcrypto](https://www.postgresql.org/docs/9.6/static/pgcrypto.html) | 提供加密函数 |
| [pg\_partman](https://pgxn.org/dist/pg_partman/doc/pg_partman.html) | 按时间或 ID 管理已分区的表 |
| [pg\_trgm](https://www.postgresql.org/docs/9.6/static/pgtrgm.html) | 提供函数和运算符，用于基于三元匹配确定字母数字文本的相似性 |
| [uuid ossp](https://www.postgresql.org/docs/9.6/static/uuid-ossp.html) | 生成全局唯一标识符 (UUID) |

### <a name="full-text-search-extensions"></a>全文搜索扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [unaccent](https://www.postgresql.org/docs/9.6/static/unaccent.html) | 删除了词素中重音（附加符号）的文本搜索字典。 |

### <a name="index-types-extensions"></a>索引类型扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [btree\_gin](https://www.postgresql.org/docs/9.6/static/btree-gin.html) | 提供示例 GIN 运算符类，该类对特定数据类型实现类似 B-tree 的行为。 |
| [btree\_gist](https://www.postgresql.org/docs/9.6/static/btree-gist.html) | 提供实施 B-tree 的 GiST 索引运算符类。 |

### <a name="language-extensions"></a>语言扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [plpgsql](https://www.postgresql.org/docs/9.6/static/plpgsql.html) | PL/pgSQL 可加载过程语言 |

### <a name="miscellaneous-extensions"></a>其他扩展

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [pg\_buffercache](https://www.postgresql.org/docs/9.6/static/pgbuffercache.html) | 提供一种方法用于实时检查共享缓冲区缓存的当前状况。 |
| [pg\_prewarm](https://www.postgresql.org/docs/9.6/static/pgprewarm.html) | 提供一种方法用于将相关数据加载到缓冲区缓存中。 |
| [pg\_stat\_statements](https://www.postgresql.org/docs/9.6/static/pgstatstatements.html) | 提供一种方法用于跟踪服务器执行的所有 SQL 语句的执行统计信息。 |
| [postgres\_fdw](https://www.postgresql.org/docs/9.6/static/postgres-fdw.html) | 外部数据包装器，用于访问外部 PostgreSQL 服务器中存储的数据 |

### <a name="postgis"></a>PostGIS

> [!div class="mx-tableFixed"]
| **扩展** | **说明** |
|---|---|
| [PostGIS](http://www.postgis.net/), postgis\_topology, postgis\_tiger\_geocoder, postgis\_sfcgal | PostgreSQL 的空间和地理对象。 |
| address\_standardizer, address\_standardizer\_data\_us | 用于将地址分析成构成元素。 用于支持地理编码地址规范化步骤。 |
| [pgrouting](http://pgrouting.org/) | 扩展 PostGIS / PostgreSQL 地理空间数据库，以提供地理空间路由功能。 |

## <a name="next-steps"></a>后续步骤
看不到想使用的扩展？ 请告诉我们。 若要支持现有请求或提出新反馈和诉求，请访问我们的[客户反馈论坛](https://feedback.azure.com/forums/597976-azure-database-for-postgresql)。

