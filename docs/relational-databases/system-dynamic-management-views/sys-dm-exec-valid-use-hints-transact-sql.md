---
title: sys.dm_exec_valid_use_hints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 628ef2cde5b345366a7ba0fb7ffff6c8e5143a0c
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806687"
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

返回[USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint)支持提示名称。 它列出了每行显示一个提示名称。  
  
使用此 DMV 来查看所有受支持提示下 USE HINT 表示法的列表。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|NAME|**sysname**|提示的名称。|

请参阅[查询提示](../../t-sql/queries/hints-transact-sql-query.md#use_hint)有关每个提示的说明。

中引入[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。
  
## <a name="see-also"></a>另请参阅  
    
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与数据库相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

