---
title: 清除合并元数据（复制 Transact-SQL 编程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b559c7ea2f1cd882a9a737935416dbd5e1869187
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179477"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>清除合并元数据（复制 Transact-SQL 编程）
  合并代理基于发布的保持设置定期清除合并复制元数据。 在发布服务器和订阅服务器的 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)和 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 系统表中将定期清除元数据。 还可以使用复制存储过程以编程方式清除这些表中的数据。  
  
### <a name="to-manually-clean-up-merge-metadata"></a>手动清除合并元数据  
  
1.  在发布服务器的发布数据库中，执行 [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)。  
  
2.  （可选）请记录步骤 1 中从 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)和 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) 系统表中删除的行数，它们分别在 **@num_genhistory_rows**、 **@num_contents_rows**和 **@num_tombstone_rows** 输出参数中返回。  
  
3.  在订阅服务器中重复步骤 1 和 2 来清除订阅数据库的元数据。  
  
## <a name="see-also"></a>请参阅  
 [订阅过期和停用](../subscription-expiration-and-deactivation.md)  
  
  
