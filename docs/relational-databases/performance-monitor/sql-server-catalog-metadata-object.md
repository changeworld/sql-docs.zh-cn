---
title: SQL Server - Catalog Metadata 对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 84a8e5324d5dcb1f2727fbc73d3a9c1f75fda618
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558364"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, 目录元数据对象
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**SQLServer:Catalog Metadata** 性能对象提供针对 SQL Server 的目录元数据提供计数器。

下表介绍了 SQL Server **目录元数据** 性能对象。


|**SQL Server 目录元数据计数器**|描述|  
|-------------|-----------------|  
|**Cache Entries Count**|目录元数据缓存中的项数。|
|**Cache Entries Pinned Count**|目录元数据缓存中已固定的项数。|
|**Cache Hit Ratio**|目录元数据缓存中命中次数和查找次数之比。|
|**Cache Hit Ratio Base**|仅限内部使用。|

每个数据库都有该计数器的一个实例。

## <a name="see-also"></a>另请参阅  
[监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
