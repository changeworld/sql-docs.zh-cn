---
title: SET STATISTICS IO (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs:
- TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 20099478d1d2dd047b1f17fe963c8fc45b1418fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670259"
---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 显示有关由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句生成的磁盘活动量的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 如果 STATISTICS IO 为 ON，则显示统计信息。 如果为 OFF，则不显示统计信息。  
  
 如果将此选项设置为 ON，则所有后续的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将返回统计信息，直到将该选项设置为 OFF 为止。  
  
 下表列出并说明了各个输出项。  
  
|输出项|含义|  
|-----------------|-------------|  
|**表**|表的名称。|  
|**扫描计数**|在任何方向都达到叶级别后启动的查询/扫描数，目的在于检索用于构造输出的最终数据集的所有值。<br /><br /> 如果使用的索引是主键的唯一索引或聚集索引并且您仅查找一个值，则扫描计数为 0。 例如 `WHERE Primary_Key_Column = <value>`。<br /><br /> 当使用对非主键列定义的非唯一的聚集索引搜索一个值时，扫描计数为 1。 这是为了针对您正在搜索的键值检查重复值。 例如 `WHERE Clustered_Index_Key_Column = <value>`。<br /><br /> 当 N 为通过使用索引键定位键值后，在叶级别的左侧或右侧启动的不同查找/扫描数时，则扫描计数为 N。|  
|**逻辑读取次数**|从数据缓存读取的页数。|  
|**物理读取次数**|从磁盘读取的页数。|  
|**预读次数**|为进行查询而放入缓存的页数。|  
|**lob 逻辑读取次数**|从数据缓存读取的 text、ntext、image 或大值类型（varchar(max)、nvarchar(max)、varbinary(max)）页的数目。|  
|**lob 物理读取次数**|从磁盘读取的 text、ntext、image 或大值类型页的数目。|  
|**lob 预读次数**|为进行查询而放入缓存的 text、ntext、image 或大值类型页的数目。|  
  
 SET STATISTICS IO 是在执行或运行时设置，而不是在分析时设置。  
  
> [!NOTE]  
>  当 Transact-SQL 语句检索 LOB 列时，有些 LOB 检索操作可能需要多次遍历 LOB 树。 这可能会导致 SET STATISTICS IO 报告的次数比预期的逻辑读取次数更高。  
  
## <a name="permissions"></a>Permissions  
 若要使用 SET STATISTICS IO，用户必须具有执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的适当权限。 但不需要 SHOWPLAN 权限。  
  
## <a name="examples"></a>示例  
 此示例显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处理语句时，进行了多少次逻辑读和物理读操作。  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS IO ON;  
GO  
SELECT *   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS IO OFF;  
GO  
```  
  
 下面是结果集：  
  
```  
Table 'ProductCostHistory'. Scan count 1, logical reads 5, physical   
reads 0, read-ahead reads 0, lob logical reads 0, lob physical reads 0,   
lob read-ahead reads 0.  
```  
  
## <a name="see-also"></a>另请参阅  
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL (Transact-SQL)](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET STATISTICS TIME (Transact-SQL)](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  
