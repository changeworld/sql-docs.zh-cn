---
title: "sys.pdw_health_component_properties (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 66fb48b26de19aca26c9edb41af4cb31b8f0f01b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  存储用于描述设备的属性。 某些属性显示设备状态和某些属性描述设备本身。  
  
|列名|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|组件的属性的唯一标识符。<br /><br /> property_id 和 component_id 组成的密钥，此视图。|NOT NULL|  
|component_id|**int**|组件的 ID。 请参阅[sys.pdw_health_components &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id 和 component_id 组成的密钥，此视图。|NOT NULL|  
|property_name|**nvarchar(255)**|属性的名称。|NOT NULL|  
|physical_name|**nvarchar(32)**|由制造商定义的属性名称。|NOT NULL|  
|is_key|**bit**|确定设备实例是唯一的或不唯一。|NOT NULL<br /><br /> 0-设备实例都是唯一的。<br /><br /> 1-设备实例不是唯一的。|  
  
## <a name="see-also"></a>另请参阅  
 [SQL 数据仓库和并行数据仓库目录视图](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  