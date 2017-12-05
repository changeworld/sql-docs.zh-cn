---
title: "sys.dm_os_server_diagnostics_log_configurations |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e5a57c9617191a53545e590aa6695d82c0ee6d30
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  返回包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集诊断日志的当前配置的一行信息。 这些属性设置确定是否已启用诊断日志记录，以及日志文件的位置、数目和大小。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|指示应启用还是禁用日志记录。<br /><br /> 1 - 启用诊断日志记录<br /><br /> 0 - 禁用诊断日志记录|  
|max_size|**int**|在每个诊断日志可以增长到兆字节为单位的最大大小。 默认值为 100 MB。|  
|max_files|**int**|可以存储在计算机上的诊断日志文件的最大数量，超过该数量后这些文件将被新的诊断日志所取代。|  
|path|**nvarchar(260)**|指示诊断日志位置的路径。 默认位置是\<\MSSQL\Log > 中的安装文件夹[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]故障转移群集实例。|  
  
## <a name="permissions"></a>Permissions  
 需要对 SQL Server 故障转移群集实例具有 VIEW SERVER STATE 权限。  
  
## <a name="examples"></a>示例  
 下面的示例使用 sys.dm_os_server_diagnostics_log_configurations 返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移诊断日志的属性设置。  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log >|10|10|  
  
## <a name="see-also"></a>另请参阅  
 [查看和读取故障转移群集实例诊断日志](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  