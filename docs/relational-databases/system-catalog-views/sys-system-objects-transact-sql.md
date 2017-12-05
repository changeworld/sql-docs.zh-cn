---
title: "sys.system_objects (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.system_objects
- system_objects
- system_objects_TSQL
- sys.system_objects_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.system_objects catalog view
ms.assetid: 069e9045-97f2-4463-8e8f-c73855f3ea0a
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4e947beabc03f97a3e764fc72f7d0b8edf1296d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemobjects-transact-sql"></a>sys.system_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  包含附带的所有架构范围的系统对象的一个行[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 所有系统对象都包含在名为 sys 或 INFORMATION_SCHEMA 的架构中。  
  
|列名|数据类型|说明|  
|-----------------|---------------|-----------------|  
|name|**sysname**|对象名。|  
|object_id|**int**|对象标识号。 是一个数据库中唯一的。|  
|principal_id|**int**|如果不是架构所有者，则为特定所有者的 ID。 默认情况下，架构包含的对象由架构所有者拥有。 不过，通过使用 ALTER AUTHORIZATION 语句更改所有权可以指定其他所有者。<br /><br /> 如果没有其他单个所有者，则为 NULL。<br /><br /> 如果对象类型为下列类型之一，则为 NULL：<br /><br /> C = CHECK 约束<br /><br /> D = DEFAULT（约束或独立）<br /><br /> F = FOREIGN KEY 约束<br /><br /> PK = PRIMARY KEY 约束<br /><br /> R = 规则（旧式，独立）<br /><br /> TA = 程序集 (CLR) 触发器<br /><br /> TR = SQL 触发器<br /><br /> UQ = UNIQUE 约束|  
|schema_id|**int**|包含该对象的架构的 ID。<br /><br /> 对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 附带的所有架构范围内的系统对象，该值将始终在 (schema_id('sys'), schema_id('INFORMATION_SCHEMA')) 中。|  
|parent_object_id|**int**|此对象所属对象的 ID。<br /><br /> 0 = 不是子对象。|  
|类型|**char(2)**|对象类型：<br /><br /> AF = 聚合函数 (CLR)<br /><br /> C = CHECK 约束<br /><br /> D = DEFAULT（约束或独立）<br /><br /> F = FOREIGN KEY 约束<br /><br /> FN = SQL 标量函数<br /><br /> FS = 程序集 (CLR) 标量函数<br /><br /> FT = 程序集 (CLR) 表值函数<br /><br /> IF = SQL 内联表值函数<br /><br /> IT = 内部表<br /><br /> P = SQL 存储过程<br /><br /> PC = 程序集 (CLR) 存储过程<br /><br /> PG = 计划指南<br /><br /> PK = PRIMARY KEY 约束<br /><br /> R = 规则（旧式，独立）<br /><br /> RF = 复制筛选过程<br /><br /> S = 系统基表<br /><br /> SN = 同义词<br /><br /> SQ = 服务队列<br /><br /> TA = 程序集 (CLR) DML 触发器<br /><br /> TF = SQL 表值函数<br /><br /> TR = SQL DML 触发器<br /><br /> TT = 表类型<br /><br /> U = 表（用户定义类型）<br /><br /> UQ = UNIQUE 约束<br /><br /> V = 视图<br /><br /> X = 扩展存储过程|  
|type_desc|**nvarchar(60)**|对象类型的说明。 AGGREGATE_FUNCTION<br /><br /> CHECK_CONSTRAINT<br /><br /> DEFAULT_CONSTRAINT<br /><br /> FOREIGN_KEY_CONSTRAINT<br /><br /> SQL_SCALAR_FUNCTION<br /><br /> CLR_SCALAR_FUNCTION<br /><br /> CLR_TABLE_VALUED_FUNCTION<br /><br /> SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> INTERNAL_TABLE<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> PLAN_GUIDE<br /><br /> PRIMARY_KEY_CONSTRAINT<br /><br /> RULE<br /><br /> REPLICATION_FILTER_PROCEDURE<br /><br /> SYSTEM_TABLE<br /><br /> SYNONYM<br /><br /> SERVICE_QUEUE<br /><br /> CLR_TRIGGER<br /><br /> SQL_TABLE_VALUED_FUNCTION<br /><br /> SQL_TRIGGER<br /><br /> TABLE_TYPE<br /><br /> USER_TABLE<br /><br /> UNIQUE_CONSTRAINT<br /><br /> VIEW<br /><br /> EXTENDED_STORED_PROCEDURE|  
|create_date|**datetime**|对象的创建日期。|  
|modify_date|**datetime**|通过使用 ALTER 语句上次修改对象的日期。 如果对象为表或视图，则创建或修改表或视图的聚集索引时，modify_date 也会随之更改。|  
|is_ms_shipped|**bit**|对象由内部创建[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]组件。|  
|is_published|**bit**|对象为发布对象。|  
|is_schema_published|**bit**|仅发布对象的架构。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [对象目录视图 &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  