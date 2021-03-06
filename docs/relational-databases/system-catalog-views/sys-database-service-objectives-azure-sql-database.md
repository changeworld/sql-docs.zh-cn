---
title: sys.database_service_objectives （Azure SQL 数据库） |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
keywords:
- 弹性池
- 弹性池管理
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: a8b37ada1fa7c6024a5454ed907b886e513c151c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769305"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives （Azure SQL 数据库）
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

如果有，将 Azure SQL 数据库或 Azure SQL 数据仓库，返回的版本 （服务层）、 服务目标 （定价层） 和弹性池名称。 如果登录到 Azure SQL 数据库服务器中的 master 数据库，返回所有数据库的信息。 对于 Azure SQL 数据仓库，您必须连接到 master 数据库。  
  
  
 有关定价的信息，请参阅[SQL 数据库选项和性能： SQL 数据库定价](https://azure.microsoft.com/pricing/details/sql-database/)并[SQL 数据仓库定价](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)。  
  
 若要更改服务设置，请参阅[ALTER DATABASE （Azure SQL 数据库）](../../t-sql/statements/alter-database-azure-sql-database.md)并[ALTER DATABASE （Azure SQL 数据仓库）](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)。  
  
 Sys.database_service_objectives 视图包含以下各列。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|database_id|ssNoversion|在 Azure SQL 数据库服务器的实例中是唯一的数据库的 ID。 使用可加入[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)。|  
|版本|sysname|数据库或数据仓库的服务层：**基本**，**标准**，**高级**或者**数据仓库**。|  
|service_objective|sysname|数据库的定价层。 如果数据库是在弹性池中，则返回**ElasticPool**。<br /><br /> 上**基本**层，返回**基本**。<br /><br /> **标准服务层中的单个数据库**返回以下值之一： S0、 S1、 S2、 S3、 S4、 S6、 S7、 S9 或 S12。<br /><br /> **高级层中的单个数据库**返回以下值： P1、 P2、 P4、 P6、 P11 或 P15。<br /><br /> **SQL 数据仓库**返回通过 DW10000c DW100。|  
|elastic_pool_name|sysname|名称[弹性池](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)属于数据库。 返回**NULL**如果数据库是单一数据库或数据 warehoue。|  
  
## <a name="permissions"></a>Permissions  
 需要**dbManager**的主数据库上的权限。  在数据库级别，用户必须是创建者或所有者。  
  
## <a name="examples"></a>示例  
 此示例的主数据库上或在用户数据库上运行。 查询将返回名称、 服务和数据库的性能层信息。  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
